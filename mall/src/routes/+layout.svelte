<script lang="ts">
	import '../app.postcss';
	import '@fortawesome/fontawesome-free/css/all.css';
	
	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
    import type { PageData } from './$types';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
	export let data: PageData;


</script>

<div class="appbar flex flex-row bg-surface-100-800-token p-3 mb-10 shadow-2xl">
	
	
	
	<div class=" justify-center flex flex-row gap-10 w-full">
		<a href="https://github.com/ContainerOFAids/Mall" class="btn-icon text-black hover:text-white left-0 absolute"><i class="fa-brands fa-github fa-4x ml-5"></i></a>
		<a href="/" class="btn h2 font-bold hover:variant-soft-primary">Hem</a>
		<a href="/login" class="btn h2 font-bold hover:variant-soft-primary">Log In</a>

		{#if data.user}
			<a href="/activities" class="btn h2 font-bold hover:variant-soft-primary">Styling</a>
		{/if}
		
		
		{#if data.isAdmin}
			<a href="/admin-panel" class="btn h2 font-bold hover:variant-soft-primary">Admin panel</a>
		{/if}
		{#if data.user}
		<a href="/profile" class=" absolute right-0">
			<div class="flex mr-2">
				<h2 class="h2 flex items-center">{data.user?.name}</h2>
				<img class="avatar-image w-16 rounded-full aspect-square ml-2" src="{data.user?.pic}" alt="">
			</div>
		</a>
		{/if}
	</div>

</div>
<slot />