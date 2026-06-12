---
title: "[SOLVED] GRUB and configuration for MS systems"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by vprasaj on 2008-10-19
Hi,

I have ben trying to solve this for two days. Google is not on my side. So, my last hope is here...

**I have installed Vista. Now I can't boot XP or vista.**

Before vista installation I had installed (all booted normaly):
Linux Mint (its basically ubuntu)
PClinuxOS
Windows XP
OSX (just to try it)

IDE drive
sda: GRUB
sda1 winXP
sda5 pclinuxos
sda6 linux mint

sdb: darwin boot loader
sdb1 osx
sdb2 ext3 data

sdc: / (will install vista boot loader)
sdc1 ntfs (will install vista)
sdc2 ntfs
sdc5 ext3 home
sdc6 swap

**When I decided to install Vista, I disabled sda in BIOS. Just to preserve GRUB and bootloader.**

**Installed, booted from sdc. Vista works.**

Then I enabled and booted from sda, where GRUB is. I booted to linux and added vista to menu.lst:
```
title Vista
root (hd2,0)
savedefault
chainloader +1
```

Then I tried to boot to vista. No go. **Even XP won't boot. The same error.**

```
Windows Failed to start. A recent hardware or software change might be the cuase.

File: \BOOT\BCD
Status: 0xc000000F
Info: An error occurred while attempting to read the boot configuration data.
```

**Vista boots from sdc if I set it as boot disk.**

What am I doing wrong? What is the connection with XP and vista?

(What is the point of so complicated boot loader in vista? Grub and lilo are simply superior.)

---

### Post by bumanie on 2008-10-19
Not sure how much I can help as I know nothing about darwin bootloader what-so-ever, but I just triple booted vista/xp/intrepid ibex beta. Vista was pre-installed. In brief the steps I took to get vista/xp working together.

1. Vista came pre-installed.
2. Shrunk vista's partition with vista's shrink function.
3. Booted gparted (via live intrepid cd) and created new ntfs partition.
4. Installed xp on this partition. 
5. Repaired vista's bootloader with vista repair cd. 
6. Got easybcd bootloader from neosmart and added xp to vista's bootloader.
7. Upon boot, got the choice of booting vista or xp.
8. Installed ubuntu as per usual. Grub is installed to the mbr and has a pointer to vista - choose vista - get the option as noted in point 7 or of course, one is able to boot straight into ubuntu from the grub screen.
I suspect you have to use something like easybcd bootloader to get xp/vista working together. You will probably have to have vista's boot files added to xp's bootloader, seeing xp was installed first and presumably was seen by grub.
Hope this may guide you in the right direction. Not sure how a similar process will work seeing you 'disabled' sda whilst vista was installed - may work OK if easybcd can configure xp and vista.

---

### Post by Bucky Ball on 2008-10-19
See if this makes any difference:

```
title           Windows Vista
root            (hd2,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd2)
map (hd2) (hd0)
```... in menu.lst
You can also try:

```
title           Windows Vista
rootnoverify            (hd2,0)
savedefault
makeactive
chainloader     +1

```Another possibility is super grub disk:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

[quote=vprasaj]
(What is the point of so complicated boot loader in vista? Grub and lilo are simply superior.)[/quote]

One reason is that Windoze needs to be tricked into thinking it is on first drive/first partition. Simply bizarre.

---

### Post by caljohnsmith on 2008-10-19
It sounds suspiciously like your XP install was modified by the Vista install even though you disabled sda in BIOS. How about posting the following to help clarify your setup:
```
cat /boot/grub/menu.lst
sudo umount /dev/sda1
sudo umount /dev/sdc1
```
Don't worry about any "not mounted" errors from the last two commands, that is only to make sure before proceeding:
```
sudo mkdir -p /media/sda1 /media/sdc1
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sdc1 /media/sdc1
ls -l /media/sda1 /media/sdc1

```
And note "-l" is a lowercase L, not a one.

---

### Post by vprasaj on 2008-10-19
Thank you for quick replay. We are making progress. Now I can boot vista but not XP.

