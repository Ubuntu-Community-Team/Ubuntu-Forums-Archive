---
title: "what if..."
date: 2008-06-13
forum: New to Ubuntu
---

### Post by cristo-father on 2008-06-13
If i had (not the case) a dual-boot, windows xp and linux mint(ubuntu based) and windows got a virus, would i be able to run linux mint or would that virus be able to affect my whole "system"?

---

### Post by philinux on 2008-06-13
> **cristo-father said:**
> If i had (not the case) a dual-boot, windows xp and linux mint(ubuntu based) and windows got a virus, would i be able to run linux mint or would that virus be able to affect my whole "system"?

Windows virus wont run on linux.

---

### Post by aktiwers on 2008-06-13
Only Windows..  remember Windows can't even see Linux - which makes it hard for the virus as well.
Don't worry it will only affect Windows.

---

### Post by issih on 2008-06-13
I suppose, as a matter of technicality, if you had your linux partition mounted read write in windows (I'm not even sure if thats possible, I've never tried) and managed to get a virus that went off indiscriminately wiping data it could theoretically take out linux. But in general its very unlikely.

---

### Post by Oldsoldier2003 on 2008-06-13
> **cristo-father said:**
> If i had (not the case) a dual-boot, windows xp and linux mint(ubuntu based) and windows got a virus, would i be able to run linux mint or would that virus be able to affect my whole "system"?

If you got a windows virus that affects the MBR you would still have problems booting to Linux because the MBR is damaged and Grub Will not run. (most of the time grub is installed to the MBR )

---

### Post by housam on 2008-06-13
To run any command you need the sudo permission and a password. windows viruses don't have that option.

---

### Post by cristo-father on 2008-06-13
> **issih said:**
> I suppose, as a matter of technicality, if you had your linux partition mounted read write in windows (I'm not even sure if thats possible, I've never tried) and managed to get a virus that went off indiscriminately wiping data it could theoretically take out linux. But in general its very unlikely.

How can i prevent this?

> If you got a windows virus that affects the MBR you would still have problems booting to Linux because the MBR is damaged and Grub Will not run. (most of the time grub is installed to the MBR )

I do not know what MBR is(:lolflag: i am soooo noob)...
But can i deny windows to alter the MBR.

---

### Post by housam on 2008-06-13
> **Oldsoldier2003 said:**
> If you got a windows virus that affects the MBR you would still have problems booting to Linux because the MBR is damaged and Grub Will not run. (most of the time grub is installed to the MBR )

I think creating a dedicated grub partition will prevent this from happening .

---

### Post by adamorjames on 2008-06-13
MBR is the Master Boot Record.

Type this in to Google, "define: mbr" and you get:

# Master Boot Record. When a hard drive is partitioned, the Master Boot Record is written to the first sector on the hard drive. It contains the Partition Table and other information needed by the BIOS to access the hard drive.
[www.pccomputernotes.com/pcterms/glossarym.htm](www.pccomputernotes.com/pcterms/glossarym.htm)

---

### Post by cristo-father on 2008-06-13
> **housam said:**
> I think creating a dedicated grub partition will prevent this from happening .

Can i do that while partitioning linux in the installation process?

---

### Post by sam_delta on 2008-06-13
MBR = master boot record, it contains instructions that your computer has to follow the first moment when you turn on your pc. (such as booting)
having a dedicated /boot partition wont help, as the default /boot partition is well safe on your ubuntu partition.
if you even get your MBR messed by windows, you can always restore it with a super grub live disk [www.supergrubdisk.org/](www.supergrubdisk.org/)

sam

---

### Post by ByteJuggler on 2008-06-13
> **cristo-father said:**
> How can i prevent this?
I do not know what MBR is(:lolflag: i am soooo noob)...
But can i deny windows to alter the MBR.

Windows XP by default running as the default user will give administrator privileges to that user, thereby giving a virus running under that user's security context pretty much unfettered access to the system, including the MBR. That in a nutshell is the problem of the Windows "unresitricted access" philosophy that  has bitten it badly in recent years.  Vista is a little better and asks for permission when doing potentially damaging things, but that's not totally foolproof either since people get used to just clicking "yeah ok whatever" when the dialog shows, so chances are when the virus triggers that check you'll probably go "Yeah ok whatever" and so the protection will have been illusory.  

Anyway, the way I see, your options to deal with MBR corruption are:
1) Don't run Windows
2) If you have to run Windows, run as restricted user.
3) If you must run as an administrative user, try to do it for as short as possible (like what Ubuntu does really), and/or get a newer version of Windows (Vista).
4) Make a backup of your MBR, and put it on a floppy/CD so you can restore it with an Ubuntu LiveCD.  (For example, the command "sudo dd if=/dev/sda of=~/PartitionTableAndMBR.img bs=512 count=1" will copy the MBR/partition table from /dev/sda into a file in your home directory.)
5) Keep Linux on a seperate drive, with its own MBR that only knows about/boots Linux.  Then put that drive to a secondary postition, and install Windows + Grub onto your primary Windows drive.  Then if the MBR on the primary drive gets damaged for any reason, your Linux drive can still boot independently if you swap the drives around.  

Notwithstanding the above, a clobbered MBR due to a virus is really fairly rare, and can in any case be recovered from without having to go to too much trouble, so you might simply want to not worry too much about it and ignore my suggestions!

Hope that helps.

---

