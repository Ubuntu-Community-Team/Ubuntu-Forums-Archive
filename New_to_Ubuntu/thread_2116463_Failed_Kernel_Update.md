---
title: "Failed Kernel Update"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by DarkraiDan on 2013-02-15
I tried updating my Kernel from 3.2.0-37 to the latest 3.8.0 from this website: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/)

I downloaded the i386 header, the all header, and the i386 generic.
I then installed using "sudo dpkg -i" after moving the 3 files to my Home folder. The headers had errors, and the generic installed just fine, so I rebooted. I went to launch the 3.8.0 kernel from the GRUB, but it just sat there on a blank blue screen. I can still boot perfectly fine into my 3.2.0-37 under "Previous Linux Kernels," or something along those lines.

I just want to know how I can remove the updated Kernel and continue using 3.2.0-37.

I'll post any information you need once you ask for it.
Thanks in advance.

---

### Post by The Spectre on 2013-02-15
This should remove the new Kernel...

Run in Terminal
> sudo apt-get purge linux-image-3.8*

---

### Post by The Spectre on 2013-02-15
Also Linux Kernel 3.8.0 is not finished yet and is at the Release Candidate stage.

You might be better off using the latest Final Linux Kernel which is currently at version 3.7.8.

I use the method posted on this Website to update mine...
[http://www.upubuntu.com/2013/02/install-linux-kernel-378-in-ubuntulinux.html](http://www.upubuntu.com/2013/02/install-linux-kernel-378-in-ubuntulinux.html)

I am currently running Linux Kernel 3.7.8 with no problems and it was quick and simple to update using this method.

---

### Post by DuckHook on 2013-02-16
Welcome to the forums.

Don't know where you got the instructions, but it is not a good idea for new users to install using dpkg directly. Best to stick to the high-level tools like apt, synaptic or software center. These tools make sure that all dependencies are met, whereas dpkg does no dependency check. Results are generally unpredictable as you discovered.

You do not say what Ubuntu version you are running. Generally not a good idea to let kernels get ahead of the version they are designed for. The software in a repository is designed for a specific set of kernels and newer kernels may confuse or break certain apps. 12.04 apps are designed for the 3.2.x kernel while 12.10 is designed for the 3.5.x series. Power users do experiment with newer kernels all the time, but they know how to tweak and recover.

---

