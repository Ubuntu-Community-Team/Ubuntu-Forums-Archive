---
title: "How to repair Grub from Grub Rescue without Live CD"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by alice2 on 2014-02-18
I have two partitions on my laptop, one which had Ubuntu 14.04 and the other which had Fedora 19. I tried to overwrite the Fedora 19 with Fedora 20 from a net install disk, but the installer crashed halfway through. I let it sit there frozen for a few hours and then took the battery out and rebooted. I got to the Grub rescue screen. When I list the partitions from the grub rescue I get "(hd0) (hd0, msdos1) (hd0, msdos2)". When I try "ls (hd0, msdos1)" I get "fileysystem unknown". Same for the other partition. Then I tried booting from my Ubuntu live CD, but that experienced a kernel panic before I got into the installer. The same thing happened with a Fedora live CD I tried. (both of those CD's worked before) Is there any way I can repair this from the Grub Rescue? Or do you think I would be more successful booting from a non-live CD and reinstalling linux? I don't have any data that isn't backed up. Would a non-live CD still be subject to the kernel panics I had with the Live CD's? (I'm thinking that the non-live CD doesn't boot the kernel, so this won't happen) I would prefer the simplest possible solution since I don't really know anything about computers. Thanks for any help you might have.

---

### Post by Bucky Ball on 2014-02-18
Welcome. Firstly, what non-live disk are you talking about? The alternate version is no longer available for newer releases so you would need a minimal install or server disk.

---

### Post by alice2 on 2014-02-18
I was thinking of using a Debian non-live install CD. I would install Debian alongside Ubuntu, and hopefully that would restore grub. Unfortunately it would take some effort to get the CD since I don't have access to a working computer right now (I'm typing this from my phone). I'm wondering if anyone knows whether this would be less likely to experience the kernel panic I had with the live CD. Or, if anyone happens to know ho to fix grub from grub rescue in this situation.

---

### Post by Bucky Ball on 2014-02-18
Have you tried booting a 12.04 disk? Don't know anything about Fedora (and any questions regarding it should be posted in Other OS Support) but 14.04 is testing and not released until April. Definitely not a good place to start. Expect bugs and breakage. 12.04 LTS is rock solid and what you should be trying next.

It is not a good idea to install an operating system in the hopes it is going to fix grub. It just installs grub again and may not change a thing, leaving you with a redundant operating system and a bunch of wasted time. I wouldn't go there.

---

### Post by alice2 on 2014-02-18
Actually, I also tried an OpenSuse live CD and that also kernel panicked. I think it's very unlikely that a fourth live CD will work, unless there's something special about 12.04. Also, this wasn't a bug or breakage in Ubuntu 14.04, it was my fault because I messed up grub. The Ubuntu 14.04 CD worked perfectly for me before.

---

### Post by Bucky Ball on 2014-02-18
Don't know anything about OpenSUSE either. What's special about 12.04 LTS is that it is a known entity, is extremely stable and your best bet for troubleshooting if you're intending to do it with Ubuntu. As I say, 14.04 is testing and not where you want to be if you're trouble shooting boot issues. Even if you do manage to get 14.04 back up you are going to be in for an unpredictable ride and unless you are a tester and intending to report, discuss and troubleshoot issues in the Ubuntu+1 section here (which is where anything regarding 14.04 is posted or will get moved to), then I'd make life a bit easier for yourself. 

But maybe 12.04 LTS will make no difference. We'll never know without a go. It is supported until 2017 and is directly upgradeable to 14.04 LTS when it is released in April.

---

### Post by monkeybrain20122 on 2014-02-18
It is not clear from your posts what happened to the Ubuntu partition. If you only tried to overwrite Fedora 19 with Fedora 20 it shouldn't affect the Ubuntu partition. What was the Fedora installer doing prior to the crash? Where did you install grub before?

 I also don't understand how failure of the Fedora installer would cause kernel panic when booting live cds/usbs, maybe it was a hardware failure that caused the Fedora installer to crash in the first place?

P.S. 14.04 is a beta, you said you have only one computer, are you running a pre-release as your main OS? This doesn't sound good (or maybe Fedora was your main OS?) I would try a 13.10 or 12.04 live usb instead.

---

### Post by alice2 on 2014-02-18
deleted

---

### Post by Bucky Ball on 2014-02-18
Yep, the source of this seems to be from the Fedora overwrite so quite possibly a Fedora issue, but rather than moving the thread to ***Other OS Support*** (yet) I'm ignoring that for the moment and sticking to the boot issues. ;)

It would pay to post in the Fedora forums also, though, as the Fedora overwrite is when the issue began. The problem is not exclusive to Ubuntu, any OS gives a kernel panic by the sounds of it.

---

### Post by alice2 on 2014-02-18
I'm guessing I had grub installed in the Fedora partition that I overwrote. (stupid, I know) I was expecting the Fedora 20 installation to work, so I didn't consider that this would be a problem. I'm not exactly sure where the installer was when it crashed, because it left me at a screen with no information. Apparently it got far enough to overwrite my Fedora partition though. As for the kernel panics, I have no idea what's causing them, but it is clearly related to this incident since all the Live CD's I tried worked before. I'm not asking for support for Ubuntu 14.04, since I know that's unsupported. I've never had any issues with it though. As I said above, I'm just asking whether people think a non-live Debian CD will avoid the kernel panics, and if anybody knows how to fix grub from grub rescue.

---

### Post by monkeybrain20122 on 2014-02-18
I think it was a hardware issue that causes the Fedora installer to crash. The Fedora overwrite of the hard drive would not cause kernel panic when booting from live usbs/cds. In fact booting from live cds/usbs would work even if you have no hard drive at all.

---

### Post by alice2 on 2014-02-18
=

---

### Post by monkeybrain20122 on 2014-02-18
> **alice2 said:**
> I'm guessing I had grub installed in the Fedora partition that I overwrote. (stupid, I know) I was expecting the Fedora 20 installation to work, so I didn't consider that this would be a problem. I'm not exactly sure where the installer was when it crashed, because it left me at a screen with no information. Apparently it got far enough to overwrite my Fedora partition though. As for the kernel panics, I have no idea what's causing them, but it is clearly related to this incident since all the Live CD's I tried worked before. I'm not asking for support for Ubuntu 14.04, since I know that's unsupported. I've never had any issues with it though. As I said above, I'm just asking whether people think a non-live Debian CD will avoid the kernel panics, and if anybody knows how to fix grub from grub rescue.

Grub is easy to fix if you can boot from a live cd. I think the fact that you keep getting kernel panic when you try is a bigger problem

---

### Post by Bucky Ball on 2014-02-18
Yep, starting to lean towards hardware myself.

---

### Post by alice2 on 2014-02-18
Okay, thanks for the ideas everyone. Maybe I'll take the computer in to a repair shop and see what they say about the hardware.

---

