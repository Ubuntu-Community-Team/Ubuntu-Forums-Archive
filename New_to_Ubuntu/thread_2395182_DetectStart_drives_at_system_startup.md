---
title: "Detect/Start drives at system startup"
date: 2018-06-27
forum: New to Ubuntu
---

### Post by jjfx on 2018-06-27
Hi, 

I noticed that when after I reboot and then I run some program and load a file from "Open Recent Files" (most programs has that) my path cannot be found. 

At first I thought that I mounted my disc some weird way. But I noticed that once I go to Files using GNOME. So pressing a tab on a dash, and manually going to my disk solves the issue. Then I can use "Open Recent Files".

So I think that after system startup my drives are not mounted yet, thats why I cannot load files. 

So how can I make Ubuntu to mount disks right after system reboot?

---

### Post by QIII on 2018-06-27
Hello!

I would recommend reading [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

That won't answer all of your questions, but it will give you an idea of the right ones to ask.  Then come on back and we'll help you figure it all out.

---

### Post by jjfx on 2018-06-27
Thanks for that link. Ok so I run this right after reboot

```
sudo blkid
```

and there are two partitions that interest me:

```
/dev/sdb: LABEL="temp_ssd" UUID="4bfa68c9-aa29-439f-a4ce-3ad0c4fabc3e" TYPE="ext4"
/dev/sdc: LABEL="big_0" UUID="43d55ebe-6caa-48ac-90e4-f6699e1f8d2e" TYPE="ext4"
```

Now when I run my program, which is HoudiniFX, I try to load a file from "Open Recent Files". The recent file shows me:

```

Load failed for /media/jjfx/temp_ssd/...rest..of..the..path..here
No such file or directory

```

So now I run terminal and want to access /media/jjfx/temp_ssd path, but cannot. so I do 

```

cd /media/jjfx
ll

total 8
drwxr-x---+ 2 root root 4096 Jun 27 21:07 ./
drwxr-xr-x  3 root root 4096 Jun 11 19:26 ../

```

There is no "temp_ssd"

So now through GNOME (this is what I understand GNOME is at least), I manually go to "Files" on a dash. Which brings up file browser. I go to "Other Locations" and then my "temp_ssd" drive.

And voila! Now I can open files with "Open Recent Files" in Houdini as well when I run this now:

```

cd /media/jjfx
ll

total 12
drwxr-x---+ 3 root root 4096 Jun 27 21:11 ./
drwxr-xr-x  3 root root 4096 Jun 11 19:26 ../
drwx------  5 jjfx jjfx 4096 Jun 19 22:36 temp_ssd/

```

Im new to Linux so I hope that those steps might help you understand my problem now

---

### Post by Bashing-om on 2018-06-27
jjfx; Hello -

Lemme chime in here with a bit of direction in thought -

The GUI mounts file systems via gvfs where in your use case you want them mounted for the terminal/CLI .
You may either manually mount the targets as on-demand ..or set up the mount in fstab to be mounted at startup automagically .

as the instance of on-demand where the file system is also available via the GUI - make a mount point in /media/
```

sudo mkdir /media/jjfx/temp_ssd
sudo mount /dev/sdb1 /media/jjfx/temp_ssd
sudo chown jjfx:jjfx /media/jjfx/temp_ssd/<some_directory>

```
where I am "assuming" there are partitions and in these partitions are some_directories on the sdb device :)
Might be good to see what you are in fact working with:
post back:
```

sudo parted -l

```

else if you want the GUI excluded - make the mount point somewhere else; traditionally on /mnt .
 

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by jjfx on 2018-07-03
@Bashing-om Thank you for the reply. Sorry for beeing so late in response but was pretty busy at work and only now I have time to finally setup mu Ubuntu the way I want, just started vacations :)

So this is what Im getting with "sudo parted -l"

[HTML]Model: ATA CT250MX500SSD1 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1305MB  768MB  ext4
 3      1305MB  250GB   249GB


Model: ATA CT1000MX500SSD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ext4


Model: ATA ST3000DM008-2DM1 (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  3001GB  3001GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 1023MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1023MB  1023MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 248GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  248GB  248GB  ext4


Error: /dev/mapper/sdb3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/sdb3_crypt: 249GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 
[/HTML]

/dev/sda (250GB) - system
/dev/sdb (1000GB)- ssd drive for my temp work
/dev/sdc (3000GB)- hdd drive to store projects.

And thats all the partitions I want. Dont need to split the drives more

I alreaady mounted those drives. And I remember using some tool for that (this was some kind of creator or sth). I dint create any partitions except for those required by the system to mount the drives.

---

### Post by Bashing-om on 2018-07-03
jjfx; Yuk on me -

As I have no experience with "/dev/mapper/ubuntu--vg-swap" thus can not be of much help.
However:
> 
Error: /dev/mapper/sdb3_crypt

is a valid warning as per the parted -l output ... sdb3 in fact does not exist. I do not know also how to deal with unpartitioned drives, LVM, or encryption. Never had the need to go there, never done that.
> 
Bashing-om:
where I am "assuming" there are partitions and in these partitions are some_directories on the sdb device


[INDENT][INDENT]a know it all I am not
[/INDENT][/INDENT]

---

