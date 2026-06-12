---
title: "wiping the hard drive"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by CristianXfree on 2012-12-08
I have no clue how to wipe a hard drive on ubuntu. it would be sweet if some one would help me out.

---

### Post by Paqman on 2012-12-08
What exactly are you wanting to do? Wipe an entire hard drive so that no data is recoverable, even by a technically competent person? Or just reformat it so that it appears like a fresh one? Or do you want to wipe some specific data on a drive without wiping everything?

---

### Post by Wim Sturkenboom on 2012-12-08
From a liveCD, run

```

dd if=/dev/zero of=/dev/sda bs=1k

```

[COLOR="Red"]Note that this wipes the complete harddisk (every single partition).[/COLOR] 
Replace sda by the disk that you want to wipe.

More examples e.g. [http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

The internet is your friend;) My search was for *linux wipe harddisk*

---

### Post by Sef on 2012-12-08
Also there is [dban]("http://www.dban.org/"), that is easy to use that wipes hard drives.

---

### Post by Bartender on 2012-12-08
Also [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php")

You make a bootable CD from the .iso, just like an Ubuntu install LiveCD.  Neat thing about having a GPLCD is once you've wiped the drive you can set it up for Windows, Linux, or both by creating the partitions you want.

That's if you just want to do something new with the disk, not wipe the drive down to zero's so the existing data is irretrievable.

---

