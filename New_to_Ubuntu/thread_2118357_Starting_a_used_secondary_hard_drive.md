---
title: "Starting a used secondary hard drive"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by Curbie on 2013-02-20
I'm transitioning from Windows to xUnuntu, so far everything is going along well. I have a couple of hard drives I used to test different Ubuntu flavors and still Window partitions that I want to wipe out completely and use as secondary drives in xUnuntu for backup and to store data.

Basically one partition and initialized,  can anyone help me?

---

### Post by pqwoerituytrueiwoq on 2013-02-20
you can use [gparted](apt:gparted) and do what ever you like with the other drives on your system
you can auto mount them using /etc/fstab

---

### Post by sudodus on 2013-02-21
Is this correct:

- You want to use the drives 'only' to store data (not to install any operating system)?

- Is it important to wipe everything, including the boot sector (at the very beginning of the drive), or would it be enough to re-partition and re-format the drives, which leaves data on the drive, but not visible to the file system?

- Do you want a file system, that is available from linux as well as from Windows, or only from linux? Or maybe more than one partition, and different properties? Select the NTFS file system for access from Windows and linux. Select an ext file system (ext4 is the newest) if only linux.
--
As suggested by pqwoerituytrueiwoq, use gparted to delete and create the partitions and file systems. Add easy-to-recognize labels to the partitions.

If you want to wipe all the content beyond that, come back and ask about it!

---

### Post by Curbie on 2013-02-21
P { margin-bottom: 0.08in; }   Sudodus,
 

 An update since the last time we spoke, I took everyone's on my last thread suggestions and evaluated different flavors of Ubuntu and settled on xUbuntu, and both dual boot (xUbuntu/XP) and single boot xUbuntu with XP running on VirtualBox and settled on single boot xUbuntu with XP running on VirtualBox. (Duckhook's Suggestion)

 

 I've done the permanent install of xUbuntu with no problems, but after all the test installs I did, I didn't expect any, and installed VirtualBox running an old XP I had in 30 evaluation (my XP licensed version should be in in a couple of days) and XP runs both my most complicated Excel and Access files without a hitch.
 

 I'm slowly setting up the permanent install of xUbuntu to my taste and thanks to everyone's help on my last thread everything has gone smoothly, so far.
 

 Is this correct:

- You want to use the drives 'only' to store data (not to install any operating system)?
 Correct, this is another .5tb hard drive that I used to do some test Ubuntu installs on and when I installed it as a secondary drive after the single boot (no boot menu) permanent install of xUbuntu, I'm now getting the boot menu, so I wanted to clear everything off it for a fresh, clean drive for xUbuntu data only backups.

- Is it important to wipe everything, including the boot sector (at the very beginning of the drive), or would it be enough to re-partition and re-format the drives, which leaves data on the drive, but not visible to the file system?
 Yes.

- Do you want a file system, that is available from linux as well as from Windows, or only from linux? Or maybe more than one partition, and different properties? Select the NTFS file system for access from Windows and linux. Select an ext file system (ext4 is the newest) if only linux.
 Xubuntu only, Windows backups will be accomplished by backing up the virtual machine folder.
 
- As suggested by pqwoerituytrueiwoq, use gparted to delete and create the partitions and file systems. Add easy-to-recognize labels to the partitions.
After pqwoerituytrueiwoq syggested gparted, I got it and have been monkeying with it, I deleted all but one partition then formatted it as a ext4 filesystem, gparted shows one partition, 458 Unused, and 7.5 used(???), with what I don't know but the beginning of the partition yellow.
 
Also, when I tried the test it by dragging and dropping a folder to it, the folder just floats back to it's original ext4 formatted folder and will not transfer.

---

### Post by sudodus on 2013-02-21
> **Curbie said:**
> 
- Is it important to wipe everything, including the boot sector (at the very beginning of the drive), or would it be enough to re-partition and re-format the drives, which leaves data on the drive, but not visible to the file system?

 Yes.

- Do you want a file system, that is available from linux as well as from Windows, or only from linux? Or maybe more than one partition, and different properties? Select the NTFS file system for access from Windows and linux. Select an ext file system (ext4 is the newest) if only linux.
 Xubuntu only, Windows backups will be accomplished by backing up the virtual machine folder.
 
- As suggested by pqwoerituytrueiwoq, use gparted to delete and create the partitions and file systems. Add easy-to-recognize labels to the partitions.
After pqwoerituytrueiwoq syggested gparted, I got it and have been monkeying with it, I deleted all but one partition then formatted it as a ext4 filesystem, gparted shows one partition, 458 Unused, and 7.5 used(???), with what I don't know but the beginning of the partition yellow.
 
