---
title: "Slow Boot &amp; Dis oriented logo."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Tux.Ice on 2008-08-26
hello,

my system wasnt up to date so i did an update (i installed all the updates available). NOw, my boot logo looks disoriented, pixelated, and monochrome. ALso it previously did not show any text on boot (setting system clock [ok], etc.) however now it shows lots of text after the disoriented logo shows up (the logo appears only for about 30 seconds and then there is 1 minute 30 seconds of text).The boot process takes 2 minutes to get to login and then another 30 seconds to get to my desktop. 

ANy body have nay ideas what could cause this, and how to fix this?

i probably sound so n00by but im stumped.

---

### Post by Tux.Ice on 2008-08-26
bumpity bump bump bump bump bumpity bump badoo

---

### Post by nicedude on 2008-08-27
if login looks out of place then I would say are you using an Nvidia or ATI graphics card and if so that it probably needs a new driver. If this is the case try envyng as it can manage this all for you.

sudo apt-get install envyng-gtk

and then

sudo envyng-gtk 

as that would start it



One of my systems did that after an update and it was Nvidia related

Hope that helps

---

### Post by Tux.Ice on 2008-08-27
it does not look disoriented. the login is slow. the boot screen looks didoriented. my graphics drivers are up-to-date

---

### Post by bobbocanfly on 2008-08-27
It would probably be handy if you posted a bootchart (shows what is running when you boot)

```
sudo apt-get install bootchart
```

Reboot and post the svg in /var/log/bootchart

---

