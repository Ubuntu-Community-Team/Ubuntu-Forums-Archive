---
title: "Auto mounting windows partition on startup"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by h2c4life on 2008-08-25
Hi
I was wondering how you auto mount the windows partition on startup, so I could avoid the hassle of mounting the partition every time I need to access windows xp files.
Thanks!

Im on Ubuntu Hardy.

---

### Post by indytim on 2008-08-25
1.  Create a new directory in your /media folder (I called mine "F-Drive").
2.  Modify your etc/fstab file (make backup first).  Add a line similar to the following:
```

# /dev/sdb1
/dev/sdba /media/F-Drive  ntfs    defaults,umask=007,gid=46 0       1

```
3.  RE-boot.

Note : substitute the "sdb1" above for your windows partition identifier.

IndyTim

---

### Post by indytim on 2008-08-25
Correction, the substitution should be /dev/sdb1

---

### Post by h2c4life on 2008-08-25
thanks tim
but it wont let me create a folder in the media foler
create a folder option is greyed out for me.
am i doing something wrong?

i have a feeling im suppose to be using the terminal to do that...but im not sure what to write for it...
i just installed ubuntu few days ago and im still unsure about a lot of things

thanks in advanced

edit:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
i found this guide on how to do it. ill try it and let you know how it goes. thanks

---

### Post by MattBD on 2008-08-25
There's a very handy utility for doing this called Storage Device Manager. Just install the pysdm package with the following command:
```
sudo apt-get install pysdm
```
You should easily be able to use it to set your Windows partition to mount automatically in future.

---

### Post by Scunge on 2008-08-25
> **h2c4life said:**
> but it wont let me create a folder in the media foler
create a folder option is greyed out for me.
am i doing something wrong?

i have a feeling im suppose to be using the terminal to do that...but im not sure what to write for it...
Type, in a terminal window, ```
sudo mkdir /media/F-Drive
```

The addition of "sudo" at the start of the command runs the command as the all-powerful user "root", which is why you'll need to enter the admin password (i.e. your password, as the installing user) before it will do it.

As a side note, and people have differing opinions on this, I wouldn't create the folder in /media. I have a backup program and so that I don't backup CDs or USB drives or such, I get it to exclude "/media". But I do want it to back up my Windows dual-boot drives. It's much easier to put the Windows mount points somewhere else than to say "exclude /media except for ...".

If this were me, in this situation, I would be creating a /Windows directory, and have /Windows/F-Drive within that:```
sudo mkdir /Windows
sudo mkdir /Windows/F-Drive
```
Then the /etc/fstab entry would read ```
/dev/sdb1 /Windows/F-Drive  ntfs    defaults,umask=007,gid=46 0       1
```with "sdb1" replaced as appropriate.

Up to you, though.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by h2c4life on 2008-08-26
I have a problem now...after following the direction from that link([https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)), the partition is read only now...
I was wondering how to make it so it could be both writable and readable.
thanks

what i did was 
cd
wget [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)
sudo bash diskmounter
rm diskmounter

my fstab now reads

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=fa8d73d8-db0f-439e-b352-e7dd21ef1d81 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4b2e1721-1b5d-4def-a3ec-c6acd8d69c52 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0111,dmask=0000 0 0


and .hal-mtab in /media/ is blank


also, i cant unmount it disk by right clicking on it and selecting the option to do so

---

### Post by Scunge on 2008-08-26
For the read-write bit, see if [**[color=blue]this guide[/color]**](http://ubuntuforums.org/showthread.php?t=217009) helps you. Perhaps read through it all first, though?
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by Joeb454 on 2008-08-26
> **h2c4life said:**
> Hi
I was wondering how you auto mount the windows partition on startup, so I could avoid the hassle of mounting the partition every time I need to access windows xp files.
Thanks!

Im on Ubuntu Hardy.

Please see the link in my sig "HowTo: Automount NTFS Drives"

This is how I auto-mounted my Windows partition

---

### Post by h2c4life on 2008-08-26
Thanks to everyone for helping!
Joeb, your tutorial was really helpful!

---

### Post by tumutanzi on 2011-03-09
> **h2c4life said:**
> Hi
I was wondering how you auto mount the windows partition on startup, so I could avoid the hassle of mounting the partition every time I need to access windows xp files.
Thanks!

Im on Ubuntu Hardy.
It is very easy, just a few steps, please see the webpage below:
[http://www.tumutanzi.com/2011/03/hwo-to-automatically-mount-windows.html](http://www.tumutanzi.com/2011/03/hwo-to-automatically-mount-windows.html)

---

