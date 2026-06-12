---
title: "Windows 95 computer distro?"
date: 2006-07-05
forum: Other OS Talk
---

### Post by codypumper on 2006-07-05
I have a windows 95 computer which is sitting in the attic. I've tryed DSL, Ubuntu, Suse slick, Sylable , and puppy linux on it. DSL got the furthest in installation, about halfway. Is there any other distro that may work?

---

### Post by LKRaider on 2006-07-05
A bare Debian with 2.4 kernel?

---

### Post by codypumper on 2006-07-05
Ok, I'll try that, any others?

---

### Post by andlinux21 on 2006-07-05
you can try slackware low memory install :D

---

### Post by codypumper on 2006-07-05
I'll try both, anything else?

---

### Post by codypumper on 2006-07-05
I would like some links...

---

### Post by Adrenal on 2006-07-06
xubuntu might do
And, for the links, [www.google.com](www.google.com) should do nicely

---

### Post by codypumper on 2006-07-06
Xubuntu will not work, we're talking 32mb of ram or less...

---

### Post by fuscia on 2006-07-06
netbsd might work.

---

### Post by Johnsie on 2006-07-06
I found Morphix to work well on older machines that Xubuntu, dsl, and puppy wouldnt. It's very much like them and uses XFCE.

---

### Post by Iandefor on 2006-07-06
I wouldn't recommend XFCE for anything that has less than 64 MB...

You might try [Elive]("http://www.elivecd.org/"), or something like [gentoo]("http://www.gentoo.org/") without anything X-related (Stick with pure bash!).

---

### Post by codypumper on 2006-07-06
I think I'll try slackware first, thank you!

---

### Post by RAV TUX on 2006-07-06
[LIST]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[Devil Linux]("http://www.devil-linux.org/")**[/COLOR][/SIZE][/FONT][/COLOR]

