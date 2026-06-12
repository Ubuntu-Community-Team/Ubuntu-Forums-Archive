---
title: "Ubuntu marks my healthy harddrive as read only."
date: 2011-11-15
forum: New to Ubuntu
---

### Post by Chikaka on 2011-11-15
I decided to give Ubuntu a go (my first serious try at Linux) and got to
installing 11.10 on an old Via SP-8000 i had never gotten around to using.

The installation goes fine, i can install updates, and installing software from
"Ubuntu Software Center" also works ok (only installed VLC and Audacity, but no errors).

The issue i have is that Ubuntu uses VESA instead of OpenChrome-drivers for my
integrated graphics on the SP-8000, and i searched for solutions on how to create
the old xorg.conf or the current version of it.

Tried first to do "sudo Xorg -configure" and got the message:
"Fatal server error:
 Server is already active for display 0
         If this server is no longer running, remove /tmp/.X0-lock
         and start again"

Figured since i was logged in to the graphical interface that was the problem...
Googled a bit more and found what seemed to be the solution for me:
I should reboot the computer, hold in shift just before GRUB loads, select recovery mode,
select root;"Drop to root shell prompt" and then try "sudo Xorg -configure" again.

So i did that, and now i got the message:

"Fatal server error:
 Could not create lock file in /tmp/.tx0-lock"

I tried doing the same while logged in with my username at the root terminal and got:

"sudo: Can´t open /var/lib/sudo/daniel/console: Read-only file system

 Fatal server error:
 Could not create lock file in /tmp/.tx0-lock"

Went searching again for some fix for that... and found that it likely was problems with my
harddrive that forced Ubuntu to set it to read only... sure enough the harddrives i had lying
around were all older Seagate 120GB SATA and 200GB PATA ones, and the first one i tried was
one of the 200GB PATA ones, SMART Data showing (ID 5) Reallocated Sector Count being over the
threshold, and (ID 197) Current Pending Sector Count was at 236 or something that silly... the
disk was a coaster-to-be, i threw it in a corner for future destruction.

So i went ahead the 2 following PATA 200GB drives i had, they were not in critical condition
like the first one i had used, only 2 and 3 Reallocated Sector Count (from what i understand
it´s never good with any reallocated sectors, but that i read harddrives have space reserved
for 100 reallocated sectors, and the "danger" threshold is set at 36). 2-3 allocated ones could
have been worse. But no, same problems with both of those as the first one, file system set to
read only.

Now i plugged the 2 120GB SATA drives in to check if either of those were 100% ok, and
luckily 1 of them had 0 Reallocated Sector Count (ID 5) and the first of the disks to
show up as "Disk is healthy" in SMART Status.
Installed Ubuntu for the... 6th(or something) time and was hoping it should be ok, but...
I still get those error messages that i got on the previous "not 100% ok" drives, is there
any other reason Ubuntu will force the filesystem to remain read-only?

Sorry for a longer post than intended, and if i have missed something stupidly easy that 
would have made the problem a non-issue!

Not that it helps or should matter, but the SATA controller refuses to recognize
my 2 WD 1.5 TB drives (even when jumpered down to lower SATA speed) so i will end
up getting a new low-power computer soon anyway to work as a media server (that was
my reason for getting the SP 8000 working with Ubuntu)

Any help is appreciated! I will stick with Ubuntu, even if i have to
get a new small computer for my mediaserver.

---

### Post by gordintoronto on 2011-11-15
Your story began as a problem with your video adapter, then turned into a problem with your hard drive, right? I couldn't follow the sequence.

What CPU is in your computer? What video adapter? If it's going to be a media server, why do you care about video performance?

Could you start at, "I installed a healthy hard drive..." and give a blow-by-blow?

---

### Post by Chikaka on 2011-11-15
I thought the reason Ubuntu would not let me write to the hard drive was because it was
about to break. But a fully working hard drive was also flagged as read only.

I want a working graphics adapter to not make the browsing on the screen painfully
slow, i´ll use it occasionally for browsing (have it hidden in the kitchen), and i tried
Youtube... got about one frame every 5 second on a non-hd clip.

So my current problem is; [B]Why is Ubuntu marking my hard drive as read only in
terminal even when i have logged in, and how come i can install programs
when running the UI?
[/B]Is it something as simple as permissions?

I guess i could have done it alot shorter by just saying "I made sure that the hard drive was OK" :D

The CPU is a fanless C5P Nehemiah 800 MHz which Ubuntu does recognize, and the built
in GPU is a  S3 Graphics UniChrome™ Pro. I know it´s a fairly old piece, but it should be
enough to run a Samba share on my network and listen to music with in the kitchen. I hope! 
Here´s the now dying homepage for it:
[http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?id=261](http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?id=261)

---

