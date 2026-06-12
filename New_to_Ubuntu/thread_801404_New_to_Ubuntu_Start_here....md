---
title: "New to Ubuntu? Start here..."
date: 2007-05-13
forum: New to Ubuntu
---

### Post by ugm6hr on 2007-05-13
Hi.

**Welcome to Ubuntu and the Forums.**

Finding your way around Ubuntu and the documentation for it can be a bit tricky.  This thread will hopefully help point you towards reliable sources of information, and also tell you how to get the most out of these forums when a search doesn't reveal the answer.


**Reading Material to get you started...**

[Free Ubuntu Pocket guide by Keir Thomas]("http://www.ubuntupocketguide.com/")
[Ubuntu website (Canonical)]("http://www.ubuntu.com/")
[Official Ubuntu documentation]("https://help.ubuntu.com/")
[Community documentation (searchable)]("https://help.ubuntu.com/community/")
[Psychocats Ubuntu guide]("http://www.psychocats.net/ubuntu")
[ZabiGG's Newbie 101]("http://ubuntuforums.org/showthread.php?t=790485")
[Comprehensive list of weblinks about Ubuntu]("http://ubuntuforums.org/showthread.php?t=232059")
[Ubuntu-centric Google Custom Search]("http://www.google.com/coop/cse?cx=001461844748502826593:hh-ikmexth4")

[B]
Links for Specific Advice[/B] (posted below)

[How to get and install Ubuntu]("http://ubuntuforums.org/showthread.php?p=5004671#post5004671")
[Using Ubuntu]("http://ubuntuforums.org/showthread.php?p=5004723#post5004723")
[Multimedia problems and Installing Codecs]("http://ubuntuforums.org/showthread.php?p=5004922#post5004922")
[Installing Programs & Applications in Ubuntu]("http://ubuntuforums.org/showthread.php?p=5004960#post5004960")
[Specific Hardware How-tos]("http://ubuntuforums.org/showthread.php?p=5004976#post5004976")
[Doesn't work? Ask for help]("http://ubuntuforums.org/showthread.php?p=5005011#post5005011")
[Books about Ubuntu / Linux]("http://ubuntuforums.org/showthread.php?p=5005069#post5005069")
[User submitted links]("http://ubuntuforums.org/showthread.php?p=5006304#post5006304")
[Ubuntu News & Blog sites]("http://ubuntuforums.org/showthread.php?p=5008928#post5008928")

 
If you've written a how-to or used another you found helpful, please tell us about it. :)
[B]
No requests for help here though![/B]

In an attempt to keep this thread compact with helpful posts only, I have moved all responses, thank-you posts etc to a derivative thread.

Please post any future comments (or additional help) in the [Beginner's Team sticky]("http://ubuntuforums.org/showthread.php?t=848814").

---

### Post by sharks on 2008-05-15
On how to install anything on Ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Medibuntu repository:(Multimedia,Entertainment & Distractions In Ubuntu)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Compiz extra plugins:

[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

Helpful Uubntu commands:
Privileges
sudo command - run command as root
sudo su - open a root shell
sudo su user - open a shell as user
sudo -k - forget sudo passwords
gksudo command - visual sudo dialog (GNOME)
kdesudo command - visual sudo dialog (KDE)
sudo visudo - edit /etc/sudoers
gksudo nautilus - root file manager (GNOME)
kdesudo konqueror - root file manager (KDE)
passwd - change your password


Display
sudo /etc/init.d/gdm restart - restart X (GNOME)
sudo /etc/init.d/kdm restart - restart X (KDE)
(file) /etc/X11/xorg.conf - display configuration
sudo dpkg-reconfigure -phigh xserver-xorg - reset X configuration
Ctrl+Alt+Bksp - restart X display if frozen
Ctrl+Alt+FN - switch to tty N
Ctrl+Alt+F7 - switch back to X display


System Services¹
start service - start job service (Upstart)
stop service - stop job service (Upstart)
status service - check if service is running (Upstart)
/etc/init.d/service start - start service (SysV)
/etc/init.d/service stop - stop service (SysV)
/etc/init.d/service status - check service (SysV)
/etc/init.d/service restart - restart service (SysV)
runlevel - get current runlevel
Package Management¹
apt-get update - refresh available updates
apt-get upgrade - upgrade all packages
apt-get install pkg - install pkg
apt-get remove pkg - uninstall pkg
apt-get autoremove - remove obsolete packages
apt-get -f install - try to fix broken packages
dpkg &#8211;configure -a - try to fix broken packages
dpkg -i pkg.deb - install file pkg.deb
(file) /etc/apt/sources.list - APT repository list
Network
ifconfig - show network information
iwconfig - show wireless information
sudo iwlist scan - scan for wireless networks
sudo /etc/init.d/networking restart - reset network
(file) /etc/network/interfaces - manual configuration
ifup interface - bring interface online
ifdown interface - disable interface
Special Packages
ubuntu-desktop - standard Ubuntu environment
kubuntu-desktop - KDE desktop
xubuntu-desktop - XFCE desktop
ubuntu-minimal - core Ubuntu utilities
ubuntu-standard - standard Ubuntu utilities
ubuntu-restricted-extras - non-free, but useful
kubuntu-restricted-extras - KDE of the above
xubuntu-restricted-extras - XFCE of the above
build-essential - packages used to compile programs
linux-image-generic - latest generic kernel image
linux-headers-generic - latest build headers
Firewall¹
ufw enable - turn on the firewall
ufw disable - turn off the firewall
ufw default allow - allow all connections by default
ufw default deny - drop all connections by default
ufw status - current status and rules
ufw allow port - allow traffic on port
ufw deny port - block port
ufw deny from ip - block ip adress
Application Names
nautilus - file manager (GNOME)
dolphin - file manager (KDE)
konqueror - web browser/filemanager (KDE)
kate - text editor (KDE)
gedit - text editor (GNOME)


System
Recovery - Type the phrase &#8220;REISUB&#8221; while
holding down Alt and SysRq (PrintScrn) with
about 1 second between each letter. Your system
will reboot.
lsb_release -a - get Ubuntu version
uname -r - get kernel version
uname -a - get all kernel information

If GRUB is corrupted :
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

To know all commands in Terminal, press tab twice in terminal.


To read and write ntfs:
sudo aptitude install ntfs-config

---

### Post by sharks on 2008-05-16
Is this useful?

---

### Post by ugm6hr on 2008-05-20
[Official Ubuntu 8.04LTS Installation guide]("https://help.ubuntu.com/8.04/switching/installing.html")
[Community guide to Installation]("https://help.ubuntu.com/community/Installation")
[Switching from Windows]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows")
[Hermanzone Illustrated Dual-boot guide]("http://users.bigpond.net.au/hermanzone/")
[AI Common Sense approach to upgrading]("http://ubuntuforums.org/showthread.php?t=644478")
[Psychocats Getting Ubuntu CD]("http://www.psychocats.net/ubuntu/iso")
[How-to-forge guide to installation and setup of Ubuntu 8.04LTS]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron")
[Video of installation of Ubuntu on a whole hard drive]("http://ubuntuforums.org/showthread.php?p=5272751")

---

### Post by ugm6hr on 2008-05-20
[Official guide to Ubuntu 8.04LTS]("https://help.ubuntu.com/")
[Official guide to switch from Microsoft Windows to Ubuntu 8.04LTS]("https://help.ubuntu.com/8.04/switching/index.html")
[Psychocats guide to finding Terminal]("http://www.psychocats.net/ubuntu/terminal")
[Mazza558 guide to using Terminal]("http://ubuntuforums.org/showthread.php?t=714338")

---

### Post by ugm6hr on 2008-05-20
[Official guide to Media]("https://help.ubuntu.com/8.04/musicvideophotos/C/index.html")
[Community guide to Proprietary formats]("https://help.ubuntu.com/community/RestrictedFormats")
[ubuntu-freak's comprehensive guide to all things multimedia]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by ugm6hr on 2008-05-20
[Forestpixie & Starcraftman's Complete guide to program installation in Ubuntu]("http://ubuntuforums.org/showthread.php?t=781352")
[NikoPSK's guide to updating and installing in Ubuntu]("http://ubuntuforums.org/showthread.php?t=644478")

---

### Post by ugm6hr on 2008-05-20
Use Ctrl+F to find key words if this list gets too long

[ZabiGG's Hardware Links 101]("http://ubuntuforums.org/showthread.php?t=820667")
[NVidea drivers]("http://ubuntuforums.org/showthread.php?t=990978")
[How to install Ubuntu on your HP Laptop]("http://ubuntuforums.org/showthread.php?t=528618")
[Atheros AR5007 (AR242x) wifi - Ubuntu 8.04]("http://ubuntuforums.org/showthread.php?t=792158")
[Speedtouch 330 USB ADSL Modem]("http://ubuntuforums.org/showthread.php?t=797804")

---

### Post by ugm6hr on 2008-05-20
[How to use the forum]("http://ubuntuforums.org/showthread.php?t=726219")
[How to ask the question to get the right answer]("https://help.ubuntu.com/community/GettingAnswers")
[Use Google to search in this Forum]("http://www.google.co.uk/search?hl=en&q=site%3Aubuntuforums.org&btnG=Search&meta=") - just add the search term after the existing entry
[Can't Connect to Internet / Wifi Problems]("http://ubuntuforums.org/showpost.php?p=5024425&postcount=1")
[ZabiGG's How-to search or ask for help]("http://ubuntuforums.org/showthread.php?t=796449")

---

### Post by ugm6hr on 2008-05-20
[Free Ubuntu Pocket guide by Keir Thomas]("http://www.ubuntupocketguide.com/")
[The Official Ubuntu Book]("http://search.barnesandnoble.com/The-Official-Ubuntu-Book/Benjamin-Mako-Hill/e/9780137151028")
[Ubuntu for Non-Geeks]("http://nostarch.com/ubuntu_3.htm")
[A Practical Guide to Ubuntu Linux]("http://www.sobell.com/UB1/index.html")
[Twenty Free Linux Books ]("http://ubuntuforums.org/showthread.php?t=1118334")

---

### Post by ugm6hr on 2008-05-20
[Linux on Desktop blog]("http://linuxondesktop.blogspot.com/2008/03/couple-of-ubuntulinux-tips.html")
[UbuntuHQ How-TO index]("http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos")
[billgoldberg's Linux Owns blog]("http://linuxowns.wordpress.com/")
[ZabiGG's How-To's 101]("http://ubuntuforums.org/showthread.php?t=820667")
[Useful Ubuntu Links]("http://www3.telus.net/lordfoul/pics/useful%20ubuntu%20links/useful%20unbuntu%20links.html")

---

### Post by ugm6hr on 2008-05-21
[Tombuntu - Ubuntu News and Tips]("http://tombuntu.com/")
[Ubuntu Geek - Tips & How-Tos]("http://www.ubuntugeek.com/")
[Wortks With U - Ubuntu News & Blog]("http://www.workswithu.com/")

---

### Post by mamyte18 on 2008-05-29
Premium Membership

Upgrade your account and earn more with Bux.to. The Premium Membership comes with the following features: 
» Surf Ads guaranteed loaded with minimum 20 ads every Day!
» Earn $0.0125 each click and $0.0125 each click from your referrals.
» Priority Payments.
Exclusively for premium members: Get your Prepaid Bux.to MasterCard®
Earnings Example
» You click 20 ads per day = $0.25
» 25 premium referrals click 20 ads per day = $6.25
» Your monthly earnings = $195.00
» Your total annual earnings = $2,340.00
Processing time: 2 working days.
I'm so proud of everybody, who clicks for bux.to and everybody who works at bux.to, they made a fantastic system. You are clicking for a wanderful system. I joined bux.to in the middle of January, but I have to admit that I wasn't brave enough to invest 500$-s with no previous knowledge about the system. So I only bought 115 refs and a premium to test bux.to and I saw that the money is comming back really fast, so in March I bought another 335 refs. So totally I invested 500$-s.

Now I reached 1000$, I duplicated my investments in 1 month. Thank you bux.to! Thanks for the clickers and the advertisers, who made bux.to a smooth running machine! Thanks for everybody, who writes success stories to make people trust the system! And finally, thanks for my referrals, especially for the guy, who bought premium membership 1 week after joining!

We have to continue our journey through the ads. Good luck for everybody!
  
Steps how to register to bux!

1 step:  [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18)   go to this site. And register here.
2 step:  [http://www.alertpay.com](http://www.alertpay.com)
Then "SIGN UP", choose your country, then "Personal Starter" and "Get Started"; and write your name and other information. Where need.
Then you will receive a message to your email address.

When the alertpay are created go to link [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18), then"I Accept the Terms of Service” and  click butoon register.   And that’s all. You are the member.

To look videos click "Surf Ads". And you will earn your money.
Good luck. Odeta.
If there are ome problems write to me I could help you I promise. [email]odetux18@yahoo.com[/email]

---

### Post by jsoreno on 2008-06-10
I'm really new to Ubuntu. . And I really want to know about this. . Hope you could help me ,maybe some tips. . thanks a lot. . :)

---

### Post by lswest on 2008-06-10
> **s3r4phim said:**
> </snip>

P.S.

Yes, ctrl+alt+backspace shuts down the X server, but annoyingly, it restarts it immediately afterward. For those wanting a command line to begin with, and then the option of choosing the desktop environment that they want afterward, do simply the following:

```

mv /etc/rc3.d/S30gdm /etc/rc3.d/K80gdm
mv /etc/rc3.d/S10xserver-xorg-input-wacom /etc/rc3.d/K80xserver-xorg-input-wacom

```

simply reverse (switch the two arguments around) the commands to make it start GNOME automatically again.

Actually, even more efficient in Ubuntu is just ```
sudo /etc/init.d/gdm stop
``` to turn it off and ```
sudo /etc/init.d/gdm start
```to turn it back on. 

*Edit* ah, sorry, you meant to enable/disable it on boot.  That could be done the way you mentioned.  Or you could do ```
#!/bin/bash
/etc/init.d/gdm stop
``` in a script (stop-gdm.sh) made executable with ```
chmod a+x stop-gdm.sh
``` moved to /etc/init.d/ with ```
mv [path of stop-gdm.sh] /etc/init.d/stop-gdm.sh
``` and then just ```
update-rc.d stop-gdm.sh defaults
``` (there may be an even easier way to do it), but that's a bit more complex (maybe too much for this thread, any mod is welcome to shorten this post/delete it if they find it out of place).

---

### Post by confused57 on 2008-06-16
This may help anyone unfamiliar with partitioning:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Ubuntu Security:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[https://help.ubuntu.com/community/UnsafeDefaults](https://help.ubuntu.com/community/UnsafeDefaults)
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

bodhi.zazen has written numerous comprehensive, helpful howto threads, in additition to the ones listed above, e.g. how to fstab:
[http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

---

### Post by sharks on 2008-06-16
I hope this will be helpful for newbies:

**10 TIPS FOR U AFTER INSTALLING OR UPGRADING UBUNTU**
[http://tombuntu.com/index.php/2008/04/25/10-tips-for-after-you-install-or-upgrade-ubuntu/](http://tombuntu.com/index.php/2008/04/25/10-tips-for-after-you-install-or-upgrade-ubuntu/)

**MAC OS X LIKE WIDGETS WITH SCREENLETS**
[http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/](http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/)

**Stop Wine From Beating Your Windows Apps With The Ugly Stick**
[http://tombuntu.com/index.php/2008/01/04/stop-wine-from-beating-your-windows-apps-with-the-ugly-stick/](http://tombuntu.com/index.php/2008/01/04/stop-wine-from-beating-your-windows-apps-with-the-ugly-stick/)

**Revolutionary New Panel Now Available in Ubuntu 7.10**
[http://tombuntu.com/index.php/2007/10/03/revolutionary-new-panel-now-available-in-ubuntu-710/](http://tombuntu.com/index.php/2007/10/03/revolutionary-new-panel-now-available-in-ubuntu-710/)

**Ten Tips for KDE 4.0 Beginners**
[http://tombuntu.com/index.php/2008/01/15/ten-tips-for-kde-40-beginners/](http://tombuntu.com/index.php/2008/01/15/ten-tips-for-kde-40-beginners/)

**Toggle Compiz with Fusion-icon in Ubuntu 8.04**
[http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)

**Animated Wallpaper with Compiz Fusion on Ubuntu**
[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu)

**Install Firefox 3 Beta 4 in Ubuntu with One Command**
[http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/](http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/)

**Five Steps to Install KDE 4.0 in Ubuntu 7.10**
[http://tombuntu.com/index.php/2008/01/14/five-steps-to-install-kde-40-in-ubuntu-710/](http://tombuntu.com/index.php/2008/01/14/five-steps-to-install-kde-40-in-ubuntu-710/)

**Testing the Gnash Flash Player in Ubuntu 7.10**
[http://tombuntu.com/index.php/2007/10/02/testing-the-gnash-flash-player-in-ubuntu-710/](http://tombuntu.com/index.php/2007/10/02/testing-the-gnash-flash-player-in-ubuntu-710/)

---

### Post by ktechman on 2008-06-19
I found this partitioning guide on the web and it gives schemes in a percentage format which I found very helpful.  

> Guide to Partitioning for Linux

In this guide I will take you through some of the tings you need to know when preparing a hard drive for Linux. Some of these things relate to performance, some to security. The first thing you should do before doing any hard drive work is to BACK UP ALL OF YOUR DATA. You've been warned.

Next thing to do is grab a pad and paper and something to drink (non-alcoholic as alcohol and partitioning doesn't mix) Partitioning is one of the lost arts of computer tuning. Let me give you some background on my experience.

First I have been able to load over 15 operating systems on the same hard drive before, all accessible from either the windows or the Linux boot managers. I have used programs like partition magic and such but I find that using the FDISK utility that comes with each operating system is just as effective and in most cases makes for far more stable a system. I have been working with hard drive geometry for over five years and during that time I have learned quite a few things. The first thing to learn is that you must do everything on paper first. "Proper Prior Planning Prevents Piss Poor Performance" as my ex-wife's father used to say.... brilliant man.

Now if you're all set we can begin. I can;t use ASCII for this since the page doesn't parse spaces correctly.(hey admin... can you make a feature that lets us draw directly into posts?)

Step One: Visualize

Draw a rectangle about the width of the page about an inch high.

Now you have the form with which to begin molding your new drive partition system. If you have multiple drives draw boxes for them too. Don't worry about proportions as this is just to visualize what you are doing.

Step Two: Positional Planning and Taking Stock

Within the box you will need to divide it into separate compartments. Each of these will represent the partition you are creating and will list what types of partitions you are creating. Before you begin slashing up this space you have to plan for what you will be installing. Some people have Windows and Linux dual booted, some just use single OS's with removable hard drive kits, still others install many operating systems. This guide will focus on a Windows/Linux Dual boot configuration. If you are just doing one or the other you can refer to the charts at the end of the guide to help you determine what you need to do after reading this guide.

Hard drives work by spinning a disk and moving several arms across the surface to read and write from the surface of the disk. When your computer is off the arms are stowed away off of the surface of the disk. When it boots up the arms move to the edge of the disk and begin reading the first track at the edge... this track 0 and is also known as the MBR. Each track is divided into sectors and again into blocks. The important thing to remember is that like a record player the arm reads data from the outside in. the majority of the time a hard drive spends looking for data is in the process of moving the arm to the appropriate track. If you want to increase system performance you need to do whatever you can to limit the amount of real estate that arm needs to cover to get to any given information.... virtual memory and Linux swap spaces included. The system hits these constantly and as such you can find the arm constantly swinging back and forth across the disk surface... causing massive time loss in the long run. The solution is to place these areas of the hard drive as close to the core operating system as possible. In the old days space was limited so this was never a problem. Even today if you have a drive of less than 20 gigs you don't need to worry about it as you don't have the real estate to do anything about it. Now with hard drives fast approaching a half a terabyte... you have the room to tweak this often forgotten aspect.

Now we'll say for the sample of this guide you have a 100 gigabyte drive. The first thing you need to do is take an inventory of all of the software you plan to install. All of your games, all of your applications... for me that's less than 30 gigabytes. This will be your windows partition. Don;t figure in your music or photo collections or any other personal data... we'll get to that later. Just the amount of data space you need for all of your applications. IF you got the number add 10% to whatever it is and round it up to the nearest increment of 5. In my case I figure I needed 30 gigabytes... add the 10% to make it 33 gigs and then rounded up to a nice even 35 gigabytes. Go ahead and draw a line at about that point on your bar. Write in Windows and 35gb in the box (leave some room for additional info as we get to it)

Now we need to separate the windows virtual memory system from the system partition. If you have the luxury of a second hard drive you can put it on there but for now we'll assume you don't. This partition only needs to be a maximum of 2 gigabytes... draw a sliver in the space next to the first box and label it as the windows VM 2gb. You have already started to amplify the speed of your hard drive by more than 50% by cutting out half of the drive you need to search to find anything. That covers windows with 2 partitions, but what about Linux?

For Linux we need to set up many partitions.. most will be small and will b e located within an extended partition. Windows has to be in a primary partition and so does Linux's /boot file system. This isn't a problem as we have one primary left to work with. out of the 100 gigabytes we have about 63 left to play with. Linux in total will need no more than 5 gigabytes, 10 if you plan to go wild with many applications. It's no where's near the "bloat ware" that windows applications are. The first partition you will need to plan for is the core of the Linux OS... the Root. All things come form root and everything in Linux.. even hardware... is a file inside of root.  You will need about 4 gigabytes for the root file system... more if you really plan to do some heavy work. I use 10gb to be on the safe side. Add in this space to your bar and label it Linux root 10gb. Now we only have one more partition left we can actually make as a primary, but several left to make. The rest of the drive will be an extended partition. Write that in and draw a new bar to represent that space. In this example I have 53 gigabytes left of real estate in the extended partition. For logical dives we will need a swap drive, a temp drive a variable drive, a home drive, and a place to save files from both windows and Linux. As with windows you will only ever need 2 gigs of swap space so draw that sliver in first. Label it accordingly as a Linux Swap 2gb. The Linux swap is similar to the windows Virtual memory page file in that it's a place for the system to store data that is in the middle of being processed but cannot fit into main memory. Unlike Windows however Linux MUST have a swap space. It is a requirement for the system to even operate, even if you have enough memory for the system to never use it. Now that we have the root and swap planned out let's begin with the rest.

The temporary and Variable /tmp and /var paths in Linux respectively are separate for security reasons. These locations are publicly writable and having them in with the rest of the operating system can cause a denial of service attack. Additionally any user can write to their home directory so you also want that separate from the rest of the root file system as possible. If the root file system's partition should ever become completely full the system will crash and most likely be lost. Keeping these areas separate will save you a lot of headache in the long run and is much safer than simply setting software disk quotas. Temp can be as small as as 500 megabytes but I like to give some breathing room for large applications to write to so I use 5 gigabytes for both of the /tmp and /var file systems. This will only bring our total remaining to 41 so it's not a big hit at all. If you plan on running a web server or FTP server the files will be stored in /var... along with system logs and such. If you plan on accessing and using these features then give it some more room as you see fit. draw and label those partitions in accordingly. when you are done you only have the /home area and the shared areas left. if you plan on transferring a lot of files between the two systems then make the shared area larger. If you plan to do most of your work in Linux and don't need a large area... make the home area bigger. I tend to allow 10 gigs for home and the rest to shared. this leaves us with a 31 gigabyte partition to make into a shared space. For the sake of simplicity I make the home a little bigger to bring the shared space under the 30 gigabyte FAT32 limit. Linux has a history of disliking NTFS so it should be avoided whenever possible.

Step 3: Partition Away

Now that the plan is settled go ahead and create your first two partitions using The windows setup and get that OS installed. Once the system is installed you can refer to my guide on windows virtual memory to move it to the second partition. For simplicity you may wish to hide this partition in windows by using the drive manager to assign no drive letter or path to it. This will effectively remove it from 2000/2003/XP's my computer and prevent you from accidentally writing to it. Once that's done it's on to Linux.

Once you start up the Linux installer you will be bombarded with a bunch of stuff that is difficult to understand at first. There are plenty of how-to's on the net on using the Linux FDisk program or the partition manager that comes in such distributions as red hat or whatnot. Just avoid changing the first two partitions and go through creating your other partitions. Most Linux installers will give you the option of installing certain file systems to certain partitions. Go ahead and do that when you are prompted. If no option is given then you may have to do it manually, which is beyond the scope of this guide. Finish the Linux install, and set up windows in the Linux Boot manager.(usually Grub or Lilo) There are also how-to's on setting this up available in almost every Linux distro's help files. When you get back into windows start up the drive manager and add in the shared partition into the remaining unallocated space at the end of the extended partition. If it shows the whole thing as unallocated you will have to exit there and do it from the Linux FDisk. Either way make this partition Fat 32 and add it to the Linux FSTAB file (once again there are how-to's on this on the net)

That's it. Below I will detail showing some different setups for different situations that work for me. If the system is a solo Linux system it will also include a /boot to keep the boot files separate. I'll use percentages of total disk space to denote the sizes of the partitions. Note that there are minimums for each area of Linux and you may have to adjust your partition sizes accordingly. It's not an exact science so feel free to experiment.

Format:
Partition Type - Usage - File system - Approx. Size

Windows / Linux dual boot
-------------------------

PRIMARY - Windows - NTFS - 30%
PRIMARY - Windows Paging - NTFS - 2%
PRIMARY - Linux / - EXT3 - 10%
EXTENDED
LOGICAL - Linux Swap - Linux SWAP - 2%
LOGICAL - Linux /TMP - EXT3 - 5%
LOGICAL - Linux /VAR - EXT3 - 5%
LOGICAL - Linux /HOME - EXT3 - 26%
LOGICAL - WIN/LIN Shared - FAT32 - 30%

Linux Solo System
-----------------

PRIMARY - Linux /Boot - EXT3 - 2% (200mb is fine)
PRIMARY - Linux / - EXT3 - 10% (3gb minimum in most cases)
PRIMARY - Linux SWAP - Linux SWAP - 2%
EXTENDED
LOGICAL - Linux /TMP - EXT3 - 5%
LOGICAL - Linux /VAR - EXT3 - 10%
LOGICAL - Linux /HOME - EXT3 - 71%

Windows / Linux Dual boot.. Multiple Hard Drives
----------------------------------------------

Hard Drive 1 (/dev/hda for Linux IDE drives)

PRIMARY - Windows - NTFS - 50%
PRIMARY - Linux / - EXT3 - 48%
PRIMARY - Linux SWAP - Linux SWAP - 2%

Hard Drive 2 (/dev/hdb for Linux IDE drives)

PRIMARY - Windows Paging - NTFS 2%
PRIMARY - Linux SWAP - Linux SWAP - 2%
PRIMARY - WIN/LIN Shared - FAT32 - 30%
EXTENDED
LOGICAL - Linux /TMP - 5%
LOGICAL - Linux /VAR - 10%
LOGICAL - Linux /HOME - 51%

(note: While more than one space for virtual memory can improve windows performance it isn't usually worth it. On the other hand having 2 Linux swap spaces on separate drives will greatly enhance the efficiency of the system.)

Once again these are general IDEAS and you can customize these to suit whatever needs you have. There is no magical scheme that will work for everyone... this is only a guide to get you going on discovering what works for you.

I hope this guide helps you plan your system and helps you understand that software planning is just as important as hardware planning.
__________________

Thanks to "Kittani" on Overclockers.net for this well thought out resource

---

### Post by PoopyTheJ on 2008-07-02
I had to do a user manual for something for class and I chose to do one on Ubuntu, in specific installing Ubuntu. This manual was written for the absolute Ubuntu newb to make it as easy as possible to switch to or install Ubuntu in a dual boot configuration. It is written for the windows audience just finding out about Ubuntu and no extreme technical knowledge is required, in fact it's probably best if it's used for those with limited technical knowledge as it's written to be as basic and simple as possible. I'm posting it here in the hopes that someone will find it useful and will take all suggestions for improvements and revisions and keep it as up to date as possible. I'll take full responsibility for updating this post in particular though if anyone wants to use it in any way they are completely free to do so. I'm not claiming any sort of ownership or anything so feel free to download, link to distribute or modify to your hearts content, I'd like some credit for the original work, but I won;t cry if it's not given ;)

Manual follows...
...
...
...

A. Introduction

	This manual is designed to enable you to install the Ubuntu Linux Distribution at your home desktop computer. This manual will cover obtaining and/or creating your Ubuntu installation CD-ROM and the subsequent steps necessary to install it on your personal computer. Ubuntu Linux is a Linux operating system designed for ease of use and with the object of enabling computer users to switch to it from another operating system easily. Ubuntu Linux is software released under the GNU/GPL meaning it is free from copyright restrictions on reproduction, distribution and modification. Ubuntu comes in a number of different variations from Ubuntu, Kubuntu and Xubuntu as well as smaller spin-off distributions. Each has it's strengths and weaknesses and will appeal to different audiences. Ubuntu is the standard version of Ubuntu offering good graphics quality and ease of use. Kubuntu uses the KDE user interface and tends to be a bit heavier on system resources, meaning it is important to have a more powerful system to run it as effectively as a distribution lighter on graphics flair. Xubuntu uses the xfce interface and tends to be the lightest on system resources and is a very good option for older machines or machines without a decent video card.  Ubuntu, Kubuntu and Xubuntu are trademarks of Canonical Ltd. 




B. What You Will Need
An Internet connection (preferably broadband) for downloading the Ubuntu ISO Images
CD Writer
Blank CD-ROM
Working Computer

1. Pre-Installation Steps
The first step in installing Ubuntu is to download or acquire an Ubuntu installation CD. The Installation Cd's come in a couple of options for users of Ubuntu. Some users will be using Ubuntu as a Server, for serving up web pages, email, databases or files. Ubuntu has a server edition or a desktop edition available for users. Also each Ubuntu edition comes in a Live CD or a text based installer. The Live CD will run a copy of the Operating system from your CD-ROM without making any changes to your system. This allows a user to try-out Ubuntu without risk of overwriting or otherwise damaging their system. The text based installer is generally used for people who have difficulty installing from the Live CD due to graphic driver issues. If you have a broadband internet connection you can download an ISO image of the Ubuntu installation media. An ISO file is an image file which is used to burn, or write the information to CD.
You can download the ISO image file from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). The current version of Ubuntu is Version 8.04 &#8220;Hardy Heron&#8221;. For this installation manual we will be covering installation of the Desktop Edition of the operating system. If you do not have a broadband connection you can still get an Ubuntu installation CD for free. Simply request the installation CD at [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/), you will be shipped a CD to be used for installation for free. The CD may take up to ten weeks to arrive though so if you have a broadband connection it's usually better, and faster to simply download and burn an ISO file.

1a. Burning an ISO File
If you are using a Windows based operating system currently you will need to have a CD burning program like Nero or Roxio installed to burn an ISO file. A great open source and free alternative to the proprietary CD writing applications mentioned above is InfraRecorder available from [http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/). Microsoft Windows does not by default include support for burning ISO files. Refer to the instructions provided by the software manufacturer for instructions on burning an ISO image file to CD-ROM.

Installation
	Now that you have a CD-Rom with your operating system burned and ready we can begin installation of the operating system. Depending on your system and hardware components you may have the most luck in installation with the text based installer, though for most the Live CD will work just fine. For now we will assume that you are using the Live CD for installation, please see Appendix A for installation instructions using the text based installer. 
	Insert the CD-ROM with Ubuntu into the CD-ROM drive of your computer and reboot the machine. Many machines are set to search out the CD-ROM drive first when booting to look for boot media. However if you have changed the system BIOS or your BIOS is not set to default to CD-ROM as first boot device you will need to change this. Most motherboard and BIOS manufacturers default to the &#8220;Del&#8221; key at boot to enter the system BIOS. If your computer is manufactured by a major manufacturer like Dell, HP or Compaq though the options for entering the BIOS will be different. Please refer to your motherboard manual or computer manual for instructions on changing the boot settings for your computer. 
Once you have setup your PC to boot from CD and started the computer your Ubuntu CD should boot up to a screen with a number of different choices available.  The first choice is &#8220;Try Ubuntu without changes to your computer&#8221;, this option should be used for those who are comfortable with a GUI screen for trying out Ubuntu directly from the CD. In this way a user can become comfortable with the Ubuntu layout and look. However for our purposes we will want to &#8220;Install Ubuntu&#8221; which is the second choice in the list. The rest of the options are for troubleshooting or simply bypassing the installation media altogether. If you have errors while attempting to install Ubuntu the third and fourth options enable you to &#8220;Check CD for errors&#8221; or &#8220;Test Memory&#8221;, both of these are the most common cause of errors in installation. If you run into errors during installation it is usually a good idea to run these tests first before any other troubleshooting steps.
Once we have chosen the &#8220;Install Ubuntu&#8221; option we will be given a pop-up windows stating &#8220;Starting Linux Kernel&#8221; allow this to load and move on to the next screen which will show you a loading bar underneath the Ubuntu logo, depending on the speed of your machine this can take a few minutes to proceed to the next step. The next three screens you see will enable you to pick language, location and then keyboard layout. Unless you have a very unique keyboard layout or are outside the US and using a different language than English simply choose the default settings for keyboard. After this you will have the option on how to partition your hard drive. For those seeking to dual-boot with a Microsoft Windows operating system please see the section titled &#8220;Keeping Windows&#8221; for instructions. If you wish to replace your current operating system completely with Ubuntu you can choose the Guided installation option and simply choose use entire disk. This will format your hard drive with a main Linux partition with all files and a small, usually under 2 Gigabyte, swap partition. The swap partition acts like windows virtual memory, keeping temporary files on the swap drive when not being stored in RAM. 
	After you have chosen how to partition your drive you will be given the option to setup a user account to log-on to your Ubuntu installation after installing. You should choose a username you want to use and then a password which is easily remembered. In order to choose a secure password the password should not be a word which can be found in a dictionary and should contain numbers or special symbols. These types of passwords are almost impossible to guess for an unauthorized user and provide very good protection against password cracking software. After you have chosen a username and password click next and you will be offered a summary of your installation choices, if anything appears incorrect simply click back and return to the section required to fix the error otherwise, click next and Ubuntu will begin installing. While Ubuntu is installing you will see a progress bar moving across the screen, after the installation has completed you will be offered with a screen showing &#8220;Installation Complete&#8221;, simply click the restart now, remove the installation media when instructed and your new Ubuntu installation will boot to the login screen. Enter the username at the prompt, then hit enter, this will change the prompt so you can enter your password, do so and hit enter again and Ubuntu will load your desktop. Congratulations on your Ubuntu install, enjoy!




Installation &#8211; Keeping Windows

	Installing Ubuntu with a Windows installation can lead to data loss! 	Always backup important data before attempting to install Ubuntu with 	Windows!

There are two options for keeping your windows installation, if you have one hard drive and windows takes up the entire hard drive then you should choose the Guided &#8211; Resize Partition option to install Ubuntu. This is not without some risk and you should back-up all important files before proceeding. Also of importance when resizing a partition it's usually a good idea to defragment the drive as thoroughly as possible first, this will limit the chances of data loss due to the resizing.  Ubuntu has the ability to attempt to resize an existing partition, this should not be attempted prior to backing-up all files! If your windows installation does not take up the entire hard drive then you can choose the Guided-Use Free Space option, or the manual option. If you choose the Guided-Use Free Space option Ubuntu will install to the first available free space on the drive, overwriting the windows boot-loader with grub, a text based boot loader which will load before any Os when you boot the computer and you'll be able to choose the OS you wish to boot into. If you choose the Manual installation option you will need to manually choose a free partition or drive to install Ubuntu, in this case Ubuntu will also overwrite the existing Windows boot-loader and replace it with Grub.

One further option for installing Ubuntu while keeping Windows is using Wubi to install Ubuntu. Wubi will install Ubuntu within Windows as a single folder, similiar to installing a windows application. This is a simple and easy way to get a full featured Ubuntu installation without having to change any windows items. To install using Wubi simply insert the Ubuntu CD into your CD drive while in windows. The Pop-up sceen will offer three options, 
Demo and full install,
Install inside Windows
Learn More
To install using Wubi simply click the Install inside windows option and a simple screen will pop-up asking where you want to install Ubuntu, be sure to choose a large enough partition, how much space to use, what language to use, a user name and password. After that click install and wubi will install Ubuntu. When you reboot the Windows boot loader will now offer you the choice to boot into windows or Ubuntu. Simply choose Ubuntu and enjoy! 



FAQ
Why Linux?
	Linux is a free and Open-Source operating system distributed under the GPLv3 license. What this means is that you are free to use, copy, distribute, and modify the operating system in any way you wish so long as any derivative works are also released under the GPLv3. Linux is a powerful and customizable OS, with all of the functionality of Microsoft Windows and none of the cost, Most Linux distributions come with many additional software components already installed. Ubuntu comes with Mozilla Firefox, an open source browser, OpenOffice and open source Office suite, Gimp an open source image editing program and many other programs as well. Compare this to Windows and you'll see a benefit right away!
Can I use my Windows programs with Linux?
	The short answer is no, probably. However there is an application called Wine which enables many windows programs to run with Ubuntu. Wine is technically not an emulator, but will install a "fake" windows installation which can be used to install windows applications. The only way to know for sure if your program will work with Wine is to try it. Otherwise there are so many open source programs available for so many different needs your sure to find one that can replace the proprietary software you were previously accustomed to with windows.

Definitions
Hard Drive &#8211; The Hard Drive is the memory of your computer, storing programs and data for long term storage, your operating system and programs are stored on this media.
Ubuntu &#8211; Linux distribution using the gnome user interface and offering an alternative to closed source operating systems.
Kubuntu &#8211; Same as Ubuntu except uses KDE as the GUI
Xubuntu &#8211; Same as Ubuntu except uses the xfce GUI
GUI &#8211; Graphical User Interface, what you see and interact with on the computer screen
Partition &#8211; Section of a hard drive set aside for a certain use, there are many different partition types, from NTFS, to FAT 16, FAT32, ext3, ext2, etc.

---

### Post by AmbiguousOutlier on 2008-11-07
Hello, I'm a newbie and now I've been using Ubuntu for about 6 weeks, I've finally got it to the point where I'm happy with it. However I could have got there a lot quicker if I didn't have to use google and these forums so much. So I thought I'd create a “Newbies guide for Newbies”. Basically what I have learnt so far explained in newbie words. Intended for those who've only installed Ubuntu 10 minutes ago and still using Windows to get on the net or those who haven't even got that far.

I thought I'd begin with a bit of background, what I learnt before I installed Linux to decide whether it was right for me. First off Linux is based around a philosophy of sharing knowledge and this is the way the world of computing worked pre 1980's, before the corporate world we know today started to take form. Ubuntu is a project that aims to promote and continue this philosophy for many years to come. Although we may think of Linux as being a free operating system because people in the own time help in making software and putting these distributions together, which largely is the case. In actual fact this guy Mark Shuttleworth who is the man behind Ubuntu has actually invested $10 million dollars and has a team of fully paid developers to ensure the project continues. 

Ubuntu is based upon a Linux distro called Debian which came about 1993, The leading developers behind these distros as such have similar goals and therefore when you reading pages about Ubuntu you may frequently see references to Debian. Ubuntu though tries to bring Linux to the masses, and aims to overcome to misconceptions that Linux is for geeks and developers. In my own opinion there is a learning curve but once you've been playing with it for a few days you will feel perfectly at home. 

What actually is Linux? Well in the mid 70's a Finnish man named Linus Torvalds whilst at university in Helsinki wanted to access the universities powerful (at the time) Unix servers, from home during the cold winter months. He decided upon Minix over DOS as this was based on Unix and would run on his home computer. Anyway Linus eventually developed Linux from Minix, which is merely some programs that allows your computers hardware to communicate with each other, so Linux is actually the kernel program, which on it's own would allow your PC to boot up and provide a blank screen. Software is then run on top of this, this software originally comes from the GNU organisation. So many people refer to what is commonly known as Linux as GNU/Linux. 

Richard Stallman who studied in at MIT in during the 70's at the very popular Artificial Intelligence Lab. When ideas and programs were shared freely however this changed in the 80's where people decided software should be proprietary (Microsoft was at the forefront of this movement), where code wasn't shared and secrets and contracts were created. Stallman left MIT and started the GNU project in 1984. 

With the history lesson over, I guess it's time to install Ubuntu. I'm assuming that as you're interested in GNU/Linux then you've probably already typed “Download Ubuntu” into google, then downloaded the relevant version (64 for AMD or i386 or Intel) burnt two copies to disk given one to a mate and put the other in your CD drive. Then rebooted your computer and followed the very simple on screen instructions. Just in case you haven't I'd recommend you keep your installation of Windows and create a second partition, Ubuntu should only take as much space as it needs. And follows the default installation steps. 

Please keep in mind I am a newbie and although I have installed Ubuntu five times and Kubuntu once they all worked seamlessly and a lot quicker then Vista did. So if you do have any initial installation issues I probably wont be able to answer them.

Once logged into Ubuntu for the first time I'd suggest you have a look around, you wont be able to break anything as you will be required to enter a password before you can make any fundamental changes to the system. Things will be very different to Windows users, almost upside down. To users with experience on a Mac then you should see some similarities after all both OS X and Ubuntu and developed from Unix. 

First things first I had issues with my Wireless networking and also my graphics card. So I suggest you install this application as your first task. We'll take the long way round to begin with. You can use the Terminal window, which is located in the Applications Menu then the Accessories submenu. More on this later, as I got very lost to begin with even though I thought I was quite good in dos.

Click System > Adminstration > Synaptic Package Manager. 

Most apps within the Admin submenu of the System menu will require you to input your password as these programs will make changes to the system, which potentially could damage your computer. Within the Synaptic Package Manager click the search button and type

```

gnome-device-manager

```

Click the first entry and select “Mark for installation” Occasionally when installing apps this way you'll be asked to accept that this app requires other apps to be installed. Then click “Apply” on the toolbar. If you're not online with your wifi then Ubuntu will work out of the box with the wired LAN connection.

After installation Device Manager can now be found within the Applications menu and System Tools submenu. This device manager is different from that what you'd be used to in Windows and provides not as much information but on a lot more components of you machine. Also unlike Windows will list hardware even if it is not yet configured to work. 

Out of the box Ubuntu did not get online wirelessly for bothof my laptops, it may have done for you, if so ignore the next bit. Ndiswrapper is an application you can install which uses your windows drivers. However I attempted this once and it didn't work, although if I had of persisted I'm sure I would have succeeded. I used madwifi which worked almost immediately, the guide I followed was;

```

http://ubuntuforums.org/showthread.php?t=816780&highlight=madwifi

```

In the terminal I did need to run before I followed the thread above;

```

sudo aptitude update

sudo aptitude install

```

You probably wont, but just in case. (And I'm still not sure exactly what they do, don't worry they wont hurt your computer). If your wifi still does not work then use the device manager you installed earlier to find the make and type of the card you have type this into Google with Ubuntu at the end. 

Next thing I did was some power saving configuration, essential in the green world we live in. Different computers have different power saving capabilities, whatever yours are they will be located in the System menu then the Preferences submenu. Select an app called power management. Change these settings to suit your own needs.

Next if I'm not using my hard disk then I like it spin down this saves on power consumption considerably over time, especially as a lot of my computer use is for internet and email. Which doesn't really require the hard drives to be available. If you want to do the same open up the terminal window and type (by the way you can just highlight and middle mouse click (the scroll wheel) or click the left and right mouse buttons simultaneously with focus on the Terminal window);

```

gksu gedit /etc/hdparm.conf

```

This will open up a file in gedit (Ubuntu's advanced text editor) click find on the toolbar and search for “spindown_time”. I have mine set to;

```

spindown_time = 24

```

Which is two minutes, for each 1 is equal to 5 seconds. Although above 240 it starts incrementing in 30 minutes, however don't worry about that. Just set it to 24. In the long run you'll save energy and your hard disk wont get as hot especially useful on a laptop. Save the file, then a reboot will be necessary.

The next important thing is graphics, my integrated Intel graphics card worked no problem out of the box however my Radeon ATI card did not. To get this working I selected Hardware Drivers from the System Menu and the Administration submenu. Remember Admin stuff requires a password. When you click the enable box next to your graphics card, then another box pops up asking you to install new software. Click apply. 

Close out of all of these boxes and then restart your computer. If this produces anything unexpected then you can disable via the same method and use Device Manager again to find the type of Graphics card you have and again Google using Ubuntu at the end of the search string. 

Although Ubuntu is secure. I am paranoid. So I installed a firewall, Firestarter is the one I chose. In the Synaptic Package Manager in the Administration menu, search for firestarter and Install. Once completed go back into the System menu and Administration submenu then Firestarter. You'll be provided with a Wizard where most of the default settings will be sufficient for the average user. 

On the first screen detected devices, eth0 refers to your LAN connection and wlan0 refers to your wifi connection choose whichever is appropriate. Assuming you have broadband put a check in the “IP address is  assigned via DHCP”. Then click forward a couple of times and Save.

Like any other firewalls you can set specific rules for inbound connections like Azureus or any other Bit torrent client for example.

If you've installed firestarter then you are probably as paranoid as me and will want an anti virus program. These are useful, as many Linux users still want to transfer files between Windows computers and it is prudent to check for Windows viruses. Now because Linux does not have security holes that are currently been exploited by any viruses, where as I believe a couple thousand are found every week on Windows. We'll be installing CalmAV which only detects and does not disinfect viruses. But at least you'll know not to transfer that file to a Windows machine. Please keep in mind although 90% of the world use windows, if Ubuntu grows in popularity (which is the goals of Ubuntu) virus programmers will soon turn there attention to Linux. (More people switch to Linux and OS X then switching to Windows).

Open up the Synaptic Package Manager, and search for calmtk (this is gui for CalmAV). Mark it for installation, in the same as we've done before and install. You'll need to be open to calmtk and update the database. To do this open up the Terminal and copy the following;

```

gsku calmtk

```

You'll need to enter your password as your running with Administration rights. Click help and Update signatures. It may be reported as already up to date on first use as during the installation it will automatically update the database. However it is advisable to update before each manual scan. You can also update the database by purely entering;

```

sudo freshcalm

```

Click Applications > System Tools > Virus Scanner to start CalmAV. For the first time select Options then Scan hidden files. Then Click File > Recursive Scan, navigate to your /home directory. CalmAV is not designed to scan your entire disk but more so for documents and files. Quarantine any files that show up as a virus in the programs window. Then Google the name of the virus and decide what to do from there.

Now we have the system working and fully protected, we want to start having a bit of fun. Click System > Preferences > Appearance, Choose a theme and customise to your hearts content. For the background, I found that typing your resolution into Google Images provides a good selection of backgrounds for instance; “1440x900”. You can also change system fonts here. On the Visual Effects tab select the Extra radio button. Hopefully if you've installed you graphics card correctly and it's powerful enough, then you be able to select this option, you'll have some cool effects as a result, the popular one being wobbly windows.

[http://www.saunalahti.fi/frog1/wavs/systemsounds.htm](http://www.saunalahti.fi/frog1/wavs/systemsounds.htm)

The above website provides a good selection of system sounds that can be downloaded to your /home directory and changed in System > Preferences > Sound.

Now back to visual effects, I just wanted to get sounds out of the way as the next step will occupy you for the next couple of hours.

Open up the Synaptic Package Manager, and search for copizconfig-settings-manager. Mark and install. Now go to System > Preferences > Advanced Desktop Effects. Alternatively Start up the Terminal and type;

```

ccsm

```

There is an amazing number of effects that can altered, some of which you may have seen on youtube and even lured you into the world of Linux. The ones I like are;

Enhanced Zoom Desktop – As the name suggests enables you to zoom into your desktop
Desktop Cube / Rotate Cube – The very popular cube that spins round and round (Please ensure within the General Options at the very top, Horizontal Virtual Size set to 4 on the Desktop Size tab) Lots and lots of settings with these so spend an hour playing around until you get it just right.
3D Windows – Very cool but sadly my graphics cards just aren't good enough. Produces a very small amount of lag, enough to be an annoyance.
Animations – These are also very good, controls how you windows look when opening and closing. I like the beam up and fire ones.

If you liked your widgets on Vista then you may be interested in the screenlets, I personnally found them as boring as they were on Vista. Go back to the Synaptic Package Manager and search for screenlets. Once installed you can find them under the preferences menu. Play with them if you wish. 

If you not happy with how your mouse and keyboard are operating then you can change these settings in the preferences menu. Just so you know a wireless Logitech mouse and keyboard connected straight away even though the box didn't mention it's compatibility with Linux. 

If you've used OS X and you like the dock at the bottom then you may want to install AWN Avant Window Manager. Within Synaptic Package Manager search for Awn-manager-Trunk. Once installed goto System > Preferences > Awn Manager, In the general options tab ensure “Automatically start AWN on login” check box is enabled. Then Change whichever preferences you like. Once setup you can drag and drop icons from any of the menus onto the dock. These will be placed in the launcher option, where you can also customise the dock. If you can't see the dock then type into the terminal;

```

awn
[/awn]

This was a bit fiddlerly to get working exactly how I wanted it but persistence pays off. Now you probably still have the “taskbar” at the bottom of the screen, I've already removed mine and can't figure out how to get it back but I'm sure I simply right clicked and removed. But a word of warning it may take a little Googling if you want to get it back. 

Hopefully by now you'll have ubuntu working and looking the way you want it. There are some additional features out of the box that may be of interest to you. Openoffice.org is pre installed and is almost identical to Windows Office. However Base which is MS Access equivalent is not installed by default. You also have image editors simailar to Adobe Photoshop called gimp although having not used used photoshop I can not tell you how good it is. Virtually any program you have on Windows can be found in a similar form for Ubuntu. Just type what you're after into Google with Ubuntu after it. We do have an email tool with a fairly decent calendar called Evolution. Now I did try and get my hotmail account to work with evolution but I just couldn't do it. You may have better luck with this;

http://ubuntuforums.org/showthread.php?t=200408&highlight=hotmail+evolution

I ended up setting up a gmail account using this guide;

http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/

And also my google calendar synced quite easily. To do this goto your Google Calendar settings and copy the “ical” option from the www onwards.

Then goto evolution and select Calendar button from the bottom left, File > New > Calendar, change type to “on the web”. In the URL box past the address from google settings after the webcal://. Type  in your username without the @gmail.com / @googlemail.com.

I have a Wii and although this is pointless you can set it up in half an hour with no additional expenditure providing you have a Wii. It is cool to show to your friends.

http://ubuntuforums.org/showthread.php?t=836231&highlight=wiimote

One of the biggest learning curves I experienced with Ubuntu is the file structure. With Linux we no longer have letters for drives. Everything in Linux effectively is treated like a file and will appear within the the Filesystem, when ever a piece of hardware is attached, a web cam, usb drive then a file will be created. Go to Places > Computer. Then click on the Filesystem icon. This will show you all the files and directories on your system. You wont be able to edit most of this data as you will need administrative permissions called root or super user in Linux. Anything you save or download will more then likely be save in your /home directory. Also of interest is your /media directory which contains any external hard drives or CD/DVD drives attached your computer. 

You may have also noticed I'm using forward slash rather then back slash as Windows does. Linux is also case sensitive so when creating a file you can have files with exactly the same name but differing capitals ie File or FILE or file keep this in mind if transferring files to and from Windows.   Windows will invariable break if you try and copy files of the same name. You can also use special characters like \:*”<>?| in your Linux file names which will not work in Windows. Another cool thing you can do is right click a file, select properties then on the Emblems tab you can add icons to each of your files to display easy to see prompts on the type of files you have.

Lastly I'd like to share what I have learnt about the Terminal Window. Like DOS the BASH Shell is Linux version but so much more powerful. Pretty much anything you do in a GUI can be done in BASH. Ubuntu's shell is based on the Unix Bourne shell, BASH means Bourne Again SHell. The Shell is very useful as we can make certain operations with one line of code rather then a whole string a mouse clicks and keyboard inputs. For instance every app we've installed so far can be installed using just a couple lines of Shell commands, which are all largely generic. 

If there is a command you're not sure of then you can use the --help command after the initial command;

[code]
ifconfig --help

```

If you are proficient in DOS then you can create aliases for instance in DOS to copy a file you would use the command COPY in shell you use cp. 

```

alias copy='cp'

```

You can change this if you wish but it probably isn't a good idea. As you should try and learn BASH. This will provide you with a list of commands and their DOS equivalent.

[http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html)

Previously we have used the sudo and gksu commands. As standard we do not have root permissions, so to enable us to run a program with root powers we need to use one of the above commands. Sudo is used most of the time, gksu is used for GUI apps, like opening the Anti Virus GUI or a file in gedit.

I think that's enough for now, I may do follow up guide in another 6 weeks of using Linux. I hope this has been useful to at least one person. And I hope I haven't got anything wrong, please let me know if I have.

Thanks for reading.
Rhys.

---

### Post by catcharavind2003 on 2008-12-07
Ubuntu has become the most popular Linux distribution for new Linux users. It's easy to install, easy to use, and usually "just works." But moving to a different operating system can be confusing, no matter how well-designed it is. Here's a list of tips that might save you some time while you're getting used to Ubuntu. 
1. Getting multimedia to work 

The default Ubuntu install contains free software only, which means that it doesn't support some popular multimedia formats straight out of the box. This is inconvenient, but the Ubuntu folks have good reasons for not shipping with support for MP3, DVDs, and so forth -- including that software could cause them some legal headaches, or incur some serious fees.

Fortunately, as a user, you don't need to worry about fees (though some of the packages may not be legal due to patent restrictions or restrictions on circumventing copy protection, depending on where you live). The Ubuntu wiki has a page on restricted formats that explains how to get the packages you need. However, if you run Ubuntu on AMD64 or PowerPC hardware, you'll still be out in the cold for some of the packages, since some multimedia formats depend on proprietary software that's not available for those hardware platforms.

2. Changing the defaults 

Ubuntu comes with a number of defaults that may or may not be to your liking. For example, the default editor is set to Nano, which isn't optimal if you're used to Vim.

The easy way to change this is to use the update-alternatives program, which maintains the symbolic links under /etc/alternatives that determine the default programs for FTP, system editor, rsh, Telnet, window manager, and so forth. Look under the /etc/alternatives directory to see what programs are managed.

To change the default editor, run sudo update-alternatives --config editor. You'll see a dialog like this:


There are 3 alternatives which provide `editor'.

  Selection    Alternative
  -----------------------------------------------
        1        /usr/bin/vim
	2        /bin/ed
  *+    3        /bin/nano

Press enter to keep the default[*], or type selection number:

Just type 1 to switch to Vim. Note that on my system, I don't have Emacs or many other editors installed; if I did, the utility would offer the other editors as choices.

3. How to install packages 

Most of the application software you'll want to add to your system will be available through the Ubuntu repositories using Synaptic, Adept, or another package management tool. What if you want to install something like Opera that is available as a package for Ubuntu, but isn't in the repositories?

In that case, download the application's Debian package (.deb) and right-click on the file. At the top of the context menu, you should see an option to open the package with the GDebi package installer. GDebi will provide a description of the package, what files are included, and other details about the package. The package installer also has a Install Package button; just click that and it will install the package. Note that the package installer also checks to verify whether it can install the package -- if it has dependencies that can't be satisfied, GDebi will give an error and refuse to install it.

If you prefer to install packages at the command line, just use sudo dpkg -i packagename.deb.

4. Sudo and gksudo 

If you've used Linux for any amount of time, you might be used to running programs as root directly whenever you need to install packages, modify your system's configuration, and so on. Ubuntu employs a different model, however. The Ubuntu installer doesn't set up a root user -- a root account still exists, but it's set with a random password. Users are meant to do administration tasks using sudo and gksudo.

You probably already know how to use sudo -- just run sudo commandname . But what about running GUI apps that you want to run as root (or another user)? Simple -- use gksudo instead of sudo. For instance, if you'd like to run Ethereal as root, just pop open a run dialog box (Alt-F2) and use gksudo ethereal.

By the way, if you really must do work as root, you can use sudo su -, which will log you in as root. If you really, really want to have a root password that you know, so that you can log in as root directly (i.e., without using sudo), then run passwd when logged in as root, and set the password to whatever you want. I'd recommend using the pwgen package to create a secure password not only for root but for all your user accounts.

5. Add users to sudo 

When you set up Ubuntu, it automatically adds the first user to the sudo group, allowing that user to make changes as the super user (root) by typing in their password. However, it doesn't automatically add additional users to the sudo group. If you want to give someone else superuser privileges on your shared system, you'll have to give them sudo access.

To add new users to sudo, the easiest way is to use the usermod command. Run sudo usermod -G admin username . That's all there is to it. However, if the user is already a member of other groups, you'll want to add the -a option, like so: sudo usermod -a -G admin username .

If you prefer the GUI way of doing things, go to System -> Administration -> Users and Groups. Select the user you want to add to sudo, and click Properties. Under the User privileges tab, check the box that says "Executing system administration tasks" and you'll be all set.

6. Adding a new desktop 

Many users aren't sure what packages to add in order to run KDE or Xfce window managers on a stock Ubuntu system -- or what packages to add to run GNOME on Kubuntu or Xubuntu. You could add all of the necessary packages one at a time, but there's a much easier way to go about it.

To install all of the packages that come with one of the flavors of Ubuntu, such as Kubuntu, run apt-get install kubuntu-desktop (or edubuntu-desktop, xubuntu-desktop, or xubuntu-desktop).

If the GUI is more your style, the *desktop packages can be installed using Adept, Synaptic, or another package manager.

7. How to reconfigure X.org 

Most of the time, X.org -- that's the software that drives your video card and provides the foundation for the GUI, whether you're running GNOME, KDE, Xfce, or another window manager -- "just works" when you install Ubuntu. In fact, I'd wager that most Ubuntu users never even have to think about their video settings.

But, sometimes you need to reconfigure X.org because Ubuntu hasn't detected your video card and monitor properly, or maybe you've just purchased a shiny new video card and need to get it working with Ubuntu. Whatever the reason, it's good to know how to reconfigure X without having to edit your /etc/X11/xorg.conf by hand.

To run through the configuration, use dpkg-reconfigure xserver-xorg at the console or in a terminal window. Then you'll have a chance to specify your monitor and video card, the resolutions and color depths you want to run the server at, and so forth.

Since every setup is different, it's hard to give concrete advice for configuring X, but it's generally OK to accept the configuration defaults. Also, you'll be given a choice between Advanced, Medium, and Simple methods for giving your monitor's specifications. As a rule, it's probably best to go with Simple unless you really know what you're doing, or the Simple method doesn't work for you.

8. Log in automagically 

By default, when you boot up the computer, Ubuntu will give you a login screen before you get to your X session. From a security perspective, this is a good idea, particularly in multi-user environments or in any situation where other people have physical access to your computer. Still, many users are used to just being logged in automatically, and don't want to fuss with logging in each time they reboot their desktop.

To set this in Ubuntu, go to System -> Administration -> Login Window. You'll need to provide your password, then you'll get the Login Window Preferences window with five tabs. Choose the Security tab and click Enable Automatic Login. If you have more than one regular user, make sure to specify which user should be logged in automatically.

Again, and I can't stress this enough, this is only a good idea for home computers where only one person has access to the computer. I don't recommend this for work computers or laptop/notebook computers, when someone else might have access to the machine.

9. Compiling from source 

Ubuntu's package repository is huge, particularly when you factor in packages in the Universe and Multiverse repositories. However, many users find themselves needing to install packages from source, either because they want to use a newer package than is available in the repository, or they want to try something that's not in the Ubuntu repository at all.

If you want to install packages from source, you can use a few shortcuts to make life easier. First, you'll probably want to get the build-essential meta-package if you haven't installed any developer tools. Run sudo apt-get install build-essential; it will grab GCC, the Linux kernel headers, GNU Make, and some other packages that you'll probably need.

Next, if you're going to compile a package such as Gaim because a new version is out, you might be able to satisfy the new version's dependencies with the old version's dependencies. To do this, grab the package's build dependencies with sudo apt-get build-dep packagename . That will grab all of the development packages you need to build the package that's currently available in Ubuntu, and will probably satisfy dependencies for the new version you're compiling.

Finally, don't make install when you compile from source -- use CheckInstall instead. CheckInstall will create a Debian package and install it for you, so you can remove or upgrade the software more easily later on.

Grab CheckInstall with apt-get install checkinstall. After you've run ./configure ; make, just run sudo checkinstall and answer a few simple questions. Note that if you compile packages on AMD64, CheckInstall will select X86_64 as the architecture rather than amd64 -- which will cause the package install to fail, since Ubuntu expects amd64 as the architecture rather than X86_64.

By the way, the packages created by CheckInstall also make it easier to deploy the same package on several machines, if you happen to have several systems running Ubuntu. See Joe Barr's excellent CLI Magic feature on CheckInstall too.

10. A new kernel 

Ubuntu will install a 386 kernel for x86 machines, which probably isn't what you'd want if you've got a Pentium II or better CPU. The 386 kernel is compiled to work with just about any x86 CPU, but extensions that appear in later CPUs can give your system a boost, if they're taken advantage of. To replace the kernel, open Synaptic or Adept and search for linux-image. You'll see several choices. Pick the one that best suits your CPU -- probably the linux-image-686 package for Pentium II and later CPUs, and linux-image-k7 for later AMD processors. Note that if you're using the AMD64 line (or Intel's x86-64 CPUs) you should be using the amd64 images.

Of course, once you install the new kernel, you'll need to reboot. Another benefit to the 686 kernels is that they have SMP support, which is a bonus for multi-core and Intel HyperThread CPUs.

If none of the tips cover questions that you have about Ubuntu, try checking out the Ubuntu wiki, forums, and mailing lists. As a rule, the Ubuntu users are a helpful lot, and you'll usually be able to find someone who's run into the same situation that you have questions about.



source : [http://www.linux.com/feature/54945](http://www.linux.com/feature/54945)

---

### Post by bapoumba on 2009-04-07
[Twenty Free Linux Books ]("http://ubuntuforums.org/showthread.php?t=1118334")

---

### Post by bapoumba on 2009-04-28
[Things you need to know about Ubuntu...that will make your life easier!]("http://ubuntuforums.org/showthread.php?p=7157629")

---

