---
title: "installed ubuntu on third hard drive, won't boot"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by zephyrpenoyre on 2013-09-16
I installed ubuntu on the third hard drive of my pc, the first two being a 120GB SSD and a 1TB HDD for data on the windows 7 side.

 Now I've just installed ubuntu 13.04 onto another 1TB HDD, went through the installation ok, changed the BIOS so that it would boot to this hard drive first automatically (although also doesn't work if i boot to it manually)

  And... nothing. Well actually, an eternally blinking underscore, but basically nothing.

  Do I need to do something clever with the grub, like install it onto the SSD? Or should it work and I've just messed up the installation?

  (n.b. was also considering installing it on a corner of the SSD and using the second HDD for data, much like the windows 7 side, but eventually i gave up on this idea as i couldn't quite get my head around it... Could that have avoided this issue/ worked better)

  Thanks for any help

---

### Post by arkan01d on 2013-09-16
Sounds like you installed it the right way. As long as you have your 3rd hard drive selected as the main boot it should work. Does Grub come up at all, or does it just load straight to a blinking underscore?

---

### Post by oldfred on 2013-09-16
BIOS or UEFI?
What video chip/card? Often black screen is a video driver issue?
Can you boot from recovery mode? Second line on grub menu? It has nomodeset built in.

Or you can add nomodeset or maybe other parameters depending on what video or system.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by fireflower on 2013-09-17
Are the hard drives sensitive to master/slave jumper settings?

---

### Post by zephyrpenoyre on 2013-09-17
Thank for the replies, i'm quite inexperienced with these things so i'll do my best to answer your questions:

Firstly I get no GRUB at all, it goes through all the non OS specific screens then straight to black.

> **oldfred said:**
> BIOS or UEFI?
What video chip/card? Often black screen is a video driver issue?
Can you boot from recovery mode? Second line on grub menu? It has nomodeset built in.


I think it's UEFI BIOS, but my understanding of these things is limited

I'm using a nvidia gtx 580.

Wouldn't booting from recovery mode require seeing grub?

As for master/slave jump settings, no idea about this, how would I check?

---

### Post by oldfred on 2013-09-17
If when Ubuntu installed, and it did not see any other systems, it may auto boot just to Ubuntu and not show grub menu. If that is the case holding shift key from BIOS until menu appears should work. Black screen is common issue particularity with nVidia video. And nomodeset is the most common solution to get you into system so you can install the nVidia proprietary drivers.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

If boot issue and not just video, from liveCD/DVD/Flash drive download and run Boot-Repair and post link to BootInfo report.

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

