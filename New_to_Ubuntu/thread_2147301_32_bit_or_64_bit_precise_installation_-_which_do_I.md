---
title: "32 bit or 64 bit precise installation - which do I have?"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by allynm on 2013-05-21
Hello everyone,
I know this question sounds foolish....but I am compelled to ask anyway in spite of opprobrium I will (deservedly) receive.  Two questions:
1.  How do I query using the shell to determine which version (32 or 64 bit) of Ubuntu Precise I have installed.  There must be a way.
2.  If in fact I installed about a year ago the 32 bit version, how do I upgrade to 64 bit without disturbing --or minimally disturbing--existing files?

Thanks,
Mark Allyn

---

### Post by deadflowr on 2013-05-21
Easiest way to find out is to open a terminal and put in

```
uname -a
```

If it includes x86_64 it's 64-bit.
If includes i386,486,586,or 686 it's 32-bit.

As far as upgrading from 32 to 64, simplest thing is to backup your files and install the 64 bit.

---

### Post by oldfred on 2013-05-21
Some commands:
 [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
32 or 64 bit
uname -a
i386 or i686 = 32-bit
x86_64 = 64-bit
lscpu
      
 Version or DISTRIB:
cat /etc/*release
cat /etc/lsb-release

List installed kernels:
dpkg --list | grep linux-image
echo $DESKTOP_SESSION

You have to do a clean new install. Do you have a separate /home as that makes it easier. And you should have good backups of your data & /home anyway.

Oldfred's backup assumes a new install, so I backup what I need to reinstall and restore my system. Primarily /home and list of installed apps. But depending on what you have you may want other details backed up.

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

Some temporary files you do not need to backup.

 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

If you have made system setting changes (not user) they would be in /etc.

 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by allynm on 2013-05-21
Oldfred and Deadflowr,

Thanks for the info.  Looks like I'm on a 32 bit Ubuntu 12.04 machine.  Too bad!

Could either of you suggest :

1.  The best way to back this version up so I don't lose the files.
2.  Having backed them up, what would you recommend I do to run them on the 64bit version?

Thanks,
Mark

---

### Post by iamkuriouspurpleoranj on 2013-05-21
```
cat /etc/debian_version
```

Next time someone says "run Debian", tell him/her you already are and show that as proof.

---

### Post by MoebusNet on 2013-05-22
> **allynm said:**
> ...
1.  The best way to back this version up so I don't lose the files.
2.  Having backed them up, what would you recommend I do to run them on the 64bit version?

Thanks,
Mark

Just to put in my 2 cents:

1) I use the default Backup (Deja-Dup) application to back up my /Home directory so that i can restore my files and settings if need be. It has backup & restore capability, which I used to restore the data from my 64-bit notebook to my newly-installed 32-bit notebook. Worked for me with no issues.

2) The data files themselves shouldn't care if you are on a 32-bit or 64-bit OS. Just use the same application to open them as you used to create the data files. You'll have to reinstall the applications after you do a clean install of your 64-bit OS, but other than that you should be good to go.

If you don't have an external USB hard drive to back up to, may I suggest that you purchase one before you attempt to move from 32-bit to 64-bit? Large external drives can be had for <$100 and are always a good way to preserve valuable data. Other alternatives are USB flash drives, CD's,  DVD's and cloud back-up solutions but I think you get the most bang for your buck with an external USB HDD. Just my opinion, YMMV.

More info:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Zill on 2013-05-22
> **allynm said:**
> ...Thanks for the info.  Looks like I'm on a 32 bit Ubuntu 12.04 machine.  Too bad!...
Why "Too bad"?

Unless you have more than 4GB of RAM the standard 32-bit Ubuntu is fine.  With a [PAE kernel]("https://help.ubuntu.com/community/32bit_and_64bit") even 32-bit Ubuntu can work with up to 64GB of RAM.

If the machine does everything you want there is no need to change to 64-bit.

---

### Post by zombifier25 on 2013-05-22
> **Zill said:**
> Why "Too bad"?

Unless you have more than 4GB of RAM the standard 32-bit Ubuntu is fine.  With a [PAE kernel]("https://help.ubuntu.com/community/32bit_and_64bit") even 32-bit Ubuntu can work with up to 64GB of RAM.

If the machine does everything you want there is no need to change to 64-bit.

Switching to 64bit is more beneficial in the long term. 64bit OS, generally speaking, has better performance than a 32bit OS, and it can take advantage of >4GB RAM. Yes, PAE allows a 32bit OS to use more than 4GB, but applications are still restricted by the 32bit virtual address space, to they can only use 4GB at a time, and not more. Also, in the future everything is probably going to be 64bit, so upgrade earlier rather than later.

You are still correct though. Unless you are going to do some very resource-intensive task (like gaming or graphics), then 64bit provides minimal benefits. Still, it's recommended that we upgrade to 64bit if our systems allow it.

---

