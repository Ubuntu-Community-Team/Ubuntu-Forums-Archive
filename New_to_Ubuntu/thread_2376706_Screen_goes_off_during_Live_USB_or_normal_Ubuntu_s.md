---
title: "Screen goes off during Live USB or normal Ubuntu startup"
date: 2017-11-05
forum: New to Ubuntu
---

### Post by pathum1 on 2017-11-05
My specs:
Core i5 CPU, AMD R9 380, 8 Gigs of RAM and Three SATA Hard drives (non SSD) out of which on one i have W10 installed.
BIOS is setup to boot in Legacy mode. Secure boot is off.

So my issue is that i've tried quite a few linux distros now, Fedora 25, Solus with Gnome, and Ubuntu 16.04/17.10. The Live USB of any of these distros boot up to the menu where you got to select whether you will install that distro or use the live system. 
Upon selection (either live system or installation of that distro) it ends up in my screen going off and i hear a system fan racing.
The nomodeset parameter in the boot options cancels this and i am able to boot into a live system or go ahead with the installation.
After installation all of the above distro's end up in the screen turning off and after about 30 secs the screen comes back on but without anything in it.
Again if i add the nomodeset option to grub i am able to boot but of course the performance seems very lackluster and I feel as if the GPU drive is not installed properly or functioning as expected.

I have tried installing the AMDgpu-pro driver in Ubuntu 16.04 and 17.10 and it has never booted beyond grub unless i use the nomodeset parameter. ( i presume that this prevents any special gpu driver being loaded)

I'm an avid DOTA 2 player and would just love to get DOTA 2 running on linux. I've attached a photo of the errors I have come across.

Any help in getting this rectified would be much appreciated guys.

---

