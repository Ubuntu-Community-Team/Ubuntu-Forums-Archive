---
title: "Boot menu help"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Visvalor on 2011-10-12
Hi.

I recently had my XP disk die and had to reinstall XP on a new disk. Problem is my boot menu is looking for XP now on dev/sda1 and my new disk is labeled as dev/sda 

How do I edit to remove the 1? Startup manager has no real options to do much of anything but aesthetics and which operating system to default on.

I don't seem to have a menu.1st file or whatever it was I was looking for in the grub/boot folder.

Any help is appreciated.

Ubuntu 11.04 to my knowledge. Thanks.

---

### Post by Visvalor on 2011-10-12
Further reading lead me to grub.cfg

If I open it in a text editor and change;

```

}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 68D1D36528063575
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

/dev/sda1 to /dev/sda

Will that work or kill my machine?

---

### Post by Mark Phelps on 2011-10-12
Do NOT edit Grub.cfg.  Perhaps you noticed the wording in there telling you NOT to edit it?

Instead, open a terminal and enter "sudo update-grub".  That will regenerate the GRUB info current contained in grub.cfg and should insert an updated entry for Windows XP.

---

### Post by Visvalor on 2011-10-12
If I did all the things I was told not to do, where would I be :p?

But thanks a billion :D!

---

### Post by Mark Phelps on 2011-10-12
> **Visvalor said:**
> If I did all the things I was told not to do, where would I be :p?

HAPPY? DEAD? Don't know all the things you have been told NOT to do!

But, editing grub.cfg is a BAD idea because routine updates overwrite it, and you're carefully crafted changes are suddenly GONE.

---

