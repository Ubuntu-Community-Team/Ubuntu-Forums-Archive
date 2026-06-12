---
title: "Unable to mount my secondary hard drives"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by wetz on 2013-05-25
Hello all, I am new to the forums, but have lurked for a while. I have searched through the forums and tried to find the solution, but am totally at a loss. I have a home server setup with 3 hard drives, one connected directly to the MB and two connected through a PCIe expansion board. The two connected to the expansion board are my data drives while I have the OS on the small drive connected to the MB. I have gone through and used GParted to format my drives as ext3 and Storage Device Manager to mount the drives and set up preferences. The drives are available and mounted at that point and I can use them normally. If I reboot the machine, I get the error message that the drives failed to mount and press S to skip and M to manually try to fix the error. If I press S, the machine will boot up and the OS will run fine. Once fully booted, the two data drives are inaccessible. If I try to mount them, I get the following message:
> Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 13 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad; rest of file ignored
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab




If I go into storage device manager, I can re-configure the drives and go through the whole process over and they will work, but I am at a loss as to what I should do so they will just mount automatically.
For reference, here is the fstab file output:
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                  proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda1 during installation
UUID=abbf01d7-6191-4151-8bf6-d9219e9f212a  /                      ext4  errors=remount-ro        0  1  
# swap was on /dev/sda5 during installation
UUID=1e3b390b-5fee-48fd-bf17-210050eebcb2  none                   swap  sw                       0  0  
/dev/sdc1                                  /media/Shared Files    ext3  defaults             0  0  
/dev/sdd1                                  /media/Windows Backup  ext3  defaults             0  0  
/dev/sdd1                                  /media/Windows Backup  ext3  defaults             0  0  
/dev/sdc1                                  /media/Shared Files    ext3  errors=remount-ro,users  0  0  
/dev/sdd1                                  /media/Windows Backup  ext3  errors=remount-ro,users  0  0  


I am working with ubuntu 12.04 on a dell system. The expansion card is [this one]("http://www.amazon.com/gp/product/B005B0A6ZS/ref=oh_details_o02_s01_i01?ie=UTF8&psc=1"). I really appreciate any help and look forward to working with this community.

PS:If this is in the wrong section please move it appropriately.

---

### Post by lethall1 on 2013-05-25
use UUID insteed /dev/sdc
If you need help paste here output of 
```
sudo fdisk -l
sudo blkid
```

---

### Post by grahammechanical on 2013-05-25
I would guess that is a bug in Storage Device Manager. When 13.04 was under development I noticed that the Disks utility In 13.04 had a feature that could be used to automount partitions at OS loading time. I tried it and got the same error message as you are getting. When I removed the changes in Disks the error message was gone.

