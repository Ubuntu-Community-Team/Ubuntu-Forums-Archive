---
title: "Trouble booting"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by zauriel56 on 2012-06-11
The only way I can boot Ubuntu is to have the Live CD in and use the workaround. And when it loads it always asks about installing even though its already installed. I'm also booting from an external hard drive.

---

### Post by timcowchip on 2012-06-11
Some machines need the boot flag set on the hard drive. Run the disk utility in Preferences and set the boot flag on the drive that you're trying to boot from.

---

### Post by zauriel56 on 2012-06-11
Ubuntu is showing me i don't know as much about computers as I thought.  I have disk utility opened but how do I set the boot flag on my external hard drive?

---

### Post by zauriel56 on 2012-06-11
I think I figured it out. I edited the left partition which had bootable checked to not checked then clicked on the other partition which had linux installed on it and clicked bootable on it. Is this right and is there anything else I need to do?

---

### Post by drs305 on 2012-06-11
If you are still having trouble booting I'd recommend installing and running Boot Repair. You can run it from the LiveCD or a running OS.

There is a link in my signature line. (Also, it has the ability to set the boot flag for you under the Advanced options, and if further troubleshooting is required, run the boot info script.)

---

### Post by zauriel56 on 2012-06-11
I got the following error.

Please enable a repository containing the [grub2] packages in the software sources of Windows 7 (sda1). Then try again.

What does this mean and how do i do it?

---

### Post by YannBuntu on 2012-06-11
Hello
that's a bug in the Boot-Repair utility (or in one of the components it's using, eg os-prober), sorry, i'll try to fix it.
Please run Boot-Repair, click "Advanced options", then click the "Backup partition tables..." button, save the ZIP file somewhere, then send me this file by email (yannubuntu ATT gmail DOTT com) or attach it to your reply in this discussion.

---

### Post by YannBuntu on 2012-06-11
ok, the bug was my fault. I fixed it in the PPA (package boot-sav >= 3.19-0ppa14). Please update Boot-Repair, try the "Recommended repair" again and indicate the new URL that will appear.

---

