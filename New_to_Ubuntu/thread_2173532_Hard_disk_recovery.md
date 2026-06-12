---
title: "Hard disk recovery"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by rock2 on 2013-09-10
Hi,

I have a samsung hard disk which Ubuntu won't recognize. I tried connecting this hard disk to other computers, it is not being recognized over there as well. Searching for how to recover data from HDD, I came across lots of different approaches. Since the data is crucial to me, i was unsure how to proceed. Could anyone suggest a method which is really safe?

I looked for the Samsung disk trouble shooter, but it was a question and answer kind of thing, which was more or less similar to Windows trouble shooting.

I have Ubuntu 12.04 installed on Dell Studio 1555. 

Regards

Chris

---

### Post by blazemore on 2013-09-10
Advanced data recovery might not be necessary.

Could you please post the output of running the command: "sudo fdisk -l" with the drive connected?

---

### Post by Mark Phelps on 2013-09-10
What's the filesystem you're trying to access on the drive -- Windows (NTFS) or Linux (ext4)?  Important to know because different filesystems need different utilities for best results.

---

### Post by miroslav3 on 2013-09-10
first look in BIOS to see if its alive an then use testdisk
if its not listed in BIOS then try replacing electronics
if it gets to testdisk be careful

---

### Post by coldraven on 2013-09-10
Start looking for an identical drive on ebay. As miroslav3 says, you may have to swap the circuit board.

---

### Post by varunendra on 2013-09-10
> **miroslav3 said:**
> if its not listed in BIOS then try replacing electronics

> **coldraven said:**
> Start looking for an identical drive on ebay. As miroslav3 says, you may have to swap the circuit board.

..which almost certainly won't work. Been there, done that. Not only the card, not only the model number and parts, but even the BIOS as well has to be matched (read - Identical) and it is NOT guaranteed to match even if both the cards are from the EXACTLY same lot of the drive.

I tried 3 different cards (we purchased 6 seagate 320 GB drives same time, same shop, same model), none worked. What worked is - I unsolded the 8-pin BIOS chip from the fried card (needs great care and expertise or will be either damaged or corrupt due to heat), replaced it with the one on the healthy card (of course voiding its warranty thus). Otherwise, the drive got detected, but showed up as a 4 MB drive (with the healthy card+its original BIOS chip)!!

---

### Post by whitesmith on 2013-09-10
I would check Samsung's site for an hdd test suite. Usually low-level diagnostic stuff that comes directly from the manufacturer is more reliable. If the drive is totally hosed, you might consider Steve Gibson's excellent *SpinRite* utility. Current versions cost around $65 but are worth their weight in gold when you've lost priceless work.

---

### Post by rock2 on 2013-09-11
1. For the output with sudo fdisk -l 

I do not have the hard disk, my friend is trying to recover it as well. So, i ll get it from him day after tomoro. 

2. The filesystem in use is NTFS. I used it with Windows machines as well. 

3. Switching electronic boards -> I can't do anything really technical. :D

4. Samsung's test suite -> Does not exist. It is a questionnaire not a software.

---

### Post by Grumpy818 on 2013-09-11
New to Linux myself but have some questions to help other guy's.
Internal or External drive.
If External tried another USB cable.
External power supply? Does it have an LED lit.
Can you feel vibration or hear clicking noise when powered on.

---

### Post by Mark Phelps on 2013-09-11
> 2. The filesystem in use is NTFS. I used it with Windows machines as well. 

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

