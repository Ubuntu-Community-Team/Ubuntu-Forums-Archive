---
title: "Increase the space size of /home drive?"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by zeuso0 on 2011-10-25
Sorry, I am absolute new to partition in Ubuntu, and I want to increase the size of ./home 
so, here is the disk space info:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            3.9G  1.3G  2.4G  35% /
none                  490M  248K  490M   1% /dev
none                  495M  1.2M  494M   1% /dev/shm
none                  495M  124K  495M   1% /var/run
none                  495M     0  495M   0% /var/lock
/dev/sda5              20G   11G  9.6G  53% /host
/dev/loop1            1.7G  1.1G  586M  65% /home
/dev/loop2            3.9G  3.2G  549M  86% /usr
```[IMG]http://ubuntuforums.org/home/zhou/Desktop/Screenshot.png[/IMG]
[IMG]http://ubuntuforums.org/home/zhou/Desktop/Screenshot.png[/IMG][IMG]http:///home/zhou/Desktop/Screenshot.png[/IMG]I dont know why I couldn't insert the screenshot image here.
I need /home space to be 20 GB ,but only 586M available right now
so HOW do I move 20 GB from sda3(the windows drive, I have dual boot) to /home drive? Please give some guidance. 

Joe

---

### Post by drs305 on 2011-10-25
You can take a look at this thread I created on expanding / by taking space from Windows.

If you are going to resize Windows, I highly recommend you shrink it with a Windows tool and then continue the operation from within Ubuntu. And always backup your important data before doing any partition work...

[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by JKyleOKC on 2011-10-25
> **zeuso0 said:**
> Sorry, I am absolute new to partition in Ubuntu, and I want to increase the size of ./home 
so, here is the disk space info:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            3.9G  1.3G  2.4G  35% /
none                  490M  248K  490M   1% /dev
none                  495M  1.2M  494M   1% /dev/shm
none                  495M  124K  495M   1% /var/run
none                  495M     0  495M   0% /var/lock
/dev/sda5              20G   11G  9.6G  53% /host
/dev/loop1            1.7G  1.1G  586M  65% /home
/dev/loop2            3.9G  3.2G  549M  86% /usr
```[IMG]http://ubuntuforums.org/home/zhou/Desktop/Screenshot.png[/IMG]
[IMG]http://ubuntuforums.org/home/zhou/Desktop/Screenshot.png[/IMG][IMG]http:///home/zhou/Desktop/Screenshot.png[/IMG]I dont know why I couldn't insert the screenshot image here.
I need /home space to be 20 GB ,but only 586M available right now
so HOW do I move 20 GB from sda3(the windows drive, I have dual boot) to /home drive? Please give some guidance. 

JoeThat "/host" partition suggests that your "dual boot" is actually a "wubi" installation, which goes into a file inside your Windows file system, that is then treated as a standalone hard drive and partitioned.

If that's the case, you won't have much luck trying to increase the size of your /home partition, since your entire "drive" for the Linux installation is no larger than the Windows file within which it resides, and is limited by the wubi program to a maximum of 30 GB.

The /host partition, in a wubi-installed system, is the original Windows drive in which the Linux system was installed. In your case it appears to be 20 GB, with all but 9 GB in use. Thus the most you could add to /home would be that 9 GB.

If you absolutely must have 20 GB in your /home partition, and also want to retain your Windows installation, your best bet would be to install an additional hard drive (which could be external, if your system allows booting via USB) and transfer your Linux installation to it. You could then expand /home to occupy all of the leftover space on the new drive.

Hope this helps! Sorry to be the bearer of bad news though.

---

### Post by LinuxFan999 on 2011-10-25
> **zeuso0 said:**
> Sorry, I am absolute new to partition in Ubuntu, and I want to increase the size of ./home 
so, here is the disk space info:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            3.9G  1.3G  2.4G  35% /
none                  490M  248K  490M   1% /dev
none                  495M  1.2M  494M   1% /dev/shm
none                  495M  124K  495M   1% /var/run
none                  495M     0  495M   0% /var/lock
/dev/sda5              20G   11G  9.6G  53% /host
/dev/loop1            1.7G  1.1G  586M  65% /home
/dev/loop2            3.9G  3.2G  549M  86% /usr
```[IMG]http://ubuntuforums.org/home/zhou/Desktop/Screenshot.png[/IMG]
[IMG]http://ubuntuforums.org/home/zhou/Desktop/Screenshot.png[/IMG][IMG]http:///home/zhou/Desktop/Screenshot.png[/IMG]I dont know why I couldn't insert the screenshot image here.
I need /home space to be 20 GB ,but only 586M available right now
so HOW do I move 20 GB from sda3(the windows drive, I have dual boot) to /home drive? Please give some guidance. 

Joe
Why do you have such a small hard drive?

---

