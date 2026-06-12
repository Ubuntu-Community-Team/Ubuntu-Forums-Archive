---
title: "faulty rules file ruins system"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by yantrak on 2012-03-22
hi all,
i,m quite new to using ubuntu & linux.for making my usb-serial port accessible via a fixed name i tried to put a rules file in /etc/udev/rules.d directory.the rule was not written in correct syntax.
after this file addition the system fails to boot in either the normal or recovery modes.i tried to delete this file in windows xp using ext2fsd,but it comes  up with a message 'media write protected' even though i've given the option of write enable in mount point options.
so it seems that my ubuntu installation is lost for me.

request anyone to please help.

thnx
ashwani

---

### Post by Grenage on 2012-03-22
Are you able to remove the file by booting from the Ubuntu (or other live) CD?  I can only assume that you have write issues due to the XP driver.

---

### Post by yantrak on 2012-03-22
thnx friend,
as mentioned above i can't boot ubuntu after the addition of this file.that is the reason i tried to delete this file using ext2fsd in win xp.

ashwani

---

### Post by coffeecat on 2012-03-22
@yantrak, Grenage suggested that you boot Ubuntu from the live CD or USB - the medium you used to install Ubuntu in the first place - not your Ubuntu on your hard drive. If you boot into a live session, you will be able to mount the partition that your system is on and delete the faulty file. Do you need help with this?

---

### Post by yantrak on 2012-03-22
thnx cofeecat,
i tried using live pendrive.even there it is write protected,would be thnkful for your guidance.
ashwani

---

### Post by ajgreeny on 2012-03-22
To get write permission, which will allow you to delete that rules file, you need the partition mounted and then to open it using command ```
gksudo nautilus
``` from the live CD, which gives you root permissions.

---

### Post by yantrak on 2012-03-22
thnx ajgreeny,

i did gksudo nautilius.the partition is available in file manager as 54gb partition.i don't know how to mount.pls help.

thnx

---

### Post by coldraven on 2012-03-22
> **ajgreeny said:**
> To get write permission, which will allow you to delete that rules file, you need the partition mounted and then to open it using command ```
gksudo nautilus
``` from the live CD, which gives you root permissions.

What is the password for a Live CD? ubuntu?

---

### Post by lisati on 2012-03-22
> **coldraven said:**
> What is the password for a Live CD? ubuntu?

AFAIK there shouldn't be one.

---

### Post by yantrak on 2012-03-22
thnx all,

the problem got solved after mounting the partition and changing permissions,followed by deletion.

thnx again.

ashwani

---

