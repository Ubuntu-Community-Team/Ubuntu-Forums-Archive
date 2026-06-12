---
title: "Reinatall of 11.10  in same partition"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by thag8 on 2011-11-16
I am having problems with 11.10 which I want to try and resolve with a reinstall. I want to reinstall 11.10 in the same partition as the original partition in order to avoid partitioning issues (I did a dual boot with XP install). I found a thread from 09 that addressed that specific issue. My only problem is that I am new to using the terminal and am paranoid that I will do something wrong and my computer will disappear in a cloud of blue smoke. below is the post and reply:

Can I install the latest Ubuntu distro on the same partition Ubuntu is already installed?

 First check what partition your / is on before reinstalling by  opening a terminal (Applications>Accessories>Terminal) and using
     Code:
     df -h 
 this will tell you what partition your / is, eg /dev/sda3
Then when you reinstall choose the "Manual Partitioning" option at the  partitioning stage. Then  choose to edit you old ext3 / partition.  (/dev/sda?)  and reset the mount point to / and tick the box to format.
This will reuse the same / partition but will format and install Ubuntu again.
________________________________________________________________________

I found out that 11.10 is on /dev/sda5.
My questions are 1. what does "ext3 /" mean?  2. does the phrase "reset the mount point to /"  mean there will be a place where I enter "/dev/sda5" as the partition? or do I just enter "/"
                                                                      Thank you

---

### Post by wolfen69 on 2011-11-16
Just choose "Something else" when given the choice before the installation starts. Then you highlight the root partition, (make it **/** again) edit, and select format, and type of file system (ext4 most likely). Then do the same for the /home partition, making sure you select **/home** and not **/** again. You can leave swap as is.

---

