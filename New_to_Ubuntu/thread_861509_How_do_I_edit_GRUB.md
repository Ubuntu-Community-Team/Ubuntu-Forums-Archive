---
title: "How do I edit GRUB?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by gabriella on 2008-07-16
I want to edit the GRUB file to chnage my boot preferences. like default = and timeout=.  I found some inst[I]ructions in a magazine that told me to enter in terminal

#nano /boot/grub/grub.conf

This doesn't do anything! I went into the grub folder and there's no such file as grub.conf. Possibly these are old instructions for my version?
So how should I change my grub preferences?

Hardy 8.04

---

### Post by Joshuwa on 2008-07-16
I believe the typical location for the configuration file is:

/boot/grub/menu.lst

---

### Post by aysiu on 2008-07-16
There's a graphical tool for editing the Grub menu. More details here:
[http://psychocats.net/ubuntu/startupmanager](http://psychocats.net/ubuntu/startupmanager)

If you prefer to manually edit it, the terminal command would be ```
sudo nano -B /boot/grub/menu.lst
``` *sudo* allows you to temporarily escalate privileges so as to edit system files (of which the menu.lst is one).

*nano* opens it in the text editor Nano.

*-B* makes an automatic back-up copy before you edit it.

Once you're done making changes, press Control-X, Y, and Enter to save.

---

### Post by Paddy Landau on 2008-07-16
> **Joshuwa said:**
> I believe the typical location for the configuration file is:
/boot/grub/menu.lst
Make a backup before editing!

---

