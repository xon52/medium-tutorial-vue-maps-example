<template>
	<div id="app">
		<div id="map" ref="map">
			<map-marker :lat="-27.344" :lng="133.036"></map-marker>
			<map-marker :lat="-26.344" :lng="132.036"></map-marker>
			<map-marker :lat="-25.344" :lng="131.036"></map-marker>
			<map-info-window :lat="-24.344" :lng="130.036">Test 1</map-info-window>
			<map-info-window :lat="-23.344" :lng="129.036">
				<span style="background:red;">Test 2</span>
			</map-info-window>
			<map-info-window :lat="-22.344" :lng="128.036">
				<img
					src="https://1.bp.blogspot.com/_S2Wkv5XI8JI/TUL5MbRnT-I/AAAAAAAAACA/g8V_yjojceA/s1600/woot.jpg"
					height="100px"
				/>
			</map-info-window>
		</div>
	</div>
</template>

<script>
	import MapMarker from "./components/MapMarker"
	import MapInfoWindow from "./components/MapInfoWindow"

	export default {
		components: {
			MapMarker,
			MapInfoWindow
		},
		data: () => ({
			map: null
		}),
		methods: {
			getMap(callback) {
				let vm = this
				function checkForMap() {
					if (vm.map) callback(vm.map)
					else setTimeout(checkForMap, 200)
				}
				checkForMap()
			}
		},
		mounted() {
			this.map = new window.google.maps.Map(this.$refs["map"], {
				center: { lat: -23.444, lng: 129.036 },
				zoom: 7
			})
		}
	}
</script>

<style scoped>
	#map {
		height: 600px;
		background: gray;
	}
</style>
