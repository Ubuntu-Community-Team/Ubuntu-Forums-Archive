---
title: "No ability to see or mount partitions or drives???"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by CommKav on 2012-09-07
I just added a new hard drive with 2 partitions, 1 TB each.  The first partition is for a fresh install of Windows XP, with ntfs file system, dev/sda1.  The second partition is extended for Ubuntu 12.04 also a fresh install, dev/sda5, file system EXT4.   

Problem:  I cannot find or mount the windows ntfs in order to access some much needed files.  I have a secondary hard drive with same files on it but cannot see or access that either to get those files to Ubuntu to read/write.  Before this fresh install i could do all of the above with no problems whatsoever thru the Home Folder.  The secondary hard drive has permissions for "root" i am not considered the owner now, where before i was. 

I need full ownership and access to ntfs on the primary hard drive and on the secondary drive and the ability to mount, preferably automatically every time at boot up.

In Home Folder the File System says the owner is "root" as well.  Under the Home directory it the permissions say i am owner and have permission.  This did not happen the first time i installed Ubuntu.

Thanx for help.

---

### Post by oldfred on 2012-09-07
With NTFS root is always shown as the owner, but it does not matter. NTFS does not support Linux ownership nor permissions.

You should see the NTFS partitions in the left panel of Nautilus and the automount should give you read/write permissions. 
Did you label your NTFS partitions, I find that helps me know which is which as Linux may just show it as 200GB or something. You can use Disk Utility or gparted  to label partitions.

If you want to permanently mount the partitions you need to add entries to fstab.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs - UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by CommKav on 2012-09-08
In the Home Folder there are just two primary directories showing:
>Home
>File System
Since the File System is "root" permission only I cannnot change /etc/fstab.  It doesn't show an /etc/fstab.  It only shows an "/etc/fstab.d", and that is completely empty.  So unfortunately I cannot follow your directions.

I guess I need to change my "File System" permissions before I can move forward here.  How do I do this???

And then how do I change /etc/fstab when no such folder exists, not that I can see?

sorry for any headache this may cause.  i know i got one.

Correction:  I did do one thing you suggested.  I changed the label to the ntfs from blank to WindowsXP.  I used GParted to do this.

---

### Post by farrinux on 2012-09-08
> **CommKav said:**
> In the Home Folder there are just two primary directories showing:
>Home
>File System
Since the File System is "root" permission only I cannnot change /etc/fstab.  It doesn't show an /etc/fstab.  It only shows an "/etc/fstab.d", and that is completely empty.  So unfortunately I cannot follow your directions.

I guess I need to change my "File System" permissions before I can move forward here.  How do I do this???

And then how do I change /etc/fstab when no such folder exists, not that I can see?

sorry for any headache this may cause.  i know i got one.

Correction:  I did do one thing you suggested.  I changed the label to the ntfs from blank to WindowsXP.  I used GParted to do this.

As Fred mentioned above the path to fstab is etc/fstab.  The path you mentioned /etc/fstab.d is actually a folder and fstab is not in it. You need to scroll down farther pass the folders and you will find fstab.
Assuming you want to use a grapical editor the command in terminal is ```
gksudo gedit /etc/fstab
``` This assumes you have gedit installed.  If you want to do it in terminal just type ```
sudo vim /etc/fstab
``` Again this assumes you have vim installed.

---

### Post by CommKav on 2012-09-08
I updated fstab and I can read/write to WindowsXP now.  thank you.  :p

But I still have permissions for the File System as owner being "root", and therefore unable to write.  I really don't want to screw this up.  I don't understand how to correct this specific problem.

I will be formatting my secondary hard drive so I will not be adding/changing permissions to that hard drive until after the format.  Are the lack of permissions authorizing me to this hd preventing me from being authorized as owner in the File System?

---

### Post by oldfred on 2012-09-08
The file system is owned by root. On the rare occasions you need to be the admin and edit things in root you use sudo for command line or gksudo for gui apps.

You should have full read/write into your /home where you save your data. Then in fstab you can permanently mount internal drive/partitions and give yourself permissions to read and write. If an external the auto mount by Nautilus should give read/write unlesss previously set to something else & a Linux file system.

---

### Post by CommKav on 2012-09-08
):P

Thanks, I guess we got it solved then.

---

