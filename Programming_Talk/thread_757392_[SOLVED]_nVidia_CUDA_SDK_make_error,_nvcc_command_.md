---
title: "[SOLVED] nVidia CUDA SDK make error, nvcc command not found"
date: 2008-04-16
forum: Programming Talk
---

### Post by sricketts on 2008-04-16
I am following the instructions here for installing CUDA on linux: [http://developer.download.nvidia.com/compute/cuda/1_1/CUDA_SDK_release_notes_linux.txt](http://developer.download.nvidia.com/compute/cuda/1_1/CUDA_SDK_release_notes_linux.txt)

I am stuck on step 3, trying to run make in the SDK_INSTALL_PATH. The output is

```
sricketts@XXXX:~/gpu/NVIDIA_CUDA_SDK$ sudo make
make[1]: Entering directory `/home/sricketts/gpu/NVIDIA_CUDA_SDK/common'
ar: creating ./../lib/libcutil.a
a - obj/release/bank_checker.cpp_o
a - obj/release/cmd_arg_reader.cpp_o
a - obj/release/cutil.cpp_o
a - obj/release/stopwatch.cpp_o
a - obj/release/stopwatch_linux.cpp_o
a - obj/release/multithreading.cpp_o
make[1]: Leaving directory `/home/sricketts/gpu/NVIDIA_CUDA_SDK/common'
make[1]: Entering directory `/home/sricketts/gpu/NVIDIA_CUDA_SDK/common'
a - obj/release/paramgl.cpp_o
a - obj/release/param.cpp_o
make[1]: Leaving directory `/home/sricketts/gpu/NVIDIA_CUDA_SDK/common'
make -C projects/Mandelbrot/ 
make[1]: Entering directory `/home/sricketts/gpu/NVIDIA_CUDA_SDK/projects/Mandelbrot'
make[1]: nvcc: Command not found
make[1]: *** [obj/release/Mandelbrot_kernel.cu_o] Error 127
make[1]: Leaving directory `/home/sricketts/gpu/NVIDIA_CUDA_SDK/projects/Mandelbrot'
make: *** [projects/Mandelbrot/Makefile.ph_build] Error 2

```

I checked my environment variables (set in ~/.bashrc):
```
sricketts@XXXX:~/gpu/NVIDIA_CUDA_SDK$ echo $PATH
/usr/local/cuda/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
sricketts@XXXX:~/gpu/NVIDIA_CUDA_SDK$ echo $LD_LIBRARY_PATH
/usr/local/cuda/lib:

```

which looks right. I can run nvcc from the command line, so the sanity check passes. The only other help I could find was here:

[http://forums.nvidia.com/index.php?showtopic=48212](http://forums.nvidia.com/index.php?showtopic=48212)

but in this case the problem was fixed by correcting the PATH variable.

Any ideas?

Thanks,
Scott

---

### Post by sricketts on 2008-04-17
Solved the problem. I was running make as sudo, but the path var was set for my user account. I changed the owner/group for the tree, then ran make without sudo:

```

sudo chown sricketts NVIDIA_CUDA_SDK
sudo chgrp sricketts NVIDIA_CUDA_SDK
make clean
make

```

---

