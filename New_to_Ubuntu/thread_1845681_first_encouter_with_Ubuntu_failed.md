---
title: "first encouter with Ubuntu failed?"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by 5pannerman on 2011-09-17
[FONT=Times New Roman][SIZE=3]Dear Linux/Ubuntu friends. I have now been told by many friends to get away from anything Microsoft and try Linux.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Last week I have taken the plunge with my old experimental fanless EPIA mini ITX 530 Mhz with 256 meg memory and 20 gig hard drive. It runs Windows XP sp3 home edition etc. quite happily, albeit slow. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]My plan of attack was to be careful and install the lighter version Xubuntu as a dual boot and then wipe windows. However, when I select Ubuntu on startup the machine reboots. There was, even after changing the boot ini no Ubuntu to be seen. I have spent quite some time on the internet and later on your forum looking for solutions.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]After a total reformat I tried to install Xubuntu from the downloaded disc but it seems the machine can’t read ISO files. So I re-installed Windows and Xubuntu again, thinking of another way of getting it working. This is where I am now, an almost total windows free machine in safemode and Xubuntu installed.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]So the question, with as little ubuntu jargon as possible please is: Is this machine too light for your op system? What did I do wrong? What do I do now?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Thanks for time reading all of this and I am very grateful for suggestions. [/FONT][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Kind regards,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]5pannerman[/SIZE][/FONT]

---

### Post by Lisiano on 2011-09-17
Well first of. If you want to Dual-Boot your system with WinXP (Due to size constraints I would advise against that) then you need to have WinXP installed first (To decrease the amount of steps) then install Xubuntu (Or Lubuntu). GRUB manages booting for both Windows and Linux.
PS. You don't have to edit the boot.ini on Windows in ANY way.

EDIT:
> After a total reformat I tried to install Xubuntu from the downloaded disc but it seems the machine **can&#8217;t read ISO files**. So I re-installed Windows and Xubuntu again, thinking of another way of getting it working. This is where I am now, an almost total windows free machine in safemode and Xubuntu installed.Did you by any chance try to copy the ISO onto a CD/USB instead of burning it?

---

### Post by 5pannerman on 2011-09-17
Thank you Lisiano for your quick reply. The dual boot idea was because I had xp already on that machine. At some point I tried to remove windows from the boot ini to enable Ubuntu to come through. Then I started clean and found the machine doesn't seem to like ISO files. etc.
 
I am still very keen to see this work.
Thanks

---

### Post by josephmills on 2011-09-17
Installation without a CD
The new generations of laptops and netbooks are increasingly shipping without CD drives. To cater to this need, or if you do not wish to burn a CD to install Ubuntu, you are not left to trudge in the dark - Ubuntu can be installed without using a CD or CD-ROM drive!

Quick Install from USB - A quick guide to installing from a USB memory stick. Intended for less technically-inclined readers.
Install from USB - Installing from a USB memory stick (full version).
USB stick + grub - Similar to above but using grub.
Smart Boot Manager - Installing from a PC which will not boot from a CD.
Install within Windows - Yes, it is possible to install Ubuntu from within Windows without using floppies, a CD, or any other removable media! This uses Wubi, and installs Ubuntu as a large file that may be uninstalled like any other program in Windows.
Install with Floppies - Installing without a CD drive over a network.
Install From Hard Drive with Floppies - Installing without a CD drive or network capabilities from a hard drive.
Install from Existing Linux - Installing using a spare partition from an existing Linux system to house the Ubuntu CD image.
Virtual Machine - Installing using a physical disk to a Virtual Machine.
Please refer also to the network installation guides below.




Server and network installations
Ubuntu can be installed over a network or the Internet.

Local Network - Booting the installer from a local server, using DHCP, TFTP, and PXE.
Installation/Netboot - Another description of installing over the net, with no CD-ROM drive or a non-bootable SCSI CD-ROM drive.
Netboot Install From Intenet - Booting using files saved to an existing partition and downloading the packages from the internet at installation time.
Network Console - Booting from a CD (could be TFTP or similar too) and installing the system over SSH.
On NFS Drive - Installing on a NFS-server and using with diskless clients.
On NFS Drive with Local Boot - Installing on an NFS-server with a local /boot (e.g. Booting from CompactFlash for a silent media center PC).
Quick Install over SSH - A quick guide for installing Hardy Ubuntu 8.04 on a dedicated server over ssh.
Over SSH - Installing on a dedicated server over ssh (full version).
Install with Floppies - Installing without a CD drive over a network.





SOURCE 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)


have you also looked at lubuntu ?

---

### Post by 5pannerman on 2011-09-17
No Lisiano, I burned the cd using the program Infra recorder.

---