**@bumanie**
Good tip. Looks promising. Thank you. I will try to fix this relation vista/XP with EasyBCD. I think it is possible to boot from GRUB to vista botloader and there to choose vista or XP. 
But this will be my last choice. I would like to configure GRUB to go directly to XP or vista.

**@Bucky Ball**
_I tried both options and firs worked_ (second won't in my case).
```
title           Windows Vista
root            (hd2,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd2)
map (hd2) (hd0)
```
I was surprised and my smile went from ear to ear. :D Thank you.

I tried the same for XP (with/without/together map and rootnoverfy), but none worked.

Is it posible that something was changed in boot sector on XP partition?

**@caljohnsmith**
```
 cat /boot/grub/menu.lst
```

```
default		0
gfxmenu=/etc/grub/message.elyssa
timeout		10
color cyan/blue white/blue

#####################
##Options and such...
#####################

title		Linux Mint, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-19-generic

title		Linux Mint, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda6 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-19-generic

##################
##Older kernels...
##################


title		Linux Mint, kernel memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP SP3
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# on /dev/sda1
title		Windows VISTA SP1
root		(hd2,0)
savedefault
makeactive
chainloader	+1
map (hd0) (hd2) #sugested by Bucky Ball
map (hd2) (hd0) #sugested by Bucky Ball

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		PClinuxOS 2007 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz BOOT_IMAGE=PClinuxOS_2007 root=/dev/hda5 acpi=on splash=silent vga=788 
initrd		(hd0,4)/boot/initrd.img
savedefault
boot

title MAC OS X x86 10.4.9
root (hd1,0)
chainloader +1

```

For windows partition I will display original folders. I hope it is ok...

```
ls -l /media/WIN_XP/ /media/WIN_VISTA/
/media/WIN_VISTA/:
skupno 2403701
-rwxrwx--- 1 root plugdev         24 2006-09-18 23:43 autoexec.bat
drwxrwx--- 1 root plugdev       4096 2008-10-18 23:14 Boot
-rwxrwx--- 1 root plugdev     333203 2008-07-17 14:56 bootmgr
-rwxrwx--- 1 root plugdev       8192 2008-10-18 23:14 BOOTSECT.BAK
-rwxrwx--- 3 root plugdev         10 2006-09-18 23:43 config.sys
drwxrwx--- 1 root plugdev          0 2006-11-02 14:00 Documents and Settings
-rwxrwx--- 1 root plugdev     171136 2007-03-17 12:41 grldr
drwxrwx--- 1 root plugdev          0 2008-10-19 09:52 NST
drwxrwx--- 1 root plugdev          0 2008-10-18 13:44 NVIDIA
-rwxrwx--- 1 root plugdev 2460831744 2008-10-19 16:31 pagefile.sys
drwxrwx--- 1 root plugdev          0 2008-07-17 15:13 PerfLogs
drwxrwx--- 1 root plugdev       4096 2008-10-19 16:22 ProgramData
drwxrwx--- 1 root plugdev       8192 2008-10-19 08:42 Program Files
drwxrwx--- 1 root plugdev          0 2008-10-18 13:31 $Recycle.Bin
drwxrwx--- 1 root plugdev       4096 2008-10-19 11:08 System Volume Information
drwxrwx--- 1 root plugdev       4096 2008-10-18 13:29 Users
drwxrwx--- 1 root plugdev      16384 2008-10-19 16:25 Windows

/media/WIN_XP/:
skupno 1036
-rwxrwx--- 2 root plugdev    549 2008-10-19 09:13 boot.ini
-rwxrwx--- 2 root plugdev    550 2008-09-01 20:47 boot.ini.bak
-rwxrwx--- 1 root plugdev 438840 2006-11-02 10:53 bootmgr
-rwxrwx--- 1 root plugdev   8192 2007-10-06 00:49 BOOTSECT.BAK
drwxrwx--- 1 root plugdev   4096 2008-05-14 13:16 Documents and Settings
-rwxrwx--- 1 root plugdev 171136 2007-03-17 12:41 grldr
-rwxrwx--- 1 root plugdev      0 2006-10-31 22:25 IO.SYS
-rwxrwx--- 1 root plugdev      0 2006-10-31 22:25 MSDOS.SYS
-rwxrwx--- 1 root plugdev  47564 2004-08-04 00:38 NTDETECT.COM
-rwxrwx--- 1 root plugdev 250048 2008-09-01 20:56 ntldr
drwxrwx--- 1 root plugdev  57344 2008-10-06 18:53 Program Files
drwxrwx--- 1 root plugdev      0 2008-10-18 13:31 $RECYCLE.BIN
drwxrwx--- 1 root plugdev      0 2006-11-01 06:48 RECYCLER
drwxrwx--- 1 root plugdev   4096 2007-06-30 13:00 System Volume Information
drwxrwx--- 1 root plugdev  61440 2008-10-14 20:22 WINDOWS
 
```

Vista was installed yesterday ( 2008-10-18 ).

[B]Now I can boot vista, but still not XP which worked before vista was instaled.

Guys, you are great.

Any ideas how to fix that with XP too?[/B]

---

### Post by Bucky Ball on 2008-10-19
A wild guess but have you tried:

```
title           Windows XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1


```... and you are most welcome. Glad it worked. :)

