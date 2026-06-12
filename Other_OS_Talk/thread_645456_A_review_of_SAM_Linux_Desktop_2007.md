---
title: "A review of SAM Linux Desktop 2007"
date: 2007-12-20
forum: Other OS Talk
---

### Post by Warren Watts on 2007-12-20
I was wasting time on distrowatch.com the other day and came across SAM Linux Desktop 2007.  
SAM Linux is a lightweight PCLOS-based distro that uses the Xfce windows manager.
It seemed like a good fit for some of my older hardware, so I downloaded and burned the Live CD. 


**Overall Look and Layout**

I popped in the CD, rebooted the system and launched the OS.  After answering a few basic questions about locale and configuring my ethernet connection, I was presented with a very nice desktop.

SAM Linux uses the Dropline Neu! Icon Theme, which I found easy on the eyes and modern looking.  The Wbar application chooser is also utilized, which to anyone who has seen it, is a really slick application for providing access to your favorite applications.

The menus were a little confusing at first; I had trouble finding the things I wanted.  After using the menus for a while I got a better graps on the general layout of the menus and didn't struggle to find an application I was looking for, but I still think some of the applications are poorly categorized.

**Included packages and package management**

Package management is accomplished via Synaptic Package Manager, with RPM's from SAM Linux and PCLOS repositories.  I struggled at first with the lack of a command line based package installer, but a thread posted on the SAM Linux forum netted me an answer in just under an hour. All I had to do was install aptitude via synaptic.

**SAM Linux includes a pretty complete set of applications "out of the box":**
**Office        **
- OpenOffice.org 2.2
- Abiword:   Word Processing
- Gnumeric:   Spreadsheet
- Dayplanner:   Calendar
- gLabels:   Label Designer
- Orage:   Calendar

**Networking & Internet    **
- Mozilla Firefox:   Web Browser
- Opera:   Web Browser
- Browser-Plugins:   Flash, Java, MozPlugger
- Sylpheed Claws:   E-Mail
- Gaim:   Multi-Messenger
- Xchat:   IRC Chat
- gFtp:   FTP-Client
- Liferea:   News-Reader
- Skype:   Internet-Telephonie
- Gtk-Gnutella:   File Sharing
- Chestnut-Dialer:   Modem-Connection
- VNC:   virtual Network Connection
- Putty
- PyNeighbourhood: Windows-Networks	

**Multimedia **
- Exaile:   mp3-Player, Internet Radio
- Mplayer:   Multimedia-Player
- gXine:   Multimedia-Player
- Xmms:   mp3-Player
- Grip:   CD-Ripping
- GnomeBaker:   CD Burning
- Streamtuner:   Internet Radio
- Realplayer:   Multimedia-Player
- TV Time:   watching TV
 	 	 
**Graphics**
- Evince:   pdf-Viewer
- Gimp:   Photo editing
- FLPhoto:   Photo editing,Viewer
- GQview:   Picture Viewer
- GTKam:   Digicam-Tool
- Sodipodi:   Vector Graphic
- Xsane:   Scanning

**Games**
- Enigma
- FloboPuyo
- Frozen Bubble
- Gweled
- IceBreaker
- LBreakout 2
- LMarbles
- PySol
- Quadra
- Supertux
- Tower Toppler
- Xskat	

**Accessories**
- Gnome Commander:   File manager
- Mousepad:   Notepad
- Calculator
- Xarchiver:   Archiving
- Alltray
- Appfinder

**Security/Rescue**
- Firewall
- nmap
- Gparted
- partimage
- Testdisk
- My-Sys
- rkhunter
- redo-mbr	

**System programs**
- PCLinuxOS Control Center
- Synaptic Software Manager
- Terminal
- Midnight Commander
- Net Applet
- GDM Login Window
- Tilda
- Gnome-Volume-Manager	

**Other**
- Beryl 3d Desktop + Emerald
- Wine Windows Emulator
- Adesklets + Adesklets Manager
- Bluefish Html-Editor


**Running the Live CD**

Overall, I was pretty impressed.  I download distros all the time to play with, and this is the first one in a while I have wanted to do more with than use for a couple of hours from the Live CD.


**Installation to the hard drive**

I dragged a 400 MHz Pentium II with 320MB RAM out of the closet and gave the disk installation a try.

Here's where I had the first of a few minor problems.  The aforementioned guinea-pig system already had Ubuntu 7.10 installed on a 14GB hard drive, so I wanted to repartition the drive to make room for SAM Linux.  

When I started the install, the install-based partition editor failed to allow me to repartition.  No problem really; I rebooted the computer with my handy-dandy Live GParted CD, and successfully repartitioned the disk, splitting it evenly into two 7.75 GB partitions, reserving the 750MB swap already set up on the drive.

Rebooted the SAM Linux CD, and tried the install again.  Chose to install to the partition I created with GParted, and the install appeared to complete successfully.  However, upon reboot, I discovered that GRUB had not been modified by the install.

So I used Ubuntu to edit menu.lst to include SAM Linux, and rebooted again.

It booted to the GDM login, where I realized that the install had never prompted me to create a user.  I rebooted and attempted to create a user and add the created user to all the appropriate groups, but with no success.

