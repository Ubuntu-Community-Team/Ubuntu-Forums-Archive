---
title: "Need to repartition drive when overwriting with ubuntu 15.04?"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by jdlaustin on 2015-07-14
[COLOR=#000000]When Ubuntu installed automatic updates on 14.04, the updates froze. My system had errors on bootup and a warning that the boot sector was not at the beginning of the drive and that some operating systems might not be able to boot properly. Thus, I followed the instructions on [/COLOR][https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

The system (which is not a dual boot system) continues to have problems so I'm going to start all over by installing ubuntu 15.04. However, from the previous steps I have a 1 GB partition (sda2) at the start of a 1 TB disk that was for the boot partition. Can someone please walk me through the steps of installing 15.04 with the existing partitions or should I merge the partitions before beginning the install or during the install? I'd prefer not to repartition if possible since it takes hours.

Any advice would be very much appreciated.

---

### Post by grahammechanical on 2015-07-14
Please use the Ubuntu live session and open Gparted and take a screen shot of the partition layout. It will help us to understand your partition layout and give you accurate advice.

Basically we use the Something Else option. The installer will present a graphical representation of the partition layout and we direct the installer where to install Ubuntu.

We select a partition and click Change. A dialog will open. It will have panels labelled Use As; Format the Partition; Mount Point.

We set Use As to Ext4. We tick the box Format the Partition. and then we select the Mount Point. A boot partition would be /boot. The partition for Ubuntu would be /. If we have a separate partition for home with our documents in then that would be /home. The installer would automatically detect and existing the swap partition. But we have to go through this process for each partition. Making the selections then clicking OK and then selecting the next partition and clicking Change again.

Then when we are back at the partitions screen we double check that we have made the right selection. We then double check that the Grub boot loader will be installed where we want it to be installed. The default is sda. But we can change that from a drop down menu. And then we click Install Now.

Use As and Mount Point are requirements but Format the Partition is optional. We should format the Ubuntu partition especially with a fresh install of a newer version but if we have a separate partition for home then formatting that partition will wipe out our documents and user configuration files. That might be something that we do not want to happen.

Regards.

---

### Post by Bucky Ball on 2015-07-14
A side note: You are aware that 15.04 is supported until January 2016 and 14.04 LTS is supported until April 2019? Just thought I'd throw it in ... Good luck.

Make sure you have backups of anything you don't want to lose prior to proceeding. If you need to backup data boot from Live media to do it. If you were getting those errors about the partitions not starting at the beginning of the drive I would suggest it is not a good idea to use them. They will still need fixing regardless I'd think.

---

