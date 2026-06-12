---
title: "Disk full?"
date: 2017-09-26
forum: New to Ubuntu
---

### Post by borg101 on 2017-09-26
Apparently my disk is full and I have no idea why.  I ran Disk Usage and it shows 214.4gb in my /var folder.  I also got a "Could not scan some of the folders contained in '/'"error which states "Error opening directory '/tmp/systemd-private-f8b8df63264741b9b3aaf4dcb9b0aa3b-systemd-timesyncd.service-VBl9Q4': Permission denied".  I did set my backup do backup ever day, but I told it to back up to a 2tb HDD and I checked the backup location as well as the backup application to make sure all the information is indeed going there and it is.  I checked my steam to double check that I have everything downloading and installing to another 2tb HDD and it is.  All my large files are on my 4tb HDD.  I'm confused as to what could be eating up my 250gb SSD.  As I'm fairly new to Linux and still learning file structures, I don't want to start deleting files that could unintentionally break my system.  Any advice?


*edit* I just checked the /var folder and apparantely in /var/log there are "60 items, totalling 211.1 GB (some contents unreadable)".  I'm not sure if this is a normal amount for that location.  There is a text file called "syslog.1" that is 211.1gb.  Why is this file so large?  Is it safe to delete?

---

### Post by TheFu on 2017-09-26
df
df -i

A full partition is bad.  [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) show what types of things are stored where.

---

### Post by HermanAB on 2017-09-26
Usually, you can delete everything in the /var/log folder with no ill effect.  The processes that really, really do want a log, will create a new one.  Other things will simply stop logging when their log files disappear.  The system will at least run again, while you sort out the mess.

---

### Post by Impavidus on 2017-09-26
The log files should be under or close to a MB. If you find a log file of that size, something is wrong. Search the log files for repeated messages. If the normal text editors are unwilling to open a file that size, use the terminal to display part of it:```
head -n 30 /var/log/syslog
```to view the first 30 lines of syslog,```
tail -n 40 /var/log/syslog.1
```to view the final 40 lines of syslog.1. Play with those commands until you find something.

---

### Post by ian-weisser on 2017-09-26
> **borg101 said:**
> *edit* I just checked the /var folder and apparantely in /var/log there are "60 items, totalling 211.1 GB (some contents unreadable)".  I'm not sure if this is a normal amount for that location.  There is a text file called "syslog.1" that is 211.1gb.  Why is this file so large?  Is it safe to delete?

Something is very wrong,the problem is repeating many times each minute, each occurrence is getting logged, and all that logging is filling your hard drive. Read a section of syslog.1 (use 'less' or 'tail' or another console-based reader. Trying to open a 211GB text file in any GUI program will promptly crash your system). Determine what the problem is, and then fix it.

---

### Post by oldfred on 2017-09-26
What brand/model system?

Some need boot parameter to prevent runaway log files.
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by borg101 on 2017-09-26
> **oldfred said:**
> What brand/model system?

Some need boot parameter to prevent runaway log files.
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

**Mobo:** *ASRock model: Z97E-ITX* **|** **CPU:** *Quad core Intel Core i5-4690* **|** **GPU:** *NVIDIA GM206 [GeForce GTX 960]* **|** **RAM:** * 16GB DDR3* **|** **SSD/HDD:** *Total Size: 8251.6GB* **|** **OS:** *Ubuntu 17.04 (Gnome3) *

---

### Post by borg101 on 2017-09-26
> **ian-weisser said:**
> Something is very wrong,the problem is repeating many times each minute, each occurrence is getting logged, and all that logging is filling your hard drive. Read a section of syslog.1 (use 'less' or 'tail' or another console-based reader. Trying to open a 211GB text file in any GUI program will promptly crash your system). Determine what the problem is, and then fix it.

Ok, So I'm reading through this thing line by line and I'm having trouble finding where the problem is.  This thing is HUGE though.  So give me awhile to see what, if anything else, I can find out.

