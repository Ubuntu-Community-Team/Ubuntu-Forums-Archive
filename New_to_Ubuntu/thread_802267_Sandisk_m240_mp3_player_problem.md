---
title: "Sandisk m240 mp3 player problem"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by jras20 on 2008-05-21
I cant seem to get the sandisk mp3 player m240 to work right, I have a screenshot of what it does, it should have my music and data on it, or that is what it does with Vista.  I have Ubuntu 8.04 any help will be helpful!
Thanks!
J

---

### Post by jeamer on 2008-05-21
Hey, I've got a similar mp3 player (I think it's the m230). Unfortunately Ubuntu will never recognize any songs that have been placed on there in Windows; also if you put anything on in Ubuntu, it wont recognize any of the songs in Windows. They are two different filesystems so as I understand there is no way around it. Personally, I used my wife's XP computer to get rid of all the windows songs on the player and now exclusively use Ubuntu and have no problem. 

PS make sure you are in MSC mode (in the USB settings of the player)

---

### Post by jras20 on 2008-05-21
Well the thing is that it is doing the same thing Windows 2000 does.  It loads it but I cant put anything in.  I was hoping there might be a driver or something I could load into Ubuntu?
for it to work right?

---

### Post by jras20 on 2008-05-21
My PSP works great with Ubuntu, but my MP3 Sandisk m240 doesnt, I wish I could get some help! :)

---

### Post by SilverWolf240 on 2008-05-21
> **jeamer said:**
> PS make sure you are in MSC mode (in the USB settings of the player)

I have mine set to Autodetect mode, and I had no trouble getting files to it once I figured out how to create MP3 files on my computer. Is there any specific reason why you should have it set to MSC mode? BTW I'm using an m230

---

### Post by jras20 on 2008-05-21
How do you set it to Automatic mode?

---

### Post by jeamer on 2008-05-21
cool, autodetect works as well

in your MP3 player (at least for mine) you go 

Menu > Settings > USB > Autodetect

Why does it still not add? What have you tried? All I do is drag files/folders onto the player via nautilus.

PS I'm pretty sure it only supports MP3 format... careful as Ubuntu defaults to .Ogg

---

### Post by jras20 on 2008-05-21
All it shows is that screenshot what I put at my first post on here, I dont understand it.  I checked it and it was set at automatic.  Still does the same thing.

---

### Post by jeamer on 2008-05-21
Yup, so if you already have songs on there that you put on in windows, you can only delete them if you go back into windows. They'll never show up in Ubuntu. Otherwise, if you want to add/delete songs on/off your MP3 player in Ubuntu, all you have to do is keep that window open, open a window displaying your music files in nautilus (i.e. /home/*username*/music) and drag whatever songs into the open window for your Sansa player. This will copy them onto your player and you're good to go.

---

### Post by jras20 on 2008-05-28
I got a question, does Linux support Sandisk mp3 players?  I posted a question up about this on a different boards and they said that it does not.  I wish I could get this problem solved, its the only thing I am having trouble with.  I may half to go back to windows XP on my laptop.  I Have Vista on it but hate it.  Thats why I put Ubuntu on it.
I have Ubuntu 8.04. 32bit.

---

