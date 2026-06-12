---
title: "[SOLVED] external hdd problems"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Truant_84 on 2008-08-24
So, I'm unable to mount my external hard drive and am given the message "mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /). Advice would be greatly appreciated.

---

### Post by halitech on 2008-08-24
can you post the output of
```
sudo fdisk -l
```
thats a lower case L not the number 1 in case you are typing it in

---

### Post by cariboo on 2008-08-24
When mounting a hard drive from the command line, it will not mount on a mount point with a space in the name, For mount points you should use and underscore, instead of a space.

Jim

---

### Post by Truant_84 on 2008-08-24
here you go! 

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3cd93cd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4905    39399381   83  Linux
/dev/sda2            4906        4998      747022+   5  Extended
/dev/sda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    c  W95 FAT32 (LBA)
zach@Zach:~$

---

### Post by Truant_84 on 2008-08-25
bump

---

### Post by halitech on 2008-08-25
when you plug the drive in, do you not get an icon on your desktop?

---

### Post by Truant_84 on 2008-08-25
No icon on the desktop. So I realized that what happened was that I changed the name of the mounting point in the hard drives settings, thinking that I was just changing the name of the hard-drive, now that the hard drive won't mount, I can't change the settings back to the original mounting point.

---

### Post by halitech on 2008-08-25
run this in the terminal
```
gksu gedit /etc/fstab
```
and see if the drive is listed there

---

### Post by Truant_84 on 2008-08-25
this is what I get 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fdca023e-13a1-4b12-9541-91e6c909eabd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=af5125fd-99e6-451c-a654-8e338f416bd4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by halitech on 2008-08-25
darn, was hoping it was there

how did you rename the drive and where did you do it?

have you tryied unplugging it, restarting and plugging it back in?

---

### Post by Truant_84 on 2008-08-25
What I did was change the mounting point from media/My Book to media/external. I have tried restarting the hdd. I changed the mounting point through Places-Computer-properties of My Book. The Harddrive still shows up in Places-Computer, only now the option to change name, mounting point, etc doesn't show up under properties (I assume because the drive isn't mounted)

---

### Post by halitech on 2008-08-25
did you do that through Nautilus or command line?

---

### Post by Truant_84 on 2008-08-25
Just throught the properties menu when I right clicked the hard drive icon under 'computer.' That's nautilus I take it? (i don't have all the linux vernacular down yet)

---

### Post by halitech on 2008-08-25
ok, if you right click on the drive, do you have a mount option?

---

### Post by Truant_84 on 2008-08-25
Yeah, i have 'mount volume,' when I click on that I get the error message I reported earlier in the thread.

---

### Post by halitech on 2008-08-25
okay, try this in the terminal

```
sudo mkdir media/external
```
and then try to mount it again

---

### Post by Truant_84 on 2008-08-25
mkdir: cannot create directory `media/external': No such file or directory

---

### Post by halitech on 2008-08-25
opps, sorry it should have been
```
sudo mkdir /media/external
```

---

### Post by Truant_84 on 2008-08-25
It's giving me the same error message still. I tried "sudo mkdir /media/My_Book" as well, just in case, no results with that either. Thanks for all the assistance, by the way. I don't know if this helps, but under it's properties, the location of the drive is listed as "computer:///"

---

### Post by Truant_84 on 2008-08-26
bump

---

### Post by halitech on 2008-08-26
this makes no sense at all

can you browse to the root folder and see if you have a media folder?

---

### Post by Truant_84 on 2008-08-26
Okay, so I went computer-file system-root. There's nothing listed in the root folder. Although there is a "media" folder listed under "file system" which contains both a folder marked "external" and "My_Book"

---

### Post by Truant_84 on 2008-08-26
Would reformatting the hard drive on a different computer possibly fix things? I only have a few gigs of music files that I could easily swap onto my main hdd if that would make things easier.

---

### Post by halitech on 2008-08-26
ok, thats where I meant, sorry if that wasn't clear

so your original mount point was /media/My Book?

I wonder if we can open Nautilus as root and rename the /media/My_Book to /media/My Book

---

### Post by Truant_84 on 2008-08-26
How would one go about doing this?

---

### Post by halitech on 2008-08-26
from the terminal type in 
```
gksu nautilus
```it will ask you for the password and then open you in /root

---

### Post by Truant_84 on 2008-08-26
okay, done. It opened "root-file browser" but also gave me a warning in terminal 

** (nautilus:6773): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

---

### Post by halitech on 2008-08-26
nothing to worry about, does that to me as well

---

### Post by Truant_84 on 2008-08-26
cool. What's my next step?

---

### Post by halitech on 2008-08-26
browse to /media and right click the My_Book folder and select rename and rename it to My Book and cross your fingers when you try to mount your external drive

---

### Post by Truant_84 on 2008-08-26
hmmmm, in this new root media folder, in addition to "external" and "My Book" there is also "My Book" which contains all of the files on my hard drive. whats the command I want to use to try and mount this?

---

### Post by Truant_84 on 2008-08-26
Wait, upon further inspection, the drive is mounted!

---

### Post by Truant_84 on 2008-08-26
Could you possibly give me a brief explanation as to how the root command in terminal fixed things?

---

### Post by Truant_84 on 2008-08-26
Damnit! I spoke too soon, when trying to open the hdd, i'm told that I don't have permission to browse the files within. Also, after unmounting the drive, i have to go back through "gksu nautilus" for it to remount

---

### Post by dingansich on 2008-08-26
I think because you manually created the mount point as root you're going to have to change the permissions on it so that nonroot users can access and use it.  If you type 'ls -l /media' into the terminal it should list the contents with the owner/permissions.  My external drive is listed as owned by root, but with the permissions drwxr-xr-x.  You can set the permissions using the chmod command (as root in this case), but I can't recall offhand what the exact command would be.  Check the man pages if you need to go this route.

---

### Post by halitech on 2008-08-26
> **Truant_84 said:**
> Could you possibly give me a brief explanation as to how the root command in terminal fixed things?

I think it was more the renaming of the folder that fixed things back almost to the way they were. Now we need to set permissions on it so you can read and write to it. We can either go back to Nautilus as root, right click and change permissions or there is a command chown that we can use

```
sudo chown -R yourusername:yourgroup /media/My Book
```
change yourusername and yourgroup to what it is for you

you can also change ownership
```
sudo chown -R yourusername /media/My Book
```

---

### Post by Truant_84 on 2008-08-26
Everything is working fine again! Thanks so much for all the help!

---

### Post by halitech on 2008-08-26
glad we got it working for you :)

now, what did we learn today class about making changes? ;)

---

### Post by Marty_McFly on 2008-09-03
I had exactly the same problem, foolishly i had tried to change the mount point in the right click --> properties of my external hdd. I found the easiest way to get back to the settings was to use gconf 
If you go to the storage tab you can edit the preferences for your external drive. Basically remove the mount point line and whatever else you might have changed and the drive should work sweet as again.

Cheers :)

---

