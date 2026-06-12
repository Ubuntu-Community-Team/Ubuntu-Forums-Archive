---
title: "Grub not loading??"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by jethier on 2008-08-13
Yesterday my computer was acting really funny. I couldn't view YouTube or other websites that I have viewed in the past.

I rebooted the computer and while loading I received this message

GRUB Loading Stage 1.5
GRUB Loading, please wait...
Error 16

Stayed like this for a few hours till I shut it down and went to bed.

I'm at work today, when I called my wife a little bit ago she had restarted the computer (not knowing anything was wrong with it) and now it's working fine?

Anybody have an explanation, could the hardrive be going bad?

---

### Post by matthewbrave on 2008-08-13
mine has done that sometimes and i just shutdown from mains, leave it for a bit and turn back on.

sometimes use live cd to select 'boot from first hard drive'

---

### Post by rbc on 2008-08-13
This may be useful, or maybe not. Seems there can be many causes of Error 16
[http://ubuntuforums.org/showthread.php?t=762870](http://ubuntuforums.org/showthread.php?t=762870)

---

### Post by jethier on 2008-08-13
> **matthewbrave said:**
> mine has done that sometimes and i just shutdown from mains, leave it for a bit and turn back on.

sometimes use live cd to select 'boot from first hard drive'

Oh Man, I was hoping to get away from mysterious errors when I moved to UBUNTU. Do you run 64 or 32 bit?

---

### Post by matthewbrave on 2008-08-13
not sure i have amd duron

---

### Post by bobnutfield on 2008-08-13
Grub error 16 "can" occur when the system is not shut down cleanly (i.e. hitting the power button when the system freezes).  It will temporarily corrupt your superblock, but usually upon subsequent reboot fsck will correct the errors.  However, numerous hard resets like this can cause bad sectors on your disk.  I doubt that has occured, but that is a possibility.

---

