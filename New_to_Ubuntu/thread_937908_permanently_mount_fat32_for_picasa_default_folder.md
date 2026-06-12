---
title: "permanently mount fat32 for picasa default folder"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by reini5 on 2008-10-04
hi there, 

I am totally new to ubuntu and still getting used to terminal, sudo etc but like it generally a lot. Tried unsuccessfully to find a solution here for my problem which is:

I have an ubuntu partition, a winxp partition, and a fat32 partition for data (for both, ubuntu and winxp). I am using picasa as photo software and have defined a folder on the fat32 partition as default folder of pictures and also for downloads. This works well as long as I do not reboot the machine. A reboot deletes the folder settings in picasa. I have similar issues with other programs, so I am thinking that perhaps the fat32 partition is not being mounted after reboot? if this is the case, any solution to overcome this? Or what else could the problem be? (hate to say that in winxp this was fairly straight forward, but I quite like ubuntu and really wanna give it a shot)

thanks so much for help!:)

---

### Post by iansane on 2008-10-04
For any program that uses files on another partition or drive there needs to be an entry in /etc/fstab that mounts the drive to a certain folder every time.

To get the drive or partition info (ie. sda1, hda2 or whatever it is)
```

sudo fdisk -l

```

the important part you need is "/dev/sda?" The "?" being some number.

Then to make it permanent, make a directory (fat32Drive, or whatever you want to call it) in /media

```

sudo mkdir /media/fat32Drive

```

Then 

```

sudo gedit /etc/fstab

```

put in a line like this:

```

/dev/sda? /media/fat32Drive defaults 0 0

```

Remember "fat32Drive" is just a name I made up for the directory. Call it what you want. and "sda?" may be hda, or something else depending on your system. The "?" needs to be replaced with the right number from what you find with "sudo fdisk -l".

Reboot and it should auto mount the drive to that folder you made.

Then tell picassa where to go.

---

### Post by reini5 on 2008-10-04
thanks so much, iansane.

I am trying and followed successfully step 1 and 2. when I type in 'sudo gedit /etc/fstab' a new window opens and I get the below: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=cf5c2d1b-555f-4211-a4e5-0e271918b78a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e55c2c03-8e73-49bb-91ee-639d385027e7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


when I then type in the terminal '/dev/sda5 /media/fat32Drive defaults 0 0'  it tells me 'permission denied'. Anything I am doing wrong?

Thanks so much again,
reini5

---

### Post by iansane on 2008-10-04
don't type it in terminal. Add it as a new line to the fstab file and save it.

The new window is the gedit text editor and it's opened with sudo so you can save changes to it.

Go to the last line and hit enter a couple of times then type in that line. The "#" you see on some is a comment. Those lines aren't read by the system. They are for you. Here's one I have for my virtual machines on another drive.

```

#/dev/sda6 seperate virtual machines
/dev/sda6 /vm ext3 defaults 0 0

```

Notice how I put in the comment line in case I forget what it is for even thought the /vm mount point kinda gives it away.

---

### Post by iansane on 2008-10-04
OH my mistake. I also forgot the file system part.

Where my example has ext3 yours should have fat32

```

/dev/sda5 /media/fat32Drive fat32 defaults 0 0

``` 
sorry about that

---

