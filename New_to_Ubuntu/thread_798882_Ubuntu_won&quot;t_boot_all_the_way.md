---
title: "Ubuntu won&quot;t boot all the way"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by evilmonkeybrewing on 2008-05-18
Need some help.  I have a completely formated Panasonic CF-M34 Toughbook w/ a Pentium III Mobile @ 700MHz and 256 megs of RAM.  I start booting Ubuntu (latest version, just downloaded yesterday), enter my language as English, but when I try to select Install Ubuntu or Try Ubuntu, it begins loading but stops and gives me the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-55ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Can someone help?  it won't load any further.

---

### Post by spiderbatdad on 2008-05-18
This machine is a little light on ram for Ubuntu, but is suited to Xubuntu. I believe 384 is recommended minimum ram for Ubuntu. You can try booting with parameter noapic nolapic by pressing F6 at the install options screen or grub menu screen and delete the end of the kernel line that appears. Delete --quiet splash, and replace with: noapic nolapic

---

### Post by evilmonkeybrewing on 2008-05-18
I'll give Xubuntu a try and let you know>

---

### Post by spiderbatdad on 2008-05-18
A number of things can cause busy box...root file system not able to mount due failed kernel compilation, or cdrom not detected. If you get busy box again, try booting with acpi=off

---

### Post by evilmonkeybrewing on 2008-05-18
Downloaded Xubuntu and got the same busy box>  I've tried every different variation of booting on the initial screen but still can't get anywhere>

---

### Post by spiderbatdad on 2008-05-18
Can you get a command prompt and run:
```
update-initramfs -k `uname -r` -c
```

Also google 'ubuntu busy box'

---

