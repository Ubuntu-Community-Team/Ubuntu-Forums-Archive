---
title: "I have 2 problems but I don't know what they're called"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by utah23 on 2013-06-18
I installed Server a year ago.  Two directories are 'empty' when I open them but I can retrieve downloaded files in one of them if I know the exact path.  The second problem is, I can no longer SSH to this server even though I was able to do so about a month ago (I only checked on it about once a month for backups or when an outage occurs).  Security updates are automatic and others are done when I log into it.

I am in sort of a panic, please forgive me if I've forgotten the version name.  If there are technical terms to these things, I may be able to navigate on my own and wouldn't need to bother anyone.  Thank you for your time.

---

### Post by CatKiller on 2013-06-18
The first problem sounds like you have execute permissions on the directory (meaning you can open files inside it) but not read permissions (meaning you can't get a listing of the files inside it) or potentially that you don't have read permissions on the files inside. Or both.

Saying you can't SSH doesn't give us much to work on. Error messages? Anything?

---

### Post by cub on 2013-06-18
Where is the server located? Can you connect to the server but not login?

---

### Post by utah23 on 2013-06-19
Thank you, Catkiller, I'll start looking into how those permissions got changed and change them back.

The server is in the garage and I can connect to it but not login--does anyone have an old AGP vidcard by chance, hehe.  I simply used PuTTY before but am now getting "Network error: Software caused connection abort".

Thank you for helping.

---

### Post by cub on 2013-06-19
Ok, but there is a chance you might be able to troubleshoot the second problem of ssh by logging on directly on the server? Provided there is a way to get a videocard in and a monitor. :D

---

### Post by Scryer on 2013-06-19
Once when I was unable to ssh to my server it was because Verizon's signal had dropped and assigned assigned the router a new IP address after it had been stable for 6 months or so.  You might verify you're still trying to ssh to the right place.

---

### Post by nerdtron on 2013-06-20
ssh -v user@ipaddress

This will show you some info.

---

### Post by utah23 on 2013-06-22
Okay, after scrounging up an AGP card (my wife hates how my being a pack rat pays off sometimes).  I am finally able to see that my server's booting into Busybox.  That's bad news, isn't it?

---

### Post by cub on 2013-06-23
Nice going with the AGP card. :D Do you get any error messages as well when ending up in Busybox? As it sounds like an older computer it could be some of the hardware has broken.

---

### Post by utah23 on 2013-06-23
I'm trying not to panic (I'm thinking worst-case scenario and the hard drive failed).  However, the data I'm worried about is on a separate physical drive.  Can I simply plug it into another machine (a Windows machine) and retrieve it that way?  Or would those permissions can only be accessed through the server?

---

### Post by cub on 2013-06-24
If the drive is formated with FAT32 or NTFS that would work. Otherwise you can connect it to the same machine and boot from a Ubuntu Live cd and access the drives. Third option is to boot the server from a Live cd and run 'fsck' to check and repair the system drive (if it is faulty and causing the normal boot to stop).

---

### Post by utah23 on 2013-06-24
Cub, thank you for your help but after hooking up the drive to another machine, I'm getting the error message: "ls: reading directory .: Input/output error"  

I tried running fsck but the warning message is scary: "WARNING!!!  The filesystem is mounted.   If you continue you ***WILL*** cause ***SEVERE*** filesystem damage."

---

### Post by cub on 2013-06-24
Did the drive mount correctly (since fsck warns about the disk being mount it should be)? If you try to open the drive in the gui file manager like nautilus instead of running ls in a terminal, any difference? I read some old thread about that it needed to index the new drive and after leaving it for a while in the nautilus it read ok.

What's the output of running:
```
sudo parted /dev/sda 'print'
```
You might need to do similar for /dev/sdb as well since you probably have multiple hard drives in the machine.

And:
```
df -h
```

I think this [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/) give a good view of how to use the fsck command.

---

### Post by utah23 on 2013-06-24
sudo parted /dev/sdb1 'print':
```
Model: Unknown (unknown)
Disk /dev/sdb1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  500GB  500GB  ntfs

```
smartctl:
```
SMART overall-health self-assessment test result: PASSED

```

Using nautilus produced 2 empty directories (the same ones that prompted this thread) and I'll let it sit and (hopefully) index itself.  When I hooked it up to a Windows machine, the error message was: "file or directory corrupted and unreadable"

---

### Post by utah23 on 2013-06-27
Well, thank you to all that helped, specifically to **Catkiller** for getting the ball rolling and to **cub** for pointing me in the right direction.  I've learned that fcsk can't fix ntfs partitions (but most of you probably already knew that) and the final fix was letting Windows run chkdsk on the drive at bootup (not sure why it didn't do that the first time).  

I'll take the easy way out of the second one and reformat the server.  Ciao!

---

### Post by newb85 on 2013-06-27
Windows can't read all formats.  NTFS and FAT32 it can.  EXT# it can't.

---

