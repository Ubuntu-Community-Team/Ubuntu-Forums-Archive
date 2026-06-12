---
title: "&quot;Cannot Mount Volume&quot;"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by raynedanser on 2008-05-06
I have an external drive that is, apparently, NTFS format and it won't read it. ALL my media is here (MP3 files, etc).

If I'm understanding the prompt correctly, I can type /dev/sdg2 / media/Chip ntfs-3g force 0 0  on the command line - but what command line? And will that allow me permanent access to the drive? 

I am a BRAND new user to Ubuntu, so whatever is said, please know it has to be dummied down a lot for me.

Thanks!

Den

---

### Post by tamoneya on 2008-05-06
```
/dev/sdg2 / media/Chip ntfs-3g force 0 0
```is supposed to be added to /etc/fstab.  This file controls what mounts when the system boots.  The way to do it otherwise is```
sudo mount -t ntfs /dev/sdg2 /media/Chip
```

---

### Post by raynedanser on 2008-05-06
> **tamoneya said:**
> . . . The way to do it otherwise is```
sudo mount -t ntfs /dev/sdg2 /media/Chip
```

But I don't even understand where to do THAT. Where do I key that in?

Also, does it matter if Chip is not left on all the time?

---

### Post by Gripp on 2008-05-06
welcome to linux :)

to get to your command line, go to applications>accessories>terminal

then you;ll get something that looks like DOS. 

"sudo" is the command that tells the computer that you want to make an administrative change to the system.  it will ask you for your password.  this is the same pass you used to log in. 

so any time you plan on making a change to the system, you need to put that in front of the command. 

as for the fstab, to get to that you need to type ```
sudo gedit /etc/fstab
``` 
this will open something like notepad.
now just copy that line that tamoneya gave you and the next time you reboot the drive should mount. 

there shouldn't be a space between the "/" and "media/..." in that line either, so fix that. 

but, rather than rebooting, run the second command that tamoneya gave you to see that the drive does mount. it will be located at /media/Chip.

if that doesn't work let us know.

edit:while i'm at it, if that doesn't work
try unplugging the drive, and run cat /proc/partitions
then try plugging it back in and running cat /proc/partitions again. see if anything changed. if it did change then that is the volume you should be mounting (hopefully, my external loads right up, so i'm only so-so that this is the location that it would show in...)

---

### Post by tamoneya on 2008-05-06
this should be typed into terminal (applications -> accessories -> terminal)
The drive does not need to be plugged in all the time but jsut remember to unmount it before you power it down```
sudo umount /dev/sdg2
``` Also make sure not to add it to fstab if it is not always going to be powered on.

---

### Post by kk0sse54 on 2008-05-06
Do you dual boot? Because for me improperly shutting down windows and then starting up Ubuntu causes Ubuntu not to be able to mount my external HD and windows partition, both of which are NTFS and forces me to reboot back into windows and properly shut it down.

---

### Post by raynedanser on 2008-05-06
C!oud - there is no dual booting as only Ubuntu is currently on my system.

tamoneya -  so would I have to do that other command every time I wanted to access that drive?

Gripp - Thank you.

I've done all this, NOW I'm being "told" that I'm not privileged to mount the volume "chip." 

So... progress, right? lol

(I'm the only user of this computer and only one profile has been set up, if that matters)

---

### Post by tamoneya on 2008-05-06
you can only access a drive if it is mounted.  You will have to run the mount command only if the drive is not already mounted.  The drive will unmount every time you restart and when you run umount manually.  I think the reason you are having a problem is because /media/Chip does not exist.```
sudo mkdir /media/Chip
```If that still doesnt fix it please post exactly what you typed and exactly what was outputted by terminal.  This should be done by copying.  This is done like normal except for the fact that the key short cut is ctrl-shift-c instead of ctrl-c.

---

### Post by kshtjsnghl on 2008-05-06
try to give us output for 

cat /etc/fstab
ls -l /media

type these commands on to the terminal and post the outputs here..

---

### Post by raynedanser on 2008-05-07
> **kshtjsnghl said:**
> try to give us output for 

cat /etc/fstab
ls -l /media

type these commands on to the terminal and post the outputs here..

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=51a08456-4646-4b92-9809-69b85a4bd2e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a061e5e2-7540-4c58-8bdf-290be58fb181 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by raynedanser on 2008-05-07
> **tamoneya said:**
> I think the reason you are having a problem is because /media/Chip does not exist

Nope, when I keyed that in, it said the drive already existed. 

Hm.

---

### Post by vanadium on 2008-05-07
I am afraid we are giving bad advice here that could break your system. You are having problems with an external drive, ntfs formatted, that does not mount. Usually, this is caused because the drive was not properly disconnected from Windows. It also happens when you hibernate Windows with the drive connected instead of shutting it off.

To resolve this issue, boot back into Windows. There, disconnect the drive using the icon to safely remove hardware. Alternatively, just shut down windows completely with the drive connected. The next time you boot into Linux, it will be auto-mounted and an icon will appear on the desktop. Remember also in Ubuntu to right-click the icon, then choose unmount before disconnecting tehd rive.

If that does not work, go again into Windows, but this time also check the disk using the Windows tools before shutting Windows down.

The point is that, to preserve the integrity of your data, ubuntu will refuse to auto-mount a drive that has not been properly closed.

---

### Post by raynedanser on 2008-05-07
> **vanadium said:**
> I am afraid we are giving bad advice here that could break your system. You are having problems with an external drive, ntfs formatted, that does not mount. Usually, this is caused because the drive was not properly disconnected from Windows. It also happens when you hibernate Windows with the drive connected instead of shutting it off.

To resolve this issue, boot back into Windows. There, disconnect the drive using the icon to safely remove hardware. Alternatively, just shut down windows completely with the drive connected. The next time you boot into Linux, it will be auto-mounted and an icon will appear on the desktop. Remember also in Ubuntu to right-click the icon, then choose unmount before disconnecting tehd rive.

If that does not work, go again into Windows, but this time also check the disk using the Windows tools before shutting Windows down.

The point is that, to preserve the integrity of your data, ubuntu will refuse to auto-mount a drive that has not been properly closed.

Yeah, I figured that out today when it DID break my system. ;-) No worries, I reinstalled Windows, unmounted the drive properly, reloaded Ubuntu and all is well that ends well. ;-)

Thanks muchly for the help.

---

