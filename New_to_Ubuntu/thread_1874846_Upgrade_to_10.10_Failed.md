---
title: "Upgrade to 10.10 Failed"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by highstandard on 2011-11-03
I recently tried to upgrade from 10.4 to 10.10. Everything seemed to be going OK until the system hung and rebooted by itself. When it starts it shows the Ubuntu 10.4 text and boots into the desktop. The only things that appear are the cursor in the middle of the screen and the a blank grey taskbar at the bottom that flashes intermittently.  I cannot move the cursor. Does anyone know how I'd go about fixing this? Is there a system restore option somewhere like windows? Any help offered is greatly appreciated.

---

### Post by dileepm on 2011-11-04
There is an system repair option in the boot menu, press Esc if u have no dual boot on boot.

---

### Post by Script Warlock on 2011-11-04
> **highstandard said:**
> I recently tried to upgrade from 10.4 to 10.10. Everything seemed to be going OK until the system hung and rebooted by itself. When it starts it shows the Ubuntu 10.4 text and boots into the desktop. The only things that appear are the cursor in the middle of the screen and the a blank grey taskbar at the bottom that flashes intermittently.  I cannot move the cursor. Does anyone know how I'd go about fixing this? Is there a system restore option somewhere like windows? Any help offered is greatly appreciated.

you might try repairing at recovery mode and drop to shell and type this sudo dpkg --configure -a

---