### Post by werries on 2008-05-28
i have no experience with this.
but a quick google returns this nice tutorial
[http://www.howtoforge.com/sandisk_mp3_player_linux](http://www.howtoforge.com/sandisk_mp3_player_linux)
It mostly involves changing the transfer protocol to MSC. good luck and report back!
EDIT: I think this requires windows to switch the protocol with the sandisk software, btw.

---

### Post by roderick on 2008-05-28
Mine worked out of the box not needing any changes. I could access it either as a removable media or from within Amarok to transfer music too.

I guess it could be newer than mine (bought a year ago).

---

### Post by werries on 2008-05-28
either way, you shouldn't have problems getting it connected.
zunes are the one big media player block right now.

---

### Post by jras20 on 2008-05-28
I have had help with this, on my earler posts but I have had no luck.  It does see it as a 1gb flash drive, but I can not read/write anything on it.  The same thing does this on windows 2,000.  Windows Vista and XP, I have no problem with it.  But I hate windows Vista as what I have now on my laptop, but I installed Ubuntu.  The player would load up the mp3 player file, but I cant read or write on it.  If I can change that maybe somewhere?  I want it fixed! Then I can sleep! :lolflag:

Edit: I also did that MSC setting, I did just about everything I can think of, formating it in XP, changing the settings, I dont know what else to do!

---

### Post by jras20 on 2008-05-29
Bump!  I still havnt solved this lol.  It does see that it is a flash drive, but why cant I read or write on it?  Does any one have any suggestions?
Thanks

---

### Post by roderick on 2008-05-29
can you provide the output from the mount command? Perhaps it sees it as read-only.

Are you able to see files on it? Can you read these files and copy them successfully to your desktop (assuming there is something already on it)?

---

### Post by jras20 on 2008-05-29
It wont read or write anything.  I posted a screenshot on this thread I had started what it does, that is what it see's.  

[http://ubuntuforums.org/showthread.php?t=802267](http://ubuntuforums.org/showthread.php?t=802267)

I'm not sure what else to do.

---

### Post by lespaul_rentals on 2008-05-29
Try opening a root file manager:

```
sudo nautilus
```

Or, if you are on KDE:

```
sudo konqueror
```

If this allows you to read and write, we will know it is a permission problem.

---

### Post by jras20 on 2008-05-29
sudo: konqueror: command not found


Still the same thing, it wouldnt let me read or write.

---

### Post by roderick on 2008-05-29
> **jras20 said:**
> sudo: konqueror: command not found

this didn't work due to the command not found message.

Anyway, can you provide output from lspci, mount, lsusb? Open a console/terminal and execute those commands and copy/paste the output here so I can get a better understanding of the device and how it was mounted.

Also, in the screenshot, I see the folders. Can you open the Record or Audible folders? If you can, then the device is correctly detected and mounted and readable. The question then is writable.

---

### Post by AmishFury on 2008-05-29
my m240 shows up as a 1GB flash drive but i cannot access the music storage... mtp mode same thing but it vanishes when i open rhythmbox
my e280 cycles between connected and disconnected

---

### Post by jras20 on 2008-05-29
> **roderick said:**
> this didn't work due to the command not found message.

Anyway, can you provide output from lspci, mount, lsusb? Open a console/terminal and execute those commands and copy/paste the output here so I can get a better understanding of the device and how it was mounted.

Also, in the screenshot, I see the folders. Can you open the Record or Audible folders? If you can, then the device is correctly detected and mounted and readable. The question then is writable.

I can open the folders and see what is in it, but if I put a mp3 file from windowsXP onto the player and then go here, I cant view the files.  What code do I need to do?  Sorry I'm still learning.

---

### Post by lespaul_rentals on 2008-05-29
Oh!  I know what's going on!  You are putting songs on your Sandisk player in MTP mode.  You must use MSC mode to support drag-and-drop file transfers.

---

### Post by MONODA on 2008-05-29
I know that you can install rockbox on them and then they will work with ubuntu easily, I know because my bro has one. BTW rockbox pwns the original firmware.

---

### Post by lespaul_rentals on 2008-05-29
> **MONODA said:**
> I know that you can install rockbox on them and then they will work with ubuntu easily, I know because my bro has one. BTW rockbox pwns the original firmware.

The firmware has little to do with how easy it is to connect.  Besides, when you plug it in using USB, it boots into the original firmware anyway.  Don't tell him he has to install Rockbox before he can get it to work.

---

### Post by MONODA on 2008-05-29
> The firmware has little to do with how easy it is to connect. Besides, when you plug it in using USB, it boots into the original firmware anyway. Don't tell him he has to install Rockbox before he can get it to work. I was just recommending it, it is really nice.
EDIT: to the OP, you should check this out: [http://ubuntuforums.org/showthread.php?t=312196](http://ubuntuforums.org/showthread.php?t=312196)

---

### Post by aysiu on 2008-05-29
**@lespaul_rentals**
Please stop recommending *sudo konqueror* and *sudo nautilus*. Even though for those particular commands there is probably no harm done, it's a bad habit for people to get into using *sudo* with graphical applications. The proper commands are ```
kdesu konqueror
``` and ```
gksudo nautilus
``` For more details, read [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

**@jras20**
I have a Sansa Clip, and what showed up in Windows was completely different from what showed up in Ubuntu. Be sure to change (on the Sandisk player itself (not in Ubuntu or Windows) to MSC mode, not Autodetect or MTP mode.

Then you can drag and drop songs to a folder, and it should all work out.

---

### Post by jras20 on 2008-05-29
Strange as it may sound, I have a earler version of that sandisk, m230 512mb and it works just fine!  I can read write and then go to windows and read and write.  I need to format my m240 again, I think something mest up.  Once I can get it formated I'll try it again.
Thanks again for the help I'll see what happens.

---

### Post by jras20 on 2008-05-29
Ok, now it tells me permission is denied when I drag and drop the files using the M240, but my M230 worked.  What to do now?

---

### Post by aysiu on 2008-05-29
> **jras20 said:**
> Ok, now it tells me permission is denied when I drag and drop the files using the M240, but my M230 worked.  What to do now?
Plug your M240 in, open up [a terminal](http://www.psychocats.net/ubuntu/terminal), paste these commands in: ```
df -h
sudo fdisk -l
``` and then paste the output back here.

---

### Post by jras20 on 2008-05-29
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  5.1G  7.2G  42% /
varrun                378M  104K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M   48K  378M   1% /dev
devshm                378M  140K  378M   1% /dev/shm
lrm                   378M   38M  341M  10% /lib/modules/2.6.24-17-generic/volatile
gvfs-fuse-daemon       13G  5.1G  7.2G  42% /home/jras20/.gvfs
/dev/sdb              970M  784K  969M   1% /media/SANSA M240

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b6dd6a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275        5519    34097962+   6  FAT16
/dev/sda3            5520        9729    33816825    7  HPFS/NTFS

Disk /dev/sdb: 1016 MB, 1016856576 bytes
32 heads, 61 sectors/track, 1017 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      398636      983425   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       86419     1078237   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      957932     1949749   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     1863334  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1863333, 7, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by aysiu on 2008-05-29
Looks as if something's wrong with the partition table on your player.

Maybe we can fix it? ```
sudo umount /media/SANSA\ M240
sudo apt-get update
sudo apt-get install gpart
sudo gpart /dev/sdb
```

---

### Post by jras20 on 2008-05-29
> **aysiu said:**
> Looks as if something's wrong with the partition table on your player.

Maybe we can fix it? ```
sudo umount /media/SANSA\ M240
sudo apt-get update
sudo apt-get install gpart
sudo gpart /dev/sdb
```

Does the player need to be pluged in?

---

### Post by aysiu on 2008-05-29
> **jras20 said:**
> Does the player need to be pluged in?
Yes. We're unmounting it but keeping it plugged in to guess the partition table.

The first command says "Let's make sure this drive isn't busy (but still connected."

The second command says "Let's check to see what software is available to install."

The third command says "Let's install the software called *gpart*."

The fourth command says "Using *gpart*, let's guess what the partition table is supposed to look like on that drive."

If the guess looks good to you, you can run ```
sudo gpart -W /dev/sdb
``` to have the partition table written. Case is important. That's a capital *W*, not a lowercase *w*.

---

### Post by lespaul_rentals on 2008-05-29
> **aysiu said:**
> **@lespaul_rentals**
Please stop recommending *sudo konqueror* and *sudo nautilus*.

Sorry about that.

---

### Post by jras20 on 2008-05-29
> **aysiu said:**
> Yes. We're unmounting it but keeping it plugged in to guess the partition table.

The first command says "Let's make sure this drive isn't busy (but still connected."

The second command says "Let's check to see what software is available to install."

The third command says "Let's install the software called *gpart*."

The fourth command says "Using *gpart*, let's guess what the partition table is supposed to look like on that drive."

If the guess looks good to you, you can run ```
sudo gpart -W /dev/sdb
``` to have the partition table written. Case is important. That's a capital *W*, not a lowercase *w*.

ok I typed it in

---

### Post by aysiu on 2008-05-29
> **jras20 said:**
> ok I typed it in
Pasting is faster and leaves less room for error than typing, but now that you've typed it, what was the output?

---

### Post by jras20 on 2008-05-29
umount: /media/SANSA M240: not found
jras20@jras20-laptop:~$ sudo apt-get update
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [77.1kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6150B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [18.2kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [898B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [33.2kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [5312B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [7119B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [972B]
Fetched 208kB in 4s (47.7kB/s)
Reading package lists... Done
jras20@jras20-laptop:~$ sudo apt-get install gpart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xaw3dg
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gpart
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
Need to get 36.2kB of archives.
After this operation, 115kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe gpart 0.1h-4.1 [36.2kB]
Fetched 36.2kB in 0s (42.2kB/s)
Selecting previously deselected package gpart.
(Reading database ... 128362 files and directories currently installed.)
Unpacking gpart (from .../gpart_0.1h-4.1_i386.deb) ...
Setting up gpart (0.1h-4.1) ...

---

### Post by aysiu on 2008-05-29
```
umount: /media/SANSA M240: not found
``` That's weird that it couldn't find /media/SANSA\ M240. Everything else looks good, though. Can you try ```
sudo umount /dev/sdb
``` and, if that works, try ```
sudo gpart /dev/sdb
``` ? Either way, post the output back here.

---

### Post by jras20 on 2008-05-29
Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

---

### Post by freddybob on 2008-05-29
If you change the player to MTP mode can you not access your music in the devices tab of Amarok?

You might need to go into Amarok's settings and add an MTP Media Device first.

---

### Post by aysiu on 2008-05-29
I'm lost. I don't know why even the guessed partition table looks empty. Go for freddybob's suggestion.

---

### Post by jras20 on 2008-05-29
lol I am lost also.  I dont get it.  Looks like it should work just like the M30 does I will try freddybob's idea.  Thanks for helping out!

---

### Post by nick_h on 2008-05-29
I have a Sandisk e200 series.  It also gives unusual output from fdisk.  I get the following:

> Partition x has different physical/logical beginnings (non-Linux?)
Partition x has different physical/logical endings:
Partition x does not end on cylinder boundary.

For my player, the first partition is the internal memory and the other partition is for a plugin card.

I have had no problems in MSC mode.

---

### Post by Neobuntu on 2008-10-07
I just got one of these and it works out of the box. Weird how it shows two different directories in Xp and then in Kubuntu. Kubutu was way easier because it didn't have to go online to "set up the hardware".

Wait, my new one is only sdb, not sdb1. So this is what you want. It's formatted kinda like a floppy. Unless Windows did that on "installation".

Reformat using the correct options and having no parttion.

Also even though my m240 worked, I set it to MSC (NOT MTP or Auto).

Our other MP3 player is a Samsung and I had to upgrade a very hard to find firmware, so it would work as mass storage (plug in and click and drag.) It does ".ogg" but this m240 does not. I don't care though. I use MP3. no such back flips with this player. I did note, it (m240) lets us browse by artist and album, off of MP3 file embedded info. Our (last model) Samsung only by folder and name (without a added "playlist".)

Let me know how it goes. I haven't even pulled mine up in Amarok yet. Wait.... It works. I just set Amarok setting to "Generic audio player" for the recognized "sdb" (look closely) and then back under Devices, clicked connect. There they are.

---

