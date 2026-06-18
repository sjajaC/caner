# Room Layout Planner

An interactive, single-file web app for planning furniture arrangements in a room,
with synchronized **2D top-down** and **3D perspective** views. Everything is in
**meters**. No build step, no dependencies, no network required — just open the file.

## Run it

Open `index.html` in any modern browser (double-click it, or serve the folder).

There is nothing to install. The 3D view uses a small hand-written canvas renderer,
so the whole app is genuinely self-contained and works offline.

## Features

**Room setup**
- Enter room width × length and ceiling height (meters) in the header to set the base rectangle.
- Floor plan is drawn to scale with a 0.5 m / 1 m grid and edge measurement labels.
- **Any room shape:** turn on *Room shape → Edit corners* to drag the room's corner
  points, click the **+** on a wall to add a corner, and right-click a corner to remove it
  (L-shaped rooms, bays, angled walls, …). Each wall shows its length; the grid, the 3D
  walls/floor, and the "outside the room" check all follow the custom shape.

**2D top-down view**
- Furniture shown as labeled, color-coded rectangles, to scale.
- Drag to move, **⟳** button to rotate 90°, corner handle to resize.
- Snap-to-grid and grid visibility toggles.
- Each piece shows its size in meters; overlaps and out-of-room pieces are
  outlined in red with warnings listed in the corner.

**3D perspective view**
- Room rendered with floor, walls and a floor grid from the real dimensions.
- Each item is a labeled 3D box using its real width × depth × height.
- **Drag** to orbit, **right-drag / Shift-drag** to pan, **scroll** to zoom.
- Item positions stay in sync with the 2D view (single shared model).

**Furniture management**
- Add a piece by name + width × depth × height, with a color picker.
- Sidebar lists every item with its dimensions and add/delete controls.
- Select an item to edit its name, size, position, rotation and color precisely.

**General**
- Metric throughout, clean minimal UI.
- Layout is saved to `localStorage`, so it persists across reloads.
- **Reset** restores the starting example room.

## Coordinate model

- Room origin `(0,0)` is the top-left of the 2D plan.
- `x` = width (left→right), `z` = length (top→bottom in 2D / depth in 3D), `y` = height (up, 3D only).
- An item's `(x, z)` is the center of its footprint. Rotation is in 90° steps; the
  footprint's width/depth swap at 90°/270°.