[COLOR=black]
[*][[IMG]http://img276.imageshack.us/img276/2373/logo5qt.th.png[/IMG]]("http://img276.imageshack.us/my.php?image=logo5qt.png")
 Devil Linux's goal is to have a small, customizable and secure Linux distribition.[COLOR=Red] **It runs with 32MB RAM**[/COLOR], with no need for a harddisk. The traditional application for Devil-Linux is to use it as a Router/Firewall.[/COLOR][/SIZE][/FONT][/LIST]Devil-Linux is a distribution which boots and runs completely from CDROM. The configuration can be saved to a floppy diskette or a USB pen drive. Devil Linux was originally intended to be a dedicated firewall/router but now Devil-Linux can also be used as a server for many applications. Attaching an optional hard drive is easy, and many network services are included in the distribution.
         The system is designed to install without the use of a hard drive. It requires the use of a CDROM and a write-protected floppy. The CDROM provides the operating system, and the floppy provides the configuration information, via a tarball that is unpacked into the /etc directory. In this way, the system is fully configurable, yet the running system has no writeable device.



 **What makes Devil Linux the best Firewall on the market**

 Devil-Linux is not like any other distribution. It is created from IT Administators for IT Administrators. We know what you need, because we need it too![LIST]
[*]         **Boots from CD**

          Traditionally Devil Linux boots from a CD-ROM which is read-only by nature. This means an intruder will not be able to install i.e. an "ordinary" root kit.
[*]         **Boots from USB pendrive**

          As all movable parts in your computer, the CD-ROM is prone to failure. This is the reason why we provide a script to install the entire system on an USB pendrive. Note: You need a computer which is able to boot from USB harddisks, in order to use this feature.
[*]         **Configuration is saved on a floppy disc or on a USB Flash Media**

          Due to the read-only nature of CD-ROMs, you need a place to save your configuration files. This can either traditionally be on a floppy disc or on a USB flash media (like a pendrive), to increase the reliability.
[*]         **Configuration can be burned on CD**

          There are cases when you have to ensure that the configuration can't be modified. This is the reason why we provide the feature for loading the configuration archive from the (read-only) CD-ROM.
[*]         **No need for a harddisk although it can optionally be used for data storage**

          Most distributions need a harddisk for data storage, with DL this is completely optional. Reasons for adding harddisk data storage would be, i.e. when you use DL as your mail server or for file sharing. DL uses dynamic disc configuration via the Logical Volume Manager, which makes adding and maintaining the harddisk storage easy (regardless if you have only 1 GB or 1 TB of data).
[*]         **Support for Intel 486 and higher**

          Got some old boxes in your bone yard? For most internet connection an old computer is enough to play the role of your Firewall, this is the reason why we still support 486 CPUs. But we're not stuck with old technologies, we also provide you a version vor 686 CPUs with SMP support.
[*]         **IPTables/Netfilter Support**

          State of-the-art firewall functionality is provided by IPTables/Netfilter, which includes features like connection tracking. Devil-Linux adds many more Netfilter modules then you find in your standard Linux Kernel.
[*]         **Create your own, customized version with our Build System**

          Since everybody has different requirements, Devil-Linux provides you with an easy-to-use build system, which enables you to create your own customized version. You can i.e. only add the packages you need on your machine or even add features which are currently missing in the mainstream version.
[*]         **Directly supported by Firewall Builder**

          Don't like writing your Firewall rules by hand? Get Firewall Builder and use a great GUI tool to create your ruleset. Firewall Builder supports writing the rules directly onto your configuration floppy.
[*]         **No graphical desktop**

          Devil-Linux has not support for i.e. X-Server. This greatly reduces the requirements to run DL and also greatly increases security by reducing the number of running programs. (Try this on Windows...)
[*]         **Almost all binaries are compiled with the GCC Stack Smashing Protector**

          Except of a very few exceptions, all binaries are compiled with the GCC Stack Smashing Protector. Applications written in C will be protected by the method that automatically inserts protection code into an application at compilation time. The protection is realized by buffer overflow detection and the variable reordering feature to avoid the corruption of pointers.
[*]         **Improved Kernel Security through GRSecurity**

          GRSecurity adds several new features and protection mechanisms to the Linux Kernel itself. This includes Chroot restrictions (did you know that it is easy to break out of a non-protected chroot jail?), Address space modification protection (like PAX), Auditing features, Randomization features and much more.
[*]         **Easy to use chroot**

          Devil-Linux has support for chroot jails which is easy to use. Just define what you need in a configuration file and our jail script will take care of the rest. Some pre-defined configurations are already available.[/LIST]**Applications for Devil-Linux**

  The traditional application for Devil-Linux is to use it as Router/Firewall. Below you see a list of other possible applications:[LIST]
[*]Proxy Server
[*]DNS Server
[*]Mail Server with TLS support and Spam and Virus filtering
[*]HTTP Server
[*]FTP Server
[*]File Server
[*]VPNs with X.509 support
[*]DHCP Server
[*]NTP Server
[*]IDS Node[/LIST]

---

### Post by RAV TUX on 2006-07-06
Also try Grey Cat Linux:[LIST]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[Grey Cat Linux]("http://www.pcpages.com/greyclinux/")**[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/LIST]from the GCL download / installation site
Grey Cat Linux is a small UMSDOS Linux distro with Xfree, Icewm, Netscape, XV, and more. **[COLOR=Red]Download is only 12 megs[/COLOR]**
For more information, support ans forums look at:  [Dekoningonline.nl]("http://www.dekoningonline.nl/")
  
To install Grey Cat Linux 3.0, download all files listed below, and extract them to C:\ when you have done that, just follow the instructions at [install.txt]("http://www.greycatlinux.myweb.nl/30/install.txt")
  files:
[linuxrar.zip]("http://www.pcpages.com/greyclinux/linuxrar.zip")
[linuxr00.zip]("http://www.pcpages.com/greyclinux/linuxr00.zip")
[linuxr01.zip]("http://www.pcpages.com/greyclinux/linuxr01.zip")
[linuxr02.zip]("http://www.pcpages.com/greyclinux/linuxr02.zip")
[linuxr03.zip]("http://www.pcpages.com/greyclinux/linuxr03.zip")
[linuxr04.zip]("http://www.pcpages.com/greyclinux/linuxr04.zip")
[linuxr05.zip]("http://www.pcpages.com/greyclinux/linuxr05.zip")
[linuxr06.zip]("http://www.pcpages.com/greyclinux/linuxr06.zip")
[linuxr07.zip]("http://www.pcpages.com/greyclinux/linuxr07.zip")
[install.zip]("http://www.pcpages.com/greyclinux/install.zip")

---

### Post by RAV TUX on 2006-07-06
Give Jailbait a try also:[LIST]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[jailbait]("http://jailbait.sourceforge.net/")**[/COLOR][/SIZE][/FONT] 
 JAILBAIT's Another Interesting Linux But Also Intimidating Too: **[COLOR=Red]A fully-functional Linux distribution that fits into 16 MB.[/COLOR]** Many modern net-appliance-type products such as the Netpliance iOpener have an internal SanDisk device that is 16 MB in size.[/COLOR][/SIZE][/FONT][/LIST]**The current release of JAILBAIT is version 6.** 
         [Screenshot 1]("http://jailbait.sourceforge.net/jailbait_6_screenshot-2.png")          | [Screenshot 2]("http://jailbait.sourceforge.net/jailbait_6_screenshot-3.png")    

                       Version 6 includes many new apps:  
       Netscape Navigator 4.73
         [ishmail]("http://ishmail.sourceforge.net/")              - for reading IMAP mail (pop not yet supported)
         esd, the ESound Daemon
         vncviewer -             [Control virtually any UNIX or 'doze box]("http://www.uk.research.att.com/vnc/")
         an installation utility to help you get going
         and many other improvements!  
       A full list of included executables can be viewed [here]("http://jailbait.sourceforge.net/applications.txt").

[[IMG]http://img146.imageshack.us/img146/7306/klownerjailbaitdistromascot5un.th.gif[/IMG]]("http://img146.imageshack.us/my.php?image=klownerjailbaitdistromascot5un.gif")

[Download V6!]("http://download.sourceforge.net/JAILBAIT/version6_fullinstall.img.gz")         
[README for V6]("http://jailbait.sourceforge.net/README")
 [JAILBAIT Faq]("http://jailbait.sourceforge.net/faq.html")
 [Go to SourceForge]("http://sourceforge.net/project/?group_id=4981")
 [LEM home]("http://www.linux-embedded.com/")
        [.config for 2.4.0test1 used in V6]("http://jailbait.sourceforge.net/config-2.4.0test1")

---

### Post by codypumper on 2006-07-06
Grey cat linux looks ideal ( only 8mb of ram reccomended)
I'm amazed by the help I get on a non-ubuntu topic...
Thank you

---

### Post by RAV TUX on 2006-07-06
[LIST]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[LNX-BBC]("http://www.lnx-bbc.org/")**[/COLOR][/SIZE][/FONT]
[*]The LNX-BBC is a mini Linux-distribution, small enough to fit on a CD-ROM that has been cut, pressed, or molded to the size and shape of a business card. LNX-BBCs can be used to rescue ailing machines, perform intrusion post-mortems, act as a temporary workstation, and perform many other tasks.[/COLOR][/SIZE][/FONT][/LIST]The LNX-BBC is a mini Linux-distribution, small enough to fit on a CD-ROM that has been cut, pressed, or molded to the size and shape of a business card.
    LNX-BBCs can be used to rescue ailing machines, perform intrusion post-mortems, act as a temporary workstation, and perform many other tasks that we haven't yet imagined.  
    For more information about the LNX-BBC, check out our [FAQ]("http://www.lnx-bbc.org/faq.html"), or consult our many [mailing lists]("http://www.lnx-bbc.org/lists.html").
    If you are interested in contributing to the LNX-BBC project, or if you just like to tinker, there is more information on the [GAR README page]("http://www.lnx-bbc.org/README.html").
    If you're just looking to download ISO images, have a look at our [download page]("http://www.lnx-bbc.org/download.html").
_[[IMG]http://img84.imageshack.us/img84/4387/labelslug0oj.png[/IMG]](http://imageshack.us)_[]("http://imageshack.us")

---

### Post by RAV TUX on 2006-07-06
[LIST][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[Monkey Linux]("http://ftp.spsselib.hiedu.cz/pub/linux/monkey/")**[/COLOR][/SIZE][/FONT] 
 Monkey Linux a complete small ELF distribution with latest kernel on 5 diskettes. Monkey can run on this minimal HW: 386SX, 4MB RAM, 30MB on IDE HDD. Contain X Window for any SVGA videocard, support for network, support for 3C5x9, 3c59x, 3c900, NE2000/NE1000, WD80x3 ethernet cards, ATAPI/MITSUMI CD.
[/COLOR][/SIZE][/FONT][/LIST]

---

### Post by codypumper on 2006-07-06
thanks, I'll tell you how it goes!

---

### Post by RAV TUX on 2006-07-06
[quote=codypumper]thanks, I'll tell you how it goes![/quote]

Cool!, I have more for you to try:

[LIST][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[slimlinux]("http://slimlinux.freezope.org/")**[/COLOR][/SIZE][/FONT] 
 slimlinux is a multi-purpose Linux mini distribution that can be installed to a FAT partition. It includes Linux 2.4.18,X Window 4.2.0, Busybox, support for IDE/ATAPI/USB/EXT2/Minix/vfat/UMSDOS/MSDOS/OSS, the retawq text browser, mutt 1.2.5.1 with IMAP, mawk, lua, nano,and over 60 Linux utilities. slimlinux is installed to a FAT16/FAT32 partition and requires 16 MB RAM, 3 MB hard disk space (system runs in RAM) and Framebuffer display device. 
[/COLOR][/SIZE][/FONT][/LIST]
**[FONT=Courier][COLOR=blue]slimlinux[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]

[/COLOR][/FONT]**[FONT=Courier][COLOR=blue]Description[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]slimlinux is multi-purpose Linux mini distribution which
fits to one floppy or can be installed to FAT partition.

Its main features are:

- Kernel 2.4.18
- minimal XFree86 4.2.0
- yeahwm 0.2.0 and ratpoison 1.3.0 window managers
- [Busybox 1.00-pre7]("http://busybox.net/")
- [uClibc 0.9.26]("http://uclibc.org/")
- IDE/ATAPI/PCMCIA/Network/OSS support
- USB support for mass storage devices
- EXT2/Minix/vfat/UMSDOS/MSDOS filesystems
- [retawq 0.2.5a text browser]("http://retawq.sourceforge.net/")
- [mutt 1.2.5.1 with IMAP]("http://www.mutt.org/")
- [Lua 4.01]("http://www.lua.org/")
- mawk 1.33
- nano 1.2.4
- mcdp 0.4
- aumix 2.8
- bplay 0.99
- over 60 Linux utilities
- [ssmtp 2.48]("http://ibiblio.org/pub/Linux/system/mail/mta")
- [udhcpc 0.9.8]("http://udhcp.busybox.net/")


slimlinux is available in both floppy (1722k, version 0.7.0) and hard disk versions, latter is 
installed to DOS/WIN (FAT16/FAT32) partition, both versions run in RAM (16 MB required) and
need Framebuffer display device.


The latest version is 0.80. 

[/COLOR][/FONT] **[FONT=Courier][COLOR=blue]Installation[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]	**Hard disk**
   
	Untar slimlinux-0.8.0.tar.gz (or unzip slimlinux-0.8.0.zip) to any directory and start from 
        MS-DOS (not Windows MS-DOS Prompt) prompt using command slim.bat. 

	
[/COLOR][/FONT]  **[FONT=Courier][COLOR=blue]ChangeLog[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]slimlinux 0.80 (09/26/04)

	-current version
	-compiled X Window 4.2.0
	-compiled yeahwm 0.2.0 and ratpoison 1.3.0
	-zile changed to nano 1.2.4
	-added OSS support to kernel
	-no floppy version
	-Clex, eForth and cmdftp removed
	-added mcdp 0.4, aumix 2.8 and bplay 0.99
        -awk changed to mawk 1.33
        -retawq updated to 0.2.5a


slimlinux 0.70 (04/18/04)

	- most components compiled with dynamic libraries
	- USB support to separate modules (slimmodules-0.7.0.tar.gz) 
	- compiled mutt 1.2.5.1 with IMAP
	- compiled Clex 3.1.8
	- compiled Lua 4.01
	- compiled eForth 1.0e
	- compiled zile 1.6.2
	- compiled cmdftp 0.7.3
	- e3 removed
	- mutt updated to 1.2.5.1
	- retawq updated to 0.2.4

slimlinux 0.60 (01/08/04)

	- compiled BusyBox 1.00-pre7
	- compiled retawq 0.2.2
	- compiled mutt-1.00 with IMAP

slimlinux 0.50 (01/28/04)

	- kernel 2.4.18
	- added PCMCIA support 
	- USB support for mass storage devices
	- compiled udhcpc 0.9.8 
	- compiled fetchpop 1.9
	- compiled smtpclient 1.0
	- compiled ssmtp 2.48
	- added e3 editor

slimlinux 0.40 (01/20/04)

	- no Slackware comnponents anymore
        - all tools build with gcc and uClibc
	- kernel 2.2.19
	- compiled BusyBox 0.60.5
	- compiled "the one true" awk
	- retawq 0.2.1 instead of Links

slimlinux 0.31 (01/09/04)
- initial release
	- added network modules (3c5xx, eepro100,ne,rtl8139,smc-ultra)
	- compiled Links 0.82
	- Busybox compiled with new options
	
slimlinux 0.3 (01/06/04)
- test version
	- changed utilities

slimlinux 0.2 (01/05/04)
- test version
	- compiled Busybox 0.60.4

slimlinux 0.1 (01/02/04)
-test version
	- Kernel 2.2.16
	- all utilities from Slackware 7.1


[/COLOR][/FONT] **[FONT=Courier][COLOR=blue]Download[/COLOR][/FONT]**

 
**[FONT=Courier][COLOR=blue]Current version[/COLOR][/FONT]**



[FONT=Courier][COLOR=blue][slimlinux-0.8.0.tar.gz, ~2.8 MB)]("http://ibiblio.org/pub/Linux/distributions/slimlinux/slimlinux-0.8.0.tar.gz")
[slimlinux-0.8.0.zip, ~2.8 MB)]("http://ibiblio.org/pub/Linux/distributions/slimlinux/slimlinux-0.8.0.zip")


[/COLOR][/FONT]**[FONT=Courier][COLOR=blue]Previous version[/COLOR][/FONT]**


[FONT=Courier][COLOR=blue]Previous versions are available from 

[ibiblio.org]("http://ibiblio.org/pub/Linux/distributions/slimlinux/")



slimlinux is released under [MIT License]("http://slimlinux.freezope.org/mit.html"). BusyBox is licensed 
under [GPL,]("http://busybox.net/license.html") full source code is available from [BusyBox site.]("http://busybox.net/download.html") 
[uClibc]("http://uclibc.org/") is licensed under [Lesser GPL]("http://www.gnu.org/copyleft/lesser.html") and [retawq]("http://retawq.sourceforge.net/") is also licensed under
GPL. 



Unfortunately there is no active support, you are in your own with slimlinux.
I will maintain and update software whenever I have time and check mails
occasionally (but will check them anyway). You can send feedback and bug reports 
to address below.[/COLOR][/FONT]
**[FONT=Courier][COLOR=blue]slimlinux[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]

[/COLOR][/FONT]**[FONT=Courier][COLOR=blue]Description[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]slimlinux is multi-purpose Linux mini distribution which fits to one floppy or can be installed to FAT partition.  Its main features are:  - Kernel 2.4.18 - minimal XFree86 4.2.0 - yeahwm 0.2.0 and ratpoison 1.3.0 window managers - [Busybox 1.00-pre7]("http://busybox.net/") - [uClibc 0.9.26]("http://uclibc.org/") - IDE/ATAPI/PCMCIA/Network/OSS support - USB support for mass storage devices - EXT2/Minix/vfat/UMSDOS/MSDOS filesystems - [retawq 0.2.5a text browser]("http://retawq.sourceforge.net/") - [mutt 1.2.5.1 with IMAP]("http://www.mutt.org/") - [Lua 4.01]("http://www.lua.org/") - mawk 1.33 - nano 1.2.4 - mcdp 0.4 - aumix 2.8 - bplay 0.99 - over 60 Linux utilities - [ssmtp 2.48]("http://ibiblio.org/pub/Linux/system/mail/mta") - [udhcpc 0.9.8]("http://udhcp.busybox.net/")   slimlinux is available in both floppy (1722k, version 0.7.0) and hard disk versions, latter is  installed to DOS/WIN (FAT16/FAT32) partition, both versions run in RAM (16 MB required) and need Framebuffer display device.   The latest version is 0.80.   [/COLOR][/FONT] **[FONT=Courier][COLOR=blue]Installation[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]	**Hard disk**     	Untar slimlinux-0.8.0.tar.gz (or unzip slimlinux-0.8.0.zip) to any directory and start from          MS-DOS (not Windows MS-DOS Prompt) prompt using command slim.bat.   	 [/COLOR][/FONT]  **[FONT=Courier][COLOR=blue]ChangeLog[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]slimlinux 0.80 (09/26/04)  	-current version 	-compiled X Window 4.2.0 	-compiled yeahwm 0.2.0 and ratpoison 1.3.0 	-zile changed to nano 1.2.4 	-added OSS support to kernel 	-no floppy version 	-Clex, eForth and cmdftp removed 	-added mcdp 0.4, aumix 2.8 and bplay 0.99         -awk changed to mawk 1.33         -retawq updated to 0.2.5a   slimlinux 0.70 (04/18/04)  	- most components compiled with dynamic libraries 	- USB support to separate modules (slimmodules-0.7.0.tar.gz)  	- compiled mutt 1.2.5.1 with IMAP 	- compiled Clex 3.1.8 	- compiled Lua 4.01 	- compiled eForth 1.0e 	- compiled zile 1.6.2 	- compiled cmdftp 0.7.3 	- e3 removed 	- mutt updated to 1.2.5.1 	- retawq updated to 0.2.4  slimlinux 0.60 (01/08/04)  	- compiled BusyBox 1.00-pre7 	- compiled retawq 0.2.2 	- compiled mutt-1.00 with IMAP  slimlinux 0.50 (01/28/04)  	- kernel 2.4.18 	- added PCMCIA support  	- USB support for mass storage devices 	- compiled udhcpc 0.9.8  	- compiled fetchpop 1.9 	- compiled smtpclient 1.0 	- compiled ssmtp 2.48 	- added e3 editor  slimlinux 0.40 (01/20/04)  	- no Slackware comnponents anymore         - all tools build with gcc and uClibc 	- kernel 2.2.19 	- compiled BusyBox 0.60.5 	- compiled "the one true" awk 	- retawq 0.2.1 instead of Links  slimlinux 0.31 (01/09/04) - initial release 	- added network modules (3c5xx, eepro100,ne,rtl8139,smc-ultra) 	- compiled Links 0.82 	- Busybox compiled with new options 	 slimlinux 0.3 (01/06/04) - test version 	- changed utilities  slimlinux 0.2 (01/05/04) - test version 	- compiled Busybox 0.60.4  slimlinux 0.1 (01/02/04) -test version 	- Kernel 2.2.16 	- all utilities from Slackware 7.1   [/COLOR][/FONT] **[FONT=Courier][COLOR=blue]Download[/COLOR][/FONT]**

  **[FONT=Courier][COLOR=blue]Current version[/COLOR][/FONT]**

  [FONT=Courier][COLOR=blue][slimlinux-0.8.0.tar.gz, ~2.8 MB)]("http://ibiblio.org/pub/Linux/distributions/slimlinux/slimlinux-0.8.0.tar.gz") [slimlinux-0.8.0.zip, ~2.8 MB)]("http://ibiblio.org/pub/Linux/distributions/slimlinux/slimlinux-0.8.0.zip")   [/COLOR][/FONT]**[FONT=Courier][COLOR=blue]Previous version[/COLOR][/FONT]**

 [FONT=Courier][COLOR=blue]Previous versions are available from   [ibiblio.org]("http://ibiblio.org/pub/Linux/distributions/slimlinux/")    slimlinux is released under [MIT License]("http://slimlinux.freezope.org/mit.html"). BusyBox is licensed  under [GPL,]("http://busybox.net/license.html") full source code is available from [BusyBox site.]("http://busybox.net/download.html")  [uClibc]("http://uclibc.org/") is licensed under [Lesser GPL]("http://www.gnu.org/copyleft/lesser.html") and [retawq]("http://retawq.sourceforge.net/") is also licensed under GPL.     Unfortunately there is no active support, you are in your own with slimlinux. I will maintain and update software whenever I have time and check mails occasionally (but will check them anyway). You can send feedback and bug reports  to address below.  [/COLOR][/FONT] [FONT=Courier][COLOR=blue]
[/COLOR][/FONT][FONT=Courier][COLOR=blue]
[FONT=Courier][SIZE=1][COLOR=red] Last update: 09/27/04
slimlinux is developed and maintained by Jukka-Pekka Kervinen.
Copyright © 2003-2004 Jukka-Pekka Kervinen. All rights reserved.
Contact: slimlinux aT mailcan dOT com [/COLOR][/SIZE][/FONT] 
[/COLOR][/FONT][FONT=Courier][COLOR=blue]
[/COLOR][/FONT]

---

### Post by RAV TUX on 2006-07-06
[LIST]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[Small Linux]("http://www.superant.com/smalllinux/")**[/COLOR][/SIZE][/FONT] 
 Small Linux is a partial distribution of the Linux kernel and support files that [COLOR=Red]**can boot on older x86 systems with less than 5 meg of RAM memory.**[/COLOR][/COLOR][/SIZE][/FONT][/LIST]**  Linux - Small Kernel Project**

**[COLOR=Red]  Small Linux has been used (console based) on a 386 laptop with 2 meg of ram and a 40 meg harddrive.      [/COLOR]**
** Resources on Small Linux**

  [ Small Linux News  ]("http://www.superant.com/cgi-bin/smalllinux.pl?Small_Linux_NEWS") [Small Linux Wiki RecentChanges]("http://www.superant.com/cgi-bin/smalllinux.pl?RecentChanges")
 [Small Linux - FAQ. ]("http://www.superant.com/cgi-bin/smalllinux.pl?Small_Linux_FAQ")
 [Small Linux mini-howto. ]("http://www.superant.com/smalllinux/howto.html")
 [Release notes for Small Linux 0.7.5. ]("http://www.superant.com/smalllinux/smalllinux075.html")
   [ How to set up plip or slip with Small Linux]("http://www.superant.com/cgi-bin/smalllinux.pl?Network_Connections") 
 [Small Linux install experiences and notes]("http://www.superant.com/cgi-bin/smalllinux.pl?Experiences_Installing_Small_Linux") 
 [Download Small Linux]("http://www.superant.com/smalllinux/smalldown.html") 
 [Small Linux Wiki - for notes and FAQs]("http://www.superant.com/cgi-bin/smalllinux.pl") 
 [ Small Linux executibles - file list]("http://www.superant.com/smalllinux/files.html") 
[small X - libc 5 format - X Windows in less only 4 megs of ram - ]("http://www.superant.com/cgi-bin/smalllinux.pl?SmallX") 
 
[Tiny X - Download ]("http://www.superant.com/smalllinux/smallX/tinyX01.html") 
  [Small Linux FAQ in Danish ]("http://www.superant.com/smalllinux/faq-dk.html")
 [Small Linux FAQ in German]("http://www.superant.com/cgi-bin/smalllinux.pl?Small_Linux_FAQ_-_German") 
 [ Running Small Linux in the Plex86 virtual machine  ]("http://www.superant.com/cgi-bin/smalllinux.pl?SmallPlex86")
 [  Linux Kernel Information   ]("http://www.superant.com/cgi-bin/smalllinux.pl?LinuxKernel")
 [Links to other projects]("http://www.superant.com/cgi-bin/smalllinux.pl?Other_Small_Linux_Projects")
 [Programming under Linux]("http://www.superant.com/cgi-bin/smalllinux.pl?Programming_Linux")
   
**Mail us at: E-mail:smalllinux at superant dot com**

---

### Post by RAV TUX on 2006-07-06
[LIST]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black][/COLOR][/SIZE][/FONT][FONT=arial, helvetica][SIZE=2][COLOR=black]
[*][FONT=arial, helvetica][SIZE=2][COLOR=black]**[TINY]("http://tiny.seul.org/")**[/COLOR][/SIZE][/FONT] 
 Tiny Linux is a small Linux distribution designed especially for old recycled computers.[/COLOR][/SIZE][/FONT][/LIST]**Tiny Linux** is a small Linux distribution designed especially for    old recycled computers.

    [COLOR=red]*05/06/18: Andre Nieuwoudt andre - at - computron.za.net is taking over the project; please contact him if you want to help!! *[/COLOR]
    [IMG]http://tiny.seul.org/zimaj/tatou.gif[/IMG]     TINY Linux distribution comes under [**GNU GPL**]("http://www.gnu.org/").


     _**Technical requirements:**_
    [LIST]
[*]processor : **i386** or better
[*]hard disk : **50 Mo** is enough for installation itself, but you will do better with at least **80** Mo
[*]ram:[COLOR=Red]** 8 MB minimum**[/COLOR], 12 MB or 16 MB is better
[*]floppy drive :**3"1/4**
[*]keyboard, mouse[/LIST]    
    
            next: [ installation ]("http://tiny.seul.org/en/i.html")

---

### Post by Iandefor on 2006-07-06
yozef... you're insane.

---

### Post by LKRaider on 2006-07-06
Please post back which distro you adopted for this pc :)

