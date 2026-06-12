---
title: "Knoppix &quot;This feature needs HAL?&quot; cd/dvd problems"
date: 2008-04-25
forum: Other OS Talk
---

### Post by Eck on 2008-04-25
Hey all!

Just attempting to get some help for a problem I've noticed in Knoppix 5.3.1 when using the persistent disc image feature on a USB Flash drive.

I've noticed that folks posting problems in the Ubuntu forums tend to get at least a discussion going, and often problems do get solved.  Posting to the Knoppix forum, as I have for several peculiarities I've noticed, goes somewhere into thin air.  About the same response results when I post to the Debian forums, although often if someone in the club like, say, a mod like Tina (lavene) posts the same problem I noticed then everyone flocks to help solve it and the answer appears.  Leaves my saying, "huh?"  My post remains unanswered as if I don't exist.  Weird.

Anyway, once a persistent image (knoppix.img) is created and the system is rebooted with Knoppix applying that image, then either logging out and in or restarting from then on, all the cd/dvd drives will appear as icons on the desktop at bootup and none of them are accessible any longer except by K3b or by mounting them with KDE's Kwikdisk.  That nice Knoppix icon that holds the running Knoppix DVD is gone, replaced by one labeled simply "DVD," and additional icons are placed on the desktop for that drive (/dev/hdc), /dev/hdd, and an additional one for /dev/cdwriter and one for /dev/cdrom.  All of the drive icons are useless except for the ones still there that weren't adversely effected, my 2 hard drives and the Sandisk Cruiser Micro USB Flash drive.  Those behave normally and I can mount/unmount them and change read/write mode on them fine.

The cd drive icons are useless.  Inserting a cd into the empty tray (/dev/hdd) does not make a new icon appear and if I try to right click and mount the existing icon I get a "This feature needs Hal" message.

If I open KDE's KwikDisk and click on the drive using that, the cd mounts in /mount/hdd and can be accessed by browsing to /mount/hdd and opening it there. Trying to open /mount/cdrom, which should open it, brings up that "This feature needs hal" thing.

So there is no way to access the running Knoppix DVD from anywhere even though the system is running from it, the KDE autorun stuff doesn't work, and I must use KwikDisk to mount, access or unmount cd or dvd inserted into my empty drive. Strangely, the browser accesses the home html file on the dvd just fine.  Just nothing in /media will open it.

The /etc/fstab is exactly the same as the Knoppix version that is there without the persistent image being used.  

I attempted to upgrade all the hal and dbus stuff thinking there may have been some fixes in the newer Debian Lenny versions, but doing that corrupts the hal package so it is no longer installable.  I've since deleted that knoppix.img and now have an empty Flash drive to start over with.  But since this has happened twice I am sure I'll get the same result.

Relevant lines:

/dev/cdrom /media/cdrom auto user,noauto,exec,ro 0  0
/dev/hdd /media/hdd auto users,noauto,exec,ro 0  0
/dev/hdc /media/hdc auto users,noauto,exec,ro 0  0


Before, and the first boot into the persistent image, those are not on the desktop except for the Knoppix DVD and inserting a disk into /dev/hdd results in an icon being created and it can be used to access the inserted media.

After the boot or logout/in following the first use of the persistent image, icons appear for all those drives on the desktop but no Knoppix icon for the DVD, a DVD icon appears instead that is not usable.  And only K3b or Kwikdisk can make use of the hdd drive.  No way for normal mounting as that stupid "this feature needs hal" message appears.

Any help with this?  Do you think it's a bug or is this behavior normal when running with a persistent knoppix image?

---

