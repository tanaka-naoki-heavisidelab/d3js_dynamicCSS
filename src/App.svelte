<script lang="ts">
  let grid_size = 32;
  let line_thick = 1;
  let grid_color = "#dddddd";
  let line_color = "#222222";

  $: gridform = {
    size: grid_size + "px",
    line: grid_size - line_thick + "px",
    color_g: grid_color,
    color_l: line_color,
  };

  $: cssVarStyles = Object.entries(gridform)
    .map(([key, value]) => `--${key}:${value}`)
    .join(";");
</script>

<div id="top" style={cssVarStyles}>
  <label for="gridsize">グリッドサイズ</label>
  <input type="range" bind:value={grid_size} min="1" max="100" />
  <input type="number" bind:value={grid_size} min="1" max="100" id="gridsize" />

  <label for="linethick">線幅 </label>
  <input type="range" bind:value={line_thick} min="1" max="5" />
  <input type="number" bind:value={line_thick} min="1" max="5" id="linethick" />

  <label for="gridcolor">背景色</label>
  <input
    style="padding:0"
    type="color"
    bind:value={grid_color}
    id="gridcolor"
  />
  <input type="text" bind:value={grid_color} />

  <label for="linecolor">線色</label>
  <input
    style="padding:0"
    type="color"
    bind:value={line_color}
    id="linecolor"
  />
  <input type="text" bind:value={line_color} />

  <div class="box" />
</div>

<style lang="scss">
  #top {
    .box {
      max-width: 500px;
      height: 500px;
      border: solid 1px var(--color_l);
      background-image: linear-gradient(
          0deg,
          transparent var(--line),
          var(--color_l) var(--size)
        ),
        linear-gradient(
          90deg,
          transparent var(--line),
          var(--color_l) var(--size)
        );
      background-color: var(--color_g);
      background-size: var(--size) var(--size);
    }

    input[type="number"] {
      width: 5em;
      border: 1px #222 solid;
      text-align: right;
    }
    input[type="range"] {
      width: 10em;
      margin: 1em;
      vertical-align: middle;
    }
    input[type="color"] {
      width: 10em;
      margin: 1em;
      vertical-align: middle;
    }
  }
</style>
