---
title: "Mount: Must be superuser to mount."
date: 2008-09-27
forum: New to Ubuntu
---

### Post by TheFly on 2008-09-27
Hi there.
I have just installed Ubuntu EEE after having a bluescreen when i used windows xp. 
But I need to use my external hard drive to transfer some files to ubuntu, but when I connect the hd to the eee usb-port and try to open it, it says: "Cannot mount volume.".
Details: Mount: Must be superuser to mount. 

How can I fix this, and make the external hd available ?

---

### Post by perlluver on 2008-09-27
> **TheFly said:**
> Hi there.
I have just installed Ubuntu EEE after having a bluescreen when i used windows xp. 
But I need to use my external hard drive to transfer some files to ubuntu, but when I connect the hd to the eee usb-port and try to open it, it says: "Cannot mount volume.".
Details: Mount: Must be superuser to mount. 

How can I fix this, and make the external hd available ?

You will want to ```
sudo mount /dev/hdb1 /media/disk
``` or whatever it may be.

---

### Post by Xiong Chiamiov on 2008-09-27
You need to have root priviledges to mount a drive.  Many desktop environments get around this with the HAL daemon, which allows you (as I understand it) to mount drives automagically in the /media folder under a normal user account.  I don't know what your Linux experience is, but are you comfortable with that, or do you need more specific assistance*?

* Which I probably can't help you with, since I've never used the Ubuntu EEE.

---

### Post by Dr Small on 2008-09-27
If the device is not specified in /etc/fstab with the 'user' option, then you will need to use sudo to mount the drive. Otherwise, sudo is not needed.

Dr Small

---

### Post by TheFly on 2008-09-27
Thanks for the answers, but I think it is a bit complicated.

I have this My Book... And i typed : "sudo mount /dev/hdb1 /media/My Book"

Then a list with commands and so appears... but I am not really sure how to use the commands.

Can anyone explain in an easy way how to get the My Book to work?

Thanks!

---

### Post by Xiong Chiamiov on 2008-09-27
> **TheFly said:**
> Thanks for the answers, but I think it is a bit complicated.

I have this My Book... And i typed : "sudo mount /dev/hdb1 /media/My Book"

Then a list with commands and so appears... but I am not really sure how to use the commands.

Can anyone explain in an easy way how to get the My Book to work?

Thanks!
Two things I see with that:

1.  Make sure that the folder /media/My Book exists.  You can't mount to a folder that doesn't already exist on your computer.
2.  My Book has a space in it.  When you type 
```

sudo mount /dev/hdb1 /media/My Book

```
mount sees 3 arguments: /dev/hdb1, /media/My, and Book.  The easiest way to fix this is to include it in single-quotes:
```

sudo mount /dev/hdb1 '/media/My Book'

```

---

### Post by TheFly on 2008-09-27
I have checked /media now, and there are two folders:
cdrom and cdrom0... How am I to create a new My Book folder, when you cannot right click and add a folder?

---

### Post by Dr Small on 2008-09-27
> **TheFly said:**
> I have checked /media now, and there are two folders:
cdrom and cdrom0... How am I to create a new My Book folder, when you cannot right click and add a folder?
```
sudo mkdir "/media/My Book"
```

---

### Post by perlluver on 2008-09-27
Also could you please post the output of ```
sudo fdisk -l
``` so that we can make sure that the other hard drive is /dev/hdb1 and not named something else.

---

### Post by TheFly on 2008-09-27
Okay, thanks!

New problem after typing "sudo mount /dev/hdb1 '/media/My Book':
"mount: special device /dev/hdb1 does not exist"

Hm.. What exactly is /dev/hdb1?

---

### Post by perlluver on 2008-09-27
> **TheFly said:**
> Okay, thanks!

New problem after typing "sudo mount /dev/hdb1 '/media/My Book':
"mount: special device /dev/hdb1 does not exist"

Hm.. What exactly is /dev/hdb1?

That is what the hard drive is called, that is why I asked for sudo fdisk -l.

For an example, I have two hard drives, first one is /dev/sda1, this is where Linux is, the second one is /dev/sda2, that is where I keep my files.

---