---

### Post by caljohnsmith on 2008-10-19
> **vprasaj said:**
> 
```
/media/WIN_XP/:
skupno 1036
-rwxrwx--- 2 root plugdev    549 2008-10-19 09:13 boot.ini
-rwxrwx--- 2 root plugdev    550 2008-09-01 20:47 boot.ini.bak
[COLOR="Red"]-rwxrwx--- 1 root plugdev 438840 2006-11-02 10:53 bootmgr[/COLOR]
-rwxrwx--- 1 root plugdev   8192 2007-10-06 00:49 BOOTSECT.BAK
drwxrwx--- 1 root plugdev   4096 2008-05-14 13:16 Documents and Settings
[COLOR="Red"]-rwxrwx--- 1 root plugdev 171136 2007-03-17 12:41 grldr[/COLOR]
-rwxrwx--- 1 root plugdev      0 2006-10-31 22:25 IO.SYS
-rwxrwx--- 1 root plugdev      0 2006-10-31 22:25 MSDOS.SYS
-rwxrwx--- 1 root plugdev  47564 2004-08-04 00:38 NTDETECT.COM
-rwxrwx--- 1 root plugdev 250048 2008-09-01 20:56 ntldr
drwxrwx--- 1 root plugdev  57344 2008-10-06 18:53 Program Files
drwxrwx--- 1 root plugdev      0 2008-10-18 13:31 $RECYCLE.BIN
drwxrwx--- 1 root plugdev      0 2006-11-01 06:48 RECYCLER
drwxrwx--- 1 root plugdev   4096 2007-06-30 13:00 System Volume Information
drwxrwx--- 1 root plugdev  61440 2008-10-14 20:22 WINDOWS
```

Glad Vista is booting OK now (good call Bucky Ball :)); from the above output though, you have Vista's "bootmgr" boot file in your Windows XP partition, so Vista did indeed modify your Win XP partition. You can go ahead and delete that file. Also, I see you've been playing with Grub4DOS, because you have the glrdr boot loader in your XP root directory too; I hope your boot.ini is OK since you obviously modified it at one point for Grub4DOS (we may have to check it at some point). 

I would first recommend fixing the XP partition boot sector, because it is likely Vista modified it too. If you boot your Windows XP Install CD, go to the "recovery console", and do both:
```
fixboot 
chkdsk /r
```
And run the chkdsk as many times as it takes until it returns no errors. You may not need to run chkdsk, but it is good insurance at this point. After that, try booting Windows XP with basically your original entry in Grub:
```
title           Windows XP
root            (hd0,0)
makeactive
chainloader     +1
```
And let me know exactly what happens. :)

---

### Post by vprasaj on 2008-10-19
@Bucky Ball
I tried but no luck. Thanx anyway.

@caljohnsmith
I did what you sugested. (it just took me allmost an hour to remember my admin password :) )

But now I can't acces XP partition.

What I did is:
booted to recovery console
Choose option c:\windows (I chacked if this is xp partition and not vista.)

