---
title: "Cannot mount the volume.Unable to mount volume"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Johnnie_Walker on 2008-06-15
I decided to try ubuntu two days ago. Before asking for F1 I must mention that I had GRUB boot problems. openSUSE caused them, when I tested it for my last time :) Fortunately, I repaired the GRUB with *super grub disk*. Although the GRUB was back I am still unable to boot the Winbooz XP. My main NTFS directory containing my important multimedia can't be opened via ubuntu.
[URL=http://www.imagecow.net/content.php?id=11048&owner=]
[IMG]http://www.imagecow.net/preview/000011048.png[/IMG][/URL]
The system directory, containing the Winbooz is not visible for me at all. I've heard that I should have closed my Win properly the last time I did it and do it again, but unfortunately I can't access it :)

I hope there will be any suggestions for the newbie :)

---

### Post by Phoenixzeus on 2008-06-15
Is Windows XP and Ubuntu on the same HDD? If so, are they on different physical partitions or did you use WUBI?

---

### Post by Kronie on 2008-06-15
wow! i got exactly the same problem! i am so glad i am not alone.. so far ive been told that this error occurs because i've shut down xp "improperly" so its like i am opening partition that is in use.. in my case, i fked the partition up, and the only way to recover it is to get some sort of recovery cd such as acronis or partition magic. in ur case, id reccomend you to boot back to xp, and shut it down using start->shut down->shut down. this error might pop because you hypernated your pc, or you just forced the shutdown...
oh, and my xp is on NTFS drive too.. my vista..or what used to be vista drive from same HD mounted perfectly fine.. but eventually i had to format it and use for ubuntu :D

---

### Post by Phoenixzeus on 2008-06-15
Also by "unable to boot" do you mean you'd get a UBV bluescreen or that it doesn't appear in Grub or that if you boot it from GRUB, the Master Boot Record is damaged?

---

### Post by Kronie on 2008-06-15
no, the machine restarts after the windows flag loading screen... am i right? :D
cuz i have exactly the same problem. i cant even boot up to windows partition from grub, nor i can access it through ubuntu.. it worked fine untill i had to use that fixboot thing on it >_< oh, and windows recovery cd cant see the directory with windows on it either(after the fixboot of course)..

---

### Post by Phoenixzeus on 2008-06-15
As machine is booting, (before the XP splash screen) keep pressing F8. You will get a boot selection screen. Highlight "Disable Automatic Restart on System Failure" and then you WILL get a Bluescreen error message :)

---

### Post by Kronie on 2008-06-15
lawl.. unfortunately i cant do that..i have dell mobo >_<

---

### Post by Phoenixzeus on 2008-06-15
Hmm if you can't press F8 on startup, it must be that you have a USB keyboard and the BIOS isn't configured (/ or can't be) to accept USB keyboards on boot :( That's brand name computers for you :)

---

### Post by Kronie on 2008-06-15
yea..i was wondering why i couldnt highlight stuff on ubuntu live cd main menu 0_o. But there are the buttons i can use during very first screen i see when i start my pc..like f12 for selecting from where to boot..and some other button..to select sumthing, that will do sumthing afterall..i think its for bios 0_o

PS: i think we sorta hijacked the thread here 0_o
PSS: but yea, i hate dell.. my next pc will be custom built..by me ;)

---

### Post by Kronie on 2008-06-15
@Johnnie_Walker
just incase you have 2nd spare pc with win..booz running on it, try to connect the hard drive with broken partition to that pc, and see if u can acces it from windows, than do a backup and..well reinstall XP

---

