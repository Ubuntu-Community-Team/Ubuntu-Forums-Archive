---
title: "Linux punked AGAIN!"
date: 2006-07-09
forum: Other OS Talk
---

### Post by rbalfour on 2006-07-09
--------Start of Rant------------

So I am at a friend's house helping him reinstall windows for the billionth time. During this time, I am telling him how great Linux (Ubuntu), even wearing my ubuntu black t-shirt ([http://www.cafepress.com/ubuntushop)](http://www.cafepress.com/ubuntushop)). He just ragging on how hard Linux is and how he is a hardcore windows user...right...
How Linux can't help him with his problems, just make things worse. So it goes on like this for 2 hours, after we get everything setup, he pulls out a cd-rom, It's a AcronisMeida boot disk. ([http://www.acronis-true-image.com-http.com/](http://www.acronis-true-image.com-http.com/)) he telling me a friend said this was GREAT for backing up a hard disk to an image. Nice compression and everything. So I say "okay", reboot the computer with this great cd, as he is explaining this is a GREAT "windows" utility, riiight, never seen one of those. So a the cdrom is booting, yep looks like a windows PE disc, he is clicking thru, the screen goes black and "Starting Acronis True Image..." nothing else, another windows xp like screen appears, really clean and understandable menu. so the backup is started to a usb drive, 50GB hard disk with 4.5GB used, ahhhh...bloat-ware. this is going to be hugh image file. 20 mins later it's done. file is only 1.3GB in size, I yelled, "no way"..damn that will be a first. Windows xp app that boots from a cdrom and takes a total image of the HD and compresses it into 1.3gb..

he clicks the "reboot" button...the cd-rom starts to whirl, here comes another black screen "shutting down kernel", what?! windows xp, shutting down kernel...hmmmm...after the pc is rebooted, I ask my friend, "can I see that cdrom for a second?", throw it into my trusty Ubuntu laptop...take a quick look at the contents. what do I find???

> 
[start]

echo Starting Acronis True Image...

initrd ramdisk.dat /s

kernel kernel.dat quiet

quiet on

mbrcrcs on

vga vesa



[continue]

sysboot /active



[bootmgr]

echo Press F11 for Acronis Startup Recovery Manager...

default continue

delay 30

bootmenu 389


yep, as sure as hell, it's a Linux boot disc with a nice "copy" of windows xp GUI interface. head over to their web page ([http://www.acronis-true-image.com-http.com/#3](http://www.acronis-true-image.com-http.com/#3)) can you find Linux anyway? I sure the hell can't! Explained to my nice windows friend, Linux may just save your bum next time!

"No respect, I get noooo respect!" -Rodney Dangerfield

"Windows software makers and others, stop dumping on linux and freeloading!"
--------------------End of rant--------------------

---

### Post by .t. on 2006-07-09
Since GNU/Linux is GPL, you should ask Acronis for their source code, and say you'll sue them if you don't. That'd be a laugh!

---

### Post by slimdog360 on 2006-07-10
nice one

---

### Post by hizaguchi on 2006-07-11
Google got me to [here]("http://www.acronis.com/enterprise/support/licensing/").  They mention that their software uses parts that are GPL and LGPL, but I still don't see where you get the source code.

---

### Post by bluenova on 2006-07-11
> **.t. said:**
> Since GNU/Linux is GPL, you should ask Acronis for their source code, and say you'll sue them if you don't. That'd be a laugh!
*If you want to receive the appropriate source code for the software listed above, please [submit a request](http://www.acronis.com/enterprise/my/support/?ab=2) to Acronis technical support.*

-----------

But I don't think it's legal for them to label it as shareware if it uses software under the GPL licence no?

---

### Post by bruce89 on 2006-07-11
> **hizaguchi said:**
> Google got me to [here]("http://www.acronis.com/enterprise/support/licensing/").  They mention that their software uses parts that are GPL and LGPL, but I still don't see where you get the source code.

[QUOTE=Acronis]If you want to receive the appropriate source code for the software listed above, please submit a request to Acronis technical support.[/QUOTE]
They do.

It's funny when people say that Linux is rubbish, and then use it in some way without realising.

---

### Post by Ptero-4 on 2006-07-11
It's laughable when some dude says that linux is hard to use and he's using it all the time to save his data without even knowing that he is using it.

---

### Post by 3rdalbum on 2006-07-12
I bet that guy has a Teac interactive digital free-to-air set-top box, too!

---

### Post by enopepsoo on 2007-06-01
> **bruce89 said:**
> They do.

It's funny when people say that Linux is rubbish, and then use it in some way without realising.
like anyone who uses google.

---

