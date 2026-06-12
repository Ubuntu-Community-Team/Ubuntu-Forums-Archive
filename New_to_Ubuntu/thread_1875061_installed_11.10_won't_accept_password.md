---
title: "installed 11.10 won't accept password"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by usorted on 2011-11-04
I was upgrading from 11.04 to 11.10 and the machine was accidentally turned off during the process. 

Reinstalled but password and search boxes were autofilling.

So I've just deleted all previous Ubuntu stuff from disc with gparted and installed 11.10. It wont allow anything to be typed into search boxes e.g. google. 

It also won't allow the password to be typed into the authenticate box for the update that it wants to do, also while waiting for the password to be input there is a fast pulsing sound. 

What can I do?

---

### Post by Garland Fox on 2011-11-04
I am probably not smart enuff to help but are you using a live cd to upgrade, and is this a dual boot setup with windows or stand alone linux?

---

### Post by usorted on 2011-11-04
I've used a live cd to install alongside existing (xp). 

I can now make the problem clearer: the keyboard isn't working.

---

### Post by usorted on 2011-11-04
_Update:_  I've also tried another live cd (10.04 LTS this time) and get the same unresponsive keyboard so I haven't installed that one. It responded to the first keystroke - then nothing!

When I boot the other system (Microsoft windows XP) the keyboard works fine.

Also when I boot Ubuntu 11.10 the keyboard works for the initial password input but once into the system it's the same - after the first keystroke of input the keyboard becomes completely unresponsive!

Any help much appreciated.

---

### Post by usorted on 2011-11-07
Thanks for your reply DRS305.

Answers to your questions:

Yes the keyboard does work at the Grub menu but not once booted.

Yes the keyboard works from my 11.10 cd (I'm typing from there now) but curiously did not work from the 10.04 LTS cd after the first character.

---

### Post by usorted on 2011-11-09
UPDATE: yesterday I booted 11.10 from the hard disk in safe mode and ran repairs then started it and it worked OK all day (except for the cursor action seemed a bit off) then closed down for an hour and re-booted only to find it was back to square one - after signing in the keyboard had no effect after the first keystroke.

Any ideas please?

---

### Post by usorted on 2011-12-16
I eventually solved this by getting a usb keyboard instead of the SP/2. It seems that the distros after Karmic will not work with the SP/2 keyboard on my Packard Bell imedia desktop. 

Having a keyboard that doesn't stop working at the user and password stage if the install has enabled me at last to install 11.10 again. 

It still suffers from the sluggish mouse movements after various times from boot. 
UPDATE: Sluggish mouse problem solved by plugging it directly into the computer instead of via a hub. However this was not convenient due to the short wire length so I've replaced it with a wireless mouse which worked perfectly out of the box (on both O/S). Make and model, if it's of any interest, is a Trust 16856.

---

