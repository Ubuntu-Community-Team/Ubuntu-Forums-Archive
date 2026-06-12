---
title: "Linux Kernel Customization"
date: 2010-06-04
forum: Programming Talk
---

### Post by hawaiian1der on 2010-06-04
A friend an I are going to make our own Linux distribution for the heck of it. I wanted to know how to go at hacking the kernel and what kinds of things should be hacked at. I have looked on the forums and the Internet, but I cannot find anything on this subject that fits my needs :/

***I am not really sure if this is where this thread needs to go... So if it isn't, I'm sorry.***

---

### Post by hawaiian1der on 2010-06-04
Can no one answer this or something? There are 45 views and no answers :/

---

### Post by ibuclaw on 2010-06-04
And just what distribution is going to be the base of your remix?

Or are you going to try LFS.


IMO, before you start thinking about which kernel to use, you need to start thinking about the toolchain that you will use to build all software, including the kernel itself. ;)

---

### Post by hawaiian1der on 2010-06-04
We are going to use good 'ol Ubuntu! The server edition for the bare-bones feel ;) I'm pretty sure that Jesse knows what the tool chain and things mean, but I don't and hes not on right now. Can you explain the different type of kernels and tool chains?

---

### Post by mmix on 2010-06-04
This link is good entry point for linux kernel development.
[http://kernelnewbies.org/](http://kernelnewbies.org/)

---

### Post by hawaiian1der on 2010-06-04
> **mmix said:**
> This link is good entry point for linux kernel development.
[http://kernelnewbies.org/](http://kernelnewbies.org/)

Aside from how to build a kernel that doesn't show a whole lot... Is there anything else?

---

### Post by ibuclaw on 2010-06-04
> **hawaiian1der said:**
> Aside from how to build a kernel that doesn't show a whole lot... Is there anything else?

Oh, if you are just making an Ubuntu derivative, then you might as well look up on [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

In your case, a custom kernel shouldn't be needed, unless you don't want to use linux 2.6.32 in your system, of course...

---

### Post by NathanB on 2010-06-04
First, you will definitely want to read "Linux From Scratch" (LFS) which you can find here:  [http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

Second, see what BLFS has to teach you about packaging:
[http://www.linuxfromscratch.org/blfs/](http://www.linuxfromscratch.org/blfs/)

If any of that looks too ambitious, then look into re-mastering existing distros:

[http://wiki.tinycorelinux.com/tiki-index.php?page=Remastering](http://wiki.tinycorelinux.com/tiki-index.php?page=Remastering)

[http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/RemasteringGuide](http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/RemasteringGuide)

---

### Post by hawaiian1der on 2010-06-04
> **ibuclaw said:**
> And just what distribution is going to be the base of your remix?

Or are you going to try LFS.


IMO, before you start thinking about which kernel to use, you need to start thinking about the toolchain that you will use to build all software, including the kernel itself. ;)

To clarify, what we really are going to do is some how make it completely from scratch, but use the packaging system from Debian/Ubuntu.

---

### Post by hawaiian1der on 2010-06-04
Scratch that! We are going to use LFS, but at the same time implement some things from Ubuntu/Debian.

---

