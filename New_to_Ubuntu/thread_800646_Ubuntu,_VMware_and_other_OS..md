---
title: "Ubuntu, VMware and other OS."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by rptizzle on 2008-05-20
Hello,

I just built a brand new computer and it has a 64-bit AMD processor.

I want to use Linux, but am not confident with Linux yet, that is I am not sure I can do everything in Linux the way I do in Windows.

So my first question is, which is the best OS for a 64-bit machine? Would you install Ubuntu 64-bit or Vista Ultimate? I know XP is not a good option because the 32-bit does not take advantage of all the RAM and 64-bit processor (and XP 64-bit isn't worth it).

I have several VMware images that I'd like to run, so if I end up installing Ubuntu 64-bit, then I am pretty sure I can still run XP and Vista as virtual machines.

If you explain which OS is better for my computer (Vista or Ubuntu), it'd be great if you provided some technical info as well.

Thank you!

- Ricardo

---

### Post by quelx on 2008-05-20
Have a read before you decide on a 64bit OS

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

If your running Ubuntu as strict vmserver get the ubuntu-server iso, it forgoes the GUI and client applications and will leave resources to your virtual machines.

---

### Post by wolfen69 on 2008-05-20
in my biased opinion, i think you should stick with 32bit and dual boot with xp. vista is not all that. unless you are doing serious number crunching, there wont be any noticable advantage to using 64bit. i didnt notice any difference in everyday use. plus it can be a wee bit harder to get some things working correctly.

Here is [Advantages and disadvantages of 64bit]("http://ubuntuforums.org/showthread.php?t=765428") good luck either way.

---

### Post by EXCiD3 on 2008-05-20
Well of course im going to have to recommend Ubuntu for you. 64 bit has great support and only a few apps require a little tweaking to get running on 64 bit because the developers havent started 64bit support yet. If you have windows on your computer you can try install Ubuntu via Wubi. It creates a dual boot with Windows that can be uninstalled via Windows Add/Remove Programs menu in case you decide to stick with windows.

I prefer using Virtualbox for virtualization because it is easier to setup. You might like to try it out.

---

### Post by rptizzle on 2008-05-21
Thank you all, for the input. I'll check the two links that were posted.

Just to clarify, I won't have a problem with running a 64-bit OS versus 32-bit. That is because I have virtual machines that are 32-bit. I want to experiment with 64-bit OS, and my question is only "should Vista or Ubuntu be my native OS?"

Personally, I prefer not to install a bunch of software on my native OS. I also don't use it for browsing as all the spyware an potential viruses that can come from browsing certain sites can compromise the native OS or at least slowdown the machine. With virtual machines I can simply restore them to a previous state: that simple! Or I can even delete them if I wanted to.

Thanks again!

---

### Post by Xiong Chiamiov on 2008-05-21
> **rptizzle said:**
> Thank you all, for the input. I'll check the two links that were posted.

Just to clarify, I won't have a problem with running a 64-bit OS versus 32-bit. That is because I have virtual machines that are 32-bit. I want to experiment with 64-bit OS, and my question is only "should Vista or Ubuntu be my native OS?"

Personally, I prefer not to install a bunch of software on my native OS. I also don't use it for browsing as all the spyware an potential viruses that can come from browsing certain sites can compromise the native OS or at least slowdown the machine. With virtual machines I can simply restore them to a previous state: that simple! Or I can even delete them if I wanted to.

Thanks again!
The question of which OS to use is entirely based upon you, and we don't really know you at all.

If you'd like to continue running everything in a virtual machine like that, then Windows is fine (though personally I'd use a sandbox instead of nested OSs).  However, those reasons you cited for doing so are not applicable in Linux.  The natural speed advantage from not having as much crap as Windows, plus the fact that you're not running two OSs at the same time, could give you quite significant performance boosts.

---

### Post by rptizzle on 2008-05-21
Just wanted you guys to know I decided to install Ubuntu 64 for my native OS and I feel great about this choice.

Because of VMware I can have a virtual Ubuntu 32-bit, virtual XP, virtual Vista, etc. I have plenty of hardware to be able to run several virtual machines at a time. This is very exciting! So I was looking for an OS that is as slimmed-down as possible and I think Ubuntu is the one. Now, if I installed Ubuntu 32-bit it'd defeat the whole purpose of having a 64-bit machine. Besides, more and more software will be released for the 64-bit versions.

Thanks again for the help.

- Ricardo

---

### Post by Xiong Chiamiov on 2008-05-21
I just want to make a note that Ubuntu is by far not a slimmed-down distro.  Compared to Windows, pretty much any flavor of Linux is thin, but Ubuntu is one of the more GUI-heavy ones.  If you really want slim, check out [Damn Small]("http://www.damnsmalllinux.org/"), [DeLi]("http://www.delilinux.org/") or [Puppy]("http://www.puppylinux.org/").

---

### Post by EXCiD3 on 2008-05-21
> **Xiong Chiamiov said:**
> I just want to make a note that Ubuntu is by far not a slimmed-down distro.  Compared to Windows, pretty much any flavor of Linux is thin, but Ubuntu is one of the more GUI-heavy ones.  If you really want slim, check out [Damn Small]("http://www.damnsmalllinux.org/"), [DeLi]("http://www.delilinux.org/") or [Puppy]("http://www.puppylinux.org/").

So very true. I would recommend Arch Linux as it is about as simple as using Ubuntu but it comes with no gui, allowing you to install only what you need, starting with your desktop environment! It is by far my favorite distro and i dont normally like KDE but with KDEmod...its perfect for me.

---

### Post by Living2007 on 2008-05-21
> **rptizzle said:**
> Hello,

I just built a brand new computer and it has a 64-bit AMD processor.

I want to use Linux, but am not confident with Linux yet, that is I am not sure I can do everything in Linux the way I do in Windows.

So my first question is, which is the best OS for a 64-bit machine? Would you install Ubuntu 64-bit or Vista Ultimate? I know XP is not a good option because the 32-bit does not take advantage of all the RAM and 64-bit processor (and XP 64-bit isn't worth it).

I have several VMware images that I'd like to run, so if I end up installing Ubuntu 64-bit, then I am pretty sure I can still run XP and Vista as virtual machines.

If you explain which OS is better for my computer (Vista or Ubuntu), it'd be great if you provided some technical info as well.

Thank you!

- Ricardo
Ubuntu is avalible in a 64-bit version, but i'm not sure which is better.
Xubuntu uses less resources and runs smoothly on 192MB+

---

