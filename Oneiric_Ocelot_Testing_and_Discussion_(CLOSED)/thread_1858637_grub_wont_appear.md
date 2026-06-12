---
title: "grub wont appear"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-10-12
Okay i think i got 11.10 to install on my laptop but im getting very stressed out because grub refuses to appear, tried installing twice.

I also tried the repair boot application from the ubuntu wiki page on repairing boot and it says grub was sorted and still it refuses to appear, anyone else get that?

---

### Post by kansasnoob on 2011-10-12
When you say it fails to appear do you mean only the menu fails to appear?

Does the machine boot?

Is Ubuntu the only OS or is this a dual/multi-boot?

---

### Post by ELD on 2011-10-12
It just auto boots into windows with no grub menu.

I just tried boot repair again and did the advanced option and got this at the end:
> 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda4
done
Setting up grub-gfxpayload-lists (0.5) ...

So it looks like it detected both Ubuntu 11.10 and Windows and i installed it to the only drive on the system so time to reboot again and see if this time it worked...

---

### Post by drs305 on 2011-10-12
If Grub fails to appear or boot Ubuntu, please download and run the Boot Info Script and post the contents of RESULTS.txt  This will show us what is going on with your boot files.

You can get to the Boot Info Script site by clicking the "BIS" link in my signature line.

---

### Post by Harry33 on 2011-10-13
Do you see the grub menu if you press and hold down the "shift" button?
Start pressing the button during early (mobo boot) and keep it pressed.

---

### Post by lolpenguin on 2011-10-13
I am also an avid Windows user (WINDOWS<LINUX), so I'll try to help.
You'll need to be logged in as an administrator for the following to work.
When you're logged in, key in [Win]+[R], type msconfig and hit enter. On the "Boot" tab, go to Timeout, and change the value to something like 10 (or something which gives you enough time to press down). Click "Apply", then "OK" and restart. You should be able to choose the "Ubuntu" entry in Windows Boot Manager. If this does not solve the problem, then it probably is a problem with GRUB.

---

