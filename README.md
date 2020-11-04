![logo](./figures/Dream-DIA.jpg)

Software for data-independent acquisition (DIA) proteomic data with deep representation features.

## Requirements

```
python >= 3.6.0
pyteomics
numpy
pandas
seaborn
cython
scikit-learn
tensorflow
keras-gpu
xgboost
```

## Installation

```bash
git clone https://github.com/xmuyulab/Dream-DIA
cd Dream-DIA
bash build.sh
```

## Quick start

```bash
python Dream-DIA/DreamDIA.py dreamscore --help
```

```bash
python Dream-DIA/DreamDIA.py dreamscore --file_dir rawdata_dir --lib library.tsv --win win.tsv --out output_dir
```

## Notes

#### 1. DIA raw data files

Centroided .mzML or .mzXML files and .raw files from Thermo Fisher equipments are supported. 

**Attention!!!** If .raw files are going to be processed on Linux systems, [mono](https://www.mono-project.com/download/stable/#download-lin) must be installed.

All raw data files are suggested being put at the same directory as below. 

```
# rawdata_dir/
	rawdata_1.mzML
	rawdata_2.mzXML
	rawdata_3.raw
```

#### 2. Spectral libraries

Only .tsv libraries are supported. All of the fields required by Dream-DIA are listed in `Dream-DIA/lib_col_settings`. Users can modify this file to adjust their own spectral libraries.

#### 3. window setting file

Dream-DIA needs a tab separated window setting file **without overlapping** among the isolation windows as OpenSWATH. An example window setting file for classical SWATH acquisition strategy is shown below.

```
399     424.5
424.5   449.5
449.5   474.5
474.5   499.5
499.5   524.5
524.5   549.5
549.5   574.5
574.5   599.5
599.5   624.5
624.5   649.5
649.5   674.5
674.5   699.5
699.5   724.5
724.5   749.5
749.5   774.5
774.5   799.5
799.5   824.5
824.5   849.5
849.5   874.5
874.5   899.5
899.5   924.5
924.5   949.5
949.5   974.5
974.5   999.5
999.5   1024.5
1024.5  1049.5
1049.5  1074.5
1074.5  1099.5
1099.5  1124.5
1124.5  1149.5
1149.5  1174.5
1174.5  1199.5
```

#### 4. output

Dream-DIA outputs identification and quantification results. A blank directory is suggested for the `--out` argument to save all of the output files.