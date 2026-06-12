---
title: "Linux kernel 3.0.0-5.6 (rc7) available"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-12
New and possibly the last rc of the kernel 3.0.0 is available from Launchpad (right now building) and soon in Oneiric repos too.
That is however not so exciting:

> 
linux (3.0.0-5.6) oneiric; urgency=low
  [ Tim Gardner ]
  * [Config] CONFIG_RTL8192CU=m
  * Rebase to -rc7
 -- Tim Gardner <email address hidden>   Mon, 11 Jul 2011 22:13:50 +0100

---

### Post by jfernyhough on 2011-07-12
Mainline builds are available:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/)

Ubuntu builds are here (or soon will be):
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-5.6](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-5.6)

---

### Post by xeizo on 2011-07-12
Well, somewhat exciting, I haven't tested the official build yet(on my way) but I built one myself and the keyboard, mouse and sound issues are gone!

Seems they where kernel-related anyway.

BUT, nvidia-current doesn't work anymore, it builds "ok" but it fails to start. Starts fine on the older 3.0.0-4-kernel. Which still has the keyboard, mouse and sound issues even after todays updates and removal of udev.

I'll see in a moment how todays build works.

---

### Post by xeizo on 2011-07-12
No, nvidia-current still doesn't work!

So the last kernel with working Nvidia was 3.0.0-4, and this new rc7-kernel has working keyboard, mouse and sound. But no Nvidia. Never can one be fully happy ;)

I hope there will soon be a kernel with _everything_ working, mabe already the "Ubuntu build" still compiling  :)

---

### Post by Harry33 on 2011-07-12
> **xeizo said:**
> Well, somewhat exciting, I haven't tested the official build yet(on my way) but I built one myself and the keyboard, mouse and sound issues are gone!

Seems they where kernel-related anyway.

BUT, nvidia-current doesn't work anymore, it builds "ok" but it fails to start. Starts fine on the older 3.0.0-4-kernel. Which still has the keyboard, mouse and sound issues even after todays updates and removal of udev.

I'll see in a moment how todays build works.

No it is not a kernel issue.
The latest udev (172-0ubuntu2) and initramfs-tools (0.99ubuntu1) updates have fixed the "no mouse - no keyboard" issue.

---

### Post by Harry33 on 2011-07-12
> **xeizo said:**
> No, nvidia-current still doesn't work!
So the last kernel with working Nvidia was 3.0.0-4, and this new rc7-kernel has working keyboard, mouse and sound. But no Nvidia. Never can one be fully happy ;)
I hope there will soon be a kernel with _everything_ working, mabe already the "Ubuntu build" still compiling  :)

Nvidia-current from Oneiric repos (275.09.07-0ubuntu4) works well and OK with the 3.0.0 rc7 kernel from Launchpad. Kernel is built now and the state is new. So you can download it directly from Launchpad (not yet in Oneiric repos).

Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-5.6](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-5.6)

---

### Post by xeizo on 2011-07-12
> **Harry33 said:**
> Nvidia-current from Oneiric repos (275.09.07-0ubuntu4) works well and OK with the 3.0.0 rc7 kernel from Launchpad. Kernel is built now and the state is new. So you can download it directly from Launchpad (not yet in Oneiric repos).

Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-5.6](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-5.6)

It does. Sort of. Something with Plymouth/Nouveau have been borked instead, I can't get Nvidia to start because Nouveau starts to totally own everything before Nvidia is about to start.
It's also impossible to install from Nvidias source because even at the commandline @ safe boot Nvidia thinks Nouveau is running.

