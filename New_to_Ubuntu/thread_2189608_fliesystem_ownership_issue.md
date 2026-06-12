---
title: "fliesystem ownership issue"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by gth65 on 2013-11-23
I am quite depressed by the regularity with which any little requirement slightly out of the ordinary in ubuntu has the capacity to infuriate me for hours before crushing any illusion of competence I may have built up over time.

I've just spent 4 hours trying to uncompress a archive onto an SD card. It should have been a 30 second job - but instead I have a headache, sore shoulders, short temper, and a partition on the sd card that ubuntu refuses to allow me to do anything with...

My goal, is to install uElastix onto a Raspberry Pi. This requires a small fat16 partition, and a large ext3 partition on an sd card each with a supplied archive expanded into them. Following the instructions [here]("http://www.uelastix.com/#") seems simple enough until I get to the part that just says "Mount both partitions..." File manager in 12.04 refused to mount them. The "mount" command from a console wouldn't do it either. I tried everything I could think of until the system became unresponsive. So I rebooted the machine to start from scratch, but absent mindedly (in my frustrated state) left the sd card in the reader while the machine booted.

Once the boot was complete, both filesystems had auto mounted. Hooray I though - somewhat prematurely, as the archive for the fat16 BOOT partition expanded perfectly into place. No such luck with the ext3 rootfs partiton. While I was apparently the owner of the "BOOT" file system, I was not the owner of "rootfs". [WHY???] I have sudo chown'ed /media/rootfs in the console, with no error - but also with no change in ownership. It is still the property of root, and I still can't have it! I had half a day to try to get uElastix working, which is now gone and I can't even copy the files onto the SD card. Why does it always have to be so hard?

I'm sure there will be a straight forward answer (and thanks in anticipation for those that point it out), but my inability to find it is indicative of why despite the strongest desire to do so, I can't quite break completely free of the Redmond megolith...  Oh well, time for a Bex and a good lie down.

---

### Post by CatKiller on 2013-11-23
Root being the owner of something you're going to boot from is entirely sensible. I would suggest extracting the files and then using a root file browser (with gksudo nautilus) to copy those files to where you want them.

---

### Post by gth65 on 2013-11-23
> **CatKiller said:**
> Root being the owner of something you're going to boot from is entirely sensible.

I have no argument against the logic of the outcome (even though I suspect it will boot from the BOOT partition rather than the rootfs one I was having trouble with.)

> **CatKiller said:**
> I would suggest extracting the files and then using a root file browser (with gksudo nautilus) to copy those files to where you want them.

As predicted - a straight forward suggestion that worked just as easily as I had hoped my first attempt would have - Thanks. Just for reference, what is the difference between sudo and gksudo? and also, how does one go about finding the file name of an application to use in the console, when the gui version uses a different name? (eg File Manager:Nautilus) - I spent ages trying to find the console version of the "Archive Manager" gui application. It's easy if you already know, but impossible if you don't...

Thanks again

---

### Post by ajgreeny on 2013-11-23
> **gth65 said:**
> As predicted - a straight forward suggestion that worked just as easily as I had hoped my first attempt would have - Thanks. Just for reference, what is the difference between sudo and gksudo? and also, how does one go about finding the file name of an application to use in the console, when the gui version uses a different name? (eg File Manager:Nautilus) - I spent ages trying to find the console version of the "Archive Manager" gui application. It's easy if you already know, but impossible if you don't...

Thanks again

The difference between sudo and gksudo is simply command line utility vs GUI application, so, for example you use **sudo parted** to use the command line application parted and **gksudo gparted** to use the GUI version gparted.

How you can find the name of a command line utility is a bit of a difficult question to give a simple answer to, and your example is a good one to try and explain about a bit more.  The GUI Archive-manager is started in command line with the command **file-roller** but that just opens that GUI application.  There is no direct equivalent command line application as file-roller is just a front end for many of the archive apps such as the various zip, rar, unrar and tar utilities.

---

### Post by gth65 on 2013-11-26
> **ajgreeny said:**
>  The GUI Archive-manager is started in command line with the command **file-roller** but that just opens that GUI application.

Thanks for the explanation, but how is it that a non-guru is supposed to be able to associate **Archive Manager** with **file-roller** (for example). There is apparently no logical connection between the two, and so far as I'm aware, no lookup table anywhere that says *X* gui application can be started with *Y* cli command. As I said previously - if you know, it's simple. If you don't, it's impossible. It seems designed to preserve the gnostic supremacy of the Illuminati, and provide a barrier to competence for everyone else...