I'm seeing "Sep 25 18:38:45 HTPC steam.desktop[5384]: process 5580: arguments to dbus_connection_unref() were incorre
ct, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connect
ion.c line 2794.
Sep 25 18:38:45 HTPC steam.desktop[5384]: This is normally a bug in some application using the D-Bus libr
ary.
Sep 25 18:38:45 HTPC steam.desktop[5384]: process 5580: arguments to dbus_connection_ref() were incorrect
, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connectio
n.c line 2656.
Sep 25 18:38:45 HTPC steam.desktop[5384]: This is normally a bug in some application using the D-Bus libr
ary.
Sep 25 18:38:45 HTPC steam.desktop[5384]: process 5580: arguments to dbus_connection_unref() were incorre
ct, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connect
ion.c line 2794."



Also, I'm not quite sure what "dleyna-renderer-service" is, but I remember right after install I got a crash and reported an error with that service.

---

### Post by oldfred on 2017-09-26
Asrock has ASmedia port issues. Only use SATA ports that are Intel.

 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)
 Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)

---

### Post by borg101 on 2017-09-26
I think I've found the issue.......

So I executed and .sh script to try to help me install Baldur's gate into GemRB.  It looks like it ran hundreds of times per second.  Either one of my cat's fell asleep on my keyboard, or something fishy is going on with the script.

---

### Post by borg101 on 2017-09-26
I deleted the file and emptied the trash and only 3.2gb are free now.  I don't see the file in the trash.

---

### Post by HermanAB on 2017-09-27
This problem is why on a server, one would make /var/log (and some others) a separate partition, so that if it fills up due to an error situation, the server will not stop running.

Anyhow, look at the log files with tail (only the last part is useful).  Then blow them away.  Schedule a fsck at next boot and then reboot to do it.  After that, the real disk space should be available.

---

### Post by borg101 on 2017-09-28
> **HermanAB said:**
> This problem is why on a server, one would make /var/log (and some others) a separate partition, so that if it fills up due to an error situation, the server will not stop running.

Anyhow, look at the log files with tail (only the last part is useful).  Then blow them away.  Schedule a fsck at next boot and then reboot to do it.  After that, the real disk space should be available.

How do I schedule that?  I ran the command in terminal and got "WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***  cause ***SEVERE*** filesystem damage."

---

### Post by TheFu on 2017-09-28
On non-systemd systems, **sudo touch /forcefsck** will do it at the next reboot.  It appears that someone over there decided maintaining that technique wasn't sufficient and removed it ... which means on 16.04 and later, you'll need to look up how to accomplish this with systemd.  I've had to look it up - that isn't hard - google.

You cannot fsck **any** mounted file system. Besides the /forcefsck file, there are other methods - like booting from a rescue disk/flash drive and manually running it or finding the systemd method.
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) might be helpful.  Debian also has a guide that is much more complete.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

### Post by HermanAB on 2017-09-30
Howdy,

I usually don't give a complete answer to things - I just point people in the general direction.  It is better for the user to google and read and figure things out by himself.  So, yeah, as suggested above, you need to read up on fsck.

Also, once you have your machine running again, look into deduplication with fslint.  If you have a ton of user data and suspect that many files are duplicates - with same or different names - then one of the fslint utilities can create hard links to these identical files which could save you oodles of disk space.  So if you want to try this, then read up on fslint and hard links also.

---

### Post by borg101 on 2017-10-01
> **HermanAB said:**
> Howdy,

I usually don't give a complete answer to things - I just point people in the general direction.  It is better for the user to google and read and figure things out by himself.  So, yeah, as suggested above, you need to read up on fsck.

Also, once you have your machine running again, look into deduplication with fslint.  If you have a ton of user data and suspect that many files are duplicates - with same or different names - then one of the fslint utilities can create hard links to these identical files which could save you oodles of disk space.  So if you want to try this, then read up on fslint and hard links also.


Just as a heads up, I both agree and disagree with your philosophy of leaving someone to their own devices to find information.  I agree because, it can lead someone to find the information on their own and, therefore, lead to personal success.  I disagree because, in most cases, an individual won't know whether or not what he or she is reading is correct.  This is the reason we have teachers, experts, doctors, etc instructing students, apprentices, etc.  That's the reason education exists, in first world economies, in its current form today.  Just my two cents.  No need to debate the topic here.  As I said, there is merit to your reasoning.

For the record, before I asked, I spent about an hour searching.


As to the initial problem, I just did a fresh install.

---

### Post by HermanAB on 2017-10-01
'fresh install' - Cool, what I like about Ubuntu is that it is very quick to do a fresh install.  If your problem starts again, then it would be a very serious head scratcher.

---

