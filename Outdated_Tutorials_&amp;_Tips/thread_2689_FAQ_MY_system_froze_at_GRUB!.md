---
title: "FAQ: MY system froze at GRUB!"
date: 2004-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2004-10-30
**Symptoms**
After a Ubuntu install (especially on a dual-boot-with-Windows system), your system will boot to the words GRUB, then freeze shortly thereafter.

After a Ubuntu install on a Dual-boot, Windows freezes while trying to boot

**Cause**
This is due to a difference in hard disk geometry. Windows uses CHS (Cylinder/Head/Sector) numbering for drives in its partition table, while Linux 2.6.x uses LBA (Logical Block Addressing) mode. Linux will write its info in LBA, which windows couldn't read, thus the system freezes. In addition, you may get "mixed" chs and lba, which'll make grub freeze quite effectively!

**Fix**

Download the System rescue CD at [http://www.sysresccd.org](http://www.sysresccd.org) 
-or-
Use Knoppix, Kanotix, or your favorite LiveCD that has the **sfdisk** command and grub.


1. Boot the liveCD
2. Run **sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda**.
3. Run **grub-install (hd0)** to reinstall GRUB.
4. Reboot!

---

### Post by josel on 2004-10-31
Could this maybe explain the following problem i have on a laptop?

Try 1) Windows installed as only system. Therafter i resize the disk with qtparted and install ubuntu with no problems. When i try to boot, Grub hangs on "stage 1_5 install". I dont even get a prompt.

Try 2) All partitions are wiped out and i install ubunto. Everything works OK. Thereafter i install Windows (intending to use systemrescuecd to fix grub thereafter)... it installs OK but i cannot boot neither XP nor ubuntu. REstoring grub does not help.
Im only capable of booting from the XP cd if there is unformatted diskspave left. if i have an ext3 and ntfs partition the cd will not boot (i find this weird).

I have tryed other combinations with no succes, so if someone recognises the symptoms i have and has had succes with the above solution i will give it another try , or else its XP on that laptop  :?

---

### Post by jdong on 2004-10-31
[QUOTE=josel]Could this maybe explain the following problem i have on a laptop?

Try 1) Windows installed as only system. Therafter i resize the disk with qtparted and install ubuntu with no problems. When i try to boot, Grub hangs on "stage 1_5 install". I dont even get a prompt.

Try 2) All partitions are wiped out and i install ubunto. Everything works OK. Thereafter i install Windows (intending to use systemrescuecd to fix grub thereafter)... it installs OK but i cannot boot neither XP nor ubuntu. REstoring grub does not help.
Im only capable of booting from the XP cd if there is unformatted diskspave left. if i have an ext3 and ntfs partition the cd will not boot (i find this weird).

I have tryed other combinations with no succes, so if someone recognises the symptoms i have and has had succes with the above solution i will give it another try , or else its XP on that laptop  :?[/QUOTE]

Sounds like this will fix it. It's a safe procedure, unless your partition table is so borked that fdisk can't interpret it.

---

### Post by josel on 2004-11-02
Well, i took a different aproach and tryed with a Knoppix harddisk install intending to upgrade it to debian unstable. I was surprised that writing the bootmanager to mbr didnt cause any problems. So now i can boot both Windows  and Knoppix. Knoppix 3.6 installed LILO and i had previously tryed with LILO from Ubuntu with no success. 

Has my laptop triggered a bug in the Ubuntu installer?

I use a Fujitsu Siemens  Amilo 1425 with XP Home.

---

### Post by jdong on 2004-11-02
No, it's more of a Linux 2.6/Windows interaction. Knoppix uses kernel 2.4. LiLO seems less affected by this bug; even with an inconsistent partition table it'll boot.

---

### Post by Verlager on 2004-11-03
These are the instructions?

1. Boot the liveCD (ok)

2. Run sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda.
[COLOR=Red][OK, but it asks for the --force option because it considers the params to be out of bounds and/or rediculous][/COLOR]

3. Run grub-install (hd0) to reinstall GRUB.

[SIZE=4]This is the correct syntax?[/SIZE] ---> **grub-install (hd0)**  

**[COLOR=YellowGreen]I don't believe that.  I never heard of parenthesis on a Linux command line. What is the real syntax, assuming installing to hd0?[/COLOR]**

4. Reboot!

---

### Post by jdong on 2004-11-06
[QUOTE=Verlager]These are the instructions?

1. Boot the liveCD (ok)

2. Run sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda.
[COLOR=Red][OK, but it asks for the --force option because it considers the params to be out of bounds and/or rediculous][/COLOR]

3. Run grub-install (hd0) to reinstall GRUB.

[SIZE=4]This is the correct syntax?[/SIZE] ---> **grub-install (hd0)**  

**[COLOR=YellowGreen]I don't believe that.  I never heard of parenthesis on a Linux command line. What is the real syntax, assuming installing to hd0?[/COLOR]**[/quote]

Yes, those are the instructions. Sometimes you need the force option, but not always.

