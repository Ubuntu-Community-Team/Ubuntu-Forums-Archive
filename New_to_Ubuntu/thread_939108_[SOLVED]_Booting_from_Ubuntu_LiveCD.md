---
title: "[SOLVED] Booting from Ubuntu LiveCD"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by EvanRogers on 2008-10-05
OK erlier, in my post, i learned about burning the live CD so, i got the cd and burned it and i cant get my computer to boot from the cd i just keep getting the grub error 15 every way that i try to get it to boot.

i burned the cd as an image using infrarecorder.

---

### Post by kellemes on 2008-10-05
> **EvanRogers said:**
> OK erlier, in my post, i learned about burning the live CD so, i got the cd and burned it and i cant get my computer to boot from the cd i just keep getting the grub error 15 every way that i try to get it to boot.

i burned the cd as an image using infrarecorder.

You need to enter the bios of your system and set the diskdrive to be first in the boot order.

---

### Post by EvanRogers on 2008-10-05
> **kellemes said:**
> You need to enter the bios of your system and set the diskdrive to be first in the boot order.

im sure i did that and it tells me to push f1 to retry and thats all it does.

---

### Post by EvanRogers on 2008-10-05
um can someone help me?

---

### Post by Dj Melik on 2008-10-05
Can you please copy paste the grub error?

---

### Post by EvanRogers on 2008-10-05
Well im not even on that computer, for the fact that i can't get it to boot off of anything but the error is. 

Grub Loading Stage 1.5

Grub loading, please wait...
Error 15

---

### Post by Dj Melik on 2008-10-05
Seems like your grub boot loader is missing/corrupt.

I suggest download another .ISO file and use PowerISO to burn a new copy. Also make sure you burn it at 4x speed.

In my opinion, thats the easiest approach. Good luck mate.

---

### Post by EvanRogers on 2008-10-05
OK my internet connection is slow, so it took me like 20 hours to download it and i did burn it at 4x speed with infrarecorder, i need help, i have the cd it just wont boot.

---

### Post by kansasnoob on 2008-10-05
I've *never* seen a grub error while booting the live cd:confused:

---

### Post by EvanRogers on 2008-10-05
well it happens every time, it just doesnt work and i have no clue how to get it working, is there any number that i can call to have help getting my computer working?

---

### Post by xreaper on 2008-10-05
Try to burn it at the slowest speed possible, and make sure that in the boot sequence your FIRST option is set to CD.

Are you sure the grub error is coming up after you use the live cd? have you tried booting without the live cd and seeing what happens? Because as far as everyone else knows, It isn't possible to get a grub error while using a live cd. It might have something to do with the image file being corrupt, but nevertheless, try to burn another one. I burn mine at 1x speed, just to remove any possibility of error.

---

### Post by EvanRogers on 2008-10-05
> **EvanRogers said:**
> im sure i did that and it tells me to push f1 to retry and thats all it does.

> **xreaper said:**
> Try to burn it at the slowest speed possible, and make sure that in the boot sequence your FIRST option is set to CD.

Are you sure the grub error is coming up after you use the live cd? have you tried booting without the live cd and seeing what happens? Because as far as everyone else knows, It isn't possible to get a grub error while using a live cd. It might have something to do with the image file being corrupt, but nevertheless, try to burn another one. I burn mine at 1x speed, just to remove any possibility of error.

OK well this is what i did, when i messed with my partitions on my computer i tried to restart and got the error, so when i restart without the cd in i get the error also, the first option in my boot sequence is IDE CD-ROM Device. when i put the live cd in then restart it i get the same error. it doesn't really sound like the CD starts spinning..but what do i know. I really need help here. I'll try re-burning.

---

### Post by xreaper on 2008-10-05
hmm... sounds interesting. have you tried checking all of the connections? and also, try to disable all of the other boot options, just for the moment, (ie: boot from first hard drive)

then try to run the live cd.

---

### Post by EvanRogers on 2008-10-05
> **xreaper said:**
> hmm... sounds interesting. have you tried checking all of the connections? and also, try to disable all of the other boot options, just for the moment, (ie: boot from first hard drive)

