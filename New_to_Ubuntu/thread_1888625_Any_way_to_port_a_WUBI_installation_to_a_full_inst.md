---
title: "Any way to port a WUBI installation to a full installation?"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by pakopako on 2011-11-29
Pretty sure the answer is "no", but still wanted to ask if I could import my WUBI installation onto a full-fledged install.

The WUBI install mostly works fine, aside from a few hardware specific issues and I've run out of HDD space to upgrade to 11.10. (It's a really old, single-core laptop with 32 GB of space.) The WUBI sits by itself on a 7.5 partition of an 18GB extended partition. I presume the 5 GB install (for some reason I wasn't able to select 7) sets aside 2GB for a swap file or such.

Can Ubuntu be installed on an extended container for logical partitions?

---

### Post by Rex Bouwense on 2011-11-29
I believe that the answer to 1. is no and 2. is yes.  Ubuntu is very happy being installed on a logical partition.  An not sure what you mean by an extended container.  You should figure on at least 9-10 Gbs for installation and /home.

---

### Post by bcbc on 2011-11-29
Yes. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by pakopako on 2011-11-30
> **bcbc said:**
> Yes. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Ah. Thank you.  Although this may mean I have to "Tower of Hanoi" this somehow. The partition I want to migrate my WUBI install to just happens to be the mounted partition that it's resting on. I could move the 5GB WUBI file to a flashdrive, but would the bootloader and GRUB know I've moved it from its original installed partition to the flashdrive? (The Disk Utility labels the 7.5GB partition WUBI is currently on a 'Logical Partition' that's inside an extended partition containing two logical partitions.)

---

### Post by oldfred on 2011-11-30
I am not sure you could then boot wubi from Windows and bcbc's scripts may not work without modification.

But you can boot wubi from grub2 or mount it and copy info.

See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

I backup my system(full install) so I can do a clean install in another partition. I keep my old install so I can go back and the first time or two I did go back to find some setting. You could just backup /home, export list of installed programs and possibly some settings from /etc if you made any system wide changes. I think this is what bcbc script does but you end up doing it manually.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Some stuff to exclude from backups
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by bcbc on 2011-11-30
You can move the root.disk and migrate back with the --root-disk= option from a live CD.

You can migrate to an external and then back again (the script works on normal ubuntu installs as well).

Or you can backup your data, reinstall, reapply etc.


If you decide to migrate with the --root-disk option, you need the same architecture on the live CD (e.g. 32 or 64 bits) as the wubi install. Also, if you have more than one virtual disk copy them all to the same place before running.

---

