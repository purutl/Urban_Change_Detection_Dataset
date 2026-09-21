# Urban_Change_Detection_Dataset
# Urban Change Detection Dataset (Google Earth, Tumakuru, Karnataka, India)

Bi-temporal, manually annotated satellite image pairs for building-level urban change detection, collected from urban and semi-urban localities of Karnataka, India. The dataset supports the article:

> Purushottama T L, "Deep Learning-Based Framework for Detecting Urban Growth and Transformation in Satellite Images."

## Image credit

**All satellite imagery in this dataset was obtained from Google Earth.**
Imagery © Google and its imagery providers `<add the provider credit line shown in Google Earth, e.g. "Image © <year> <provider>">`. Google and Google Earth are trademarks of Google LLC. This dataset is not affiliated with or endorsed by Google. The imagery remains the property of Google and its data providers and is subject to [Google's terms of use and attribution guidelines](https://www.google.com/permissions/geoguidelines/). The authors contributed the image-pair selection, the manual change annotations and the derived masks.

## Overview

| Item | Description |
|---|---|
| Task | Urban change detection (binary and ternary) |
| Source imagery | Google Earth, pre-change and post-change scenes of the same location |
| Image size | 1024 x 1024 pixels |
| Ground sampling distance | Typically 0.3-0.5 m per pixel, depending on acquisition scale |
| Study areas | Tumakuru (Amanikere, surroundings of DD Hills, Amanikere Ring Road corridor, other densely built-up pockets), Mangaluru, Madikeri |
| Number of image pairs | `<number>` |
| Train / validation / test | `<numbers>` |
| Acquisition dates | `<pre-change and post-change years>` |

## Content

Each pair consists of a pre-change (T1) and a post-change (T2) image captured at different times. The scenes document:

- new construction
- demolition of older structures
- vertical and horizontal expansion of buildings
- land-use change

The dataset includes real-world difficulties such as varying illumination, seasonal change and shadow effects. Locations were chosen to vary terrain, building morphology and landscape pattern.

## Annotation

Method: Every image pair was annotated manually by CVAT: Computer Vision Annotation Tool.
Binary masks: white pixels (value 1) mark changed areas and black pixels (value 0) mark unchanged areas.
Ternary masks: three-class reference maps for the ternary model. They separate positive change (construction) from negative change (demolition or clearing) and no change. Class-to-value mapping.

## Directory structure


|-- README.md
|-- Urban_Change_Detection_Dataset
```

Use identical file names across `A`, `B` and `label`, for example `0001.png`.

## Area estimation

Each pixel covers a known ground area, so a predicted change map can be converted to area:

A = N_c x d^2

where N_c is the number of changed pixels and d is the ground sampling distance in metres. For example, with d = 0.5 m (0.25 m^2 per pixel), 10,000 changed pixels correspond to 2,500 m^2. Because the GSD of this dataset varies (0.3-0.5 m), adjust d for each image.

## Related benchmark

The models in the article were also evaluated on the public LEVIR-CD benchmark (637 pairs of 1024 x 1024 pixels at 0.5 m), which must be obtained from its original authors.



