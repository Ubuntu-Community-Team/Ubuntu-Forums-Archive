---
title: "Assembler opcodes for Nvidia GPU"
date: 2008-01-24
forum: Programming Talk
---

### Post by Royall on 2008-01-24
I want to write some assembler code that directly accesses the GPU so that I can make it do something useful besides graphics.
 Anyone done this before or have any resources to direct me to?](*,)

---

### Post by Wybiral on 2008-01-24
For nvidia, I believe [CUDA]("http://www.nvidia.com/object/cuda_get.html") is what you're looking for. Also see [wikipedia]("http://en.wikipedia.org/wiki/CUDA"). Aside from that, I don't know of any other way to access the GPU directly.

---

### Post by Royall on 2008-01-24
Yeah, I looked at CUDA which allows C programs to access the GPU, but it only works on 8000 series. I may have access to some Quadros that can do it soon, but I'd rather be able to do some stuff on my 7800. I feel like there must be a way, but I'm not sure if it  actually exists.

---

### Post by Anthon berg on 2008-02-14
> **Royall said:**
> Yeah, I looked at CUDA which allows C programs to access the GPU, but it only works on 8000 series.

Just to be sure: CUDA is actually a "C-like" language that is compiled by NVidia's own compiler to generate GPU-native code. This GPU code is then accessible through standard library calls.

I have a tiny bit of CUDA experience, and I'd suggest checking out the GPGPU page at Wikipedia to try to find a nice GPGPU language to write in. I doubt anybody would have a good time writing in native assembly for the GPU, so I'd recommend writing the GPU code in a GPU language.

Then you'd compile the GPU code to a binary with C-style shared library + header file, and try to hack some assembly code into using the shared lib.

If you'd really like to write in GPU assembler, I'd still advise you to check the GPGPU page at Wikipedia, selecting a sensible language and having a look at its GPU-assembly innards.

---

