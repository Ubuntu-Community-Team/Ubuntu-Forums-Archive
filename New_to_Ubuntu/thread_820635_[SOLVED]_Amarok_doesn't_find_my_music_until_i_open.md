---
title: "[SOLVED] Amarok doesn't find my music until i open the music folder. HELP!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by jimmysheldon on 2008-06-06
Hi,

I'm fairly new to ubuntu and so this is probably something that is easily sorted out. My situation is this, i have two hard drives, windows on one and hardy on the other. All my music is on the drive i have windows installed on and so i've added my music folder to my amarok library thing. But the problem is, amarok doesn't find any of the the music unless i open the drive. It seems to me that the hard drive hasn't been 'found' my ubuntu until i open it. So i'm not sure whats going on. Sorry if i haven't explained this very well.
I was wondering if there was a startup command to 'find' the hard drive, so that i don't have to manually open and close it every time i want to play my music on amarok.

Thanks for any help, jimmy.

---

### Post by sayakb on 2008-06-06
At a terminal:
```
gksudo gedit /etc/fstab
```And add this to the end of the file"
```
/dev/sda1 /media/win    ntfs-3g   defaults     0    0
```Replace /dev/sda1 with the one for you Windows drive. Check that by typing
```
sudo fdisk -l
```

EDIT: You need to reboot after adding the line.

---

### Post by wolfen69 on 2008-06-06
And add this to the end of the file
```
/dev/sda1 /media/win	ntfs ro,**noauto**,user	0	0
```

you would actually want to make it auto, not noauto.

---

### Post by Duck2006 on 2008-06-06
or

> /dev/sda1 /mount/point ntfs nls=utf8,umask=0222 0 0

Some info on mounting.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jimmysheldon on 2008-06-28
Thank you very much for your suggestions.

I got a little confused at what i actually needed to do. Should i have done all of those things? Or one or the other? I've tired a few of them, and in different combinations and it still isn't working. Infact it has actually got worse, when i try to open (mount?) the windows hard drive manually as i usually do, i now get an error message saying 'unable to mount volume'.

Can someone give me a straight forwards and complete guide to fixing this. Thank you.

---

### Post by mcduck on 2008-06-28
> **jimmysheldon said:**
> Thank you very much for your suggestions.

I got a little confused at what i actually needed to do. Should i have done all of those things? Or one or the other? I've tired a few of them, and in different combinations and it still isn't working. Infact it has actually got worse, when i try to open (mount?) the windows hard drive manually as i usually do, i now get an error message saying 'unable to mount volume'.

Can someone give me a straight forwards and complete guide to fixing this. Thank you.

Please run "sudo fdisk -l" and "blkid" & post the outputs here.

Nobody can give you exact line to put into fstab without knowing what is the correct device name for your Windows drive and what file system it's using..

---

### Post by jimmysheldon on 2008-06-29
okay for fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89ea89ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1ccf1cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris

and blkid

/dev/sda1: UUID="60B4784FB4782A24" TYPE="ntfs" 
/dev/sdb1: UUID="f7ddd873-646a-4291-9328-123f9f06316c" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="0417efff-ba2a-4eee-81fe-10c042f78819"

hope this helps. thanks for your patience with my ignorance :)

---

### Post by sayakb on 2008-06-29
Did you try adding any of the above lines to the /etc/fstab file?

---

### Post by jimmysheldon on 2008-06-30
which lines?

i followed the all the suggestions as best as i could, and none of them made any difference (after re-booting) so i removed them.

---

### Post by NikS on 2008-06-30
In simple words, its called MOUNTING a drive.
Drives that do not belong to linux filesystem!! or portable drive!!

The need to be mounted before u can use them,
every time, after boot when u open the drive, it is mounted n then the music is detected!!!
The drives that are mounted are added to /media/*drivename*.

What these commands do is they auto-mount the drive for you!!!
so u dont have to open the drive everytime u boot!!!
:)

---

### Post by Cadmus on 2008-06-30
I realise it's not so clear, so I'm going to try and explain what's happening here...

Ubuntu is aware of Windows partitions on your machine, but it doesn't mount them (that is, make them part of your running Ubuntu). It keeps them in 'standby' so to speak, and applications can't see the files on it (like your music).

When you open the drive by clicking on it you're asking Ubuntu to mount it, once that's done it stays mounted until you shut the machine down, this is why Amarok can then see it.

/etc/fstab is a file that tells Ubuntu about your hard disk partitions, where they are and what file system type they are. 

Each line says:[LIST=1]
[*]Where the drive is (almost always in /dev which is like a catalog of all the physical devices connected to your machine)
[*]Where you want it to be mounted (/media/win is where Ubuntu mounts your Windows drive when you mount it by clicking on it, so we may as well put it there)
[*]The filesystem type (NTFS is the file system Windows has used since Win2K
[*]A list of options (numerous, and it's different for each filesystem)
[*]The numbers at the end are about checking the file system, if you're adding a line yourself they'll almost always be '0 0'[/LIST]

Hope that's made things clearer and a bit less like magic incantations.

---

### Post by Elfy on 2008-06-30
Make a drive to mount it into

```
sudo mkdir /media/[COLOR="Red"]name[/COLOR]
```

change name to a name you like :) use the same name below as well

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

The file has been backed up and is now open for editing - add this to the bottom of the file, I got the options from psychocats site - they should be ok - but I don't have a ntfs partitoin to check against.

> #dev/sda1
UUID=60B4784FB4782A24 /media/[COLOR="Red"]name[/COLOR] ntfs nls=utf8,umask=0222 0

save and exit

check that it has mounted ok

```
sudo mount -a
df -h
```

If it has mounted it will show in the output for df -h

Now open amarok and navigate to /media/[COLOR="Red"]name[/COLOR] and enable it as your source

---

### Post by Cadmus on 2008-06-30
> **forestpixie said:**
> Make a drive to mount it into

```
sudo mkdir /media/[COLOR="Red"]name[/COLOR]
```

Do you need to make sure that the mount point exists before you stick it in fstab?

---

### Post by Elfy on 2008-06-30
Not necessarily - but if you don't make the mountpoint before you run mount -a it won't, so it has to be done before then.

I just do it in that order for my head :D

If you didn't run mount -a for instance, you would need to make sure you do it before you reboot - otherwise you would get errors on boot when it tried to mount to a non-existent mountpoint.

---

### Post by jimmysheldon on 2008-06-30
hi thanks forestpixie, i followed you're guide. unfortunately when i tried to check it mounted properly, the following happened:

jimmy@jimmy-desktop:~$ sudo mount -a
jimmy@jimmy-desktop:~$ df-h
bash: df-h: command not found

i'm guessing that means it didn't mount it?

---

### Post by Elfy on 2008-06-30
No not at all - if there was an error with the mount command it would have appeared before you ran the second one.

 > bash: df-h: command not foundUsually means what it says on the box, it can't find the command, syntax error or just getting it wrong -  I typed it wrong :D

try ```
 df -h
```

---

### Post by jimmysheldon on 2008-06-30
top notch. it seems to be working.

thank you very much

---

### Post by Elfy on 2008-06-30
You're welcome - can you mark thread as solved please, assuming that it is :)

---

### Post by jimmysheldon on 2008-06-30
haha just done it now. still adjusting to the forum etiquette.

---

