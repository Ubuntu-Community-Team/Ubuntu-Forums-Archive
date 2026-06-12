---
title: "How tightly is an install bound to its original hardware?"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by mikebravo on 2012-08-04
Let me illustrate my question with an example: You have two computers whose major similarity is that both have one SATA hard drive on which Ubuntu is running well without modification. The computers are different in every other respect, different processors, different mother boards with different chip sets, etc. Can you then swap the hard drives between the computers and find that the computer is operating as well as before the swap?

---

### Post by djheadley on 2012-08-04
A couple of versions back I had to replace a motherboard and except for a longer boot time the first time, everything ran just fine.  I guess it depends on what else is different (maybe video card).

---

### Post by wildmanne39 on 2012-08-04
Hi, it will run fine except you if you have adriver for your video card installed that is not the generic one you will need to uninstall it to get it to boot properly and your wireless probably will not work without some tweaking.
Thanks

---

### Post by Cheesemill on 2012-08-05
Unless you are switching video chipsets from Nvidia to ATI or vice versa **and** you have installed the restricted drivers then it isn't tied at all.

The Linux kernel auto detects hardware and loads the correct drivers every time you boot the machine anyway.

If you are switching video cards then just uninstall the restricted drivers before you make the switch.

Obviously you can't switch a 64-bit install to a 32-bit machine either.

---

### Post by daniell59 on 2012-08-05
I took out my hard drive from the laptop and installed it in the desktop. I then installed Ubuntu in that hard drive. Put the hard drive back into the laptop. It now works flawlessly.

---

