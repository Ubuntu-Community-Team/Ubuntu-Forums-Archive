---
title: "Format HD using disk utility TROUBLE"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by furioususer on 2015-01-25
I have a new hard drive that I will use only for storing data. I just installed it but I am having difficulties readying a clean empty drive...


I am following the instructions from: [http://www.ubuntulinuxguide.com/ubuntu-1204-lts/hard-disk-partition](http://www.ubuntulinuxguide.com/ubuntu-1204-lts/hard-disk-partition) -  but I can't find this window! 
[IMG]http://i.stack.imgur.com/Cm3gU.jpg[/IMG]


**My problem right now** is that I seem to have made 3 partitions! 
[IMG]http://i.stack.imgur.com/c0i0Y.jpg[/IMG]
I want to format the whole damn thing and make it just one partition (with filesystem NTFS) for private data. 
When I try to format or delete the disk, it formats/deletes every partition individually - instead of merging everything and cleaning out the entire disk. What am I doing wrong?

---

### Post by sudodus on 2015-01-25
[COLOR=#ff0000]Warning: Editing partitions is risky[/COLOR]. It is easy to destroy valuable data. Check and double-check that you are editing the drive you want to edit, and not another drive, where you have valuable data !!!

I think it is easier to use the tool ***gparted***. It is very intuitive.

gparted is available in the Ubuntu desktop iso files and the boot CD/DVD/USB drive. But if you want it in an installed system you need to install it.

```
sudo apt-get install gparted
```

1. What you do in gparted is to first check that the partitions (in the drive you want to edit) are unmounted.

2. Then you can either remove the partitions or simply and directly create a new partition table: Use the drop down menu

***Device -- Create partition table***

Select GPT if the drive is more than 2 GB or if you want to boot in UEFI mode from the drive. Otherwise the default MSDOS partition table is OK.

3. After creating or cleaning the partition table, you can create a new partition, in your case create one big partition and give it the file system NTFS. Click on the green tick icon to really perform the edits.

---

### Post by furioususer on 2015-01-25
sudodus, THANK YOU! Thank you! 

gparted worked like a charm! A program infinitely superior than the built-in version.

---

### Post by sudodus on 2015-01-25
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

