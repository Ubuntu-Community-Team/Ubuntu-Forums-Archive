---
title: "External SD card reader,need to reboot to work"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by paichkash on 2012-07-13
hi
i have external card reader by syomtech. when i first insert it works and i can see my sd card .. but if i unmount it and then remove the sd card from usb port and insert new card and re insert into usb port it doesnt works.. i have to restart for it to work
 
after searching forums i came accross one solution 
  but its not recgnizing this command

root@r-desktop:/etc/default# sudo sed -i s/splash/splash\ pciehp.pciehp_force=1/g /etc/default/grub
sed: can't read /etc/default/grub: No such file or directory


i am using Ubuntu 9.10 ..
please i cant upgrade to new as i am on dialup and i have a huge number of softwares installed . and it were installed when i went to other city where there was dsl... installed all softwares and took few days .. now upgrad is not possible in these situations..

thanks

---

### Post by Cheesehead on 2012-07-13
That command is going to change one line in your grub bootloader config.
Are you sure you want to do that? The cure might be worse than the current problem.

A link to the instructions you are following would be helpful.

---

### Post by Cheesemill on 2012-07-13
Those instructions will only work if you are using 10.04 or later as they are for GRUB2.

You should really try and upgrade as 9.10 has been end-of-life for over a year so no longer receives any support or security updates. There are likely to be security issues with using such an old release.

---

### Post by tea for one on 2012-07-13
> **paichkash said:**
> hi
i have external card reader by syomtech. when i first insert it works and i can see my sd card .. but if i unmount it and then remove the sd card from usb port and insert new card and re insert into usb port it doesnt works.. i have to restart for it to work

i am using Ubuntu 9.10 ..

Good afternoon

When you unmount your card reader, do you have a choice between:-

Eject
Safely remove drive

If you can choose "eject", I expect that you may not have to restart the PC.

Card readers sometimes behave like CD drives.

If you are able to upgrade to Ubuntu 12.04 in the future, the Nautilus file manager provides both options.

---

