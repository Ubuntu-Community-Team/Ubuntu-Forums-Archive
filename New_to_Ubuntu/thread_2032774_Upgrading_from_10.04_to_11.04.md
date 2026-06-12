---
title: "Upgrading from 10.04 to 11.04"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by barrykgerdes on 2012-07-24
I had 10.04 in a Vmware virtual box and decided it was time to upgrade before the 10.4 to 10.10 upgrade was not available and eventually get to 12.04

The first step to 10.10 went OK (took 4 hours). When I got 10.10 running I was given the opportunity to upgrade to 11.04. This I took.

The upgrade took another 4 hours and appeared to complete OK and I was given the request to re-start.

However on restart I got a command line "grub>" waiting for an input "tab" gives a lot of optional commands but I have no idea what needs to be entered to get the standard 11.04 start up.

Barry

---

### Post by drpjkurian on 2012-07-24
Hi
Why are you upgrading to 11.04 when a robust 12.04 LTS is available?
I suggest you to upgrade to 12.04 or a clean install of 12.04 from scratch if you have messed it up

---

### Post by barrykgerdes on 2012-07-25
That does not answer the question of how to get out of the grub> prompt

I can and have put a new installation of 12.04 but I want to check out the upgrade procedures to get to 12.04 from 10.04

It worked from 10.04 to 10.10, apparently it works from 10.10 to 11.04 except I cant start after the 11.04 upgrade because I don't know what to enter at the grub> prompt

Barry

---

### Post by waynefoutz on 2012-07-25
> **barrykgerdes said:**
> That does not answer the question of how to get out of the grub> prompt

I can and have put a new installation of 12.04 but I want to check out the upgrade procedures to get to 12.04 from 10.04

It worked from 10.04 to 10.10, apparently it works from 10.10 to 11.04 except I cant start after the 11.04 upgrade because I don't know what to enter at the grub> prompt

Barry

You should have been given the option to go from 10.04 to 12.04. The upgrade path between LTS versions is a direct one. I don't recommed it though. Every time I'veran a dist-upgrade it's panned out to be a huge waste of time.

---

### Post by barrykgerdes on 2012-07-25
I thought that would be so but I was only given the option to go to 10.10 before I got the option to go to 11.04. I have read that this type of upgrade can give trouble but I hoped to keep a program intact that takes two to three hours to re-install from scratch.

The thing I really want to know is how to get out of the grub> prompt


Barry

---

### Post by drpjkurian on 2012-07-25
Please try the command ```
startx
```

---

### Post by mastablasta on 2012-07-25
if you got grub prompt then chances are something went wrong with grub update. i would suggest using latest 12.04 verison, booting into live OS and using the boot repair programme.
 
upgrading like that is a waste of time. i too find it out, when i noticed that fresh install will be done withing an hour or so (including updates and a few additional pogs i installed). while every upgrade took me close to 3.5 hours despite the fast internet connection.

---

### Post by barrykgerdes on 2012-07-25
As I already said I have 12.04 on the system as well. Running quite nicely. I was looking to find an answer to the grub> prompt before I remove the damaged program. 

Barry

---

### Post by mastablasta on 2012-07-25
try the boot repair programme then. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Wim Sturkenboom on 2012-07-25
> **drpjkurian said:**
> Please try the command ```
startx
```I doubt very much that, at the grub prompt, 'startx' is available. Might be mistaken though.

---

