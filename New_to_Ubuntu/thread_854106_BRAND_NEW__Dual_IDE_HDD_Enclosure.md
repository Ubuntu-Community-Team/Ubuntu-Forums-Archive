---
title: "BRAND NEW  Dual IDE HDD Enclosure"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by itouch-nas on 2008-07-09
Hi,
I am newbie, would like setup home-server with  Dual IDE HDD Enclosure + (2x300gb)
FEATURES:
  Supports RAID and JBOD functions so I can even install 2 drives to expand data capacity up to 1 Terabyte (TB) (500GB x2) - . - . - . - . - . - . -
  Provides an instant share of photos, videos, music and data over your network
  Easy configuration using the web based management application - no software installation required
  Built-in SAMBA server for cross-platform transfer among different operating systems
  Built-in FTP server to provide Internet data transfer between external users
  Built-in USB printer server - just connect your printer to the enclosure's USB port to enable printer sharing without occupying any PC's resources
  Easy installation and low support cost, suitable for home or office networks
  Aluminium housing with large fan design to prevent overheating
 
SPECIFICATIONS:
  Chipset: Storlink Centroid SL3316-G - - - - - - - - , - -
  Interface: RJ45 (LAN), USB1.1 (for print server)
  Data Transfer Rate: Up to 8MB/s (networking)
  Partition configuration: FAT32/ EXT2 EXT3
  RAID support: RAID 1 / RAID 0
 
Supported Protocol:
TCP/IP, NBNS (Net BIOS Name Server), Microsoft Networks (CIFS/SMB), DHCP Server/Client (Auto detection), SNTP Client
  Weight: 700g (excluding hard drive)
  Dimensions: 120 x 180 x 80mm
 
Minimum System Requirements:
Apple Safari, Linux Mozilla, IE 5.x, Netscape 6.2 up
Win 98SE / ME / 2000 / 2003 / XP / Vista
Mac OS X
  
please help step by step many thanks

---

### Post by Xerp on 2008-07-09
Step 1 - Install Ubuntu 8.04 onto your computer
Step 2 - Install all the updates
Step 3 - Attach your SAN to your computer running Ubuntu 
Step 4 - Use Firefox to connect to the device's web interface to configure shares and partitions
Step 5 - Enjoy!

---

### Post by itouch-nas on 2008-07-09
> **Xerp said:**
> Step 1 - Install Ubuntu 8.04 onto your computer
Step 2 - Install all the updates
Step 3 - Attach your SAN to your computer running Ubuntu 
Step 4 - Use Firefox to connect to the device's web interface to configure shares and partitions
Step 5 - Enjoy!

Thanks Xerp very quick reply ,Which release do I need ?
Ubuntu 8.04 LTS Desktop Edition - Supported to 2011 
Ubuntu 8.04 LTS Server Edition - Supported to 2013

Cheers

---

### Post by Jive Turkey on 2008-07-09
here's a link to the Ubuntu download area [http://releases.ubuntu.com/hardy/]("http://releases.ubuntu.com/hardy/") It looks like the unit has some Linux operating system already.  Instead of connecting it to your computer you could connect it to your router instead.  If you don't have or want Ubuntu you could probably just open the SAN's IP address in a browser.  It should offer you some security options out of the box, I recommend locking it down as a first step before someone you don't know takes control of it.

Edit: on your computer you would want the desktop edition, you probably could but dont need to install the server edition on the SAN.  The desktop edition has Gnome and some aplications which drive the GUI, the server has only the command prompt and is intended to run without a monitor or anything but a network cable attached to it.

---

### Post by Xerp on 2008-07-09
You can use either the Server or the Desktop edition, depending on how you are going to use your computer. For example, if you will be using your computer as a regular desktop then install the Desktop edition.

---

### Post by itouch-nas on 2008-07-09
> **Xerp said:**
> You can use either the Server or the Desktop edition, depending on how you are going to use your computer. For example, if you will be using your computer as a regular desktop then install the Desktop edition.

I just Install Desktop edition Ubuntu 8.04 onto my computer
an attach SAN to computer running Ubuntu=ok
 how Network Storage System can be set up to be accessible directly from the Internet via a web browser or FTP. Files can be available publicly.?
 
Thanks

---

