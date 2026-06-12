---
title: "Still stuck on this Unable to mount drive"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Dik_Starbuck on 2008-09-29
I have been searching thru this site for a solution. Ive tried other threads but couldnt get it to work for myself. Trying different things here and there and I thought i'd finally just ask.

So I had no trouble connecting a USB drive before, then I wanted KATE so I installed KDE, now it say Kubuntu instead of Kubuntu. Now I cant seem to access my USB drive. I know it should work because I installed Unbuntu from the USB drive, but haven't really had it work since. i installed Ubuntu Eee 8.04.1 on me EEEPC ASUS 1000, then did the KDE update

Troubleshooting:: I placed the USB drive in the windows computer and hit "safely remove hardware", rebooted, restarted. Tried it on another linux computer (Fedora). Then tried random things from random post here. This all happens when I plug the USB drive in. HERES WHAT I HAVE

Error Message: Unable to mount volume, Must be superuser to mount volume

[B]Sudo fdisk -l 
Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x13fc8d48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3936     1007600    6  FAT16[/B]


TO the best of my knowledge, i am the superuser since there are no other usernames. I just dont wanna change any other things and mess things up, I appreciate the help

---

### Post by perlluver on 2008-09-29
> **Dik_Starbuck said:**
> I have been searching thru this site for a solution. Ive tried other threads but couldnt get it to work for myself. Trying different things here and there and I thought i'd finally just ask.

So I had no trouble connecting a USB drive before, then I wanted KATE so I installed KDE, now it say Kubuntu instead of Kubuntu. Now I cant seem to access my USB drive. I know it should work because I installed Unbuntu from the USB drive, but haven't really had it work since. i installed Ubuntu Eee 8.04.1 on me EEEPC ASUS 1000, then did the KDE update

Troubleshooting:: I placed the USB drive in the windows computer and hit "safely remove hardware", rebooted, restarted. Tried it on another linux computer (Fedora). Then tried random things from random post here. This all happens when I plug the USB drive in. HERES WHAT I HAVE

Error Message: Unable to mount volume, Must be superuser to mount volume

[B]Sudo fdisk -l 
Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x13fc8d48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3936     1007600    6  FAT16[/B]


TO the best of my knowledge, i am the superuser since there are no other usernames. I just dont wanna change any other things and mess things up, I appreciate the help

You could add it to /etc/fstab:  It will mount automatically:  ```
sudo mkdir -p /media/disk
```
then ```
sudo chown username /media/disk
```
then add it to fstab: ```
kdesu kate /etc/fstab
```
add this line: ```
/dev/sdc1 /media/disk fat16 defaults 0 0
```
If that doesn't work let us know.

---

### Post by gnuvistawouldbecool on 2008-09-29
To me, it sounds like a similar problem I had in Mandriva a few weeks back.  For some reason when I rebooted with the USB stick in, it decided it was a proper hard drive and so added it to fstab.  As a result of this it appeared mounted on startup, but wouldn't let me unmount it, and if I did remove it and then put it back in either being in already or after starting up without it in.

In any case, open fstab up as a superuser eg sudo kate fstab (if in that directory) and edit out the line, or to be on the safe side just comment it out with # (i think it's that in fstab).

It should then work.

This is how my fstab looks (/ partition, /home partition, /mnt/windows XP partition, swap partition):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=6d9fe9be-8926-4cc8-bb1c-640e0723c352 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=ee7b6048-c012-4523-9151-1e4d95d70c1e /home           ext3    relatime        0       2
# /dev/sda1
UUID=A4A45DD2A45DA796 /mnt/windows    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=c1f8dd62-85d6-460e-a53d-5cbf40acd3ae none            swap    sw              0       0
```

---

### Post by Dik_Starbuck on 2008-09-29
> **perlluver said:**
> You could add it to /etc/fstab:  It will mount automatically:  ```
sudo mkdir -p /media/disk
```
then ```
sudo chown username /media/disk
```
then add it to fstab: ```
kdesu kate /etc/fstab
```


thanks for response.... i got up to this step and it says

```
:~$ kdesu kate /etc/fstab
kbuildsycoca running...
Reusing existing ksycoca
passprompt

sudo: kate: command not found

Launched ok, pid = 12193
:~$ kdesu kate /etc/fstab
sudo: kate: command not found

:~$ ICE default IO error handler doing an exit(), pid = 12190, errno = 11

:~$ kdesu kate /etc/fstab
kbuildsycoca running...
sudo: kate: command not found


```

SO from there i just opened KATE thru my favorites and i opened up fstab and when i tried to edit it it says

[B]The document could not be saved, as it was not possible to write to /etc/fstab.

Check that you have write access to this file or that enough disk space is available[/B]

do i need to change my user status? i thought i would be the admin\superuser

---

### Post by perlluver on 2008-09-29
> **Dik_Starbuck said:**
> thanks for response.... i got up to this step and it says

```
:~$ kdesu kate /etc/fstab
kbuildsycoca running...
Reusing existing ksycoca
passprompt

sudo: kate: command not found

