---
title: "replacing windows with Ubuntu"
date: 2015-07-29
forum: New to Ubuntu
---

### Post by romello6543 on 2015-07-29
Hello,
I would like to replace my Windows 8.1 OS with Ubuntu, but I would like to  implement Kernel Virtual Machine. So I would like Ubuntu to be my host box and I would like to virtualize Windows 10 ( when i comes out) and any other Operating systems. 
-There are so many different distros of Ubuntu, which one should I use for this implementation?

Thanks

---

### Post by NathanRodriguez on 2015-07-29
Since virtualization demands performance I would go with a lightweight distribution like Xubuntu or Lubuntu.

---

### Post by euphoria42 on 2015-07-29
Any of the flavors of Ubuntu will of course work for this, the only difference between all of them is the desktop environments and the pre-installed programs. So pick the variant that you feel is the best for you. Lubuntu, Xubuntu, Ubuntu MATE, and Kubuntu will probably feel the most familiar if you are used to Windows. That said, your choice may also depend on how good your PC is. Kubuntu is arguably the most resource intensive variant due to the KDE desktop environment which features lots of "eyecandy." So with all that in mind, pick the flavor that you like the most. I have a pretty beefy PC that could run Kubuntu fine, but I opt to use Ubuntu GNOME or Xubuntu because i enjoy their respective desktop environments more.

---

### Post by yancek on 2015-07-29
Whether you would need a lighter version of Ubuntu depends pretty much on the hardware.  If you have an older machine, Lubuntu, Xubuntu or others may be better.  You should be able to use Virtual software with any.

---

### Post by steve_mc on 2015-07-29
I replaced windows 8.1 with ubuntu 15.04 about a month ago.  I quickly realized that i wanted to run a virtual machine to support some programs
that would not run correctly in ubuntu. My pc has 4 gigs of RAM. Running windows 8.1 within Virtual Box on the unity desktop performed ok, but it
performs much better running the less resource intensive LXDE desktop. Currently i am running Virtual box with windows 8.1 playing a java game. Using the lxde desktop, Firefox and terminal open. The results of the free -m command show that i have 1101 MB of free Ram available at this moment.

---

### Post by sandyd on 2015-07-29
> **steve_mc said:**
> I replaced windows 8.1 with ubuntu 15.04 about a month ago.  I quickly realized that i wanted to run a virtual machine to support some programs
that would not run correctly in ubuntu. My pc has 4 gigs of RAM. Running windows 8.1 within Virtual Box on the unity desktop performed ok, but it
performs much better running the less resource intensive LXDE desktop. Currently i am running Virtual box with windows 8.1 playing a java game. Using the lxde desktop, Firefox and terminal open. The results of the free -m command show that i have 1101 MB of free Ram available at this moment.

Try KVM (virt-manager), I've found that if you have the proper CPU virtualization extensions, KVM is much much faster than VirtualBox.

---

### Post by romello6543 on 2015-07-30
My machine is newly built gaming PC with 16 gigs i7 chip. Although, i am not using it for gaming but basic daily usage. I think i will go with Lubuntu for the learning experience and having the option to install the packages that I want installed instead of having pre-installed packages that I probably will not use. Having the Kernel manage the VM is the route I want to take instead of installing additional software for VM's.

---

### Post by jason_gibson2 on 2015-07-30
KVM is great for virtualizing server things. Not so much for anything with graphics of any kind. Virtualbox is best choice for that. Guest additions make the vm seamless with the host and that is worth it's weight in gold depending on what you plan on doing.

---

### Post by MGrowl on 2015-07-31
Is there a big difference between qemu vs virtualbox? I personally prefer using only open-source but I've heard some people using qemu say that it is considerably slower. Might not be appropriate to this thread, sorry OP. Just thought of asking since there's talk about virtualization.

---