Then I did:
cd .. #to go to c:\
dir   #to be shure the partition is XP
fixboot #messege said it is was fixed
chkdsk /r #messege: "The volume appears to contain one  or more unrecoverable problems."
(tried couple of times)
dir   #messege: "An error occured during directory enumeration."
exit  #reboot

Then I tried to boot from GRUB anyway and I get: #File type unknown, partition type 0x7".

I have SP3 installed but I used XP SP2 boot cd. I think this is not the problem.

I tried to boot again in to recovery console, but now I have only vista option. In vista disk management disk is shown as RAW file system. In Acronis Disk Director is like NTFS with 0MB of fre space. In GParted in linux is locked and suggests chkdsk /f, but I can't access it anywhere.

caljohnsmith, I know this was the most logical think to do. But who knows where I messed up.

Somehow I'm getting strange felling that I don't like MS systems that much. And I didn't like those before. Specially when it has no sense. Recovery console? Now it's just a mess.:confused:

O.K., seriously now.

I can give additional information if needed.

Any idea? (I'm on refresh button :) + google )

---

### Post by caljohnsmith on 2008-10-19
Vprasaj, sounds like XP has some major problems if even chkdsk won't complete successfully. I suppose if I were you, I would try and mount the XP partition in Linux, save all your important files, and reinstall it. How old is the HDD? Hopefully you aren't experiencing a hardware problem. How about first posting:
```
sudo fdisk -lu
```
So we can see what your setup looks like, and be sure to let us know which partitions are XP and Vista.

---

### Post by vprasaj on 2008-10-19
It's like this.

sda1 = XP
sdc1 = vista

```
Disk /dev/sda: 81.9 GB, 81964302336 bajtov
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sektorji of 1 * 512 = 512 bytes
Disk identifier: 0xbc0cbc0c

  Naprava Zagon    Za&#269;etek       Konec     Bloki    Id  Sistem
/dev/sda1   *          63    94140899    47070418+   7  HPFS/NTFS
/dev/sda2        94140900   160071659    32965380    5  Raz&#353;irjen
/dev/sda5        94140963   118720349    12289693+  83  Linux
/dev/sda6       118720416   160071659    20675622   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bajtov
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sektorji of 1 * 512 = 512 bytes
Disk identifier: 0xd8897a2d

  Naprava Zagon    Za&#269;etek       Konec     Bloki    Id  Sistem
/dev/sdb1   *          63    74123909    37061923+  af  Neznano
/dev/sdb2        74123915   625137344   275506715   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bajtov
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sektorji of 1 * 512 = 512 bytes
Disk identifier: 0x35f935f8

  Naprava Zagon    Za&#269;etek       Konec     Bloki    Id  Sistem
/dev/sdc1   *          63    40805099    20402518+   7  HPFS/NTFS
/dev/sdc2        40805103   585537119   272366008+   7  HPFS/NTFS
/dev/sdc3       585537120   620735534    17599207+  83  Linux
/dev/sdc4       620735535   625137344     2200905   82  Linux izmenjalni / Solar
```

HDD is Maxtor 80GB. I boot linux mint, pclinuxos and XP from it. It is old some 5 years but I didn't experience any hardware problems. Now I just booted in to mint. Before executing fixboot in recovery console I was able to mount XP partition in linux and vista.  

Vista boots and works now.

I searched google for this, but no go.

I tried to do shkdsk /f in vista, but I chkdsk is aborted.

[IMG]http://shrani.si/f/m/CZ/4QeN1GaZ/screenshotdev-sda-gparte.png[/IMG]

[IMG]http://shrani.si/f/G/ym/2VuxxT8C/screenshot-podatki-odev-.png[/IMG]

Maybe stupid idea, but... in gparted, can I use repair?

---

### Post by caljohnsmith on 2008-10-19
If your HDD is five years old, then I think having a hardware problem with it is a definite possibility; if you google it, I think you'll see that the "rule of thumb" is that most HDDs are not expected to last past about 5 years. Do you have a HDD diagnostics CD that came with your HDD? I would use that, or if you don't have one, you can use the [Ultimate Boot CD]("http://www.ultimatebootcd.com") which has many HDD diagnostic tools. Let me know if that turns up anything.

---

### Post by vprasaj on 2008-10-19
O.K. I'll try. I'm burning it right now and will be back in couple minutes.

---

### Post by vprasaj on 2008-10-19
I did long and short test with SeaTools. Both passed.
Another one with Salvations. 0 defective.

Should I try that check in gparted?

---

### Post by vprasaj on 2008-10-19
gparted-->check

ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
ERROR(5): Opening '/dev/sda1' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

---

### Post by caljohnsmith on 2008-10-19
That's great that your HDD passed the diagnostic tests, but unfortunately, I don't think there's a good chance of recovering Windows if chkdsk doesn't even work on it. One more thing you could try would be to rebuild the Windows boot sector with testdisk in Ubuntu; even though I'm doubtful it will help, it's worth at least trying since it will only take a minute:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". If you testdisk actually allows you to do that, then see if you can mount the Windows with:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt -o force
```
And if that doesn't give any errors, you should be able to browse the /mnt directory to see your Windows files (although unfortunately, I'm doubtful you will get this far).  

If using testdisk doesn't work, you can use "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover your files off of it if you have anything on it you want to recover, but other than that, I think you're only option now is to reformat it and reinstall Windows. If you want to use photorec, it is also part of the testdisk package:
```
sudo photorec
```
But you'll need a lot of HDD space and time to run photorec, because photorec by default recovers every file it can find. Let me know how it goes. :)

---

### Post by vprasaj on 2008-10-19
**[COLOR="Red"]caljohnsmith... I simply don't know what to say...[/COLOR]**

[SIZE="7"][COLOR="Orange"]IT WORKS!!![/COLOR][/SIZE]

I followed steps you suggested for testdisk. Bootsector was different from the one on the end of partition. I had no problem to restoring it.

Now everything works. I can boot to every system on my computer.

Man, if you would be here I would kiss you. (maby... probably not, but anyway...)

**[SIZE="7"][COLOR="Blue"]Thank you, thank you,...[/COLOR][/SIZE]**

You have made my day.

\\:D/:guitar:[IMG]http://smileyjungle.com/smilies/celebrate8.gif[/IMG] [IMG]http://smileyjungle.com/smilies/celebrate9.gif[/IMG] [IMG]http://smileyjungle.com/smilies/music2.gif[/IMG] [IMG]http://smileyjungle.com/smilies/smiling1.gif[/IMG]

We can go for a beer if you are anywhere near... :)

---

### Post by caljohnsmith on 2008-10-19
I'm absolutely thrilled that testdisk worked, vprasaj, because it was certainly a long shot considering that even chkdsk completely failed. :) Isn't it great that testdisk (open-source software) succeeded where Microsoft's own chkdsk (proprietary software) wouldn't? Somebody should send this thread to Microsoft and watch them squirm and try and explain their way out of this one. 
[CENTER]
================================================
**[SIZE="4"]Final Score:[/SIZE]**
[SIZE="3"]:KS :KS :KS   Open-Source Software: +100   :KS :KS :KS
Microsoft: 0 = [COLOR="Red"]FAIL[/COLOR][/SIZE]
================================================[/CENTER]

Anyway, so glad you didn't have to resort to a complete reinstall; cheers and have fun. :)

---

### Post by Bucky Ball on 2008-10-19
Good news, good tweaking and great work. :)

---

### Post by vprasaj on 2008-10-20
This is something... I saw countless posts all over the net where fixboot did messed up bootsector. The only solution I came across was to use something like r studio to backup data and then recreate partition.

Microsoft totally failed in my case. Now recovery console looks like a joke. 

I still wonder how it was changed in the first place. (Before fixboot and testdisk.) Vista created its own mbr and bootsector on its own disk and partition. Why would vista change bootsector on xp partition on another disk after re-enabling it in BIOS? I didn't use bcd or easybcd to change anything.
This is strange.

But anyway... now everything is in order and works. Both, vista and xp are bootable from GRUB.

Thank you **caljohnsmith**, thank you **Bucky Ball**.

You guys are the best.

Cheers!

---

