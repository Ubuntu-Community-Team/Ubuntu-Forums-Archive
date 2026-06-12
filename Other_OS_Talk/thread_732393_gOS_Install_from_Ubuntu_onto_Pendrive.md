---
title: "gOS Install from Ubuntu onto Pendrive"
date: 2008-03-22
forum: Other OS Talk
---

### Post by wormser on 2008-03-22
I want to install gOS to a pendrive from Ubuntu.  All the directions I find online are from installing from Windows.  Is it possible to install gOS from an .iso in Ubuntu?

---

### Post by smoker on 2008-03-22
as gos is based on ubuntu, you could maybe try this:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

never tried it myself, but best of luck, and let us know if you succeed!

---

### Post by wormser on 2008-03-22
> **smoker said:**
> as gos is based on ubuntu, you could maybe try this:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

never tried it myself, but best of luck, and let us know if you succeed!

I saw that one on my searches.  It won't work for me because I want to install with out using a CD.  I am looking for a way to install from my desktop.  BTW, thanks for the link.

Update:

I got to a XP box and got it installed.  I am still interested in a solution.

---

### Post by ralyon on 2008-03-26
> **wormser said:**
> I saw that one on my searches.  It won't work for me because I want to install with out using a CD. 

I'm assuming you mean you don't want to waste a disk and if so you can mount the iso file from within your desktop to a folder like this:

```
sudo mkdir /media/isoloop
sudo mount -o loop /"path to iso file" /media/isoloop
```

ralyon

---

