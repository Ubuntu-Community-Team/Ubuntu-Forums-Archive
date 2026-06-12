---
title: "Close to having a heart attack..Help!"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Asclepius28 on 2008-05-15
So here is the situation(which im sure you have heard before).. with my limited knowledge. I tried to look up how to fix this and i had some trouble. So i loaded Ubuntu on my external hard drive, set up my bios to boot to the cd first usb storage second and internal harddrive third. Now whenever I turn on my computer it says it need s a recovery/system cd. So i put in the ubuntu cd and then i can say go to first drive and then i can choose between windows and ubuntu(i would prefer to be able to choose w/o the cd). When the external harddrive isnt plugged it it says error loading GRUB error 21. So what noobie mistake did i make and how do i fix it? sorry kinda long i know... oh and im running a dell :(

---

### Post by EXCiD3 on 2008-05-15
Where did you install Grub to?

Also, while the thread title was kinda funny, please post a descriptive title next time. ;)

---

### Post by HotShotDJ on 2008-05-15
> **Asclepius28 said:**
> So what noobie mistake did i make and how do i fix it? sorry kinda long i know... oh and im running a dell :(You installed GRUB to the first internal harddrive.  Well... YOU didn't do it.. that is the default since it is almost always the right thing to do... except with installs to a USB device. :)  So, now when you boot up the computer, GRUB can't find its files because they are on the USB device that just happens to not be attached at the moment.

I know this can be fixed.  But I honestly don't remember how.  But i thought I'd at least let you know that there IS help (perhaps they are posting right now as I type this) and it is not a total disaster... for your coronary health, you know. :)

---

### Post by Asclepius28 on 2008-05-15
Well im assuming that GRUB was loaded on my internal hd as HotShotDJ suggested. And im hoping for a very easy solution lol, but i know that this isnt always the case. And sorry for the non descriptive title EXCiD3, lets just hope that there isnt a next time! As for right now my computer better start drinking its coffee cause its gonna be awake all the time.

---

### Post by Xiong Chiamiov on 2008-05-15
Take a look at [SuperGrubDisk]("http://supergrubdisk.org"); even if it doesn't solve your problems, it'll easily allow you to boot to any partition.  I would've saved quite a bit of time if I had known about it sooner than I did.

---

### Post by EXCiD3 on 2008-05-15
> **Asclepius28 said:**
> Well im assuming that GRUB was loaded on my internal hd as HotShotDJ suggested. And im hoping for a very easy solution lol, but i know that this isnt always the case. And sorry for the non descriptive title EXCiD3, lets just hope that there isnt a next time! As for right now my computer better start drinking its coffee cause its gonna be awake all the time.

What you are going to need to do is reinstall grub onto your external drive and reinstall the mbr on your internal drive.

Do you have windows installed on your internal drive? If so you can configure your boot order to 1) CD, 2) external, 3) internal. This will bring you to GRUB on your external (if its plugged in) where you can add an option to boot to the internal drive. If its not plugged in you will just boot to your internal normally.

You can use this to install grub to your external drive. Make sure you make the correct changes so that it installs to your external and not your internal one again. ;)

Then you will need to recover your internal hdd OS's mbr depending on what it is. Hope this helps get you started. Don't worry about there being a next time...with computers its guaranteed there will be a next time. :lolflag:

---

### Post by kansasnoob on 2008-05-15
[http://ubuntuforums.org/showthread.php?p=3995006#post3995006](http://ubuntuforums.org/showthread.php?p=3995006#post3995006)

---

### Post by EXCiD3 on 2008-05-15
> **kansasnoob said:**
> [http://ubuntuforums.org/showthread.php?p=3995006#post3995006](http://ubuntuforums.org/showthread.php?p=3995006#post3995006)

Good call, this should take care of it all for you.

---

### Post by Asclepius28 on 2008-05-15
thanks for all your quick replys!!!

---

### Post by EXCiD3 on 2008-05-15
> **Asclepius28 said:**
> thanks for all your quick replys!!!

If this worked make sure to mark your thread as solved and i encourage everyone to click Thanks, the blue medal, on the posts that were helpful to make it easier for people browsing the threads to find the answers that were helpful.

---

### Post by DaF101 on 2008-05-15
The issue that your having that it is installed on the external HDD, probally not a good idea because it is removable storage. next time, just resize your windows partition so you can dual boot ubuntu and windows. 

What version of Windows are you running and what version of Ubuntu are you running?

If you REALLY wanted to install ubuntu on a external hard drive I would unplug your internal ones on the inside just to play it safe.

---

