---
title: "can't fix the resolution , help"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by JiMMaR on 2008-10-27
hello people
I'm new to ubuntu , so I may be kinda stupid so please be patience with me

here's what I did and what happened

while I was downloading new applications for ubuntu , I got a notice to update the kernel and I did update that too
after updating the kernel was done (from kernal 2.6.24-19-generic to kernal 2.6.24-21-generic) I got a message asking me if I want to delete the old files or not , and I deleted them , restarted my computer and when I logged into ubunut it said that ubuntu didn't recognize my monitor and asked me to pick my monitor manualy

as that I work on 1280*800 and I have a laptop , so I just picked a random one that has 1280*800 (this was a stupid action , but I did it)

anyway , now what happens is
1- the maximum res I can put my monitor on is 1024*768
2- as that my monitor is a widescreen I get like 2 black lines on both sides (like the ones appears if you watch a video made for normal monitors on a widescreen ones)
3- compiz doesn't work or actually seems there is a problem with my graphics card too

my laptop is:
dell inspiron 1520
dual core2due 2.4
2GB ram
Nvidia 8600M GT

and I run on dual boot with vista

here's how the boot menu looks like

> Ubuntu 8.04.1, kernal 2.6.24-21-generic
ubuntu 8.04.1, kernal 2.6.24-21-generic(recovery mode)
Ubuntu 8.04.1, kernal 2.6.24-19-generic
ubuntu 8.04.1, kernal 2.6.24-19-generic(recovery mode)
Ubuntu 8.04.1, memtest86+
other operating systems
Microsoft Windows Vista (long horn)
Mircosoft Windows XP Professional

(I dunno why I have xp in there , maybe because I tried to install it , but didn't work but that's not the point anyway)

here's what I tried to do:
with a help of a friend , he managed to figure that the problem is from my graphic card driver , so he told me to download a recent one and install it

here's what I get when trying to install it

> 
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

so , help please :lolflag:

---

### Post by LowSky on 2008-10-27
lets make this easy...
boot to ubuntu 8.04.1, kernal 2.6.24-21-generic(recovery mode)
choose to fix Xorg
then when ubutnu is up and running (hopefully) go to add/remove, download EnvyNG
use it to install Nvidia drivers
restart all should be fine

---

### Post by JiMMaR on 2008-10-28
did that , resolution got fixed thanx

I downloaded EnvyNG , and used it to install the drivers , after that was done I had to restart when I logged into ubuntu again , it said the same thing that ubuntu couldn't detect my monitor

I just didn't chose any monitor , restarted and fixed Xorg again , booted again resolution got fixed , no visual effects again

I booted into Ubuntu 8.04.1, kernal 2.6.24-19-generic and it was working properly
any idea how to fix kernal 2.6.24-21 or to remove it and just live with 19 ?

---

