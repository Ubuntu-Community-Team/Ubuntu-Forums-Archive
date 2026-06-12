---
title: "[SOLVED] Adding Second HDD to Filesystem"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by dslachut on 2008-06-16
I'm running Ubuntu Hardy and am beginning to run out of storage on my 160GB IDE HDD containing my filesystem.  I also have a 320GB SATA HDD installed. I have it in two partitions: a 240GB and and 80GB.  I want to keep the 80GB partition to install WinXP or Vista for LAN Parties.

So my Question is:  How do I add the 240GB partition to the main Ubuntu filesystem?

I tried Google, read something about LVM, saw all the terminal code, saw Gparted doesn't have Linux-LVM as a format, became thoroughly confused and registered for this forum.

---

### Post by wolfen69 on 2008-06-16
i make my storage partitions FAT32. just because any OS is able to read and write without permission problems. but that is just me. try [PartedMagic]("http://partedmagic.com/") for formatting and partitioning.

---

### Post by dslachut on 2008-06-16
I'm not (I think) trying to make a storage partition.  Rather, when I go to Main Menu>Place>Computer>Filesystem, I want it to show a total size of 400GB, if that's possible.

---

### Post by wolfen69 on 2008-06-16
first you need to format the drive. then ubuntu will see the drive/partitions.

---

### Post by tamoneya on 2008-06-16
personally I would make it an NTFS or ext3 depending on where you will use it the most.  Compatability for both has increased recently with the NTFS drivers included in ubuntu and fs-driver available for windows.  The reason why I opt out of fat32 is that it cant store files larger than 4GB.  This may seem like a small issue for most people but I run into this limitation fairly often and with HD video and everything on the rise 4GB files are going to become more and more common.  

As for how to actually add the file system here is my short guide:
1. Format the file system as ext3 if you primarily use linux or NTFS if you primarily use windows.  Do this with gparted:```
sudo gparted
```

2. Next mount it to a temporary mount point (all of this will assume that your new partition is /dev/sdb2 since it is the second partition on your second drive and is sata):```
sudo mkdir /media/temp
sudo mount /dev/sdb2 /media/temp
```If you are using NTFS you should add the -t ntfs option:```
sudo mount -t ntfs /dev/sdb2 /media/temp
```

3. Copying the home directory so that you can eventually mount the drive to /home:```
cp -R /home /media/temp
```

4. Unmount the drive:```
sudo umount /dev/sdb2
```

