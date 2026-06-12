---
title: "attempting to boot 14.10 gnome, studio from dvd image. alongside win 7. epic fail"
date: 2014-12-17
forum: New to Ubuntu
---

### Post by noobiedoodbydoo on 2014-12-17
i'm running a 64bit amd laptop with windows 7 home installed.
and for the time being it is vital to work tools to let it remain installed.

so, i downloaded ubuntu 14.10 (i think gnome?) desktop LTS, 64bit, .iso.torrent zip to windows, and burned it to disc.
i actually expected as with officiual ubuntu dvd discs that i could run it from the disc, but nothing happened. no boot op[tion or anything of that sort.
so i had tyo let windows boot,then went into the disc manually,and opened wubi.exe.

i ran the installer which took an hour to download, even though as far as i know most of the needed files must have been on the disc already.
i chose the ubuntu studio option.

then when a sort of boot screen appeared, albeit rather squinted down and to the right an inch or so (due to external monitor?) asking me at bottom to go back, quit, or install.  i tried to choose install but constantly got a root partition error window which asked me to cl;ick ok, but just kept coming back.
googling only gave me various instructions which were impossible to perform when the screen i saw before me was my only option (of course the "back, install,quit" options were inactive due to the overlain mini window telling me of the partition error (i hadnt been given any option to create a partition, and was by now rather fed up due to not having wanted to fully install as yet anyhow) and asking me to click "ok" which, as mentioned only brought back the same error window.
round in circles.
i could think of no other choice but to manually shutdown by pressing and holding down the power button till the laptop switched off.

i am guessing my best option is to uninstall wubi.exe, then find a better option of apparently bootable dvd image that WILL boot straight from a burned disc?
and that perhaps, as i think it was gnome, choose another style of ubuntu?

so, why wouldnt it boot from disc? 
what can i do to ensure it will boot from disc?
and was gnome a good idea for a relative newbie?

---

### Post by Bucky Ball on 2014-12-17
Welcome. Wubi is no longer supported so I suggest we try and get to the bottom of why the regular installer was not working.

You mention nothing happened, but what did actually happen when you booted from the Ubuntu install disk/USB? Blank screen? A cursor?

If you are trying from a disk, perhaps try burning a USB instead and booting from that to see if that makes any difference.

---

### Post by noobiedoodbydoo on 2014-12-17
> **Bucky Ball said:**
> Welcome. Wubi is no longer supported so I suggest we try and get to the bottom of why the regular installer was not working.

You mention nothing happened, but what did actually happen when you booted from the Ubuntu install disk/USB? Blank screen? A cursor?

If you are trying from a disk, perhaps try burning a USB instead and booting from that to see if that makes any difference.


hi,thanks for a rather speedy reply there bucky ball!

well, i ran an installation from wubi.exe from ubuntu 14.10's own .iso.torrent rar folder via download link, earlier thgis morning, it gave me a window with fields to enter username, and password, and choice of form of ubuntu, xubuntu, ubuntu, ubuntu studio and so on.
i selected ubuntu studio, then it began to download for around an hour.
beiung rather tired by this time i'm not 100% certain what happened between then and getting as far as another dialogue box/window (no partition option was given at all that seemed obvious unless the first wubi window contained that within it's options in a dumbed down form,but i dont think so at all) that then asked me to download ubuntu studio, (and after first fail when looking through iobit uninstaller in win 7 it said the ubuntu studio package contained 0kb, 2nd attempt gave me around 19gb i think it said?) and it seemed to download something at least on 2nd attempt, but still no means of partitioning given.

it then brought up a window asking if i wanted to install, (from the download i'd say,not disc,and tried a 3rd time without the disc with same result)
and gave 3 option, "quit/back/install". 

but i could not get past any of these as one window popped up saying roughly that there were too many partitions (?), with a button to click saying ok.
as soon a i clicked "ok", up pops another dialogue window saying something like "error no root partition" with an "ok" button.
each time i click that button, it just brought the same notification up,with no way of fullfilling it's suggestion of going to partition menu. so it just went round in a circle. and had to close down laptop manually from the "on/off" button"as there was no means of controling or accessing anything but that error window,so had to abruptly switch off by that means.

i havnt a USB device at the moment and it may be a few weeks before i can afford one.
however my dvd doc drive appears to be fine, and i have used it successfully to run ubuntu 14.04 from before, and then do a full install with ubuntu alone.
i did however this time burn the ubuntu iso image onto a dvd formatted as a fUSB-drive style burn. was this a bad idea?

it is very frustrating as i simply wanted to boot from the disc, and not full install yet till i've got proper space to partition more adequately untill i get my old pc going again to run ubuntu on it's own.

i apologize for my tired sleepy untechnical writing style here today,and hope explained enough.
thank u warmly, paul

---

### Post by grahammechanical on 2014-12-17
These are the official instructions for burning the ISO image from a Windows Installation. Just so you can confirm that you are doing that correctly. I do not have Windows. So, this is the best that I can offer.

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

Remember, when we use wubi.exe we are in fact installing a Windows application inside Windows. And we remove the Wubi install the same way as we remove any Windows application that we have installed. If you are going to continue using wubi.exe, then it may be better to un-install any previous failed attempts.

Regards.

---

### Post by yancek on 2014-12-17
> but i could not get past any of these as one window popped up saying  roughly that there were too many partitions (?), with a button to click  saying ok.
as soon a i clicked "ok", up pops another dialogue window saying something like "error no root partition" with an "ok" button.

If you have downloaded the Ubuntu Studio iso it should be about 2GB not 19GB.  If you actually burned it as an image to a DVD and are trying to boot with it, the messages showing above would indicate that you are using and MBR system and you already have 4 windows primary partitions.  You can't create any more.  You would have to delete a partition which would delete all of its data in order to create another partition.

If you are trying to use the no longer supported wubi method, you should be able to do that if you have enough space inside one of your current partitions.   The official wubi documentation page is at the link below.  Looks a little outdated.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by hakuna_matata on 2014-12-17
> **noobiedoodbydoo said:**
> 
but i could not get past any of these as one window popped up saying roughly that there were too many partitions (?), with a button to click saying ok.
as soon a i clicked "ok", up pops another dialogue window saying something like "error no root partition" with an "ok" button.

Maybe, [bug 1385930]("https://bugs.launchpad.net/wubi/+bug/1385930") ?

_Recommendation:_ Try an install without Wubi
If this is not what you want, a workaround is possible: [http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861](http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861)

---

