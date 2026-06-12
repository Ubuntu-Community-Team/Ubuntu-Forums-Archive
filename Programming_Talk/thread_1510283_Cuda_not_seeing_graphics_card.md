---
title: "Cuda not seeing graphics card"
date: 2010-06-15
forum: Programming Talk
---

### Post by kaspar_silas on 2010-06-15
Has anyone tried CUDA working in 64bit 10.04 and ran into problems.

My installation procedure followed:
[http://forums.techarena.in/operating-systems/1336959.htm]("http://forums.techarena.in/operating-systems/1336959.htm")

All seemed good and the examples compiled without issue. However running the resultant binaries gave the alarming message:

cutil error: no devices supporting CUDA.

Which is in contrast to what my xorg.conf and even lspci -v says:

```
...
03:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fe000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, nouveau

...
```

So anyone else encountered this?

---

### Post by Zugzwang on 2010-06-15
Hmm, the GeForce 6200 is not listed on [http://www.nvidia.com/object/cuda_gpus.html](http://www.nvidia.com/object/cuda_gpus.html), so are you sure that it is Cuda-capable?

---

### Post by cascade9 on 2010-06-15
Your 6200 doesnt support CUDA- 

> CUDA ENABLED GEFORCE PRODUCTS               
    GeForce 8, 9, 100, 200, 400-series GPUs with a minimum of 256MB of local graphics memory. 

[http://www.nvidia.com/object/cuda_gpus.html](http://www.nvidia.com/object/cuda_gpus.html)

*edit- you win Zugzwang, but only by seconds :lolflag:

---

### Post by kaspar_silas on 2010-06-15
A okay that's pretty clear then. Plus in retrospect very obvious (like most things). Thanks guys for pointing this out. 

Oddly I would have swore I tried an earlier version of cuda on this card. O well I must have been thinking of another machine. 

In short, Damn.

---

### Post by cascade9 on 2010-06-16
Its only 'damn' if you let the magic smoke out IMO ;)

---

### Post by Strid on 2011-02-08
Maybe this post will help others. However, when I installed CUDA on ubuntu 10.04 Server, there was no /dev/nvidia* file. So I had to construct one manually and load it. I call it cuda-start.sh and load it at boot time.

After this fix, CUDA was able to see my graphics card. This worked with both a 8400GS and 210

cuda-start.sh:
```

#!/bin/bash

/sbin/modprobe nvidia 

if [ "$?" -eq 0 ]; then 
  # Count the number of NVIDIA controllers found. 
  NVDEVS=`lspci | grep -i NVIDIA` 
  N3D=`echo "$NVDEVS" | grep "3D controller" | wc -l` 
  NVGA=`echo "$NVDEVS" | grep "VGA compatible controller" | wc -l` 

  N=`expr $N3D + $NVGA - 1` 
  for i in `seq 0 $N`; do 
    mknod -m 666 /dev/nvidia$i c 195 $i 
  done 

  mknod -m 666 /dev/nvidiactl c 195 255 

else 
  exit 1 
fi

```

---

