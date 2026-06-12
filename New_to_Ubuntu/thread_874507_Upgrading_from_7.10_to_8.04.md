---
title: "Upgrading from 7.10 to 8.04"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by IlMadCowlI on 2008-07-30
In the middle of the upgrade from Gutsy to Hardy it froze with 5 min left of install.  I gave it over an hour to try to do something but it was done.  I have tried to load into tty and do a "sudo apt-get update" but it tells me that a previous install was pending.  It says to try "sudo dpkg --config -a".  I try that and i freeze at the same spot. I was wondering if anyone has experienced this or has another way to upgrade using tty???

---

### Post by iaculallad on 2008-07-30
Try to boot on the recovery mode and try inputting the following commands:

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

In that order.

---

### Post by IlMadCowlI on 2008-07-30
Hey thanks I will try that, but what recovery mode should I load??

---

### Post by iaculallad on 2008-07-30
> **IlMadCowlI said:**
> Hey thanks I will try that, but what recovery mode should I load??

Recovery mode at during boot-up. By pressing the ESC key to break the boot option.

---

### Post by IlMadCowlI on 2008-07-30
When I try to boot into recovery it asks me multiple options: Recovery Menu- "resume" "dpkg" "root" "xfix"...  One thing i did notice when boot in grub it still says 7.10  but when i load into a tty it says 8.04.

---

### Post by iaculallad on 2008-07-30
> **IlMadCowlI said:**
> When I try to boot into recovery it asks me multiple options: Recovery Menu- "resume" "dpkg" "root" "xfix"...  One thing i did notice when boot in grub it still says 7.10  but when i load into a tty it says 8.04.

Try the **xfix** instead.

---

### Post by IlMadCowlI on 2008-07-30
when i try to load the "xfix" it tells me xserver-xorg is broken..  So i am trying to use dpkg and it seems like it is locking up at pretty much the same spot it locked up at during install.  Generating locales...
            en_AU.UTF-8...

---

### Post by IlMadCowlI on 2008-08-01
-Update- I got it to update...  In tty1 I  did  a "sudo dpkg --force-all" then i did a sudo apt-get -update...  Now my laptop is on Hardy and fully upgraded...

---

