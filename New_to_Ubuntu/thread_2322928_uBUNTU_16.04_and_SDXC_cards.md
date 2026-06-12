---
title: "uBUNTU 16.04 and SDXC cards"
date: 2016-05-01
forum: New to Ubuntu
---

### Post by Clifford_Sarokoff on 2016-05-01
I went from 51.10 to 16.04 and now I cannot read my SDXC cards. Would a fresh install of 16.04 be the answer to my problem?  I've already wasted time trying different suggestions from a Google search. 
I guss what I'm asking is: Has anyone successfully (with a clean install) opened an SDXC  card without any mod?
CliffordS

---

### Post by Bucky Ball on 2016-05-01
You will probably need exfat-utils and exfat-fuse. Install them and try again.

A reinstall is a last-ditch and radical approach and no, it probably wouldn't have made any difference.

---

### Post by Clifford_Sarokoff on 2016-05-02
Already installed exfat-utils and exfat-fuse.  Not happy that I have to go tp Windows 10 to read an SDXC card.  Ubuntu is letting me down.

---

### Post by Bucky Ball on 2016-05-03
Strange. You shouldn't have to. Keep digging. I can read them without issue in 14.04 and 16.04.

(Yep, easiest to blame Ubuntu when something doesn't work. Join the club, plenty of others make the same mistake, or do the work and check the back story. 

Generally, Canonical, Ubuntu, and open-source  have nothing to do with it. Your current level of frustration probably prevented you from finding out why exactly you might be having problems and why sdxc doesn't work natively in Linux/Ubuntu. You might have found this very quickly if you had:

> SDXC adopts Microsoft's exFAT file system as a mandatory feature.

... from Wikipedia. Fancy that. It was created with a Microsoft file system as mandatory! Wonder why it doesn't work natively on Linux. :-k ;)

As I said, with exfat-fuse and exfat-util installed, sdxc works faultlessly for 99.9% of users (thanks to unpaid Linux enthusiasts who have bothered to figure it out probably). You are the .1% unfortunately which would point to something specific with your machine/setup, not anything to do with Ubuntu 'letting you down'. I'd say whoever decided to base sdxc on a Microsoft filesystem has let you down, but that's not at the root of your issue here either I wouldn't think.)

---

### Post by Clifford_Sarokoff on 2016-05-07
> **Bucky Ball said:**
> Strange. You shouldn't have to. Keep digging. I can read them without issue in 14.04 and 16.04.

(Yep, easiest to blame Ubuntu when something doesn't work. Join the club, plenty of others make the same mistake, or do the work and check the back story. 

Generally, Canonical, Ubuntu, and open-source  have nothing to do with it. Your current level of frustration probably prevented you from finding out why exactly you might be having problems and why sdxc doesn't work natively in Linux/Ubuntu. You might have found this very quickly if you had:



... from Wikipedia. Fancy that. It was created with a Microsoft file system as mandatory! Wonder why it doesn't work natively on Linux. :-k ;)

As I said, with exfat-fuse and exfat-util installed, sdxc works faultlessly for 99.9% of users (thanks to unpaid Linux enthusiasts who have bothered to figure it out probably). You are the .1% unfortunately which would point to something specific with your machine/setup, not anything to do with Ubuntu 'letting you down'. I'd say whoever decided to base sdxc on a Microsoft filesystem has let you down, but that's not at the root of your issue here either I wouldn't think.)

First, thanks for the reply.  We have three notebooks running 16.04 and one running 14.04; two Dells, one Sony and one Lenovo. All have the same problem.  However, I have found a solution that works for me. *** I purchased a six dollar external card reader from Amazon, plugged the reader into one of the USB3 slots and I can now read the SDXXC cards.***  I hope this info helps others.
CliffordS

---

### Post by Bucky Ball on 2016-05-07
Excellent find! Strange how that works and the regular way doesn't, but these anomalies do pop up. 

Thanks for sharing and please mark the thread solved to help other (Thread Tools at top right or the second link in my signature if you get stuck). Good luck.

---

### Post by neu5eeCh on 2016-05-09
For what it's worth:

[http://askubuntu.com/questions/579630/formatting-128gb-sd-card-to-ext4-with-gparted](http://askubuntu.com/questions/579630/formatting-128gb-sd-card-to-ext4-with-gparted)

Unless the wrong terminology was used, **Askubuntu** provides a guide for reformatting _SDXC_ drives to ext4. I haven't tried this... yet... but unless there was a mistake, exfat isn't as married to SDXC as claimed.

---

