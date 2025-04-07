# Dynamic Grid Composition Generator

This repository contains a JavaScript tool that dynamically generates grid-based compositions from photographic images. The layout is designed to leave reserved areas (for typography) and to create a dynamic, “river-like” flow of images that range in size—from large blocks to scattered small ones. The images are processed with Floyd–Steinberg diffusion dithering to produce a halftone black-and-white effect. The final output is rendered as separate layers (photos, margins, and a grid with numbered cells) that can be exported as PNG files for further editing in design tools like Photoshop.

## Purpose

The primary goal of this tool is to automate the creation of experimental, grid-based layouts with these characteristics:

- **Reserved Areas:**  
  Specific grid cells (defined by row-major numbering) are reserved for a typography layer.

- **Dynamic River Path:**  
  A continuous “river” of image blocks is forced through each column (if available), creating a meandering flow of images.

- **Mixed Block Sizes:**  
  The tiling algorithm uses a mix of allowed block sizes—including small (1×1 and 2×2) and larger blocks—to achieve a dynamic, scattered composition.

- **Dithered Imagery:**  
  Each image is cover-cropped into its allocated grid block and processed with Floyd–Steinberg diffusion dithering for a GIF-like, black-and-white, halftone aesthetic.

- **Layered Output:**  
  The tool renders multiple layers:
  - **Composition (Photos) Layer:** Contains the dithered images on a transparent background.
  - **Margin Overlay:** Displays variable, color-coded margins (with white replaced by transparency) around the image blocks.
  - **Grid Overlay:** Shows a numbered grid with a drop shadow on the numbers for legibility.

- **Download Options:**  
  Separate download buttons allow you to export the photos and margins layers as individual PNG files.

## Features

- **Grid-Based Layout:**  
  The canvas is divided into a 36×20 grid, organizing image placement.

- **Reserved Areas:**  
  Specific cell ranges (in row-major order) are reserved so that no images or margins appear there, leaving space for a separate typography layer.

- **River Path Generation:**  
  A “river” of 1×1 image blocks is forced (one per column, if available) to create a continuous, meandering path through the grid.

- **Dynamic Tiling:**  
  The remaining free cells are tiled using a mix of allowed block sizes (including small blocks) to create a scattered yet balanced composition.

- **Image Processing with Dithering:**  
  Images are cover-cropped onto offscreen canvases and processed using Floyd–Steinberg diffusion dithering to yield a halftone, black-and-white look.

- **Layered Rendering:**  
  Separate canvas layers are used for:
  - **Photos (Composition) Layer:** Rendered on a transparent background.
  - **Margin Overlay:** Drawn over the photos with color-coded margins.
  - **Grid Overlay:** Placed on top with numbered cells and a white drop shadow for clarity.

- **Export Options:**  
  Download buttons allow you to export the photos layer and the margins layer as separate PNG files.

## Approach

1. **Grid Initialization & Reserved Areas:**  
   - The canvas is divided into a 36×20 grid.
   - An occupancy grid is created where each cell is marked as reserved if its row-major number falls within specified ranges.

2. **River Path Generation:**  
   - For each column, a free cell is randomly selected (if available) and forced as a 1×1 block, creating a continuous “river” of images.

3. **Dynamic Tiling:**  
   - The remaining free cells are tiled using a probabilistic algorithm that selects from a mix of allowed block sizes (including 1×1 and 2×2 blocks).
   - An extra pass fills any rows that remain completely empty.

4. **Image Processing:**  
   - Each block’s image is cover-cropped into an offscreen canvas, then processed with Floyd–Steinberg dithering.
   - The processed image is drawn into the block’s area on the composition canvas with variable margins.

5. **Layer Rendering:**  
   - The composition (photos) layer is rendered with a transparent background.
   - The margin overlay is drawn with color-coded margins.
   - The grid overlay (with numbered cells and drop shadows) is drawn on top for reference.

6. **Exporting Assets:**  
   - Separate download buttons export the photos layer and the margins layer as standalone PNG files.

## Usage

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/yourusername/dynamic-grid-composition-generator.git
   cd dynamic-grid-composition-generator

2.	**Open the HTML File:**
    - Open index.html in your web browser (Chrome, Firefox, etc.). This tool is intended for local use.

3.	**Customize Settings:**
    - You can modify the reserved cell ranges, allowed block sizes, and tiling probabilities directly in the code.
	
4.	**Generate & Export:**
    - The composition is generated dynamically on page load. Use the toggle checkboxes to show or hide the grid and margin overlays. Click the download buttons to export the photos and margins layers as individual PNG images.


## License

This project is licensed under the MIT License. See the [LICENSE](https://opensource.org/license/mit) file for details.