---
title: "What is GRUBB"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by figarotaff on 2012-04-25
I installed version 11 but when I startup I now get the message  Grub error >    wrong partition and I cannot get into the computer.  I have windows on the computer but I am not sure what exactly is on it and I can't get it up to look at it.
I tried reinstalling 11 and deleting the partitions that were created for Ubuntu and then reinstalling but I still get the same message.  I have an Asus T180 with am Athlon 64 x2 4400 processor and 4Gig of memory.  I have windows 7 installed(or did have when I started ) .:sad:
Any comments(polite please) would be welcomed, thank you.

---

### Post by ronaldbrijo on 2012-04-25
Grub is the bootloader for Ubuntu. It is used to startup whichever operating system on the pc. 

I suggest use your windows 7 installation disc, and run the startup repair from it. Or as the pc bootup go into the repair option on startup.

Once you are able to boot into windows, try and install Ubuntu again.

One concern though, How did you install Ubuntu... Alongside windows or did u use the use whole hard disk option?

---

### Post by corrytonapple on 2012-04-25
To fix your issue, we are going to just install a whole new GRUB.  
Boot up to an Ubuntu Live media, equal to your operating system.  So if you run 11.10, you need to boot from 11.10 live media.  This has to do with different GRUB versions.  This media may be a CD, or a USB stick.  Do it just as you installed Ubuntu.  Boot to the Live Desktop.  Open up Firefox, and download this program from this thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

So, to do so, open up a Terminal, and put in:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair

```
That will launch boot-repair.  Then, have it go through the default options.  Just have it install it.
Reboot and you should be good!

---

### Post by QIII on 2012-04-25
Before attempting the method above, it might be helpful to know the answer to ronaldbrijo's question.  Did you use Wubi to install Ubuntu?

---

### Post by YannBuntu on 2012-04-26
Boot-Repair is also compatible with Wubi, so no problem using it, it won't harm the system.
After using it ("Recommended repair" button), it will display a BootInfo URL. Please indicate it so that it will help us understand your situation.

---

### Post by figarotaff on 2012-04-30
I found an old IDE hard disk and started clean.  I formatted it with windows 7 OK then I installed Ubuntu 11 OK now I always get Ubuntu loading up at startup and I cannot get windows.  The previous disk did not respond to treatment and I now have an 80Gb disk that reports only 31Gb.
The present setup-  I split the disk into two partitions about 80Gb each and let Ubuntu go on the second partition and this is probably the reason it does mix with windows.  
Anyway I now have a working Ubuntu to play with and I can play with this and perhaps not be so thick.  Thabnk you for youe efforts but if you have any comments to the abouve I would be greatful. Many thanks.

---

### Post by YannBuntu on 2012-05-02
Please could you indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?

---

### Post by *^kyfds( on 2012-05-02
i had the same issue a while ago.

it's really quite difficult to get this fixed. 

just please god don't reformat your windows partition.

you'll end up regretting it later.

did your copy of windows come pre-installed?

---

