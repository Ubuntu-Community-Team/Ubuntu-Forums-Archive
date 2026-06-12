---
title: "Access is Denied on files in NTFS touched from 8.04?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Ansible on 2008-05-20
I have a dual boot XP/8.04 machine.  

I'm not certain, but I suspect that files I have touched (or maybe created) in 8.04 (or 7.10, when I had that installed) have wierd permissions on them so that I can't copy/view them in windows.  When I try to copy or view these files, I get an 'access is denied' message from explorer.  I suspected disk errors, but some kind of permission hijinks seems more likely.  Out of the 180000 files in my docs directory there were about 25 files that had this problem; chkdsk doesn't find any errors on the disk.  I can't copy these files for backup, but I can delete them.  

Is there something I should be aware of with this?  Is this a known issue?

---

### Post by Ansible on 2008-05-20
Forgot to mention that this drive is from a laptop that is having a bios problem.  I had to take the drive out of the laptop and put it in my desktop to get the files off it.  So I'm accessing these files from windows, but I'm booting off a different drive than usual.

---

### Post by rraj.be on 2008-05-20
try this

FOR NTFS
-----------



-->Click Applications &#8594; System Tools &#8594; NTFS Configuration Tool
    

      The upcoming tool will detect NTFS partitions on your system. Check each partition you wish to access, and, if you wish to, click the mount directory to change it. When finished, click Apply.

--> On the next screen Enable write support for internal device will be selected by default. Click OK.

Your NTFS drive will be now be available in the mount point you selected.
---------------------------------------------------------------------------



FOR FAT 
----------


--> Create a folder where the partition will be accessed (or mounted). Default for Ubuntu is to create all filesystem mount points in the /media directory.

      mkdir /media/windows

--> To automatically mount partitions at boot-up, you will need to edit the filesystem table, /etc/fstab. This is a configuration file that contains the information about all filesystems on your computer. Open the file with this command:

gksudo gedit /etc/fstab 

and add the following line for each FAT32 partition:

--> /dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

   
-->Two additional parameters are "shortname=mixed" and "user=user,group=group". The first will take care that all-caps short filenames show up in all-caps instead of in small characters. The second will take care that you are the owner of all files on the vfat partition, this will allow you to maintain file modification date/time when copying files to the FAT32 partition.
   
-->Then run

sudo mount -a

to mount all the partitions.

Your FAT32 drive will be now be available in the mount point you selected.

---

### Post by Ansible on 2008-05-20
Sorry rraj.be, but your post doesn't address my problem at all.  I'm not trying to access my NTFS partition from ubuntu - I could already do that.  My problem is that I think files that I have touched from ubuntu are not accessible from XP.

---

### Post by rraj.be on 2008-05-20
Ok sorry dear.....

Surely the below will help you

The actual cause for your problem is file system conflict between your Ubuntu and windows....

First run checkdisk utility both in Windows and in ubuntu

in windows checkdisk and i Ubuntu fsck.

then try to access your folders......

this may be some times horrible because your Ubuntu may overwrite some "multiply-block" or some inodes .........

and my best idea would be try some DATA RECOVER TOOLS........

like PC inspector, and try to recover your files and save it to other disk..

this will help you because such data recovering tools are powerful such that it can copy violating any file permissions.

I had the same problem three times and first time i run check disk. It worked.

Then next time it Overwritten my mbr making my system weired......

But then my data recovery technique helped me......

Try data recovery first and if you cant..................then go to check disk utility

---

### Post by KevJB on 2008-05-20
Were you using XP Pro? It could be a ownership/permissions thing. Maybe Ubuntu modified or didn't write them properly. Try this:

Right click on a fonder containing an effected file and click properties.

Click on the security tab.

Click on Advanced...

Click on the Owner Tab.

Click on a user to become the owner, yourself or Administrators if you have admin rights.

Tick the Replace owner on subcontainers and objects.

Click Apply.

Click on the Permissions Tab.

Tick the Replace Permission entries on all chile objects ...

Click Ok.

Try and do stuff with the file again.

---

### Post by Ansible on 2008-05-20
> **KevJB said:**
> Were you using XP Pro? It could be a ownership/permissions thing. Maybe Ubuntu modified or didn't write them properly. Try this:

Right click on a fonder containing an effected file and click properties.

Click on the security tab.

Click on Advanced...

Click on the Owner Tab.

Click on a user to become the owner, yourself or Administrators if you have admin rights.

Tick the Replace owner on subcontainers and objects.

Click Apply.

Click on the Permissions Tab.

Tick the Replace Permission entries on all chile objects ...

Click Ok.

Try and do stuff with the file again.

Cool, that did it.  Not sure what ubuntu did there, but taking ownership did the trick.  Windows couldn't display the current owner, so I guess either that means the owner was not in the current system or the owner was somehow corrupted.

---

