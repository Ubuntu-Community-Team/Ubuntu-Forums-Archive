---
title: "Installing earlier version of Kernel"
date: 2015-02-22
forum: New to Ubuntu
---

### Post by Gran_Jartin on 2015-02-22
Hi!

Since I'm completely new to this forum, I apologize beforehand if this post turns up in the wrong context - i guess you could call it a hardware or installation problem. I have also searched for answers to my problem, without any luck.

Anyway: I have a Sapphire Edge VS8 barebones computer that worked very well with kernel 3.11.x. It doesn't work at all well with the newer kernels, though. At the moment, I use Fedora, since it's simple to install 3.11.

But since I really prefer Ubuntu, I hope to find a solution to this problem. Is there a (reasonably simple) way to install 3.11 with 14.10 (or 14.04)?

/goran j

---

### Post by grahammechanical on 2015-02-22
Although I use the development release of Ubuntu I have never installed a kernel. I always use the kernel that is delivered by the Kernel Team through update manager. It is more usual to install a kernel that is newer than the one we already have. Anyway, first you need to get the kernel and it needs to be in a .deb package

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.10.11-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11.10.11-saucy/)

Then you need to follow the advice given here

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

Notice this point:

> [COLOR=#333333][FONT=Ubuntu Beta]When this process completes you should have a new entry on your boot menu representing the upstream kernel. This will appear as an entry like this:[/FONT][/COLOR]
Ubuntu Trusty, kernel 3.14.4-031404-generic

With Ubuntu 14.04 and later we find previous kernels in the Advanced Options for Ubuntu sub-menu. As kernel 3.11 is a previous kernel, then I would expect to find it at the bottom of the list in Advanced Options.

If you do not see it there, then run

```
sudo update-grub
```

and see if that kernel is listed in the printout.

Regards.

---

### Post by jacobpratt909 on 2015-02-22
You could try to install an older version of Ubuntu, which (should) include an older version of the kernel, though I think *[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")* would be more help.

---