then try to run the live cd.

When i disable the only other boot option it just tells me to push f1 to retry or f2 to enter boot setup. f2 just takes me to the bios and f1 never works.

---

### Post by EvanRogers on 2008-10-05
Also im sure its not the connections, because the green light underneath the CD drive lights up when i start the computer but i still get the error.

---

### Post by xreaper on 2008-10-05
Have you tried other live cds in your cdrom drive? 

To me it sounds like your CD drive has died,and you'll need to replace it.

---

### Post by EvanRogers on 2008-10-05
> **xreaper said:**
> Have you tried other live cds in your cdrom drive? 

To me it sounds like your CD drive has died,and you'll need to replace it.

Are you serious? haha i like never use it...and i can't see it being ruined. Hmm..interesting tho..god idk i jsut want my computer to run ubuntu. or anything for that matter.

---

### Post by xreaper on 2008-10-05
uhhh the only other thing I can think of.. you are using another computer right? you can always take the cd drive out of it and put it into the one you are trying to boot the live cd in? just temporarily of course.

---

### Post by taladan on 2008-10-05
Burn off a simple rescuedisk livecd or some other small livecd like Damn Small Linux.  Anything that won't take forever to download.  Use that to check your cd drive.  If it does boot from that then I'd suspect you may just have either a bad iso or a bad burn on the ubuntu livecd.  

If it doesn't boot from that, check your data connection to the optical drive and the mainboard, try swapping out a data cable.  Just because the light comes on doesn't mean the drive is in good working order.

Tal

---

### Post by EvanRogers on 2008-10-05
> **xreaper said:**
> uhhh the only other thing I can think of.. you are using another computer right? you can always take the cd drive out of it and put it into the one you are trying to boot the live cd in? just temporarily of course.

Ha yeah like my mom would let me take her computer apart...but i think you might be right, i can't even hear the disk spinning. If i tried putting the disk into the computer i am on rite now it wouldn't automatically install it would it? just to check to see if it works.

---

### Post by EvanRogers on 2008-10-05
> **taladan said:**
> Burn off a simple rescuedisk livecd or some other small livecd like Damn Small Linux.  Anything that won't take forever to download.  Use that to check your cd drive.  If it does boot from that then I'd suspect you may just have either a bad iso or a bad burn on the ubuntu livecd.  

If it doesn't boot from that, check your data connection to the optical drive and the mainboard, try swapping out a data cable.  Just because the light comes on doesn't mean the drive is in good working order.

Tal

I'm downloading damn small linux rite now, i will try to burn that to a cd, if i can get it to boot then should i just download Ubuntu off of the booted damn small linux?

---

### Post by taladan on 2008-10-06
assuming that you've tried burning a couple of different disks with the same ISO, if it boots off of the DSL then you probably do want to dl another copy of the Ubuntu ISO, and check the md5sum when you do to ensure that the dl isn't corrupted.

Tal

---

### Post by kansasnoob on 2008-10-06
How about trying to run the live CD on your moms computer? **Not to install, just to boot it!**

When you boot the live CD you should first see the language screen:

[http://www.psychocats.net/ubuntu/images/installinghardyplus01.png](http://www.psychocats.net/ubuntu/images/installinghardyplus01.png)

Then you'll see this:

[http://www.psychocats.net/ubuntu/images/installinghardyplus02.png](http://www.psychocats.net/ubuntu/images/installinghardyplus02.png)

**DO NOT CHOOSE INSTALL!**

If it boots to that screen I'd check the CD for defects.

If it won't boot on her puter then you know it's a bad burn - maybe not truly burned as an ISO image. Or maybe the md5sum isn't right:confused:

---

### Post by EvanRogers on 2008-10-06
Well thanks for all you're help guys, today i got some new disks and burned DSL to it and that booted my computer up, then i burned Ubuntu to another one and it booted my computer too, im now running ubuntu and its working fine, i guess i had bad disks or bad burns. Thanks again guys.

---

### Post by taladan on 2008-10-08
Glad we could help.  Ya might think about using that little blue ribbon to thank a couple of folks ;)

Happy Ubuntu'ing,

Tal

---

