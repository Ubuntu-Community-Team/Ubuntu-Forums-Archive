---
title: "re-install ubuntu 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jocko_johnson on 2008-04-29
hello,
I recently added ubuntu 8.04 to my existing Vista setup.  Everything works fine and I dual boot no problem.  However, I was unclear what I was doing in Ubuntu (this being my first time using it) and I changed some settings and moved things around that I now wish I hadn't.

Can someone tell me how I can re-install a fresh copy on the Ubuntu partition?  I don't have any files to worry about losing - I've only had Ubuntu for a few days, but I sort of know what I'm doing now and I just want to start over fresh.

Any help is appreciated.
Thanks

---

### Post by aheckler on 2008-04-29
Just start the installation in the same way you did last time and select it to install on the partition Ubuntu is on now. It will overwrite your broken install with a fresh one.

---

### Post by jocko_johnson on 2008-04-29
Thanks aheckler....
you mean, choose the "manual" option and select the current partition Ubuntu is on now?
I figured that might be it.  This stuff makes me nervous though - I was happy to get through the first install without nuking my machine.

I'll give your suggestion a try.

---

### Post by aheckler on 2008-04-29
Yeah, it will just write a new install right on top of your current (broken) Ubuntu install.

---

### Post by Hesperion on 2008-04-29
Not sure if this question is related (or related enough). If a person were to download and burn a fresh Live DVD of 8.04 on a given day would have download contain everything, fixes, patches, updates, etc. up to that point? In other words: Would a download from today be different than a download done on the first day? This may be apparent to many of you but I couldn't find an answer. ""preciate it.

---

### Post by jocko_johnson on 2008-04-29
aheckler (or anyone...)
I tried to simply re-install and write over the current Ubuntu partition, but I got stuck - when I chose the "manual" option and the window titled "prepare partitions" showed up.

I had these options
/dev/sda1 fat16  41MB  33MB   (  ?  )
/dev/sda2 ntfs   10737MB  4500MB  (vista recovery partition)
/dev/sda3 ntfs   107277MB  62100B   (Vista main partition)
/dev/sda5 ext3  40172MB  4200MB   (Ubuntu 8.04)
/dev/sda6 swap  1768MB  0MB   (Ubuntu recovery?)

I am forced to choose one and then edit or delete.
Do I delete the ubuntu partition and then go back and have Ubuntu install itself into the space I just cleared?  if so, do i delete the recovery partition also?

Or do I edit the current partition?   if so, what options do I choose?

I'm lost and don't want to destroy the windows partition as I have lots of apps installed that I'd rather not waste time reconfiguring.

Any help is greatly appreciated.
Thanks

---

### Post by aheckler on 2008-04-29
Yes, what you would do it first delete the Ubuntu partition and then tell the installer to install Ubuntu on the same partition you just erased it from. I'm not sure if Ubuntu uses a recovery partition; I suspect that sda6 is a swap partition, which, if it is, is OK to erase because Ubuntu will just make another one when you install again.

So what you want to do is leave sda1-3 alone, delete the sda5 and 6 partitions, so then you'd have a large block of empty space at the end of your drive. Then you'd select that space and tell Ubuntu to use that as the place to install.

Hope that's clear lol

---

### Post by jocko_johnson on 2008-04-29
crystal...
sorry to be so dumb and paranoid.  I appreciate the help

---

### Post by garyedwardjohnston on 2008-04-29
Glad to see you are dual booting.  It will take you some time to get used to Linux.  Keep both handy until you're comfortable enough to make the switch permanently.  In time you will, don't worry.  Keep fiddling and playing with the nobs.  That is the true joy of Linux!!!

---

### Post by aheckler on 2008-04-29
> **jocko_johnson said:**
> crystal...
sorry to be so dumb and paranoid.  I appreciate the help

I was the same way when I switched over. :-) Comes with the territory.

---

### Post by kansasnoob on 2008-04-29
Personally I'd use GParted (partition editor) from the Ubuntu Live CD and delete the bad install leaving a blank partition, then I'd restart with the live CD again and just select "Use the largest continuous free space".

NOTE: If you tried to boot to windows at this time rather than using the Live CD you wouldn't be able to because the MBR is messed up with no Ubuntu install.

Then Ubuntu does it's thing while leaving your other occupied partitions alone. 

That allows me more milk and cookie time :^)

---

### Post by kansasnoob on 2008-04-29
Great place top get acquainted with GParted:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Check out the screen shots.

---