### Post by Lisiano on 2011-09-17
+1 for the [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
If you plan to remove Windows later on, why not remove it right away? Just install any [KXL]ubuntu on the whole disk. That is if you don't have any files you wish to save beforehand. You can copy them somewhere safe for example onto another computer or a USB drive.

---

### Post by Mark Phelps on 2011-09-17
The memory is too little to use Ubuntu effectively.  Having 512MB would give you a much better experience.

You could try a lighterwieight disto, like Lubuntu or Puppy Linux -- but then, you wouldn't get quite the same experience.

---

### Post by 5pannerman on 2011-09-17
[FONT=Times New Roman][SIZE=3]Hi Lisiano, I have tried a clean installation and found that the ISO file could not be read. Is there an other way to start it?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks Mark for your reply. I understand that this machine has the minimum required memory, but I hate to admit that xp runs on it and I am told that Linux versions are less demanding. Before I start again with a newly formatted disk I would like to know if there is another way or using non ISO files that this machine can read. If there is such a start file I will start from scratch, if not I will have to find a way to start it in XP, or forget about the whole thing.   But that would be a pitty, wouldn’t it.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks people[/SIZE][/FONT]

---

### Post by wildmanne39 on 2011-09-17
Hi, it needs to be an iso file.

You should try to download it using a bit torrent it verifies the files and makes sure they are not corrupt.

Also post 4 gives you several other methods to install ubuntu.
Thank you

---

### Post by gopal711 on 2011-09-17
i have tried to install ubuntu 11.04 on my pc. this is the first time i'm trying. i'm already using win xp on my pc. i've tried to install ubuntu 11.04 from a usb, everything goes fine and i selected install ubuntu on hard disk option. after sometime where live desktop should appear, the system hangs and even the live desktop is not being loaded. downloaded ubuntu again and tried..but the result was same. can anyone guide me what to do?

---

### Post by wildmanne39 on 2011-09-17
Hi, have a look at this link and try what it says it may help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by GWBouge on 2011-09-17
> **5pannerman said:**
> I have tried a clean installation and found that the ISO file could not be read.

This is quite confusing, as there should be no .iso file on the CD for the computer to try to load.

Just for clarification, when you view the CD's contents from within Explorer/My Computer, does it show an .iso file, or a bunch of files and folders?

---

### Post by Blasphemist on 2011-09-17
> **gopal711 said:**
> i have tried to install ubuntu 11.04 on my pc. this is the first time i'm trying. i'm already using win xp on my pc. i've tried to install ubuntu 11.04 from a usb, everything goes fine and i selected install ubuntu on hard disk option. after sometime where live desktop should appear, the system hangs and even the live desktop is not being loaded. downloaded ubuntu again and tried..but the result was same. can anyone guide me what to do?

It's really better to create your own thread to get an issue resolved but I'll try to help you. It's just that's its easy to get issues confused when two peoples issues are in one thread.

Let's start with learning some things about your system. What is the make and model and any other details you know. 

A couple points. If you have chosen to install ubuntu, you'll not get a live desktop. It's the other way around. You can choose try ubuntu and get the live desktop and then when ready choose to install ubuntu. And what if any prompts do you get before it hangs up? We may be able to tell by where it fails what the install may be trying to do at the time.

---

### Post by 5pannerman on 2011-09-18
[FONT=Times New Roman][SIZE=3]Thanks GWBouge, this sounds interesting. *All the disks I initially made just have an ISO file*. However, I tried to do the USB option, as suggested in answer 4 by Joseph Mills last night, and on that USB stick are a bunch of files. I stopped late for bed because I suspect the machine doesn&#8217;t like to boot from USB.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]OK, is there then a program, like the USB making one, that makes the bootable CD? That would be great. :P[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Edited: or can I copy the imige of the USB stick to a CD, or is that silly[/SIZE][/FONT]

---

### Post by 5pannerman on 2011-09-18
[FONT=Times New Roman][SIZE=3]Latest update, I made a new disk with “Copy Image to CD” from Alex Feinman that I found on the forum, made a CD with multiple files, not just an ISO image. The machine started to boot from this but runs into trouble at loading bootlogo...:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Graphics initialisation failed[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Error setting up gfxboot.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Boot:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Loading bootlogo...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I suppose this machine is not compatible? :icon_frown:[/SIZE][/FONT]

---

### Post by 5pannerman on 2011-09-18
[FONT=Times New Roman][SIZE=3]Right, brain wave. I had a search in the loft and found an old Packard Bell, 800Mhz, 500 meg mem and I put in the 2gig hard drive from the fanless.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Booted with the latest disk I made, as mentioned above, and I now have a purple screen.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]For me this thread is closed, I now know the fanless is not ready for Ubuntu but I now do have a toy to play with and make up my mind regarding Windows. (bit sad moment if so, started with DOS in the eighties) [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks again for your help, I may be back for more noobish questions in future, if you don’t mind.  ):P[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]5pannerman[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by Lisiano on 2011-09-18
Ah. So you were copying the image instead of burning it. Anyway. Glad that this is resolved. Also please mark the thread as solved using the Thread Tools.
Btw if you want to use the CLI only, Ctrl+Alt+F1-F6 and you get a CLI only environment.
Also for the old one, you can install the Server Edition, it's just without a graphic environment, the lightest of all.

---

### Post by 5pannerman on 2011-09-18
[FONT=Times New Roman][SIZE=3]Thank you Lisiano for your advice. The program I used made the disk as it was, I had no options then. In a later stage I will come back to the fanless and give it another go, first I have to play with what I have. Also, if Ubuntu in any of it&#8217;s forms is going to be interesting to me it has to be able to run AutoCad. This, I noticed on the forums, may not be the case yet??[/SIZE][/FONT]

---

### Post by Lisiano on 2011-09-18
Correct. But there are alternatives like LinuxCAD ([http://www.linuxcad.com/](http://www.linuxcad.com/)) or others. I don't use CAD software so I'm not sure how good are the alternatives.

---

### Post by IHeequ5i on 2011-09-18
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=86](http://appdb.winehq.org/objectManager.php?sClass=application&iId=86)

WineHQ is your friend for all things related to trying to get Windows programs to work under Linux.

---

### Post by Lisiano on 2011-09-18
[http://alternativeto.net/software/autocad/?platform=linux](http://alternativeto.net/software/autocad/?platform=linux)

Also your friend for knowing any alternatives be it platform or just another vendor.

---

### Post by 5pannerman on 2011-09-18
The CAD options sound interesting. However, in the business environment I work in there is a standard and to come up with a potential non-compatible drawing is not a good idea. If AutoCad works as is on Ubuntu or so, then that is a different matter and would be very desirable.

Ps. The install program is happily coping away, and that option to detect the keyboard, very nice indeed.

---

