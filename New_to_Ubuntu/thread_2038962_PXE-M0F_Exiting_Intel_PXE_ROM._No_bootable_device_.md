---
title: "PXE-M0F: Exiting Intel PXE ROM. No bootable device -- insert boot disk and press any"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by WitchCraft on 2012-08-07
Hi, question:

I have this problem here:
[http://askubuntu.com/questions/173155/cant-boot-pxe-m0f-exiting-intel-pxe-rom](http://askubuntu.com/questions/173155/cant-boot-pxe-m0f-exiting-intel-pxe-rom)

Anybody has an idea what I could do ?

---

### Post by WitchCraft on 2012-08-11
HELP ! HELP !

I backed-up the data and reinstalled (erasing all partitions).

AND I STILL GET THE SAME FAULT !!!

Boot settings are OK.
I tried resetting the BIOS to factory defaults, too...

---

### Post by WitchCraft on 2012-08-12
Oh man I get it working.

For the record, if anyone has the same problem:

If you get this message (and your BIOS settings are OK):

1. Switch off your laptop for more than 30 seconds.

2. Start, and wait until you get to the error screen

3. press CTRL + ALT + DEL

4. Wait as it reboots, until you the the same error screen again

5. Press the power button and wait until it switches off.

6. Wait no longer than 5 seconds, and then press the power button

7. It boots to grub selection ! In grub, select "recovery" (because normal startup won't work)

8. Select regenerate grub.

9. select boot

---

