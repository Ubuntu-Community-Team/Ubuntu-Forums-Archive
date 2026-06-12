---
title: "eGPU is detected but no output is displayed"
date: 2019-03-23
forum: New to Ubuntu
---

### Post by stayandwait on 2019-03-23
I have an aorus 1080 eGPU. I plugged monitors into the eGPU and I have no signal. I believe I have everything setup correctly. Any solutions would be great.

After installing the nvidia drivers and cuda I did (I restarted after installing the drivers)
```
# sudo prime-select nvidia
```

When I run nvidia-smi (assuming everything is good)
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 418.43       Driver Version: 418.43       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1080    Off  | 00000000:07:00.0 Off |                  N/A |
| 46%   36C    P0    38W / 180W |      0MiB /  8119MiB |      5%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```

---

### Post by wildmanne39 on 2019-03-23
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

