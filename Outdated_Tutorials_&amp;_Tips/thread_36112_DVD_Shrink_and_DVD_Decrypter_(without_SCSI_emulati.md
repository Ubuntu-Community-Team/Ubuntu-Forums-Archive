---
title: "DVD Shrink and DVD Decrypter (without SCSI emulation) in wine"
date: 2005-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by mrbass on 2005-05-21
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

credit goes to **jpl** who tipped me off that changing win2k or winxp to **nt40** is all that is required to get DVD Decrypter working **without SCSI emulation** using STPI - Microsoft.

Now I can rip a DVD in 15 mins and burn a DVD in 8 mins with DMA enabled.  Also this keeps dvd players from getting confused with /media/cdrecorder etc....keeps the /media/cdrom.

---

### Post by aragorn2909 on 2005-05-22
Briiliant!  Getting closer everyday to saying good-bye to M$!

---

### Post by SNo0py on 2005-05-22
Great!!!

---

### Post by sonny on 2005-05-22
Good How-To, I've just backed up my first dvd... and it works like a charm... thank you for this... I looking for something under linux, but now with this I won't need it... keep it up...

---

### Post by Bomper on 2005-05-23
Bravo.

---

### Post by fluideye on 2005-05-23
I am new to DVD shrink, decrypter and wine.  Some where in the process of following the instructions posted here...

> [http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/) 

...I must have chosen to run as Win98.  I don't know if that's what's causing me troubles but I can't select...

>  Make sure in DVD Decrypter Setttings under I/O tab STPI - Microsoft is checked 

...STPI - Microsoft because it's greyed out and I get an error message when running DVD Decryptor that tells me "know device selected"

HelP?

---

### Post by mrbass on 2005-05-24
two things must be true for you to be able to select STPI and for it to find a device.

1) in your [Version] section of .wine/config it must say nt40  not win98, not win2k or winxp.

2) your dosdevice symlinks must be correct.  Did you do the following?
cd .wine/dosdevices
rm d:
ln -s /media/cdrom d:

You can test it by sticking a dvd in your drive and open dvdshrink and click 'Open Disc' it should show you the drive with the volume name of the dvd.

Do you have a dvd-rom and a dvd-burner on your system perhaps? Did you previously have SCSI emulation setup?  If so do the following:
remove ide-scsi from /etc/modules
remove hdd=ide-scsi in kernel line in /boot/grub/menu.lst
and obviously remove your symlink to /media/cdrecorder

---

### Post by ferris55 on 2005-05-24
Hello,

I installed wine following the howto, but when i run winesetup i get this after i clicked finish at th command prompt:

CBase::AutoConf:GetWinInstalls: unable to grep /media/windows/msdos.sys: child process exited abnormally

nowi ignored that and downloaded dvd decrypter, started it up with wine and i get nicely the setup from Dvd Decrypter, then when i get to the window installing, a window appears with the following text:

Error opening file for writing

c:\program files\DVD Decrypter\DVDDecrypter.exe


I solved: it was auto to my excisting windows NTFS partition!!!!


Abort,ignore or Retry


Whats wrong, can anyone help me?

---