### Post by borahshadow on 2008-05-14
I think I have the same problem. I noticed it one day I was trying to connect my mp3 player which acts like a jumpdrive. It would not bring u[ the popup that it normally does so I went into storage media. Instead of having my drive listed like it normally does (XXXGB media) it had hard disk (uuid blah blah blah) and if i tried to click on it it would bring up an error at the little bottom status bar (this feature only available with hal) everything used to work fine I don['t know what happened. This in on kubuntu 8.04 (hardy) and kde 3.5.9. this is also along with a few other strange things that started happening the last few days (Power manager does not load half the time including sometimes after resume). Any ideas would be great. I have reinstalled hal from the package manager and restarted it from the command line. No dice. I really don't want to reinstall I just did shortly after hardy cam out. errr

---

### Post by SunnyRabbiera on 2008-05-14
well first do you have knoppix installed or do you just run it as a live?
I am not an expert on knoppix but I do know about HAL and I may have a solution for you.

---

### Post by Eck on 2008-05-14
borahshadow on Ubuntu seems to have encountered similar there, but mine is Knoppix 5.3.1 running Live from the DVD with a persistant image (knoppix.img) booted along with it on a Sandisk 8GB USB flash drive.

Without booting with the persistent image I can use the drive normally, the Knoppix DVD icon appears on the desktop and can be mounted, opened, and the USB pendrive also can be mounted normally and used.

With the persistent system applied I get the problems I pointed out.  First use works properly along with the Knoppix DVD icon, but then on the 2nd logout/in or restart (first restart or logout/in and things are fine) the problem of all the drive icons for the cd drives appearing on the desktop but no Knoppix DVD icon and none can be mounted normally.  That needing hal error message appears.  Using KwikDisk, I am still able to mount the cd's placed into my second cd drive and use them fine.  But the desktop icons don't change once a cd is placed into the drive and none of the existing ones are mountable through the normal process of right clicking them.  K3b can see and use the inserted cd as well.  The USB drive functions normally, right from the icon.  I can use, access files on the rest of the non-knoppix image portion of the USB drive fine without the use of KwikDisk.

Once the problem happens, future bootups result in the same problems.  All those drive icons appear but are useless with the exception of the USB drive.

Seems to be a problem with how the normal KDE mounting stuff is working with hal, or not working with it in this case.  Seems to lose track that hal is there.

---

### Post by borahshadow on 2008-05-14
I do not have knoppix installed my problem is under ubuntu. New twist when I booted up my laptop this morning my drives showed up normal. Now I had rebooted and shut down yesterday and the problem persisted but this morning it was gone.

I agree that KDE seems to not know hal is there. I have restarted hal from the command line and the problem would still be there but hal was running.

---

### Post by SunnyRabbiera on 2008-05-14
did you try to install the kde-hal-device-manager?
or kdebase-kio-plugins?

---

### Post by Eck on 2008-05-15
No, and I'll check whether they are installed the next time I run my Knoppix.  I don't see how those could have been uninstalled without my knowing it.  That kind of stuff is likely part of the default Knoppix since all the features work unless I'm running Knoppix from a persistent image.

I know that I did aptitude search hal, which should have produced at least the kde-hal-device-manager in the list.  If that wasn't listed as being installed it would have jumped off the page at me.  Knoppix appears to include the entire KDE including recommends and suggests, so it's unlikely it doesn't include the base-plugins by default.  But I will boot up Knoppix with my persistent image (which works fine except for this problem) and check out whether these are installed.

One fella who had responded to someone else asking about this problem a long time ago on the Knoppix forum recommended trying to upgrade hal and udev.  On my previous knoppix.img persistent image I tried that and it destroyed the system as after aptitude as part of its upgrade removed the installed version, dpkg could not successfully configure the new version of hal and attempts to go back to the original version, running the -f switch, etc, were not successful either.  The system could no longer bootup.

---

### Post by borahshadow on 2008-05-20
After mine started working again the next time I rebooted it quit working again.after many reboots it still didn't work. However the next day it did:confused: 

I think this is the same as this bug [https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/89580]("https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/89580")

---

### Post by Eck on 2008-05-21
Well!  Very interesting.  I had no idea it could be a kde package bug.  At first I thought it was just a Knoppix thing until more action appeared on this thread.

Maybe, since there is a bug going, this is something we have some hope of getting fixed eventually.

It may not be exactly the same situation but it's extremely similar.  Some combination of devices triggers the bug and KDE looses its noticing that hal IS there and doesn't run it, and in my case also litters the Knoppix desktop with useless drive icons.  Those drives CAN fully mount discs and use them, but just not in the usual KDE automount or Knoppix right click icon mount ways.

I'll be without computer access, or at least I expect to be, for the next couple of weeks as I travel and visit with my sister and brother.  My Mom passed last week and they couldn't come so now I'm going to them.  So non-computer savvy they don't own one.  But I'm bringing along a Knoppix DVD in case there's a library or somewhere I can get to the net and check my email.  Possibly browse around to keep up with my usual interests too.  Not counting on it but one never knows.

I think my next computer may be a laptop as this is kind of ridiculous.

---

### Post by stream303 on 2008-06-12
> **Eck said:**
> borahshadow on Ubuntu seems to have encountered similar there, but mine is Knoppix 5.3.1 running Live from the DVD with a persistant image (knoppix.img) booted along with it on a Sandisk 8GB USB flash drive.

I'm having the same issue with a setup exactly like yours.  I wondered if I wrote this? :)

I'll try to find a solution, but in the meantime at least for cdroms, I can mount them from the commandline:

```
sudo mount /dev/cdrom  /media/cdrom
```

On a side note, since there is no need for a pendrive to eject, I always use the two boot options of "noeject noprompt".

If I come up with something, you'll be the first to know!

---

### Post by borahshadow on 2008-06-18
I think I found a workaround. When it happens I normally roboot MANY times until it works but once I tried ctrl-alt-backspace instead of rebooting and it worked. Today I was forced to reboot again and so when it came up and had the bug I ctrl-alt-backspaced and it worked. So both times I tried that it worked so maybe you can try it? it seems to work everytime for me.

---

### Post by stream303 on 2008-06-19
I tried your suggestion, but on my hardware, it doesn't work.  I still have to manually mount and unmount my external devices.  Once I mount them, I can use any file manager of course...

Maybe on the next Knoppix spin?!

Thanks for the tip anyway...

---