### Post by Stefanie on 2008-06-15
> **Johnnie_Walker said:**
> I decided to try ubuntu two days ago. Before asking for F1 I must mention that I had GRUB boot problems. openSUSE caused them, when I tested it for my last time :) Fortunately, I repaired the GRUB with *super grub disk*. Although the GRUB was back I am still unable to boot the Winbooz XP. My main NTFS directory containing my important multimedia can't be opened via ubuntu.
[URL=http://www.imagecow.net/content.php?id=11048&owner=]
[IMG]http://www.imagecow.net/preview/000011048.png[/IMG][/URL]
The system directory, containing the Winbooz is not visible for me at all. I've heard that I should have closed my Win properly the last time I did it and do it again, but unfortunately I can't access it :)

I hope there will be any suggestions for the newbie :)

i read somewhere that you can "fix" the ntfs volume with this command:

```
sudo ntfsfix /dev/sda1 
```
replace sda1 according to your windows partition, of course. i have never used this command and i don't know if it involves any risks... someone suggested it in another topic and it worked to solve the problem, so i wrote it down.

---

### Post by bumanie on 2008-06-15
Before you can do ntfsfix, you need to install ntfsprogs > sudo apt-get install ntfsprogs The you can ntfsfix <your device name> (eg, /dev/sda1 ; /media/sda1 or whatever your device is called). You could also follow the command line input given on the error message and force mount the drive. Nothing is guaranteed, but force mounting, usually doesn't do harm.

---

### Post by Johnnie_Walker on 2008-06-15
> **Phoenixzeus said:**
> Is Windows XP and Ubuntu on the same HDD? If so, are they on different physical partitions or did you use WUBI?
In general, I have 5 partitions on 1 HDD: two NTFS s*ckers :) (one system and one dir), two ext partitions and one swap.

No blue or whatever screen appears, mates. It just doesn't run and teh GRUB reloads. Just help me backup my important media and I promise and won't Winbooz any more :d

---

### Post by Johnnie_Walker on 2008-06-15
> **Stefanie said:**
> i read somewhere that you can "fix" the ntfs volume with this command:

```
sudo ntfsfix /dev/sda1 
```
replace sda1 according to your windows partition, of course. i have never used this command and i don't know if it involves any risks... someone suggested it in another topic and it worked to solve the problem, so i wrote it down.
I am not sure, that it wont harm any system files.

---

### Post by bumanie on 2008-06-15
I know of users who have used ntfsfix to allow mounting of usb devices. Can anyone guarantee no file loss - not 100%, but as far as I know, no-one has lost files doing this. Refer to my post re installing ntfsprogs first, otherwise ntfsfix won't work - ntfsfix is part of the ntfsprogs project. Otherwise force mount as suggested by the error message.

---

### Post by hopelessone on 2008-06-15
Option 1 : boot into windows and do a chkdsk
Option 2 : Do what it says force mount..(@ ur own risk)
Option 3 : Boot into repair console of windows CD and run chkdsk

I've had Option 2 without probs...but still...

---

### Post by Johnnie_Walker on 2008-06-15
> **hopelessone said:**
> Option 1 : boot into windows and do a chkdsk
Option 2 : Do what it says force mount..(@ ur own risk)
Option 3 : Boot into repair console of windows CD and run chkdsk

I've had Option 2 without probs...but still...
If it regards me, it doesn't help. ;) I've mentioned, that no boot from GRUB menu is possible. I believe some configuring stuff and scripts from the console would help me start the XP or make possible browsing NTFS partitions. However, an expert is needed in this case :)

---

### Post by Johnnie_Walker on 2008-06-15
> **bumanie said:**
> Before you can do ntfsfix, you need to install ntfsprogs  The you can ntfsfix <your device name> (eg, /dev/sda1 ; /media/sda1 or whatever your device is called). You could also follow the command line input given on the error message and force mount the drive. Nothing is guaranteed, but force mounting, usually doesn't do harm.
You convinced me to try this, but 'command was not found' :(

---

### Post by Kronie on 2008-06-16
@Stefanie, bumanie
OMG! you guys! thank you! THANX A LOT! its working again! zomg!!! god bless u!
*cries*
@Johnnie_Walker
heres a step-by-step tut for u :)
1) ```
sudo apt-get install ntfsprogs 
```
2) ```
sudo ntfsfix /dev/sda5
``` (heres the problem, stephanie wrote "sudo ntfsfix /dev/**sda1**", but in your case its sda5(for me it was sda2). thats why the 'command was not found'! :) 
3) enjoy! :D

