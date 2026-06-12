---
title: "android phone not recognized"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by Phateless on 2011-09-29
The phone charges but I can't find any indication that the computer realizes there's a phone connected. Works fine in windows XP.

---

### Post by carranty on 2011-09-29
Have you set the phone to USB storage mode? On my phone its in the notifications dropdown menu.

---

### Post by carranty on 2011-09-29
If you open up a terminal and type *mount*, then press return it will list all the currently mounted file systems, if you copy and paste the output of that I can tell if its mounted or not.

---

### Post by The Cog on 2011-09-30
What make of phone?

I have a galaxy s2 and to be able to get usb storage to work, you have to:
1: in Settings / Applications / Development, enable USB debugging (you can leave this on forever)
2: Connect USB cable to the computer
3: in Settings / Wireless and Network / USB Utilities, tap Connect Storage to PC.
4: Open the USB drive in nautilus

---

