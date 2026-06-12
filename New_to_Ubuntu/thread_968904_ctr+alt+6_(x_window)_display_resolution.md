---
title: "ctr+alt+6 (x window) display resolution"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by newbe2007 on 2008-11-03
Hi,
I just installed for the first time ubuntu 8.10 (ubuntu-8.10-desktop-i386.iso) on windows virtual Pc 2007

I'm trying to install the nvidia drivers for my NVIDIA GeForce 8600 GT but:

1) I can't use the alt+ctrl+F6 (I think you call it xwindow) because the resolution isn't correct! (see pic,this is actually what i see, the crock letters ,My working area is only the top of the screen until the green strips [IMG]http://mathandmore.googlepages.com/ctrl_alt_6.jpg[/IMG])

2)I downloaded the NVIDIA-Linux-x86-177.80-pkg1.run, Is this the right driver ? how to install it ? Do I need to remove the std drivers from the system first ?

Regards,
Newbe

---

### Post by jpkotta on 2008-11-03
I don't know of any virtual machines that do hardware acceleration.  

X usually uses VT 7, which would be ctrl-alt-F7.

It sounds like you got the correct driver installer, but like I said before, it probably won't work in a VM.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by FrostyFlames on 2008-11-03
Virtual machine programs emulate a graphics card. They do NOT allow direct access to your graphics card on your physical machine.

Also, Virtual PC 2007 is basically crap for running anything but Windows. VirtualBox and VMWare are both extreamly well suited for linux guests. Both also have guest additions which I believe Virtual PC does not.

I personally use VirtualBox and find it extremely easy to setup and use.

[http://en.wikipedia.org/wiki/Microsoft_Virtual_PC](http://en.wikipedia.org/wiki/Microsoft_Virtual_PC)

---

