---
title: "How do I identify partitions ?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Prathmesh on 2008-05-28
I have 200 GB SATA HDD having partitioned 15,15,25....
I have Windows XP installed on 1st drive(that is 15 GiB identified as C: in windows)
I wish to install Ubuntu on 2nd drive(that is also 15 GiB and identified as D:)

I'm trying to format using manual option.
Now the problem is I can't choose and format the D: and install Ubuntu. There is no way I can identify the D: among the other 5 drives(partitions) since there isn't anything as such C: D: ... .

I simply can NOT risk formatting wrong partition and lose all the data.
So plz suggest me any way to install Ubuntu on D: as a 2nd OS Without touching a single byte of other partitions.

Currently I'm using Ubuntu installed inside Windows Xp which I guess is not as good as having on the its own partition.

Thank You 

PS; I'm a newbie to the Linux and understand very less of the technical stuff of Linux

---

### Post by starcannon on 2008-05-28
```
fdisk -l
```

hmmm that may not work for you as I re-read your post....

the windows partitions will have file formats like NTFS and VFAT that is a good indicator of who is what.

---

### Post by Prathmesh on 2008-05-28
Well partitions are 15, 15 , 25, 25, 25, 25, 25, 36 GiB and named C: D: E: F: G: H: I: J: respectively. I m confused because both of the 15 GB(C: & D: )are NTFS. I'm afraid I might accidentally format the Windows XP drive( C: ) insted of D:

I had chosen the last option (Manual) While installing but since I was unsure I'd canceled the installation and installed inside the windows XP instead. I just cant wait to install it on a separate drive/partition.

Can anyone plz tell me what should be the next step. Am I doing right by choosing manual option ?

---

### Post by overdrank on 2008-05-28
> **Prathmesh said:**
> Well partitions are 15, 15 , 25, 25, 25, 25, 25, 36 GiB and named C: D: E: F: G: H: I: J: respectively. I m confused because both of the 15 GB(C: & D: )are NTFS. I'm afraid I might accidentally format the Windows XP drive( C: ) insted of D:

I had chosen the last option (Manual) While installing but since I was unsure I'd canceled the installation and installed inside the windows XP instead. I just cant wait to install it on a separate drive/partition.

Can anyone plz tell me what should be the next step. Am I doing right by choosing manual option ?

HI and welcome, If you have Ubuntu installed with WUBI then you may look at LVPM
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
If you have any data on the d drive as you call it then you should be able to mount it via the live cd and the it will be identified by gparted sda1 or sda2  or so on.

---

### Post by dwasifar on 2008-05-28
> **Prathmesh said:**
> I have 200 GB SATA HDD having partitioned 15,15,25....
I have Windows XP installed on 1st drive(that is 15 GiB identified as C: in windows)
I wish to install Ubuntu on 2nd drive(that is also 15 GiB and identified as D:)

I'm trying to format using manual option.
Now the problem is I can't choose and format the D: and install Ubuntu. There is no way I can identify the D: among the other 5 drives(partitions) since there isn't anything as such C: D: ... .


Unless you have specifically changed the drive letter assignments in Windows, it will have assigned the drive letters sequentially to the partitions on the drive.  The first partition is C, the second is D, and so on.  

You can verify this in Windows by going into Control Panel > Administrative Tools > Computer Management > Storage > Disk Management.  There you will find all your disks, and the partition layout and drive letter assignments of each.  Identify where the D partition falls in the map of your 200GB drive.  Then when you run the partitioner in Linux, choose the partition that is shown in that same place.

Why do you have all those little partitions?

---

### Post by Prathmesh on 2008-05-29
Thanks for the replies !

Well I managed to identify the D: It is labeled 'sda 5' and I figured out the reason why it was labeled so. I had another HDD which has been removed few days back. So sda 2,3,4 dose not belong to this 200 GB HDD.

Now I tried all the ways to install Ubuntu. 1st Method to the 4th but all the time it keeps saying root file system not set. How am I suppose to do that ? I dont see any such option. 

And besides when I proceeded by method #1 Installation said 'all the previous changes will be saved on disk.' And that involves Format of C: D: and I: . Point to be noted is all of them are NTFS and I NEVER selected ANY action for I:  

Whatever I want to do is very simple
 
1. Format 'D:' or 'SDA 5' and install Ubuntu on it.
2. Set Root File System (Needed to install Ubuntu)
3. Keep All the other drives/partitions untouched by undoing whatever I have done during last installation attempt. 

