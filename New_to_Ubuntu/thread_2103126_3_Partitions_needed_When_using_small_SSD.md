---
title: "3 Partitions needed? When using small SSD"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by cwkid on 2013-01-09
Hello

I have been reading various Ubuntu HTPC setup guides and several of them recommend when installing Ubuntu to create 3 disk partitions. One for root one for /home and one for swap. Is this needed when just using a small 60GB Solid State Drive ?

All media data will be stored on another server PC.

Thanks in advance.

---

### Post by Pjotr123 on 2013-01-09
In my opinion a separate /home is a needless complication:
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-)
(item 15, right column)

---

### Post by Grenage on 2013-01-09
It's not really necessary, and I rarely bother; not that there aren't times when it's useful.  With an HTPC, you might not even want to bother with swap at all.

---

### Post by cwkid on 2013-01-09
Wow fast replies thanks guys!

I still haven't bought the parts for the HTPC but planning on using an Intel DH67CF ITX Media motherboard, i3 2105 IGP, 4GB RAM, 60GB SDD etc. And XBMC. 

I am very new to both Linux and XBMC having come from a Windows Media Center background but hoping to migrate if things work out well!

---

### Post by cwkid on 2013-01-09
I managed to install Ubuntu 12.10 Desktop on a test PC OK. However want to swap to Ubuntu Server 12.10 but having issues with the boot CD at the moment.

---

### Post by mastablasta on 2013-01-09
> **cwkid said:**
> I managed to install Ubuntu 12.10 Desktop on a test PC OK. However want to swap to Ubuntu Server 12.10 but having issues with the boot CD at the moment.
 
 
if you want to swap just uninstall the desktop environment and you will basically get the server edition. then install the server packages you want/need.
 
if you are reinstalling - make sure md5sum of the image is good and that the burn is good (if you are using DVD).
 
also what is the benefit of SSD in this PC?
 
and also have you checked this project: [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by Grenage on 2013-01-09
To be honest, SSDs are so cheap now, it's often cheaper to put one in rather than a basic mechanical for boot purposes.  They're pretty handy for media centres, being fast, low profile, low power, low heat, and cheap!

---

### Post by cwkid on 2013-01-09
Hi

OK I am installing Ubuntu Server 12.10 now, CD booting OK I had something set wrong in the BIOS. 

Under Partitioning I selected Guided - Use Entire Disk - Install LVM 
or something along those lines. 

When I get to the desktop how can I view the partition information? To see what partitions have been created etc. 

I always use SSD drives in HTPC's they make them boot fast. 

I could just use OpenElec but I want to learn about Linux / Ubuntu and have a system that is not restricted in what I can do with it etc. XBMCbuntu is another option but my friend who builds  Linux HTPC's for a living recommended using Ubuntu Server and XBMC.

---

### Post by Paqman on 2013-01-09
> **mastablasta said:**
> 
and also have you checked this project: [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

I'd steer clear of Mythbuntu if you're just after a box to stream content from the web or a source on your network. XBMC will do that job with waaaaaaaay less bother. MythTV is the route to go down if you want to watch and record TV, but is pretty complicated and fiddly to set up (or it was the last time I looked at it). XBMC you just install it on top of Ubuntu, set it as the default DE and you're done.

---

### Post by cwkid on 2013-01-09
Now its asking me what predefined collections of software I want to install ? It never asked me this on the desktop version of Ubuntu. 

OpenSSH server
DNS server
LAMP server 
Mail server
PostgreSQL Database
Print Server
Samba File Server
Tomcat Java Server
Virtual Machine
host
Manual package section

I just need the bare minimum for a HTPC build.

---

### Post by cwkid on 2013-01-09
> **Paqman said:**
> I'd steer clear of Mythbuntu if you're just after a box to stream content from the web or a source on your network. XBMC will do that job with waaaaaaaay less bother. MythTV is the route to go down if you want to watch and record TV, but is pretty complicated and fiddly to set up (or it was the last time I looked at it). XBMC you just install it on top of Ubuntu, set it as the default DE and you're done.

I do plan on using Live TV / PVR in XBMC eventually with UK Freeview. I am currently using this feature in Windows Media Center. I have a 7.5TB Windows Home Server with lot of movies and music on it, I plan to keep this as the back-end for now.

"set it as the default DE" 

Can you explain this a little further please

Thanks

---

### Post by Paqman on 2013-01-09
> **cwkid said:**
> 
"set it as the default DE" 

Can you explain this a little further please


On Linux you can choose to use a different Desktop Environment when you log in. The standard Ubuntu one is called Unity, but others exist (KDE, XFCE, etc). XBMC provides it's own DE so you don't need to run one on top of the other.

Set your machine to log you in automatically, then log out and click the icon by your user name and pick XBMC from the list. From then on when you hit the power button your machine will boot straight into XBMC.

---

### Post by cwkid on 2013-01-09
> **Paqman said:**
> On Linux you can choose to use a different Desktop Environment when you log in. The standard Ubuntu one is called Unity, but others exist (KDE, XFCE, etc). XBMC provides it's own DE so you don't need to run one on top of the other.

Set your machine to log you in automatically, then log out and click the icon by your user name and pick XBMC from the list. From then on when you hit the power button your machine will boot straight into XBMC.

OK excellent, sounds a bit like changing the explorer shell in Windows. So I assume the desktop will still be accessible?



Thanks

---

### Post by Paqman on 2013-01-09
> **cwkid said:**
> OK excellent, sounds a bit like changing the explorer shell in Windows.

Yep. Linux is very modular though, so things like this are really easy to do. Not as scary as messing about with Windows in the same way.

Linux's modularity is why it's really good on things like HTPCs with smallish disks. You don't need to have any more parts of the OS installed than you actually need. My HTPC sites on only a handful of GB on the disk and runs very happily on 1GB of RAM.

> 
So I assume the desktop will still be accessible?


Yep, one of the options in XBMC is to log out instead of shutting down. This will drop you back at the login screen and you could choose to log in to a more traditional desktop.

---

### Post by mastablasta on 2013-01-09
> **Grenage said:**
> To be honest, SSDs are so cheap now, it's often cheaper to put one in rather than a basic mechanical for boot purposes. They're pretty handy for media centres, being fast, low profile, low power, low heat, and cheap!
 
ah yes low power and heat. yeah maybe that.
 
cheap? not here. cheaper than they were yes, but not cheap. however if you don't need large storage it gues they are ok. though i would rather use something for large storage that can play media normally. additionally, how many times do you boot a server? i guess again if oyu'd like to have ti turned off... but then wouldn't it be cheaper and more cost effective to just use a USB stick for OS and remove the swap part? i mean for 70 EUR (WD) here you get a 1 TB hard disk and a few more for the USB key to hold the server and such... cheapest 60 GB SSD they sell here (Kingston) is 63 EUR. intel's is 72 EUR
 
> **cwkid said:**
> Now its asking me what predefined collections of software I want to install ? It never asked me this on the desktop version of Ubuntu. 
 
OpenSSH server
DNS server
LAMP server 
Mail server
PostgreSQL Database
Print Server
Samba File Server
Tomcat Java Server
Virtual Machine
host
Manual package section
 
I just need the bare minimum for a HTPC build.
 
well yes. it's asking what kind of servers you want to run. like i said you couldn't have just removed the desktop and install some of these.... :-)
you will porbably need samba since you plan to do sharing with windows. though maybe not necessarily server... you probably won't need mail and LAMP and SQL database (not sure what XBMC uses but it will get installed as dependency anyway) these are mostly used for webserver. print server also can be remove as most others. but in any case you can easilly install them later on using tasksel for example (note you can't use tasksel to uninstall !).

