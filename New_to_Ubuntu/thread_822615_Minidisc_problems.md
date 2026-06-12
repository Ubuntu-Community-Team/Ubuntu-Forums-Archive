---
title: "Minidisc problems"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by taunting on 2008-06-08
Hi all!

Please help. I'm a noob.

I've got issues mounting my Sony Hi-MD Minidisc player MZ-NH900 on Ubuntu Gusty. It recognises it as an external hard-drive but refuses to mount it.

Does anyone know how I can either mount it or know of a programme that will allow me to take the omg files from it and turn them into WAVs?:popcorn:

Thanks bundles,
Taunting

---

### Post by cprofitt on 2008-06-08
tagging your post for the unanswered posts team. Hope someone can help you.

---

### Post by ibuclaw on 2008-06-08
Hi there.

Unfortunately I cannot test if any of this stuff works. (I do have a NetMD, but it is old and battered in, won't connect).

But here are two links you can check out, see if there is any useful information:
[http://www.minidisc.org/NetMD_faq.html](http://www.minidisc.org/NetMD_faq.html)

[http://tuxmobil.org/player_linux_survey_sony.html](http://tuxmobil.org/player_linux_survey_sony.html)

Regards
Iain

---

### Post by mgmiller on 2008-06-08
If it's an external USB device, try this:

First, you need to figure out where it is being seen in /dev
so run the command:
```
sudo fdisk -l
```

and look for the entry for the drive.  You may need to unplug and replug the USB cable for it to appear.

Once you know the device name use the pmount command to mount it.

If the fdisk command showed you the drive is /dev/sdg and you want to mount it as "Minidisc"
enter the command:
```
pmount /dev/sdg1 Minidisc
```

Look in /media and you will see a new folder called Minidisc.  

To unmount the drive, use the command pumount with the name of the mount point.
For our example:
```
pumount Minidisc
```
and the entry should disappear from /media

You can now make buttons for your panel to mount and unmount and save a bookmark in nautilus for the mounted location to semi automate the whole thing.

---

### Post by bowsider on 2011-01-28
Hi,

I've found it hard to find any good info on this topic.

I can see my minidisc player (Sony Hi-MD RH10) with the lsusb command:

Bus 006 Device 002: ID 054c:0219 Sony Corp. Net MD

However I see only my hdd with the fdisk -l command.

Anyone know how to get progress with mounting a minidisc like this?

I'm on Lucid Lynx.

Thanks.

---

### Post by Uschiekid on 2011-08-06
Hi

I wrote on another topic, but this seems closer to my problem, as I have the exact same issue as bowsider wrote on Jan 28 of this year...and like he/she, i have had problems finding any information on this topic.

I've been using ubuntu for awhile, but just decided recently to try to get a few things working in ubuntu that i'd previously not bothered to try.

My minidisc player is Sony NetMD MZ-N920 and i'm using Ubuntu lucid lynx 10.04 as well.

Any ideas how to get the needed info to mount under fdisk -l command would be greatly appreciated!

---

### Post by Uschiekid on 2011-08-23
bump

---

