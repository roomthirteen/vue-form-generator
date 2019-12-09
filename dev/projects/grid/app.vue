<template>
	<div class="container">
		<h1>Grouping</h1>
		<div class="row">
			<div class="col-sm-12">
				<vue-form-generator :schema="schema" :model="model" :options="formOptions" tag="section"></vue-form-generator>
			</div>
		</div>
		<div class="row">
			<div class="col-sm-12">
				<pre v-if="model" v-html="prettyModel"></pre>
			</div>
		</div>
	</div>
</template>

<script>
import mixinUtils from "../../mixins/utils.js";

export default {
	mixins: [mixinUtils],

	data() {
		return {
			model: {
				name: "Brian Blessed",
				email: "brian@hawkman.mongo",
				others: {
					more: "More",
					things: "Things"
				},
				single: "blah"
			},
			schema: {
				grid: {
					rows: [
						{
							cols: [
								{
									type: "input",
									inputType: "text",
									label: "Name",
									model: "name",
									cols: 8,
								},
								{
									type: "input",
									inputType: "email",
									label: "Email",
									model: "email",
									cols: 4,
								}
							]
						},
						{
							cols: [
								{
									type: "input",
									inputType: "text",
									label: "More",
									model: "others.more"
								},
								{
									type: "input",
									inputType: "text",
									label: "Things",
									model: "others.things"
								}
							]
						},
						{
							cols: [
								{
									type: "input",
									inputType: "text",
									label: "Single field (without group)",
									model: "single"
								}
							]
						}
					]
				}
			},
			formOptions: {
				fieldIdPrefix: "frm1-"
			}
		};
	},

	created() {
		window.app = this;
	}
};
</script>

<style lang="scss">
@import "../../style.scss";
</style>