Plz help me to solve these three problems.

Thank you.

---

### Post by cdtech on 2008-05-29
I think the best way, for a new Ubuntu user, is to remove the windows drive so you wont loose any data then install the Ubuntu OS on the drive you have installed in the computer.

Once you have Ubuntu installed you can then reinstall the other window's drive and use grub to reinstall the bootloader.

just my thought.

---

### Post by overdrank on 2008-05-29
> **Prathmesh said:**
> Thanks for the replies !

Well I managed to identify the D: It is labeled 'sda 5' and I figured out the reason why it was labeled so. I had another HDD which has been removed few days back. So sda 2,3,4 dose not belong to this 200 GB HDD.

Now I tried all the ways to install Ubuntu. 1st Method to the 4th but all the time it keeps saying root file system not set. How am I suppose to do that ? I dont see any such option. 

And besides when I proceeded by method #1 Installation said 'all the previous changes will be saved on disk.' And that involves Format of C: D: and I: . Point to be noted is all of them are NTFS and I NEVER selected ANY action for I:  

Whatever I want to do is very simple
 
1. Format 'D:' or 'SDA 5' and install Ubuntu on it.
2. Set Root File System (Needed to install Ubuntu)
3. Keep All the other drives/partitions untouched by undoing whatever I have done during last installation attempt. 

Plz help me to solve these three problems.

Thank you.

HI and choose the manual partition then you can edit the partition you want and create the mount point of / for root. If you like you can post a screen shot.

---

### Post by hyper_ch on 2008-05-29
actually I believe the reason it's labelled as sda 5 is a different one than having used another harddisk earlier...

on a disk you can have up to four primary partitions: sda 1-4... if you want more partitions you need to create an extended one and inside it logical partitions. I assume the 15gb (d: drive) is a logical partition and hence sda 5

---

### Post by Prathmesh on 2008-05-29
Ok I managed proceed installation thanks to **overdrank**

But at the very end of installation it said failed to load something called GRUB(I'm not sure about the word) and installation was not cleanly done :(  OS not installed atall.

Is that becoz I have not chosen any partition as swap space :confused: 

I never used swap space(Paging file) for windows since I have 1 GB RAM. Though windows secure about 3 GB of swap space on the partition it is installed.

EDIT
----
Ubuntu is there on 2nd partition just dose not shows up while booting
The errors I have while installing are
```

GRUB Bootloader failed to load in h0
Failed to initialize HAL

```


Any tips how to get rid of this problem ?

---

### Post by overdrank on 2008-05-29
> **Prathmesh said:**
> Ok I managed proceed installation thanks to **overdrank**

But at the very end of installation it said failed to load something called GRUB(I'm not sure about the word) and installation was not cleanly done :(  OS not installed atall.

Is that becoz I have not chosen any partition as swap space :confused: 

I never used swap space(Paging file) for windows since I have 1 GB RAM. Though windows secure about 3 GB of swap space on the partition it is installed.

EDIT
----
Ubuntu is there on 2nd partition just dose not shows up while booting
The errors I have while installing are
```

GRUB Bootloader failed to load in h0
Failed to initialize HAL

```


Any tips how to get rid of this problem ?

HI and you may try and reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=542683](http://ubuntuforums.org/showthread.php?t=542683)
this link is also great for the grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Prathmesh on 2008-05-30
Thanks a lot overdrank I'll go try those methods to solve my probs.

I have been googling a lot for this issue. Installed Ubuntu more than 10 times and faced same issue.

This is how it gose for me
----
Installation nearly complete over 90% done then it says GRUB Boot loader install failed this is fatal error.
Screen gose black for a while and when it returns it shows up logged in as live user. I can't use internet coz I can't configure my NIC. How am I suppose to download missing stuff ? 
Where is the user account that I created during the install ?
I tried logging in with that account but Ubuntu returned with 'no such account' error.

It is very frustrating for those who haven't used Linux before.
 
Thank you very much for the help.

---

### Post by Prathmesh on 2008-06-02
Last week I wasted many hours installing 8.04 LTS Hardy. Its just not working for me. 

Main issue "GRUB"

But I guess its the time to fallback

Thanks a lot all the helpers for helping me out. I'm going back to windows. I ll come back after next release. I hope it will work next time :D . 

My best wishes !

---

