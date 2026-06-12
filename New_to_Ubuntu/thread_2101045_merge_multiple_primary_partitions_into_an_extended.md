---
title: "merge multiple primary partitions into an extended partition?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by stri8ed on 2013-01-03
In my current installation of ubuntu, I created both a boot and root partition as two separate primary partitions. I now wish to add a swap partition, but my drive already has 4 primary partitions. My question is, how can I merge my boot and / partitions into one extended partition which would enable me to create a swap?

[IMG]http://i47.tinypic.com/1zqfwb6.png[/IMG]

I am currently dual booting between windows 7 and ubuntu, and im using grub as my bootloader, which I presume is installed on my "boot" partition.

Any help on this is really appreciated.

---

### Post by audiomick on 2013-01-03
That is an unusual setup...

Quick answer is, you are going to have to delete something, I think, to make way for a logical partition.

Before to much speculation happens, I suggest you go here and generate a boot info summary according to the instructions.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

The information that this contains tells exactly what is where on the computer, including the answer to your question about where your grub is. Do that first, and then we will see what to do next.

---

### Post by stri8ed on 2013-01-03
> **audiomick said:**
> That is an unusual setup...

Quick answer is, you are going to have to delete something, I think, to make way for a logical partition.

Before to much speculation happens, I suggest you go here and generate a boot info summary according to the instructions.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

The information that this contains tells exactly what is where on the computer, including the answer to your question about where your grub is. Do that first, and then we will see what to do next.

I suppose I would have to delete the boot partition?

Here is my summary:
[http://paste.ubuntu.com/1492682/](http://paste.ubuntu.com/1492682/)

---

### Post by sandyd on 2013-01-03
Theoretically, you would go through something like this:

1. Put /boot back in the root partition. This is essentially done by mounting boot in a seperate place, and copying all files in the boot partition over to /boot. Make sure all files are owned by root and that permissions are preserved.

2. Delete the grub folder in /boot

3. Install grub
```

sudo grub-install /dev/sda
```

4. Update grub
```

sudo update-grub
```

---

### Post by oldfred on 2013-01-03
It looks like your partitions are next to each other. Fixparts will within the rules of primary & extended partitions convert primary to logical.

With anything like this best to have good backups and backup partition table so you can revert if necessary.
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
    
       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


Several years ago I also did do sandyd's move of /boot, so that does work.

---

