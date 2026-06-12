---
title: "[SOLVED] install stops at &amp;quot;initramfs prompt&amp;quot;"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by RICARDO MENDES on 2008-08-09
I'm trying to run live cd ubuntu 8.04 and the installation stops on a screen with the following: 

Busybox v1.1.3 (Debian 1:1.1.3-5 ubunt12) Built-in shell (ash)

(iniramfs)


I have a AMD Athlon 64 x2 3800, 2.0Ghz, ASUS M2n-MX SE, with Windows XP professional, an HD with 250GB, and 512 ram.

I tried checking the CD for errors and it went to the same screen.

---

### Post by Sleeve98 on 2008-08-09
Yeh, I get same.  Date on your post is June; did you get it resolved?

---

### Post by spiderbatdad on 2008-08-09
Often I see the suggestion to try the alternate cd to resolve this issue. There are also boot options that might be helpful...like noapic nolapic. I always recommend deleting quiet splash when applying boot options:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by RICARDO MENDES on 2008-08-09
Yes, still have the same problem.

Already tried noapic nolapic. Even tried older version (ubuntu 7...) suggestions like all_generic_ide and pci_nomsi that I thought seemed related to the problem. 

Nothing has worked. 

Stupid question: do I type in these option immediately after "quiet splash" or after the "--"?

---

### Post by RICARDO MENDES on 2008-08-09
> **Sleeve98 said:**
> Yeh, I get same.  Date on your post is June; did you get it resolved?
No, havent solved yet. Already tried lots of boot options. Going to try with alternate CD as Spiderbatdad suggested.

---

### Post by tinker312 on 2008-08-09
What type of operating system are you trying to run the live cd on? I googled initramfs and it appeared fairly buggy back in late 2007.  The posts I read had information about Fat32 partitions and initramfs limitations in dealing with these. I referenced a post about Wubi installer (Windows Ubuntu Installer) not exactly the same issue but relating to initramfs.  Hope this renews your quest to find an answer. 

[http://ubuntuforums.org/showthread.php?t=591746](http://ubuntuforums.org/showthread.php?t=591746)

---

### Post by Sleeve98 on 2008-08-15
Booting to alternate CD reveals the root problem (or at least a different one):  No hard disk drives detected, though, as seems to be common judging by all the threads, Windows can boot, format and run just fine.

Trying to resolve...

HDD1:  WD1000BB
HDD2:  WD300AB

Installer wants diskette w/ HDD "drivers," but no such animal can be found on WD's website, nor can I find anything related in Ubuntu.com's support docs.

...still banging head...

---

### Post by ingeva on 2008-08-15
> **Sleeve98 said:**
> HDD1:  WD1000BB
HDD2:  WD300AB


I had a very similar problem. It may be caused by having more than one HD in the system, but not necessarily.

Restart the computer and enter setup. Find the disk interface definition and change from IDE (or something else) to RAID.

You will still not get a RAID system, but you may be able to boot and install properly.
For some reason Windows doesn't seem to care about this setting, but Linux does.

---

### Post by Sleeve98 on 2008-08-15
Well -

It wasn't until I put the optical drive on the 2ndary IDE controller BY ITSELF, jumpered as Master, that the Ubuntu installer detected the drives.

Now, Grub's happy, Gnome's happy, user's happy. :)

Thanks for all the help!


*If there's anything I can't stand, it's intolerance!*

---

### Post by ingeva on 2008-08-15
> **Sleeve98 said:**
> Well -
It wasn't until I put the optical drive on the 2ndary IDE controller BY ITSELF, jumpered as Master, that the Ubuntu installer detected the drives.
Now, Grub's happy, Gnome's happy, user's happy. :)

*If there's anything I can't stand, it's intolerance!*

Great! Congratulations!

I too hate intolerant people .... :)

---

### Post by zaivala on 2008-08-25
Well, I'm getting the problem now.  My Ubuntu 8.04 HH is installed through Wubi on my Windows drive.  It has worked like a dream for several months.  I just had to reboot to Windows (to do some work, as mentioned on my other threads here and on OOo's forum), booted back to Linux (about 2 hours later), and I'm stuck with 

(initramfs) 

prompts.  Has anyone figured out how to get out of initramfs and back to Gnome?  Do I have to reinstall again???  (Using the alternative CD won't work, as I don't have one.)

I have added no new drives, done absolutely nothing new (other than edit a few documents in Word and use Firefox to upload the documents to other users).

---

### Post by zaivala on 2008-08-25
I solved the problem.  Easier than it seemed.  Once I read that post that it can be caused by an abnormal shutdown of Windows, I decided to try another reboot from Windows (Windows booted properly, or I wouldn't have been able to make my posts and searches).  Before I did so, I did a defrag and used CCleaner and another file cleaner program, just for luck.

Booted down properly, booted up to Linux just fine.

I still would like to know what causes this, but it's fixed for now.

---

