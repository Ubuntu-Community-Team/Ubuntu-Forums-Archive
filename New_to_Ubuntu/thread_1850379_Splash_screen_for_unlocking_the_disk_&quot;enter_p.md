---
title: "Splash screen for unlocking the disk &quot;enter passphrase&quot;"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-09-26
I have a lubuntu installed on a encrypted file system and when I start the computer tell it get to the 

unlocking the disk /dev/disk/by-uuid/efb917c2-50e4-4a44-BB66-038C41249D8D (sda5_crypt)
Enter passphrase:

all on a black text screen.

I used How to install Ubuntu 11.04 on an encrypted LVM file system guid at  [http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/](http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/)

If i hit the esc key i get a screen like the attached pic. I want to use a screen like the attached pic with out having to hit the esc key how do i do that?

---

### Post by Lisiano on 2011-09-26
You want to remove the splash screen am I right?
When you boot and see GRUB, select Ubuntu and press E, now find and delete ```
splash quiet
```then press Ctrl+X, if this is the effect you want, then let's make it permanent.
Type this```
sudo nano /etc/default/grub
```
Find this line```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
```
And turn it into ```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
If it has anything else on the line, leave it as is and just remove "splash quiet". If you see this line```
GRUB_CMDLINE_LINUX="splash quiet"
```
Do the same. Now press Ctrl+O, Enter and Ctrl+X. Now finally type this```
sudo update-grub2
```
Now every time you boot you won't see the splash screen.

---

### Post by lance bermudez on 2011-09-26
no I want the splash screen by flowing you directions i changed the lines

GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

to 

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX="splash quiet"

thank you for your help.

---

### Post by Lisiano on 2011-09-26
Ah, guess I misread. Well good thing that it worked how you wanted.
Also, please mark the thread as solved using the Thread Tools on the top of the page.

---

