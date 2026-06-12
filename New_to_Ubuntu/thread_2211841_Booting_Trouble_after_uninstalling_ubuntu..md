---
title: "Booting Trouble after uninstalling ubuntu."
date: 2014-03-18
forum: New to Ubuntu
---

### Post by takunechan on 2014-03-18
Hey, I'm pretty much a noob when it comes to using partitions & and stuff, well I installed / uninstalled Ubuntu (I don't know how many times) I used super boot loader in one of these installations w/e just played around with the settings like an idiot, but I was unaware of what was going on with my Windows install, HOWEVER when I uninstalled Ubuntu at that moment (using [os-uninstaller]("http://ubuntuforums.org/showthread.php?t=1769489")) , then after uninstalling the OS when I WAS expecting to boot back into windows it showed the "Grub rescue " screen ,THEN when googled it using a Ubuntu 13.10 live CD to search the problem I tried using **BootRec / cmds *and so on*** , now when I boot into Windows it shows a black sceen with _ (blanking) so basically a black screen, I tried tools such as [boot repair]("http://help.ubuntu.com/community/Boot-Repair") within the Ubuntu boot CD as well, ALSO I eariler installed EasyBCD so I could boot Windows 7 + Ubuntu , but it never worked out, which is the reaosn why I reinstalled ubuntu so many times,I have no idea right now where to go on about fixing this also I found this using the installation type thing for managing patitions; [IMG]http://i.imgur.com/UN67aEy.png[/IMG]
I found out that it has two windows 7 loaders, ALSO when I used mbr the windows repair disk did not detect windows, anyway I hope this explains enough for you guys to help me, I know I'm a complete noob, but please help me fix my windows install. :c *P.S: I not TRYING to install Ubuntu at the moment, I am trying to fix my Windows Install (I am sure it's connected to ubuntu somehow)*

---

### Post by LinuXXuniL on 2014-03-18
Hi, the boot recovery files for windows should be on the 105 MB partition, but it looks it is free, that's why you can't recover. The windows repair disk should work, see if you are using the correct repair disk (x64 bit or x86) according to your windows version. If you are using USB try this tutorial for making a windows repair USB: [http://www.techradar.com/news/software/operating-systems/how-to-create-a-windows-rescue-usb-stick-984726](http://www.techradar.com/news/software/operating-systems/how-to-create-a-windows-rescue-usb-stick-984726)

---

### Post by fantab on 2014-03-18
> **takunechan said:**
> [I].....
I not TRYING to install Ubuntu at the moment, I am trying to fix my Windows Install (I am sure it's connected to ubuntu somehow)[/I]

You will have to repair the MBR with Windows Install DVD/USB or Windows Repair Disc.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

