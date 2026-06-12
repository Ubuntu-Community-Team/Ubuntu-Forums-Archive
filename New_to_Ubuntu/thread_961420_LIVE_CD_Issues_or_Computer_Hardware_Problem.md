---
title: "LIVE CD Issues or Computer Hardware Problem?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by BitCrusher on 2008-10-28
:guitar:Hello:

Well, after several weeks of effort, I am still no closer to getting Ubuntu set up on my computer. So I'm baaacccckkkkk..:)

I use MS Vista and wanted to have Ubuntu set up on the same hard drive (a dual boot OS). Using the directions from the Ubuntu 8.04 magazine and the Live CD, I allowed the Live CD to set up the proper partitions (workes like a charm). At the end of the setup process, Ubuntu asks me to restart the computer. Everything is fine until MS Vista reboots. There is no mention of Ubuntu, and no oppportunity to pick which OS I need to utilize. However, I went to DOS and verified that Ubuntu is setup on the I partition. However, Vista did not execute CHKDSK so it makes me wonder exactly what is going on. I almost hit wibu.exe on I Drive (i.e. Ubuntu Boot partition)  to see if that was ubuntu but decided I shouldn't play around without some additional guidance.

My primary reason for wanted to use Ubuntu Studio is because I am a musician and really want to try out the 64 bit engine for capturing my music. It looks so promising, but I need to have it run seamlessly.

Here is my computer setup :I have an nForce680i SLI motherboard, 4 GB Ram, a Seagate 160 GB hard drive (IDE), an EMU 1010 PCI Card (audio), an MSI NX8600GT Series Video Card. Is the hard ware the problem, or is GRUB just not setting up the boot sector correctly?

Incidentally, I am not sure where to find the correct driver for the EMU Card. Creative does not support LINUX and I couldn't find the driver on the ALSA site. Any help on this one would also be helpful. 

Thanks,

Joe

---

### Post by phidia on 2008-10-28
It sounds like, from what you've described, that grub did not install correctly.
You can use a live cd and [this method]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") or get [super grub disk]("http://www.supergrubdisk.org/") (which might be easier).

---

### Post by aeiah on 2008-10-28
it seems like there's a problem installing rather than compatibility wise, although you may have compatibility problems too of course :p

have you tried following an online guide for dualbooting ubuntu with vista?. wubi is a method for installing ubuntu within vista, and ive never tried it myself. some people say its great for beginners, but some people have problems with it. id suggest going the proper way with partitioning if you're up to the task, which it seems you are.

what do you mean by 'went to DOS and verified'? as far as i know, DOS hasnt really been shipped with windows since windows 95

---

### Post by BitCrusher on 2008-10-28
I'm sure you're correct. I 'm not anything like a computer expert. 

I am using the "terminal" in Vista, and it takes me what appears to be the old DOS command line, and when I used DOS commands they worked. That's was how I verified that the partition was in existence and where I found Ubuntu and wubi.exe. I'm already at the edge of my expertise...wish I was more computer savvy..

Thanks,

Joe

---

