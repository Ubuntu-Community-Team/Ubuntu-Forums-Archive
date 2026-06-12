---
title: "Is it possible to partition hard drive without formatting it?"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by piyushshri on 2011-10-17
I have Ubuntu 11.10 installed on my continuous (without partitions) hard drive 90 GB of which is free. I want to create partitions over this 90 GB free space. Is it possible to create partitions without formatting the drive? I don't want to uninstall or reinstall Ubuntu, also all my data is stored in the drive so I don't want to lose it.

---

### Post by mcduck on 2011-10-17
Are you absolutely sure the drive is unpartitioned? Because while that *is* possible, it's truly a rare setup. And the Ubuntu installer by default will set you up with at least two partitions, one for root and one for swap...

(Actually I'm not sure if the installer would even allow you to install without any partitions on the drive).

You can check that by running "sudo fdisk -l" in a terminal. The command will list all your drives, and their partition schemes. Post the output here if you need help decyphering it. :)

If the drive actually has partitions, then things should be fairly easy. Existing partitions can be resized and moved around as necessary to get the new partitions you want, and that doesn't require formatting (although you definitely should have backups of all your data when messing around with partitions and filesystems, as there is always a risk of something going wrong...)

On the other hand if the drive really is unpartitioned, your only option would be to copy all data from it to somewhere else, and then create partitions on the drive & copy the data back.

---

### Post by mike555 on 2011-10-17
Yes you can, just make sure you don't shrink your ubuntu area too much , if you use the live cd and gparted it will show you a highlighted area that ubuntu is taking up , just leave enough area for ubuntu (at least 20GB)then a swap partition (about 4GB )the rest you can use for something else .....just don't format the area that Ubuntu is on.

---

### Post by FormatSeize on 2011-10-17
Yes. You can create a partition in the free space without formatting the drive. You can either use cfdisk, or you can use a utility with a graphical user interface like gparted or something like it.

---

### Post by egalvan on 2011-10-17
The OP is most likely looking at a drive with only one partition...

that's probably where is comment "continuous drive" comes from..

---

### Post by grahammechanical on 2011-10-17
The best advice is always back up first.

I have used a Live Ubuntu CD to create additional partitions and I did not loose my data. I have also moved and resized partitions and it was safe. I have resized my /home partition twice to create two 10GB partitions to install other versions of Ubuntu on for testing purposes. I am running 11.10 from one of those partitions now. And I did not lose any data on my working Ubuntu install.

You will need to format the new partitions in order to use them. If you are thinking of making a separate /home partition. Do not make my mistake. You need a way to tell Ubuntu that the /home folder is on the new /home partition. Otherwise the OS will fail to boot. It happened to me.

I sorted out my mess by re-installing Ubuntu into the first partiton and mounting it as / and also mounting the new partition as /home. And then I put my data into the home folder of the new /home partition.

There may be another way to do this through the command line. I do not know. Others may be of help here.

Regards.

P.S. I built my own machine. New empty hard drive. Installed Ubuntu. I chose, use entire disk. And there was only partition apart from the swap partition. If I had not read up on Linux I would not have known that the swap partition was being created. I would have said one continuous partition.

---

