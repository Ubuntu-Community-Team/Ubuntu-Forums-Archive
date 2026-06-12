---
title: "Interested in Ubuntu Studio, I have a few questions"
date: 2019-11-29
forum: New to Ubuntu
---

### Post by disabled20191124 on 2019-11-29
Next January 14th, 2020, Microsoft will end their support for Windows 7, since buying Windows 10 is out of the question for me, I consider using Ubuntu Studio in the future.

I made some searches about it but I cannot find an answer to the following questions:
 
[LIST=1]
[*]does Ubuntu Studio support "discrete" GPUs? 
[*]how problematic would be installing it before installing the necessary proprietary drivers for my GPU if discrete GPUs are not natively supported? 
[/LIST]
My GPU is an [Nvidia GeForce GTX 970M]("https://www.geforce.com/hardware/notebook-gpus/geforce-gtx-970m").

 Thank you for reading this.

---

### Post by TheFu on 2019-11-30
[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)

Beware that newer isn't always better. Any hardware that was released to the world less than 1 yr ago can have issues until the vendor or some volunteer does the work to get it working in the kernel. The bleeding edge is called that for a reason.  It can be painful to have very new stuff.  Other times, new stuff "just works."  As for GPU models, I want to be at least 1 yr behind and only run the LTS release, never non-LTS.

"discrete GPUs" have been supported by Linux since the early 1990s.

The best advice I have for whether any specific computer, especially a laptop, will work, is to google with the model name, number, and install ubuntu 18.04.  For laptops, any issues or tricks to get installed or use specific hardware that other people have discovered will usually have lots of blog entries and ubuntuforum posts.  

For desktops, each part should be researched if there is any concern.  The motherboard, GPU, storage controller, ether controller, wifi chips, anything extra that might be unusual, like an extra NIC or extra HBA and especially check printers, scanners for drivers and compatibility.  Certain vendors which do a great job with Windows, completely ignore Linux.  

About the last 10 yrs, all my systems have just worked and I didn't need to do anything funny to get Ubuntu installed or working. OTOH, my new-to-me laptop has a fingerprint reader for which there aren't any Linux drivers and there never will be any made.  I've thrown away a scanner and a few printers for lack of Linux support.  My photo and slide scanner only has drivers for WinXP - nothing later. I haven't looked for Linux support, but have my doubts.  I have a WinXP virtual machine somewhere just for using that device.

---

### Post by CatKiller on 2019-12-01
> **disabled20191124 said:**
> My GPU is an [Nvidia GeForce GTX 970M]("https://www.geforce.com/hardware/notebook-gpus/geforce-gtx-970m").

Optimus setups (laptops with both Intel and Nvidia graphics) can be a pain. One or the other has been fine for ages, but switching between them is sometimes awkward depending on the choices that the laptop manufacturer made. It's getting easier, though.

> Ubuntu Studio

All of the different Ubuntu flavours have the same stuff underneath, they just differ by the desktop environment and default applications that are installed. They all use the same repositories so you can install whichever applications you want into whichever flavour. Ubuntu Studio's main advantage is that it comes with the lowlatency kernel and a bunch of audio manipulation applications already installed, which saves you the step of downloading them afterwards. If your machine is just for general computing and you aren't going to take advantage of those then you might prefer a different flavour.

---