Both of these utilities claim > [COLOR=#333333][FONT=Ubuntu Beta]full customization of hard disk mount points without the need to edit fstab manually. [/FONT][/COLOR]

You may need to undo what you have done with Storage Device Manager and edit fstab manually.

Regards.

---

### Post by Morbius1 on 2013-05-25
> /dev/sdc1                                  /media/Shared Files    ext3  defaults             0  0  
/dev/sdd1                                  /media/Windows Backup  ext3  defaults             0  0  
/dev/sdd1                                  /media/Windows Backup  ext3  defaults             0  0  
/dev/sdc1                                  /media/Shared Files    ext3  errors=remount-ro,users  0  0  
/dev/sdd1                                  /media/Windows Backup  ext3  errors=remount-ro,users  0  0                        
If Storage Device Manager did that don't ever use it again.

** First of all you have multiple references to /dev/sdd1 and /dev/sdc1 so all of them need to be removed except the first occurrences.

** Second, you can't have spaces in the mount point. Linux reads the line sequentially and considers what's after a space to be the next field. So in this case it's thinks /media/Shared is formatted in Files and /media/Windows is formatted in Backup instead of ext3.

** Third, do what   lethall1 said and use UUID's.

A far better way to avoid the problem with spaces in mount points is to create mountpoints in CamelBack ( just remove the space but keep the capitals ):
```
sudo mkdir /media/WindowsBackup
sudo mkdir /media/SharedFiles
```
Then your lines in fstab would look like this:
```
/dev/sdc1  /media/SharedFiles    ext3  defaults             0  0  
/dev/sdd1  /media/WindowsBackup  ext3  defaults             0  0  
```
[COLOR=#0000cd]*And as lethall1 suggested use UUID's instead of /dev/sdxy.*[/COLOR]

---

### Post by deadflowr on 2013-05-25
I'm going go to out here on a limb and say, try renaming the mountpoint without any spaces in between the words.
So, take /media/Windows Backup, and try making it /media/Windows-Backup.

Otherwise it's only reading /media/Windows, which doesn't exist.

Added: +1 to what both Moribus1 and lethall1 said and use UUID instead.

---

### Post by wetz on 2013-05-26
Thank you guys for all your help. I am doing the research now on using the UUID in the fstab file. Should I not use Labels and just assign the drives a mount point instead? Here is my output from the sudo blkid command:
```
$ sudo blkid
/dev/sda1: UUID="abbf01d7-6191-4151-8bf6-d9219e9f212a" TYPE="ext4" 
/dev/sda5: UUID="1e3b390b-5fee-48fd-bf17-210050eebcb2" TYPE="swap" 
/dev/sdc1: LABEL="SharedFiles" UUID="b723fb67-8178-4668-a895-6dfe9ccee1ba" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: LABEL="WinBack" UUID="b6160327-55e1-4826-8894-d14763bf927e" SEC_TYPE="ext2" TYPE="ext3"

```

At this point, I have gone in and changed the Labels and mount points to ones with no spaces to make sure that error does not occur again. Here is my fstab file that I have edited, but have commented out what I have done so far to make sure I don't screw anything up further than I already have...
```
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                  proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda1 during installation
UUID=abbf01d7-6191-4151-8bf6-d9219e9f212a  /                      ext4  errors=remount-ro        0  1  
# swap was on /dev/sda5 during installation
UUID=1e3b390b-5fee-48fd-bf17-210050eebcb2  none                   swap  sw                       0  0
# /dev/sdc1
#UUID=b723fb67-8178-4668-a895-6dfe9ccee1ba  /media/SharedFiles     ext3  defaults                 0  0  
# /dev/sdd1
#UUID=b6160327-55e1-4826-8894-d14763bf927e  /media/WindowsBackup   ext3  defaults                 0  0
```

I was just going to uncomment the UUID lines, but I was not sure if it would be smarter to remove the labels from the drives first so I do not have a conflict between the mount point and the labels. Thanks for all your help again!!

---

### Post by CatKiller on 2013-05-26
I won't comment on your fstab because I can't read it on my phone, but FWIW you can escape spaces in the shell with \, like Windows\ Backup. I can't think of a good reason why that wouldn't also work in fstab for your mount point.

---

### Post by wetz on 2013-05-26
I thank you all for your input, I changed my fstab file to reflect the UUIDs and it works wonderfully! Now to set up some automatic backups so my wife doesn't lose all her pictures (so horrible when it happened before). For anyone that has the same problem in the future, this is what my fstab file looks like now:
```
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                  proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda1 during installation
UUID=abbf01d7-6191-4151-8bf6-d9219e9f212a  /                      ext4  errors=remount-ro        0  1  
# swap was on /dev/sda5 during installation
UUID=1e3b390b-5fee-48fd-bf17-210050eebcb2  none                   swap  sw                       0  0
# /dev/sdc1
UUID=b723fb67-8178-4668-a895-6dfe9ccee1ba  /media/SharedFiles     ext3  defaults                 0  0  
# /dev/sdd1
UUID=b6160327-55e1-4826-8894-d14763bf927e  /media/WindowsBackup   ext3  defaults                 0  0

```

Again, thanks for the help!!

---

### Post by Morbius1 on 2013-05-27
> **CatKiller said:**
> ...  but FWIW you can escape spaces in the shell with \, like Windows\ Backup. I can't think of a good reason why that wouldn't also work in fstab for your mount point.
I was going to go there - actually I was going to suggest a \040 to escape the space but then I saw this post: [http://ubuntuforums.org/showthread.php?t=2143396](http://ubuntuforums.org/showthread.php?t=2143396)

Now I don't know if it's a problem with a "\040" specially and a "\ " would work or if it's just spaces in general that got hosed up so I went safe and removed all spaces in my suggestion.

---

### Post by CatKiller on 2013-05-27
Good to know, thanks. I've never used spaces in a mount point so it wasn't something that I'd tried. With it being standard shell behaviour, if it doesn't work I would consider that a bug for mount/fstab.

---

