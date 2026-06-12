---
title: "Managing upgrade progression using &quot;chroot&quot;"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by IrmaLiddleTeapot on 2013-05-04
On occasions I've upgraded Ubuntu or other  Linux distro's (Gentoo, Slitaz) and found that the upgrade "breaks stuff" that was working perfectly before the upgrade, often because the technology was old or no longer supported.  I use GRUB as my boot loader and yes I could have multiple OSes occupying real estate on my boot drive but don't want to.   

Where I have a particular distro such as Ubuntu being used for science and engineering applications (I love fortran) , I want to maintain the source code and apps on a separate drive and know I can continue using them if dependencies change in, say, gcc.   To achieve this, I wondered about having 2 distro paths: one of the existing (stable) version and another for the new upgrade.   Thus would mean I could "roll back" to the older stable version at any time I chose.

   I'd greatly appreciate any pointers anyone could give me on how to achieve this --    O'Reilly "Linux in a Nutshell" perhaps.   Many thanks.

---

### Post by deadflowr on 2013-05-04
For what you want, you'll Have to install a second OS.

Or run a second OS in a VM.

---

### Post by IrmaLiddleTeapot on 2013-05-06
> **deadflowr said:**
> For what you want, you'll Have to install a second OS.

Or run a second OS in a VM.


Hi deadflowr - thanks for your comment.   I have Slitaz (for quick and dirty coding), Ubuntu 11.04 and Win 7 installed on a 180 GB SSD which functions as my OS drive and a further 10 TB of storage on a mixture of internal and external drives (with about 3TB free for backups etc).   My existing OSes occupy about 100 GB of the 180 GB drive and I also have GRUB bootloader on that drive.   The machine has 8GB of RAM installed and a further 8 GB of virtual memory.

[1] Using a second OS:
Are you suggesting that I make a new appropriately sized new partition on my SSD and install Ubuntu 13 into that and let GRUB manage the OSes at boot ?

[2] Using a VM:
I understand that Ubuntu has Zen as a VM (more of a slim hypervisor?) and I could use that, though getting it up and running is probably outside my current skill set.

I thought/hoped I might be able to chroot between differnt kernels once the dependencies were sorted but perhaps my understanding of the chroot function is flawed.   If so could you point me to a reference that would help a noob ?   I've had a bit of a look around but the syntax and explanations seem targeted at either noobs oe power users and I fall somewhere in between.   I'd greatly appreciate any assitance you could provide even if it is just telling me which Friendly Manual to Read <grin>.

Thanks again for your help.

---

### Post by Kopkins on 2013-05-07
Chroot lets you change your root directory for a certain instance, like in a terminal. But to unmount and remount a different physical root partition would crash your system. If you like manuals, try the man pages. In a terminal type `man <command>` where <command> is a command you want to learn about. Try `man chroot`. Most would recommend VirtualBox to run a virtual machine. It's free and relatively easy to use. That way, you could run whichever system on your actual hardware and your other system in a virtual machine. 

Back to chrooting your system, to have two different roots that you chroot between, is basically like having two root partitions. But to chroot you have to reboot.

Good Luck,

Kopkins

---

### Post by IrmaLiddleTeapot on 2013-05-07
Hi Kopkins,

Thank you for clarifying the differences in those methods for me.
Using a virtual machine certainly seems to offer greater advantages
than "chroot"-ing.

Last question - Windoze 7 ultimate 64 bit (w7u64) offers a virtual
machine for XP mode.  Will Microsoft allow others to play in their
sandpit or do they get snarky and toss their toys ?

Many thanks (again)
Irma Liddle-Teapot.

---

### Post by Kopkins on 2013-05-07
A common example is that you forgot your password for your computer. So you start up a liveCd in the Live Cd environment. Next, you mount your actual partitions and chroot into them. Now, your root environment, in that terminal/instance, is your computer's root. Then you use passwd user to change your password. But you're still using the LiveCd root to run programs. The Chroot environment is NOT the entire environment you are in and only applies to a terminal, not the whole desktop. 

The windows virtual machine is integrated into windows. So you couldn't install ubuntu in a VM there. However, Virtualbox is available for windows. 

EDIT: To confirm, I tried running startx from within a chroot and my system hanged. So I don't think you'll be able to do exactly what you want. I chrooted from my arch install to my ubuntu 12.04 root and did startx and it executed but then just hanged.

Kopkins

---

### Post by IrmaLiddleTeapot on 2013-05-08
Many thanks to deadflowr and Kopkins for your excellent and informative 
advice.   A special thanks to Kopkins for supplying very useful illustrative 
examples.

Kind regards,
Irma Liddle-Teapot

---

