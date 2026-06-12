---
title: "Can anyone explain a little about graphics drivers?"
date: 2020-12-17
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-12-17
Hello all,

So one thing that has so far eluded me is fully understanding graphics drivers in Linux. The things I *do* know are...


[LIST]
[*]I understand what graphics libraries are and the difference between a graphics library implementation and it's API
[*]I get roughly how Direct Rendering Infrastructure works and know it's various components
[*]I know that AMD provide an open source driver that it built into the kernel, as opposed to Nvidia's proprietary drivers
[/LIST]

But I still don't understand some basic things, for instance


[LIST]
[*]are the DRM kernel module and a graphics card driver one and the same (i.e AMDGPU, AMDGPU-PRO, RADV, AMDVLK = DRM kernel modules)?
[*]This slightly conflicts with the above point but do the AMD Vulkan drivers work with the (openGL?) ones, i.e your card can use AMDGPU and RADV at the same time?
[*]can a system have multiple drivers installed and switch between them?
[/LIST]

Also to make things more confusing [this]("https://en.wikipedia.org/wiki/AMDGPU#/media/File:Linux_AMD_graphics_stack.svg") diagram shows the RADV driver actualy being part of Mesa, which might answer my first question. If anyone can expand on this it would be much appreciated, I come across this stuff constantly in the context of gaming on Linux and I honestly cant believe any laymen understand any of it, although maybe my brain just isn't wired that way :D

---

### Post by #&amp;thj^% on 2020-12-17
> **jcdenton1995 said:**
> 
[LIST]
[*]are the DRM kernel module and a graphics card driver one and the same (i.e AMDGPU, AMDGPU-PRO, RADV, AMDVLK = DRM kernel modules)?
[/LIST]


**In a nutshell, No one has ever said Linux is intuitive!**:D

"Graphics driver" can mean any number of things. The way X (the graphical windowing system) works is that there is a central X server, which can load modules ("X drivers") for different hardware. ... "DRM kernel drivers" provide an interface for both.

Compared to OpenGL, Vulkan&#8482; substantially reduces &#8220;API overhead&#8221; &#8211; the background work a CPU does to interpret what a game asks of the hardware &#8211; to do.

> **jcdenton1995 said:**
> 

[LIST]

[*]can a system have multiple drivers installed and switch between them?
[/LIST]



You can NOT install two different drivers on the same OS without overriding or offloading the previously installed version. (I know still a bit vague)
All will become clear over time.
So to add to the confusion, mine is a hybrid Nvidia/Intel. I mostly run it through "Mesa DRI Intel HD Graphics 4600".
When I need the power side I then offload  Intel to the Nvidia chip. "prime-run application"
```
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 
  v: kernel 
  Device-2: NVIDIA GK208M [GeForce GT 730M] driver: nvidia v: 455.45.01 
  Device-3: 8SSC20F26960L1GZ53308AS Integrated Camera type: USB 
  driver: uvcvideo 
  Display: x11 server: X.Org 1.20.10 driver: modesetting,nvidia resolution: 
  1: 1920x1080~60Hz 2: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2) 
  v: 4.5 Mesa 20.3.0 

```

---

