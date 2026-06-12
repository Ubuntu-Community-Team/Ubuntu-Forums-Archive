---
title: "[SOLVED] How do I install generic Linux driver for LAN"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by DocWu on 2008-07-26
I am totally new to Linux. I've played with live CDs a few times, but never got comfortable enough to commit to using them. 

I built up a box with Ubuntu 7.10 in a dual-boot with Windows. The network card works in Win XP.

I've seen some references to a problem with this particular mobo and the on board LAN, but no solutions.

Here's the details:

Intel DG945GCLF desktop board (Atom Processor)
Onboard LAN is Realtek Fast Ethernet controller .

I am using Ubuntu 7.10. (8.04 would not install) Almost everything else is working. 

The Intel website has a "Linux" driver update for the LAN. I downloaded it, but am lost as to how to use it. The unzipped driver file has a makefile file and a couple folders (src and .svn) 

The readme file tells me to do some things, but they apparently don't work in Ubuntu. For example:
```
<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports linux kernel 2.4.20 and latter.
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8101-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8101-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8101.ko	(or r8101.o for kernel 2.4.x)


```

etc. 

Can this file be used to patch Ubuntu to work with this network chip? How would I do it? Or is this too advanced for the beginner area? :)

It may very well be too advanced for me, but I'm willing to try. This is a "learning" box for me, so there's nothing to loose.

---

### Post by jamesrfla on 2008-07-26
Go to system>administration>hardware drivers and tell me what you see. Ubuntu 8.04 should be able to install.

---

### Post by DocWu on 2008-07-26
> **jamesrfla said:**
> Go to system>administration>hardware drivers and tell me what you see. Ubuntu 8.04 should be able to install.

I don't find that at all, but under system>administration>preferences>hardware information, I get a box with a tree-view of devices on the left and details on the right. Is this what you need?

In the tree, there is an entry "82801G (ICH7 Family) PCI Express Port 1" with "Realtek RTL8101E PCI Express Fast Ethernet Controller" as a child.

Is that any help?

---

### Post by hyper_ch on 2008-07-26
tried 8.04 wehther it recognized that lan card out-of-the-box?

---

### Post by DocWu on 2008-07-26
> **hyper_ch said:**
> tried 8.04 wehther it recognized that lan card out-of-the-box?

8.04 would not install. It stopped and went to some kind of command line I didn't understand. 

From what I've read elsewhere, this is also related to the Realtek on-board LAN.

Some people have gone as far as to disable the on-board LAN and put in a PCI card, but I need the one slot for another card.

Incidentally, this mobo is popular with the Hackintosh people and will run OSX with a little work.

Not sure if I'm up to trying that, I have even less Mac experience than Linux :(

---

### Post by DocWu on 2008-07-26
Okay, I think it is working. I don't know how, or if it was working all along and I didn't know it.

All of a sudden, I started seeing my local network. After I made some changes to the network settings, I was able to get to the internet.

My son, doing some research on this, found something saying the nightly builds of 8.04 fixed the problem of crashing while installing with this board. I could have used a new download of it, but now, I'm running the update manager.

At least now I can get online to find answers to my questions without jumping over to another machine...

Thanks for the help.

---

### Post by DocWu on 2008-07-27
> **DocWu said:**
> 8.04 would not install. It stopped and went to some kind of command line I didn't understand. 

From what I've read elsewhere, this is also related to the Realtek on-board LAN.

Here's more info in case someone else has this mobo:

[Page 1]("http://softwarecommunity.intel.com/isn/Community/en-US/forums/thread/30257522.aspx") and [Page 2]("http://www.intel.com/support/motherboards/desktop/d945gclf/sb/CS-029475.htm")

(both are on Intel's forums.)

---

