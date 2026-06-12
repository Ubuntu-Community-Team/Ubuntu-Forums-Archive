---
title: "Grub"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Dessx on 2008-10-19
Hey guys im new to ubuntu and i just recently followed this guide here [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630) to uninstall ubuntu from my harddrive i burned the thing to the cd booted up with it and deleted the linux partitions but when i restart my computer i still get the GRUB error mind you that i installed ubuntu with the full harddrive so i have no windows partition i just wanted to uninstall ubuntu install my windows again and possibly install ubuntu with my windows. currently im on ubuntu loaded from my ubuntu cd that i burned, so if someone could help me figure out how to get rid of the GRUB thing and just go back to my computers default settings i would be much obliged.


Thank you, 

Dess

---

### Post by bumanie on 2008-10-19
A format of the hard drive will get rid of grub. Format the hard drive to ntfs and then install windows. You can use gparted; either from the ubuntu live cd or get the dedicated gparted live cd from the gparted site. Even if you boot with the windows disc that should give you the option of formatting the hard drive at the beginning of the installation process.

---

### Post by mobilediesel on 2008-10-19
> **bumanie said:**
> 
__________________
Windows is the best virus detector on the market! 

That's gotta be one of the top-5 signatures!
I used Windows since 3.11 for workgroups. When Microsoft announced end of support for XP I wiped my drive and installed Ubuntu. After a steep learning curve I keep finding things that make me say "why the hell doesn't windows do it that way?"

---

### Post by Dessx on 2008-10-19
I downloaded the live cd of gparted burned it and booted it up i made a new partition from my "freespace" unformatted then right clicked it format to ntfs hit apply restarted my computer from the disc and im still getting the grub error i dont get why grub is still on my computer after all the partitions are gone and i even made a new one...
help plz

---

### Post by Gone fishing on 2008-10-19
To get rid of grub you will need to remove grub from the mbr if you've done a standard ubuntu install.

Start the PC on the XP install disk and and go to the recovery console (type r when asked) and type fixmbr this will overwrite grub and XP should boot as it did.

But why not keep both OSes can be very handy having 2 OSes when for eg when XP get trashed by malware you can easily recover your files :)

---

### Post by Gone fishing on 2008-10-19
Just reading you post again - I don't quite follow if you've removed Ubuntu and reinstalled XP you shouldn't get any grub error as XP should have overwritten the mbr (generally this is a bit of a pain).

---

### Post by Dessx on 2008-10-19
i havent reinstalled windows yet i just want to get rid of everything linux first lol. and how do i remove grub from the mbr??? and what is an mbr lawl

---

### Post by Gone fishing on 2008-10-19
When you install XP it **will** overwrite the mbr and grub so there is no need to do anything just reinstall XP, if you wanted you could over write the mbr  first by booting on the XP install disk going to the console and typing fixmbr but this is not necessary as an XP install will remove grub from the mbr

---

### Post by luctor on 2008-10-19
if you do a clean install from the windows xp install cd, you will get rid of 'everything linux'. the win cd will format the entire disk and install the windows boot loader in the mbr.
mbr = master boot record ..
[http://en.wikipedia.org/wiki/Mbr](http://en.wikipedia.org/wiki/Mbr)

---

### Post by Dessx on 2008-10-19
im not installing xp but im installing vista and when im booting from my vista disk its all ****** up lol i either get the blue screen of death after it loads the files or i get a blank backround screen for the installer and nothing happens so i dont know what to do... ive only used the disk once before to install the operating system the first time i got the computer and the second i finished that ive kept it in the case ever since and its in perfect condition so i dont know whats wrong

---

### Post by Gone fishing on 2008-10-19
I don't think that will be grub on the mbr, my guess is Vista doesn't like the ntfs partition you made using gparted my recommendation would be to start up on the gparted disk and remove all the partitions and leave the disk blank, although the console on the XP disk sould be able to do this presumably a Vista console should be able to do this too.

Apparently when you install vista it will ask you where to install Vista if you click advanced you will have the option to remove any partitions this you should do if you don't use the gparted option

Bootrec.exe /FixMbr is the command to overwrite the mbr in the vista recovery console

---

### Post by GROMS on 2008-10-31
My problem is a little different. I installed Ubuntu 64 from an iso disk and all seemed to go well. Now, when I boot the machine, it tells me to put in the boot disk. If I insert the install disk I can get to Grub and boot from first hard drive. I must have something wrong. I checked to see that the bios boot order is hd first then cd. It sounds like the mbr doesn't point to grub or grub is pointing to the wrong disk. Is there a way to tell??

---

### Post by caljohnsmith on 2008-10-31
Dessx, if you want to get rid of both Grub and your partition table on your HDD so that your HDD looks unformatted and entirely clean to Windows, just do the following from the Live CD terminal (applications > accessories > terminal):
```
sudo dd if=/dev/zero of=/dev/[COLOR="Blue"]<your HDD>[/COLOR] count=1
```
Where <your HDD> would be sda, sdb, etc. Be cautious with that command, as it wipes both Grub and your partition table, so make sure you get the drive correct.

---

### Post by meierfra. on 2008-10-31
caljohnsmith:   You might want to point out that your advice is for Dessx and not for  GROMS.

---

