---
title: "Do I want to unmount my hard drives from Vista?"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by njn44 on 2011-10-12
I have the 1st hard drive on an HP laptop failed and the 2nd has a backup that I can't access from 2009 (absolute beginner).  I can't boot Windows Vista (64 bit) but I can boot Ubuntu.  I am trying to install Ubuntu and it says, "The installer has detected that the following disks have mounted partitions /dev/sdb, /dev/sdc  Do you want the installer to try to unmount the partitions on these disks before continuing?  If you leave them mounted you will not be able to create, delete or resize partitions on these disks but you ay be able to install to existing partitions there."

I can see in Disk Utility in Ubuntu that the 2 hard drives show up but I can't get the information off of them.  Do I just resign myself to losing all of my information and just go with Ubuntu?  If I umount the partitions will I lose any future chance to get the information?  Basically, I rationally know and understand that all of my 100s of Stickies that have loads of key information must be gone but I still have a small glimmer of hope that I might possibly be able to salvage.  Also, I have no iTunes backup and only a small iTunes shuffle so none of my music is backed up (from lack of funds not lack of sense).

Many thanks in advance for your assistance.

---

### Post by FLCL on 2011-10-12
You're description is a little hard to understand so correct me here if I'm wrong. You're attempting to dual boot Ubuntu and Windows Vista? 
You have 2 hard drives, one from your laptop that failed to install Ubuntu onto and a 2nd that is being used for backup (which you don't want to use because you'll lose all your data) Right so far?

---

### Post by njn44 on 2011-10-12
Sorry for the poor explanation.  I can't boot Vista so I burned a Ubuntu disk on an old Macbook and I got my PC to boot using Ubuntu.  There are two HDD and the first seems to be busted.  When I decided to install Ubuntu it asked me if I wanted to unmount the partitions.  I am concerned this will permanently make it impossible to ever get anything off of the Vista formatted drives.  Is unmounting the drives like formatting them and erasing them?

Thank you very much for your help!

---

### Post by njn44 on 2011-10-12
I couldn't boot from the 1st drive (blue screen of death with white cursor that can move but nothing else).  I tried System Restore and it didn't work.  The only way to get the PC laptop up and running was with Ubuntu. I can see both drives in Disk Utility in Ubuntu but can't get the information off of it.  The second drive has backup.exe but won't execute if you click on it.

I am pretty much resigned at this point to saying goodbye to Vista since HP doesn't give you backup/restore disks.  

I am worried that unmounting the two hard drives in my Ubuntu installation will make it impossible to get the information (if any is still there) when or if I ever get the money to have a qualified person look at it.

How can I install Ubuntu and have it co-exist with Vista?

I apologize if this is confusing, I appreciate your patience and assistance very much.

---

### Post by hreichgott on 2011-10-12
Using a LiveCD (or live USB stick) to "Try Ubuntu without any changes to your computer" might be the right thing for you. It won't actually install Ubuntu or alter anything on the hard drives, it just runs Ubuntu from the CD or USB, so you'll have a chance to check whether you can in fact get at the files you want from Ubuntu.

A how-to is here
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Files from other partitions may not show up immediately; if they don't you may have to open up a terminal and mount the drives yourself. Search this forum or help.ubuntu.com for "mount hard drive" for better information than I could give you.

Also, the liveCD includes a partition editor so you can make changes to those partitions if you want. (Editing partitions is a totally different thing from looking at files inside those partitions--think of partition editors as things that change the size of a closed box containing your information, not things that can open the box.)

---

