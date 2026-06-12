---
title: "[SOLVED] Rkhunter issued some warnings... what to do?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by the8thstar on 2008-04-29
Hello,

I just ran rkhunter -c with the latest update and it returned some **warnings**:

> 
[17:13:09]   Checking /dev for suspicious file types         [ Warning ]
[17:13:09] Warning: Suspicious file types found in /dev:
[17:13:09]          /dev/shm/pulse-shm-431927995: data
[17:13:09]   Checking for hidden files and directories       [ Warning ]
[17:13:09] Warning: Hidden directory found: /etc/.java
[17:13:09] Warning: Hidden directory found: /dev/.static
[17:13:09] Warning: Hidden directory found: /dev/.udev
[17:13:09] Warning: Hidden directory found: /dev/.initramfs

My question is: [COLOR="Blue"]**what can I do from there to set the system straight?**[/COLOR]

---

### Post by spiderbatdad on 2008-04-29
Doesn't appear to be a problem Just Rkhunter unaware of certain files in Ubuntu.

[https://lists.sourceforge.net/lists/listinfo/rkhunter-users](https://lists.sourceforge.net/lists/listinfo/rkhunter-users)
> 
* If you get warnings about hidden files or applications you have verified are trusted: please check rkhunter.conf for whitelisting options. 

---

### Post by the8thstar on 2008-04-29
Thank you **spiderbatdad**. From the website you gave me:

> If you get warnings about hidden files or applications you have verified are **[COLOR="Blue"]trusted[/COLOR]**: please check rkhunter.conf for whitelisting options. 

My problem is that I don't know if I can "trust" the apps with the warning flags. And I don't want to white-list some potential danger. How would I know???

---

### Post by pedja_portugalac on 2008-04-29
> **the8thstar said:**
> Thank you **spiderbatdad**. From the website you gave me:

 

My problem is that I don't know if I can "trust" the apps with the warning flags. And I don't want to white-list some potential danger. How would I know???
I use ubuntu for more then a year and I never had a single problem even that I've white-listed 

/etc/.java
/dev/.static
/dev/.udev
/dev/.initramfs 

But this time it comes to me another warning and it comes after the fresh install of hardy.

/dev/shm/pulse-shm-3801237314

I don't know what it is exactly but as it comes from the fresh install, before even first connect to the internet, I thought it is problem with rkhunter database. So I've tried to clean that warning with command

$sudo rkhunter --propupdate

It doesn't work and it steel come back, again and again. Don't know what to do. It comes to me ones idea to reinstall 7.10 but then, I don't have really important things to hide on my computer and I love new features in hardy. Some day, somebody will surely fix this. It's up to you now, if you have really important things on your computer or if what you do with it is top secret don't install any non open source package and try debian. Otherwise kip ubuntu hardy for great multimedia features, reasonable security, easy of use and learn how to secure it. 
Cheers man. :lol:

---

### Post by pedja_portugalac on 2008-05-08
Now first!

**What is /dev/shm and its practical usage**

/dev/shm is nothing but implementation of traditional shared memory concept. It is an efficient means of passing data between programs. One program will create a memory portion, which other processes (if permitted) can access. This will result into speeding up things on Linux.

shm / shmfs is also known as tmpfs, which is a common name for a temporary file storage facility on many Unix-like operating systems. It is intended to appear as a mounted file system, but one which uses virtual memory instead of a persistent storage device.

If you type mount command you will see /dev/shm as a tempfs file system. Therefore, it is a file system, which keeps all files in virtual memory. Everything in tmpfs is temporary in the sense that no files will be created on your hard drive. If you unmount a tmpfs instance, everything stored therein is lost. By default almost all Linux distros configured to use /dev/shm.

**Nevertheless, where can I use /dev/shm?**

You can use /dev/shm to improve the performance of application software or overall Linux system performance. On heavily loaded system, it can make tons of difference. For example VMware workstation/server can be optimized to improve your Linux host's performance (i.e. improve the performance of your virtual machines).

**Rkhunter warning**

It seems to me, /dev/shm/pulse-shm-0123456789 or whatever number is not dangerous for the system. Contrary, it's advantageous and I suppose that's the reason why it comes in default installation of Ubuntu (hardy). 

**How to configure rkhunter to avoid that warning?**

I don't know as the /dev/shm/pulse-shm-0123456789 file change on every reboot. One could say to rkhunter config file that /dev/shm/pulse-shm-0123456789 is not dangerous for the system adding this line:

# Allow the specified files to be present in the /dev directory and not
# regarded as a suspicious file.  One file per line (use multiple
# ALLOWDEVFILE lines), wildcards accepted.
#
#ALLOWDEVFILE=/dev/abc
ALLOWDEVFILE=/dev/shm/pulse-shm-2964075512

But this will stop warning just until reboot of system. The number in the end of pulse-shm file change on every start and is unpredictable.  

**Conclusion**

Actually, I don't see how to disable definitely rkhunter warning for /dev/shm/pulse-shm and I hope people who work on rkhunter development will fix this soon. Also I presume gutsy Ubuntu need this and that's way it comes by default on fresh install. So don't unmount it and don't touch it at all.

**Warning**

I am not security expert and you should considering this explanation at your own risk. In any way I'll not be responsible for data loss or security holes in your system because of this post!!!

---

### Post by kwilliam on 2008-05-26
> **pedja_portugalac said:**
> But this will stop warning just until reboot of system. The number in the end of pulse-shm file change on every start and is unpredictable. 

If I understand the config file correctly, it says you're allowed to use wildcard characters. So you could add /dev/pulse-shm-* I assume.

---

### Post by BlackBaron1024 on 2008-07-05
> **kwilliam said:**
> If I understand the config file correctly, it says you're allowed to use wildcard characters. So you could add /dev/pulse-shm-* I assume.

I just tested this, and it works indeed like a charm.

Thanks to everyone for the info.

---

