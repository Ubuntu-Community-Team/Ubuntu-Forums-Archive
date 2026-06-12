---
title: "trouble installing ubuntu"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by Mostahter on 2013-07-14
i tried to install ubuntu 13.04 on my pc..
first it didn't detect my original os which is win 7 ,then i had to erase my C disk , so now i have no os to run on my pc, and the worst thing is that the installer stuck on detecting file systems and when i try to skip it it shows a terminal-like part in the bottom of the installation window and it just froze , i can't go back and it wouldn't go forward..
what do i do???:confused:

---

### Post by oldfred on 2013-07-14
Did you backup system before attempting install? 
Make a Windows repairCD?

Do you have the 4 primary partition limit that most Windows 7 systems have?
Did you then try to create partitions with Windows which converts to dynamic partitions. Dynamic partitions do not work with Linux.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Mostahter on 2013-07-15
> **oldfred said:**
> Did you backup system before attempting install? 
Make a Windows repairCD?

Do you have the 4 primary partition limit that most Windows 7 systems have?
Did you then try to create partitions with Windows which converts to dynamic partitions. Dynamic partitions do not work with Linux.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

no I didn't backup my system , didn't make a windows repair CD
and yes I have the limit of four partitions, I actually have five..
no I didn't try to create partitions with windows and none of my partition are dynamic

and i don't think my problems has anything to do with my hard disk partitions, I think all my problems started when ubuntu installer didn't detect my original os (windows 7)
so you took the wrong approach at the problem
Though,
thank you very much, [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") 
I really appreciate your effort.

---

### Post by oldfred on 2013-07-15
Besides dynamic partitions another reason other systems may not be seen is if drive was in RAID. Some do not even know drive is or was RAID as vendor set it up that way. We had one user who said a new drive out of the box had RIAD settings that caused install issues.

Best to see details. Even if after an install this shows/runs a lot of scripts that show system configuration.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Mostahter on 2013-07-17
I'll check if my disk is Raid,
then run the boot-repair and post the boot-info link ASAP.
again, thank you for your concern in my problem:KS

---

### Post by Mostahter on 2013-07-17
I've checked my hard disk and I'm sure it is not RAID configured so this is not the problem.
still haven't run the boot-repair, will run it soon and post boot-info link.

---

### Post by mastablasta on 2013-07-17
Ubutnu doesn't always detect the OS on install. however it does detect empty (unformatted) disk space.

note you can boot into live OS ("try ubuntu") and then start with install that way you can browse and such during OS install. or you can first have a look at how partitions are made, user various boot repair features, backup files and more....

---

### Post by Mostahter on 2013-07-19
I ran the boot-repair and got the the link..
the link is [http://paste.ubuntu.com/5891813/](http://paste.ubuntu.com/5891813/), please take a look at it and tell me what's wrong.

---

### Post by oldfred on 2013-07-19
I do not see anything wrong with your system.

You do have several FAT32 partitions in an extended partition. You would have to shrink or delete one of them to make unallocated space for Ubuntu to install into.

I prefer not to use FAT32 anymore unless you have to have it for compatibility with some other device. FAT32 has no journal and cannot store files over 4GB. NTFS is better for a shared data partition with Linux.

---

