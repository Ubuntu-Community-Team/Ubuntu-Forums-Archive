---
title: "update ubuntu 32bit to 64bit"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by biji on 2008-11-10
Hi All,
i have mistakely installed 32bit version on my 64bit laptop.. is there any easy way to update form 32bit to 64bit... 
and i want to ask what are pros and cons from using 64bit version
thanks a lot

---

### Post by mapes12 on 2008-11-10
Hmmm I think you will have to do a fresh installation of the 64 bit version. I haven't come across a 32 bit to 64 bit upgrade route before.

---

### Post by pzs on 2008-11-10
I moved from 32 to 64 bit about 6 months ago. I created a new partition for it, so that I could go back to 32 bit if I had problems. It also helps to  migrate files over - you can just mount the 32 bit installation and copy what you need. I never needed to boot back into 32 bit, but it was nice to have it there.

This thread:

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

provides oodles of information on why you might want to upgrade (or not). Personally, I did it because I'm running some computationally intensive software that works better on 64 bit. 

Running 64 bit is almost exactly the same as 32 bit. The only major difference is that it's a bit harder getting flash to work on browsers, but there is copious documentation (linked from that thread) on getting this to work.

Good luck! :)

---

### Post by biji on 2008-11-10
wow you are happy 64bit ubuntu user ^^ glad to hear that..
how about 3d accel is it work? (compiz and intel) and basicly i'm using openoffice, firefox, pidgin, and eclipse.. see if those apps run smoothly

---

### Post by pzs on 2008-11-10
I use all of those. Yes, they run smoothly, although I haven't used Eclipse much since making the switch. Compiz works fine.

Oh, the other thing I struggled with was Java applets, but these aren't exactly common these days so I never bothered to get it fixed. I'm sure you can get it to work if you really need to.

---

### Post by biji on 2008-11-10
Thanks.. so I will try  64bit version of ubuntu intrepid

---

### Post by Paqman on 2008-11-10
> **pzs said:**
> The only major difference is that it's a bit harder getting flash to work on browsers, but there is copious documentation (linked from that thread) on getting this to work.


That thread is pretty old. These days there's no extra work required at all. Just install flashplugin-nonfree (which is included in ubuntu-restricted-extras, btw) and all the magic will take place behind the scenes to install 32-bit Flash into your 64-bit browser.

---

### Post by biji on 2008-11-10
well..... tried ii 64bit live cd ...... flawless!
and..... for eclipse users.. i see eclipse 64bit version so don't worry about that
wondering if anyone experience problem with wine in 64bit?

---

### Post by WRDN on 2008-11-10
I run a both a 32bit and 64 bit (current) Ubuntu installation, and I found found the 64bit version to be slightly more stable. As for WINE, I have found it to be identical on both 32 and 64bit installations.

---

### Post by biji on 2008-11-11
yes... installed to my hardisk... everything run smooth...
some tips for wine users, type this to enable 3d acceleration in wine:
export LIBGL_DRIVERS_PATH='/usr/lib64/dri:/usr/lib32/dri'

---

### Post by heggink on 2008-12-04
From what I could tell, moving from 32 to 64 requires a fresh install + restore of backup/settings, correct? Is anyone aware of an 'upgrade path' to more or less automatically migrate frmo 32 to 64 (like from 8.04 to 8.10)?
Thx. H

---

