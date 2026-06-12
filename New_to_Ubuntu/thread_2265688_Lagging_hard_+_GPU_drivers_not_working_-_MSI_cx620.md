---
title: "Lagging hard + GPU drivers not working - MSI cx620 (i3 version)"
date: 2015-02-17
forum: New to Ubuntu
---

### Post by Humunuk on 2015-02-17
Hello!

Running Ubuntu 14.10 (dual boot to windows 7)
Specs:
Processor: i3-330m
RAM: 4gb
Graphics: ATI Mobility Radeon HD 5470

For the graphics drivers to get working properly i have given up, as far as I have understood the best solution would be to uninstall drivers for onboard Intel graphics and force to only use AMD dedicated card, but how can I do it? (Tutorials/instructions I have found only point different ways to install fglrx and xserver together)

AM I right that xserer-xorg deal with the onboard intel graphics chip, so that when I need to only use amd HD i should clean uninstall xserver and then install fglrx?

The other thing is, everything in Ubuntu is lagging really really really hard, I even installed LXDE to take the load off, but it didnt help.
I understand my computer is old, but still shouldnt it run properly and smooth or is the problem here that I dont have properly working graphics?

---

### Post by grahammechanical on 2015-02-17
> [COLOR=#000000]AM I right that xserer-xorg deal with the onboard intel graphics chip, [/COLOR]

No. X-server is the X windowing system. X.org is the organisation that maintains and develops the X-sever which in turn renders on the screen what we see on the screen. Without the X-server all we would have is the default video capabilities of the motherboard. We would not have a graphical user interface.

You have hybrid graphics and the problem for all Linux users whether the hybrid system is a combination of Intel and AMD/ATI or a combination of Intel and Nvidia is that the manufacturers do not give the same priority to providing video drivers for these machines as they do for Microsoft Windows . After all, it is Windows that they pre-install. So, things have to work well. But they do not pre-install Linux. So, where is the profit for them in providing free Linux drivers that work as well as their Windows drivers?

The proprietary video driver for AMD/ATI graphic adapters is called fglrx. That is why the advice centers around installing the fglrx driver.

> 
[LIST]
[*]
[LIST]
[*]NOTE: you can easily switch between GPUs using AMD's control panel.
[/LIST]
[/LIST]

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

I have no experience with hybrid graphics but I know that when there is a mess up with Nvidia proprietary drivers then Ubuntu will load using a kind of fallback open source video driver called llvmpipe. It tries to approximate 3D rendering on machines that have graphic adapters that cannot do hardware accelerated 3D rendering. When llvmpipe is running a graphic adapter that can do 3D then the visual effect definitely lags. This is my experience. You could be experiencing a similar situation.

> [COLOR=#000000][FONT=Open Sans]LLVMpipe isn't meant to replace GPUs / hardware drivers by any means, but is simply a fallback in cases where there is no hardware acceleration available due to hardware issues or driver problems. With a modern processor, LLVMpipe tends to at least be "good enough" to handle a composited Linux desktop, light WebGL content, and other very basic graphics tasks. LLVMpipe is also useful to driver developers for testing out new code and debugging problems along a hardware-independent driver.[/FONT][/COLOR]


[http://www.phoronix.com/scan.php?page=article&item=mesa_92_9llvmpipe&num=3](http://www.phoronix.com/scan.php?page=article&item=mesa_92_9llvmpipe&num=3)

Regards.

---

### Post by Humunuk on 2015-02-18
I am really thankful for your reply, it explained a lot for me.

But I guess I have to stick to the "urban myths" that became real.

---

