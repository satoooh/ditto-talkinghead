<h2 align='center'>Ditto: Motion-Space Diffusion for Controllable Realtime Talking Head Synthesis</h2>

<div align='center'>
    <a href=""><strong>Tianqi Li</strong></a>
    ·
    <a href=""><strong>Ruobing Zheng</strong></a><sup>†</sup>
    ·
    <a href=""><strong>Minghui Yang</strong></a>
    ·
    <a href=""><strong>Jingdong Chen</strong></a>
    ·
    <a href=""><strong>Ming Yang</strong></a>
</div>
<div align='center'>
Ant Group
</div>
<br>
<div align='center'>
    <a href='https://arxiv.org/abs/2411.19509'><img src='https://img.shields.io/badge/Paper-arXiv-red'></a>
    <a href='https://digital-avatar.github.io/ai/Ditto/'><img src='https://img.shields.io/badge/Project-Page-blue'></a>
    <a href='https://huggingface.co/digital-avatar/ditto-talkinghead'><img src='https://img.shields.io/badge/Model-HuggingFace-yellow'></a>
    <a href='https://github.com/antgroup/ditto-talkinghead'><img src='https://img.shields.io/badge/Code-GitHub-purple'></a>
    <a href='https://colab.research.google.com/drive/19SUi1TiO32IS-Crmsu9wrkNspWE8tFbs?usp=sharing'><img src='https://img.shields.io/badge/Demo-Colab-orange'></a>
    <!-- <a href='https://github.com/antgroup/ditto-talkinghead'><img src='https://img.shields.io/github/stars/antgroup/ditto-talkinghead?style=social'></a> -->
</div>
<br>
<div align="center">
    <video style="width: 95%; object-fit: cover;" controls loop src="https://github.com/user-attachments/assets/ef1a0b08-bff3-4997-a6dd-62a7f51cdb40" muted="false"></video>
    <p>
    ✨  For more results, visit our <a href="https://digital-avatar.github.io/ai/Ditto/"><strong>Project Page</strong></a> ✨ 
    </p>
</div>


## 📌 Updates
* [2025.01.21] 🔥 We update the [Colab](https://colab.research.google.com/drive/19SUi1TiO32IS-Crmsu9wrkNspWE8tFbs?usp=sharing) demo, welcome to try it. 
* [2025.01.10] 🔥 We release our inference [codes](https://github.com/antgroup/ditto-talkinghead) and [models](https://huggingface.co/digital-avatar/ditto-talkinghead).
* [2024.11.29] 🔥 Our [paper](https://arxiv.org/abs/2411.19509) is in public on arxiv.

 

## 🛠️ Installation

Tested Environment  
- System: Ubuntu 20.04 (WSL2)
- GPU: NVIDIA RTX 3070
- Python: 3.10
- tensorRT: 8.6.1


```bash
git clone https://github.com/satoooh/ditto-talkinghead
cd ditto-talkinghead

# install dependencies
uv sync

# download checkpoints
git lfs install
git clone https://huggingface.co/digital-avatar/ditto-talkinghead checkpoints

# run inference.py
uv run python inference.py --data_root "./checkpoints/ditto_trt_Ampere_Plus" --cfg_pkl "./checkpoints/ditto_cfg/v0.4_hubert_cfg_trt.pkl" --audio_path "./example/audio.wav" --source_path "./example/image.png" --output_path "./tmp/result.mp4"
```

❗Note:

We have provided the tensorRT model with `hardware-compatibility-level=Ampere_Plus` (`checkpoints/ditto_trt_Ampere_Plus/`). If your GPU does not support it, please execute the `cvt_onnx_to_trt.py` script to convert from the general onnx model (`checkpoints/ditto_onnx/`) to the tensorRT model.

```bash
uv run python script/cvt_onnx_to_trt.py --onnx_dir "./checkpoints/ditto_onnx" --trt_dir "./checkpoints/ditto_trt_custom"
```

Then run `inference.py` with `--data_root=./checkpoints/ditto_trt_custom`.
