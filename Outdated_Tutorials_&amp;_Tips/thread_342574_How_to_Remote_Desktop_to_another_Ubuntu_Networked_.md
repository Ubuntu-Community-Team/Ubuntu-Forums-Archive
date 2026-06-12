---
title: "How to Remote Desktop to another Ubuntu Networked PC using the embedded &quot;tsclient&quot;"
date: 2007-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by dvarsam on 2007-01-20
Hello!

This is my contribution to other Ubuntu users:

**Tutorial - How to Remote Desktop to another Ubuntu Networked PC using the embedded "tsclient":**


[color=red]_For Ubuntu v6.10 (Edgy Eft) - Gnome Desktops_:[/color]

This is the easiest method I have found on using Remote Desktop to connect to another Ubuntu Networked PC.
It does NOT require any installation of Packages & I don't understand why it isn't considered the standard method of dealing with Remote Desktop connections...

_Note_:
For Kubuntu &#8211; KDE Desktops, you can use the package "Krdc". I think this is also embedded too!

**_Part A_:**
On the computer you want to connect to:

**1.** From your Menu, select "[color=blue]System\Preferences\Remote Desktop[/color]".

**2.** Click on the box named "[color=blue]Allow other users to view your desktop[/color]".

    _Note_:
    The following check boxes should also be checked:

    Under Sharing:

	a. "[color=blue]Allow other users to view your desktop[/color]" (required)
	b. "[color=blue]Allow other users to control your desktop[/color]" (optional &#8211; this is up to you)

    Under Security:

	c. Remove click from "[color=blue]Ask you for confirmation[/color]" (optional &#8211; this is up to you)
	d. Click on "[color=blue]Require the user to enter this password[/color]" & add your preferred password (optional &#8211; this is up to you).

	e. Click on the button named "[color=blue]Close[/color]".

**_Part B_:**
On the computer you are connecting from:

**1.** Launch a Terminal window & type "[color=blue]tsclient[/color]" (package comes already pre-installed in Ubuntu v6.10) 

**2.** Under the Tab named "[color=blue]General[/color]", add the following info:

    a. Under "Computer", type:		[color=blue]IP[/color] of PC you want to connect to (e.g. 192.168.1.3)

    b. Under "Protocol&#8221;, select:		[color=blue]VNC[/color] (to connect to an Ubuntu PC) [color=red]or[/color] [color=blue]RDPv5[/color] ( to connect to a Windows PC)
				_Note_:
					RDPv5 enables copy&paste to work between the 2 connected PCs.
					In this way, you can transfer files between the 2 connected PCs.

    c. Under "User Name", type:	The [color=blue]username[/color] of the PC you are connecting to (e.g. elena)

    d. Under "Client HostName", type:	The [color=blue]HostName[/color] of the Client PC (e.g. elena-desktop)
					_Note_:
					If you don't know what the Hostname of Client PC is, launch a 
					Terminal window on the Client PC & type: "hostname".

    e. Click on the button named "[color=blue]Connect[/color]".

A new window will appear on your Desktop & inside it, you can view your other Ubuntu PC's Desktop, connected on your local LAN, Remotely!

_Notes_:
1. Whatever you select/click on the Client PC Remotely, the person sitting on the Client PC can see it - PartA2b option (this is good for education purposes &#8211; the person sitting on the Client PC could initiate a presentation and all users Remotely connected users can watch the ongoing Presentation!).
2. 2. IMHO, using "tsclient", is the easiest Remote Desktop program I have found for Ubuntu Gnome. There is no packages you need to install &#8211; all you have to do is a few simple clicks to set this up... (I provided these above).
However, other users in this forum, suggest using other programs like:

	a. "Vnc" or "Realvnc" (name of Free version - from: [www.realvnc.com](www.realvnc.com)) - you can find more [ here1](http://ubuntuforums.org/showthread.php?t=122402), [ here2](http://ubuntuforums.org/showthread.php?t=259448), [ here3](http://ubuntuforums.org/showthread.php?t=135036), [ here4](http://ubuntuforums.org/showthread.php?t=42941), [ here5](http://ubuntuforums.org/showthread.php?t=197964), [ here6](http://ubuntuforums.org/showthread.php?t=279069) & [ here7](http://ubuntuforums.org/showthread.php?t=88011).
	b. "TightVnc" (from: [www.tightvnc.com](www.tightvnc.com))
	c. "X11vnc" (from: [www.karlrunge.com](www.karlrunge.com)) - you can find more [ here1](http://ubuntuforums.org/showthread.php?t=299489).
	d. "NX" or "FreeNX" (name of Free version &#8211; from: [www.nomachine.com](www.nomachine.com)) you can find more [ here1](http://ubuntuforums.org/showthread.php?t=1968).
	e. "Krdc" (embedded in Kubuntu KDE &#8211; from: [www.kde.org](www.kde.org))

**_Suggestions for Future Improvements_:**
**1.** I don't understand why there is NO shortcut/link of the program "tsclient", showing on the Ubuntu Menus (why on earth in order to run this program I have to launch it from the Terminal... :confused:).
   A shortcut/link should be added & called "Remote Desktop" (I truly wonder why the Ubuntu developers haven't though of that... :-\" ).
**2.** It would be important if only the "root" user had the privileges to access the settings of the "System\Preferences\Remote Desktop" window. This is good for Administration purposes! A check box for this should be added inside the "System\Preferences\Remote Desktop" window. Something like "[ ] Only &#8220;root&#8221; can access this window".
**3.** Unfortunately the program "tsclient" does not support "compression" or "cryptography".
The former is needed because in cases of connecting to Remote destination (other than local LAN), the connection will "hijack" all your bandwith & will still NOT be enough... (i.e. even an Ethernet 100Mbps connection shows delays &#8211; don't attempt to play a DVD on your Client machine or you will experience crashes. :) ). 
The later is needed because in cases of connecting to Remote destination (other than local LAN), anybody can "hack" the video data stream & see what you are doing on your Remote machine... (i.e. the "peeping tom" story...).
**4.** Streaming "audio" is NOT yet supported. That would be an interesting feature too!
    A workaround would be to audio chat using "gaim" messenger &#8211; but that is NOT ready yet either!!! :)

Have fun!!! :guitar:

P.S.> I have NOT yet tested whether it is possible to connect a Windows PC & an Ubuntu PC &#8211; but I assume (hopefully) that this is possible too (by using the embedded "tsclient" on the Ubuntu side)!

---

### Post by bluenova on 2007-01-23
Hi there, thanks for your contribution. I just wanted to point out that people should not use this on a wide area network, i.e. the internet as it's not secure unless routed via an encrypted service such as SSH. There are also how-to's on the forum about using VNC via SSH. It's also very easy to brute force the password so having the "Ask you for confirmation" is really essential unless you are not on the internet and trust all the computers that can access your VNC service. I think this is why people do not promote VNC much around here.

1. There is a menu shortcut to 'tsclient', it can be found under 'Applications > Internet > Terminal Server Client'.

2. The service will only function while the user with VNC enabled is logged on, so having it setup on the root account wouldn't work as Ubuntu locks down the root account.

VNC between Windows and Ubuntu is possible both ways, or with MacOS and a couple of other systems, as shown here:
[http://www.realvnc.com/what.html](http://www.realvnc.com/what.html)

---

### Post by dtgolder on 2007-02-04
Any idea how to exit full screen mode in tsclient?

Found it myself - CTRL-ALT-ENTER

---

### Post by venik212 on 2007-02-08
How do we do this in Kubuntu (under KDE)?

---

### Post by Aero9000 on 2007-04-16
Hi there,

For instructions on how to do this in KDE, see here: [http://www.howtogeek.com/howto/ubuntu/kubuntu/enable-remote-desktop-vnc-on-kubuntu/](http://www.howtogeek.com/howto/ubuntu/kubuntu/enable-remote-desktop-vnc-on-kubuntu/)

Cheers.

---

### Post by bangor on 2007-05-03
I have a follow-up question on using tsclient. Where does one specify the display number?
Appending the display to the hostname (e.g. 192.168.1.xxx:1) doesn't seem to work.
I'm running ubuntu 7.04 and tsclient 0.148. 
Thanks in advance.

---

### Post by arijarot on 2007-06-01
> **bluenova said:**
> Hi there, thanks for your contribution. I just wanted to point out that people should not use this on a wide area network, i.e. the internet as it's not secure unless routed via an encrypted service such as SSH. There are also how-to's on the forum about using VNC via SSH. It's also very easy to brute force the password so having the "Ask you for confirmation" is really essential unless you are not on the internet and trust all the computers that can access your VNC service. I think this is why people do not promote VNC much around here.

1. There is a menu shortcut to 'tsclient', it can be found under 'Applications > Internet > Terminal Server Client'.

2. The service will only function while the user with VNC enabled is logged on, so having it setup on the root account wouldn't work as Ubuntu locks down the root account.

VNC between Windows and Ubuntu is possible both ways, or with MacOS and a couple of other systems, as shown here:
[http://www.realvnc.com/what.html](http://www.realvnc.com/what.html)

Is there a secure way (e.g., a different app) to setup a remote desktop connection (i.e., feisty to feisty) like the VNCviewer? And a way that doesn't need to have the remote desktop authorize ("ask you for confirmation") like the tsclient does, but just the use of a password is required?

---

### Post by dbott67 on 2007-06-01
I use NoMachine for secure, remote desktop.  Here's a thread describing VNC over SSH, as well as NoMachine.  Post #2:

[http://ubuntuforums.org/showthread.php?t=437562](http://ubuntuforums.org/showthread.php?t=437562)

-Dave

---

### Post by arijarot on 2007-06-01
> **dbott67 said:**
> I use NoMachine for secure, remote desktop.  Here's a thread describing VNC over SSH, as well as NoMachine.  Post #2:

[http://ubuntuforums.org/showthread.php?t=437562](http://ubuntuforums.org/showthread.php?t=437562)

-Dave


Thanks, Dave, again;)

---

### Post by unclesamslair on 2007-11-10
I like this. How come remote desktops and assistance on Ubuntu can't be this simple, or even simpler?

Why can't there be a "Hey, I'm going to send you this file, when you open it it'll let me take control of your computer" approach

I'm a tech geek and all this port forwarding SSH bullcrap just has me sick

I live in Orlando and my sister lives in Gainesville. I have a laptop using a wireless router and so does she. Every now and then she needs a little help.

I want something where the only things me and her have to worry about is some sort of password confirmation thing to both allow me access to her machine and notify her of my entry. NO ip adresses, no clientnames, no terminal, no ssh, or vnc or pd whatever, no port forwarding, no BS.:mad: This is why I got Ubuntu, user-friendliness. Whenever I did remote assistance from my Windows machine I never had to worry about any of this.

I'm sorry for ranting but this has been a frustrating 6 hours. I still can't figure out what I need to do, and I won't try to for fear of ******* up my machine. Other than that, Ubuntu has done a very good job with what little it has. Thanks for listening and good bye.

---

### Post by gigaferz on 2007-11-20
to unclesam
 
dont worry, just keep trying, guess what???

this simplest way to remote control computers doesnt work for me...and the computers are next to each other.... and im barely beggining (again) ,they dont even see each other in "network" and i have 3....

the mistake i made (well maybe not) is to set up ubuntu computers and they are ~40 miles away from me...so ughh!!!

(ohh ive'been trying...)

i remember in xp with a hotmail account i was helping my friends...(i know not so fast and not secure) but really easy....

if dont do it in the next couple of days ill try like next month or somehting... and start all over again....   

hopefully the next lts version will be better in this networking area....(i mean user friendly)

---

### Post by myharshdesigner on 2007-11-21
Nice tutorial :)

Thanks

---