5. Mount onto /home(add -t ntfs if necessary:```
sudo mount /dev/sdb2 /home
```

6. Set it to automatically.  Add this line in fstab. (change ext3 to ntfs if necessary)
```
/dev/sdb2 /home ext3 defaults 0 0
```
Note: you can edit fstab like this:```
sudo nano /etc/fstab
```

---

### Post by tamoneya on 2008-06-16
> **dslachut said:**
> I'm not (I think) trying to make a storage partition.  Rather, when I go to Main Menu>Place>Computer>Filesystem, I want it to show a total size of 400GB, if that's possible.

It doesnt quite work like that unfortunately. While that is possible if you used RAID 0 and such it isnt recommended and not really necesarry.  It is going to cause a bunch of issues with booting the OS since the root filesystem is on a software RAID and you would need to preload the drivers.  A large majority of your files are store in /home so by mounting to /home you will be able to store most of you stuff on the larger harddrive.

---

### Post by dslachut on 2008-06-16
I got to step 3 where instead of using terminal I ran 
gksudo nautilus
and did a copy and paste of the same data (b/c I'm too impatient to not have a graphical display) to the same place but even as root, there are about 12gb of files that it says I lack permission to move.

ed: Should I be worried? do I still need to move those?

---

### Post by tamoneya on 2008-06-16
what are these 12 GB of files? Can you try copying instead of moving?  The purpose of this step is to copy over your files so that when you mount the new drive to /home you can still access everything that was there previously. If you dont do this when you mount to /home it will appear as if /home is empty and your files will be gone.  They are still there it is just you can access them because the were mounted ontop of.

---

### Post by dslachut on 2008-06-16
Ok, got the transfer problem cleaned up.

did step 4, tried step 5
lost all my settings couldn't access any places, so I unmounted doublechecked and tried again

I lost all control of the terminal: "bash: sudo unmount is not a command"
my desktop went white

I pressed Main Menu>quit where my options were Log Out, Lock Screen, and Hibernate.  Logged out, it wouldn't let me relog, so I rebooted.  Logged in, lost the window borders.  Rebooted, my computer seems back in the state it started, finally.

---

### Post by tamoneya on 2008-06-16
thats because the command is not unmount it is just umount.  That wasnt a typo up above.

---

### Post by dslachut on 2008-06-16
good thing I'm posting in the beginner talk forum :)

I copy pasted the mount command and it blew up on me though, any idea what I did wrong there?

---

### Post by tamoneya on 2008-06-16
> **dslachut said:**
> good thing I'm posting in the beginner talk forum :)

I copy pasted the mount command and it blew up on me though, any idea what I did wrong there?

how exactly did it "blow up".  You can copy out of command line by selecting with the mouse and then hitting ctrl-alt-c.  Then paste into the forums with ctrl-v. Try putting it in the code blocks.

---

### Post by dslachut on 2008-06-17
Sry, I meant 'blew up' as I had mentioned in the previous posts.  
More specifically: I successfully unmounted after step 3.  
Round 1 - I copy/pasted step 5 into the command line.  My wallpaper changed to a white screen, I exited the terminal, and tried to access the home folder through the main menu and a dialog box informed me that it did not exist, I tried to open the terminal from the menu and it crashed out because my home folder did not exist. So I rebooted and everything went back to normal.
Round 2 - I c/p step 5 into the terminal and the same thing happened, only this time I left the terminal open.  I c/p'ed the 'umount' command and everything went back to normal.
Round 3 - just like round 2 except I typed 'unmount', was told the command didn't exist, I freaked out, and then had a fun time trying to reboot again. Then posted.

I do appreciate the help so far.

---

### Post by ChameleonDave on 2008-06-17
> **tamoneya said:**
> personally I would make it an NTFS or ext3 depending on where you will use it the most. 

I disagree.  I see people with NTFS problems all the time on these fora.  Stick to FAT, Ext2 or Ext3.

---

### Post by ChameleonDave on 2008-06-17
> **dslachut said:**
> I typed 'unmount', was told the command didn't exist, I freaked out,.

Type this into a terminal

```
echo "alias unmount='umount'" >> ~/.bashrc
```

The next time you open a terminal, it will understand "unmount" as a misspelling of "umount".

---

### Post by tamoneya on 2008-06-17
> **dslachut said:**
> Sry, I meant 'blew up' as I had mentioned in the previous posts.  
More specifically: I successfully unmounted after step 3.  
Round 1 - I copy/pasted step 5 into the command line.  My wallpaper changed to a white screen, I exited the terminal, and tried to access the home folder through the main menu and a dialog box informed me that it did not exist, I tried to open the terminal from the menu and it crashed out because my home folder did not exist. So I rebooted and everything went back to normal.
Round 2 - I c/p step 5 into the terminal and the same thing happened, only this time I left the terminal open.  I c/p'ed the 'umount' command and everything went back to normal.
Round 3 - just like round 2 except I typed 'unmount', was told the command didn't exist, I freaked out, and then had a fun time trying to reboot again. Then posted.

I do appreciate the help so far.

This means that you had a problem around step 3.  Please start from the beginning and after step three stop and I want you to post the results of the two following commands:```
ls -la /media/temp
ls -la /home
```

---

### Post by dslachut on 2008-06-19
Output:
```
cp: cannot stat `/home/dslachut/.gvfs': Permission denied
```
ls -la /media/temp:
```
total 16
drwxr-xr-x 4 root root 4096 2008-06-18 22:48 .
drwxr-xr-x 4 root root 4096 2008-06-18 22:46 ..
drwxr-xr-x 3 root root 4096 2008-06-18 22:48 home
drwx------ 4 root root 4096 2008-06-18 22:41 .Trash-0

```
ls -la /home:
```
total 12
drwxr-xr-x  3 root     root     4096 2008-06-13 09:55 .
drwxrwxrwx 25 root     root     4096 2008-06-17 12:58 ..
drwxrwx--- 68 dslachut dslachut 4096 2008-06-18 22:42 dslachut

```

---

### Post by tamoneya on 2008-06-19
it appears as if there was an error in my command on step three.  I am going to address two issues.  First it was shifted by one directory.  the structure originally was /home/dslachut but I made it /home/home/dslachut.  Also I want to fix the permission denied error.  To do this we will run the command via sudo to gain the necessary permissions but use the "-p" parameter so that you permissions and ownership dont get messed up.

Here is the new step 3.```
sudo cp -p -R /home/* /media/temp
```Then continue to the end of the steps above and you should be set.

---

### Post by dslachut on 2008-06-19
Thanks for you help and patience!  It works.

---

