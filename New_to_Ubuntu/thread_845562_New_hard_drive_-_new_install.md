---
title: "New hard drive - new install"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by sixgunSal on 2008-06-30
Hiya All,

Just registered and wanted to pop in and say HI!  I just had a hard drive crash a week ago and have a new 500gb hard drive on the way.  Going to start completely from scratch and try and do a dual boot system for the first time.  Xp and Ubuntu - was going to do it when version 7.1 was out but really had no room on that old drive.  I have always wanted to try this and get away from Windows if possible.  Have been doing a bit of reading here, and after I install XP, I guess the optimum partitions would be one for xp, one for Ubunta /, one for Ubunta /home (shared data), and one for a /swap.  Is this correct?  Any suggestions on size of partitions - got 500gb to play with.  I have an older dell 2.66 w/640mg ram.  Any suggestions are more then welcome.  :D  tia

sgS

---

### Post by jamesrfla on 2008-06-30
I think all you need is a ext3 partition and you want to mount it as / For the SWAP partition make it a 1GB. I might be wrong so don't try it till someone with a lot of experience can verify that I'm right.

---

### Post by Mornedhel on 2008-06-30
> **sixgunSal said:**
> I guess the optimum partitions would be one for xp, one for Ubunta /, one for Ubunta /home (shared data), and one for a /swap.  Is this correct ?

Yes. Though you could merge the / and /home partition if you wanted. Having a separate / and /home makes for easier backups and migrations.

A general rule of thumb for /swap used to be "2x or 4x your RAM, depending on usage". Now I find out I rarely use swap, but consider that you may want to suspend/hibernate your computer, especially with a virtual machine running. So the rule still applies.

Now there are several factors to consider. Are you going to be using the XP partition much ? Install heavy stuff on it ? XP alone will be comfortable on 15-20 GB. Make that 50-60 if you want Office and a few games.

/ holds your shared data, not /home . / (aka. "the root") is for the OS, libraries, and applications shared between all users. /home is where you'll have your personal data. You may need 20 GB for / if you install a lot of features, all the rest goes to /home.

But if you set it up this way there will be no (practical) way for XP to access the data, which may be awkward if you end up with all your music on /home and want to listen so something while on XP, so you may want to set up another partition with a filesystem understood by both OSes. If you do that, shrink /home and add a partition in FAT32, or NTFS since NTFS support seems to be nearing 100% on Linux are two possibilities.

---

### Post by stoneybroke on 2008-06-30
Make sure that you install windows first then Ubuntu then when grub loads the menu you can chose what o/s you want to boot into. As for the partitions I might be wrong here but I don't think XP can see a 500gb drive in total or it might be partitioning I have a 250gb drive and when I did what you want to do I'm sure that windows had a problem with partitioning though. Anyway try a small partition say 50-100gb for windows and use the rest for ubuntu and see what portion of the disk you can access.

Hope that helps a bit.

---

### Post by WRDN on 2008-06-30
The partitioning structure you suggested seems fine.

For a HDD, I would create:

- NTFS Partition for XP
- Ext3 Partition for Ubuntu Root Filesystem (/)
- Swap Partition (Recommended to be double RAM)
- Ext3 Partition for Ubuntu Home (/home)
- Shared Partition - NTFS (for both OS, this should be the largest)

---

### Post by sixgunSal on 2008-07-01
Does Ubuntu now recognize NTFS? I thought I read that the shared drive had to have a program called "FS-Drive" so windows can read/write an Ext3 partition?  Is this old news now?  My hdd came today and if I get a chance tomorrow, I"d like to start the install.

---

### Post by dondad on 2008-07-01
> **sixgunSal said:**
> Hiya All,

Just registered and wanted to pop in and say HI!  I just had a hard drive crash a week ago and have a new 500gb hard drive on the way.  Going to start completely from scratch and try and do a dual boot system for the first time.  Xp and Ubuntu - was going to do it when version 7.1 was out but really had no room on that old drive.  I have always wanted to try this and get away from Windows if possible.  Have been doing a bit of reading here, and after I install XP, I guess the optimum partitions would be one for xp, one for Ubunta /, one for Ubunta /home (shared data), and one for a /swap.  Is this correct?  Any suggestions on size of partitions - got 500gb to play with.  I have an older dell 2.66 w/640mg ram.  Any suggestions are more then welcome.  :D  tia

sgS

Depending on what you plan to do with Windows, have you considered loading it in a virtual machine rather than dual boot? I have XP running in Virtual Box and it works fine for the two times a year I run it (to get the updates ;-) That makes it much easier to get rid of if/when you wean from Windows.

---

### Post by sixgunSal on 2008-07-02
Dondad,

I didn't consider a virtual machine.  I would bet if I do a search I could find out how to do that.  But I want to use it more then that, I would like to learn how to use it as well, if not better then windows.   BTW - where in Michigan do you hail from?

Go Wings
sgS

---

### Post by eapache on 2008-07-02
Ubuntu can read and write to NTFS (Windows partitions) by default since version 7.10.

Windows cannot read or write ext3 (Ubuntu partitions) by default. It is possible to install the driver at [http://www.fs-driver.org/](http://www.fs-driver.org/) though, which enables this.

---

### Post by dondad on 2008-07-02
> **sixgunSal said:**
> Dondad,

I didn't consider a virtual machine.  I would bet if I do a search I could find out how to do that.  But I want to use it more then that, I would like to learn how to use it as well, if not better then windows.   BTW - where in Michigan do you hail from?

Go Wings
sgS

I meant run Window in the virtual machine ;-) I run Ubuntu as my native OS with XP in the box.

I am in Canton, MI, near Ann Arbor.

---

