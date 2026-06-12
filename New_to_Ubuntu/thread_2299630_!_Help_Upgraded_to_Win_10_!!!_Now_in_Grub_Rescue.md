---
title: "! Help Upgraded to Win 10 !!! Now in Grub Rescue"
date: 2015-10-20
forum: New to Ubuntu
---

### Post by Darrell_W._Coates on 2015-10-20
I've Upgraded to Win 10 From Dual Boot Win 7 And Ubuntu 15.4
Grub was Booting Win 7 or Ubuntu 15.4 Before I Upgrade to Win 10
 Now In Grub Rescue

   Where Do I Go From Here?
                                      Thanks Again,
                                                         Darrell

---

### Post by yancek on 2015-10-20
Your upgrade to a newer version of windows has overwritten the Grub bootloader without asking or notifying you that this would be done.  Standard behavior for windows.  You will now need to reinstall the Grub bootloader as the default windows bootloader will not boot any Linux.  The method for repairing Grub will vary depending upon whether your windows 10 is using UEFI or MBR to boot.  You can go to the site below and get the boot repair software, burn it to a CD and boot with it and then select the option to Create BootInfo Summary and post a link to it here.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by NathanRodriguez on 2015-10-20
You can install Boot Repair on a live Ubuntu disk with net connection too.

---

### Post by mystics on 2015-10-20
Not sure if it's the exact same problem, but there's been a couple of these on Ask Ubuntu that might help:
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue)
[http://askubuntu.com/questions/655011/windows-10-upgrade-kills-grub-and-boot-repair-doesnt-help](http://askubuntu.com/questions/655011/windows-10-upgrade-kills-grub-and-boot-repair-doesnt-help)

> **yancek said:**
> Your upgrade to a newer version of windows has overwritten the Grub bootloader without asking or notifying you that this would be done.  Standard behavior for windows.

Well, at least now I know that Linux isn't the only one that does that. And yes, I'm speaking from experience.

---

### Post by oldfred on 2015-10-20
Post this to see if you have gap in extended partition where Linux partition was:
       sudo parted /dev/sda unit s print

If that is the case then the links posted above by mystics should work.
Most seem to now find parted rescue easier than testdisk.

 Backup current partition table structure to text file & save to external device, just in case. Only for MBR(msdos).
sudo sfdisk -d /dev/sda > PTsda.txt


Similar threads in Ubuntu forums:
      Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

---

### Post by yancek on 2015-10-20
> Well, at least now I know that Linux isn't the only one that does that. And yes, I'm speaking from experience.         

The difference between windows and Linux is of course, with Linux you are always given the option to install to the MBR or / partition and with some distributions, not to install it at all which in a multi-boot situation isn't necessary.  The problem most people have is not paying attention during the install.  The default is to install to the MBR and with Ubuntu and derivatives, there is always the option 'Device for bootloader installation' available on screen.  With windows, you are never informed that this will happen and certainly aren't asked if that's what you want.

---

### Post by mystics on 2015-10-20
> **yancek said:**
> > Well, at least now I know that Linux isn't the only one that does that. And yes, I'm speaking from experience.

The difference between windows and Linux is of course, with Linux you are always given the option to install to the MBR or / partition and with some distributions, not to install it at all which in a multi-boot situation isn't necessary.  The problem most people have is not paying attention during the install.  The default is to install to the MBR and with Ubuntu and derivatives, there is always the option 'Device for bootloader installation' available on screen.  With windows, you are never informed that this will happen and certainly aren't asked if that's what you want.

As far as I'm concerned, if an installer doesn't present things in a way to inform users of obscure information (seriously, not everyone installing Linux, especially Ubuntu, understands what MBR and / are) is just as bad as hiding the information or not giving a choice at all. None of those benefit the end user unless they are fully informed, which they often aren't. From what I've read, seen, and experienced, both Windows and Ubuntu have caused many users trouble in this regard, but many users don't experience these problems, so I'd hardly say either are actively trying to sabotage the end user. As far as I'm concerned, both have a ways to go on installing and upgrading, but I'd say that in regards to stop overlooking potential issues rather than stop being malicious, as I don't think either are being actively malicious.

And with that, I'm not going to bother commenting any more on this. The OP wants to know how to fix a problem. Let's stick to offering that here and keeping the Windows vs. Linux stuff in OS Chat and The Cafe.

---

### Post by yancek on 2015-10-20
> The OP wants to know how to fix a problem. 

My initial post suggested a method for the OP to get information to post here so someone could help.  Your post made no suggestions to the OP in regard to his problem and was an irrelevant comment about Ubuntu/Linux.

---

### Post by Geoffrey_Arndt on 2015-10-21
Darell,  . . . both Yancek and Mystics have provided good info and several potential fixes.    What have you tried so far . . . ?  (the ball's in your court).   Also, that boot-repair link/data could be useful.

---