Launched ok, pid = 12193
:~$ kdesu kate /etc/fstab
sudo: kate: command not found

:~$ ICE default IO error handler doing an exit(), pid = 12190, errno = 11

:~$ kdesu kate /etc/fstab
kbuildsycoca running...
sudo: kate: command not found


```

SO from there i just opened KATE thru my favorites and i opened up fstab and when i tried to edit it it says

[B]The document could not be saved, as it was not possible to write to /etc/fstab.

Check that you have write access to this file or that enough disk space is available[/B]

do i need to change my user status? i thought i would be the admin\superuser

kdesudo will allow you to become temporary root, Linux does not run in root all the time.  That is unsafe.  So if kdesu didn't work try kdesudo.  If you fill like you can handle nano, then ```
sudo nano /etc/fstab
```

---

### Post by gnuvistawouldbecool on 2008-09-29
Alternatively, just open up a konqueror window with sudo from the command line.  I think then if you open a file, you have the super user privileges to modify it.

---

### Post by Dik_Starbuck on 2008-09-29
so i tried both of those solutions and im still receiving the same issue. No change

---

### Post by gnuvistawouldbecool on 2008-09-29
Can you post the fstab file here, so we can see if that is the issue or not?

---

### Post by Dik_Starbuck on 2008-09-29
> **gnuvistawouldbecool said:**
> Can you post the fstab file here, so we can see if that is the issue or not?

no problem.. this is the original

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c9e269db-58fa-4e43-9664-3be22e1de6fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=61437014-b6a3-4417-b42b-e922fa7355ed none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by Dik_Starbuck on 2008-09-29
Heres an update.. i used a neighboors flash drive (im in class right now) and his connected with no problem....

Ill try formatting it and see if it makes any difference

---

### Post by Dik_Starbuck on 2008-09-30
> **Dik_Starbuck said:**
> Heres an update.. i used a neighboors flash drive (im in class right now) and his connected with no problem....

Ill try formatting it and see if it makes any difference

update... same problem, no change

......... help

---

### Post by mc4man on 2008-10-01
As far as editing fstab
in 'normal' kubuntu you could do it this way. (never used the 'setup' you have
Open your file browser (dolphin ?) and navigate to /etc/fstab.
If your on the 2 click setup then just single click fstab (highlight) and then click on the "open as Root" icon, enter your password if asked, ect.

If your on the single click then mouse over fstab, it will appear in upper right box, and carefully move your cursor out without touching any other files.  Then the same. ...

Edit: if you have fstab at the top or bottom of the browser box it's easy to exit the cursor without touching another file

---

### Post by Dik_Starbuck on 2008-10-03
IT FINALLY WORKS..
So i just edited the fstab and edited out the CD rom which had the same name as the external... it works
thanks for everyones help

---

### Post by jmiller87 on 2008-10-06
I am new to ubuntu as of yesterday and I am very confused on everything. I am trying to use an external hard drive simply for storage of my stuff. and when I try an use it I get the message of 
Unable to mount volume.
When I click to see the details it says:
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (Usually /)

If anyone can help me I would greatly appreciate it.

---

### Post by drowner on 2008-10-06
> **jmiller87 said:**
> I am new to ubuntu as of yesterday and I am very confused on everything. I am trying to use an external hard drive simply for storage of my stuff. and when I try an use it I get the message of 
Unable to mount volume.
When I click to see the details it says:
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (Usually /)

If anyone can help me I would greatly appreciate it.
 
Howdy

Bit more info:

Did you just plug it in? (Or did you try mounting it with a command or by editing a file (like fstab))?

Does the external drive have a name, and if so, what is it?

---

### Post by jmiller87 on 2008-10-06
The dirve is named "mybook" that is what it called its self when I pluged it in.

My friend was helping me set it up so I could access the files over my home network and I was just following what he said over the phone and I think I went to the wrong area cuz I change something in the properties and I think that is what went wrong cuz after that it gave me that unable to mount volume message.

I am a way newbee so I'm not sure what my friend was having me do, not to sure if he knew either.

---

### Post by Joeb454 on 2008-10-06
What file system is the drive formatted as?

---

### Post by jmiller87 on 2008-10-06
Not really sure but I think its NTFS or something like that?? 
How would I find out for sure????
I still have and use my windows laptop and the hard drive was used on that first and still works with the laptop.

---

### Post by drs305 on 2008-10-06
jmiller87,

Welcome to the ubuntu forums. We will be happy to help you resolve your problems. It would be better to start a new thread for a couple of reasons. 

Generally, it is better not to present a new problem in a current thread. Even though the original poster's problem seems resolved and yours is semi-related, leave this thread to him/her.

Secondly, when helpers are looking for people to help, when they see a thread with a lot of posts they are less likely to look at it than if there are no or few posts.

If you will start a new post I will be on the lookout for it. When you open it, present your problem and the results of these commands. Thanks:

```
sudo blkid
sudo fdisk -l
cat /etc/fstab
```

Note: in "sudo fdisk -l" it's a small L.

If you know the name of the mountpoint (folder name) you would like, tell us that also.

---

