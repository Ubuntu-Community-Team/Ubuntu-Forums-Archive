---
title: "missing drives"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by astr0 on 2013-05-18
Hey Folks! 

am very much new to linux , having some issues with some of the drives missing, previously i was running on windows 7 ultimate , i formatted the system using ubuntu setup selecting the option of remove windows and install ubuntu, previously while i was running on windows i had multiple drives such as D , E , F , but after when i completed installing linux i can't find those drives in the system , it might sound dumb but any kind of help would really help me , my college project files and rest are on those drives :) 

Thank you

---

### Post by Kevin McCready on 2013-05-18
It looks like you formatted your computer. Do you have backups? If not, people more knowledgeable than me might be able to help you recover the data, but it will be very tricky.

You could start by post the output of
```
sudo fdisk -l
```

---

### Post by astr0 on 2013-05-19
> **Kevin McCready said:**
> It looks like you formatted your computer. Do you have backups? If not, people more knowledgeable than me might be able to help you recover the data, but it will be very tricky.

You could start by post the output of
```
sudo fdisk -l
```

no bro i dont have any backups i thought it will only erase C drive and install ubuntu on it rest of the drives will be save :| that's what i thought

---

### Post by 3rdalbum on 2013-05-19
When you say "C, D, E and F", do you mean that you have four hard disks in your computer?

Or is it one, just partitioned into four drives?

When Ubuntu says it will erase the hard disk, it means the whole hard disk, not just a partition; sorry.

---

### Post by QIII on 2013-05-19
Hello!

I would stop using the machine *immediately *if you are to have any luck recovering any files.  The more you use the disk, the less likely it will be for you to recover your data -- if it can be done.

Don't panic!  This is not the first time someone has done this.  Generally, but not always, many of the files can be recovered.

There are some trial versions of data recovery programs for Windows.  Someone will probably be by with suggestions presently.  I recommend that you use tools designed to recover your Windows files that are designed for doing that.  However, if you can't do that, you may be able to use some Linux tools like PhotoRec or TestDisk.

Unfortunately, Windows uses the term "drive" or "disk" for multiple partitions on a single physical drive.  In Linux, a drive/device means the entire physical drive.  When the installer asked you if you wanted to install using the entire drive, it meant the whole physical drive and that's what it did.

I suppose that it now goes without saying, but in the future you should always make regular backups -- and make special backups when you make OS level changes.

Again: don't panic.  But don't use that drive, either.

Best wishes.

---

### Post by Mark Phelps on 2013-05-19
Here's a Windows-based approach ...

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

### Post by astr0 on 2013-05-19
> **3rdalbum said:**
> When you say "C, D, E and F", do you mean that you have four hard disks in your computer?

Or is it one, just partitioned into four drives?

When Ubuntu says it will erase the hard disk, it means the whole hard disk, not just a partition; sorry.

no bro its one hard disk partitioned into 4 drives

> **QIII said:**
> Hello!

I would stop using the machine *immediately *if you are to have any luck recovering any files.  The more you use the disk, the less likely it will be for you to recover your data -- if it can be done.

Don't panic!  This is not the first time someone has done this.  Generally, but not always, many of the files can be recovered.

There are some trial versions of data recovery programs for Windows.  Someone will probably be by with suggestions presently.  I recommend that you use tools designed to recover your Windows files that are designed for doing that.  However, if you can't do that, you may be able to use some Linux tools like PhotoRec or TestDisk.

Unfortunately, Windows uses the term "drive" or "disk" for multiple partitions on a single physical drive.  In Linux, a drive/device means the entire physical drive.  When the installer asked you if you wanted to install using the entire drive, it meant the whole physical drive and that's what it did.

I suppose that it now goes without saying, but in the future you should always make regular backups -- and make special backups when you make OS level changes.

Again: don't panic.  But don't use that drive, either.

Best wishes.

Thank you sir , but the softwares you mentioned like PhotoRec or TestDisk will they able to recover the files which were on windows or should i do install windows on a dual boot and use windows based recovery tools?? 

Thank you again for the advice  very much appreciated

> **Mark Phelps said:**
> Here's a Windows-based approach ...

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

ok i will try this , money is not a problem , but the files are pretty much important for me , its my whole semister's work , my research notes and stuff i dont need to recover things like movies and stuff only some doc and pdf documents that's all

---

### Post by astr0 on 2013-05-19
> **QIII said:**
> Hello!

I would stop using the machine *immediately *if you are to have any luck recovering any files.  The more you use the disk, the less likely it will be for you to recover your data -- if it can be done.

Don't panic!  This is not the first time someone has done this.  Generally, but not always, many of the files can be recovered.

There are some trial versions of data recovery programs for Windows.  Someone will probably be by with suggestions presently.  I recommend that you use tools designed to recover your Windows files that are designed for doing that.  However, if you can't do that, you may be able to use some Linux tools like PhotoRec or TestDisk.

Unfortunately, Windows uses the term "drive" or "disk" for multiple partitions on a single physical drive.  In Linux, a drive/device means the entire physical drive.  When the installer asked you if you wanted to install using the entire drive, it meant the whole physical drive and that's what it did.

I suppose that it now goes without saying, but in the future you should always make regular backups -- and make special backups when you make OS level changes.

Again: don't panic.  But don't use that drive, either.

Best wishes.

and yes i stopped using that machine now using my home pc for now

---

