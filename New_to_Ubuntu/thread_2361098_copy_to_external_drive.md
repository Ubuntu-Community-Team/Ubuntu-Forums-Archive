---
title: "copy to external drive"
date: 2017-05-12
forum: New to Ubuntu
---

### Post by Phil Binner on 2017-05-12
I have a failed netgear stora device which has failed. I need to recover the files so I put the hard drive into my Ubuntu computer and got it to load.  In order to recover the files I need to copy them to another site, so I attached an appropriate external drive, which I formatted as FAT and called EKNAS.  Nautilus does not recognise my permissions, so I need to do the copy as root. (I tried to launch Nautilus from the terminal where I was already in root, but that failed.) I have tried to use the terminal to copy to EKNAS, but it says "no such directory".  I tried to move to EKNAS. I used the commands cd /EKNAS    cd /media/EKNAS   cd ../EKNAS   cd ../media/EKNAS  .  It still says "no such file or directory.  There is a directory.  It has an icon in the Launcher and I can open it from there, just not with the authorisation required to recover my files.  

I accept I am (expletive deleted) with the terminal, but I seem doomed to need it.

Please point out the simple route.

---

### Post by oldfred on 2017-05-12
Did you format drive like sda, sdb, sdc? or format partition like sdc1?
You have to format partitions or else you have a "super floppy" or very large floppy drive configured drive which is not easily handled.
Post this:
sudo parted -l

And FAT32 is not best format for larger devices.
FAT32 does not support any file over 4GB nor has journal to help in repairs. FAT32 is ok for smaller partitions or devices where you do not have 4GB files and repairs are quick & easier.

Windows formats like FAT32 & NTFS do not support Linux ownership & permissions. That is usually ok, if just data, not system files as data can be reset to defaults. 

       [URL="https://help.ubuntu.com/community/MountingWindowsPartitions"]https://help.ubuntu.com/community/MountingWindowsPartitions
[/URL]
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion. 

[URL="https://help.ubuntu.com/community/MountingWindowsPartitions"]
[/URL]

---

### Post by Impavidus on 2017-05-12
If you let that external drive mount automatically, it's probably at /media/your-user-name/EKNAS. But normally you should have write permission automatically.

---

### Post by ajgreeny on 2017-05-12
One way to keep all the permissions of files and folders from your failed Netgear device would be to compress or archive them all in, for example, a tar.gz file using the -p option to preserve permissions of the contents and put that on the FAT32 or NTFS backup disk.  The archive itself will not have any permissions retained, but the contents of the archive, once extracted, will all be exactly as they were previously.

If the files are only data it probably will not matter too much.

---

### Post by Phil Binner on 2017-05-12
OK. I now know where EKNAS is mounted, because the instruction   cd /media/first_user/EKNAS works.     Unfortunately the instruction       cp /media/stora /media/first_user/EKNAS doesn't.  What do I try next.

---

### Post by Phil Binner on 2017-05-12
The instruction I used was     cp /media/stora /media/first_user/EKNAS  .  
cd /media/stora        
and 
cd /media/first_user/EKNAS   
both put me in the respective directories.  
The copy command gave me the message "cp: omitting directory '/media/stora'". and didn't do anything.
What am I doing wrong.

---

### Post by cc1984 on 2017-05-13
Hi Phil, I know the terminal can be a bit daunting but once you used to it you will find that it really is a great and powerful tool. I recommend reading [The Linux Command Line]("http://linuxcommand.org/tlcl.php"). It is a great book freely available in pdf. It covers most commands you will need including how to copy files and directories.

As you know to copy a file in the command line you use the ```
cp *thefiletocopy thedestinaton*
```I suspect the reason it gave you the error is due to files and FOLDERS being stored at /media/stora. If you have folders that you need to copy in addition to files then you will need to make the copy recursive by using the -r option. This would look like ```
cp -r *thedirectorytocopy thedestination*
```or in your case ```
cp -r /media/stora /media/first_user/EKNAS
```

---

### Post by Phil Binner on 2017-05-13
Thanks for your help, but it's still fighting.

I tried 

sudo -i (password)
cp -r /media/stora /media/first_user/EKNAS

and got 

cp: cannot create special file '/media/first_user/EKNAS/stora/0tmp/tmp/backupagent/ctl': Operation not permitted

What do I try next.

---

### Post by Phil Binner on 2017-05-13
actually, I think the problem is something different now.  I think it's trying to do the copy but failing in most cases.  I am just not getting a window telling me the copy is taking place, and the failure is slowing it down.  I suspect it's having a problem with the raid format.

I found where the stora disk was by using the Disks program, then got it mounted by using the commands

sudo -i
mkdir  /media/stora
mount -t xfs -r /dev/sdb1 /media/stora/

I tried to run Nautilus from the command line to get the permissions to copy by drag and drop, but that didn't work, which is why I am trying to do the copy from the terminal.  Is there a better way of doing this.

---