### Post by TheFly on 2008-09-27
I have sda and sdb on mine. Sda is where linux is, and sdb is where my files are.

When i type :" sudo mount /dev/sda '/media/My Book'" it says "mount: /dev/sda already mounted or /media/My Book busy

---

### Post by perlluver on 2008-09-27
> **TheFly said:**
> I have sda and sdb on mine. Sda is where linux is, and sdb is where my files are.

When i type :" sudo mount /dev/sda '/media/My Book'" it says "mount: /dev/sda already mounted or /media/My Book busy

You will want to type sudo mount /dev/sdb1 '/media/My Book', the one is important. And yes sda1 is already mounted if that is where Linux is Installed.

---

### Post by Xiong Chiamiov on 2008-09-27
/dev/sdb refers to the 2nd hard drive, which /dev/sdb1 refers to the 1st partition on that drive.  For instance, I have some 10-odd partitions on one of my drives (for various operating systems), which I differentiate between with /dev/sda1, /dev/sda2, etc.

Posting the output of 
```

sudo fdisk -l

```
as requested will help us explain this a bit better.

---

### Post by TheFly on 2008-09-27
Okay, it seemed to be mounted now, but the "superuser"-error still appears when I try to open the my book..

---

### Post by perlluver on 2008-09-27
You will want to own My Book so ```
sudo chown username '/media/My Book'
``` then you should be able to access the directory.

---

### Post by TheFly on 2008-09-27
I will have to rewrite everything from terminal since I cannot use the Wi Fi on the internet with my eee, so I am on another computer now. I cannot copy it with a USB stick either, since the same error occurs...

Device boot:   boot:   Start:       End:
/dev/sda1          *           1            486           Linux
/dev/sda2                     487         490           Linux Swap

Device boot:      start           end
/dev/sdb1            1               981                  Linux

---

### Post by Xiong Chiamiov on 2008-09-27
> **TheFly said:**
> Okay, it seemed to be mounted now, but the "superuser"-error still appears when I try to open the my book..
I was about to ask if you have followed my instructions to chmod and chown it, then realized that was in [a different thread]("http://ubuntuforums.org/showpost.php?p=5866189&postcount=8")...

You should be able to copy files if you open nautilus as root:
```

gksudo nautilus

```

---

### Post by perlluver on 2008-09-27
Ok summing this all up: ```
sudo chown yourusername '/media/My Book'
``` then ```
sudo mount /dev/sdb1 '/media/My Book'
``` then you should be able to open and transfer files from that hard drive.  Or you can do the above stated by Xiong.

---

### Post by Dr Small on 2008-09-27
You can also try:
```
sudo mount -o rw,user /dev/sdb1 '/media/My Book'
```

---

### Post by TheFly on 2008-09-27
Perlluver: I have now entered both commands, but it didn't seem to work? Still getting the error.

---

### Post by perlluver on 2008-09-27
> **TheFly said:**
> Perlluver: I have now entered both commands, but it didn't seem to work? Still getting the error.

Did you try what Xiong said, opening up gksudo nautilus and trying from there?

---

### Post by TheFly on 2008-09-27
Yes, then I get "Cannot mount volume. Invalid mount option when attempting to mount the volume 'My Book'"

---

### Post by perlluver on 2008-09-27
> **TheFly said:**
> Yes, then I get "Cannot mount volume. Invalid mount option when attempting to mount the volume 'My Book'"

Ok instead of trying to open that, run gksudo nautilus and then just mount /dev/hdb1.  It will mount it to another location.

---

### Post by TheFly on 2008-09-27
You mean I should first type gksudo nautilus (then the root folder appears) and then do a new command in the terminal with /dev/hdb1 ?

hdb1 doesn't exist on my laptop, btw?

---

### Post by TheFly on 2008-09-27
However, "/dev/sdb1" is already mounted on /home it says, after running "mount /dev/sdb1" from root.

---

### Post by TheFly on 2008-09-27
> **perlluver said:**
> Also could you please post the output of ```
sudo fdisk -l
``` so that we can make sure that the other hard drive is /dev/hdb1 and not named something else.

