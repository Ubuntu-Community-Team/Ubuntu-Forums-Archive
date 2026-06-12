---
title: "Ubuntu throwing off time in Windows"
date: 2017-12-01
forum: New to Ubuntu
---

### Post by littlefoot505 on 2017-12-01
Okay so basically, whenever I boot into my Linux partition and then boot later into my Windows 10 partition, the time is on GMT when I boot into Windows. Not very convenient when you're in America. I'm wondering if there's any way to make that stop. Thanks!

---

### Post by Impavidus on 2017-12-01
[https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876)
Does that help?

On dual boot systems it would be better if all systems agreed on using UTC, else every system tries to adjust the clock for DST, but reconfiguring Ubuntu is easier than reconfiguring Windows.

---

### Post by littlefoot505 on 2017-12-01
Ok thanks. I like having it show the actual time where I am. What I do as a workaround is just turn the auto-adjust off and back on when I boot into Windows and it shows the time in UTC. Could I maybe just disable the auto-adjust and manually adjust it come DST or me being in a different time zone?

---

### Post by leunam12 on 2017-12-01
I think all you have to do is open a terminal and type ```
timedatectl set-local-rtc 1
``` then press enter

---

### Post by littlefoot505 on 2017-12-01
> **leunam12 said:**
> I think all you have to do is open a terminal and type ```
timedatectl set-local-rtc 1
``` then press enter

I'll check into that. Will that change it to UTC on Linux or will it just make it not adjust automatically? I'd rather use my existing workaround than set either system to default to UTC, as I want it to show my local time.

---

### Post by Frogs Hair on 2017-12-01
I use the method at the link, though usually set time from the Linux side. 

 [http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html](http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html)

---

### Post by littlefoot505 on 2017-12-01
Thanks! I'll try that later and let you know if that fixes it (it seems like it will, though). [-o

---

### Post by Autodave on 2017-12-01
Is it like 5 or 6 hours difference? (I can't remember.) I just go into into Win? and change my time zone so that W#in & Linux clocks match. According to Linux, I live in the NY time zone (EST). In Windows, I live somewhere else.

---

### Post by leunam12 on 2017-12-01
> **littlefoot505 said:**
> I'll check into that. Will that change it to UTC on Linux or will it just make it not adjust automatically? I'd rather use my existing workaround than set either system to default to UTC, as I want it to show my local time.It will change Linux to local time and it will be the same than Windows

---

### Post by Yellow Pasque on 2017-12-01
I always adjust Windows to tell it that hardware clock is UTC. [https://wiki.archlinux.org/index.php/Time#UTC_in_Windows](https://wiki.archlinux.org/index.php/Time#UTC_in_Windows)
Then I can select the proper timezone in my multiple Linux distros without Windows messing with my system clock. Did I tell Windows it could alter my system clock? (<-- rhetorical question)

---

