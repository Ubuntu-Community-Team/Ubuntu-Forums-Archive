---
title: "Data Recovery Help Needed"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by russ5811 on 2008-11-24
I recently followed a tutorial to put my Home on a different partition. (Here's the link to the tutorial: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) )

After I did this, I got numerous errors involving .dmrc and .ICEauthority. I tried to use recovery mode and the live CD to fix this and it did not work.

So, I now just want to reinstall Ubuntu 8.10, but I have a MAJOR problem. All the files in my Documents, Music, and Video folders are not accessible. I can see them, but when I try to copy them to an external hard drive, I get write errors because the files can't be read because I'm not the owner.

Please, can someone tell me what to do to recover these files either from the live CD environment or from the recovery mode command line. I have some irreplaceable files in there.

I can't believe I was this stupid!! PLEASE HELP Guys!

---

### Post by santy_kushwaha on 2008-11-24
first of all i wanted to know that when u created the partition did u choose the part of the HDD which had those files and and overwrite it or it was just and issue caused while u creating an fresh partion at different location

---

### Post by antmenj on 2008-11-24
My favorite way is to boot a puppy linux live CD.  If you can mount drives with the ubuntu live CD you may be able to use that.

OR

If your drive is less than half full you may be able to squash the partition with gparted then copy the first partition to the seconds and then delete the first one and reinstall then mount the second in your new install and copy across the stuff you want.

OR someone tells you how to fix what you did.

---

### Post by russ5811 on 2008-11-24
I followed the tutorial i linked to exactly. I created a new partition, copied my /home folder there, backed up the /home folder on the original partition, then went in with gedit and added some sort of command to the bottom of the page. I'm somewhat of a newbie at this so it may help to look at the link to see what i did. 

thank you for even trying to help!

---

### Post by russ5811 on 2008-11-24
i've tried the live cd. i can find the files, but I cannot access them or change their permissions in order to copy them. i've tried this from the original /home folder, the backup of the original /home folder, and from the new /home folder on the new partition.

---

### Post by russ5811 on 2008-11-24
see my reply below

---

### Post by santy_kushwaha on 2008-11-24
hey do u have a second computer at home.....if so then take out ur HDD and plugin it in as  a slave and try to get files out 

if not the only way to take them out is try to gain a root access and i have to test b4 telling u how to get root access in live CD or wait till some expert come and look ur post

---

### Post by russ5811 on 2008-11-24
i have a 2nd computer (which I'm on) but it's a laptop. what is the other way you speak of?

---

### Post by bumanie on 2008-11-24
You should be able to able to mount the file system with the files you want to retrieve as root and copy them to another partition/drive, via a live cd.
Do you know the name of the partition you wish to copy from and the name of the device you wish to send the files to? If so, please state which is which. You could also do dd commands to copy the whole partition to another device with a healthy filesystem on it - this can also be done with gparted, just ensure that the device you are sending the filesystem to is of equal or greater capacity than the partition you are copying. I prefer dd commands but that will only be useful if the 'target' device is larger than the one containing the files you want.

---

### Post by russ5811 on 2008-11-24
the original /home folder is on dev/sda1 and the copy is on dev/sda3 i have an external usb HDD that i would like to copy them on. dev/sda1 is about 250GB and dev/sda3 is 50GB. unfortunately, the external HDD is only 40GB

---

### Post by bumanie on 2008-11-24
OK, that means you are stuck trying to copy the files only. Which partition can you 'see' the files on? sda1 or sda3? I assume the external device will mount as sdb. Is this correct?

---

### Post by russ5811 on 2008-11-24
both. i can see the files on both partitions (dev/sda1 and dev/sda3)

---

### Post by bumanie on 2008-11-24
It's a while since I've done this myself - I think this is correct. Boot live cd, go to terminal > sudo -iwill give you a bash shell as root. > mkdir /mnt/recoveryThis makes a mount point to mount /dev/sda1's filesytem to > mount -t ext3 dev/sda1 /mnt/recoverymounts /dev/sda1 filesystem to /mnt/recovery > cd /mnt/recovery> ls -al you should be able to see the names of all the files on that partition. then > cp -R <filename> /dev/sdbI think this will work, assuming /dev/sdb is the name of your external drive, if not substitute the correct name. Good luck. Wait for confirmation from someone else if you like.

---

### Post by russ5811 on 2008-11-24
Here's what I did. Is something wrong? I did not see the filenames.

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir/mnt/recovery
-bash: mkdir/mnt/recovery: No such file or directory
root@ubuntu:~# mkdir /mnt/recovery
root@ubuntu:~# mount -t ext3 dev/sda1/mnt/recovery
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@ubuntu:~# cd /mnt/recovery
root@ubuntu:/mnt/recovery# ls -al
total 0
drwxr-xr-x 2 root root 40 2008-11-24 12:13 .
drwxr-xr-x 3 root root 60 2008-11-24 12:13 ..
root@ubuntu:/mnt/recovery#

---

### Post by 4leite on 2008-11-24
The message after the command  "mount -t ext3 dev/sda1/mnt/recovery" is because you need an extra space, the command should be:
```

mount -t ext3 dev/sda1 /mnt/recovery

```

However, I would caution against the use of "sudo -i". The prefered method is "sudo [command]" for each command. This less convenient, but there is less risk of performing commands as the super user unnecesarily. After you type "sudo -i" you should remember to type "exit" or otherwise close the terminal.

A few questions:
What version/flavour of Ubuntu are you running?
Could you boot the live cd, open a terminal, type:
```

mount | grep /dev/sd

```
and paste the output?

I suspect the drive will be mounted automatically either similar to:
/dev/sda3 /media/disk-2 

Replace <source> and <destination> with what you found above to copy your files.
```

sudo cp -R /media/<source> /media/<destination>

```

Don't forget the space between "/media/<source>" and "/media/<destination>"

---

### Post by ByteJuggler on 2008-11-25
Just another correction, the mount command should be:

```
mount -t ext3 /dev/sda1  /mnt/recovery
```

(Note the leading slash on the "dev/sda1" that's been added.  Without the leading "/" the mount command will assume the "dev" folder to be in the current folder, which is incorrect unless you're running the command from the "/" folder.)

---

### Post by handydan918 on 2008-11-25
You posted as your mkdir command:
```
mkdir/mnt/recovery
```

Whereas it needs to be 
```
mkdir /mnt/recovery
```

note the space between mkdir and /mnt/recovery.
This is sufficient to cause the errors you are getting.

---