---

### Post by RAV TUX on 2006-07-06
[quote=Iandefor]yozef... you're insane.[/quote]

I think that might be a compliment. Thank You.;)

---

### Post by codypumper on 2006-07-10
I attempted Gray Cat, Small, and  Deli linux. None of them complete installation. Seems Cd-drive is broken. Deli LInux had the lowest requirements for its WM (XFCE)

---

### Post by NESFreak on 2006-07-11
FreeDOS for the good old dos games your modern windows can't run :)
[http://en.wikipedia.org/wiki/Freedos](http://en.wikipedia.org/wiki/Freedos)
[http://freedos.sourceforge.net/](http://freedos.sourceforge.net/)

---

### Post by alecjw on 2006-09-26
Ubuntu.:) I've installed Ubuntu on a PII 266MHz, 64MB RAM (ex-w95). I just did a server install and then installed the gnome desktop environment.

---

### Post by K.Mandla on 2006-09-26
True, [Ubuntu will work]("http://www.ubuntuforums.org/showthread.php?t=259901"). But for [what I've seen]("http://www.ubuntuforums.org/showthread.php?t=125334"), some [Slackware]("http://www.slackware.com/")-based distros might have better performance on older hardware. 

I know [SLAX Standard 5.1.7b]("http://www.slax.org/") runs perfectly on a couple of old laptops that proved stubborn with Ubuntu (hardware detection hangups ...).

---

