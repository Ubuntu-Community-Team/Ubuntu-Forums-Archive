---
title: "Gparted scans /dev/sda partitions indefinatley"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by ProboshTodosh on 2013-02-19
Hi, 

I want to use Gparted to reallocate that lost space on my hard drive between both operating systems. Unfortunately for me, Gparted won't even move on past the initial scanning of "/dev/sda partitions". I have attempted to use Gparted from root & using live CD with version 0.14.1-6-i486.iso

     I have scanned various threads in various places, yet I have not seen a situation quite like this one nor am I quite comfortable tossing commands into terminal that I do not understand. As an aside, if there is a website link or page that I can go to in order to learn basic Terminal protocol & Ubuntu function, that would be outstanding. I just impulsively made the switch to Ubuntu after too many Windows failures.

[Background information that may be of use to diagnose this issue]
     I've recently installed Ubuntu 12.04 LTS on my Dell Inspiron mini  dual booting with Windows 7 starter that initially came with the system.  Prior to installing 12.04 when I did not have Internet readily  available & using Live USB to get the job done, I had installed  11.04 on my system as a dual boot. Rather than installing 12.04 over  11.04 as if I were upgrading, I had (quite noobishly i might add)  created another partition where I installed 12.04; later on realizing my  mistake I moved to delete that partition while having my current set up  run well the way it is (12.04 & Windows 7)

     Any help would be greatly appreciated.

---

### Post by ProboshTodosh on 2013-02-19
Bump

---

### Post by kagashe on 2013-02-19
You can have a look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/155047").

Kamalakar

---

### Post by ProboshTodosh on 2013-02-20
Thanks for the reply and I took a look at that bug post. I then went into my BIOS to see if there was anything labeled "Floppy" to disable which there was not, though I did disable Removable Devices being that it differentiates from my USB Storage in the BIOS to see if that would do the trick - it did not.

I also tried entering these commands as the bug link suggested, which didn't produce any results either:
"sudo rmmod floppy" 
"sudo rmmod -f floppy"

Do you have any other suggestions? Perhaps there is an alternative means to reallocate my partition sizes?

---

### Post by ProboshTodosh on 2013-02-20
Updated - 

So what it ended up being was something inherently related to Dell Inspiron laptops, as seen in this link:

[HTML]http://gparted-forum.surf4.info/viewtopic.php?id=16547[/HTML]

There is a tiny sliver partition listed first before all other partitions on my hard drive labeled "Dell Utility". Gparted ceased to scan continuously "/dev/sda partitions" upon identifying & killing the process that perpetuated it, as seen below taken from my terminal window:


```
root@partedmagic:~# ps -ef | egrep "dosfsck|ntfs"
root      3510  3451 96 19:00 tty1     00:10:00 dosfsck -n -v /dev/sda1
root@partedmagic:~# kill -s 15 3510
root@partedmagic:~#
```

---

