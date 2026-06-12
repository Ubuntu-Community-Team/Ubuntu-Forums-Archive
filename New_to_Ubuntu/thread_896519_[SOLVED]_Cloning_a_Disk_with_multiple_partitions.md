---
title: "[SOLVED] Cloning a Disk with multiple partitions"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-08-21
I need a way to create a backup such that If I start with a blank hard drive with no partitions, I can restore my backup to it. After the restore the new hard drive will have the ext2 partitions and the ntfs partition from the original drive. I can't just use something like gparted and just copy and paste from one drive to the other because my intent would be to apply it to the same drive after I break it. I like experimenting with different forms of bootable live USB drives but they don't always work and I may prefer to go back to a previous state for the drive.

Thanks

P.S. I forgot to mention that I've tried partimage and I love it, but I don't think it will backup multiple partitions into one file. Though, I hope I'm wrong about that, I would prefer just to use partimage.

---

### Post by ByteJuggler on 2008-08-21
[See here]("http://ubuntuforums.org/showthread.php?p=5627660#post5627660") for an explanation on how to clone an entire disk, partition table and all partitions included. (I think partimage focusses on imaging partitions rather than entire disks, so probably isn't entirely suitable for your purposes.)

---

### Post by JohnGalt131 on 2008-08-21
Thanks
I found dd.
I believe what I want to do is:
$ sudo dd /dev/sde | gzip > /media/400/16GB.gz

---

### Post by ByteJuggler on 2008-08-21
> **JohnGalt131 said:**
> Thanks
I found dd.
I believe what I want to do is:
$ sudo dd /dev/sde | gzip > /media/400/16GB.gz

Very nearly, it should be like this:

```
sudo dd if=/dev/sde | gzip >/media/400/16GB.gz
```

To restore:

```
zcat /media/400/16GB.gz | dd of=/dev/sde
```

---

### Post by caljohnsmith on 2008-08-21
JohnGalt131, I think you would be interested in [this thread that also uses "dd" to image a HDD]("http://ubuntuforums.org/showthread.php?t=892237"); but by choosing the block size to be 512 bytes (same as your HDD sector size), and saving your partition table with "sudo fdisk -lu", it is possible to restore just a single partition from the entire HDD image if you want to. So it basically gives extra functionality over just a simple dd backup where block size is not set, because then the only choice is to restore the entire HDD.

---

### Post by heatblazer on 2013-04-12
OK, I am interested - can I clone 2 partitions. Let`s say I have /dev/sda but sda has sda1 sda2 sda3. By cloning sda I`ll get a raw clone of everything so  if the hdd is 500 G and the OS I want to clone is 80... like what? I`ll have 500Gb image?

---

### Post by overdrank on 2013-04-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

### Post by howefield on 2013-04-12
Old thread closed.

Have a look at Clonezilla, and feel free to start a fresh thread.

---