### Post by remin on 2005-05-24
*cough*
native ways of dvd backups :)
[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=308](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=308)
[http://developer.berlios.de/projects/lxdvdrip/](http://developer.berlios.de/projects/lxdvdrip/)
*cough*
I'm trying these methods atm, I'll let you know how it goes.

the first method worked flawlessy on ubuntu, takes longer to do the backup compared to dvd decrypter/dvd shrink. Im planning on writing a script to automate this whole process. (btw just use gnome baker instead of k3b as suggested in the guide)

Lxdvdrip on the other was a real pain to get running, works exactly the same, but I wouldnt bother with it.

---

### Post by remmelt on 2005-05-25
I'm wondering... I'm running a clean Hoary, with universe and marillat, But I can't install transcode. This is a known dependency problem. How can you say it works flawlessly? What's your secret?

(In short: transcode depends on libvorbis0 which was replaced with libvorbis0a...)

---

### Post by remin on 2005-05-25
[QUOTE=remmelt]I'm wondering... I'm running a clean Hoary, with universe and marillat, But I can't install transcode. This is a known dependency problem. How can you say it works flawlessly? What's your secret?

(In short: transcode depends on libvorbis0 which was replaced with libvorbis0a...)[/QUOTE]

 :| You've got me there, I can't remember how I got it to install, just remember I'm very new to linux.
But here's proof:
[http://img.photobucket.com/albums/v443/_sentinel/Screenshot.png](http://img.photobucket.com/albums/v443/_sentinel/Screenshot.png)
Also my repositories are definetly more "expanded" than just universe and marillat.
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

deb http://backports.ubuntuforums.org/ubp hoary-backports bleeding main universe multiverse restricted
deb http://backports.ubuntuforums.org/ubp hoary-extras  bleeding main universe multiverse restricted
deb http://backports.ubuntuforums.org/ubp hoary-backports-staging bleeding main universe multiverse restricted
deb http://backports.ubuntuforums.org/ubp hoary-extras-staging bleeding main universe multiverse restricted

# Typical file to track testing while keeping eye on unstable

# Standard Debian binary archives in USA
deb http://ftp.us.debian.org/debian/ stable main non-free contrib
#deb http://ftp.us.debian.org/debian/ testing main non-free contrib
#deb http://ftp.us.debian.org/debian/ unstable main non-free contrib
# Standard Debian binary archives in non-USA
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
#deb http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free
#deb http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free

# Standard Debian source archives in USA
#deb-src http://ftp.us.debian.org/debian/ testing main non-free contrib
#deb-src http://ftp.us.debian.org/debian/ unstable main non-free contrib
# Standard Debian source archives in non-USA
#deb-src http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
#deb-src http://non-us.debian.org/debian-non-US testing/non-US main contrib non-free
#deb-src http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free

# Security Debian binary archive
deb http://security.debian.org/ stable/updates main contrib non-free
# Security Debian source archive
#deb-src http://security.debian.org/ stable/updates main contrib non-free

#Cinelerra archives
deb http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/ ./

```
As you can see I'm definetly not scared of breaking my ubuntu, so sad though, can't get unstable from the debian site to work properly :(
Also I do believe Properties|Force Version played a part in getting this to work.

All in favor of me writing a HOWTO on how the hell I got this to work say I (once I remember myself :P)

---

### Post by carney1979 on 2005-05-25
After following this procedure and failing, I did or checked the following:

[QUOTE=mrbass]two things must be true for you to be able to select STPI and for it to find a device.

1) in your [Version] section of .wine/config it must say nt40  not win98, not win2k or winxp.

2) your dosdevice symlinks must be correct.  Did you do the following?
cd .wine/dosdevices
rm d:
ln -s /media/cdrom d:

You can test it by sticking a dvd in your drive and open dvdshrink and click 'Open Disc' it should show you the drive with the volume name of the dvd.

Do you have a dvd-rom and a dvd-burner on your system perhaps? Did you previously have SCSI emulation setup?  If so do the following:
remove ide-scsi from /etc/modules
remove hdd=ide-scsi in kernel line in /boot/grub/menu.lst
and obviously remove your symlink to /media/cdrecorder[/QUOTE]

DVD Shrink will show the DVD when I click on the 'Open Disc' button.

But DVD Decrypter still gives me an 'No Devices Detected' error in the source box.

Help!

David

<edit>
Hey all: Once I pulled my head out and ACTUALLY CAREFULLY READ the instructions I saw a key step I had missed at first. 

It all works as claimed, and works well, I might add.

---

### Post by fluideye on 2005-05-25
> two things must be true for you to be able to select STPI and for it to find a device.

1) in your [Version] section of .wine/config it must say nt40 not win98, not win2k or winxp.

2) your dosdevice symlinks must be correct. Did you do the following?
cd .wine/dosdevices
rm d:
ln -s /media/cdrom d:
 

I've done this and am able to select STPI, but  when I try and open DVD Decryptor I am getting a wine error of "1" and unable to open.

Any ideas?

---

### Post by mrbass on 2005-05-25
wine --version
what is yours?  mine is 20050310

cat /etc/fstab
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
```

ls -l .wine/dosdevices/
```

lrwxrwxrwx  1 family family 31 2005-05-06 21:44 c: -> /home/family/.wine/fake_windows
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com1 -> /dev/ttyS0
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com2 -> /dev/ttyS1
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com3 -> /dev/ttyS2
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com4 -> /dev/modem
lrwxrwxrwx  1 family family 12 2005-05-21 14:00 d: -> /media/cdrom
lrwxrwxrwx  1 family family  8 2005-05-06 21:44 d:: -> /dev/hdd
lrwxrwxrwx  1 family family  8 2005-05-06 21:44 lpt1 -> /dev/lp0
lrwxrwxrwx  1 family family  4 2005-05-06 21:44 x: -> /tmp
lrwxrwxrwx  1 family family  9 2005-05-06 21:44 y: -> ../%HOME%
lrwxrwxrwx  1 family family  1 2005-05-06 21:44 z: -> /
 
```

Do yours look similiar?

---

### Post by joekr on 2005-05-26
Has anyone gotten this to work on Ubuntu x86_64?

---

### Post by mrbass on 2005-05-26
one guy is using Fedora Core 3 AMD64, kernel 2.6.11 SMP, WINE 20050419 and can't get any device detected. 

Another guy is using LFS 2.6.11, SMP, WINE 20050419 and says it detects it but only if the dvd is mounted. A third guy says same thing only if it's mounted it'll detect the device Gentoo 2.6.12-rc4 WINE lastest CVS version.

So I think it's not the kernel, nor SMP.....64-bit...could very well be.  Could just be getting wine to compile in 64-bit.

---

### Post by synaptic revolt on 2005-05-27
I've followed everything in this thread, but neither dvd decrypter nor shrink can see any drives.

What am I doing wrong?

---

### Post by mrbass on 2005-05-27
post the following:

cat /etc/fstab

wine --version

ls -l .wine/dosdevices

---

### Post by synaptic revolt on 2005-05-28
[QUOTE=mrbass]post the following:

cat /etc/fstab

wine --version

ls -l .wine/dosdevices[/QUOTE]

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/windows  ntfs    umask=0222      0       0
/dev/hdb5       /media/flyingdog  ntfs    umask=0222      0       0
```

Wine 20050310

lrwxrwxrwx  1 yoonix yoonix 10 2005-05-27 13:22 c: -> ../drive_c
lrwxrwxrwx  1 yoonix yoonix 13 2005-05-27 13:40 d: -> /media/cdrom0
lrwxrwxrwx  1 yoonix yoonix  4 2005-05-27 13:22 e: -> /tmp
lrwxrwxrwx  1 yoonix yoonix 23 2005-05-27 13:23 f: -> /home/yoonix/.winetools
lrwxrwxrwx  1 yoonix yoonix 12 2005-05-27 13:22 h: -> /home/yoonix
lrwxrwxrwx  1 yoonix yoonix  4 2005-05-27 13:22 t: -> /tmp
lrwxrwxrwx  1 yoonix yoonix  1 2005-05-27 13:22 z: -> /


DVD Decrypter and Shrink work, they just don't see any drives. If I enable scsi emulation, decryptor works, but no burning programs work.

---

### Post by mrbass on 2005-05-28
cdrom0 is a DVD-ROM and cdrom1 is DVD burner?
first remove your wine installation and start over
rm -rf .wine/

Now (this is very important and I don't think most bother doing it just glance over it in my guide) but put a dvd in cdrom0 and put a dvd in cdrom1 and then install DVD Decrypter which will create all your /dosdevices symlinks correctly.  

Also someone mentioned some issue with have windows partition wine wanted to install there or something.  Not sure why those with windows even are trying to get dvdshrink and dvddecryptper in linux working unless they're planning to nuke their windows soon.

---

### Post by fluideye on 2005-05-28
[QUOTE=mrbass]Now (this is very important and I don't think most bother doing it just glance over it in my guide) but put a dvd in cdrom0 and put a dvd in cdrom1 and then install DVD Decrypter which will create all your /dosdevices symlinks correctly.[/QUOTE]
What if you only have one dvd/cd drive?

---

### Post by synaptic revolt on 2005-05-28
[QUOTE=mrbass]cdrom0 is a DVD-ROM and cdrom1 is DVD burner?
first remove your wine installation and start over
rm -rf .wine/

Now (this is very important and I don't think most bother doing it just glance over it in my guide) but put a dvd in cdrom0 and put a dvd in cdrom1 and then install DVD Decrypter which will create all your /dosdevices symlinks correctly.  

Also someone mentioned some issue with have windows partition wine wanted to install there or something.  Not sure why those with windows even are trying to get dvdshrink and dvddecryptper in linux working unless they're planning to nuke their windows soon.[/QUOTE]

I believe cdrom0 is my dvd burner, and cdrom1is my cdrw. I did have a dvd in the drive when installing decrypter, but I'll try it again. Also, I'm using winetools to setup wine, the normal wineconfig doesn't make any wine directories or anything.

I'm not using it under windows because I can't get grub to boot the windows partition, and anyway I'd rather get this working because I don't want to go back to windows if I can help it.

---

### Post by fluideye on 2005-05-28
[QUOTE=mrbass]wine --version
what is yours?  mine is 20050310

cat /etc/fstab
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
```

ls -l .wine/dosdevices/
```

lrwxrwxrwx  1 family family 31 2005-05-06 21:44 c: -> /home/family/.wine/fake_windows
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com1 -> /dev/ttyS0
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com2 -> /dev/ttyS1
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com3 -> /dev/ttyS2
lrwxrwxrwx  1 family family 10 2005-05-06 21:44 com4 -> /dev/modem
lrwxrwxrwx  1 family family 12 2005-05-21 14:00 d: -> /media/cdrom
lrwxrwxrwx  1 family family  8 2005-05-06 21:44 d:: -> /dev/hdd
lrwxrwxrwx  1 family family  8 2005-05-06 21:44 lpt1 -> /dev/lp0
lrwxrwxrwx  1 family family  4 2005-05-06 21:44 x: -> /tmp
lrwxrwxrwx  1 family family  9 2005-05-06 21:44 y: -> ../%HOME%
lrwxrwxrwx  1 family family  1 2005-05-06 21:44 z: -> /
 
```

Do yours look similiar?[/QUOTE]
mine:
cat /etc/fstab/
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0

```
ls -l .wine/dosdevices/
```
total 0
lrwxrwxrwx  1 corey corey 12 2005-05-24 08:38 c: -> /media/cdrom
lrwxrwxrwx  1 corey corey 12 2005-05-24 08:47 d: -> /media/cdrom
lrwxrwxrwx  1 corey corey  8 2005-05-23 16:49 d:: -> /dev/hdc
lrwxrwxrwx  1 corey corey  4 2005-05-21 16:02 e: -> /tmp
lrwxrwxrwx  1 corey corey 22 2005-05-21 16:02 f: -> /home/corey/.winetools
lrwxrwxrwx  1 corey corey 11 2005-05-21 16:02 h: -> /home/corey
lrwxrwxrwx  1 corey corey  4 2005-05-21 16:02 t: -> /tmp
lrwxrwxrwx  1 corey corey  1 2005-05-21 16:02 z: -> /

```

---

### Post by mrbass on 2005-05-29
@fluideye
remove the c: symlink in dosdevices
cd .wine/dosdevices
rm c:

Why are you guys using winetools?  That's not in my guide.  I specifically say install winesetuptk then run winesetup.

---

### Post by synaptic revolt on 2005-05-29
[QUOTE=mrbass]@fluideye
remove the c: symlink in dosdevices
cd .wine/dosdevices
rm c:

Why are you guys using winetools?  That's not in my guide.  I specifically say install winesetuptk then run winesetup.[/QUOTE]


Because otherwise nothing can install, there's no fake_windows, no drive_c, etc. How do I get them installed without it?

Following the guide to the letter I get

```
Error opening file for writing:

C:\Program Files\DVD Decrypter\DVDDecrypter.exe

Abort, Retry, Ignore
```

---

### Post by mrbass on 2005-05-29
This is from the guide
> 
sudo apt-get update
sudo apt-get install wine winesetuptk

 winesetup Just press NEXT twice, then FINISH

Running winesetup creates the .wine/fake_windows, etc.  Your dosdevices symlinks will be created as soon as you insert a DVD and setup DVD Decrypter for the first time.


Now you have a windows dual boot ntfs partition so maybe you have to specifically tell it not to install there but rather to your ext3 home directory instead since NTFS is not writable.
/dev/hda5       /media/windows  ntfs    umask=0222

---

### Post by synaptic revolt on 2005-05-30
[QUOTE=mrbass]This is from the guide

Running winesetup creates the .wine/fake_windows, etc.  Your dosdevices symlinks will be created as soon as you insert a DVD and setup DVD Decrypter for the first time.


Now you have a windows dual boot ntfs partition so maybe you have to specifically tell it not to install there but rather to your ext3 home directory instead since NTFS is not writable.
/dev/hda5       /media/windows  ntfs    umask=0222[/QUOTE]

ahh, everything works now. I was telling winesetup to use my old windows drive. DURR


Thank you so much!

---

### Post by iammike on 2005-05-30
My problem doesn't seem to have been ran into yet.

Everything seems to work as far as seeing my DVD drive, accessing it, etc.  All looks well except this.

You know the window that pops up when it wants you to select a directory?  That one just has "Desktop" listed and won't let me expand it to select anything else.  If it's trying to have me select a file, it works fine.

This happens in both programs.  A good way to see what I'm talking about is in DVD Shrink.

Click on the Open File button and in that window where I should be able to expand the directory tree...it just won't do it so I can't actually complete the whole process.

Tips?

---

### Post by mrbass on 2005-05-31
dvdshrink in wine 
open disc image (rip to .iso)
open disc (insert dvd and rip decrypt with dvdshrink)

open files (does not work in wine)
if you wish to rip all files to hd
wine .wine/fake_windows/Program\ Files/DVD Shrink\DVDShrink.exe D:\MOVIE\VIDEO_TS

the above path is from my head so most likely not 100% correct but you get the idea.

---

### Post by SNo0py on 2005-06-01
[QUOTE=mrbass]
open files (does not work in wine)
[/QUOTE]Yeah, which is a bit bad - but you can just open the disc directly anyways... in my opinion it should not be too hard to fix the file-select dialog... maybe someone could raise this bug to the wine-developers? Or maybe we just need the right DLL?

btw, another problem, the startup time of DVDShrink is very slow - after running the command "wine DVD\ Shrink.exe" it takes more than two minutes until DVDshrink shows up, the same applies for DVD Decrypter. Any ideas?

---

### Post by mrbass on 2005-06-01
Not sure why yours opens in two minutes.  DVD Shrink and DVD Decrypter opens immediately.  You got me stumped there.

btw, Lightning UK said he's gonna make an option to 'select drives' so in the next version most likely win2k and winxp should work with dvddecrypter without scsi emulation.
[http://forum.doom9.org/showthread.php?t=91078&page=3]("http://forum.doom9.org/showthread.php?t=91078&page=3")

---

### Post by Jergar on 2005-06-03
[QUOTE=mrbass]Not sure why yours opens in two minutes.  DVD Shrink and DVD Decrypter opens immediately.  You got me stumped there.

btw, Lightning UK said he's gonna make an option to 'select drives' so in the next version most likely win2k and winxp should work with dvddecrypter without scsi emulation.
[http://forum.doom9.org/showthread.php?t=91078&page=3]("http://forum.doom9.org/showthread.php?t=91078&page=3")[/QUOTE]
 Today I tried ExactAudioCopy and it works great, just enable nt40 as my "windows" and in winesetup added all my drives. Next DVDShrink ;-)

Jergar

---

### Post by Jergar on 2005-06-03
DVDShrink and Decrypter are working like a charme ;-)

Jergar

---

### Post by bonifacio on 2005-06-08
mount displays:
[INDENT]/dev/hdc on /media/cdrom0 type udf (ro,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrecorder type udf (ro,nosuid,nodev,sync,uid=1000,gid=1000,umask=007,iocharset=utf8 )[/INDENT]
hdc is dvd rom
scd0 is usb dvd burner

How do I enabled dma on the burner? Again this is a **USB** device not an IDE.

---

### Post by knathraak on 2005-06-09
So I guess by now most of you have heard about the motion picture cartel's takedown of dvd decrypter:
[http://slashdot.org/article.pl?sid=05/06/06/1822211]("http://slashdot.org/article.pl?sid=05/06/06/1822211")

This is truly sad news.:cry:
[pours an ounce on the curb for lightning uk]

Anybody know an any emerging alternatives? Particularly native to linux? One major feature that dvd decryptor has that no other program seemed to master was the ability to deal with sony's ACROS (i think?) copy protection. While your current downloaded and installed versions of the program will continue to work for the time being, expect to see further "innovation" with regard to non-standard dvd-video encoding schemes (ie copy protection).

---

### Post by bonifacio on 2005-06-09
I STILL do not know how to enable DMA on a USB device.  But went ahead and follow the instruction to a T.

Decrypter cannot see the USB DVD burner using [COLOR=Blue]STPI[/COLOR].  However it detects the DVD ROM.

Using [COLOR=Red]ASPI[/COLOR] it detects the USB DVD burner but not the DVD ROM.

What is the difference anyway between STPI vs ASPI?

So reverted the interface to STPI.  To test I rip to ISO using Decrypter and pass the image to Shrink for further compression.  Then I used nautilus burning support (growisofs) to write the image to my burner.

Not the most convenient alternative but it works.

Here is my fstab:
[FONT=Courier New]
[SIZE=1]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,user_xattr,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

# User addition ---------------------------------------------------------------
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
[/SIZE][/FONT]

---

### Post by T.M on 2005-06-10
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

Gives me no howto just words of wisdom....

Could someone give me url-into howto document ???

---

### Post by knathraak on 2005-06-10
[QUOTE=T.M][http://mrbass.org/linux/ubuntu/dvdshrink/]("http://mrbass.org/linux/ubuntu/dvdshrink/")

Gives me no howto just words of wisdom....

Could someone give me url-into howto document ???[/QUOTE]

Looks like he's redirecting all requests to the website to a moment of silence for Lightning UK, maker of dvd decrypter, since he (lightning UK) got kicked in the charlies by the movie cartel (see a few posts above). Truly a sad day...

Don't know if he's removed the instructions to avoid a similar fate, or if this is temporary only.

---

### Post by knathraak on 2005-06-10
Better search google and print out google cache before it's gone....

---

### Post by sbassett on 2005-06-11
[QUOTE=knathraak]Better search google and print out google cache before it's gone....[/QUOTE]
 Either today or tomorrow I will be posting the contents (including all files) in a tarball on my server. I will post the url, AS LONG AS there are no objections from the Moderators.

---

### Post by slade_slater on 2005-06-15
Used this on a prev. installation--very cool guide, thank you mrbass!

---

### Post by mrbass on 2005-06-15
[QUOTE=sbassett]Either today or tomorrow I will be posting the contents (including all files) in a tarball on my server. I will post the url, AS LONG AS there are no objections from the Moderators.[/QUOTE]
apologize for downtime but it was due to legality of dvdderypter.  Long story...no need to worry though about other guides.

---

### Post by i3dmaster on 2005-06-15
this is so wonderful! I made it work. Thanks very much for the howto!!

---

### Post by craft47 on 2005-06-18
[QUOTE=ferris55]

Error opening file for writing

c:\program files\DVD Decrypter\DVDDecrypter.exe


I solved: it was auto to my excisting windows NTFS partition!!!!


Abort,ignore or Retry


Whats wrong, can anyone help me?[/QUOTE]

I have an NTFS partition as well.  So, WHERE is DVDDecrypter supposed to be installed?

I've never tried to use wine before so I'm kind of lost! ](*,)

---

### Post by craft47 on 2005-06-18
oops ok I managed to setup the fake_windows, but now when I try to download dvd decrypter, I  get:

NSIS Error:

Error writing temporary file. Make sure your temp folder is valid.

And in the error log it says:

"Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels to set the screen resolution and remove the "Resolution" entry in the config file."

Which doesn't seem to have much to do with the download problem.

Anyone got any ideas?

---

### Post by mrbass on 2005-06-18
go back about 20 posts or so...I don't know...and read synaptic revolts post.  You can't install it to a windows partition.  In a nutshell install it to ~/fake_windows/ instead of c:\program files\
when I say "it" I'm referring when you run winesetup

---

### Post by joekr on 2005-06-19
I have successfully installed and executed DVD Decrypter via a 32bit chroot on a x86_64 system :D

[Picture](http://onfinite.com/libraries/498148/f48.jpg)

---

### Post by craft47 on 2005-06-21
getting wine setup isn't the problem.  I have fake_windows all setup just fine.  The problem is that I can't download DVDDecrypter.  I get 

NSIS Error:

Error writing temporary file. Make sure your temp folder is valid.

---

### Post by mrbass on 2005-06-22
so your telling me
cd ~/.wine/
ls -al
it shows
/fake_windows
like I said install it to your linux partition not your NTFS partition. NTFS is not writable in linux only fat32 and hfs+. (don't some wise guy say captive)

---

### Post by manicka on 2005-06-22
mrbass,
your guide is excellent. I'd been unable to get these apps running in SuSE for some time, but this how-to for Ubuntu is spot-on and just makes me happier about my decision to switch distros  :grin:

---

### Post by lucascr on 2005-06-22
mrbass, is it possible to install DVD shrink and DVD decrypter using Crossover Office and not wine? I have Crossover Office installed and I would like to use it (above all it is based on wine). If I install Wine it will conflict with Crossover Office?
Thanks,

luca

---

### Post by fastb on 2005-06-22
I keep getting aspi error. It detects my dvd drive but aspi error keeps apearing.
I modified config file but it doesn't change anything.
What should I do?

---

### Post by pelon42004 on 2005-06-22
I alreay installed wine but when I try to open dvd shrink i get the following.

nvoking /usr/lib/wine/wine.bin DVD Shrink 3.2.exe ...
wine: cannot find 'DVD Shrink 3.2.exe'
Wine failed with return code 1

Please help

---

### Post by craft47 on 2005-06-23
[QUOTE=mrbass]so your telling me
cd ~/.wine/
ls -al
it shows
/fake_windows
like I said install it to your linux partition not your NTFS partition. NTFS is not writable in linux only fat32 and hfs+. (don't some wise guy say captive)[/QUOTE]

Yes, the /.wine/fake_windows  is there in my home directory.  When I try to download DVDDEcrypter, I get the dialog box and select open with wine; wine starts and then I get the error

NSIS Error:

Error writing temporary file. Make sure your temp folder is valid.

and can't go any further. If I look in the /tmp folder, the SetupDVDDecrypter file "appears" to be there, but wine doesn't seem to be able to open it up.

I've never used wine before.  I do have Decrypter and Shrink on the XP partition; I  don't suppose there is any way to use wine to run it from there?

---

### Post by knathraak on 2005-06-24
Don't run it directly from the download dialog box. Sounds like firefox (or what ever browser you're running) is saving the file to a temporary directory then attempting to execute it from there. Instead just tell it to save the file to your home folder or where ever, then run it with wine from the command line. like this:

 ```
$ cd /path/to/downloaded/file/
$ wine name_of_file.exe
```

---

### Post by r0ydster on 2005-06-24
Mr. Bass

Just wanted to thank you for the how-to.  I can now finally get rid of my winblows partition.  I only had it for these 2 apps.

Thanks again, and keep up the good work!

Mike

---

### Post by craft47 on 2005-06-24
[QUOTE=knathraak]Don't run it directly from the download dialog box. Sounds like firefox (or what ever browser you're running) is saving the file to a temporary directory then attempting to execute it from there. Instead just tell it to save the file to your home folder or where ever, then run it with wine from the command line. like this:

 ```
$ cd /path/to/downloaded/file/
$ wine name_of_file.exe
```[/QUOTE]

Thank you for the reply.  Unfortunately it still doesn't install!  I got the same error plus this error on the command line:

$ wine SetupDVDDecrypter_3.5.4.0.exe
Invoking /usr/lib/wine/wine.bin SetupDVDDecrypter_3.5.4.0.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
Wine failed with return code 2


There's something wrong with the resolution and this prevents me from installing?? ](*,) 

I'm not sure I understand how to fix this.  Is it something in the config file I need to change?

Help oh help, I'm SOOOO confused!!!!!!!   Somebody give me a clue (or a brain transplant!)

---

### Post by edemark on 2005-06-26
[QUOTE=craft47]Thank you for the reply.  Unfortunately it still doesn't install!  I got the same error plus this error on the command line:

$ wine SetupDVDDecrypter_3.5.4.0.exe
Invoking /usr/lib/wine/wine.bin SetupDVDDecrypter_3.5.4.0.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
Wine failed with return code 2


There's something wrong with the resolution and this prevents me from installing?? ](*,) 

I'm not sure I understand how to fix this.  Is it something in the config file I need to change?

Help oh help, I'm SOOOO confused!!!!!!!   Somebody give me a clue (or a brain transplant!)[/QUOTE]
 Hi all 

I followed the guide by mrbass with the small difference that i changed to nt40 before running DVD decripter. Thus it installs flawlessly. However when i try to install dvdshrink i got the following error: 
[email]mark@supernova:~/.wine[/email]$ WINEDLLOVERRIDES="riched=n"
[email]mark@supernova:~/.wine[/email]$ wine dvdshrink32setup.exe
Invoking /usr/lib/wine/wine.bin dvdshrink32setup.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:font:load_VDMX Failed to retrieve vTable
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
Wine failed with return code 130

I guess that the logpixel issue can be resolved commenting out one line. But still i get the second part of the error message.

Any idea? 
pls help 
thanks in advance

---

### Post by Mercury on 2005-06-28
I seem to be having the same trouble as craft47  :?

I have installed DVD Shrink fine, and have been using it for about 6 months, so I know that my wine install is fine. However, I tried to install DVD Decypter today, but when I run:

#> wine SetupDVDDecrypter_3.5.4.0.exe

I get an error box appear saying "Error writing temporary file. Make sure your temp folder is valid."

I have tried running it as root also, with no luck. 

It has nothing to do with the resolution problem; that is in fact an ignorable warning as DVD Shrink works fine while the resolution warning appears.

I tried setting "Temp" = "/tmp" in my ~/.wine/config file but that didnt help. I also tried setting my temp folder to various other locations and none would work  :mad: 

I also tried updating to the latest wine install, which still didnt help.

Any ideas what the problem is with the temp directories?

---

### Post by dtessier on 2005-06-28
[QUOTE=edemark][email]mark@supernova:~/.wine[/email]$ WINEDLLOVERRIDES="riched=n"
[email]mark@supernova:~/.wine[/email]$ wine dvdshrink32setup.exe
Invoking /usr/lib/wine/wine.bin dvdshrink32setup.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:font:load_VDMX Failed to retrieve vTable
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
Wine failed with return code 130[/QUOTE]

What you want to run is ```
WINEDLLOVERRIDES="riched=n" wine dvdshrink32setup.exe
``` all on the same line, or alternatively ```
export WINEDLLOVERRIDES="riched=n"
wine dvdshrink32setup.exe
```

---

### Post by mrbass on 2005-06-30
[QUOTE=dtessier]What you want to run is ```
WINEDLLOVERRIDES="riched=n" wine dvdshrink32setup.exe
``` all on the same line, or alternatively ```
export WINEDLLOVERRIDES="riched=n"
wine dvdshrink32setup.exe
```[/QUOTE]

that's clearly in the guide...some just fail to read it.  When I get emails about it I don't bother replying anymore...can't help some people.

---

### Post by SNo0py on 2005-06-30
[QUOTE=mrbass]that's clearly in the guide...some just fail to read it.  When I get emails about it I don't bother replying anymore...can't help some people.[/QUOTE]
You are so right!

---

### Post by Mercury on 2005-06-30
[QUOTE=Mercury]... when I run:

#> wine SetupDVDDecrypter_3.5.4.0.exe

I get an error box appear saying "Error writing temporary file. Make sure your temp folder is valid." .....
[/QUOTE]

I managed to get round this by running the setup program through an old version of winex  (now called cedega) to install it, however, you could easily install it on windows. Basically just copy the program's files from its Program Files/.... directory to a directory on your linux box, then you can run it with wine fine.  :grin: 

wine will happily run the program, it just seems that it sometimes has trouble with the installer.

---

### Post by markdone on 2005-07-13
I have followed the guide "to the letter" as everyone has said many times, and everthing appears to be working.  ISO's are ripped, compressed, and burned without any error messages, but my computer shows the disk as blank (ejected and reinserted) and my DVD player won't load the disk.  The disk has been burned on (I can see the color difference) and looks like every other burned DVD I have made (complete burn).  I tried burning the ISO with Nautilus and it worked (for now), but I would like to know why DVD Decrypter's successful burns aren't working.  Any ideas of what is going on?  Great HOWTO mrbass, hopefully I can figure out this error.

Mark

---

### Post by sizzam on 2005-07-14
[QUOTE=craft47]getting wine setup isn't the problem.  I have fake_windows all setup just fine.  The problem is that I can't download DVDDecrypter.  I get 

NSIS Error:

Error writing temporary file. Make sure your temp folder is valid.[/QUOTE]

I was getting this error as well.   To fix it, I wiped out my current wine config and reconfigured:  

```
 
$ rm -rf .wine

```
(don't do that if you have any important info in there that you don't want to delete).

After that, I ran:

```

$ winesetup

```

From that point, you click Next/Next/Finish and should be able to follow the guide.

---

---

### Post by dolson on 2005-07-19
With the latest version of Wine, the .wine/config file is no longer used, but instead the registry files. They ship a crappy EXE utility called winecfg since we can't use winesetuptk anymore. I can't get it to properly work now. This is one of the reasons I've always hated Wine and WineX - things change too much, to the point of breakage.

---

### Post by MBro on 2005-08-02
I'm unable to preview the video files in DVD Shrink.  Is anyone else having this problem?  I followed the instrctions on Mr. Bass' site to the T and yet nothing.

---

### Post by mrbass on 2005-08-04
Just like to chime in here and say it's a crapshoot with the new wine.  I haven't tried it myself but once the new ubuntu is out in october I'll redo the guide and hopefully be able to get most, if not all, of it working again with the new wine version.

---

### Post by seethru on 2005-08-19
[QUOTE=mrbass]Just like to chime in here and say it's a crapshoot with the new wine.  I haven't tried it myself but once the new ubuntu is out in october I'll redo the guide and hopefully be able to get most, if not all, of it working again with the new wine version.[/QUOTE]
 I can't seem to select STPI, it's greyed out. I've changed the windows version to nt40, d: is linked to /media/cdrom1 (my dvd-rom), and DMA is enabled.

---

### Post by knathraak on 2005-08-29
Can't get new wine (in breezy universe 20050628) to work right with spti in dvd decrypter.

Upgraded to the new wine.  Bunch of stuff broke so I deleted my entire .wine directory :-( .  After setting up with the newfangled winecfg, things were happier.

Setting emulation (either global or per app), to nt40, enables the spti option, but under that option no cd drives are detected.  Under the plain winaspi32.dll option ONLY my firewire dvd-rw is detected, not my two atapi drives, hda & hdc.  Hey at least I have one drive working--it could be worse, I guess.

Anybody else have luck with the breezy wine?

---

### Post by mrbass on 2005-08-30
If I do get breezy working fine with the new wine in October/September I'll be sure to offer the current version of wine and keep it on my webpage as we've seen the wine development is  crazy (or so it appears as of late).  Also I suppose we'll have to pin our version of wine so it's not upgraded during a apt-get update.

---

### Post by knathraak on 2005-08-30
[QUOTE=mrbass]as we've seen the wine development is  crazy (or so it appears as of late). [/QUOTE]

Yes it is. But I have to say, I think wine is getting really good. A couple of years ago, it wasn't much more than a novelty. Now, for me at least, it's actually a viable solution in some instances.

Wine does appear to be getting...ahem...better with age....

---

### Post by makisupa123 on 2005-08-31
This al seems to work well....except I need to resize the fake_windows directory.  It shows it around 4 GB and I'd like it to be able to hold 8.5 GB.  Any ideas?

Thanks

/mak

---

### Post by kanem on 2005-08-31
[QUOTE=makisupa123]This al seems to work well....except I need to resize the fake_windows directory.  It shows it around 4 GB and I'd like it to be able to hold 8.5 GB.  Any ideas?[/QUOTE]The size of the fake_windows directory should only be limited by the size of the partition it's in. So to get more room for fake_windows you'll have to either resize the partition or redo the Wine setup and have it put fake_windows in a larger partition.

---

### Post by makisupa123 on 2005-09-01
Thanks Kanem ---Guess I should have deleted a couple isos before i tried another.  It just seemed like such a coincidence...remaining space being exactly what can fit on a single-layer DVD. 

/mak

---

### Post by kanem on 2005-09-17
[QUOTE=knathraak]Anybody else have luck with the breezy wine?[/QUOTE]
Not really, but if you go [here](http://packages.ubuntu.com/hoary/libs/libwine) to download Hoary's libwine and [here](http://packages.ubuntu.com/hoary/otherosfs/wine) to get wine it'self you can uninstall Breezy's libwine and wine and reinstall Hoary's. Everything should be back to normal. And so that future upgrades don't upgrade wine, put this in your /etc/apt/preferences:```
Package: libwine
Pin: version 0.0.200503*
Pin-Priority: 999

Package: wine
Pin: version 0.0.200503*
Pin-Priority: 999

```

---

### Post by arunsub on 2005-09-17
if i try hdparm /dev/hdd I get /dev/hdd: No such file or directory
. I have cdrom, cdrw, dvd, dvdrw under /dev. All those have 0 in dma (hdparm /dev/cdrom etc). I have only one dvd writer. Do i have to enable dma for each one of them (like cdrom, cdrw)? How do i enable?

---

### Post by confused_user on 2005-09-18
Thanks for the guide, unfortunatly i am new to wine and cant make it work.

When run up dvddecryptor it cant see any drives, the reason is becuase "SPTI microsoft" is still greyed out in dvd decryptors settings page.

Yes i have done a 

<rm d:>
<ln -s /media/cdrom d:>

perhaps this might help someone help me

Wine 20050310

my etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs defaults        0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hda6       /stuff          reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

and an ls -l of my dosdevices

lrwxrwxrwx  1 matt matt 29 2005-09-18 09:07 c: -> /home/matt/.wine/fake_windows
lrwxrwxrwx  1 matt matt 10 2005-09-18 09:07 com1 -> /dev/ttyS0
lrwxrwxrwx  1 matt matt 10 2005-09-18 09:07 com2 -> /dev/ttyS1
lrwxrwxrwx  1 matt matt 10 2005-09-18 09:07 com3 -> /dev/ttyS2
lrwxrwxrwx  1 matt matt 10 2005-09-18 09:07 com4 -> /dev/modem
lrwxrwxrwx  1 root root 12 2005-09-18 09:09 d: -> /media/cdrom
lrwxrwxrwx  1 matt matt  8 2005-09-18 09:07 d:: -> /dev/hdb
lrwxrwxrwx  1 matt matt  8 2005-09-18 09:07 lpt1 -> /dev/lp0
lrwxrwxrwx  1 matt matt  4 2005-09-18 09:07 x: -> /tmp
lrwxrwxrwx  1 matt matt  9 2005-09-18 09:07 y: -> ../%HOME%
lrwxrwxrwx  1 matt matt  1 2005-09-18 09:07 z: -> /

i sort of had it working to begin with but i messed up abd rm'd d::, so i completely removed wine and started again and now cant get spti to enable

I hope this is somthing silly, i certainly feel a bit inadequate seeing as so many other people managed to follow a well written, simple guide ;)

any help would be appreciated
confused_user

---

### Post by confused_user on 2005-09-18
OK, forget it, i hadnt done anythign wrong but i still had a terminal open that was doing somthing (who knows what), so i closed it and then noticed a dvddecryptor short cut on my desktop, clicked on it, now it works ;)

linux eh?

---

### Post by confused_user on 2005-09-18
ok so dvd decryptor seems to working fine, i have just successfully ripped a dvd.

but dvdshrink is not working properly at all, the only way i can get it to run is to install it and then the gui will start, i have made the short cuts as suggested but it errors if itry and start it from the start menu in gnome.

all i really want it to do is to transcode my pre ripped vobs (courtesy of dvd decryptor) and burn them.

so in windows i would usually just navigate to the directory in which these vobs are located.

I cant do this in wine, dvd shrink can see neither my fake windows drives nor my dvd burner.

i have followed the instruction but cant get it work!, please help

oh i did the <WINEDLLOVERRIDES="riched20=n" wine dvdshrink32setup.exe> bit as well.

while i'm on the subject, how would a non programer know that he had to do that? over ride dll's i mean?, i have some other apps i need to get running in wine but have no chance if i have to do anything like that.

many thanks dvd ripping gurus

---

### Post by arunsub on 2005-09-18
[QUOTE=ferris55]Hello,

I installed wine following the howto, but when i run winesetup i get this after i clicked finish at th command prompt:

CBase::AutoConf:GetWinInstalls: unable to grep /media/windows/msdos.sys: child process exited abnormally

[/QUOTE]
I got the same error. how do i solve it? 
Also wine setup shows win98, ME etc but not win XP. How do i make wine to show XP?

---

### Post by Benzima on 2005-09-24
Ok...I pulled a real bonehead move. I was having trouble with SPTI Microsoft section also. I too got ahead of myself and didn't put DVDs in both drives before downloading the setupexe. I did the "ln -s /media/cdrom d:" but still had a problem so trying to be a smart guy I thought maybe it was because my dvdshrink was installed on c: instead of d: so I changed it to 'ln -s /media/cdrom c:' and now I get "NSIS Error" Error writting tempory file. Make sure your temp folder is available"

What should I do?

Can someone also please tell me how to uninstall a program I've previously installed using wine?

Thanxxx in advance.

---

### Post by Eversmann on 2005-09-26
What a great guide!

Thanks for this :-D

I've followed it and changed the config file of wine to "nt40" but when i start dvd decrypter it keeps telling me win98 se.

You know what i'm doing wrong?

Thanks in advance.

---

### Post by confused_user on 2005-09-26
Sorry if you had already thought of these but are you sure that the account you are using has the correct permissions to write to the wine config file?

What text editor are you using and are you sure that you are actually saving your changes? vi can be a bit of a bitch if your not used to it and its easy to exit without saving, same with joe and nano.

if your not sure how to check permissions, just use the root terminal in the gnome applications drop down menu and do it from that terminal, you will then have root permissions (well sort of), see if your changes are saved then.

---

### Post by Eversmann on 2005-09-26
thanks for the reply.

Yeah, all is correct in that. I'm running Wine under a normal user (not root), the changes are made (if i cat the file with cat config | more the changes are there).

I'm using vi as an editor.

wine is in default installation. I only did what is in the guide, change the config file to nt40 and the link at dosdevices to link to the correct drivers.

I've done houndred of test before posting here, i like to search before for an answer ;-)

but it's very weird, i've tried with win2k too after reading at doom9 forums that is the correct set for wine and dvd decrypter.

argh, i want to get rid of windows and only use ubuntu :-D

---

### Post by confused_user on 2005-09-28
i can post my config file if you want?

mine works so you coudl cross reference them.

its a long file so i wont post it unless you ask (dont want to piss anyone off);)

---

### Post by Eversmann on 2005-09-28
Yeah, if you don't mind of course.

Please add your file here and i will compare with mine. Must be something i'm missing.

thanks in advance.

---

### Post by confused_user on 2005-09-28
[COLOR=Red]*Here you go then :D*[/COLOR]

WINE REGISTRY Version 2
;; All keys relative to \\Machine\\Software\\Wine\\Wine\\Config

;; If you think it is necessary to show others your complete config for a
;; bug report, filter out empty lines and comments with
;; grep -v "^;" ~/.wine/config | grep '.'
;;
;; MS-DOS drives configuration
;;
;; Each section has the following format:
;; [Drive X]
;; "Path"="xxx"       (Unix path for drive root)
;; "Type"="xxx"       (supported types are 'floppy', 'hd', 'cdrom' and 'network')
;; "Label"="xxx"      (drive label, at most 11 characters)
;; "Serial"="xxx"     (serial number, 8 characters hexadecimal number)
;; "Filesystem"="xxx" (supported types are 'msdos'/'dos'/'fat', 'win95'/'vfat', 'unix')
;;   This is the FS Wine is supposed to emulate on a certain
;;   directory structure.
;;   Recommended:
;;   - "win95" for ext2fs, VFAT and FAT32
;;   - "msdos" for FAT16 (ugly, upgrading to VFAT driver strongly recommended)
;;   DON'T use "unix" unless you intend to port programs using Winelib !
;; "Device"="/dev/xx" (only if you want to allow raw device access)
;;

[Drive C]
"Path" = "/home/matt/.wine/fake_windows"
"Type" = "hd"
"Label" = "/home/matt/.wine/fake_windows"
"Filesystem" = "win95"

[Drive D]
"Path" = "/media/cdrom0"
"Type" = "cdrom"
"Label" = "/media/cdrom0"
"Filesystem" = "win95"
"Device" = "/dev/hdb"

[Drive X]
"Path" = "/tmp"
"Type" = "hd"
"Label" = "Tmp Drive"
"Filesystem" = "win95"

[Drive Y]
"Path" = "%HOME%"
"Type" = "network"
"Label" = "Home"
"Filesystem" = "win95"

[Drive Z]
"Path" = "/"
"Type" = "hd"
"Label" = "Root"
"Filesystem" = "win95"

[wine]
"Windows" = "C:\\Windows"
"System" = "C:\\Windows\\System"
"Temp" = "X:\\"
"Path" = "C:\\Windows;C:\\Windows\\System;X:\\;X:\\test;Y:\\"
"GraphicsDriver" = "x11drv"
; Wine doesn't pass directory symlinks to Windows programs by default.
; Enabling this may crash some programs that do recursive lookups of a whole
; subdir tree in case of a symlink pointing back to itself.
;"ShowDirSymlinks" = "1"
;"ShowDotFiles" = "1"
"ShellLinker" = "wineshelllink"

# [wineconf]

[Version]
; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win2k3,win20,win30,win31)
"Windows" = "nt40"
; DOS version to imitate
;"DOS" = "6.22"

; Be careful here, wrong DllOverrides settings have the potential
; to pretty much kill your setup.

[DllOverrides]
; some dlls you may want to change
"oleaut32" = "builtin, native"
"ole32" = "builtin, native"
"commdlg" = "builtin, native"
"comdlg32" = "builtin, native"
"shell" = "builtin, native"
"shell32" = "builtin, native"
"shfolder" = "builtin, native"
"shlwapi" = "builtin, native"
"shdocvw" = "builtin, native"
"advapi32" = "builtin, native"
"msvcrt" = "native, builtin"
"mciavi.drv" = "native, builtin"
"mcianim.drv" = "native, builtin"
"msi" = "native, builtin"
; you can specify applications too
; this one will apply for all notepad.exe
;"*notepad.exe" = "native, builtin"
; this one will apply only for a particular file
;"C:\\windows\\regedit.exe" = "native, builtin"
; default for all other dlls
"*" = "builtin, native"

[x11drv]
; Number of colors to allocate from the system palette
"AllocSystemColors" = "100"
; Use a private color map
"PrivateColorMap" = "N"
; Favor correctness over speed in some graphics operations
"PerfectGraphics" = "N"
; Color depth to use on multi-depth screens
;;"ScreenDepth" = "16"
; Name of X11 display to use
;;"Display" = ":0.0"
; Allow the window manager to manage created windows
"Managed" = "Y"
; Use a desktop window of 640x480 for Wine
;"Desktop" = "640x480"
; Use XFree86 DGA extension if present
; (make sure /dev/mem is accessible by you !)
"UseDGA" = "Y"
; Use XVidMode extension if present
"UseXVidMode" = "Y"
; Use XRandR extension if present
"UseXRandR" = "Y"
; Use the take focus protocol
"UseTakeFocus" = "Y"
; Enable DirectX mouse grab
"DXGrab" = "N"
; Create the desktop window with a double-buffered visual
; (useful to play OpenGL games)
"DesktopDoubleBuffered" = "Y"
; Run in synchronous mode (useful for debugging X11 problems)
;;"Synchronous" = "Y"
;
; Use the Render extension to render client side fonts (default "Y")
;;"ClientSideWithRender" = "Y"
; Fallback on X core requests to render client side fonts (default "Y")
;;"ClientSideWithCore" = "Y"
; Set both of the previous two to "N" in order to force X11 server side fonts
;
; Anti-alias fonts if using the Render extension (default "Y")
;;"ClientSideAntiAliasWithRender" = "Y"
; Anti-alias fonts if using core requests fallback (default "Y")
;;"ClientSideAntiAliasWithCore" = "Y"
;

[fonts]
;Read the Fonts topic in the Wine User Guide before adding aliases
;See a couple of examples for russian users below
"Resolution" = "96"
"Default" = "-adobe-helvetica-"
"DefaultFixed" = "fixed"
"DefaultSerif" = "-adobe-times-"
"DefaultSansSerif" = "-adobe-helvetica-"

;; default TrueType fonts with russian koi8-r encoding
;"Default" = "-monotype-arial-*-*-*--*-*-*-*-*-*-koi8-r"
;"DefaultFixed" = "-monotype-courier new-*-*-*--*-*-*-*-*-*-koi8-r"
;"DefaultSerif" = "-monotype-times new roman-*-*-*--*-*-*-*-*-*-koi8-r"
;"DefaultSansSerif" = "-monotype-arial-*-*-*--*-*-*-*-*-*-koi8-r"
;; default cyrillic bitmap X fonts
;"Default" = "-cronyx-helvetica-"
;"DefaultFixed" = "fixed"
;"DefaultSerif" = "-cronyx-times-"
;"DefaultSansSerif" = "-cronyx-helvetica-"

; the TrueType font dirs you want to make accessible to wine

[FontDirs]
;"dir1" = "/usr/X11R6/lib/X11/fonts/TrueType"
;"dir2" = "/usr/share/fonts/truetype"
;"dir3" = "/usr/X11R6/lib/X11/fonts/TT"
;"dir4" = "/usr/share/fonts/TT"

[serialports]
"Com1" = "/dev/ttyS0"
"Com2" = "/dev/ttyS1"
"Com3" = "/dev/ttyS2"
"Com4" = "/dev/modem"

[parallelports]
"Lpt1" = "/dev/lp0"

[ppdev]
;; key:  io-base of the emulated port
;; value : parport-device{,timeout}
;; timeout for auto closing an open device ( not yet implemented)
;"378" = "/dev/parport0"
;"278" = "/dev/parport1"
;"3bc" = "/dev/parport2"

[spooler]
"FILE:" = "tmp.ps"
"LPT1:" = "|lpr"
"LPT2:" = "|gs -sDEVICE=bj200 -sOutputFile=/tmp/fred -q -"
"LPT3:" = "/dev/lp3"

[ports]
;"read" = "0x779,0x379,0x280-0x2a0"
;"write" = "0x779,0x379,0x280-0x2a0"

[Debug]
;"RelayExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"RelayInclude" = "user32.CreateWindowA"
;"RelayFromExclude" = "user32;x11drv"
;"RelayFromInclude" = "sol.exe"
;"SnoopExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"SpyExclude" = "WM_SIZE;WM_TIMER;"

[registry]
;These are all booleans.  Y/y/T/t/1 are true, N/n/F/f/0 are false.
;Defaults are read all, write to Home
; Where to find the global registries
;"GlobalRegistryDir" = "/etc";
; Global registries (stored in /etc)
"LoadGlobalRegistryFiles" = "Y"
; Home registries (stored in ~user/.wine/)
"LoadHomeRegistryFiles" = "Y"
; Load Windows registries from the Windows directory
"LoadWindowsRegistryFiles" = "Y"
; TRY to write all changes to home registries
"WritetoHomeRegistryFiles" = "Y"
; Registry periodic save timeout in seconds
; "PeriodicSave" = "600"
; Save only modified keys
"SaveOnlyUpdatedKeys" = "Y"

[Tweak.Layout]
;; supported styles are 'Win31'(default), 'Win95', 'Win98'
;; this has *nothing* to do with the windows version Wine returns:
;; set the "Windows" value in the [Version] section if you want that.
"WineLook" = "Win98"

[Clipboard]
"ClearAllSelections" = "0"
"PersistentSelection" = "1"

; List of all directories directly contain .AFM files

[afmdirs]
"1" = "/usr/share/ghostscript/fonts"
"2" = "/usr/share/a2ps/afm"
"3" = "/usr/share/enscript"
"4" = "/usr/X11R6/lib/X11/fonts/Type1"

[WinMM]
; Uncomment the "Drivers" line matching your sound setting.

"Drivers" = "wineoss.drv"      ; default for most common configurations
;"Drivers" = "winearts.drv"    ; for KDE
;"Drivers" = "winealsa.drv"    ; for ALSA users
;"Drivers" = "winejack.drv"    ; for Jack sound server
;"Drivers" = "winenas.drv"     ; for NAS sound system
;"Drivers" = "wineaudioio.drv" ; for Solaris machines
;"Drivers" = ""                ; to disable sound
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

[dsound]
;; HEL only: Number of waveOut fragments ahead to mix in new buffers.
;"HELmargin" = "5"
;; HEL only: Number of waveOut fragments ahead to queue to driver.
;"HELqueue" = "5"
;; Max number of fragments to prebuffer
;"SndQueueMax" = "28"
;; Min number of fragments to prebuffer
;"SndQueueMin" = "12"
;; Forces emulation mode (using wave api)
;"HardwareAcceleration" = "Emulation"
;; Sets default playback device (0 - number of devices - 1)
;"DefaultPlayback" = "0"    ; use first device (/dev/dsp)
;"DefaultPlayback" = "1"     ; use second device (/dev/dsp1)
;"DefaultPlayback" = "2"     ; use third device (/dev/dsp2)
;; Sets default capture device (0 - number of devices - 1)
;"DefaultCapture" = "0"        ; use first device (/dev/dsp)
;"DefaultCapture" = "1"        ; use second device (/dev/dsp1)
;"DefaultCapture" = "2"        ; use third device (/dev/dsp2)

[Network]
;; Use the DNS (Unix) host name always as NetBIOS "ComputerName" (boolean, default "Y").
;; Set to N if you need a persistent NetBIOS ComputerName that possibly differs 
;; from the Unix host name. You'll need to set ComputerName in 
;; HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ComputerName\ComputerName, too.
;"UseDnsComputerName" = "N"

#########################################
# Application dependent sections follow #
#########################################

[AppDefaults\\_INS5576._MP\\x11drv]
; Lotus Notes R5 installer
; I'm quite not sure this will run on some other machine than mine, but it 
; can't hurt
"Managed" = "N"
"Desktop" = "N"

[AppDefaults\\nlnotes.exe\\x11drv]
"Desktop" = "800x600"

[AppDefaults\\explorer.exe\\x11drv]
"Desktop" = "800x600"

[AppDefaults\\notes.exe\\DllOverrides]
"msvcrt" = "native"
"msvcrt40" = "native"
"crtdll" = "native"
"imagehlp" = "native"
"rnaph" = "native"

[AppDefaults\\nlnotes.exe\\DllOverrides]
"msvcrt" = "native"
"msvcrt40" = "native"
"crtdll" = "native"
"imagehlp" = "native"
"rnaph" = "native"

[AppDefaults\\nhldaemn.exe\\DllOverrides]
"msvcrt" = "native"
"msvcrt40" = "native"
"crtdll" = "native"
"imagehlp" = "native"
"rnaph" = "native"

# [/wineconf]

---

### Post by Eversmann on 2005-10-04
Thanks a lot for the information, was very useful.

I finally found my problem. Looks like i had enabled the backport repository and when i was doing apt-get i was installing an old version of wine.

Now i've installed a new one, the winetools worked and i have dvd decrypter and shrink doing its "job" ;-)

thanks a lot for the help.

---

### Post by tuka on 2005-10-12
I have the greyed "STPI" option. But I followed the how-to correctly, set up the wine version to nt40, and if I go manually to the directory D: i can list the files on the device. 

tuka@tuka:~$ wine --version
Invoking /usr/lib/wine/wine.bin --version ...
Wine 20050628

[email]tuka@tuka:~/.wine[/email]/dosdevices$ ls -l
total 0
lrwxrwxrwx  1 tuka tuka 14 2005-10-12 12:17 a: -> /media/floppy0
lrwxrwxrwx  1 tuka tuka  8 2005-10-12 12:17 a:: -> /dev/fd0
lrwxrwxrwx  1 tuka tuka 29 2005-10-12 12:17 c: -> /home/tuka/.wine/fake_windows
lrwxrwxrwx  1 tuka tuka 10 2005-10-12 12:17 com1 -> /dev/ttyS0
lrwxrwxrwx  1 tuka tuka 10 2005-10-12 12:17 com2 -> /dev/ttyS1
lrwxrwxrwx  1 tuka tuka 10 2005-10-12 12:17 com3 -> /dev/ttyS2
lrwxrwxrwx  1 tuka tuka 10 2005-10-12 12:17 com4 -> /dev/modem
lrwxrwxrwx  1 tuka tuka 13 2005-10-12 12:17 d: -> /media/cdrom0
lrwxrwxrwx  1 tuka tuka  8 2005-10-12 12:17 d:: -> /dev/hda
lrwxrwxrwx  1 tuka tuka 10 2005-10-12 12:17 f: -> /documents
lrwxrwxrwx  1 tuka tuka  8 2005-10-12 12:17 lpt1 -> /dev/lp0
lrwxrwxrwx  1 tuka tuka  4 2005-10-12 12:17 x: -> /tmp
lrwxrwxrwx  1 tuka tuka  9 2005-10-12 12:17 y: -> ../%HOME%
lrwxrwxrwx  1 tuka tuka  1 2005-10-12 12:17 z: -> /

/dev/hda        /media/cdrom0   iso9660 ro,user,noauto  0       0

any suggestions on what to do? playing with the Version didn't help. The DVD-RW is an ide device so I can't figure out the problem. There is no ide-scsi emulation.

---

### Post by bugsout on 2005-10-14
OK, this is my third attempt,(don't give up on me yet!) and it is with a clean Ubuntu install. I took my time and read every post in this section and then followed Mr. Bass's install guide VERY carefully. DVD Shrink works good. DVD DEcrypter on the other hand gives me these errors upon startup. 1st one; a box pop's up and says,

 I/O Error!
 Device :[0:0:0:] (H:)
 CDB: 12 00 00 00 FC 00
 Interpretation Inquiry
 Reason Invalid Function

I then tried the 2 options in this box which are Retry and Cancel, Retry the same error message, Cancel the box goes away..

 Then,, it looks like everything is OK, but when I try to burn the ISO I get:

  Device IO Control (FSCTL_LOCK_VOLUME) failed
  Device [0:0:0:] Memorex DVD+/-RW True 8x 1.19(D:)
  Unable to lock volume for exclusive access-
  Reason: Invalid Parameter


Any help would be greatly appreciated, my objective is to get M$ off my other HD !

Oh, also upon booting Ubuntu I get a line about 7 or 8 down that says:
 device HDD No such file or directory

thanks again
bugsout.............newbie

---

### Post by bugsout on 2005-10-14
No go, I am very reluctant to go back to windows, but I need to produce some DVD's......

Thanks for everyone's advise and assistance

---

### Post by mrbass on 2005-10-14
[quote=bugsout]Sorry  I think I posted this twice......


Unable to lock volume for exclusive access-

[/quote]
uncheck that setting in dvddecrypter.  Not sure about the other errors.  Main thing is that wine is constantly changing.  Just today I finally downloading 5.10 ubuntu, kubuntu, and edubuntu so I'll give it a spin but if it doesn't work most likely just have to wait for a newer version of wine.

---

### Post by manicka on 2005-10-14
mrbass, any thoughts on getting dvdshrink to work properly in breezy?

---

### Post by Cmdrkeen on 2005-10-23
Okay, I've just upgraded to breezy and after spending 2 days fighting with fglrx I'm on to my next problem. It seems that either something in wine, or one of its dependant libs has changed and now even with the proper settings (per mrbass)  SPTI is greyed out. If anyone has any idea's on this please let me know, otherwise I'm just going to poke at it until I give up or it starts working.

-Keen

---

### Post by manicka on 2005-10-23
[http://www.ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink](http://www.ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink)

---

### Post by jamesroe on 2005-10-24
[QUOTE=mrbass]<snip>  Just today I finally downloading 5.10 ubuntu, kubuntu, and edubuntu so I'll give it a spin but if it doesn't work most likely just have to wait for a newer version of wine.[/QUOTE]

Well, I'm certainly looking forward to that.  I might report my experiences in the hope that they will provide some insight into mere mortals.

With the 'original' how-to, I did manage to follow the guide precisely and get both DVDDecrypter and DVD Shrink to work, sort of.  That is, DVDDecrypter found the dvd burner and could rip dvds.  The 'problem' was, I couldn't tell it where to put the resulting file(s).  It turned out they were in the root of fake_windows.

Then, DVD Shrink would load, appeared to be okay, but I couldn't browse the file system to find the ripped file(s).  I got errors about some missing dll or other.  

I Googled the thing and found a bug report in Wine that said it was fixed, just download and install the newest version of Wine - which I did.  As has been noted, the later version (20050725 - I think there is now a later one?) is quite a bit different in its file structure (drive_c vs. fake_windows for example) and setup (winecfg vs. winesetup) and I had to re-install both DVDDecrypter and DVD Shrink (I saved the old .wine directory to .wine-bak).

Now, DVD Shrink works as it should.  I can navigate the file system, find the ripped file(s), process them and save an .iso image (but cannot burn with DVDDecrypter).  DVDDecrypter cannot find the dvd burner, though.  The log file shows it to find NT 4.0 and that SPCI is working, but no dvd burner (/dev/hdc mounted on /media/cdrom0 in my Hoary system).

I burned the .iso with K3b but cannot rip any new ones, so it is back to Windoze for the time being (I hope).

Jim Roe

---

### Post by BLTicklemonster on 2005-10-26
> 1) Rip the DVD title(s) to harddisk with DVD:RIP in a project folder. This will create VOB files of the chosen title in that folder containing the movie and the soundtrack you picked.

Lmao, nice. Next?



(by that, I mean .. for example:

A ROCKET SCIENTIST'S GUIDE TO GETTING TO THE MOON

Fly a rocket ship in an upwardly manner, oriented towards the Earth's satellite.

the end.

hint: I think if I could get dvd rip to work, I could crap dvds out my bum.
koff koff)

---

### Post by matva on 2005-10-30
i'm trying to follow the guide, but i'm stuck.
i've installed and ran the setup (winesetup), and have download dvddecrypter. However, when i do "open with" i cant find wine (default). ?? When i tried this before i was able to get it over with another version of wine by doing wine DVDDecryptersetup and it worked, but with this wine that command doesnt work. Any suggestions? Also, when i get the programs installed, how do i make links in the applications menu?

---

### Post by MetalMusicAddict on 2005-10-30
[QUOTE=matva]i'm trying to follow the guide, but i'm stuck.
i've installed and ran the setup (winesetup), and have download dvddecrypter. However, when i do "open with" i cant find wine (default). ?? When i tried this before i was able to get it over with another version of wine by doing wine DVDDecryptersetup and it worked, but with this wine that command doesnt work. Any suggestions? Also, when i get the programs installed, how do i make links in the applications menu?[/QUOTE]
Are you using Breezy or Hoary? If your using Breezy installing wine setup will remove WINE. WINE now comes with its own config utility.

The WINE in the Breezy repos dosnt work as well as Hoary. Go to [THIS]("http://ubuntuforums.org/showthread.php?t=81947&highlight=wine") thread and follow the link/read the thread. ;)

---

### Post by bugmenot on 2005-11-27
I finally got DVD Decrypter and DVD Shrink installed and working thanks to the great people here and the MrBass guide.  Also I found another site that helped me:

[http://dhost.info/kpex/guides/dvd-winehowto.html](http://dhost.info/kpex/guides/dvd-winehowto.html)

Pay attention when creating the sym links.  I was using:

$ ln -s /mnt/cdrom d:
$ ln -s /dev/hdc d:

instead I needed to use 

$ ln -s /media/cdrom0 d:
$ ln -s /dev/scd0 d:

To check what your computer is using, in a terminal type:

cat /etc/fstab

that will tell you what to use for your sym links.

Sometimes I have trouble getting DVDDecrypter to recognize a Blank DVD, but GnomeBaker works beautifully I don't really see the need to burn with DVDDecrypter anymore.

I hope this helps someone.  That was my problem.


Later

---

### Post by [pl]ice on 2005-12-21
hi, i'm trying to follow howto using dvd shrink/decryptor, i had no probs under hoary... but here it's a mess!
installing wine (through apt) gives me set of directories, but none of them have the right structure! : dosdevices drive_c system.reg userdef.reg user.reg
in the howto i need to run winesetup, to get the folders correct/config files. but when i install winesetup (have to uninstall wine) the folders change to right thing, but i can't install programs couse i don't have wine then! shits me this thing!
pls help!

---

### Post by manicka on 2005-12-21
[QUOTE='[pl]ice']hi, i'm trying to follow howto using dvd shrink/decryptor, i had no probs under hoary... but here it's a mess!
installing wine (through apt) gives me set of directories, but none of them have the right structure! : dosdevices drive_c system.reg userdef.reg user.reg
in the howto i need to run winesetup, to get the folders correct/config files. but when i install winesetup (have to uninstall wine) the folders change to right thing, but i can't install programs couse i don't have wine then! shits me this thing!
pls help![/QUOTE]

What how-to are you using. The ones given in this thread are for hoary and won't work in breezy.

Try this

[http://ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink+breezy](http://ubuntuforums.org/showthread.php?t=78611&highlight=dvd+shrink+breezy)

---

### Post by [pl]ice on 2005-12-21
interesting :) yeh, i had used the breezy wine , thnx

---

### Post by brodiepearce on 2007-04-20
Last time I tried the guide in the OP worked, but now whenever I try to start DVDShrink it just uses up 100% on the cpu usage, and doesn't actually start, if I start it through terminal it also spews out a massive amount of errors.  DVD Decrypter seems to be working fine though....  In fact... the only thing in the DVD Shrink directory that Wine is executing correctly is the uninstall exe ironically!

Here's a snippet of the errors coming through the terminal:
```

fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:ole:CoGetClassObject class {e30629d1-27e5-11ce-875d-00608cb78066} not registered
err:ole:CoGetClassObject no class object {e30629d1-27e5-11ce-875d-00608cb78066} could be created for context 0x1
err:quartz:GraphBuilder_Connect Unable to create filter (80040154), trying next one
err:seh:setup_exception stack overflow 16 bytes in thread 0009 eip b7d4e48f esp 00230ff0 stack 0x231000-0x340000

```

There is an immense amount of errors, the Terminal doesn't even scroll far enough to display them all to give you an idea of the scale.

---

### Post by mgmiller on 2007-04-23
I just upgraded edgy to feisty and now my dvdshrink gives the exact same error.  It always worked perfectly in dapper/edgy.  I first got an error message saying it couldn't find xvidcore.dll,  so I downloaded that and put it in windows/system and windows/system32.  That is when the massive error messages started.  I hope this gets sorted soon.

---

### Post by brodiepearce on 2007-05-12
> **mgmiller said:**
> I just upgraded edgy to feisty and now my dvdshrink gives the exact same error.  It always worked perfectly in dapper/edgy.  I first got an error message saying it couldn't find xvidcore.dll,  so I downloaded that and put it in windows/system and windows/system32.  That is when the massive error messages started.  I hope this gets sorted soon.

Trust me this is funny... I Ctrl-C'd during the process of the uber long error message to try another fix, and DVD-Shrink opened, I tried it twice to see if I could duplicate the results, and it worked both times!  So this might do as a temporary fix till someone more adept than myself can figure out what's going wrong.  ;)

I had a feeling it might be something to do with permissions within the .wine folder in the Home folder as my emulated cdrom0 drive in dos_devices only had permissions for root as well as some other folders.

---

### Post by mgmiller on 2007-05-12
> Trust me this is funny... I Ctrl-C'd during the process of the uber long error message to try another fix, and DVD-Shrink opened,

I just tried ctrl-c, but all it did was stop the long error message.  DVD Shrink did not open.  Did you put the xvidcore.dll file in?

---

### Post by brodiepearce on 2007-05-14
> **mgmiller said:**
> I just tried ctrl-c, but all it did was stop the long error message.  DVD Shrink did not open.  Did you put the xvidcore.dll file in?

No I just did a straight install with Wine.  If I Ctrl-C as soon as the first error messages start or a distance into the errors it stops and goes to DVD-Shrink... seems you have to time it right though, otherwise yeah it just stops the error messages and nothing happens.

---

### Post by mgmiller on 2007-05-14
Interesting.  I removed the xvidcore.dll file and ran dvd shrink in a terminal.  When I hit ctrl-c, the program popped open, just as you said.  I changed my entry in Main Menu, so it runs in a terminal instead of just executing, so I can use the ctrl-c trick.  Thank you.  Very weird problem, though.  I wonder if there is some command line switch in wine that is now needed to get around this issue.

---

### Post by EnigMattic on 2007-05-15
> **mgmiller said:**
> Interesting.  I removed the xvidcore.dll file and ran dvd shrink in a terminal.  When I hit ctrl-c, the program popped open, just as you said.  I changed my entry in Main Menu, so it runs in a terminal instead of just executing, so I can use the ctrl-c trick.  Thank you.  Very weird problem, though.  I wonder if there is some command line switch in wine that is now needed to get around this issue.

Anyone figured this out yet? Still getting the same problem :-(

---

### Post by mgmiller on 2007-05-16
Yesterday, I went to winehq.org and entered a report about this problem.  Previously, DVD Shrink had been rated gold.  I changed the rating to garbage and gave all the details I could.  I have discovered that even with the ctrl-c trick, often the program is non responsive.   I don't know if the regression is in feisty somewhere or in wine, but clearly, something has gone wrong. .

---

### Post by brodiepearce on 2007-05-22
> **mgmiller said:**
> I don't know if the regression is in feisty somewhere or in wine, but clearly, something has gone wrong. .

Goodonya' for posting the error report, hopefully someone into the nitty gritty details of wine will be able to shed some light on it.

I can say that I was having this same problem running DVDShrink under wine in Dapper.  Albeit I hadn't tried the Ctrl-C trick back then, but it was giving me similar error messages.

---

### Post by mgmiller on 2007-06-06
This bug has persisted through the 0.9.38 version of wine.  They are aware of it and are working on getting it fixed.  I have fixed it for now by uninstalling wine in syaptic, then unchecking the wine repos in the 3rd party tab and after a reload, reinstalling wine from the official Ubuntu version which is 0.9.33.  All is now good.

---

