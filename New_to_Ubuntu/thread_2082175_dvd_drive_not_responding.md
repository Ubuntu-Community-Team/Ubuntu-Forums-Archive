---
title: "dvd drive not responding"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by Yanook on 2012-11-08
Hi there,

Complete newbie/schmuck here, running 12.10, installed libdvdread4, still can't get any useful response from my DVD drive:

I tried to run a command I found on [this forum post]("http://ubuntuforums.org/showthread.php?t=2074472"), but got:

yan@yan-Aspire-5715Z:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
yan@yan-Aspire-5715Z:~$ uname -a
Linux yan-Aspire-5715Z 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux

yan@yan-Aspire-5715Z:~$ cat/var/log/dmesg|egrep'(CD|DVD)'
bash: cat/var/log/dmesg: No such file or directory
egrep(CD|DVD): command not found

Disk is definitely there, as per [this forum]("http://askubuntu.com/questions/47329/discs-in-dvd-drive-not-being-read"):

yan@yan-Aspire-5715Z:~$ sudo lshw -C disk
[sudo] password for yan: 
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-T20N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: WP03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
 
I've installed regionset, tried to run it and get:

yan@yan-Aspire-5715Z:~$ sudo regionset
[sudo] password for yan: 
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
yan@yan-Aspire-5715Z:~$ 

(There was a readable disk in the drive)

I'd really appreciate any help you can give me!:confused:

---

### Post by Terl on 2012-11-08
Is this a movie you are trying to play?  Have you installed libdvdcss?  You need that to play some of the encrypted dvd's

---

### Post by Yanook on 2013-01-06
OK, sorry to have left this post unattended for so long :oops: Yes, indeed, I have installed libdvdcss2, and the rest of the ubuntu restricted extras. The drive responds, very slowly, to audio cds, and to homemade or semi-professional dvds (not as creepy as it sounds, really), but it still won't play most professionally produced dvds. Regionset still can't seem to find the drive, so I have no idea if that is the problem.

Whenever I try to open a dvd in VLA I get:

Playback failure:
DVDRead could not open the disc "/dev/dvd".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.

And yes, I changed that path a bunch of ways, and I disabled menus.:confused:

---

### Post by llamabr on 2013-01-06
You only posted the output, not the thing you typed, which makes it difficult to troubleshoot.

Anyway, try xine for dvd playing.

---

### Post by Yanook on 2013-01-09
Thanks Llamabar, that's really helped. 

OK, I have now discovered that I need to create something called a symlink (symbolic link) to my dvd device.

I found out about this [here]("http://www.tldp.org/HOWTO/DVD-Playback-HOWTO/prep.html") and [here]("http://www.xine-project.org/faq#id673477").

After startup, I  ran:

dyan@yan-Aspire-5715Z:~$ dmesg|grep dvd
[    1.993137] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

Which tells me my device is actually mapped to a scsi bus even though its an IDE drive, none of which I understand. But hey, I'll make a link to it anyway with:

[5~yan@yan-Aspire-5715Z:~$ sudo ln -s -f /dev/sr0 /dev/dvd

OK, so I now have a symlink to my dvd drive, but, guess what? I still get sweet FA. So I check the permissions for the device:

yan@yan-Aspire-5715Z:~$ ls -l /dev/dvd
lrwxrwxrwx 1 root root 8 Jan  9 22:20 /dev/dvd -> /dev/sr0

Which looks fine to me. 

So, the fabled xine says: "There is no plugin available to handle DVD:/ Maybe MRL syntax is wrong or file/stream source doesn't exist" and also "The source can't be read. maybe you don't have enough rights for this..." blah blah blah.

VLC says exactly what it said before.

I am a poor man. I have a Linux system because of this. I cannot afford a TV and a DVD player and a spare Windows system to play my DVDs on. I chose Linux because it was free and open source, not because I did a degree in computing. Can anyone out there help me get this working?

Or is this just a wild goose chase? Are the DVDs I buy legally in shops destined NEVER to work on Linux?

---

### Post by TREESofRIGHTEOUSNESS on 2013-01-09
Hi, I had a very similar problem before, but, I notice one thing in your original post you say you are running 12.10, but that is not what your computer says.  This means you miss-typed something, or you upgraded.  I would like to encourage a fresh install of 12.04 (as long as your data is backed up of course).  I also like to suggest putting your /home directory on a separate partition as well, because it makes reinstalling much easier (all your configs are there and all your docs are there)
I had issues with 12.10 and my dvd drive, but I am using Lubuntu on a really old comp for my dvd player, like you

---

