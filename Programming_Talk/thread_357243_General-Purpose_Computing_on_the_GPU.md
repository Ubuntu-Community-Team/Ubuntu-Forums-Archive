---
title: "General-Purpose Computing on the GPU"
date: 2007-02-09
forum: Programming Talk
---

### Post by Houman on 2007-02-09
hi there;
I just wanted to start a thread on this very hot topic of General-Purpose Computing on Graphics Processing Units. For those who don't know this is basically using the SIMD architecture of the GPU and its pipelined architecture to do non graphics processing on the GPU. Its a very hot topic these days. In fact today I was at a presentation in school where someone claimed he implemented his algorithm on the GPU and got a 26000x performance increase (well, that sounds unbelievable).

I was wondering if people who know more could shed some more light on this. Even best would be if someone wrote a small tutorial and showed how to implement something simple, like matrix multiplication on the GPU and showed the performance increase.

I dont know much about this, but since I heard the 26000x faster figure I have been frantically going through my undergraduate comp architecture books to see if thats at all possible, what do you think?


regards

Houman

---

### Post by 23meg on 2007-02-09
A couple of years ago, a project called BionicFX was aiming to utilize the GPU to do audio processing. It seems most GPUs can do pretty good FFT, but I don't know what happened to the project; their website seems to be down, and I never saw any working product from them, so the vaporware probability is high.

---

### Post by Quikee on 2007-02-09
Look [here]("http://www.gpgpu.org/") for a simple example or how-to start with GPGPU programming. [Sh]("http://libsh.org/") and [brook]("http://graphics.stanford.edu/projects/brookgpu/") are 2 "meta" programming languages designed for programming on GPU. 

The problem with using GPU as a more general purpose unit, you have to "hack" OpenGL (or DirectX) to achieve computation. This is why it is not as effective as it could be, if you would talk to GPU directly.

---

### Post by hod139 on 2007-02-09
UNC's gamma group has been doing more and more on the GPU.  There website is [http://gamma.cs.unc.edu/hardware/](http://gamma.cs.unc.edu/hardware/)

---

### Post by LordHunter317 on 2007-02-09
It's hardly general-purpose programming.  Only things that are amenable to stream-based programming (i.e., signal processing, mostly) will run well on a GPU.

---

### Post by 23meg on 2007-02-09
> **LordHunter317 said:**
> It's hardly general-purpose programming.  Only things that are amenable to stream-based programming (i.e., signal processing, mostly) will run well on a GPU.Non-graphical may be a better term.

---

### Post by Houman on 2007-02-09
thank you all for all the links, I am checking them out. Also I heard about this book that might be of interest: Gpu Gems [http://developer.nvidia.com/object/gpu_gems_2_home.html](http://developer.nvidia.com/object/gpu_gems_2_home.html)

Also 23megs, what LordHunter says is correct, stream processing applications are merely a subset of non graphical applications, so not every non graphical application will benefit by being implemented in the GPU. Also the presentation that I went to also was a signal processing related application.

Also it seems with the possible performance gains possible by implementing these stream processing algorithms by GPU, I would be an idiot not to use it! I wonder why there arnt more libraries that utilize the GPU. The link that hod139 provided had some interesting examples like FFT implementations on teh GPU, but im surprised that there arnt more such libraries (and you cant say because not every computer has a dedicated GPU, because most have).

regards and thanks for all the feedback

Houman

---

### Post by LordHunter317 on 2007-02-09
Because GPU hardware has only become general purpose enough to support this very recently.  They're becoming closer to DSPs instead of the very specialized units they once were.

---

### Post by lnostdal on 2007-02-09
using gpus or expansion cards for general programming is a cool idea - even if not quite there yet...  

maybe having [http://en.wikipedia.org/wiki/Cell_microprocessor](http://en.wikipedia.org/wiki/Cell_microprocessor) available as expansion-cards would be cool (i see PCI Express mentioned there)

..or just remove the cpu and ram from the motherboard and only have an insane fast bus there .. then put cpu(s), ram, and all the other stuff on "standard"(?) expansion boards .. or if possible do something like USB where you can just keep expanding regardless of the original number of USB-ports

..just wishful thinking, and not really related to what is generally available now :)

---

### Post by Houman on 2007-02-09
well, there are alot of people who buy the PS3 these days just so they can do programming with the cell processors, and I have heard some amazing results from their performance comparisons.

---

### Post by hod139 on 2007-02-20
From [Arstechnica:]("http://arstechnica.com/news.ars/post/20070219-8878.html")
Today, NVIDIA announced the release of beta versions of the SDK and C compiler for their [Compute Unified Device Architecture (CUDA)]("http://www.developer.nvidia.com/object/cuda.html") technology. The C compiler includes a set of C language extensions that will enable developers to write C code that targets NVIDIA's GPUs directly. These extensions are supported by software libraries and a special CUDA driver that exposes the GPU to the OS and applications as a math coprocessor.

---

