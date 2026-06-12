---
title: "Use Nvidia GPU in Blender"
date: 2015-08-21
forum: New to Ubuntu
---

### Post by tristan16 on 2015-08-21
I'm trying to enable CUDA GPU rendering in Blender. I followed the post here: [https://askubuntu.com/questions/628680/nvidia-cuda-in-15-04-for-gpu-rendering-in-blender](https://askubuntu.com/questions/628680/nvidia-cuda-in-15-04-for-gpu-rendering-in-blender)

After installing nvidia-cuda-toolkit and nvidia-modprobe, my GeForce GTX 760 now comes up under CUDA in Blender System Settings:
[ATTACH=CONFIG]263981[/ATTACH]

As you can see, I have it selected as the compute device. However, I don't see an option to select my compute device when I'm rendering:
[ATTACH=CONFIG]263982[/ATTACH]

Can anyone help me resolve this issue? Here's my version info:

nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2014 NVIDIA Corporation
Built on Thu_Jul_17_21:41:27_CDT_2014
Cuda compilation tools, release 6.5, V6.5.12

Graphics Driver Version 352.30, CUDA version 7.5

---

### Post by tristan16 on 2015-08-22
Solved it! Apparently, only the Cycles rendering engine has this support. The Blender Internal engine (which I was using) only uses the CPU.

---