no credit goes for me :P

---

### Post by Johnnie_Walker on 2008-06-16
> **Kronie said:**
> @Stefanie, bumanie
OMG! you guys! thank you! THANX A LOT! its working again! zomg!!! god bless u!
*cries*
@Johnnie_Walker
heres a step-by-step tut for u :)
1) ```
sudo apt-get install ntfsprogs 
```
2) ```
sudo ntfsfix /dev/sda5
``` (heres the problem, stephanie wrote "sudo ntfsfix /dev/**sda1**", but in your case its sda5(for me it was sda2). thats why the 'command was not found'! :) 
3) enjoy! :D

no credit goes for me :P
And no success for me as well :P 
```
usr@usr:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libzzip-0-13 libboost-regex1.34.1 libmagick++10
  libboost-program-options1.34.1 python-bittorrent bittorrent
  libboost-iostreams1.34.1 libboost-filesystem1.34.1 rblibtorrent1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed:
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 391kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://bg.archive.ubuntu.com hardy/main libntfs10 2.0.0-1ubuntu2 [122kB]
Get:2 http://bg.archive.ubuntu.com hardy/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 391kB in 0s (1604kB/s) 
Selecting previously deselected package libntfs10.
(Reading database ... 132120 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
usr@usr:~$ sudo ntfsfix /dev/sda5
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.

```

But...still: "You are not privileged blah-blah."

---

### Post by Kronie on 2008-06-16
> Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.
i think it means that it was successfully repaired 0_o cuz i got exactly same message, and i am now backing up the drive to format it.. have u tried to mount it? it wont appear on desktop by itself.. you need to go to places->whatever drive that was broken..

srry didnt finish reading ur post. 
try
```
sudo mount /dev/sda5
```
or if that wont help try to open it as a root. 
```
sudo nautilus
```
this will open up a root file browser..

---

### Post by Johnnie_Walker on 2008-06-16
> **Kronie said:**
> 
```
sudo mount /dev/sda5
```

You can't imagine how grateful I am. It finally worked that way. I guess I must buy you a beer wherever you are :)

P.S: The only thing left is to make my C(Windows) drive visible and format it.

---

### Post by Kronie on 2008-06-16
its good to know i can be helpful :P
k to format it(the easiest way)
```
$ sudo apt-get install gparted 
$ sudo gparted
```thats ubuntu partition manager(the one thats on live cd)
right click on your xp partition->format to->whatever you want(ext*, fat, ntfs blablabla) just make sure u backed up all nececerry files!
and to make c drive visible.. wait. shouldnt it be on ur desktop after you mount it? 0_o

---

### Post by Johnnie_Walker on 2008-06-16
> **Kronie said:**
> 
and to make c drive visible.. wait. shouldnt it be on ur desktop after you mount it? 0_o
Nope. I mentioned it somewhere, that C isn't visible at all from the beginning.

---

### Post by tsharky87 on 2008-11-21
Yes, I've been having issues mounting my external NTFS drive for quite some time and I've checked several forums and nothing helped. I scanned the drive for errors and it came back OK. In the end, all I had to do to mount it was install ntfsprogs and mount it using ntfsmount and it worked perfectly with no errors.

---

### Post by aysiu on 2008-11-21
> **tsharky87 said:**
> Yes, I've been having issues mounting my external NTFS drive for quite some time and I've checked several forums and nothing helped. I scanned the drive for errors and it came back OK. In the end, all I had to do to mount it was install ntfsprogs and mount it using ntfsmount and it worked perfectly with no errors.
Why are you reviving this old thread?

---

