---
title: "security 12.04"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by fattyz on 2012-06-13
Hi can I password protect 12.04 and prevent rebooting or unplugging from getting around it?  My HP computer does not have an option for a BIOS level password.

Thanks

---

### Post by Frogs Hair on 2012-06-13
There is nothing that can be done about a power outage unless you are hardwired to surge protector and have backup power in the form of a battery and generator. You may be able to prevent non administrative users from shutting down and secure the boot loader. The links are dated , so search for newer information. 

Password Protect Boot loader:[http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/](http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/)

Prevent Shutdown:[http://embraceubuntu.com/2006/03/20/disable-shutdown-for-normal-users/](http://embraceubuntu.com/2006/03/20/disable-shutdown-for-normal-users/)

---

### Post by Gone fishing on 2012-06-13
Have a look at this [http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)
to password protect grub 2, this will prevent users starting up the machine without a password.


I'm guessing that changing the permissions of /sbin/shutdown will prevent users shutting down.

---

### Post by Cheesemill on 2012-06-13
Anyone with physical access to the machine can get root access.

The only way around this is to encrypt your hard drive with a strong password.
They will still be able to use the hardware but they won't be able to access any of your data.

---

### Post by isa.dsouza on 2012-11-27
> **Cheesemill said:**
> Anyone with physical access to the machine can get root access.

The only way around this is to encrypt your hard drive with a strong password.
They will still be able to use the hardware but they won't be able to access any of your data.

 Does this mean that a partition that is ext4 with ownership taken by admin. can be accessed by a live usb with root privileges?

---

### Post by Cheesemill on 2012-11-27
Yes.

Without encryption anyone who has physical access to a machine can easily access everything on it.

---

