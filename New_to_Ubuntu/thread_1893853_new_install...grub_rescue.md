---
title: "new install...grub rescue"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by moviebug on 2011-12-11
I have two drives attached to my HTPC.
One is a 500GB drive(for the OS)
2nd one is a 1TB drive
I have tried to install Mythbuntu 11.10 from a Live CD
to the 500GB drive.
Each time I rebooted after the install had finished
it just sat with a flashing prompt.... - 

So I thought it maybe somehow getting itself confused with the two drives.
The 1 TB drive is NTFS formatted...and used for storage.

So I disconnected the 1TB drive and tried one more time to 
reinstall Mythbuntu 11.10 again...
This time it succeeded...
it booted to the desktop okay

So I shutdown and reconnected the 2nd 1TB drive
and now when I reboot it comes up with...

error: no such device: and a long series of numbers and letters

and then it goes to ...grub rescue>
and sits there

I am writing this on my other machine ...
and being a noobie to linux
have no idea how to fix this problem...

I cant just try and re-install Mythbuntu 11.10 again
cause it will go back to the original problem...of not starting correctly.

**Can you help ...??**:confused:
I have the Live CD of Mythbuntu 11.10 

this is putting me right off Linux

---

### Post by raja.genupula on 2011-12-11
the first part will be useful to you

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by moviebug on 2011-12-11
**Re: new install...grub rescue**
 		the first part will be useful to you

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

So you are saying I can boot up from the Mythbuntu 11.10 Live Disc
and use that OS... to access my drives 
and try and fix the 500GB OS drive problem??

---

### Post by raja.genupula on 2011-12-11
oh its my fault

[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by moviebug on 2011-12-11
> **raja.genupula said:**
> oh its my fault

[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)


Thats fine...I follow that...

but at present...if I boot up with only the 500GB drive with Mythbuntu installed
it boots okay...

but if I then go back and reconnect my 2nd drive agian and reboot again
it comes up with the error 
and grub rescue

So obviously somehow the 2nd drive is interfering with a successful boot...
either thru it installing something meant for the OS drive but instead installs 
on the 1TB drive
or uses the 1TB address or something.

I am quite prepared to reinstall the OS again...I mean I have done it 5 times
already..
I just want to fix the issue of why the 2nd drive is causing issues??

---

### Post by westie457 on 2011-12-11
Have you tried to change the boot order of the drives in the BIOS

---

### Post by ashu. on 2011-12-11
hey first boot the mythubuntu without the external harddisk...then when in ubuntu plugin the drive n in terminal type this command

sudo update-grub

n now reboot n try login with the harddisk plugged in might work so try n reply....

---

### Post by moviebug on 2011-12-11
when I type sudo fdisk -l
I get this back...

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07783966

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cdd41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   970743807   485370880   83  Linux
/dev/sdb2       970745854   976771071     3012609    5  Extended
/dev/sdb5       970745856   976771071     3012608   82  Linux swap / Solaris

---

### Post by moviebug on 2011-12-11
So it is seeing the 1TB drive as sda
and the 500GB OS disc as sdb

If I swap the Sata drive connections on the drives
then it should swap the sda and sdb??

I have checked in the BIOS and the 500GB is the drive 
shown after the CD/DVD drive in boot order

Oh and I am now accessing this forum via the Mythbuntu Live disc..and Chrome browser
so I am on the problem machine..

---

### Post by moviebug on 2011-12-11
Then after swapping the sata cables...so the 
500GB becomes sda(instead of sdb)

then I can reinstall Mythbuntu 11.10?

or is there still a problem with the 1TB drive?
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT

whats this HPFS business on the system part of the 1Tb drive?

its supposed to be NTFS..ie formatted under windows 7

---

### Post by moviebug on 2011-12-11
> **ashu. said:**
> hey first boot the mythubuntu without the external harddisk...then when in ubuntu plugin the drive n in terminal type this command

sudo update-grub

n now reboot n try login with the harddisk plugged in might work so try n reply....

I initially installed Mythbuntu with both drives connected to the motherboard...and during the install process
selected the 500Gb drive..which showed as>> sdb
for installing Mythbuntu onto...
but it never booted up correctly..
I tried two further times reinstalling Mythbuntu
with both drives connected

So then I unplugged the 1TB drive from the Motherboard connection
..ie it isnt an external drive
and then reinstalled Mythbuntu
and then rebooted
**and it booted up correctly**

So I then reconnected the 2nd drive(1 TB one) to the motherboard
and rebooted
and that is when I got the error message
and ..grub rescue... prompt

---

### Post by westie457 on 2011-12-11
We should have asked for this earlier.

Go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) follow the instructions to download, run the program and post the RESULTS.TXT here between [CODE] tags by clicking on the #  at the top of the window.

---

### Post by moviebug on 2011-12-11
> **westie457 said:**
> We should have asked for this earlier.

Go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) follow the instructions to download, run the program and post the RESULTS.TXT here between [CODE] tags by clicking on the #  at the top of the window.

How do I extract this zip file under a Live CD?
I have it in a folder on the desktop

---

### Post by moviebug on 2011-12-11
> **moviebug said:**
> How do I extract this zip file under a Live CD?
I have it in a folder on the desktop

Okay I extracted on my other machine 
and transferred using a USB stick..
and have run script in Terminal window

so here is the results.txt file below

---

### Post by moviebug on 2011-12-11
Hope the attachment is able to be opened..??
and provides some useful info...??

I cant look at it here thru anything under the Live CD:)

---

### Post by westie457 on 2011-12-11
You have Grub installed to both hard drives.
> ============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

