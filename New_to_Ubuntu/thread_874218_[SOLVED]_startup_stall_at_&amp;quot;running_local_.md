---
title: "[SOLVED] startup stall at &amp;quot;running local boot scripts&amp;quot;"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by JimTheSpaz on 2008-07-29
I have an Averatec 3200 laptop that i just partitioned and put ubuntu 7.10 on with my windows xp.  Everything was working perfectly until i tried to use my external monitor with the standard monitor cable and such.  after i had disconnected the monitor and tried to turn my computer on, it stalled at "running local boot scripts." however, it works when the external monitor is attached again.  i believe it is stalling because it believes the monitor is missing and it can't load without it. i know the problem (i think) i just don't know how to fix it.  any help would be greatly appreciated.

---

### Post by sdennie on 2008-07-29
You could try booting into recovery mode (it's an option in the grub menu) and trying the xfix option.

---

### Post by JimTheSpaz on 2008-07-29
i know how to go into recovery mode, but i'm not sure how to go about using xfix.  if you could explain how to do that, that would be great.

---

### Post by sdennie on 2008-07-29
In 8.04, there is a menu when you go into recovery mode.  One of the options is xfix.  You can't miss it.  ;)

---

### Post by JimTheSpaz on 2008-07-29
> **vor said:**
> In 8.04, there is a menu when you go into recovery mode.  One of the options is xfix.  You can't miss it.  ;)

i have 7.10

---

### Post by PmDematagoda on 2008-07-29
In that case, boot Ubuntu in Recovery Mode and run:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then reboot Ubuntu with:-
```
reboot
```
then see if the problem is cleared up in any way.

---

### Post by JimTheSpaz on 2008-07-30
thanks a ton. that solved it perfectly.

---

