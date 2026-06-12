---
title: "[SOLVED] How to mount the windows partitions in suse ?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by bhadotia on 2008-06-20
I have recently installed suse 10.3. The problem is it is not mounting my windows drives by default.
That was not a problem in ubuntu. I don't exactly know how to edit the /etc/fstab to get the job done.
I've tried editting it mysrlf but without any luck. Here's how it looks like(after my trying to edit it):


```
/dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part7 /                    ext3       acl,user_xattr        1 1
part2 /media/E             ntfs       defaults
/dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part8 swap                 swap       defaults              0 0
/dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part2 /media/E  
ntfs                defaults          0 0
/dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part1 /media/C
ntfs defaults 0 0
/dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part5 /media/F
ntfs defaults 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
```

I will appreciate all help. Thanks in advance.

---

### Post by tjwoosta on 2008-06-20
[http://www.linuxquestions.org/questions/susenovell-60/mount-windows-drive-in-suse-10.1-494316/]("http://www.linuxquestions.org/questions/susenovell-60/mount-windows-drive-in-suse-10.1-494316/")


that should help, i hope   (next time you should probably try a forum that actually supports suse first)

---

### Post by bhadotia on 2008-06-20
Sorry I forgot to tell , this is what happens when I do 'sudo mount -a':


mount: special device part2 does not exist
mount: unknown filesystem type ''
mount: mount point defaults does not exist
mount: unknown filesystem type ''
mount: mount point defaults does not exist
mount: unknown filesystem type ''
mount: mount point defaults does not exist

---

### Post by Cypher on 2008-06-20
I presume your Windows partition is formatted in NTFS, so do you have the NTFS package installed in SuSE?

PS, you might get more detailed help in the SuSE forums..

---

### Post by bodhi.zazen on 2008-06-20
LOL, be nice.

You mount the in SUSE just like Ubuntu or any other distro.

mount <partition> <mount_point>

from your error messages, do the mount points exist ?

you need to su -> become root
mkdir /media/C /media/D /media/E

Then 

mount -a

If that fails, mount by device or uuid

---

### Post by bhadotia on 2008-06-20
THanks

---

### Post by N.N. on 2008-06-20
Can't help you with mounting NTFS partitions in SUSE, but it looks as if you messed up your /etc/fstab file when you edited it by unintentionally inserting line breaks in the lines that refer to your NTFS partitions.

The bits that say ```
ntfs                defaults          0 0
``` should be matched with the lines that describe the location of the device nodes (the parts that look like /dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part2) and their mount points (e.g., /media/E).

Thus, to exemplify, consider the part that currently looks as follows: ```
/dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part2 /media/E  
ntfs                defaults          0 0
```
This entry is split into two lines while, in order to conform with the syntax of the /etc/fstab file, it should only take up one line: ```
/dev/disk/by-id/scsi-SATA_WDC_WD800BEVS-6_WD-WXE607C89872-part2 /media/E                 ntfs                defaults              0 0
```

When you edit a file with an editor such as nano, automatic line breaking is often default behaviour. While such behaviour might be desirable for casual writing, it can cause problems when editing configuration files, as is evident from the output of mount: ```
mount: unknown filesystem type ''
mount: mount point defaults does not exist
mount: unknown filesystem type ''
mount: mount point defaults does not exist
mount: unknown filesystem type ''
mount: mount point defaults does not exist
```

Also, you should remove the following line (line 2) as it does not conform with the syntax of the file: ```
part2 /media/E             ntfs       defaults
``` This line causes the mount command to output the following error message: ```
mount: special device part2 does not exist
```

---

### Post by bhadotia on 2008-06-21
Thanks for the information.

---

### Post by bodhi.zazen on 2008-06-21
two most useful flags with nano ?  -Bw  nano -Bw /etc/fstab  -B == make backup of original file -w == disable wrap. keeps information from appearing to be 2 lines.

---

### Post by bhadotia on 2008-07-01
Bodhi that just went over my head (I did'nt get a word!)!:popcorn:
I have never used nano (or any CLI based editor)you see .
Any way , now that we are at it , what are flags (- I see this word a lots of time in linux)?

---

### Post by tjwoosta on 2008-07-01
haha..

what he said is..

the two most usefull flags for nano are -B and -w (-Bw)


the -B makes a backup of the original file for you

and the -w disables word wrap (makes it so when a line is too long to fit on the screen it wont wrap around to the next line, it will just make it so you can scroll left instead)

so for instance you can do 
```
nano -Bw filename
```
and this will open the file in nano as well as make a backup of the original and stop words from wrapping

---

### Post by bhadotia on 2008-07-01
:)
What I meant to ask was what basically are flags in general ? 
You just explained what those flags do in nano:).

---

### Post by tjwoosta on 2008-07-01
u mean like what are some of the usual flags?

..well they are different for every application


to find the flags for a certain command just do
```
man command
```
where command is your command

(this opens the man pages for the command, explaining how to use it and what the flags are)

---

### Post by bhadotia on 2008-07-01
You still did not get it:)
I mean: Are flags like options given while executing command or something else?
If they are options why not use this easy word instead of  flag:)

---

### Post by bodhi.zazen on 2008-07-01
> **bhadotia said:**
> You still did not get it:)
I mean: Are flags like options given while executing command or something else?

Yes flags are options

> If they are options why not use this easy word instead of  flag:)

Because it would confuse all the geeks if you started calling "flags" "options" :lolflag:

Just part of the terminology I guess. You could call them options ...

If there is anything posted here you do not understand, just ask ;)

---

### Post by bhadotia on 2008-07-01
I think I get it now .
You people are the best.:KS

---