---

### Post by bab1 on 2013-11-26
> **gth65 said:**
> Thanks for the explanation, but how is it that a non-guru is supposed to be able to associate **Archive Manager** with **file-roller** (for example). There is apparently no logical connection between the two, and so far as I'm aware, no lookup table anywhere that says *X* gui application can be started with *Y* cli command. As I said previously - if you know, it's simple. If you don't, it's impossible. It seems designed to preserve the gnostic supremacy of the Illuminati, and provide a barrier to competence for everyone else...

If you become enlightened, do you become one of the Illuminati?  

The use of gksudo (gksu) vs sudo has more to do with *the environment that the application runs in* (GUI vs the terminal) and not so much as whether you can launch the application from the terminal.  The command gksudo sets up a different set of environmental variables than what the sudo command sets up.  A good example of this is the use of a text editor.  The application ***gedit***  is an editor that is a GUI based application.  You can launch it from a terminal but it runs in a graphical environment.  On the other hand ***nano*** is an editor the runs in a text based environment (e.g. the terminal).  You launch ***nano*** from the CLI and it runs in that terminal.

Normally you don't launch GUI based applications via the terminal.  For the most part the only need to do that would be for a text editor or to run Nautilus (files) or on occasion Firefox.  All three are well known.  In the long run only the text editor and Nautilus really count as the problem is with manipulating (saving, copying, etc) files, not so much running the actual application.

Experience is the best teacher.  Keep asking questions.  There is no all seeing guru out there.  The IT field is to vast for that to happen.

---

### Post by heir4c on 2013-11-26
You can work from inside the terminal as root, type:
```
sudo -i
```
You can now use all the command that are be used in the HowTo.
for mounting use the command: mount
```
mount /dev/sd*1 /dev/sd*2
```
*=the character of the disk you use.
You can use "Disk-Utility to see what character he use.
Or you can use this command to show some info:
```
parted -l /dev/sd*
```
If you not work with root permissions, use:
```
sudo parted -l /dev/sd*
```

To use chown maybe you have to use the option -R (look for more info to the man-pages with the command: man chown ) 
```
sudo chown -R ......
```
But if you work with root permissions from the terminal you don't have to change the permissions.

---

### Post by bab1 on 2013-11-26
> **heir4c said:**
> If you not work with root permissions, use:
```
sudo parted -l /dev/sd*
```

This is a little misleading.  I believe the writer means if you are not **already** the root user use sudo.  Parted always needs the root user (superuser) to call it.  This is what lyou get if you are **not running** as root (sudo or sudo - or su to root)```

$ parted
WARNING: You are not superuser.  Watch out for permissions.
/dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.
Error: No device found                                                    
Retry/Cancel?                           
```

---

### Post by heir4c on 2013-11-26
Yes, that's what I meant. ThanX bab1.


But, before I use 14.04 (and 13.10) I don't have to do that. I could use (for example) fdisk -l or parted -l and I don't have to be root. (I thought, It warning me that I should better run as root)
Now it is changed. Now I need to use sudo.
Strange but safer.
Edit: 
But maybe when I run this command in the past, maybe I had already used a sudo command in the terminal and had still the root permissions to act like that. Maybe that is why I think I don't have to use the sudo. ??

---

### Post by bab1 on 2013-11-26
> **heir4c said:**
> Yes, that's what I meant.

But, before I use 14.04 (and 13.10) I don't have to do that. I could use (for example) fdisk -l or parted -l and I don't have to be root. (It warning me that I should better run as root)
Now it is changed. Now I need to use sudo.
Strange but safer.
Interesting.  That was from a Ubuntu 12.04.3 machine.  I've always used sudo. I would not have seen the difference.  :-)

---

### Post by heir4c on 2013-11-26
bab1 I have Edit my post above. See the last line.

---

### Post by bab1 on 2013-11-26
> **heir4c said:**
> bab1 I have Edit my post above. See the last line.
Maybe you were correct the first way.  See the red below ```
Failure to communicate with [COLOR="#FF0000"]kernel device-mapper driver[/COLOR].
```
It could be that the kernel driver was updated.  There have been a lot of kernel updates.

---

### Post by heir4c on 2013-11-26
Ok, but I get here also the permission issue here (Not the 'Failure' message) so I use sudo in the future. It's better and safer to do that anyway.

---

