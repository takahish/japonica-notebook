# japanica-notebook

A docker image and container of Jupyter Notebook. The environment uses the [japonica-warehouse](https://github.com/takahish/japonica-notebook) as a database. It is assumed that the data in the database can be used in a training machine learning model or an autonomous AI system.

## Table of content

- [Bulding steps](#Building-steps)
    - [Build image from docker-compose](#Build-image-from-docker-compose)
    - [Run container](#Run-container)
    
## Building steps

### Build image from docker-compose

You don't need to build the image if you use the image from the docker hub. But you can build the image manually. Here are the build steps.

```shell
# Clone this repository.
$ git clone https://github.com/takahish/japonica-notebook.git

# Update submodules.
$ git submodule update --init --recursive

# Build japonica-notebook image.
$ docker-compose -f docker-compose-for-build.yml build
```

### Run container

```shell
# Detach japonica-notebook.
# Here is the commands if you build image manually.
$ docker-compose -f docker-compose-for-build.yml up -d

# ... or you can run the container directly from the image from the docker hub.
# After this step, I will describe the topics using the image from the docker hub.
$ docker-compose up -d
```

## Usage notebook with japonica-notebook

You can access http://localhost:8801/login?token=jnbuser and open Jupyter-labs. Installed libraries are below,

- japonica-warehouse as data store.
    - https://github.com/takahish/japonica-warehouse
    - You can connect data warehouse with python client.
- Originally scipy-notebook has the basic python libraries such as,
    - Everything in jupyter/minimal-notebook and its ancestor images
    - altair, beautifulsoup4, bokeh, bottleneck, cloudpickle, conda-forge::blas=*=openblas, cython, dask, dill, h5py, matplotlib-base, numba, numexpr, pandas, patsy, protobuf, pytables, scikit-image, scikit-learn, scipy, seaborn, sqlalchemy, statsmodel, sympy, widgetsnbextension, xlrd packages
    - ipympl and ipywidgets for interactive visualizations and plots in Python notebooks
    - Facets for visualizing machine learning datasets
- In addition to the scipy-notebook's libraries, some deep learing libraries such as,
    - pymc3, xgboost, lightgbm, shap
    - tensorflow, tensorboard, tensorflow-probability for CPU setting
    - torch, torchvision, torchaudio, torchtext, pytorch-lightning, transformers for CPU setting
    - fugashi, ipadic for morphological analysis.

Especially, GPU settings for TensorFlow and PyTorch will be set in the future.

## Remarks

Japonica Notebook is famous as the study notebook at the elementary school in Japan. Therefore, I hope the japonica-notebook and japonica-warehouse help those who want to experiment and explore a machine learning algorithm on your project and who want to manage the datasets and the metadata that includes the experimental results, etc., by using the notebook or database, the same as a student in elementary school writes and tracks their study history. Here is the Amazon link for the [Japonica Learning book](https://www.amazon.co.jp/%E3%82%B8%E3%83%A3%E3%83%9D%E3%83%8B%E3%82%AB%E5%AD%A6%E7%BF%92%E5%B8%B3/s?k=%E3%82%B8%E3%83%A3%E3%83%9D%E3%83%8B%E3%82%AB%E5%AD%A6%E7%BF%92%E5%B8%B3) and special thanks to [SHOWA NOTE CO., LTD.](https://www.showa-note.co.jp/)