BUT, there is nothing wrong with the Nvidia-driver itself, because I CAN get it to start, but the only way to do that is to do a safe boot to the commandline and issue sudo telinit 3(can't be done during normal boot) in which case Xorg automagically starts up with the Nvidia-driver!
Sound and keyboard/mouse is working, of course. But it is a very strange way to boot ...

That is with the new 3.0.0-5 kernel, with the older 3.0.0-4 kernel and exactly the same config Nvidia starts normally during normal boot. But with the sound/mouse/keyboard-issues of course.

The other kernels I tried inbetween seemed to have various stages of progress towards the new borkage ie fixing old faults but not fully working.

---

### Post by Harry33 on 2011-07-12
> **xeizo said:**
> It does. Sort of. Something with Plymouth/Nouveau have been borked instead, I can't get Nvidia to start because Nouveau starts to totally own everything before Nvidia is about to start.
It's also impossible to install from Nvidias source because even at the commandline @ safe boot Nvidia thinks Nouveau is running.

BUT, there is nothing wrong with the Nvidia-driver itself, because I CAN get it to start, but the only way to do that is to do a safe boot to the commandline and issue sudo telinit 3(can't be done during normal boot) in which case Xorg automagically starts up with the Nvidia-driver!
Sound and keyboard/mouse is working, of course. But it is a very strange way to boot ...

That is with the new 3.0.0-5 kernel, with the older 3.0.0-4 kernel and exactly the same config Nvidia starts normally during normal boot. But with the sound/mouse/keyboard-issues of course.

The other kernels I tried inbetween seemed to have various stages of progress towards the new borkage ie fixing old faults but not fully working.

Have you upgraded to udev (172-0ubuntu2) and initramfs-tools (0.99ubuntu1)?
Check also that you do NOT have the directory /run/udev in your setup (if it is an empty one and you have not updated udev and initramfs).

---

### Post by xeizo on 2011-07-12
> **Harry33 said:**
> Have you upgraded to udev (172-0ubuntu2) and initramfs-tools (0.99ubuntu1)?
Check also that you do NOT have the directory /run/udev in your setup.

I have. And I did. But when I look so has /run/udev popped back in ... I removed it again, hopefully that was the trick .. we'll see!

---

### Post by cariboo on 2011-07-12
WHen you installed nvidia-current, it should have blacklisted the nouveau driver. Check to see if you have nvidia-graphics-drivers.conf in /etc/modprobe.d

the contents of my file are:

```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
```

---

### Post by Harry33 on 2011-07-13
> **xeizo said:**
> I have. And I did. But when I look so has /run/udev popped back in ... I removed it again, hopefully that was the trick .. we'll see!

If you have upgraded to the new udev and initramfs-tools, you will have these directories (not empty anymore):
/run/initramfs
/run/mount
/run/udev
Do not delete them!

---

### Post by dino99 on 2011-07-13
got lot of broken links into /run/udev/watch/ & /firmware-missing/

---

### Post by Harry33 on 2011-07-13
> **dino99 said:**
> got lot of broken links into /run/udev/watch/ & /firmware-missing/

Hmm, so do I, in /run/udev/watch.
All of them (26) are broken.

---

### Post by dino99 on 2011-07-13
hm, after have removed the previous broken ones, i still got new broken, and /udev/links/*/ files are 0 byte, strange

might need to report, but dont know which to blame.

---

### Post by Harry33 on 2011-07-13
> **dino99 said:**
> hm, after have removed the previous broken ones, i still got new broken, and /udev/links/*/ files are 0 byte, strange

might need to report, but dont know which to blame.

I think it is the new udev (172-0ubuntu2).

---

### Post by dino99 on 2011-07-13
Looks like nothing have been set to use it (dont have side effect on my end, so i'll wait)

---

### Post by Harry33 on 2011-07-13
> **dino99 said:**
> Looks like nothing have been set to use it (dont have side effect on my end, so i'll wait)

Yes that seems to be true. No problems here either.

---

### Post by Sworddragon on 2011-07-13
I get the message about the missing firmware too and the nvidia module can't be loaded anymore for 2 days. I have reinstalled nvidia-current but this hasn't helped. I'm running now xserver-xorg-video-nouveau and installed libgl1-mesa-dri-experimental for 3D accelaration support. But all games are saying that they can't load the GLX module.

---

### Post by petersonja on 2011-07-14
My webcam doesn't work with this new (3.0) kernel anymore. :(

---