Yes, #3 is correct. Please read the man page for grub-install. Quoted:

> 
 INSTALL_DEVICE can be a GRUB device name or a system device filename.

---

### Post by Verlager on 2004-11-06
[QUOTE=jdong]**Symptoms**
After a Ubuntu install (especially on a dual-boot-with-Windows system), your system will boot to the words GRUB, then freeze shortly thereafter.

**Fix**

Download the System rescue CD at [http://www.sysresccd.org](http://www.sysresccd.org) 
-or-
Use Knoppix, Kanotix, or your favorite LiveCD that has the **sfdisk** command and grub.

1. Boot the liveCD
2. Run .
3. Run **grub-install (hd0)** to reinstall GRUB.
4. Reboot![/QUOTE]Note that there are two parts to the sfdisk cli: **[COLOR=Sienna]sfdisk -d /dev/hda[/COLOR] | [COLOR=DarkOrange]sfdisk --no-reread -H255 /dev/hda[/COLOR]** [SIZE=3]Where does the --force option go?[/SIZE]

Also, after:  Run **sfdisk -d /dev/hda | sfdisk --no-reread -H255 /dev/hda**

I ran:  **cfdisk /dev/hda** 

_I got an error message:_
[COLOR=Red]
[B]Fatal error: Bad primary partition 1: partition ends in the final partition cylinder. 
Press  any key to exit cfdisk.[/B][/COLOR]

and **grub-install (hd0) **
just gave an wonderful error message **zsh: unknown file attribute** in the latest System Rescue CD (a gentoo subset, I believe)

---

### Post by jdong on 2004-11-07
Force goes in the second half of the command.

---

### Post by HungSquirrel on 2004-11-22
After trying this FAQ, I believe the correct syntax is **grub-install hd0**, without the parentheses.

At any rate, I have had no luck fixing GRUB.  I simply need to re-install it so I can boot Ubuntu again.  (I installed Windoze on my Fat partition so I could play HL2, and of course NTLDR was happy to overwrite GRUB.)

When I issue the grub-install command in a root shell on Knoppix 3.4, I get the following:

```
root@ttyp0[knoppix]# grub-install hd0
mkdir: cannot create directory `/boot/grub': Read-only file system
```

Same if I give it a Unix device name.

```
root@ttyp0[knoppix]# grub-install /dev/hda
mkdir: cannot create directory `/boot/grub': Read-only file system
```

It is trying to rebuild a /boot dir on the Knoppix CDROM, which of course it cannot do.

I have tried chrooting into my Ubuntu install, but doing grub-install that way gave me other errors.

```
root@ttyp0[knoppix]# chroot /mnt/hdb3 /bin/bash
root@Knoppix:/ # grub-install /dev/hda
/sbin/grub-install: line 1: sort: command not found
/sbin/grub-install: line 1: uniq: command not found
/sbin/grub-install: line 1: expr: command not found
/sbin/grub-install: line 429: /dev/null: Permission denied
/sbin/grub-install: line 431: /dev/null: Permission denied
```

Those binaries are located in /usr, but for some reason I was not allowed to mount my /usr in the chrooted shell.

```
root@Knoppix:/ # mount /usr
mount: block device /dev/hdb5 is write-protected, mounting read-only
mount: cannot mount block device /dev/hdb5 read-only
```

It does this even though the partitions are not mounted according to Knoppix's /etc/mtab.

I've tried everything I can think of.  I seek help from someone much smarter than I.   8-)


Edit: fixed, with an unbelievably complicated mount.  I booted the Ubuntu install disk, and after my partitions had been detected, switched to tty2 and did the following:

```
mkdir foo
mount /dev/ide/host0/bus0/target1/lun0/part3 foo
chroot foo /bin/bash
mount /usr
grub-install /dev/hda
```

/dev/ide/host0/bus0/target1/lun0/part3 is /dev/hdb3 in normal Linux land.  That's the most confusing device name I have ever seen.   ](*,)

---

### Post by zenwhen on 2004-11-24
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

Did you try these instructions? Perhaps your issue is that you are not specifying a root, thus it is using your current root.

---

### Post by johnmc on 2005-07-17
even if it's a bit old it still did the trick on my hoary Installation fixing my boot problem with WinXP

Thanks!

---

### Post by wouter78 on 2006-08-13
I see the last message is posted about a year ago, but for those that accidentally came here: getting grub back when you reinstalled Windows is even simpler than stated.
Boot the LiveCD (Ubuntu or almost any other), type:
> sudo grub(in Ubuntu, for other distro's: become root and type: grub)
Now you are at het grub commandline, at this commandline run:
> root (hd?,!)
setup (hd0)
quit
Where "?" should be replaced with the number the hard drive Linux is installed on and "!" the number of the partiton is is on.
Note!! Grub starts counting at 0, so /dev/hda3 would be (hd0,2) and /dev/hdb1 (hd1,0). No harm in trying to root several partitions when you don't know what hard disk or partition your install is on. When grub says it has rooted a ext2 or ext3 partition you've most likely found the right one.

---

