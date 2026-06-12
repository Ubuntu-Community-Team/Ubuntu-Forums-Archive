---
title: "Ubuntu doesn't boot after installing windows xp"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Higatron on 2008-09-18
I installed xp on a seperate hard drive. Then I download an ext2 driver for xp (ext2ifs) so I can copy my music onto itunes (the only reason I'm on windows). After getting my music into my ipod, I restart my computer and the usual ubuntu startup doesn't happen. I check my bios boot options, and it's set up right. I check my cables and such, all good there. I tried to boot without the hard drive xp is on and I get a no boot drive detected or something along those lines. Not sure what I did, but I think it has something to do with the ext2 driver. I didn't delete any files in the ubuntu drive, just copied 3 gb of music onto the windows drive.

---

### Post by jemate18 on 2008-09-18
> **Higatron said:**
> I installed xp on a seperate hard drive. Then I download an ext2 driver for xp (ext2ifs) so I can copy my music onto itunes (the only reason I'm on windows). After getting my music into my ipod, I restart my computer and the usual ubuntu startup doesn't happen. I check my bios boot options, and it's set up right. I check my cables and such, all good there. I tried to boot without the hard drive xp is on and I get a no boot drive detected or something along those lines. Not sure what I did, but I think it has something to do with the ext2 driver. I didn't delete any files in the ubuntu drive, just copied 3 gb of music onto the windows drive.

XP might have overwriten your MBR therefore... GRUB of Ubuntu was damaged/deleted...

---

### Post by rbc on 2008-09-18
I agree with jemate18. The Windows install hosed up grub. Have a look here for a fix:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by eriqjaffe on 2008-09-18
FWIW, there are a number of Ubuntu-native apps that can transfer music to an iPod.  Amaraok and GTKPod come to mind.  I'm pretty sure that Banshee and Exaile have iPod support as well.

---

### Post by gnrathon on 2008-09-19
instead of installing windows just for iTunes, you could just try a variety of different Media Players available for linux. The default one in ubuntu is Rhythmbox, which has iPod support built-in

also a great alternative for iTunes in Linux is Songbird.

They are very similar and it also has iPod support!!!


[http://getsongbird.com/](http://getsongbird.com/)


it also lets you browse the internet at the same time!!!!

Use this link for the simplest install on ubuntu:
[http://www.getdeb.net/release/3116](http://www.getdeb.net/release/3116)

---

