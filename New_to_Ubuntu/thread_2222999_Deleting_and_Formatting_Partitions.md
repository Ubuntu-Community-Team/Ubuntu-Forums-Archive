---
title: "Deleting and Formatting Partitions"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by chris221 on 2014-05-09
[COLOR=#333333][FONT=UbuntuRegular]So, I just deleted the XP partition on my hard-drive, and now have 30 Gb of extra space. But that space isnt being used by my Ubuntu file-system, and I'm getting warnings that there is only about 200 Mb of space left, even though I have the empty 300 gb partition[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So, my question is how do I connect the two partitions and allow Ubuntu to use the 30gb?[/FONT][/COLOR]

---

### Post by Impavidus on 2014-05-09
You deleted the WinXP partition. Did you also format the free space to something useful for Ubuntu or did you leave it as unallocated? It has to formatted to be useful.

There are two options. First option is to expand your Ubuntu partition into the free space. This is the flexible option, but it takes time and you need good backups of all your files because if anything goes wrong you can loose all files from the partition that is being resized. The resize can only be performed from a live disk.

The second option is to create a new partition for Ubuntu and mount it somewhere in your file system. The extra storage space will be available in the directory where you mounted it. Best way is to mount it automatically during boot.

If you tell us the details of your current partitioning scheme we can give you detailed instructions. Run```
sudo parted -l
```or post a screenshot from gparted.

---