---

### Post by cwkid on 2013-01-09
I guess ideally you would want to have the Ubuntu UI locked down and only the XBMC UI available to users, so they can't get to the desktop and mess up settings, but have a way to unlock the desktop for admin, I use to do this in Windows using a program called dWinLock.

---

### Post by cwkid on 2013-01-09
> **mastablasta said:**
> 
well yes. it's asking what kind of servers you want to run. like i said you  couldn't have just removed the desktop and install some of these.... :-)
you will porbably need samba since you plan to do sharing with windows. though maybe not necessarily server... you probably won't need mail and LAMP and SQL database (not sure what XBMC uses but it will get installed as dependency anyway) these are mostly used for webserver. print server also can be remove as most others. but in any case you can easilly install them later on using tasksel for example (note you can't use tasksel to uninstall !).

Too late I already blew away the desktop installation. 

I will be using SMB in XBMC to access my existing Windows Home Server shared folders. I have tested this already and it works fine. 

As I wont be having any media stored locally on the HTPC itself I don't think I need to install Samba file server? 

Do I need OpenSSH Server? 

All the other options I dont think I need on the HTPC client. 

I will be installing MySql on to the Windows Home Server (WHS) for centralized XBMC database for video book marks, watched status and thumbnails I think. 

Thanks

EDIT: I didnt select any of those server components and selected Manual package selection as that was the only other option to progress, its now on Select and Install software and preparing / configuring stuff with a percentage progress indicator.

---

### Post by mastablasta on 2013-01-09
> **cwkid said:**
> Do I need OpenSSH Server? 

 
if you want to securely connect to server remotely via SSH. maybe you want to play a movie at home while you are away on holiday? why? because you can..... :-)

---

### Post by cwkid on 2013-01-09
> **mastablasta said:**
> if you want to securely connect to server remotely via SSH. maybe you want to play a movie at home while you are away on holiday? why? because you can..... :-)

Excuse my ignorance, SSH is the command terminal ? For accessing and configuring Ubuntu via command line ? 