### Post by CelticWarrior on 2020-12-17
> [COLOR=#000000]You can NOT install two different drivers on the same OS without overriding or offloading the previously installed version. (I know still a bit vague)[/COLOR]


This is considering different drivers versions or even variants for the same hardware.
There are also many hybrid graphics laptops and desktop where iGPU co-exists with a dGPU so, in this specific configurations different graphics drivers must co-exist but, again, their for different hardware (Intel + Nvidia / AMD + Nvidia).

---

### Post by CatKiller on 2020-12-17
> **jcdenton1995 said:**
> So one thing that has so far eluded me is fully understanding graphics drivers in Linux.

It isn't straightforward.

There are two parts. The part that talks to the hardware is in the kernel. The implementation of the graphics APIs (OpenGL, Vulkan, some others in some cases) that applications talk to is Mesa.

I think you already know that the kernel is monolithic, but that you can load and unload modules as necessary. There are multiple modules for some pieces of hardware, so you can often choose a different module for the same sort of job. 

There are also different implementations of the graphics APIs in Mesa, so you can use one implementation for one task and a different implementation for a different task. 

As an aside, Nvidia's driver is essentially their Windows driver made to work on Linux, so they don't use Mesa, and they don't really use the kernel other than through a shim. Instead, they've reimplemented most of the graphics stack in their own image. Hence it often does its own odd things. 

Then sometimes you have multiple graphics devices - one integrated and one dedicated, usually. So you have the driver for each device loaded, and a means to stuff the data from userspace into one or the other as appropriate. The mechanism for doing that is now called Prime. It works better in some configurations than others.

---

### Post by jcdenton1995 on 2020-12-18
> **CatKiller said:**
> There are also different implementations of the graphics APIs in Mesa, so you can use one implementation for one task and a different implementation for a different task.

When you say Mesa contains different implementations of the APIs, do you mean this as in it contains an implementation for each of OpenGL, Vulkan, Direct 3D 9 etc., or do you mean it contains different implementations of the same API, (e.g more than one OpenGL implementation).

My understanding currently is that Mesa contains implementations of a number of different APIs, not just OpenGL and Vulkan?

---

### Post by CatKiller on 2020-12-18
> **jcdenton1995 said:**
> When you say Mesa contains different implementations of the APIs, do you mean this as in it contains an implementation for each of OpenGL, Vulkan, Direct 3D 9 etc., or do you mean it contains different implementations of the same API, (e.g more than one OpenGL implementation). 

Both. 

> My understanding currently is that Mesa contains implementations of a number of different APIs, not just OpenGL and Vulkan?

Yep.

---

### Post by jcdenton1995 on 2020-12-18
> **1fallen said:**
> **In a nutshell, No one has ever said Linux is intuitive!**:D

"Graphics driver" can mean any number of things. The way X (the graphical windowing system) works is that there is a central X server, which can load modules ("X drivers") for different hardware. ... "DRM kernel drivers" provide an interface for both.

Compared to OpenGL, Vulkan&#8482; substantially reduces &#8220;API overhead&#8221; &#8211; the background work a CPU does to interpret what a game asks of the hardware &#8211; to do.



You can NOT install two different drivers on the same OS without overriding or offloading the previously installed version. (I know still a bit vague)
All will become clear over time.
So to add to the confusion, mine is a hybrid Nvidia/Intel. I mostly run it through "Mesa DRI Intel HD Graphics 4600".
When I need the power side I then offload  Intel to the Nvidia chip. "prime-run application"
```
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 
  v: kernel 
  Device-2: NVIDIA GK208M [GeForce GT 730M] driver: nvidia v: 455.45.01 
  Device-3: 8SSC20F26960L1GZ53308AS Integrated Camera type: USB 
  driver: uvcvideo 
  Display: x11 server: X.Org 1.20.10 driver: modesetting,nvidia resolution: 
  1: 1920x1080~60Hz 2: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4600 (HSW GT2) 
  v: 4.5 Mesa 20.3.0 

```

I have a similar situation, with having an AMD APU but also a discrete graphics card. I generally just plug my monitor into the card. So the "Mesa DRI Intel HD Graphics 4600", my understanding is that is the a userspace driver that's part of Mesa, but the iGPU will have it's own kernel module that the userspace driver interfaces with via 'libdrm_intel_somethingorother' on your machine? 

If I look under my '/usr/lib/x86_64-linux-gnu/' I can find '../libdrm_amdgpu.so.1.0.0'. And if I look under '/usr/lib/x86_64-linux-gnu/dri/' then I can find '../radeonsi_dri.so'. so I *think *that the former is the library used to interface with the amdgpu kernel module, and the latter is the hardware specific userspace driver that is part of Mesa that acts a middleman between the hardware agnostic portion of Mesa, and the libdrm*/amdgpu kernel module/GPU side of the stack.

If that makes sense, it seems to [according to this diagram]("https://en.wikipedia.org/wiki/AMDGPU#/media/File:Linux_AMD_graphics_stack.svg")...

Edit: I actually have two versions of '/usr/lib/x86_64-linux-gnu/libdrm_amdgpu.so*', one with the suffix '.1.0.0' and one that is simply siffixed '.1'. I'm assuming they are the same thing just installed by two different packages?

---

### Post by jcdenton1995 on 2020-12-18
> **CatKiller said:**
> Both.

Wow, how confusing! so one final question if I may, are these different versions of the same API left in there for compatibility reasons? or are they different versions as in the implementations of, for instance OpenGL, that are meant for different tasks? Like I know there is one for mobile graphics, and another for rendering web content I believe? that sort of thing anyway.

---

### Post by CatKiller on 2020-12-18
> **jcdenton1995 said:**
> Wow, how confusing! so one final question if I may, are these different versions of the same API left in there for compatibility reasons? or are they different versions as in the implementations of, for instance OpenGL, that are meant for different tasks? Like I know there is one for mobile graphics, and another for rendering web content I believe? that sort of thing anyway.

So, as an example, there are several software implementations - llvmpipe, swrast, and something else, I think - so that things that need support can get it even when hardware acceleration isn't available. It's easier to add a new one when you have a different approach, and then remove the old one when it turns out that it isn't being used any more. There's a lot of code sharing so, other than new user confusion, there isn't that much overhead to having lots. 

I'm on Nvidia's stack, so I don't know all the details of Mesa. It's just what I've picked up by osmosis.

---

