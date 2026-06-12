---
title: "Installed Ubuntu overwriting entire disk how to recover old data and partition... ?"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by 3mr 3bdeen on 2012-11-24
Hi ! today i installed ubuntu 12.04 LTS from Usb flash memory , In installation setting i replaced my window 7 with ubuntu 12.04 but after replacing i lost  my all data approx 160 gb  and all the drives are converted into a  single drive i try but can't recover my data,
and can't boot from hard disk after remove Usb flash memory from PC , But PC boot when Usb flash memory connected in PC ?

Please, 
               1- Give me a solution for  recovery of my data ?
               2- Give me a solution for boot from hard disk ?



Thanks, for all

---

### Post by newb85 on 2012-11-24
> **3mr 3bdeen said:**
> In installation setting i replaced my window 7 with ubuntu 12.04 but after replacing i lost  my all data approx 160 gb  and all the drives are converted into a  single drive

The installer didn't warn you it would overwrite your data?

I don't have successful experience with digital forensics, so you'll have to wait for someone who can walk you through that.  In the meantime, don't do anything else with your HDD.  The more you do, the less success you'll have.

As a side note, I think you were confused by Windows' convolution of terms.  Windows uses the term "drive" where everyone else uses "partition".  A drive is a piece of hardware.  A partition is a portion of space on that drive.  When you tell Ubuntu to install using the entire drive, it overwrites all partitions on that drive.

---

### Post by ibjsb4 on 2012-11-24
Try testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mark Phelps on 2012-11-24
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by 3mr 3bdeen on 2012-11-24
> **ibjsb4 said:**
> Try testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Idon't know How install testdisk at my PC @ ubuntu 12.4 lts . So sorry but i can't control at my mind for lost my all data .. 
please, are every anyone can learn me step by stop ..  Sorry 
please help me ..
Thanks,

---

### Post by 3mr 3bdeen on 2012-11-24
> **Mark Phelps said:**
> In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.
Thanks, Now i trying ..

---

### Post by ibjsb4 on 2012-11-24
> **3mr 3bdeen said:**
> Idon't know How install testdisk at my PC @ ubuntu 12.4 lts . So sorry but i can't control at my mind for lost my all data .. 
please, are every anyone can learn me step by stop ..  Sorry 
please help me ..
Thanks,

You do not install it, you need to burn a CD.  So find another computer to do this on.

Upon loading TestDisk to your broken computer it will tell you what can be seen/saved.  Since you have overwrote your windows install I expect you will be only able to recover bits and pieces and not a total recovery with this method.

Mark may have the better idea

---

### Post by uzumakifahim on 2012-11-24
> **3mr 3bdeen said:**
> Idon't know How install testdisk at my PC @ ubuntu 12.4 lts . So sorry but i can't control at my mind for lost my all data .. 
please, are every anyone can learn me step by stop ..  Sorry 
please help me ..
Thanks,

My opinion is same as [ibjsb4]("http://ubuntuforums.org/member.php?u=1729120"), maybe mark's suggestion is better. But you can install testdisk from Ubuntu Software Center, it's already on their repository with great rating.

---

### Post by 3mr 3bdeen on 2012-11-25
> **Mark Phelps said:**
> In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...


[SIZE=2]**[COLOR=Red]hhh ... ![/COLOR]**[/SIZE] [COLOR=RoyalBlue]_**Done .. Done .. Done**_[/COLOR]

I followed _**MR| Mark Phelps**_ steps .. step by step .. to catch my data files again . ! 

Thanks _**MR| Mark Phelps**_

Thanks for all .

Sincerely,

---

### Post by DuckHook on 2012-11-25
Please mark the thread "solved" using the thread tools option at the beginning of the thread. I'm sure that after this experience, you will have learned to back up all of your important data before doing any sort of OS installation or system upgrade. It is sad how many people visit this forum with exactly the same critical problem after a bad install. Don't know how to alert people to the need for critical data backup, so expect the same problem as a recurring future issue.

---

