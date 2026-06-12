---
title: "PC Won't boot Ubuntu, Stuck on GNU Grub Command Line"
date: 2016-04-16
forum: New to Ubuntu
---

### Post by callum7 on 2016-04-16
I am new to ubuntu and recently installed Ubuntu on my old laptop, had no OS on it, was working fine and after a reboot It didn't load Ubuntu it came up with a CLI saying "GNU Grub version 2.02-beta2-9ubuntu1.7" I had no idea what this was or how to re run Ubuntu, i searched for a while to see what i could do but found nothing. I have since wiped my hard drive and it still comes up with it. It doesn't allow me to boot from a USB either. Could anyone help?

---

### Post by grahammechanical on 2016-04-16
When we install Ubuntu we also install a boot loader (Grub). Part of Grub goes into the MBR of the hard disc but Grub configuration files go onto the partition that Ubuntu is installed on. The file grub.cfg defines the boot menu. And that is located at /boot/grub/.

If Grub (in the MBR) cannot find that file it brings us to a Grub command line so that we can run a few Grub commands to try to direct Grub where to look. There is now no point in attempting that as you have wiped the hard drive.  I doubt that wiping the hard drive would remove Grub from the MBR.

That explains (I hope) the situation. The solution since you wiped the hard drive is to re-install. But you say you cannot boot from a USB memory stick. That is a matter for making changes to the settings in the BIOS boot system settings utility. You might need to go to the section for Boot options and look under hard drives as the BIOS might be seeing the USB memory stick as an external USB drive.

That is what I have to do. I have to change the BIOS setting so that the motherboard boots from the external USB drive & not the internal hard disk.

Regards.

---

### Post by callum7 on 2016-04-17
Thanks for the reply, I knew about changing the boot order and did so prior to trying to boot from my USB and it would still load Grub.

---

### Post by RobGoss on 2016-04-17
I think **Grahammechanical, **pretty much covered it as far as changing your boot order and if you since wiped your drive I can't see why you would get that message,

How did you wipe your drive?

If you wanted to wipe your drive you are given that option when installing Ubuntu all you need to to is choose it and Ubuntu's installation will do the rest

---

