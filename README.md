# Sparge Attention
This repository provides the official implementation of SpargeAttn.

**SpargeAttn: Accurate Sparse Attention Accelerating Any Model Inference**  
Paper: https://arxiv.org/abs/2502.18137  
Jintao Zhang, Chendong Xiang, Haofeng Huang, Haocheng Xi, Jia Wei, Jun Zhu, Jianfei Chen

<!-- <img src="./assets/overview.png" width="95%" alt="overview."> -->

<img src="./assets/speed_comparison.png" width="90%" alt="speed comparison.">

## Installation
### Base environment
+ `python>=3.9`   , `torch>=2.3.0`
- `CUDA`:
  + `>=12.8` for Blackwell
  + `>=12.4` for fp8 support on Ada
  + `>=12.3` for fp8 support on Hopper
  + `>=12.0` for Ampere


### Install Package

```bash
python setup.py install   # or pip install -e .
```


## Avalible API
- `spas_sage2_attn_meansim_cuda`: SpargeAttn based on [SageAttention2](https://github.com/thu-ml/SageAttention).

- `spas_sage_attn_meansim_cuda`: SpargeAttn based on [SageAttention](https://github.com/thu-ml/SageAttention).



## Usage Examples
### CogVideoX

Tuning:  
```bash
python evaluate/cogvideo_example.py  --use_spas_sage_attn --model_out_path evaluate/models_dict/CogVideoX-2b_0.06_0.07.pt --tune
```

Inference:  
```bash
python evaluate/cogvideo_example.py  --use_spas_sage_attn --model_out_path evaluate/models_dict/CogVideoX-2b_0.06_0.07.pt
```

> **Note:**
We provide pre-tuned hyper-parameters `CogVideoX-2b_0.06_0.07.pt` that allow you to run the inference script directly. However, for better performance in both speed and quality, we recommend re-tuning because the provided hyper-parameters are tuned with SpargeAttn based on SageAttention, whereas the default API is based on SageAttention2 now.

### LLama
The tuning and inference usage is similar to CogVideoX.



## Performance
![Local Image](./assets/exp_table.png)
> **Note:** All experiments in this paper used SpargeAttn based on SageAttention. An updated implementation based on SageAttention2, is available now. It further offers a 30% speedup.

<!-- <img src="./assets/more_mochi_example.png" width="60%" alt="End-to-end video generation on Mochi.">  

*End-to-end video generation on Mochi.*

<img src="./assets/niah128k.png" width="60%" alt="End-to-end performance of NIAH.">

*End-to-end performance of NIAH.*

<img src="./assets/visible_image.png" width="80%" alt="image generation."> -->



## Citation
**If you use this code or find our work valuable, please cite:**
```
@misc{zhang2025spargeattn,
      title={SpargeAttn: Accurate Sparse Attention Accelerating Any Model Inference}, 
      author={Jintao Zhang and Chendong Xiang and Haofeng Huang and Jia Wei and Haocheng Xi and Jun Zhu and Jianfei Chen},
      year={2025},
      eprint={2502.18137},
      archivePrefix={arXiv},
      primaryClass={cs.LG},
      url={https://arxiv.org/abs/2502.18137}, 
}

@inproceedings{zhang2025sageattention,
      title={SageAttention: Accurate 8-Bit Attention for Plug-and-play Inference Acceleration}, 
      author={Zhang, Jintao and Wei, Jia and Zhang, Pengle and Zhu, Jun and Chen, Jianfei},
      booktitle={International Conference on Learning Representations (ICLR)},
      year={2025}
}

@misc{zhang2024sageattention2,
      title={SageAttention2: Efficient Attention with Thorough Outlier Smoothing and Per-thread INT4 Quantization}, 
      author={Jintao Zhang and Haofeng Huang and Pengle Zhang and Jia Wei and Jun Zhu and Jianfei Chen},
      year={2024},
      eprint={2411.10958},
      archivePrefix={arXiv},
      primaryClass={cs.LG},
      url={https://arxiv.org/abs/2411.10958}, 
}
```
