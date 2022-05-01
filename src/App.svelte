<script>
	import {onMount} from "svelte";

	let launches;

	onMount(async () => {
		var response = await fetch("https://api.spacexdata.com/v4/launches");
		launches = await response.json();
		console.log(launches);
	});
</script>

{#if launches}
{#each launches as launch}
	<div>
		<img src="{launch.links.patch.small}" alt="{launch.name}" width="200" height="200"/>
		<h1>Flight {launch.flight_number} - {launch.name}</h1>
		<p>{launch.details}</p>

	</div>
{/each}


{/if}

