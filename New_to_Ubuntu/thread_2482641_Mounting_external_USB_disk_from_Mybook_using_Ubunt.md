---
title: "Mounting external USB disk from Mybook using Ubuntu 22.04 virtualbox VM on Win10 host"
date: 2023-01-06
forum: New to Ubuntu
---

### Post by vjekobalas on 2023-01-06
What can I do to mount and copy data from a disk which was previously
in a WD Mybook Live ? 

I had to remove the disk from MyBook Live as the network copy became
extremely slow / saw a brown spot on the Mybook Live pcb when I removed the disk).

The disk is connected to my pc as a USB drive (via a SCYTHE sata->USB "adapter").
Win10 is host OS and Ubuntu 22.04 is guest OS to which I have tried to mount the drive.
The drive is /dev/sdf as can be seen from

sudo lsblk

loop6    7:6    0 400,8M  1 loop /snap/gnome-3-38-2004/112
loop7    7:7    0  45,9M  1 loop /snap/snap-store/599
loop8    7:8    0  91,7M  1 loop /snap/gtk-common-themes/1535
loop9    7:9    0  45,9M  1 loop /snap/snap-store/638
loop10   7:10   0  49,6M  1 loop /snap/snapd/17883
loop11   7:11   0   284K  1 loop /snap/snapd-desktop-integration/14
loop12   7:12   0   304K  1 loop /snap/snapd-desktop-integration/43

