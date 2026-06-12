---
title: "error when trying to get to a hard drive"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by majorburt on 2012-10-02
the short of it is, what does this mean and how do i fix it?

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


my computer"s hard drive crashed in windows (possibly killing some boot info) and i'm trying to get the files off using Linux. i can see the hard drive (i assume that the 500 gig file system is my hard drive) but, when i try to access it, i get the above error.

please help a poor man find his way back to his files. :)

---

### Post by critin on 2012-10-02
A quick search found these.  I hope they lead you in the right direction at least.

[http://www.linuxforums.org/forum/ubuntu-linux/164227-solved-error-mounting-mount-exited-exit-code-13-a.html](http://www.linuxforums.org/forum/ubuntu-linux/164227-solved-error-mounting-mount-exited-exit-code-13-a.html)

[http://askubuntu.com/questions/143292/getting-data-off-a-windows-drive-by-booting-with-ubuntu](http://askubuntu.com/questions/143292/getting-data-off-a-windows-drive-by-booting-with-ubuntu)

---

### Post by majorburt on 2012-10-03
> **critin said:**
> A quick search found these.  I hope they lead you in the right direction at least.

[http://www.linuxforums.org/forum/ubuntu-linux/164227-solved-error-mounting-mount-exited-exit-code-13-a.html](http://www.linuxforums.org/forum/ubuntu-linux/164227-solved-error-mounting-mount-exited-exit-code-13-a.html)

[http://askubuntu.com/questions/143292/getting-data-off-a-windows-drive-by-booting-with-ubuntu](http://askubuntu.com/questions/143292/getting-data-off-a-windows-drive-by-booting-with-ubuntu)

thanks for the links!!!

if you could help be understand what is in the links then i would appreciate it alot.

1: how do i access command prompt in Linux so i can use the commands?
2:this is from the second link what is "dd" and how would i find/use it?

thanks alot.

---

### Post by NikTh on 2012-10-03
Hi , 

Try to boot from a LiveCd/Usb of Ubuntu and then open a terminal with [Ctrl]+[Alt]+[t] keys combo. 

First see how Linux recognize your drive's partitions (ntfs) with this command
```
sudo fdisk -l
```We assume now , that Ntfs partition with your files is /dev/sda2 

Then apply below commands 
```
sudo mount /dev/sda2 /mnt
```If mounted successfully without an error , then connect with this command
```
cd /mnt
```and see your files with this command
```
ls
```Let me know if above steps helped you to see your files, If yes , then hopefully we can retrieve them.

Thanks

---

### Post by Mark Phelps on 2012-10-03
One of the most common reasons for that error is corruption of the NTFS filesystem -- which in MOST cases, you can not fix from Linux.  The nftsfix command only repairs the most trivial of errors and is not a substitute for the MS Windows CHKDSK.

If you have no way of booting into MS Windows and running CHKDSK, then you will need to look into removing the drive from your PC, connecting it to a PC running MS Windows, and trying to run CHKDSK from there.  You do that by selecting Computer --> Right-click Properties of the partition you want to repair --> Tools --> Error checking.  That will run CHKDSK on that partition.

---

### Post by majorburt on 2012-10-03
> **NikTh said:**
> Hi , 

Try to boot from a LiveCd/Usb of Ubuntu and then open a terminal with [Ctrl]+[Alt]+[t] keys combo. 

First see how Linux recognize your drive's partitions (ntfs) with this command
```
sudo fdisk -l
```We assume now , that Ntfs partition with your files is /dev/sda2 

Then apply below commands 
```
sudo mount /dev/sda2 /mnt
```If mounted successfully without an error , then connect with this command
```
cd /mnt
```and see your files with this command
```
ls
```Let me know if above steps helped you to see your files, If yes , then hopefully we can retrieve them.

Thanks
when i try to use the seccond command that you gave me, it says this without the quotes:
"special device /dev/sda2 does not exist"

---

### Post by windscape on 2012-10-03
Hi,

That was just an example that might not apply to your system. Please provide the output of sudo fdisk -l

---

### Post by NikTh on 2012-10-03
> **windscape said:**
> Hi,

That was just an example that might not apply to your system. Please provide the output of sudo fdisk -l

Correct. 

**@majorburt**

I tend to agree with @Mark Phelp's opinion , but we don't lose something to give it a try. 

Give the results of ```
sudo fdisk -l
``` 

and ```
sudo parted -l
```

Thanks

---

### Post by ezsit on 2012-10-03
Mark Phelps wrote:
> If you have no way of booting into MS Windows and running CHKDSK, then you will need to look into removing the drive from your PC, connecting it to a PC running MS Windows, and trying to run CHKDSK from there. You do that by selecting Computer --> Right-click Properties of the partition you want to repair --> Tools --> Error checking. That will run CHKDSK on that partition.

I second this advice. It is always more reliable to correct Windows filesystem problems with Windows tools, not Linux tools. No disrespect, just being honest and trying to solve the problem without introducing new issues.

---

### Post by majorburt on 2012-10-08
thanks all!!! i managed to get the stuff off of my hard drive. it didnt want to work when connected through SATA, so i got an adapter. weird huh?

once again, thank you! 
I'm off to my next challenge, using ".exe" in Linux!! I'm thinking wine.

---

### Post by DuckHook on 2012-10-08
Visiting Wine website first will help:

[http://www.winehq.org/](http://www.winehq.org/)

and please mark thread "solved".

---

