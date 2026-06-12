---
title: "Re-installing Ubuntu 11.10"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by Kayman on 2012-02-21
I installed from a CD Ubuntu 11.10 alongside Win XP (dual boot).
The installer automatically created 2 new partitions for Ubuntu.
All went well, I was able to download all updates for the system
and (NVIDIA) drivers. I also successfully changed the booting sequences.

I then was trying setting up dual monitors which proved to be a 
futile exercise.

Even after numerous reboots the monitors did not display anything
but instead produced 'black screens' or 'Ubuntu default color' 
without any icons to click on.

I mouse-clicked (left and right) all over the screens but no responses.

So I decided to uninstall Ubuntu. In Windows (Desk Management) I 
manually deleted the 2 partitions created by Ubuntu and used 
Windows XP's disk management tool to restore the bootloader using
the Windows XP install disk (fixboot and fixmbr).

My (C) drive in Windows has now 2 partitions viz 46.76 GB NTFS
for Win XP and 27.77 GB Free space.

Since I wish to steer away from Windows and migrate gradually to
Ubuntu (Linux), I naturally like to re-install Ubuntu 11.10 to
the existing free space of my (C) drive creating the partition 
set up as previously.

Questions:
What precautions and prerequisites need to be observed in order
to to re-install Ubuntu to the free space of my hard disk drive?
And can I be sure that only 2 partitions will be created on the
free space by Ubuntu?

(I had bad experiences with GP Parted and if it is possible would prefer doing without any partition editor software). 

Thanks in advanve for guidances.

---

### Post by Gone fishing on 2012-02-21
When you install you can control the partitioning process. I'd delete the extra partition in Windows to create free space on the drive and then install into that.

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

Personally I think you would be best with 2 partitions a swap and an extended partition then create / (root) and /home as logical partitions within the extended partition. The advantage of this is that it keeps your personal file separate form the system files and makes reinstallation upgrading potentially easier.

---

### Post by Kayman on 2012-02-21
Many thanks for response and link.

---

