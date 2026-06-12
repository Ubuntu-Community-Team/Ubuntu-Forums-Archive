---
title: "Ubuntu as an NAS (Network-attached Storage) ?"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by CharlesMRhoads on 2013-12-05
Greetings,

I've looked around a bit in the forums and on the software in Ubuntu so I hope I am not missing some extremely obvious things here (which is why I am hear asking!).

I'm an avid Windows user having had been an MCSE, I'm currently an Android Developer but save Android, I haven't REALLY delved into Linux until now (partly because of always going back to Windows knowing it so well) so some of my purpose herein is to force me to finally break down and learn Linux.

(Background wall of text done)

I'm coming off of using a WD Personal Cloud NAS that has failed on me three times now and have finally decided this failure rate is too high for me to reasonably consider continuing using it. I looked at other NAS solutions on the market and was appalled to learn that with the availability of ATOMs today (or even Raspberries if I wanted to go that route), I could build my own NAS for about 1/3 to a 1/4 of the price anyone wants for a reasonably reliable good NAS solution. 

I got my hardware figured out now: ASUS AT3N7A-I Mobo, ATOM D2700, 2 GB of memory (upgradable to 4 if needed) and a nice Mini-ITX case from Coolermaster that can house 4 drives.

Software is my problem now.

I'm trying very much to resist the urge to throw some form of Windows on this box simply because I know it well enough to do mostly what I want it to it. I'm trying to use this as a way to finally force myself to get my feat wet in full Linux. But beyond that, I know Windows isn't going to be nearly as efficient with the resource management and it would probably be foolish to throw Windows on to hide from stepping out of my comfort zone. Conversely, I've considered throwing Android on it because I will be able to make it do what I want, but on the same token I would be coping out; besides Android acting as a server isn't extremely practical (though it can) for many of many similar-ish reasons I don't want to use Windows on this. Android is a consumer OS after all.

In playing around with a Live Boot version of Ubuntu I'm having trouble figuring out a few pieces I really need to get going software wise and I feel like I am missing some very obvious points, but here's what I am trying to make Ubuntu able to do:

- Unified logons (hopefully) for all that follows. I'd prefer some sort of account management tool that I can enable / disable the following services.
- The ability to have the device be accessible from the internet (DDNS)
- VNC for control over the device from remote locations
- FTP Server
- Samba Server
- Some sort of media server (like Twonky, though I was never happy with Twonky).
- Preferably some sort of means to access the files easily over Android remotely (Similar to WD's My Cloud App [https://play.google.com/store/apps/details?id=com.wdc.wd2go](https://play.google.com/store/apps/details?id=com.wdc.wd2go))
- A web interface would also be nice but not needed
- Backup tools for the device itself (Probably some sort of RAID tool)

Generally, these are the things I hope to establish on the device but if anyone can give me some high recommendations on the best way to go about any of this on the software end, I'd greatly appreciate it. 

Thanks for any help!

---

### Post by Kirboosy on 2013-12-05
Let me be the first to welcome you the forums! :D

If the server is truly going to be a server I would recommend installing [Ubuntu Server]("http://www.ubuntu.com/download/server") 12.04 on it. If you plan on using it occasionally like a regular desktop then look at a lighter version of Ubuntu such as [Lubuntu]("http://www.lubuntu.net/") or [Xubuntu]("http://xubuntu.org/").

> -Unified logons (hopefully) for all that follows. I'd prefer some sort of  account management tool that I can enable / disable the following  services.
You should be able to setup local accounts on the box and grant or deny access to services based on groups and permissions.
> - The ability to have the device be accessible from the internet (DDNS)
As long as you setup your network correctly this shouldn't be any different than your windows computers.
> - VNC for control over the device from remote locations
You can use VNC but there are several ways to communicate with your server. I would highly recommend [SSH]("https://help.ubuntu.com/community/SSH"). You could even run both VNC and SSH and have two methods of talking to it. 
> - FTP Server
Piece of cake. Ubuntu has a [guide]("https://help.ubuntu.com/10.04/serverguide/ftp-server.html") on it. It is listed for 10.04 but it will still work just fine with newer versions.
> - Samba Server
Another super simple item to setup. [Samba Setup guide]("https://help.ubuntu.com/community/Samba/SambaServerGuide")
> - Some sort of media server (like Twonky, though I was never happy with Twonky).
I personally use [XBMC]("http://xbmc.org/") for this. I can stream any video I want to send to it. Setup is really straight forward and easy.
> - Preferably some sort of means to access the files easily over Android remotely (Similar to WD's My Cloud App [https://play.google.com/store/apps/d...=com.wdc.wd2go]("https://play.google.com/store/apps/details?id=com.wdc.wd2go"))
This is easy too. Since you will have FTP and SSH running you can use [ES File Explorer]("https://play.google.com/store/apps/details?id=com.estrongs.android.pop&hl=en") from your smartphone to talk to your server
> - A web interface would also be nice but not needed
A web interface for what? For controlling your box or just to have a webserver that is hosting a website?
> - Backup tools for the device itself (Probably some sort of RAID tool)
There are many different tools to do this. [DejaDup]("https://launchpad.net/deja-dup") comes to mind but there are a few others out there. Another one that comes to mind is [luckyBackup]("http://luckybackup.sourceforge.net/")

Hope that helps!
~Caboose

---

### Post by CharlesMRhoads on 2013-12-05
Thankyou much Caboose885!

I was toiling between Desktop and Server already but didn't really know the difference exactly. From some of what I've been able to read up on it, it seems Server has more packages it comes with pre-enabled and less GUI.

I had concerns that the difference between the two would be the difference between Windows NT Workstation and Windows NT Server :-|. IE You can do just about everything you can on one as you can on the other except Server allows you to do 3 or 4 ever so super critical things. 

That being said, I think I'd prefer to run the desktop version because in an ideal world, this things primary purpose will be a file server and its secondary purpose will be a lite entertainment center if I can configure it streamlined enough that the average dummy can sit down and use it (because far too many people in the house won't be able to grasp its usage otherwise). 

I've actually already decided I'm going to install FreeNAS on a ATA DOM so I can get everything up and running asap because, frankly, I'm evaluating my time and until January I'm not going to have time for the work I should put in to make sure I setup Linux right. Then I'm installing an 80 GB HDD just for Linux so I can hot swap between the two depending on which OS I boot into (Yea, I guess I said Dual Boot the long way, lol). 

Your links are very useful though. It's going to help facilitate playing with the Linux setup but what would be really awesome is if there's something almost like FreeNAS that runs on Linux.

Thanks again for the response.

---

### Post by Lars Noodén on 2013-12-05
FreeNAS is a distro based on FreeBSD.  Both Linux and FreeBSD operate on an a la carte plan.  Distros like FreeNAS or Ubuntu just happen to pre-bundle some applications for you.   FreeNAS, like any distro starts with a core and then things are added to it.  As mentioned above, you can start with Ubuntu Server, which will give you a rather bare bones setup, and then add the services you want.  You are free to add anything you see in FreeNAS or to leave things out if you wish.  
 
About [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp), you probably meant SFTP.  It's part of the package openssh-server and needs no additional configuration for basic operation.  You'll find SFTP clients in Nautilus and other file managers or in custom apps like FileZilla.

---

### Post by Kirboosy on 2013-12-05
Ubuntu server and Desktop versions are significantly different out of the box. However, you can make a desktop version of Ubuntu run server functions. There aren't any limitations placed on the version like Windows. Ubuntu is the same core across the board its just the default software that is bundled with it.

FreeNAS is BSD based which is similar to Linux. Getting your feet wet with Unix in general will help you across the board.

~Caboose
PS If you could mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") that would be greatly appreciated.

---

### Post by ted.drain on 2014-01-07
I've in a similar situation (returning my WD my cloud this week) and have been doing a lot of research lately (QNap, FreeNAS, Ubuntu, etc).  I've settled on an Ubuntu server w/ SnapRAID and other various services (ssh, ftp, samba, plex, etc).  Today I found this: [http://owncloud.org/](http://owncloud.org/) which is a free, dropbox style application that has a web interface and an android app ($.99) which makes it really easy to use from mobile phones.  The only down side to OwnCloud that I see is having to learn how to set up and harden an Apache install on the server.

FYI - my build is here: [http://pcpartpicker.com/p/2xoE0](http://pcpartpicker.com/p/2xoE0).  I decided to use an i3-4130 so I can use AES-NI for full disk encryption (NAS theft deterrent) and transcode multiple media streams w/ plex.

---

### Post by mastablasta on 2014-01-08
i though RAM limit on Atoms maxed at 2GB :-O

like freeNAS doesn't have each share of issues.

want stuff preconfigured with nice web interface but linux based? have a look at Zentyal (Ubuntu based), Openmediavault (Debian based and probably a tad better than freenas at least in a few reviews i read), ClearOS (CentOS/Redhat based) or you can just install ubuntu server and add webmin to it for example.

linux (and BSD) are modular. so you can install server, then just install desktop environment package (for example Lubuntu or Xubuntu or Ubuntu desktop) or windows manager (IceWM, openbox...) of your choice if you want one. or you just install CLI programms you need and leave it headless (no monitor, keyboard) and control it via web or SSH.

---