```
anders@anders-laptop:~$ sudo fdisk -l
sudo: timestamp too far in the future: Sep 28 02:24:51 2008
[sudo] password for anders: 

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6eb0b942

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         486     3903763+  83  Linux
/dev/sda2             487         490       32130   82  Linux swap / Solaris

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc136

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         981     7879851   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

```

---

### Post by nothingspecial on 2008-09-27
There are 2 main users on your system - root and you.
Root owns your system. It allows you access to directories (folders) that ,if you change or delete them, will not harm your system.
For some reason your my book is owned by root.
You cannot mount it, or copy things on to it, or copy things from it, or delete things from it etc.
 Typing sudo and gksudo in the terminal and then entering your password gives you temporary root powers to manipulate these directories should you need to.
You shouldn`t do this with most directories owned by root but some times stuff that you should own is owned by root, such as  your My Book.

Typing sudo mount is giving you the root powers to mount that drive.

Typing sudo chown (change owner) is giving you the power to change who owns it - root can give it to you but you can`t take it from root.
So (give me powers) sudo (change the owner) chown (to me) yourusername (of this directory)'/media/My Book'

gksudo gives you root powers over guis (windows, as in pointy clicky things not microsoft)

Nautilus is a file browser, when you click on places in your menus the window opens with nautilus. gksudo nautilus opens these files as root so that you can drag, drop and delete by pointing and clicking.
When you have finished with nautilus as root you should close it straight away just in case you forget you are root and change something you shouldn`t by mistake.

All this root business may seem like a pain at times but it`s why we don`t get viruses and it keeps you from messing up your system. Most people who totally waste their system do so by becoming root - I speak from experience.

I`m sorry if I`m being too simplistic but a little understanding can help alot and this is absolute beginners.

---

### Post by nothingspecial on 2008-09-27
> **TheFly said:**
> ```


Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

```

Ok assuming your My Book is a 320gig external it`s /dev/sdc1

---

### Post by TheFly on 2008-09-27
It seemed to be sdc1 yeah!
Thanks a lot for the explaination! Now I things are a bit clearer.

---

### Post by TheFly on 2008-09-28
Now that I have turned the computer on again, it gives me the same error (must be superuser). Do I have to mount the device every single time I connect it to the pc?

---

### Post by TheFly on 2008-09-28
After trying the chown command, terminal says
```
anders@anders-laptop:~$ sudo chown anders '/media/My Book'
chown: changing ownership of `/media/My Book': Operation not permitted
```

---

### Post by Zoasterboy on 2008-10-10
@TheFly:

I had the same problem using Ubuntu-eee and was able to solve it from help provided in this post. As to your question, you will have to mount at every boot.

To make this easier, just create a script you can click on after booting. This is how I did it:

1. Open text editor and enter the mount command (sudo mount dev/...)

2. Save as "MountSD.sh" or name it whatever you want, including sh helps signify that it is a shell script.

3. Right click the new file and hit Properties. Go to the Permissions tab and make sure the "Allow executing file as program" check box is checked.

4. Now, whenever you want to mount, just click the file (or a link to it) and click "Run in Terminal".

There is probably a way to build this into the ubuntu-netbook menu system for the eee, but I have no idea how.

***EDIT***
I've found out that manually mounting like this causes problems, as you can't un-mount from the main menu, and the icon will stay there in the main menu even if the drive is removed. The only way to get it to go away is to do a reboot. I have not tried manually un-mounting yet.

---

### Post by B3n3v3nt3 on 2008-10-13
This problem also happens with my pendrive, it's very simple to solve :)

In /etc/fstab:
> /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

^Just delete that line

---

### Post by josel777 on 2008-10-13
Here is what you do:

- open a terminal
- sudo nano /etc/fstab
- find the line where /media/cdrom is mentioned and put a # at the beginning
- ctrl+o forsaving, ctrl + x for closing
- try again your stick 

[http://forum.eeeuser.com/viewtopic.php?pid=351430]("http://forum.eeeuser.com/viewtopic.php?pid=351430")

---

### Post by got_rice64 on 2008-10-21
Just figured it out with a friend right before i got to the last post.. Sigh.. would have saved like 45min.

If an admin would please mark this solved...

The  commenting the cdrom0 line solved my problem.

---