Personally I am not sure on how remove Grub from one hard drive only. The easy way (read destructive) would be to write a new partition table to sda, however that would also wipe all files off the drive.

The best course of action for you at the moment would be to completely purge Grub from your system and reinstall to sdb only.

For guidance on this read this [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) at least 3 times before committing yourself to any actions.

---

### Post by grahammechanical on 2011-12-11
In my opinion it should not matter whether Mythbuntu is installed on sda or sdb because grub should know where to look for the Linux image to boot.

Examine the file grub.cfg to find out where Grub is expecting to find the Linux image to boot into.

It is File System/boot/grub/grub.cfg.

Look for this line

> ### BEGIN /etc/grub.d/10_linux ###

And then this line

> menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {

This is from the grub.cfg of Mythbuntu that I installed two weeks ago in a fifth partition.

In the lines that follow I see this

> set root='(hd0,msdos8 )'

This is Grub speak for the first hard disk and the eighth partition. I also see this

> root=UUID=9ebf52fc-54ab-4c3a-b862-d0f27fb486b5 ro   quiet splash 

That is telling Grub which partition to find the Mythbuntu Linux image on from its disk UUID.

Try to find out if the disk UUID that Grub is looking for is the same as the disk UUID of the 500GB disk.

As for HPFS see this

[http://support.microsoft.com/kb/100108]("http://support.microsoft.com/kb/100108")


Regards.

---

### Post by moviebug on 2011-12-11
> **westie457 said:**
> You have Grub installed to both hard drives.


Personally I am not sure on how remove Grub from one hard drive only. The easy way (read destructive) would be to write a new partition table to sda, however that would also wipe all files off the drive.

The best course of action for you at the moment would be to completely purge Grub from your system and reinstall to sdb only.

For guidance on this read this [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) at least 3 times before committing yourself to any actions.

So its as I thought..somehow ..in installing..Mythbuntu
on the 500Gb drive its ..also installed Grub on my storage 
drive(1TB)...Damn!!

Would that storage drive be able to read in windows 7...??
as it has about 500GB of Movies and Music(Arggh!!)
so I can transfer the files off ..to another drive??

---

### Post by moviebug on 2011-12-11
> **grahammechanical said:**
> In my opinion it should not matter whether Mythbuntu is installed on sda or sdb because grub should know where to look for the Linux image to boot.

Examine the file grub.cfg to find out where Grub is expecting to find the Linux image to boot into.

It is File System/boot/grub/grub.cfg.

Look for this line



And then this line



This is from the grub.cfg of Mythbuntu that I installed two weeks ago in a fifth partition.

In the lines that follow I see this



This is Grub speak for the first hard disk and the eighth partition. I also see this



That is telling Grub which partition to find the Mythbuntu Linux image on from its disk UUID.

Try to find out if the disk UUID that Grub is looking for is the same as the disk UUID of the 500GB disk.

As for HPFS see this

[http://support.microsoft.com/kb/100108]("http://support.microsoft.com/kb/100108")


Regards.

Okay so ..forgot ..now you point to the Microsoft reference
re HPFS under system
about good old OS2..it was used then
so this should mean it is still readable under windows 7?
if I have to transfer all those files 
to another free drive(groan!)

---

### Post by moviebug on 2011-12-11
> **grahammechanical said:**
> In my opinion it should not matter whether Mythbuntu is installed on sda or sdb because grub should know where to look for the Linux image to boot.

Examine the file grub.cfg to find out where Grub is expecting to find the Linux image to boot into.

It is File System/boot/grub/grub.cfg.

Look for this line



And then this line



This is from the grub.cfg of Mythbuntu that I installed two weeks ago in a fifth partition.

In the lines that follow I see this



This is Grub speak for the first hard disk and the eighth partition. I also see this



That is telling Grub which partition to find the Mythbuntu Linux image on from its disk UUID.

Try to find out if the disk UUID that Grub is looking for is the same as the disk UUID of the 500GB disk.

As for HPFS see this

[http://support.microsoft.com/kb/100108]("http://support.microsoft.com/kb/100108")


Regards.

How do I look at the grub.cfg file?
I found it using file manager...
but I assume I need to use Terminal in some way
to see whats inside...

**A thought**...If I change the sda and sdb connections
on the physical drives(ie Sata connections on motherboard)
 that may at least allow me to boot successfully...
as then ...I assume ..it would look at sda ..
first for a Grub???  Is this correct thinking?

Then I can get all the stuff off the storage drive(1 TB)
if necessary...later at leisure??

---

### Post by moviebug on 2011-12-11
> **moviebug said:**
> How do I look at the grub.cfg file?
I found it using file manager...
but I assume I need to use Terminal in some way
to see whats inside...

**A thought**...If I change the sda and sdb connections
on the physical drives(ie Sata connections on motherboard)
 that may at least allow me to boot successfully...
as then ...I assume ..it would look at sda ..
first for a Grub???  Is this correct thinking?

Then I can get all the stuff off the storage drive(1 TB)
if necessary...later at leisure??

Yep!!...I changed the physical sata connections...around
so the 500Gb(OS) is on the other sata lead(sda?)
and rebooted..and voila
it has successfully rebooted into Mythbuntu!!:D

The storage drive(1TB) is still accessable under Mythbuntu
so thats something.. 
will have to see later whether I can transfer the Movies etc
...so I can then re-format the drive completely!!
and then transfer the Movies back again..

What a lesson!!
Thanks to all!!... for you help and patience!!
Much appreciated!!

---

