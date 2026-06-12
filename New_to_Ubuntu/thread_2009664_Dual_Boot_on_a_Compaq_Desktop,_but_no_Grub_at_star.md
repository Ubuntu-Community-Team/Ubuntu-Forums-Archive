---
title: "Dual Boot on a Compaq Desktop, but no Grub at start-up"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by thefoolisme on 2012-06-24
Hi there, 

I installed Ubuntu 12.04 LTS on an older Compaq computer (WinXP Media Edition)using Wubi.  It seems to have installed, however, when I start up the computer, I don't see Grub.  I only see Compaq's start up screen where you can select boot menu, recovery, etc. and then it goes into Windows.  Is there a way to incorporate the Compaq start-up screen into Grub?  I don't want to lose the option to go to the recovery disc on the Compaq.  

Your help is appreciated.

---

### Post by mbzn01 on 2012-06-24
Since you used wubi to install ubuntu runs "like a virtual machine" in windows. So, you have to load windows and ubuntu from there. I have personally never used wubi so i cant give you all the correct info, but you wont have grub.
Try [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Hope it helps

---

### Post by shyamjoshi on 2012-06-24
Hi , 

I had the same problem with my laptop about a month ago when i tried installing , I dont know whether its relevent , but you could give my solution a try:

I blogged it step by step:
[http://shyam-techblog.blogspot.in/2012/05/ubuntu-1204-boot-up-problems.html](http://shyam-techblog.blogspot.in/2012/05/ubuntu-1204-boot-up-problems.html)

:popcorn:

---

### Post by thefoolisme on 2012-06-24
Thanks for the responses.  According to the Wubi link provided, I should still have a start-up screen where I can choose which OS to enter.  I don't have that screen, probably because of the Compaq start-up screen. I can't erase the Compaq screen because of the link to recovery options, but somehow I must be able to blend them together.

---

### Post by jmfal on 2012-06-24
The Compaq start up screen will be there  without any operating system installed,

that is part of your bios  and is the only way to enter bios/setup  and the boot menu

Don't try to delete it .

I don't use wubi but if you boot into ubuntu youo can install grub either from the synaptic or using a terminal:
```
 sudo apt-get install grubpc 
```

And then you boot to the grub screen and go into recovery kernal and update grub from there.
If you think grub is there already at restart >>select boot menu>>select ubuntu >>then hold sown the alt key and tap the shift key      That should get you to the grub screen

---

### Post by thefoolisme on 2012-06-26
It won't allow me to boot into Ubuntu, that's my problem.  Grub does not come up, so there is no option to select Ubuntu.  If I go into the Compaq boot menu, only HDD and CD Drive are options.  

It seems that the Wubi aspect has confused you.  I don't mind reinstalling using a CD after making a partition.  My fear though is that if I do that, I will still have the same problem with the Compaq boot screen and no grub.

Does anyone have experience with getting around a PC's built-in boot menu for a dual-boot system?

---

### Post by oldfred on 2012-06-26
With wubi you do not actually boot with grub. You boot with Windows and Windows XP's boot.ini or Vista/7's BCD has a wubi entry which loads a grub menu.

So if Windows does not have the wubi entry, you may have updated Windows or in other ways deleted the entry.

You can add the wubi entry to XP's boot.ini.

boot.ini entry:
c:\wubildr.mbr="Ubuntu-Linux"

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

