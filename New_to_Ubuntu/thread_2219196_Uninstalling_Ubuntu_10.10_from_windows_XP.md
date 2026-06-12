---
title: "Uninstalling Ubuntu 10.10 from windows XP"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Greg_Sargent on 2014-04-23
I put Ubuntu 10.10 on my computer with windows XP after my boss said I could have the computer but now she wants it back and I need to get it out. How do I go about doing so. It is not in the Add and Remove program section of my computer. Any help would be appreciated.

Thanks...Greg

---

### Post by Elfy on 2014-04-23
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

If it's wubi.

If it isn't - you'll need to remove the partitions and reinstall the windows bootloader if it is using  grub.

Check to see what partitions you have 

```
sudo fdisk -l
```

If you've no linux partitions I would assume it to be wubi.

---

### Post by Greg_Sargent on 2014-04-23
How do I type in the sudo fdisk - 1

---

### Post by deadflowr on 2014-04-23
From the Ubuntu side, you need to open up a program called "terminal" and then enter the command.
It will prompt you for a password, you should have one, if when  you log in to Ubuntu you enter a password, try that one.
(The password field will appear to be blank, it is actually typing the password invisibly.)

---

### Post by Elfy on 2014-04-23
and it is a lower case L not a 1 :)

---