### Post by cristo-father on 2008-06-13
> **ByteJuggler said:**
> Windows XP by default running as the default user will give administrator privileges to that user, thereby giving a virus running under that user's security context pretty much unfettered access to the system, including the MBR. That in a nutshell is the problem of the Windows "unresitricted access" philosophy that  has bitten it badly in recent years.  Vista is a little better and asks for permission when doing potentially damaging things, but that's not totally foolproof either since people get used to just clicking "yeah ok whatever" when the dialog shows, so chances are when the virus triggers that check you'll probably go "Yeah ok whatever" and so the protection will have been illusory.  

Anyway, the way I see, your options to deal with MBR corruption are:
1) Don't run Windows
2) If you have to run Windows, run as restricted user.
3) If you must run as an administrative user, try to do it for as short as possible (like what Ubuntu does really), and/or get a newer version of Windows (Vista).
4) Make a backup of your MBR, and put it on a floppy/CD so you can restore it with an Ubuntu LiveCD.  (For example, the command "sudo dd if=/dev/sda of=~/PartitionTableAndMBR.img bs=512 count=1" will copy the MBR/partition table from /dev/sda into a file in your home directory.)
5) Keep Linux on a seperate drive, with its own MBR that only knows about/boots Linux.  Then put that drive to a secondary postition, and install Windows + Grub onto your primary Windows drive.  Then if the MBR on the primary drive gets damaged for any reason, your Linux drive can still boot independently if you swap the drives around.  

Notwithstanding the above, a clobbered MBR due to a virus is really fairly rare, and can in any case be recovered from without having to go to too much trouble, so you might simply want to not worry too much about it and ignore my suggestions!

Hope that helps.

I like the fifth,but i only have one hard disk...Is it possible to do something similar, like faking that i have two hard disks by not letting any data transfers(between them or just from linux to windows not vice-versa) and each having their own MBR.

---

### Post by cristo-father on 2008-06-13
anyone?

---

### Post by Golem XIV on 2008-06-13
There is no way of protecting any disk in an infected system if the virus writer wants to cause damage, for the simple reason that it can write raw data on any sector of any disk(s) connected to the system, regardless of whether they're encrypted or not or what the file system is.

The solution is prevention:  Be reasonably paranoid, keep a decent AV and firewall running on your Windows system, don't run suspicious software, do periodic AV sweeps both from Windows and Linux and **BACK UP YOUR DATA REGULARLY**.

If you're really paranoid, create a custom LiveCD with antivirus installed and boot and scan from it regularly.  Not really practical, since you would have to create new CDs often in order to keep the virus database updated.

---

### Post by sam_delta on 2008-06-13
just use ubuntu, and stay away from windows as much as posible, if for some reason you get a virus in windows, its VERY rare that the virus will damage your MBR, if your very very very unlucky and get your MBR messed up, you insert your super grub disk, and get everything fixed in less than few mins. everything else will be fine.

you dont need to do anything exotic, just do backups as mentioned before and keep a supergrub disk handy ([www.supergrubdisk.org](www.supergrubdisk.org))

sam

---

### Post by housam on 2008-06-14
Here is how to create a [[COLOR="Red"]_dedicated grub partition _[/COLOR]]("http://www.troubleshooters.com/linux/grub/grubpartition.htm")
You need to create a 10 MB ext3 format partition manually before the install process .

---

### Post by ByteJuggler on 2008-06-14
> **cristo-father said:**
> I like the fifth,but i only have one hard disk...Is it possible to do something similar, like faking that i have two hard disks by not letting any data transfers(between them or just from linux to windows not vice-versa) and each having their own MBR.

No. 

Note also (as others have pointed out) that in principle if a virus has full administrator access to your computer it can in principle do a lot worse than just clobbering your MBR on your boot drive.  So even having a seperate disk is no guarantee against data loss, it only addresses the case of losing your MBR on your primary boot disk.  

Even if you have 2 hard disks, the only way to totally protect your Linux disk from Windows is to disconnect it physically while using Windows.  If you have an e-Sata external disk and you install Linux on that, you can actually make such a setup work without sacrificing any speed due to the disk being external thanks to it being still SATA, but while being easily disconnectable due to being external.

Alternatively as others have said, be as vigilant as you can be, employing a healthy dose of paranoia while using Windows and you'll be fine.

---

### Post by the_doc on 2008-06-14
> **ByteJuggler said:**
> Vista is a little better and asks for permission when doing potentially damaging things, but that's not totally foolproof either since people get used to just clicking "yeah ok whatever" when the dialog shows, so chances are when the virus triggers that check you'll probably go "Yeah ok whatever" and so the protection will have been illusory.  


Not true.  If you log into Vista as the admin then yes, all you have to do is click to confirm.  If on the other hand you log in as a normal user you have to enter the admin password to confirm.

---

### Post by ByteJuggler on 2008-06-14
> **the_doc said:**
> Not true.  If you log into Vista as the admin then yes, all you have to do is click to confirm.  If on the other hand you log in as a normal user you have to enter the admin password to confirm.

Uhmmm, yeah and you know as well as I do that Windows by default puts the default (installation) user (which is what most people will use) into the Administrators group.  Ergo my explanation.  It's better than it was, but not exactly a foolproof solution, for the reasons I explained.  I didn't particularly comment on "normal" users as such, as that's not what tends to be used on Windows systems.

---

### Post by mdpalow on 2008-06-15
> **housam said:**
> I think creating a dedicated grub partition will prevent this from happening .

I think it would be MUCH easier to simply make a back-up of your MBR. See the 'back-up' link in my signature below if you would like a tool that will do this for you. Then if anything happens, you can restore your MBR in all of about 1 second. :)

---

