---
title: "I can only compile non-executable executables!!!"
date: 2006-02-13
forum: Programming Talk
---

### Post by orlox on 2006-02-13
Well, I posted about this some time ago when I was trying to generate executables from assembly using nasm or as, and I wasn't able to fix it. But I just realized that also the executables I compile with gcc are non-executables!!!!!(i.e. they don't have execution permissions for anyone (-rw-rw-rw-), and i haven't been able to modify the permissions, not even as root)...
Some weeks ago this problem was unexistant for me, and it appeared all of a sudden. Guess that a sure solution would be to simply reinstall my ubuntu but there must be some other way...

I'm pretty clueless about this, and any help would be aprecciated...

---

### Post by orlox on 2006-02-13
Just find a way to do it!!!!!

it just happened that i was trying to compile the files on a FAT32 partition i shared with windows. I simply compiled them on my ubuntu partition and that was it...anyway, why does the compiler creates non-executables on that partition remains a mistery for me...

(sorry for the self-aswered post)

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=orlox]Just find a way to do it!!!!!

it just happened that i was trying to compile the files on a FAT32 partition i shared with windows. I simply compiled them on my ubuntu partition and that was it...anyway, why does the compiler creates non-executables on that partition remains a mistery for me...

(sorry for the self-aswered post)[/QUOTE]
Maybe you have the partition mounted so that no files on it can be executable?

---

### Post by Lux Perpetua on 2006-02-13
> (sorry for the self-aswered post)Actually, thanks! If you hadn't posted the solution, we would be left wondering what the issue was. 

I can't explain the mystery, but you have certainly shed some light on it. Different filesystems have different file permission systems, so it's not surprising that the filesystem was at the root of the issue. I don't know the specific cause, though.

---

### Post by WakkiTabakki on 2006-02-13
[QUOTE=cwaldbieser]Maybe you have the partition mounted so that no files on it can be executable?[/QUOTE]

Yeah, check your [FONT="Courier New"]/etc/fstab[/FONT] to see if you've got [FONT="Courier New"]noexec [/FONT]as a parameter to the mount...


/N

---

### Post by orlox on 2006-02-13
Here's my fstab:

################################################

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/hda5 /media/hda5 vfat rw,user,fmask=0111,dmask=0000 0 0

###############################################

my FAT32 partiton is the /dev/hda5 that's mounted on /media/hda5. there's nothing about a "noexec", but I tried passing a working executable to the partition, and it inmediately lost the execution permissions, so i guess there's something wrong with it....

---

### Post by Sutekh on 2006-02-13
[QUOTE=orlox]Here's my fstab:
...
/dev/hda5 /media/hda5 vfat rw,user,**fmask=0111**,dmask=0000 0 0
...[/QUOTE]
When you mount the partition it starts with full permissions.  The flag **fmask** *removes* permissions for files.  

So using **fmask=0111** *removes* execute permissions for everyone.

Using **fmask=0000** gives full permissions to everyone.  Was there any reason you set fmask=0111?

---

### Post by orlox on 2006-02-13
I changed that fmask thing and restarted my computer. Now, the files do have execution permission, but when trying to execute them, I still get that permission denied message...Also, when initializing ubuntu, i saw that when mounting the partition, the system puts something about noexec, so i guess the partition isn't still  correctly configured to run executables...

(There was no reason for me to set fmask=0111. It's just that I used a diskmounter script that set all that automatically)

---

### Post by Sutekh on 2006-02-13
Okay well if you have no specific options you want enabled I'd use this fairly stock standard default for mounting FAT32
```
/dev/hda5 /media/hda5 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by orlox on 2006-02-13
Did that, and finally was able to execute things on the partition. However, the system startup took quite a while, and when mounting the partitions said something about "utf8 is not a recommended charset"...dunno now if it would be safe to modify files on the partition, and the increase in the system start-up time is really anoying... Even though, thanks for the advice, guess i'm getting closer to solving this.

---

### Post by wmcbrine on 2006-02-19
FAT32 has no file permissions at all, in the Unix sense. You can make everything executable, or nothing; those are the only choices.

For this and other reasons, FAT32 is not suitable for Linux software development.

---

