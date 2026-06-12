---
title: "OpenCL on Intel"
date: 2010-04-07
forum: Programming Talk
---

### Post by Dougie187 on 2010-04-07
Hey Guys,

So I have been reading a ton about OpenCL. For those of you who don't know, it basically provides a device agnostic method of programming, so you could code for a GPU or a CPU.

The benefit really comes in from being able to write for a GPU.

Anyways, I got it running on my GPU. Which is an NVIDIA Quadro NVS 140M. My issue comes in that when I try to do 

clGetDeviceIDs(NULL, CL_DEVICE_TYPE_CPU, 1, &cpu, NULL);

I get 0 devices returned, so my Intel Core 2 Duo isn't showing up. I was curious if anyone knows how to make the Core 2 duo work with opencl, under ubuntu.

Anyways, I know this isn't a widely used product yet, but it could be big later. I hope that this at least lets more people know about it so they could use it, but hopefully someone else has ran into this problem too. Thanks!

---

### Post by Dougie187 on 2010-04-07
Not sure how many of you care, but it turns out that intel doesn't have any OpenCL drivers, so I doubt there is any OpenCL support yet, especially for linux.

But it works great for running stuff on Nvidia GPUs. I guess I could just use OpenMP for the CPU stuff, and OpenCL for the GPU stuff.

---

### Post by Dougie187 on 2010-04-08
More developments....

apparently if you install AMD/ATI's stream sdk it supports all CPU's. I haven't tested it, so I'm not sure if it works or not. But thats what I read.

I'll give it a shot later today and let everyone know. That way hopefully someone will be able to use this information.

---

### Post by kahootbot on 2010-04-08
Sorry if I seem to be answering a question with a question, but I'd looked into openCL before a few months back and couldn't find guides or anything and I just assumed it was still in development. My understanding is it's kind of a open approach similar to cuda.. Where did you get started on compiling/running in ubuntu?

---

### Post by checoimg on 2011-02-23
[http://ubuntulife.wordpress.com/2010/10/09/%C2%BFque-nos-vamos-a-encontrar-en-ubuntu-10-10/](http://ubuntulife.wordpress.com/2010/10/09/%C2%BFque-nos-vamos-a-encontrar-en-ubuntu-10-10/)

check this it is on spanish but maybe you can translate it.

---

### Post by M4570D0N on 2011-05-27
I was looking up some info on OpelCL support for Intel and came across this thread, as well as this article. Just thought I would pass it along.

[**Intel Releases OpenCL SDK For Linux**]("http://www.phoronix.com/scan.php?page=news_item&px=OTQzMQ")
> Intel has released an OpenCL Software Development Kit that provides support under Linux. 

The Linux support for the Intel OpenCL SDK is currently in a preview  state and is also available for Microsoft Windows. This SDK currently  supports the Khronos OpenCL 1.1 specification. 

More information on this new Intel SDK can be found in [this Intel Software blog posting]("http://software.intel.com/en-us/blogs/2011/05/09/conformant-intel-opencl-sdk-11-beta-announced-linux-support-available/").

---

### Post by night_fox on 2012-10-17
They only made a 64 bit linux OpenCL. Unfortunately, you really need a 32 bit version to compile WINE with it.

---

