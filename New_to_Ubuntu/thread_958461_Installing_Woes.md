---
title: "Installing Woes"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by youcouldbemine on 2008-10-25
So here I am. I just got a new laptop yesterday, and I'm trying to install Ubuntu on it, because although I'm not a total Vista hater, I'd like to have a different option. 

So some background. Its a Toshiba Satellite A305-S6872. 
[specs]("http://explore.toshiba.com/laptops/satellite/A300/A305-S6872")
Its got a Core 2 Duo, 3GB RAM, 250GB HD. I know the wireless won't work out of the box, until i upgrade the kernel, but I can deal with that. 

So I try out a 8.04.1 64bit Live CD. It boots, but once it reaches the desktop, the whole screen was covered in lines, making it so you couldn't see anything at all. 

I reboot with a 8.04 32bit Live CD, and it boots into the 'busy box' screen. I figured that I'd try a wubi install and that did the same thing so I uninstalled that and did some more research. I've looked around for a solution to the busy box error, and I found a tip that said if you put in pci=nomsi, then it might boot. So I tried that with the 32bit, and got an error that read

udevd-event [1627]: run_program: '/sbin/modprobe' abnormal exit

I let this sit, then I got 

[88.182434] squashfs: version 3.3 (2007/10/31) Phillip Lougher. 

So now I'm stuck and I'd really really appreciate some help. If I can't get it to work, then tell me that and I'll tough it out with Vista. If I can, then please tell me how. I've tried to provide as much info as I can, and do as much as my own research as possible, but I'm lost and I'd really appreciate it. 

thanks in advance

---

### Post by Duck2006 on 2008-10-25
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by cantormath on 2008-10-25
do you mean this error?
[http://ubuntuforums.org/showthread.php?t=958413](http://ubuntuforums.org/showthread.php?t=958413)

did you try safe graphics mode?

---

### Post by youcouldbemine on 2008-10-25
> **cantormath said:**
> do you mean this error?
[http://ubuntuforums.org/showthread.php?t=958413](http://ubuntuforums.org/showthread.php?t=958413)

did you try safe graphics mode?

will this work for the 32bit or the 64bit?

---

### Post by youcouldbemine on 2008-10-25
I tried both of these, and the same thing happened both times. :(

---

### Post by youcouldbemine on 2008-10-25
so theres nothing i can do? :confused:

---

