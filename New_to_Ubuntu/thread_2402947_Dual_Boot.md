---
title: "Dual Boot"
date: 2018-10-05
forum: New to Ubuntu
---

### Post by genesisclimber on 2018-10-05
Hello, I am using Kubuntu KDE plasma and I'm finding it extremely difficult just to perform basic functions and it's severely impacted my workflow.  Ideally, I would like to dual boot windows 10 or just completely revert back. It seems like this is such a simple task, but for some reason I cant figure out how to do it... I tried mounting an .ISO and that didn't work, I can't install .exe files...I have no idea what i'm doing. It would really help if I could get some live support and someone walk me through this...

---

### Post by guiverc on 2018-10-05
If you want 'live' support, click 'Other Support - Ubuntu IRC Support', or open your favorite IRC client & go to #ubuntu on freenode.

Chat channels are listed on [https://wiki.ubuntu.com/IRC/ChannelList](https://wiki.ubuntu.com/IRC/ChannelList)  (support channels have a webirc that can be accessed via browser).

I'm not sure you understand what dual booting means.  It will mean you have two+ partition groups on your hdd/sdd, and at boot you select which you want to run (windows or Ubuntu).  To switch to the other you reboot to return to the boot-manager menu (grub usually) which asks what you want to run.  You don't mount ISO's on Ubuntu, you write them to a thumb-drive & boot them, letting them install themselves.  I'm not familiar with windows 10 so couldn't advise, but I always prepare my disk (gparted/kde partition manager) before hand, though because [partition changes] require the drive to be unmounted, I use a 'live' system to do it (ie. my Ubuntu wouldn't be mounted).

---

### Post by oldos2er on 2018-10-05
*.exe files are for Windows, and will not natively run on Linux. 

I found some information [here]("https://unix.stackexchange.com/questions/319019/is-there-a-kde-tool-for-mounting-disk-images-like-gnome-disks") on mounting ISO files on KDE, hope it helps.

---

