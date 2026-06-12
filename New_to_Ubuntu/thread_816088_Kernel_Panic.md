---
title: "Kernel Panic"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Cront on 2008-06-02
Hi guys,

I've been trying to resolve my reoccurring kernel panics and have tried several solutions none of which have worked so far.

I'm currently using ubuntu x86 64bit and I have a D-Link 510 wireless card which from what I've read is the cause of my trouble.

I've followed the instructions listed here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142/comments/6)

The backports did not resolve the issue for me and so I was hoping to try the .25 kernel

I've created the file /etc/apt/sources.list.d/kernel-ppa.list to include the following two lines as per the instructions and ran apt-get update but for the life of me I can't figure out how to install the kernel.

All is says is "You should then be able to install the linux-image-2.6.25 kernel package." but I can't seem to find it in Synaptic.

Any help would be very much appreciated.

---

### Post by philinux on 2008-06-02
Double check the file the you created.

When you run

sudo apt-get update 

You should see the new package downloading in the text messages.

---

### Post by spiderbatdad on 2008-06-02
Right here:[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by Cront on 2008-06-02
I can see it hitting those servers when I run apt-get update but I can't find the actual image in synaptic.

I search for image and I see all the .24-17 and 16 ones but not .25

---

### Post by Cront on 2008-06-02
So I'm in the process of compiling my own kernel now but is there something I'm missing to be able to do this straight from synaptic?

---

