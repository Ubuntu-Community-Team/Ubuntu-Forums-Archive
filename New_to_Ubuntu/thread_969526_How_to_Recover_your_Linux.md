---
title: "How to Recover your Linux"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Armaniboy on 2008-11-03
I typed a command line into the computer that was like fdsk something because it was on a posting to make my computer faster. 

If you search Armaniboy in the forums you should find the posting. My computer won't start right now and is asking me for a command like. It's saying:

"sdev1: failed" 

My question is how do I recover my linux? It still starts and says Ubuntu, but it checks the disk because it says an unclean shutdown happened.

Armaniboy :KS

---

### Post by Kinetic_lord on 2008-11-03
Oh man... fdsk=format disk... I'm sorry, who put this post? You should report him!

---

### Post by philinux on 2008-11-03
He was only told to run sudo fdisk -l

However the other command e2fsck should only be run when the filesystem is not mounted.

You were asked to run these commands from the livecd. If you ran that last command from a terminal on your mounted file system, then that could have done the damage.

---

### Post by oldos2er on 2008-11-03
> **Kinetic_lord said:**
> Oh man... fdsk=format disk... I'm sorry, who put this post? You should report him!

 fdisk != format disk. fdisk=partition table manipulator for Linux.

---

### Post by Armaniboy on 2008-11-03
That was it, but how do I recover my system? I'm trying to reinstall ubuntu, but it won't even do that :(

---

### Post by philinux on 2008-11-03
Can you reboot and at the first sign of grub press the esc key. This gives you the grub menu. Choose the recovery mode by using the up/down arrows then hit enter.

The command ```
sudo fdisk -l
```

Did not format your disk. Bur e2fsck will have messed with it if you were not using the livecd.

---

### Post by Armaniboy on 2008-11-03
I'm at that screen in the grub. After I type in the coding it says:

fdisk: invalid option -- '1'

---

### Post by inportb on 2008-11-03
That's a lowercase L, not a one.

---

### Post by Armaniboy on 2008-11-03
OK sda1 is my device boot. What do I do now?

Armaniboy:KS

---

### Post by Armaniboy on 2008-11-03
Does anyone know the next step?:KS

---

