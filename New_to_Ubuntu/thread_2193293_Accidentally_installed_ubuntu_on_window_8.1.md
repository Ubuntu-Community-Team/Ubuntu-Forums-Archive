---
title: "Accidentally installed ubuntu on window 8.1"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by Hylobates on 2013-12-12
Greetings,

Yet another thread of this indeed. So let me tell you what happened: I was planning to install ubuntu on a seperate partition, while still retaining windows 8. So I made a bootable usb and followed the steps to install ubuntu. Past weeks however I've been messing with linux mint and the first option it always gave me was: install linux alongside with windows. With ubuntu the first option was to overwrite windows. Out of habit I chose the first option. I immediately shut down my pc but it was too late, no bootable operating system was found. 
I restarted the ubuntu usb and tried to recover my data from there using testdisk. I was always stuck at: The harddisk seems too small! The following partition can't be recovered: ... which is the partition I need to recover. Then I tried photorec but the stuff I get from that is not helping at all, maybe 1 photograph of my thousand in every file that contains hundred unusable files. Else I tried some other stuff but cant recall how it was named. Haven't tried creating a bootable windows usb, which may give me a recovery option? 
I have no cd drive, an ssd of 128 gb, drive that needs to be recovered was ntfs I believe.

Can anyone help me with this? Should I go to a pc repair man or would he try the same stuff as me?

Edit: played around in testdisk again and I recovered 2 partitions I had on my original pc, however these were empty. So It's been useless to have these 2 partitions recovered. Problem is testdisk can't recover the other disks with my main data on it. And now i've looked at that main disk and it says: unallocated space. Am I doomed?

---

### Post by Mark Phelps on 2013-12-12
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by Hylobates on 2013-12-12
Ok thanks a lot! However how do I connect an ultrabook ssd to a computer? Buy msata to usb connector?

---

### Post by Mark Phelps on 2013-12-12
> Buy msata to usb connector? 

I have used a "dock" that will accept SATA drives and have that permanently attached to my desktop -- but a simple SATA-to-USB adapter will work.

Also realize that the solution I proposed only serves to recover individual files and folders.  If you want to recover entire partitions, you would need to use a Windows-based partitioning tool.  Minitool Partition Wizard Boot CD is such a solution.  You download the ISO file, burn a CD from it, boot from the CD -- and can then use that to restore partitions.

---

### Post by Hylobates on 2013-12-14
Thanks again Mark!
I've let R-studio recover my files and out of all recovery programs I tried, this succeeded! Partially... I have the names of the folders, and names of the files + it is not 0kb. However, they seem to be corrupt. I can't open the word image in word for example. R-studio does not give me a preview, but directs me to the hexadecimal editor. Any idea? But I guess I'll have to ask it in another forum, thanks for the help though!

Hmm found out the files I needed most weren't recoverable. I formatted it all, so this thread can be closed. I'm going to start anew on ubuntu.

---

### Post by danny.techify on 2014-02-02
Yeah Ubuntu erased all the partitions and everything so you need to buy a Windows 8.1 disc.

---

### Post by squakie on 2014-02-02
You can't recover an executable via a copy - you would have to install it again.  Software updates system files and installs some other things on the system it is installed on.  Coipying the executable, or even it's folder tree, won't be enough in Windows.

---

