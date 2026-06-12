---
title: "glx not working on 12.04"
date: 2013-06-03
forum: New to Ubuntu
---

### Post by jweiner on 2013-06-03
Dear Readers:

Two weeks ago I installed ubuntu 12.04. I have some little experience with linux but am completely new to the ubuntu world.  A numerical simulation program that I use requires graphics acceleration via glx so the first thing I tried after installation was the commad "glxgears", a little graphical test window for the presence of glx.  It appeared to be working fine and so was my graphics-intensive program.  About a week later, after updating all packages, any command involving glx generates the following error...

X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request: 153 (GLX)
Minor opcode of faled request: 19 (X_GLXQeryServerString)
Serial number of failed request: 12
Current serial number in output stream: 12

I tried looking in the Xorg log with, less /var/log/Xorg.0.log|grep "gl"
The result was,  Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
So it appears that the glx library gets loaded.

I then tried looking for an "error" string in the same log with less /var/log/Xorg.0.log|grep "error"
The result was (EE) GLX error: Can not get required symbols.

I have no idea what this means or what to do about it.  Can somebody give me hand?

---

### Post by jweiner on 2013-06-04
This problem, at least for the moment, seems to be solved.  According to a reply to a bug report, there was a suggestion to use a commad, sudo apt-get purge fglrx.  Apparently fglrx is a driver for certain AMD/ATI graphics cards.  I don't have such a graphics card, but I tried the command anyway.  After rebooting, everything appears to be operating normally.  I would be grateful to anyone that explain why purging a graphics card driver resulted in freeing glx to function normally.

---

### Post by gordintoronto on 2013-06-04
What video card is in the computer? Did you install an "Additional Driver"?

---

### Post by jweiner on 2013-06-05
There is no separate video card in the hardware.  That is, I did not install a separate card in the PCIe slots.  I did not software-install "Additional Driver" intentionally, but maybe I did inadvertantly and did not realize it when I was playing around with installing packages with apt-get.  

Actually I don't understand how graphics "acceleration" like glx works when there is no apparent separate graphical processing unit.  Is this function take over by the cpu?  Is glx somehow implemented in software instead of hardware?  Is there a write-up of graphics implementation somewhere that would help me understand what is going on?

---

### Post by gordintoronto on 2013-06-06
OK, what video adapter is in your computer? If you are not sure, open terminal and enter this command:
lspci

It will produce about 15 lines of output, and one of them will contain the word "VGA", that's your video adapter.

Many recent CPUs have a video adapter in the CPU chip, and some motherboards include a video adapter on-board. In any case, they should show up in lspci.

---

### Post by jweiner on 2013-06-06
The result of lspci (among many other lines of output) is:

VGA Compatible controller:  ASPEED Technology, Inc ASPEED Graphics Family (rev21).

I also tried lspci|grep VGA just to make sure I hadn't missed anything, but I came with the same result.

---

### Post by gordintoronto on 2013-06-06
Wow, that's a new one. Has ASUS gone into the video controller business?

---

### Post by jweiner on 2013-06-07
The processor is Intel Xeon E5-2650 with an LGA2011 form.  This is an 8-core processor that I got for intensive numerical simulation work.  The motherboard is a Gigabyte board so I don't think that ASUS has anything to do with the VGA graphics.

I still don't understand why purging a graphics driver made the problem go away.  I'm glad the problem is gone, but I would be more reassured that it won't reappear if I understood it better.

---

### Post by 3rdalbum on 2013-06-07
When you installed the fglrx package, it took over all 3D graphics. Because you don't have an ATI graphics card, you essentially lost 3D capabilities because the 3D commands were going to a driver that was doing nothing.

When you removed the driver, Ubuntu was free to select the more appropriate preinstalled driver for 3D.

FGLRX does not come preinstalled, you must have inadvertantly installed it at some point.

---