Also, when I tried the test it by dragging and dropping a folder to it, the folder just floats back to it's original ext4 formatted folder and will not transfer.

It might be enough to wipe the first 446 bytes of your drive. But it is extremely important to wipe it on the correct drive, otherwise you destroy your installed system or some other drive. If you want to be 100% sure that you won't wipe your Xubuntu drive, disconnect it, or do it in another computer, where you can disconnect the internal drive and

***boot from your Xubuntu install CD/USB drive***.

Otherwise you can identify the drive with the following commands
```
sudo fdisk -lu
```
and
```
sudo blkid
```
Use only the drive letter, no digit (because you should not write to a partition)
```
sudo dd if=/dev/zero of=/dev/sd[COLOR="Red"]x[/COLOR] bs=446 count=1
```

where x is the drive letter (a for the first drive, b for the second drive etc).

So if you have disconnected the internal drive and boot from an external drive, the command should be
of=/dev/sd[COLOR="red"]a[/COLOR]

and if your internal drive is connected the command should probably be
of=/dev/sd[COLOR="red"]b[/COLOR] (but you need to check that, it might be different)

See this link [[COLOR="Red"]http://www.axllent.org/docs/data-storage/erase-your-mbr/[/COLOR]]("http://www.axllent.org/docs/data-storage/erase-your-mbr/")

Disconnect that drive and connect only your Xubuntu drive. Now you should be able to reboot into your installed Xubuntu and run
```
sudo update-grub
```

/*
only if necessary to make it bootable (but I think you won't need it)
```
sudo grub-install /dev/sd[COLOR="red"]X[/COLOR]  # Example: sudo grub-install /dev/sd[COLOR="red"]a[/COLOR]
```
*/

See these links

[[COLOR="red"]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

[[COLOR="Red"]https://help.ubuntu.com/community/Grub2/Installing[/COLOR]]("https://help.ubuntu.com/community/Grub2/Installing")
--
An alternative is to wipe the whole drive, but then you have to make the partition and file system again.
--
The used space on the 'empty' file system is overhead: file system table, journaling information etc.

---

### Post by Curbie on 2013-02-21
P { margin-bottom: 0.08in; }   Sudodus,
 

 Thanks, I'm sneaking up on it (I hope), following your post solved the dual boot menu issue (grub?), but the issue of dragging and dropping a folder to it, and the folder just floating back to it's original ext4 formatted drive and will not transfer, still exists.
 

 Also, the secondary hard drive has some flavor of an Ubuntu OS on it that has survived the gparted re-formatting to ext4 format, (bin,boot, cdrom, dev...).

---

### Post by sudodus on 2013-02-21
> **Curbie said:**
> 
 Thanks, I'm sneaking up on it (I hope), following your post solved the dual boot menu issue (grub?), but the issue of dragging and dropping a folder to it, and the folder just floating back to it's original ext4 formatted drive and will not transfer, still exists.
 

 Also, the secondary hard drive has some flavor of an Ubuntu OS on it that has survived the gparted re-formatting to ext4 format, (bin,boot, cdrom, dev...).
If you have really reformatted (all of) the drive, (bin, boot ...) are wiped. When in gparted, did you click on the [COLOR="SeaGreen"]green tick icon[/COLOR] at the top of the gparted window? You must do that after selecting what to do. Otherwise nothing happens.

I'm not sure what you want to do with the drag and drop. You can't move or copy a partition, if there is not space enough for it.

---

### Post by Curbie on 2013-02-21
P { margin-bottom: 0.08in; }   Sudodus,
 

 Well, I've got something goofed up, if I try to drag and drop a copy of this post written in Libre Office Write, and saved in home\Documents to the cleared drive, the file (icon) just floats back to it's original home\Documents, I did click the green tick icon originally to apply all to procedures I wanted gparted to perform, but I  redid gparted anyway for reformat for ext4.
 

 I may have misread the “File system – File Manager” program opened on the  secondary drive, all file systems seem to have a hard drive icon button, then a “media” button, then a drive label button, and the hard drive icon button seems to always display the to boot OS no matter what drive the File Manage is displaying (was opened on), maybe that secondary drive is clear, but I still have that data not transferring issue.

---

### Post by sudodus on 2013-02-21
Please make a screen dump of that window and attach it to a reply! You may need to decrease the quality to get it small enough to be allowed (max 976 kB, 1024x768)

---

### Post by Curbie on 2013-02-21
Sudodus,

[IMG]http://i825.photobucket.com/albums/zz177/Curbie_Pics/Screenshot_zpseeafd42d.png[/IMG]

---

### Post by sudodus on 2013-02-22
This looks OK.

It means that you have the following partitions:

- the root file system mounted at / (shown as File System)

- the Data partition mounted at /media/Data (shown as Data)
and you have now browsed to it and are watching it's content. so far only the lost+found directory, no personal files or directories.

- a partition named 520 MB Filesystem (the name is truncated at its icon on the Desktop)

- There is also an icon to your home folder /home/curbie

- There are eject symbols at the 'Data' and '520 MB Filesystem' icons in the left panel of the file browser. If you click on such an eject symbol, the partition will be unmounted (if you are allowed to do it, and you are if they are automounted, but you need superuser privileges to unmount a partition mounted at boot because it is entered into the file **[FONT="Courier New"]/etc/fstab[/FONT]**

You can use this file browser (by default 'Thunar' in Xubuntu) pretty much like you use Explorer in Windows (drag and drop, ctrl a, ctrl x, ctrl c, ctrl v etc).

---

### Post by Curbie on 2013-02-22
P { margin-bottom: 0.08in; }   Sudodus,
 

 I still have something goofed up. For example, when I use Thunar to navigate to the home/curbie folder, I can use Thunar to “Create folder” and it creates a new folder, but when I use Thunar to navigate to the /media/Data, the same “Create folder” option is grayed out, or when I navigate to the home/curbie/Documents, right click on a document, and “send to” “desktop”  it works fine, but if I try to send the same file to “Data”, I get "Permission denied".
 

 Somehow, I don't seem to have write permission for that drive. The  520 MB Filesystem is a USB thumb drive with some Windows apps and data I'll need when I setup XP pro, which a new copy and license came in today for VirtualBox, but I don't want to register until I can backup the virtual machine file to a separate drive in case a one or the other drive pukes.

---

### Post by sudodus on 2013-02-22
I think that the ownership or permissions or both for /media/Data need to be changed.

What is the output of
```
ls -l /media
```

I guess it is owned by root, and that only the owner has write permission. So if you will be the only user, you can change owner to curbie
```
sudo chown -R curbie:curbie /media/Data
```

but if you plan that more people (for example family members) should also use the Data drive, you can create subdirectories for each of these people with their name that are owned by them. This way it is possible to have read access to everything (if the owner wants that), but write and execute access only to the own data.

```
sudo mkdir /media/Data/curbie
sudo mkdir /media/Data/next-guy
...

```
and
```
sudo chown -R curbie:curbie /media/Data/curbie
sudo chown -R next-guy:next-guy /media/Data/next-guy
...
```

If you want a more open system, you can add permissions, so that everybody has read/write/execute permissions. You decide  what you want.

---

### Post by Curbie on 2013-02-24
Sudodus,

After 3 days of reading Internet tutorials and trial and error learning, I&#8217;ve finally got a the second drive working properly and the system booting properly, I&#8217;m sure the whole thing was due to operator error (me), but don&#8217;t ask me what I was doing wrong, I truly don&#8217;t know. For any one else who seems to have the same issue and runs into this thread, here&#8217;s what solved it for me.

Band new system won't boot with two band new seagate 500gb drives,
drive 1 /dev/sda loaded with xUbuntu with one partition and will boot with only this drive in the system,
drive 2 /dev/sdb with one partition, but hangs the system at BIOS when added to the one dive system. Both drives where used to test different flavors of Ubuntu, so both where boot-able at one time or other. 

So, first I booted up from xUbuntu cd.
Then, ran sudo dd if=/dev/zero of=/dev/sdb bs=64k on the second drive to totally clean it (took about 1.25 hours),
Reboot to see if the system will boot with both drives.
...Now it boots from /dev/sda with both drives (the problem had to be something xUbuntu writes to the drive).

Get and install from the Ubuntu Software Center "Disk Utility" and open it, which shows two 500gb drives on the SATA host adapter,
drive 1 /dev/sda ext4 format loaded with Linux with one partition and is boot-able,
drive 2 /dev/sdb is an "Unknown 500gb".
Select  /dev/sdb
Click "Format Volume", Type: ext4, Name: Data, check "Take ownership of filesystem", click "Format".
Click "Mount Volume".
Close "Disk Utility".

Open the Media/Data filesystem from the File Manger (Thunar) and create a folder and copy a folder from home (all good).
Reboot system to see if it will boot with both dives formated.
It does.

Thanks for your replies and patients with all this, now on to understanding backups so I can load my last XP license  on Virualbox and save the virtual machine file and complete this transition.

Curbie

---

### Post by sudodus on 2013-02-24
Great :KS

It is valuable for others, when the solution is described at the end of the thread. Finally, please mark this thread as SOLVED :-)

---

