---
title: "Virus protection in Linux"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by webdfeet on 2013-10-28
I am running Ubuntu from a 1 terabyte external hard drive. My main computer has WinXP on the hard drive, on which is installed AVG2013 as antivirus protection.
Will this AVG program also cover the external hard drive, or do I have to install an antivirus program on that as well? System is dual-boot.

---

### Post by david98 on 2013-10-28
Are you using the external drive for anything else if not everything is going to be fine will not need to install anything. If opening in window's you could always scan for virus's

---

### Post by DeezyFaReal on 2013-10-28
Virus protection in Linux
in case your looking for that^ try rkhunter (rootkit hunter), or clamav (clam antivirus) for ubuntu, and gufw firewall. I heard wireshark is good.

---

### Post by buzzingrobot on 2013-10-28
If the external drive is visible to XP, then a Windows AVG program ought to be configurable to scan it.

viral threats to Linux are minimal.  If you are on a network and exchange mail/files with Windows users, then something like ClamAV on Linux will target Windows viruses in mail/files sent to you, preventing you from passing them on.

---

### Post by deadflowr on 2013-10-28
From what I remember, you can set the AVG to scan any external drives/partitions as well as the main partition.

---

### Post by cdaver on 2013-10-28
Just do a google search next time, plenty of discussions regarding this topic. No need to start your own discussion.

[http://askubuntu.com/questions/10373/do-i-need-to-have-antivirus-software-installed](http://askubuntu.com/questions/10373/do-i-need-to-have-antivirus-software-installed)

---

### Post by webdfeet on 2013-10-29
Thanks. The external disk drive doesn't show up under My Computer, but I'll take a further look at my AVG...I don't usually fiddle much with that, so it's probably got other capability that I haven't tapped into yet.

---

### Post by 3rdalbum on 2013-10-29
> **webdfeet said:**
> Thanks. The external disk drive doesn't show up under My Computer

Then it's fully Linux-formatted. Windows can't read Linux partitions or hard disks.

Which also means that you won't get any viruses on it. If Windows can't understand it, no virus would get onto it either.

---

### Post by mastablasta on 2013-10-29
unless a user moves the infected file from linux into windows disk... linux won't get infected, but windows might.

---

### Post by whitesmith on 2013-10-29
> **3rdalbum said:**
> Then it's fully Linux-formatted. Windows can't read Linux partitions or hard disks.
Which also means that you won't get any viruses on it. If Windows can't understand it, no virus would get onto it either.Actually there's a sneaky back door that allows Windows viruses to clobber Linux boxes. Just install an infected Winapp under Wine running as root. Admittedly it doesn't happen often because most *nix guys are wise to this kind of thing, but still...

---

### Post by oldos2er on 2013-10-29
> **cdaver said:**
> Just do a google search next time, plenty of discussions regarding this topic. No need to start your own discussion.

[http://askubuntu.com/questions/10373/do-i-need-to-have-antivirus-software-installed](http://askubuntu.com/questions/10373/do-i-need-to-have-antivirus-software-installed)

Except this is Absolute Beginners, and we encourage all questions no matter how "dumb" or how often they've been asked in the past. While some topics may be moved to Recurring Discussions, that's much more a matter of categorization than a judgment on the question.

---

### Post by Impavidus on 2013-10-29
> **whitesmith said:**
> Actually there's a sneaky back door that allows Windows viruses to clobber Linux boxes. Just install an infected Winapp under Wine running as root. Admittedly it doesn't happen often because most *nix guys are wise to this kind of thing, but still...

And even then I think you have to tweak wine as by default it refuses to run as root. I think. I haven't installed it.

---

### Post by DeezyFaReal on 2013-11-04
cdaver Good point!, 3rdalbum I noticed that too, windows don't recognize my macpup thumbdrive, whitesmith you really have had way too much ubuntu

---

