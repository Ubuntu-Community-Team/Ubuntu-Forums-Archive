---
title: "Issues in booting my windows 10 OS after installing Ubuntu 14.04"
date: 2017-11-28
forum: New to Ubuntu
---

### Post by mohamedgougam on 2017-11-28
Greetings,
 

  I had a partitioning in my computer between window 10 and Linux  Ubuntu 17.10 and when I tended to downgrade the ubuntu to 14.04 I  couldn't find the windows anymore. 

 

 I tried boot-repair but the windows 10 is still not available in the list of the installed operating systems.
 Please find the link of my problem in:
 [http://paste.ubuntu.com/26064517/](http://paste.ubuntu.com/26064517/)
 [http://paste.ubuntu.com/26064567/](http://paste.ubuntu.com/26064567/)
 

 Looking forward to hear from you.
 

 
Thanks
 Kind Regards
 

 Mohamed Gougam

---

### Post by oldfred on 2017-11-28
It looks like you elected one of the install options that is erase entire drive and install just Ubuntu.
If you used older version it may not have given warnings that now are in newer versions.

And if newer UEFI system better to use 16.04.3 as it has many updates to work better with newer UEFI systems. 

Did you make a full image backup of Windows before installing Ubuntu?
If you have data you did not back up in Windows, it may be possible to recover part of it. Ubuntu writes its install over entire drive and is smaller than Windows. Windows typically has all data at beginning of drive. So you cannot recover a bootable system, but tools that scan drive like photorec or some Windows NTFS tools may be able to find some files. But if so STOP using system and only use flash drive. As the more you use it, the more you overwrite.

---

### Post by mohamedgougam on 2017-11-29
Thanks Oldfred for your reply. This is a total nightmare. I installed ubuntu 17.10 before the 14.04 but I needed the 14.04 for my Hadoop cluster (big data eco-system). I dint face this when I installed the 15.10 hence I dint take a backup of my data. I have been with this since yesterday. I have sensitive data in my hard drive. I tried to go to the recovery mode and selected Grub-update bootloader (something like that), but it dint work. when I check on the existing partitions by executing sudo fdisk-i, I don't find the windows partition. 
While the installation, the system dint ask about the windows partition, it asked only if I wanted to replace the existing Ubuntu (obviously I must have missed something, but the prominent question was about the 17.10).

Any help would be very appreciate it. 
Thanks

---

### Post by oldfred on 2017-11-29
When reinstalling system, best to only use Something Else install option. I do not use any auto options as I have several Ubuntu installs, other installs, and unallocated space that I do not necessarily want used. So I have to use Something Else.

Do you just now want to fix current Ubuntu install or attempt to recover some data from Windows?

And if you have sensitive data, you absolutely must have a good backup procedure.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

      
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)

---

