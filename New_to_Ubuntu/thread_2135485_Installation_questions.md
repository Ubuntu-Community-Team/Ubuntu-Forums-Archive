---
title: "Installation questions"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by valleyjim on 2013-04-14
I have a Win7 box and I want to install Ubuntu along side for a dual boot configuration.  I have a ~50G partition set up that I would like to use for Ubuntu.


Whenever I run through the install, I get to the partition section and I see partitions there but none of them match any of the partitions for size that I have on my system.  All of them have the standard linux naming of sda etc.

However, when I am just exploring the drives on my system I see all of the drives correctly, including the partition I created for Ubuntu, by name.

My question is how do I know which partition do I install to?  And when I do look at partitioning I get a message that says that all of the partitions will be destroyed and I cannot have this right now.

I have read through all of the installation instructions and everything that I can find but nothing seems to address my concerns.  Any help/advice will be greatly appreciated.


Jim

---

### Post by carl4926 on 2013-04-14
Run the live system and gparted
Take a screen and post it here

---

### Post by valleyjim on 2013-04-14
Here is a screenshot of what I see.....

[ATTACH=CONFIG]241325[/ATTACH]

---

### Post by wickedpuppy on 2013-04-14
I can see 3 Windows partitions , NTFS , and 1 unknown with just 1mb. You are sure there is a partition with 50GB? Formatted? Unformatted? Perhaps Screenshot of Windows Disk Management if possible?

---

### Post by valleyjim on 2013-04-14
I am positive about the partitions.  As you can see I have one at ~50G named Ubuntu and that is where I would like to do the install....

My disk management console

[ATTACH=CONFIG]241328[/ATTACH]

---

### Post by Cheesemill on 2013-04-14
Unfortunately you are using dynamic disks which is a Microsoft invention that can't be recognised by any other OS's.

You can't install Ubuntu on a drive when Windows has turned it into a dynamic drive so without repartitioning your drive from scratch I think that you're out of luck.

---

### Post by Mark Phelps on 2013-04-14
Linux doesn't use NTFS partitions; instead, it uses its own filesystem partitions.  When you forced the creation of another NTFS partition, you also forced the conversion of ALL your partitions from Basic to Dynamic -- a bad thing.  You will have to remove the F: partition before you can do anything else.

You should then look into converting the Dynamic Disks back to Basic.

---

### Post by fantab on 2013-04-14
Back Up your DATA.

Using Windows Disk Management Tool DELETE the **F:** partition then follow [this tutorial]("http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html").

---