### Post by gordintoronto on 2011-11-15
> **Chikaka said:**
> ...I want a working graphics adapter to not make the browsing on the screen painfully
slow, i´ll use it occasionally for browsing (have it hidden in the kitchen), and i tried
Youtube... got about one frame every 5 second on a non-hd clip.

So my current problem is; [B]Why is Ubuntu marking my hard drive as read only in
terminal even when i have logged in, and how come i can install programs
when running the UI?
[/B]Is it something as simple as permissions?

The CPU is a fanless C5P Nehemiah 800 MHz which Ubuntu does recognize, and the built
in GPU is a  S3 Graphics UniChrome™ Pro. I know it´s a fairly old piece, but it should be
enough to run a Samba share on my network and listen to music with in the kitchen. I hope! 
Here´s the now dying homepage for it:
[http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?id=261](http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?id=261)

Your CPU is really quite slow, and you have a dreadful video adapter. I'm not surprised it can't play videos at an acceptable rate. However, it should be fine as a file server and music player.

If you can browse, your hard drive is not read-only. Can you post Disk Utility output? What makes you think the hard drive is read-only?

---

### Post by Chikaka on 2011-11-15
It should be able to play Youtube if the OpenChrome drivers worked, and it wasn´t
using VESA. The computer was running faster when it had XP installed.

And the "read only" issue i mentioned in my first post, it´s what i get back when i
start in recovery mode and go to root to try and create xorg.conf.
[I]"sudo: Can´t open /var/lib/sudo/daniel/console: **Read-only file system**

 Fatal server error:
 Could not create lock file in /tmp/.tx0-lock"[/I]

Any PC i have owned played videos less choppy than the S3 with VESA drivers. :(
If only i could make "sudo Xorg -configure" to work and get Ubuntu to use OpenChrome.

---

### Post by thatguruguy on 2011-11-15
... 

Next time, I'll read your question better, I promise.

---

### Post by thatguruguy on 2011-11-15
Can you create a file in your home directory?

---

### Post by Cyclane on 2011-11-15
Doesn't recovery mode boot to RO (Read-Only) automatically? 

Use the following command to mount is as RW:
```
mount -o remount,rw  /dev/sdXY
```

---

### Post by Chikaka on 2011-11-16
> **Cyclane said:**
> Doesn't recovery mode boot to RO (Read-Only) automatically? 

Use the following command to mount is as RW:
```
mount -o remount,rw  /dev/sdXY
```

Thank you! "mount -o remount,rw  /dev/sda1" lets me run "sudo Xorg -configure" and
create xorg.conf, and luckily it also lets me delete the xorg.conf from /etc/x11/ every
time i mess it up trying to get OpenCrome to load! [-o<

Now i just gotta figure out why i end up with 3 ***Section "Device"***, each with a
corresponding ***"Monitor***" and "***Screen"*** ***0***, ***1*** and ***2***. First device is openchrome, second
is fbdev and third is VESA... i tried deleting fbdev and VESA devices, but nothing
changed, Ubuntu still loaded OK when rebooting, then i deleted "***Screen***" ***1*** and ***2***, but
Ubuntu locked up on the loading screen. Will try to replace all device driver with
"openchrome" and hope something great happens!

System info should show Graphics Driver OpenChrome when it´s loaded, or is that too
easy a way to check? Now it shows "Driver Unknown, Experience Standard" :o

---

### Post by Chikaka on 2011-11-16
Marking it as solved since the issue i have now has nothing to do with the harddrive being read only.

I like Ubuntu more today than i´ve done the last week!:popcorn:

---

### Post by JKyleOKC on 2011-11-16
Welcome to the ever-changing world of *buntu video support!

As recently as four years ago, the video situation was reasonably normal. The Xorg.conf files were standard and it was fairly easy to get things working. Then, starting in 2008 with the Hardy Heron releases, the system began to quit depending on Xorg.conf, and instead configured itself during the boot process according to what it discovered present in the system.

So long as your system components were reasonably similar to those used by the developers and testers, this worked great and removed the need for diddling with Xorg.conf. However if there were significant differences, you could come up with a black screen and no obvious way to fix it. Fortunately, the system still recognized the Xorg.conf file if one existed, and used it instead of doing its own discovery. Thus installing an appropriate Xorg.conf could fix the black-screen situation.

It's still a valid solution, but using the automatic configuration tools may not help much. You need to find out just what needs to be in the file to support your hardware. Having three devices is not really a problem; the fbdev device is used during the boot sequence before the video drivers are fully loaded, and the vesa device is a failsafe version that works with most graphics hardware, but not very well with any of it. I'd leave it available for use as a parachute.

For now your best bet is to search Google for "xorg.conf" and learn more about the meaning of each section of this file. It has zillions of possible options, and each specific video driver adds a few dozen more of its own. Be careful with monitor settings if you're still using a CRT monitor, since bad values in the file can cause the monitor to release its magic smoke and retire from the land of the living, but most of the other settings are safe to monkey with...

---