Obviously I am going to have to learn some Linux commands to get by but the more I can stick with the UI maybe better for a Windows guy like myself. 

Also looking for a good dummy guide book for beginners, currently reading the Getting Started with Ubuntu 12.10 PDF manual to get use to the user interface etc.

---

### Post by cwkid on 2013-01-09
Now I am in trouble lol, the Ubuntu Server installation has finished / rebooted and when I login I just get the command prompt. 

I was expecting the server version to also have the Unity desktop ? 

Man it sucks being a newbie again.. 

EDIT: Seems I might be able to add a Server Gui

[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Thanks

---

### Post by Paqman on 2013-01-09
> **cwkid said:**
> 

As I wont be having any media stored locally on the HTPC itself I don't think I need to install Samba file server? 


Nope. You only need the full Samba package to serve files. The desktop version of Ubuntu comes with the Samba client packages already, but I don't know about the server edition. You may need to install them.

> Do I need OpenSSH Server? 

Not if you're accessing the shares over SMB/CIFS, no.

> I will be installing MySql on to the Windows Home Server (WHS) for centralized XBMC database for video book marks, watched status and thumbnails I think.

Interesting, didn't know XBMC could do that.

---

### Post by cwkid on 2013-01-09
> **Paqman said:**
> 

Interesting, didn't know XBMC could do that.

I followed this setup guide for MySQL

[http://lifehacker.com/5634515/how-to-synchronize-your-xbmc-media-center-across-every-room-in-the-house](http://lifehacker.com/5634515/how-to-synchronize-your-xbmc-media-center-across-every-room-in-the-house)

Paqman so are you using the desktop version of Ubuntu with XBMC ?

---

### Post by Paqman on 2013-01-09
> **cwkid said:**
> 
Paqman so are you using the desktop version of Ubuntu with XBMC ?

Sort of. I installed a [minimal system]("https://help.ubuntu.com/community/Installation/MinimalCD") and added only the stuff I needed, but I did install the core desktop packages.

---

### Post by Grenage on 2013-01-09
I'm using the full version, although it boots into XBMC.  I've never actually needed to use the Ubuntu desktop, but as I had ample space, I did so 'just in case'.

All admin is done via SSH.

---

### Post by cwkid on 2013-01-09
> **Grenage said:**
> I'm using the full version, although it boots into XBMC.  I've never actually needed to use the Ubuntu desktop, but as I had ample space, I did so 'just in case'.

All admin is done via SSH.

By full version I presume you mean the desktop version. 

I started a new thread about this on the XBMC forums

[http://forum.xbmc.org/showthread.php?tid=151422](http://forum.xbmc.org/showthread.php?tid=151422)

Going to be a steep learning curve with no desktop UI and having to use all command line.

---

### Post by cwkid on 2013-01-09
> **Paqman said:**
> Sort of. I installed a [minimal system]("https://help.ubuntu.com/community/Installation/MinimalCD") and added only the stuff I needed, but I did install the core desktop packages.

So what is the desktop called you are running Unity or something else? KDE / XFCE

---

### Post by Paqman on 2013-01-09
> **cwkid said:**
> So what is the desktop called you are running Unity or something else? KDE / XFCE

When I originally installed it I used the core packages from the Gnome desktop on Ubuntu 10.04. I've since upgraded it to 12.04 and IIRC it does now run Unity. TBH I haven't logged into the desktop in so long I can't remember exactly what's on there.

---

### Post by mastablasta on 2013-01-11
> **cwkid said:**
> Excuse my ignorance, SSH is the command terminal ? For accessing and configuring Ubuntu via command line ? 

well it's a secure network protocol:
from wiki
 
> **Secure Shell** (**SSH**) is a cryptographic [network protocol]("http://en.wikipedia.org/wiki/Network_protocol") for secure data communication, remote shell services or command execution and other secure network services between two networked computers that connects, via a [secure channel]("http://en.wikipedia.org/wiki/Secure_channel") over an insecure network, a server and a client (running [SSH server]("http://en.wikipedia.org/wiki/SSH_server") and [SSH client]("http://en.wikipedia.org/wiki/SSH_client") programs, respectively).[[1]]("http://en.wikipedia.org/wiki/Secure_shell#cite_note-rfc-1") 
 
 > 
Obviously I am going to have to learn some Linux commands to get by but the more I can stick with the UI maybe better for a Windows guy like myself. 
 
 
again from wiki and as you've found out there is a GUI for that: [http://en.wikipedia.org/wiki/Comparison_of_SSH_clients](http://en.wikipedia.org/wiki/Comparison_of_SSH_clients)
 
 
i am also a GUI person since i ran norton command on dos. anyway... plenty of commands have GUI. there is not need to use terminal command, but if oyu knwo it it's a bonus as there is plenty additional setups you might be able to do via command line-

---

