<script>
	export let task;
	export let ongoing;
	import { ttGetDurationString, ttSlotToTtime, ttGetTimeString } from '../../../ddtt/ttime';
	import { ddGetFullRelativeDateShort, ddToday } from '../../../ddtt/ddate';
	import { ttimeToNslots } from '../../logic/logic';
</script>

<div class="yysbp ggshadow ll1 {task.completed ? 'gg-c-task2' : 'gg-c-task1'}">
	<div class="yys-wbp-hbc ggshadowtext yynoselect ll3">
		<nobr class="yys-wbp-hbc">
			{#if task.ttime !== 0}
				<nobr>
					{ttGetTimeString(task.ttime)}
					&ndash;
					{ttGetTimeString(task.ttime + task.tdur)}, ({ttGetDurationString(task.tdur)})
				</nobr>
			{:else}
				<!-- <nobr>
					{ttGetTimeString(ttSlotToTtime(taskInfo.slot))}
					&ndash;
					{ttGetTimeString(ttSlotToTtime(taskInfo.slot + ttimeToNslots(task.tdur)))}
				</nobr> -->
				<nobr>
					({ttGetDurationString(task.tdur)})
				</nobr>
			{/if}
		</nobr>
		<nobr>
			{ddGetFullRelativeDateShort(ddToday(), task.ddate)}
		</nobr>
	</div>

	<div class={"yys-wbp-hbc yycc ll5 ggshadowtext yynoselect"+(ongoing?" llog":"")}>
		<p class="yysbc">
			<nobr class="yysbc">{task.text}</nobr>
		</p>
	</div>

</div>

<style>
	.ll1 {
		display: flex;
		flex-direction: column;
		padding: 10px;
		gap: 20px;
		justify-content: start;
		/* border-radius: 20px; */
	}

	.ll3 {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		gap: 10px;
		font-family: Roboto;
		font-style: normal;
		font-weight: normal;
		font-size: 18px;
		color: #007;
	}
	.ll5 {
		font-family: Roboto;
		font-style: normal;
		font-weight: normal;
		font-size: 18px;
		overflow-x: hidden;
	}
	.llog{
		color: #700;
	}
</style>
