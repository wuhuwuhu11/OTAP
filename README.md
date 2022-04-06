# Environmental requirements

* [PyTorch](http://pytorch.org/) version >= 1.5.0
* Python version >= 3.6
* For training new models, you'll also need an NVIDIA GPU and [NCCL](https://github.com/NVIDIA/nccl)
* **To install fairseq** and develop locally:

``` bash
git clone https://github.com/pytorch/fairseq
cd fairseq
pip install --editable ./

# on MacOS:
# CFLAGS="-stdlib=libc++" pip install --editable ./

# to install the latest stable release (0.10.x)
# pip install fairseq
```

* **For faster training** install NVIDIA's [apex](https://github.com/NVIDIA/apex) library:

``` bash
git clone https://github.com/NVIDIA/apex
cd apex
pip install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" \
  --global-option="--deprecated_fused_adam" --global-option="--xentropy" \
  --global-option="--fast_multihead_attn" ./
```

* **For large datasets** install [PyArrow](https://arrow.apache.org/docs/python/install.html#using-pip): `pip install pyarrow`
* If you use Docker make sure to increase the shared memory size either with `--ipc=host` or `--shm-size`
 as command line options to `nvidia-docker run` .

* **Install required packages**
``` 
pip install -r requirements.txt
```
# Emphasize
* Replace the fairseq package containing the DR-reformer model
* Replace the fairseq package under this git with the default fairseq package installed in the virtual environment you use(Otherwise fairseq has no DR-reformer model)
# Start Using
* Pre-training
```buildoutcfg
export CUDA_VISIBLE_DEVICES=0 && bash /home/a/OTAP/train/pre-train.sh /home/a/OTAP/pre-train.yml
```
* Fine-tuning
```buildoutcfg
export CUDA_VISIBLE_DEVICES=0 && bash /home/a/OTAP/train/fine-tune.sh /home/a/OTAP/fine-tune.yml
```