sda      8:0    0    25G  0 disk 
[FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda1 8:1 0 1M 0 part 
[FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda2 8:2 0 513M 0 part /boot/efi
&#9492;&#9472;sda3   8:3    0  24,5G  0 part /var/snap/firefox/common/host-hunspell

                                 /

sdb      8:16   1     0B  0 disk 
sdc      8:32   1     0B  0 disk 
sdd      8:48   1     0B  0 disk 
sde      8:64   1     0B  0 disk 

sdf      8:80   0 931,5G  0 disk 
[FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sdf1 8:81 0 1,9G 0 part 
[FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sdf2 8:82 0 1,9G 0 part 
[FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sdf3 8:83 0 489M 0 part 
&#9492;&#9472;sdf4   8:84   0 927,2G  0 part 

sr0     11:0    1  50,5M  0 rom  /media/username/VBox_GAs_7.0.4

If I look at GUI files view, I can see the USB disk (marked as 996 GB Volume)
If I try to mount it, I get the error:
"Unable to access "996 GB Volume"
Error mounting /dev/sdf4 at /media/username/number: wrong fs type,bad option,bad superblock
on / dev/sdf4, missing codepage or helper program, or other error.


I found this link referring to blocksize:
[https://kevrocks67.github.io/blog/accessing-data-from-wd-my-book-live-hdd.html](https://kevrocks67.github.io/blog/accessing-data-from-wd-my-book-live-hdd.html)

---

### Post by oldfred on 2023-01-06
Is format NTFS?
Windows fast start up may have set hibernation flag preventing normal mount. 
It can be force mounted read only from terminal, but best to turn off fast start up in Windows.

Post this in question above (-e 7 to exclude snaps):
lsblk -e 7 -f

---

### Post by vjekobalas on 2023-01-06
[INDENT]As far as I could understand from from googling, the format is ext4 (or is that for the OS partitions/not sure)
All I can say is if I plug the USB disk in pc, with Win10 host only running, I see two drives in Win10 but can't open either. 
Once I start the Ubuntu VM, the disks disappear from Win10 and the one USB disk is visible in Ubuntu GUI
and I can't mount it with reason described in the message.

I think hibernation is turned off in Win10 as I split the Win10 disk into two partitions a few days ago
and turned it off as one possible cause of not being able to reduce size of Win10 partition enough.


Output for lsblk -e 7 -f:


AME FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS

sda                                                                         
&#9500;&#9472;sda1
&#9474;                                                                           
&#9500;&#9472;sda2
&#9474;    vfat   FAT32       FEDD-D067                             506,7M     1% /boot/efi
&#9492;&#9472;sda3

     ext4   1.0         8b1027f1-b30a-4989-b297-f1c94e7335f9    9,7G    54% /var/snap/firefox/common/host-hunspell

                                                                            /
sdb                                                                         
sdc                                                                         
sdd                                                                         
sde                                                                         
sdf                                                                         

sr0  iso966 Jolie VBox_GAs_7.0.4

                        2022-11-16-17-05-17-10                     0   100% /media/username/VBox_GAs_7.0.4



[/INDENT]

---

### Post by MAFoElffen on 2023-01-06
@oldfred

This is a Virtualization question. With Windows 10 running VirtualBox and trying to temporarily mount USB to an Ubuntu VM Guest.

I am sure that there is an option in the VirtualBox VM window menu to connect USB devices... But I haven't used VirtualBox for almost a decade.

I am sure there are VirtualBox Users in the Virtualization Section that can answer this question in an instant.

I'm thinking something like this:
[https://www.linuxbabe.com/virtualbox/access-usb-from-virtualbox-guest-os](https://www.linuxbabe.com/virtualbox/access-usb-from-virtualbox-guest-os)
...but it might be even simpler by a window menu option for something temporary.

EDIT: I know 3 different ways to do this from KVM... LOL

---

### Post by tea for one on 2023-01-07
Why not remove the obstacles of Windows 10 host and Ubuntu Guest?
Have you tried to access the drive via a live Ubuntu session?
> Error mounting /dev/sdf4 at /media/username/number: wrong fs type,bad option,bad superblock
on / dev/sdf4, missing codepage or helper program, or other error.
The above message may still appear but, possibly, easier to diagnose?

---

### Post by MAFoElffen on 2023-01-07
Is the VirtualBox Extension Pack installed? By default VB only supports USB 1.0. With the extension Pack it supports USB 2.0 and 3.x.

---

### Post by vjekobalas on 2023-01-19
I installed Ventoy with Ubuntu 22.04 .iso on a USB disk drive and used Ubuntu in live mode with the 
hard disk in question connected again as a USB drive (via a SCYTHE sata->USB "adapter").

The result is the same - the disc is visible but can't mount it and get the following error:

Unable to access "996 GB Volume"
Error mounting /dev/sdc4 at /media/ubuntu/.........: wrong fs type, bad option,
bad superblock on /dev/sdc4, missing code page or helper program, or other error

---

### Post by tea for one on 2023-01-19
Assuming that your file system is ext4 (as mentioned in post 3), this info should help:-
[https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)
I know the instructions are old but I'm pretty sure that they are valid for ext4.
You may need elevated (sudo) privileges now.

---

### Post by ActionParsnip on 2023-01-19
Windows can't read Ext4. I suggest you boot to a USB stick with Ubuntu on it and read the data that way.

Secondary question, is there no backup of the data? If not......why not?

---

### Post by vjekobalas on 2023-01-19
Thanks, will try that out.

---

### Post by vjekobalas on 2023-02-05
Trying the suggestions above the furthest I could get was to
see the directories and "?" in the permission fields for the drive and
still unable to mount or access.

I felt I was a bit out of my league in Linux to go further so I 
tried using Photorec to try to recover the files but after 3 days running,
saw what was recovered was garbage (small bits and pieces of text
and corrupt images/videos.

In the name of learning, was wondering if anyone else has any
ideas on how to proceed otherwise, I'll call it a day with the data
on that disk and format it for further use.

---

### Post by DuckHook on 2023-02-05
The fact that you can now see the directories is encouraging and means that you are closer to the end zone than you may think. 

Directories with a string of ?s in the permission fields mean that you have the wrong permissions to see those directories. However, the mere act of their displaying themselves to you means that they are accessible. It's just a matter of using the right user ID to see them.

Others have suggested that you try reading them as root. That is to say, instead of simply:```
ls -laH
```…preface that command with *sudo*. That may be all it takes.

PS. Photorec is strong medicine. It may not be necessary in this case. Proceed on a least harm basis by trying to read those directories with *sudo* first. If that doesn't work (they aren't owned by root) then chown them into the UID:GID that corresponds to yours (usually 1000:1000). Then try accessing the files.

---

### Post by vjekobalas on 2023-02-26
While trying to make headway via instructions in post #8, I
could conclude that it was 64K block size ext4 and
via this web page :
[https://n-dimensional.de/blog/2012/05/01/wd-mybook-live-data-rescue/](https://n-dimensional.de/blog/2012/05/01/wd-mybook-live-data-rescue/)
I found debugfs(8) could be used, with which I was able to
rescue what was relevant from the disk.

---

### Post by DuckHook on 2023-02-27
Congratulations on finding your solution. And thanks for returning to this thread and sharing it.

It's an awesome one and well worth the read.

Good Luck and Happy Ubuntu-ing!

---

