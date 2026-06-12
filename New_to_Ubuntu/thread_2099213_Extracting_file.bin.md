---
title: "Extracting file.bin?"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by fairbird on 2012-12-28
Hi all...
I want to ask there is way to extract any file.bin as i have it "rootfs.bin" this file for vu+ receiver (linux) ? 
It is deferent about file.nfi ..
So any chance to extract it?

Thank you advance

---

### Post by fairbird on 2012-12-29
80 Views and no answer :o

---

### Post by steeldriver on 2012-12-29
File extensions mostly don't have the same meanings on Linux/Unix as they do on Windows - so unless we know exactly what this "rootfs.bin" file is or where you got it, it's hard to advise you

Take a step back and tell us exactly what you are trying to do

---

### Post by fairbird on 2012-12-29
As i mentioned this file build on Linux environment...this file for vu+ receiver as like dreambox both boxes work with linux image, It is linux extension not win.
Thank you

---

### Post by gnush on 2012-12-29
It's a bit annoying to mount bin files, because you'll have to convert it to iso first.

```
# apt-get install bchunk
$ bchunk image.bin image.iso
$ mount -o loop -t iso9660 image.iso ~/dir/image
```When that's done, all you need to do is cd into *~/dir/image* (replace *~/dir/image* with whatever directory you want).

```
$ cd ~/dir/image
$ ls -al
```

---

### Post by fairbird on 2013-01-03
> **gnush said:**
> It's a bit annoying to mount bin files, because you'll have to convert it to iso first.

```
# apt-get install bchunk
$ bchunk image.bin image.iso
$ mount -o loop -t iso9660 image.iso ~/dir/image
```When that's done, all you need to do is cd into *~/dir/image* (replace *~/dir/image* with whatever directory you want).

```
$ cd ~/dir/image
$ ls -al
```

Thank you..and sorry for being late
I will try it and give you my result ):P

---

### Post by fairbird on 2013-01-03
I got this lines ...what option should be put it with that command?
By the way i'm using ubuntu 10.04
Thank you advance :D

[IMG]http://www14.0zz0.com/2013/01/04/01/126855366.png[/IMG]

---

### Post by fairbird on 2013-01-04
up...

---

### Post by windscape on 2013-01-04
Hi,

Perhaps that is not a CD image that bchunk can handle at all. Please post the output of the command ```
file rootfs.bin
``` That will hopefully tell us exactly what type of file rootfs.bin is.

---

### Post by remarks999 on 2013-01-04
Have you tried....

bchunk IMAGE.bin IMAGE.cue IMAGE.iso

That's assuming you have the cue file available.

---

### Post by fairbird on 2013-01-04
> **windscape said:**
> Hi,

Perhaps that is not a CD image that bchunk can handle at all. Please  post the output of the command ```
file rootfs.bin
``` That will  hopefully tell us exactly what type of file rootfs.bin is.
Thak you ..here is output 
```
root@fairbird:/home/raed# file rootfs.bin
rootfs.bin: HIT archive data
root@fairbird:/home/raed# 

```


> **remarks999 said:**
> Have you tried....

bchunk IMAGE.bin IMAGE.cue IMAGE.iso

That's assuming you have the cue file available.

Thank you...
```
root@fairbird:/home/raed# bchunk rootfs.bin root.cue root.iso
binchunker for Unix, version 1.2.0 by Heikki Hannikainen <hessu@hes.iki.fi>
    Created with the kind help of Bob Marietta <marietrg@SLU.EDU>,
    partly based on his Pascal (Delphi) implementation.
    Support for MODE2/2352 ISO tracks thanks to input from
    Godmar Back <gback@cs.utah.edu>, Colas Nahaboo <Colas@Nahaboo.com>
    and Matthew Green <mrg@eterna.com.au>.
    Released under the GNU GPL, version 2 or later (at your option).

Could not open CUE root.cue: No such file or directory
root@fairbird:/home/raed#
```

---

### Post by gnush on 2013-01-04
Create a file called rootfs.cue.

```
$ touch rootfs.cue
```Insert the following text into the cue-file, as shown with cat. Just paste in the text after entering cat, then hit enter.

```
$ cat >> rootfs.cue
FILE "rootfs.bin" BINARY
TRACK 01 MODE1/2352
INDEX 01 00:00:00
```Now create the iso-file and extract it.

```
$ bchunk rootfs.bin rootfs.cue rootfs.iso
$ mount -o loop -t iso9660 rootfs.iso ~/dir/image
```

---

### Post by fairbird on 2013-01-04
Thank you "gnush"
I have got those lines...

[IMG]http://www10.0zz0.com/2013/01/04/20/625792790.gif[/IMG]

---

### Post by gnush on 2013-01-04
Try this instead then.

```
sudo mount -o loop example.iso ~/image
```

---

### Post by fairbird on 2013-01-04
Thank you again..

```
raed@fairbird:~$ sudo mount -o loop rootfs.iso01.iso /home/raed/image
mount: you must specify the filesystem type
raed@fairbird:~$ sudo mount -o loop -t rootfs.iso01.iso ~/image
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
raed@fairbird:~$ 
```

---

### Post by gnush on 2013-01-04
```
sudo mount -o loop rootfs.iso01.iso ~/image
```
Skip the **-t**.

---

### Post by fairbird on 2013-01-05
Already i did it with out -t as before shown lines ..
```
raed@fairbird:~$ sudo mount -o loop rootfs.iso01.iso ~/image
mount: you must specify the filesystem type
raed@fairbird:~$ 
```

---

### Post by fairbird on 2013-01-05
up...:)

---

### Post by fairbird on 2013-01-05
Any advice [gnush]("http://ubuntuforums.org/member.php?u=1150977") ?

---

### Post by fairbird on 2013-01-06
up....

---

### Post by fairbird on 2013-01-07
So ...No advice .. :(

---

