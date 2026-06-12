---
title: "Samsung NC10 - Ubuntu 11.10 backlight flashing at startup"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Adrik Egorski on 2011-10-15
Hi,

I have a Samsung NC10 netbook. I've been running Ubuntu 10.10 and 11.04 on it without any problems. After I upgraded to 11.10, a weird problem appeared.

At startup the backlight starts flashing and it won't stop until I use the Fn+arrow down combination to turn the light to the minimum. After this if I try to turn up the light, one click with Fn+arrow up is OK, but if I click again, the light goes straight to 100% and after a while the flashing starts.

Is this a some kind of bug or is my NC10 broken?

---

### Post by LinuxFan999 on 2011-10-15
How long have you had your netbook?

---

### Post by john__doe on 2011-10-15
hi,

i have the same netbook and the same issue (but for me only when i am with the battery).
i dont think that it's the hardware.

if you need more information, i can provide it too.
thanks for help.

---

### Post by Adrik Egorski on 2011-10-15
> **LinuxFan999 said:**
> How long have you had your netbook?

I've had it for 18 months.

---

### Post by kolinab on 2011-10-15
Hi,

I've got the same netbook and was searching tonight to no avail how to get the backlight settings working. The GUI feedback works but the backlight doesn't change for me at all. I tried to update the firmware using the windows firmware updater but it fails to download . . . 

John_doe if you have more info on how to get the backlight working properly with 11.04 or 11.10 that would be much appreciated!

[edit] I fixed mine. I added the repository ppa:voria/ppa and installed packages samsung-backlight and samsung-tools. Works like a charm! Now that I have the screen brightness issue fixed I'm considering upgrading to oneiric just for fun. Maybe tomorrow . . .

---

### Post by john__doe on 2011-10-15
> **kolinab said:**
> John_doe if you have more info on how to get the backlight working properly with 11.04 or 11.10 that would be much appreciated!

the backlight was working properly with ubuntu 11.04 out of the box. but not with 11.10.
i installed the samsung-backlight package from voria ppa and it now works !!!!
thanks kolinab.

---

### Post by kolinab on 2011-10-16
I guess it might have to do with the system . . . truth be told I don't have a NC10 - I have a NC110. Anyway, after fixing the brightness on this system (actually my wife's) it is a lot nicer to run! She never complained of the screen being dim but in strong light it's nice to have full brightness back.

As a workaround, before I installed the brightness package, I learned that the FN+ up, down function works on the grub menu, so it I set the brightness to max it would persist for the rest of that session.

---

### Post by Adrik Egorski on 2011-10-16
Thank You very much for the help!

I added the voria repository and installed the backlight package and now my NC10 and Ubuntu 11.10 are working very well together: no flashing and the backlight adjustment works fine.

---

### Post by dukeinlondon on 2011-12-11
One thing though, just reboot after installing the samsung-backlight package. For me it didn't work straight after install. But fixed the problem adjusting it and the flashing when on battery power.

---

### Post by Siddhartha Valmont on 2012-01-12
Thanks for the trick.

I have installed samsung-backlight, samsung-tools and even phc-intel as suggested by apt and after a reboot I got the backlight and the keyboard shortcut back !!!!

Validated on a HP Mini 1099ef Vivienne Tam under Ubuntu 11.10 :)

---