I rebooted again via the Live CD, and installed a second time, and was prompted at the finish of the install to create a root password and a user account.  I removed the CD, rebooted, to discover that GRUB STILL hadn't been modified.  However, I had already modified GRUB from the first failed install, so I was able to select and boot SAM Linux.

Logged in from the GDM login, and everything worked just fine!

Looking over the xorg.conf file, I realized that my 128MB ATI card was using the ati driver and not fglrx.

A quick look through Synaptic, and I installed the Proprietary ATI drivers.  After automatic installation (including an automatic edit of xorg.conf) and a restart of X, I was able to run the ATI Cataylst application.

However, the DRI module didn't get activated (I'm sure a tweak of xorg.conf could have fixed it) and I didn't feel like farting around with fixing it.  I just went back to the ati driver. Xfce's compositing doesn't seem to slow it down much without the fglrx driver, so I'm satisfied.


**Usability**

I have spent a total of about 15 hours playing with SAM Linux so far.  About an hour with the Live CD, another three or so getting it installed and tweaked the way I wanted it, and the balance of the time just playing with it, 

I like PCLOS's GUI approach to configuration, although sometimes all the layered configuration menus and eye-candy can be a little irritating when all you want to do is something simple.

The large number of installed packages is well rounded, with something there to satisfy most any users need.


**Pros:**
Excellent "Look and feel" and general usability
Large number of pre-installed packages
Simple package management via Synaptic
Easy GUI based approach to system management and configuration
Runs well on older, slower hardware.  My test system was a 400MHz Pentium II with 320MB of RAM, and I felt it ran acceptably well.  

**Cons:**
I struggled with the hard disk installation.  I would think that a lot of people would be installing SAM Linux in a dual-boot configuration, and would certainly struggle if they experienced difficulties similar to mine with GRUB, especially if they were unfamiliar with manually editing GRUB's menu.lst file.  Perhaps installing it onto an empty hard drive would have gone more smoothly.

Because SAM Linux is based on PCLOS and utilizes PCLOS's GUI approach to system management and configuration,  more experienced Linux users might be a bit put off.  K.I.S.S certainly isn't the word of the day in SAM Linux. 

SAM Linux's user base is pretty small.  At the time of this writing there were only roughly 1,300 members in the SAM Linux forum.  I have to admit however that I got a pretty quick response to a thread I posted about installing packages from the command line.

**Overall**
I would recommend SAM Linux Desktop 2007 to anyone who was looking for a lightweight, well rounded, and easy to use Linux distribution. Lots of pre-installed software, easy package management, and easy system administration.

I had some problems with the install, but they were pretty basic and easy to overcome.

**I give it 4.5 out of 5 stars.**

---

### Post by 67GTA on 2007-12-20
I really liked SAM. I tried the live cd a few months back. I keep waiting for the final........waiting......

---

### Post by igknighted on 2007-12-20
> **67GTA said:**
> I really liked SAM. I tried the live cd a few months back. I keep waiting for the final........waiting......

SAM 2007 went final well before PCLOS 2007 (PCLOS was held up due to KDE bugs that did not effect SAM).  There was a public beta for 2007.1 in mid summer, but there has since been some shake-ups in both SAM and PCLOS that caused development plans to change some.  Work on the next new version of SAM is underway (still based on PCLOS) and progressing nicely.  Not sure when to expect another final, there's still plenty of work to go with the current development, but it is shaping up very nicely.

---

### Post by 67GTA on 2007-12-20
I tried SAM-2007.1test1. Is that the current development version, or is there another version that hasn't been reported? It seemed very stable a few months back. I have been waiting for the 2007.1 final.

---

### Post by igknighted on 2007-12-20
> **67GTA said:**
> I tried SAM-2007.1test1. Is that the current development version, or is there another version that hasn't been reported? It seemed very stable a few months back. I have been waiting for the 2007.1 final.

There is a newer version but it is a private developer's preview (2/3 weeks old IIRC).  Instead of using the PCLOS repo's for everything (d...i...r...t... s...l...o...w...), SAM wants to move to it's own repo's and sync with PCLOS.  This will hopefully lead to better customization of packages for the Xfce environment.  The early 2007.1 test release was put on hold for some time while events external to SAM that would have direct impact on us played out.  As mentioned before, development is back on track and looking better than ever.

---

### Post by smartboyathome on 2007-12-20
I tried SAM, and stayed with it for a whole 3+ months after I tried Ubuntu. I only moved back because it didn't have some of the packages I wanted which were in Ubuntu.

---

### Post by 67GTA on 2007-12-20
> **igknighted said:**
> There is a newer version but it is a private developer's preview (2/3 weeks old IIRC).  Instead of using the PCLOS repo's for everything (d...i...r...t... s...l...o...w...), SAM wants to move to it's own repo's and sync with PCLOS.  This will hopefully lead to better customization of packages for the Xfce environment.  The early 2007.1 test release was put on hold for some time while events external to SAM that would have direct impact on us played out.  As mentioned before, development is back on track and looking better than ever.

Awesome. I will keep an eye on it.

---

### Post by Warren Watts on 2007-12-20
> **igknighted said:**
> Instead of using the PCLOS repo's for everything (d...i...r...t... s...l...o...w...)

I noticed the poor speed performance when I installed a couple of packages.  When I used apt-get to install a package, I could REALLY see how slow it was.

---

