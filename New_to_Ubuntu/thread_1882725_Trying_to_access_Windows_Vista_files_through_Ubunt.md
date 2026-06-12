---
title: "Trying to access Windows Vista files through Ubuntu Live CD"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by lukebishop on 2011-11-17
My Windows Vista computer crashed yesterday. I'm currently using the laptop through an Ubuntu Live CD I created on another computer. I'm trying to get into my music and documents folders to save all my stuff on my external hard drive.

I can get into the drive, then click into "users" but then when I click on "Luke" it comes up as empty and properties show that the file is empty. Does anyone know how to fix this?

I've been trying to do some research and on How to Geek there was a page about this very issue but I couldn't follow it because it was mostly about getting access to the drive, which I have access to.

Thanks,
Luke

---

### Post by rosencrantz on 2011-11-17
If the computer crashed, it is very probable the file system is compromised. I had the same problem recently with what was probably a faulty master file table on a NTFS data drive and the corrupted directories appeared empty. Try navigating to your folders in a terminal, you'll get  file I/O messages for corrupted entries. 
The first thing I'd do is a bit-by-bit clone of the whole drive to an external disk if you have space enough, so you'll still have that backup image if anything goes wrong.
```
dd if=/dev/sda1 of=/some/mountpoint/or/other
``` (replace paths where appropriate).
It's probably difficult to run ```
chkdsk /f C:
``` on a non-bootable Windows computer. Ubuntu isn't that good at repairing NTFS if I remember right. Do you have access to another Windows desktop with a spare SATA or IDE connection? Try plugging in your drive and repairing the filesystem from there.
When you set up a new system again, try to put your personal data on a separate partition. Usually, only one partition is damaged at a time which makes rescue missions much easier.

Good luck
rosencrantz

---

### Post by lukebishop on 2011-11-17
I meant to add the error message I got. The problem file was 

\Windows\system32\drivers\Wdf01000.sys

and is said that it's status was: 0xc0000098

This comes up on the same screen that says Windows didn't shut down properly, it won't get beyond that. The screen will flash with the Toshiba logo and I can push F12 to get into the boot drive options and can start Ubuntu through the disc I made.

Also, I didn't understand what you said Rosencrantz, I appreciate the help a lot, as well as the quick response but I don't understand anything about code and about how to figure out what NTFS, SATA, or IDE mean.

I was wanting to try to hook up my wife's desktop to the laptop to access the files I need, but it's years old and I doubt very highly that I would have the cables or the know-how to do that.

---

### Post by pbpersson on 2011-11-17
NTFS - the file system used by modern versions of Windows, Linux uses EXT3 or EXT4.

SATA - This is a modern drive interface type

IDE - This is an old drive interface type


He was saying that Linux might not be good at repairing NTFS which is a Microsoft invention and based on whether the hard drive is SATA or IDE seeing if you can physically connect the drive into a Windows machine to let Windows repair the NTFS partition.

Does that help?

OH!  I just saw this is a laptop!  Well, there goes that idea!   :-(

---

### Post by alphacrucis2 on 2011-11-17
It isn't usually difficult to remove the hard disk drive from a laptop. You should be able to get an inexpensive USB caddy that is compatible with the laptop hard disk. That will allow to easily plug the laptop disk into any Windows machine to run chkdisk. You need to get the right sort of caddy though.

---

### Post by lolpenguin on 2011-11-18
I did a quick search and found out the the error code 0xc0000098 which means that a system driver is missing or corrupted. The recovery CD may help you, so may chkdsk.

---

### Post by rosencrantz on 2011-11-18
OK, sorry about all the acronyms ;)
Yep, your error message sounds rather like a file needed for the bootup sequence is corrupted.

Even if it's a laptop drive, connecting it to a desktop is not too complicated.
On the bottom side of your laptop (usually front left or right) there should be a larger access cover fastened by screws. Below that is your hard drive (there is probably also a second one covering your RAM modules which is slightly smaller). 
If the drive is screwed down, unscrew it and pull it backwards towards the side of the laptop. This should detach it from the data port. 

Check the connector pins on the drive: if they look like [this]("http://upload.wikimedia.org/wikipedia/en/thumb/7/7c/SATA_Ports.jpg/800px-SATA_Ports.jpg"), you're in luck and it's SATA, which makes no difference between desktop and laptop drives. If you have access to a fairly recent desktop (SATA became standard a few years ago), you can just disconnect the desktop's power cable, open the case, balance the disk somewhere inside and connect it to the motherboard (cf. the connector and cable images in this [wikipedia article]("http://en.wikipedia.org/wiki/SATA")). If there's no free cable/connector, unplug the CD drive.

If it's an older IDE (ATA) drive, the connectors are two rows of little pins and it's not compatible with a desktop without an adapter.

The caddy idea is easier, but might not work in every circumstance. I've had drives which were pretty much unreadable from an external USB enclosure, but salvageable over a direct IDE connection.

In any case, if you have really important data on the drive, you should attempt cloning the disk before you do the chkdsk.

You'll need an external hard drive with enough free space to fit the contents of the hard drive (the nominal size is relevant: if you have a 40 GB drive that's only 30% full, you still need 40 GB free space). The drive shouldn't be FAT formatted, as FAT has a maximum file size of 4 GB (to check, click Ubuntu button, type 'disk utility' in the search field).

To figure out the IDs of the drives you want to copy from/to, open a terminal (Ubuntu button, type 'terminal' in the search field) and type 'cat /etc/mtab'. Copy the output (highlight/right mouseclick) and post it here; someone will figure out the proper paths for you (should be something like /dev/sda1 for the internal disk and /media/disk for the external one).

Go back to the terminal and type 'dd if=/dev/sda1 of=/media/disk/backupimage.iso' (or whatever the paths turn out to be). After a few hours of patience, this should get you a bit-by-bit image of your disk called 'backupimage.iso' which you can copy back to the original disk if anything goes wrong.

---

### Post by lukebishop on 2011-11-20
Hmm, okay. It makes me really nervous to start taking apart my computer.

It dawned on my today that perhaps the reason why I can access every other file in the hard drive and not the files in my personal folder is because a virus infected my computer causing the Wdf01000.sys file to crash and also delete my personal files.

Does this seem possible?

---

### Post by juliandracos on 2011-11-21
Just had a similar thing happen, although it was caused by a virus.  What happened to me was when the virus was removed, it messed things up.  All of the files were missing.  Turns out it was something to do with the file structure and invalid security things and registry.  I forget all of the things that windows said was wrong and had to fix.  I got it all fixed except when I went to C: it listed nothing, but I could do like cd windows and it would go to the windows folder.  Then I could see files in that directory.  

Anyway, what I did was this:

1.  Boot from windows disk
2.  Click repair
3.  Vista will pull up a bunch of options.  The last one is command prompt.  Click that.
4.  type chkdsk /f c:
5.  Now see if you can navigate with the command prompt to the area where your files are.
6.  After that is done, shutdown
7.  Boot using the linux disk
8.  You should now be able to view the files assuming chkdsk worked
9.  If that does not work, you can try bootrec.exe /fixmbr

---

### Post by sadaruwan12 on 2011-11-21
It's mostly that the Vista kind of hides the user files so when another person tries to view them it's stays hidden from view this is a security measure but some times it's very annoying.

Here try these links which I found this might help you to recover your dead PC

[LINK 1]("http://www.howtogeek.com/howto/31804/the-10-cleverest-ways-to-use-linux-to-fix-your-windows-pc/")

---

### Post by mastablasta on 2011-11-21
just as a side note (since i see newcommers being bombarded with command line) there is a nice little Ubuntu based distribution that handles disk backup/cloning. just to keep your data safe, no don't use clonezilla. it is powerfull but scary for us newbies. use Redo backup.: [http://redobackup.org/](http://redobackup.org/)
 
A vista repair and checkdisk command as suggetsed above might be all you need to do. However if you wish you can install an antivirus on a live Ubuntu cd and use it then to scan your mashcine or do an online scan.
 
also for future it is good to have an antivirus (Avira, Avast, FreeAVG to name a only a few free ones)installed in windows and you also need firewall (for example Comodo or ZoneAlarm are descent ones). the combination of both make a preety good combo against viruses. especially if you know what you are doing. ofcourse nothing is completelly bullet proof.

---

### Post by lukebishop on 2011-11-21
Last night I decided to try downloading a torrent of a Vista recovery disc. I am nervous of downloading stuff like that in case someone puts in a virus, but I figured it didn't matter since my computer had already crapped out anyway.

So I used that and opened the repair option to search for and repair problems. It found and repaired a couple problems but the computer still wouldn't start. Long story short I got back onto Ubuntu and it could access my files now! I've transferred all the important crap onto my external hard drive.

Now all I need to do is to install Ubuntu full time and then reformat my hard drive. But I need to figure out which order first.

Thanks you everyone for your help! Although it seems as though I may not have followed all of the advice it's because I didn't understand it.

Oh, and to mastablasta, I did have a virus program installed on my computer then when I needed it rebooted the guy at the computer store told me I didn't need one and installed a program to simply scan for virus' but doesn't actually block any. Fat lot of good that did! By the time the thing could tell me I have a virus my computer had already crashed. Apparently my critical thinking skills aren't as good as I had thought!

---

