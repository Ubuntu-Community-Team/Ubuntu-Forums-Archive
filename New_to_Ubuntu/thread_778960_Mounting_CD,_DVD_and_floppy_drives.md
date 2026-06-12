---
title: "Mounting CD, DVD and floppy drives"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by akparker on 2008-05-02
my newly configured xubuntu hp desktop (details in signature line) does not recognize the dvd drive, the cd-rw drive or the floppy drive.

they are unmounted

can someone give me a play-by-play on how to mount these and get them working?

i'm still pretty new to linux and very new to xfce, so i'd appreacite as many details as you can provide ... it will help me learn

thanks,
akp

---

### Post by Bruce M. on 2008-05-08
> **akparker said:**
> my newly configured xubuntu hp desktop (details in signature line) does not recognize the dvd drive, the cd-rw drive or the floppy drive.

they are unmounted

can someone give me a play-by-play on how to mount these and get them working?

i'm still pretty new to linux and very new to xfce, so i'd appreacite as many details as you can provide ... it will help me learn

thanks,
akp

Hi akp

What happens when you put in a Floppy disk and use Thunar to view the contents?

Same with a DVD, does Thunar open when you insert one?

In "Places" my Floppy Disk is greyed out if there is no disk inserted, and neither my CD or DVD shows until I insert some media into them, at which time they are mounted and Thunar opens, or Totem if its a film.

What does your fstab file say.  Mine looks like this:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Have a nice day.
Bruce

---

### Post by maybeway36 on 2008-05-08
GUI mounting can be iffy at times, but these terminal commands should always work:
mount /dev/fd0 - Mount a floppy disk
umount /dev/fd0 - Unmount a floppy disk
mount /dev/cdrom - Mount a CD or DVD
umount /dev/cdrom - Unmount a CD or DVD

---

