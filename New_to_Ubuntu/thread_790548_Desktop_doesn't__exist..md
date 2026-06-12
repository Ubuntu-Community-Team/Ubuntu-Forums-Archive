---
title: "Desktop doesn't  exist."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by mitsos_ on 2008-05-11
blackout occurred since upgrading to 8.04. Desktop doesn't  exist now.

---

### Post by SunnyRabbiera on 2008-05-11
ounch, do you have a dual boot by any chance?
any live CD's laying about?

---

### Post by mitsos_ on 2008-05-11
Yes I do have a live cd of ubuntu 6.04.

---

### Post by nynoah on 2008-05-11
most likely you messed up your drivers.  check this thread it will help you out.
[http://ubuntuforums.org/showthread.php?t=745133](http://ubuntuforums.org/showthread.php?t=745133)

---

### Post by nynoah on 2008-05-11
actually just do this when you are logging in.  Get into your grub menu and type this into it.

sudo dpkg-reconfigure xserver-xorg

then set your driver to vesa.  Go through all the promts and just agree with them all and reboot.  This should get you back to a generic driver.  When that is done and you are back on your desktop, then you can activate your proprietary graphics drivers again.

---

### Post by jamieh on 2008-05-11
> **mitsos_ said:**
> Yes I do have a live cd of ubuntu 6.04.

There's a 6.04?

---

### Post by nynoah on 2008-05-11
6.04 is very old.

---

### Post by 0ni on 2008-05-11
You can use a server cd to fix installations can't you?

---

### Post by jamyskis on 2008-05-11
Could it be that the initlevel is set incorrectly?

Try typing one of the following from the command line when you've logged in.

startx 

or 

/etc/init.d/gdm start

What does it say?

---

### Post by jamieh on 2008-05-11
> **nynoah said:**
> 6.04 is very old.

Isn't it 6.06?

---

### Post by mitsos_ on 2008-05-13
Finally I downloaded 8.04 and I  put it over my last Ubuntu version without loosing anything. It is necessary not to format the root partition. Thanks anyway.:)

---

