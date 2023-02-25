# Spring Inflammasome Benchmark Dataset

Spring conducted a high content imaging screen on inflammasome activated primary human PBMCs using a library of bioactive small molecules to identify novel inflammasome inhibitors. Using images from these phenotypic datasets, we established a computational method to score phenotypic similarity in order to identify compounds that are likely biologically related.

This dataset is designed to benchmark the compound similarity method by allowing measurements of inherent sources of variability such as donors, plates, and experimental runs. We used a bespoke library of 623 compounds, profiled in 4 batches of 8 plates each across a total of 16 donors.

More details about the dataset can be found in our [SLAS2023 poster](https://www.springdiscovery.com/pdf/SLAS23-Poster-2-Inflammasome-Benchmark.pdf).

## Explore the data

The data can be visualized and analyzed on the [Spring platform](https://app.springscience.com/explore-iinflammasome-benchmark).

## Download the data

The raw image data, along with field metadata and pre-computed features can be accessed from the public [spring-inflammasom-benchmark-dataset](https://console.cloud.google.com/storage/browser/spring-inflammasome-benchmark-dataset) GCS bucket.

The dataset is organized in directories, one for each of the four batches of experiments.
Each directory is named with the date the experiment was executed, and includes the following items:
- The `raw_images` directory contains 2048x2048 16bit TIFF files organized in directories for each plate. The file names encode the location in the plate (`<well>_<field>`, e.g. `A01_f00`), as well as the timepoint `t`, the z-layer `z` and the channel `c` (e.g. `t0z0c0`). Note that for this dataset all images are taken at the same timepoint (`t0`) and z-layer (`z0`).
- The `immunofluorescence_metadata.json` file provides the information about the immunofluorescence dyes used in the experiment. The order in the `palette` arrays corresponds to the `channel` numeral in the image names.
- The `well_metadata.parquet` file contains the metadata information for each well in the experiment. See below for details about the metadata fields.
- The `features` directory contains `.parquet` files with pre-computed features for each cell. The files are organized in directories for each plate.

## Metadata

| Field Name | Description |
|-----------|------------|
| `plate` | Plate identifier, e.g. `plate-1-widefield-1` |
| `well` | Well identifier, e.g. `A01` |
| `field` | Field identifier, e.g. `f00` |
| `compound_id` | Compound identifier, e.g. `SD12405`|
| `compound_concentration` | Compound concentration used |
| `condition` | Treatment used to induce inflammation |
| `condition_concentration` | Concentration of the treatment used to induce inflammation |
| `acquisition_date` | Date of acquisition (same across whole plate) |
| `experiment` | Experiment batch identifier |
| `imager` | Imager used in the experiment |
| `palette_number` | Palette of immunofluorescence dyes used in the experiment (index of the `palettes` array in `immunofluorescence_metadata.json`)|
| `source_plate` | Plate unique identifier across the whole dataset |
| `staining_date` | Staining date |
| `donor_type` | Donor type |
| `order` | Unique identifier for the cell cohort (i.e. purchase order) |
| `donor_id` | Donor identifier |
| `compound_name` | Compound name |

## License

[![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
