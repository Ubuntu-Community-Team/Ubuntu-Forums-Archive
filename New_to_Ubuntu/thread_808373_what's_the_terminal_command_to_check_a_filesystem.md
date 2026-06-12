---
title: "what's the terminal command to check a filesystem"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Raccoon1400 on 2008-05-26
I want to check hda1 for errors. What command do I use.

---

### Post by drs305 on 2008-05-26
> **Raccoon1400 said:**
> I want to check hda1 for errors. What command do I use.

fsck is the utility that will do this. However it must not be run on a mounted partition. The easiest option is to:
```

sudo touch /forcefsck

```

This will create a 'forcefsck' file to be placed in the root directory and cause an fsck check on that partition during the next boot.

---

### Post by Raccoon1400 on 2008-05-26
What would I use to check the filesystem right now, from a different OS that doesn't mount that partition.

---

### Post by newbreed on 2008-05-26
take a look here.. [http://www.er.uqam.ca/nobel/r10735/unixcomm.html]("http://www.er.uqam.ca/nobel/r10735/unixcomm.html")

---

### Post by vanadium on 2008-05-26
The command in fact is fsck, but for any permanent drive, the tip of drs305 to "force" a check on the next boot is your safest bet.

---

### Post by Paqman on 2008-05-26
> **Raccoon1400 said:**
> What would I use to check the filesystem right now, from a different OS that doesn't mount that partition.

The LiveCD is handy for this. Boot up into it and run fsck.

drs305's suggestion is probably quicker, though.

---

### Post by Raccoon1400 on 2008-05-26
The check using the first method failed. It told me to run fsck manually in recovery mode with the fs mounted read-only. How do I get recovery mode to mount hda1 as read-only?
This is why it failed. [http://ubuntuforums.org/showthread.php?t=807473](http://ubuntuforums.org/showthread.php?t=807473)

---

### Post by philinux on 2008-05-26
Press esc when stage 1 grub loads. select the recovery mode.

Then

fsck -v /dev/xdax

some people have sda1 others have hda1 etc

---

### Post by Raccoon1400 on 2008-05-26
I did the check and I think I may have fixed it. At least part of it.

---

### Post by Raccoon1400 on 2008-05-26
I need to do the same check on hardy, on the same machine, but recovery mode did not mount it as read-only.

---

### Post by vanadium on 2008-05-28
Do not make things complicated.

* If you want to check a partition other than one that is used for the system (e.g. /, /home, /boot...) then just unmount the drive and check. Example, assuming /dev/sdc1 is the partition you want to check:
```

sudo umount /dev/sdc1
sudo fsck /dev/sdc1

```

* If you want to check a partition that cannot be unmounted, then follow drs305's advice. e.g (in an already exotic system) I have /home on /dev/sdc1

```

sudo touch /home/forcefsck

```

and restart the system. In practice, this will be rarely necessary: such drives are usually mounted in fstab with the instruction to be checked. They will undergo a quick check every time the machine is booted and a thorough check every 30 mounts or 30 days, whichever comes first (and dependent on the filesystem parameters set).

However IT IS IMPORTANT THAT YOU TAKE A HABIT OF CHECKING A REMOVABLE DRIVE from time to time. Indeed, these drives are never checked automatically, only when you instruct so! It is an important task, thus, keep it simple!

---

