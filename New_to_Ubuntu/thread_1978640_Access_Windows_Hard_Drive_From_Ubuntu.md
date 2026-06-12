---
title: "Access Windows Hard Drive From Ubuntu"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by Tbuch on 2012-05-12
I am completely new to Linux/Ubuntu
I have a USB-harddive with all my back-up. But when I connect it to an  USB-port - nothing is happening?? (Its a NTFS formatted Drive)

I have been searching a lot to find answers. Now i understand that there is a tools called "Sudo" (I guess) 

This is a screen dump from "Disc Utility"

[IMG]http://s3.kkloud.com/gett/6to4LZH/Screenshot%20from%202012-05-12%2008%3A26%3A58.png.0x675.nsrhnvfqypjpp66rwvlck4lt9z281tt9.png[/IMG]

   I've tried with different Sudo commands like:[INDENT]sudo mount /dev/sdb2 /media
[/INDENT]Then I got the message: [INDENT][FONT=Courier New][SIZE=1]mount: you must specify the filesystem type[/SIZE][/FONT]
[/INDENT]and that's where I'm stuck - for now

---

### Post by cmont899 on 2012-05-12
try installing ntfs and loading the kernel module:
```
sudo apt-get install ntfs-3g
sudo modprobe ntfs
```

---

### Post by Tbuch on 2012-05-12
[SIZE=2]Thanks for trying to help

Something new happening
[/SIZE][INDENT][FONT=Courier New][SIZE=2]NTFS signature is missing.
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/SIZE][/FONT][SIZE=2]
[/SIZE][/INDENT][SIZE=2]What now?[/SIZE]

---

### Post by wilee-nilee on 2012-05-12
When was the last time you ran a chkdsk on that external drive, has to be run from windows.

---

### Post by Tbuch on 2012-05-12
Thats a long time ago - but I have no trouble to acces the USB-drive from Win XP

But I do a chkdsk

---

### Post by Tbuch on 2012-05-12
[SIZE=2]Okay this is no good (but I hope it's not a disaster)

Suddenly the partition is now showing in windows XP as a so-called "GTP Protective Partition"

Before I doing anything furter - I will be complete sure and safe that I am not going to loose my back-ups :shock:

So no more attempts (Fooling curiously naive around with the settings) on my part 
 I am (pleeeeease) awaiting qualified support[/SIZE]

---

### Post by wilee-nilee on 2012-05-12
> **Tbuch said:**
> [SIZE=2]Okay this is no good (but I hope it's not a disaster)

The partition is showing in windows XP as a so-called "GTP Protective Partition"

Before I doing anything furter - I will be complete sure and safe that I am not going to loose my back-ups :shock:

So no more attempts (Fooling curiously naive around with the settings) on my part 
 I am (pleeeeease) awaiting qualified support[/SIZE]

Good idea.

---

### Post by Tbuch on 2012-05-12
> **wilee-nilee said:**
> Good idea.

But do you have any "good ideas" to solve this?
(I am a little bit concerned)

---

### Post by wilee-nilee on 2012-05-12
> **Tbuch said:**
> But do you have any "good ideas" to solve this?
(I am a little bit concerned)

Probably a easy fix, not sure what that may be, may not even need a chkdsk. This is a slow time on the forum so if no one answers bump it during the day US time.

I would boot the computer with it plugged in as well to see if that gets it mounted. 

If you have added it to the fstab, comment that out with a # and reboot then plug it in to see if it mounts.

If you have made a entry to the fstab be sure to mention this on the thread.

---

### Post by Tbuch on 2012-05-12
> **wilee-nilee said:**
> 

If you have added it to the fstab, comment that out with a # and reboot then plug it in to see if it mounts.

If you have made a entry to the fstab be sure to mention this on the thread.

Thanks - but dont even know vhat fstab is - so I guess I have not added it to the fstab

---

### Post by wilee-nilee on 2012-05-12
> **Tbuch said:**
> Thanks - but dont even know vhat fstab is - so I guess I have not added it to the fstab

So if you go to home the HD is not showing in the left side panel?

---

### Post by Tbuch on 2012-05-12
No I cannot see the the device in my Home

---

### Post by Tbuch on 2012-05-12
Perhaps It would be a good idea to tell what was happening

Firstly, it was so blatantly stupid to sit working on my backup hard disk at. 3 am - you have to go to bed and not work with something like this when you are tired - especially not when you are in new territory that you not are accustomed to.

I know that I was in the "Disk Utility" and in here - not, that I totally remember it - I guess in an eagerness to get Ubuntu to know the disc  - I've changed the type to a "Linux Basic Data Partition "- as seen in this picture here

[IMG]http://s3.kkloud.com/gett/6to4LZH/Screenshot%20from%202012-05-12%2012%3A51%3A05.png.0x675.wiw7reg6md8fflxra2h1p54ncpfa8aor.png[/IMG]

I would be very happy to get some certainty about what this actually resulted in.
So if there is a friendly soul who has a good knowledge of the program "Disk Utility" that could tell me what happening when I changed the type: Did I made irreparable damage to the disk or have I just modified a "flag" and nothing had then been deleted??

 It would be incredibly nice and reassuring if I could just get certainty about where I stand

---

### Post by Tbuch on 2012-05-12
I also try to find a way to mount the drive by following some "googled" advises 
In the terminal Window I have done a least the following:

1:

[LIST]
[*]cd /mnt
[*]sudo mk.dir windrive (remove the dot between mk and dir – I had to  enter that here to get round a mod_security rule whilst creating this  post!)
[/LIST]
2:

[LIST]
[*]sudo apt-get install ntfs-config
[*]sudo ntfs-config
[/LIST]
I dont know if this helps

---

### Post by Tbuch on 2012-05-12
During all my trouble trying to mount the USB-Drive I tried sometimes to connect it to my Laptop Windows XP computer which have no problems to see the drive.

At some point after I had been trying a while with the "disk utility" and among other things, had written these commands in "Terminal Window":
[INDENT]sudo mount /dev/sdb2 /media
[/INDENT] got the message:
[INDENT]mount: you must specify the filesystem type
[/INDENT] After an advise here in this forum I also did this
[INDENT]sudo apt-get install ntfs-3g
sudo modprobe ntfs
[/INDENT] After this things Windows XP could not access the partition anymore ( it say it was a GPT protected Partition) and Windows 7 prompt me to formated thedrive and told it was a "RAW" partition
As told Linux cannot access it and regard the partition as a "Linux Basic Data Partiton" with nothing added for the "Usage" and the "flags"

Again see the screen-dump:

[IMG]http://s3.kkloud.com/gett/6to4LZH/Screenshot%20from%202012-05-12%2008%3A26%3A58.png.0x675.nsrhnvfqypjpp66rwvlck4lt9z281tt9.png[/IMG]

---

### Post by oldfred on 2012-05-12
Windows will not see any LInux formated partitions.

And Windows XP (I thought) could not work with gpt(GUID) partitioning, but Windows 7 will. gpt is the new partitioning system for very large drives and recommended for SSDs. MBR(msdos) is the 30 year old partitioning system used for hard drives since the PC started having hard drives. But if drive is less than 2.2TB you do not have to have gpt. 

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

RAW means the NTFS partition lost its partition boot sector or PBR. If it was formated before you may be able to recover the PBR as NTFS does keep a backup.

You should not have to install the ntfs driver as it is already installed in all new versions of Ubuntu (for years).

Download in Ubuntu or liveCD/USB and run this, just so we can see your entire configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

