<template>
  <div></div>
</template>
<script>
import L from "leaflet";
import { findRealParent } from "vue2-leaflet";
import LeafletSearch from "leaflet-search";

export default {
  name: "VueLeafletSearch",
  data() {
    return {};
  },
  mounted() {
    this.parentContainer = findRealParent(this.$parent);
    this.parentContainer.mapObject.addControl(
      new L.Control.Search({
        url: "https://nominatim.openstreetmap.org/search?format=json&q={s}",
        jsonpParam: "json_callback",
        propertyName: "display_name",
        propertyLoc: ["lat", "lon"],
        marker: L.circleMarker([0, 0], { radius: 30 }),
        autoCollapse: true,
        autoType: true,
        minLength: 2
      })
    );
  },
  methods: {
    leafletSearcInit() {
      LeafletSearch;
    }
  }
};
</script>
<style>
@import "~leaflet-search/src/leaflet-search.css";
</style>
