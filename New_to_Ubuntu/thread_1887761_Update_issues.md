---
title: "Update issues"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by Autumnie88 on 2011-11-27
Let me preface this post with, I have no clue what I'm doing!  I haven't even turned on this computer in months, possibly longer, so when I turned it on, I have 207 updates.  When I try to install the updates, it tells me this
"Not enough free disk space
The upgrade aborts now. The upgrade needs a total of 290M free space on disk '/'. Please free at least an additional 3527k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I ran the sudo apt-get clean and emptied the trash, but it didn't clear enough space.  Is there any other way to clear that much space? 

Thanks!

---

### Post by bluexrider on 2011-11-27
1. Do you have other partitions with free space? 
2. Possibility of external HDD? 
3. Remove un-essential programs or apps. 
4. Do you have VM ware installed with images, this takes a lot of space? 
5. Move your downloads off your system to DVD.

What else?

---

### Post by drs305 on 2011-11-27
Are you surprised that you have run out of space?

I'm not being sarcastic or funny - if your partition is normally not space-limited it could be that you have trash in root's trash bin that hasn't been emptied, or perhaps you've made a backup to / instead of an external drive, have very large log files, etc.

If you think your partition is large enough that it shouldn't have this problem, here is a link to a guide for investigating why a partition is suddenly full:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Autumnie88 on 2011-11-27
So, I'm not really sure about the partition.  To be honest, I don't really even understand how to find that out.  (which infuriates me, because there is nothing I hate more than feeling dumb!)  I don't have an external hard drive, nor can I move anything to a DVD.  I really don't have hardly any downloads or even documents on this computer.  Can I remove all the games and non essential crap that came on the computer?  If so, how?  Thanks for your help, and I apologize for my Ubuntu ignorance!

---

### Post by Autumnie88 on 2011-11-27
I am surprised that I have run out of space.  I am looking at the HOWTO link that you included, and checked the disk usage.  Problem is, I am not sure exactly what it means.  This is what I did...

autumn@autumn:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext3    3.4G  3.0G  272M  92% /
varrun       tmpfs    247M   96K  247M   1% /var/run
udev         tmpfs    247M   36K  247M   1% /dev

---

### Post by Autumnie88 on 2011-11-27
I have gone through your tutorial and am trying to delete the log files, and it tells me I don't have permission to do so.  Am I missing something or doing something wrong?

---

### Post by drs305 on 2011-11-27
> **Autumnie88 said:**
> I have gone through your tutorial and am trying to delete the log files, and it tells me I don't have permission to do so.  Am I missing something or doing something wrong?

You have to be root (use "sudo" or "gksu" for GUI apps like nautilus) at the start of commands that affect system files. But overall, your Ubuntu partition is pretty small and it's not surprising you are running out of room.

Here is another thread you may find useful - about how to take space from another partition to expand /. This assumes you have an independent Ubuntu installation on its own partition (not a Wubi installation).

The most important thing if you attempt to do this is to make backups of important data files and use a Windows partitioner to resize Windows if you are going to resize that partition.

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

