---
title: "Managing Partitions Safely"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by prajagop on 2013-08-08
How can I safely partition my disk retaining Windows7 and Ubuntu? I am not sure which one belongs to which. I also had Suse Linux partitions that I don't need anymore. Windows and Ubuntu exists in disk. Suse Linux shows up in Grub with /dev/sda6/ /dev/sd10 and /dev/sd11 and also when I see the disk contents (I don't need it anymore).

I have Ubuntu cd but not Windows, so I wanted to be careful. I can re install Ubuntu as I only installed 12.04 ISO via USB yesterday. I would like to retain Windows 7 partitions but combine all Linux partitions for Ubuntu (assuming that is the right direction I should think).

Attached is my GParted. Please note I am a fairly new user when it comes to disk / memory management.

---

### Post by prajagop on 2013-08-08
I had copied my image to editor window, but it look scrambled. Apologies to everyone. I am re attaching here.

---

### Post by Gone fishing on 2013-08-08
In Windows you could open up the disk management tool delete all the Suse partitions (marked as of unknown type) and then simply install Ubuntu into the free space created.

---

### Post by oldfred on 2013-08-08
I would use gparted. Windows does not see Linux partitions, so it may not work correctly on those partitions.
Generally Linux tools for Linux and Windows tools for Windows, but of course there are exceptions.

The only issue you now have is sda12, your new / (root) partition is between your NTFS partitions which I expect you want to change. You  also have mounted swap with existing boot. But you can delete & recreate swap, but have to edit fstab with new UUID for new swap partition.

About 20GB for / is not far from what I normally suggest, but then I suggest either a separate /home or (what I use) separate data partition(s). I have both a Linux formatted data partition and still have a NTFS data partition from when I still used XP. Eventually I will finally move all data from NTFS and only have Linux on my system.

---

