---
title: "boot up error could not write byte: broken pipe"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by le_anh_dung on 2013-09-29
Hi,
I have been using ubuntu for 3 months and I am quite satisfied with it, but today during booting up I got blackscreen and a single-line error: could not write byte: broken pipe and it stopped there. I have tried searching for answers in threads with similar errors, but did not succeed. I really need help because I cannot access my files and have to complete some assignments tomorrow. Thank you very much in advance.

---

### Post by heir4c on 2013-09-29
Use Ctrl+Alt+F1 to go to the tty and log in. Than use:
```
startx
```

---

### Post by erind on 2013-09-29
> **le_anh_dung said:**
> 
[...]

but today during booting up I got blackscreen and a single-line error: could not write byte: broken pipe and it stopped there. 

[...]

That could be a disk full related error from an overgrown log file or the user (or root) trash full. Open a terminal and post the output of:

```
df -h

df -i
```

If you cannot boot straight to your ubuntu install, you might need to boot to recovery mode or boot from a Live CD and post the ouptut of the above commands.
There could also be other reasons for that error (or so I've read), but first make sure that you have enough free space.

---

### Post by le_anh_dung on 2013-09-29
so I made a live usb and used it. This is what i got from:
df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.8G  604M  1.2G  34% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           726M  896K  725M   1% /run
/dev/sdb1        30G  851M   29G   3% /cdrom
/dev/loop0      667M  667M     0 100% /rofs
tmpfs           1.8G  160K  1.8G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.8G  560K  1.8G   1% /run/shm
/dev/sda1       584G   15G  540G   3% /media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0
```

and df -i 
```

Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/cow             464481   4228   460253    1% /
udev             462042    534   461508    1% /dev
tmpfs            464481    459   464022    1% /run
/dev/sdb1             0      0        0     - /cdrom
/dev/loop0       155017 155017        0  100% /rofs
tmpfs            464481     33   464448    1% /tmp
none             464481      4   464477    1% /run/lock
none             464481      6   464475    1% /run/shm
/dev/sda1      38830080 396098 38433982    2% /media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0

 
```

and can you just briefly explain to me what are these data? Thanks for the replies.

---

### Post by erind on 2013-09-29
From the output you posted, it seems that the problematic line is this one:

```
**/dev/loop0 667M 667M 0 100% /rofs**
```

Have you used *WUBI* to install Ubuntu? If so check this link on how to increase the space: 

[http://askubuntu.com/questions/23198/how-to-increase-wubi-root-disk-space](http://askubuntu.com/questions/23198/how-to-increase-wubi-root-disk-space)

I haven't used WUBI before so you might need to do some research on how to do that or you might get help here in the meantime.
There's always the possibility (as I said above) of other reasons for that error (which I've not run into yet), but first check the disk space issue reported above.
--

This line below is your main OS disk, and it looks fine:
```
/dev/sda1       584G   15G  540G   3% /media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0
```
The other lines are OS (Live USB) related devices (tmpfs, udev, ... ), and **/cow** is the USB stick, they look OK too.
I'd be checking only **/dev/loop0** (*probably* wubi) mounted on **/rofs** (read only file system).

---

### Post by le_anh_dung on 2013-09-30
I don't know whether I used WUBI to install ubuntu or not. I installed Ubuntu via live CD.

---

### Post by heir4c on 2013-09-30
/dev/loop0 is the iso mountpoint on your usb. /cow is casper-rw. (See this on my own live-usb via "disk-utility")

The broken pipe: it's a bug (what I have read on internet, I'm not a expert or so)
It's something to do with parent- and child-processen and de RAM. (What I understand from what I read on internet). When the parent process is ending or killed, the child process can't find the right data or the right address to write data to the RAM and to do his job. In many releases of Ubuntu it happens.

---

### Post by Impavidus on 2013-09-30
The UNIX family has the concept of a pipe. It's a connection sending the output of one process directly into the input of another process, without using temporary files. There's only a small first-in-first-out (FIFO) buffer. When the process reading from the pipe terminates (or just closes the input) the data cannot be send anywhere any more. At that moment the pipe breaks and a signal is sent to the process writing to the pipe. The usual result is that the writing program is terminated. Broken pipes may be used on purpose. The program **yes** is nearly always terminated by a broken pipe.

I think the /dev/loop0 device at 100% usage is only there because you ran the command from a live system.

The /dev/sda1 partition is probably your Ubuntu root partition or your /home partition (if you have one). There's nothing wrong with that.

Try running [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). This should give us at least some diagnostics, as right now we don't know what's wrong with your system.

---

### Post by heir4c on 2013-09-30
ThanX Impavidus for the explanation about the broken pipe!!!

---

### Post by le_anh_dung on 2013-09-30
Thank you for your helps and explanations. I needed to work with my computer, so I installed another Ubuntu parallelly with my old one (live cd was not enough, because I wanted to compile something from latex). Now booting up with live cd I tried to use boot-repair, but it seems that it will only fix the boot-up of my new Ubuntu located in sdb (as the GRUB also locates there). How can I make boot-repair repair the problem with my Ubuntu in sda1?

---

### Post by Impavidus on 2013-09-30
Did it give a link to a summary? It may contain some useful information.

---

### Post by le_anh_dung on 2013-09-30
The link it gave me is [http://paste.ubuntu.com/6177055/](http://paste.ubuntu.com/6177055/)

---

### Post by le_anh_dung on 2013-10-01
I'm sorry to spam this thread, but does anyone have a solution?

---

### Post by Impavidus on 2013-10-01
This is a more complicated one...

I notice a few things:
Your hard drive is called sdb, the live disk sda. Usually it's the other way around, but I don't think it matters. Leave it.
Your /etc/fstab of the first Ubuntu installation (on sdb1) has the line```
# UUID=9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0 /               ext4    errors=remount-ro 0       1
```It starts with #<space>. I don't know why these two characters are there, but I think they shouldn't be there so you can remove them. You can access the file from your new Ubuntu install or from a live disk.
You have two older kernels in your first Ubuntu install. Did you try booting one of those?

---

### Post by le_anh_dung on 2013-10-01
I also tried to boot from older kernels in my first Ubuntu installation, but I got the same error. How can I access the file from my first Ubuntu installation? I typed gedit /etc/fstab, but I opened the file from my new Ubuntu instead, because the characters you mentioned #<space> were not there.

---

### Post by Impavidus on 2013-10-02
First mount the partition. The file will be in /media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0/etc/fstab or something like that. Use **gksu gedit <name>** to open it for editing, as it will be root owned. I don't know wether it will solve your problem though.

---

### Post by le_anh_dung on 2013-10-02
I followed your instruction and found out that there was nothing in the file (which is weird) and the command opened *fstab instead of fstab.

---

### Post by heir4c on 2013-10-02
What you can do is: Go to the directory and look for the fstab and the *fstab files:
First command (if it is mounted on /media/....):
```
cd /media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0/etc/
```
Second:
```
ls
```
Now, you see al the files in /etc (on sdb1)
If you find the fstab file rename it to fstab.original with this command (you stay in de /media/9974...../etc/ directory):
```
mv fstab fstab.original
```(maybe you need to be root so use than: root mv fstab fstab.original )

Now there is the file fstab.original and is the file fstab gone.
(If ther is no fstab, you make just the new fstab):
```
sudo touch fstab
```
Than you open the new fstab:
```
gksudo gedit fstab
```
Than you Copy/Paste the tekst below in the file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d683d028-cd14-469e-aead-cd03f87b7ee0 none            swap    sw              0       0
```

Save the file.
Now, you can reboot the system. 
Success!

---

### Post by le_anh_dung on 2013-10-03
First I tried to mount sdb1 to media by the command: 
```
sudo mount /dev/sdb1 /media 
```
and got the error:
```
mount: special device /dev/sdb1 does not exist 
```
then I tried 
                        ```
sudo fdisk -l 
```
and got 
```
 Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003eda7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   638874940   319436446+  83  Linux
/dev/sda2       638875646  1250263039   305693697    5  Extended
/dev/sda5      1242550272  1250263039     3856384   82  Linux swap / Solaris
/dev/sda6       638875648  1242550271   301837312   83  Linux

Partition table entries are not in disk order 
```

The information showed that there is no sdb1 (which is weird or is it just that the partitions rename themselves depending whether I boot up with live CD or with my new Ubuntu?), so I supposed my old Ubuntu was in sda1, so I mounted sda1 instead:
```
sudo mount /dev/sda1 /media 
```
and then according to heir4c's next step: 

```
cd /media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0/etc/
```
and got the error
```
bash: cd: /media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0/etc/: No such file or directory
```
I think the error is caused by the fact that there is no folder named 

9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0 in media

---

### Post by heir4c on 2013-10-03
le_anh_dung, you can't see the sdb1 in the Live-usb/dvd? Ofcource, I was forgotten that. How did you mount before when you find the (empty) *fstab file?
do:
```
sudo mount /dev/sdb1
```
what is the output?

---

### Post by le_anh_dung on 2013-10-03
In my post #19 I booted up with my new Ubuntu and before that I mounted to /mnt, than used the command 
```
 **gksu gedit **/media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0/etc/fstab 
``` 
and I think that (maybe I am totally wrong) this command means that if the file doesn't exist then it will create a new empty one (in this case *fstab), because when I tried to copy/paste the tekst, I could not save it because of incorrect or nonexistent directory. When I browsed in /media there was indeed no folder named 9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0.

---

### Post by le_anh_dung on 2013-10-03
> **heir4c said:**
> le_anh_dung, you can't see the sdb1 in the Live-usb/dvd? Ofcource, I was forgotten that. Howe did you mount before when you find the (empty) *fstab file?
do:
```
sudo mount /dev/sdb1
```
what is the output?
the output is 

```
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

```

---

### Post by heir4c on 2013-10-03
> **le_anh_dung said:**
> In my post #19 I booted up with my new Ubuntu and before that I mounted to /mnt, than used the command 
```
 **gksu gedit **/media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0/etc/fstab 
``` 
and I think that (maybe I am totally wrong) this command means that if the file doesn't exist then it will create a new empty one (in this case *fstab), because when I tried to copy/paste the tekst, I could not save it because of incorrect or nonexistent directory. When I browsed in /media there was indeed no folder named 9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0.

Ok, but can you see the sdb1 in your new Ubuntu install after you booted up?
If so you can try to open /etc via Nautilus. So than you can see if there is a fstab file.
You can try to mount via "Disk utility" (or just look there if he recognize the partition.)

---

### Post by le_anh_dung on 2013-10-04
I cannot see sdb1 in my new Ubuntu. When I used fdisk -l there was no such partition in the list.

---

### Post by heir4c on 2013-10-04
Have you try to mount it with the "Disk Utility"? (or at least recognized) Try not only in your new Ubuntu but also via Live-cd/usb.

---

### Post by le_anh_dung on 2013-10-05
Disk utility unfortunately does not recognize any sdb partition. There are only sda partitions. Is there any hope? It begins to irritate me, that the operation systems just suddenly does not function without any reason, eventhough I do not have any valuable files or documents I spent a lot of time with configurations for my old Ubuntu and I really do not want to go over the same process again.

---

### Post by heir4c on 2013-10-05
You mount it on /mnt?

---

### Post by le_anh_dung on 2013-10-06
when I tried to mount it into /mnt via Terminal, I got the error: mount: special device /dev/sdb1 does not exist

---

### Post by heir4c on 2013-10-06
The problem we have is this:

> **Impavidus said:**
> This is a more complicated one...

I notice a few things:
Your hard drive is called sdb, the live disk sda. Usually it's the other way around, but I don't think it matters. Leave it.
Your /etc/fstab of the first Ubuntu installation (on sdb1) has the line```
# UUID=9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0 /               ext4    errors=remount-ro 0       1
```It starts with #<space>. I don't know why these two characters are there, but I think they shouldn't be there so you can remove them. You can access the file from your new Ubuntu install or from a live disk.
You have two older kernels in your first Ubuntu install. Did you try booting one of those?

Because of the #<space> in front of the UUID, the sdb disk is not visible on your new ubuntu or via the live-cd/usb. But BootRepair see the fstab file. So there must be a possibility to see (and change) the fstab in sdb1.

---

### Post by heir4c on 2013-10-06
I start a tread with your problem on the Dutch Ubuntu forum. 
There someone ask if you see the disk in the BIOS. So, go in to bios (or maybe the bootmenu with F12 or F8) and look for the boot sector and look for the sdb drive. (I don't think so but you never now).

---

### Post by christopher-freibichler on 2013-12-07
Thank you folks!
I had the same error message and startx gave me a similar message according 
**/dev/sda1 [...] 0 100% /rofs**Because somebody wrote that it could be a "disk full problem", I started autoremove from terminal (which deleted about 138 MB), tried a reboot, and everything was ok again :-)

---

### Post by heir4c on 2013-12-07
> **le_anh_dung said:**
> In my post #19 I booted up with my new Ubuntu and before that I mounted to /mnt, than used the command 
```
 **gksu gedit **/media/9974d4e1-ad8f-4ccc-acaa-04e86a93f8d0/etc/fstab 
``` 


I see now this little difference: You mount it to /mnt and then you used in your command: /media/9974.... When you mount it on /mnt than you must use /mnt/9974.... and not /media. That are 2 different mount points under /

---

### Post by cecilieaux on 2014-07-13
I just got that error after updating the Hardware Enablement Stack. I say this because I just tried 

> startx

per the recommendation of [heir4c]("http://ubuntuforums.org/member.php?u=739011") and I got the message that my HWE is OK until 2017.

---

