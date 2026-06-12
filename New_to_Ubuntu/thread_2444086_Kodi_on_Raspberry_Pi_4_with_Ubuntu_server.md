---
title: "Kodi on Raspberry Pi 4 with Ubuntu server"
date: 2020-05-24
forum: New to Ubuntu
---

### Post by franciscorc on 2020-05-24
Hi,

I´m trying to install Kodi on a Pi4 with Ubuntu server with no GUI, straight to Kodi.
I´m following a guide I found  [here ]("https://forum.odroid.com/viewtopic.php?t=22386")to boot straight to Kodi that i found [https://forum.odroid.com/viewtopic.php?t=22386](https://forum.odroid.com/viewtopic.php?t=22386), and everything works OK, except that when I enter Kodi, the interface as well as the videos I play are lagging.
 When I look at htop, I find that all 4 cores are at 100%.
I tried to install Libreelec to check if it was a harware limitation, but when using Libreelec CPU is around 10% and only in 1 CPU. I think this is due to the fact that the GPU is not used.
I only install the below, and as I said everything but looking at htop have a lot of processes of kodi-standalone running occuping all 4 cores at 100%.

[COLOR=#2E8B57][FONT=Monaco]sudo apt-get install xserver-xorg-legacy Kodi xinit[/FONT][/COLOR]

I´m trying to learn linux, and searched quite a bit, but I seeing terms like "mesa drivers", "X11", "Xorg" and I´m a bit lost.

Can you please help me or point me to the right direction.

Many thanks
FranciscoRC

---

### Post by TheFu on 2020-05-24
wikipedia for most terms you don't know.
Web search terms not in wikipedia, just add "linux" to the search.

You probably don't want X11 on a r-pi to be used for media playback.
For someone new, best to use a r-pi specific distro for media use for historical reasons from the XBMC days.  i use OSMC.

---

### Post by franciscorc on 2020-05-25
I´ve tried Libreelc and it works very good, so I´m trying to achieve the same results with Ubuntu (... if possible). The "challenge" was to install it on Ubuntu Server. Plan to install other software later (Openhab + Mosquitto).


I think that you share my opinion, that google is full of information, and for a area which is new to you, sometimes its difficult to sort a good source from a opinion or someone who got a lucky shot.
As I said my problems is that the new terms are pilling up. Been trying to get there googling it, but I´m having trouble sorting the information.
I´m not expecting for anyone to show me the highway (it would be nice ;)) , but if someone could point me to a less bumpy and curvy road it would be nice. I expect it have an educational side.


Either way, thank you for reading and your contribution


Francisco

---

### Post by TheFu on 2020-05-25
There is a very steep learning curve when you jump into something like multi-media on a non-standard device like r-pi.

You are going to find that raspberry-pi software assumes it is a 1-purpose device. To change what a device does, most people just swap the microSD card and reboot.  That's because there are specific distros pre-configured AND optimized for the rPi devices to accomplish that 1 thing. Each thing has optimizations that break what the other major software needs.

I wrote:
> historical reasons from the XBMC days
By any chance did you look up how XBMC was designed and the funky things about it?  It was designed to work on an XBOX which is a single-purpose machine and required constant video updates. Those updates are extremely taxing to the CPU. Last time I looked, the same method was being used on Kodi because Kodi is a single-purpose software for most machines where it gets installed.  "kodi using 100% cpu" would be a good search term.  BTW, 100% CPU means 1 core is running hard. The other 3 aren't.

Also, you installed "server", but intend to run the system with a GUI?  That's just a mistake.  Servers don't have GUIs. They don't have Wayland or X11.  You get a text interface, a console, only.  Most of the time, you'd setup ssh and use a normal desktop/workstation to ssh into the "server" for management from terminals. There ain't no GUI.  If you don't have any Unix background, that is usually too hard for someone.

I'd recommend that you buy a 4-pak of 8GB microSD cards. Use each one for 1 purpose.  Elec or OSMC for Kodi.  The others for different things.  When you break things - and you will - the teams that answer questions about any specific project routinely say they only help with their software and don't recommend adding anything else.  I've seen people attempting to run a VPN on a Kodi machine, screw things up and have to reinstall the Kodi stuff (dd the microSD card completely fresh) again.  On rPi hardware, certain tools are swapped out from normal Ubuntu or Debian. For example, the network management is often conman, not network-manager, on rPi distros.  That's easier because effectively rPi hardware comes in only 3-4 versions, so there's no need to support 200 different NICs as with a normal Linux distro.

A rpi is a good way to learn ... about non-PC hardware and some funky things related to that.  If you want to learn about Linux as you'll see it in the real world most of the time, then running it in a virtual machine is the safest, easiest way.  rPi's don't have a BIOS, PCs do.  That's a pretty big difference.  Running inside a VM removes most hardware incompatibilities that can happen when Linux is directly installed on physical PC systems.

You can load an Ubuntu-Mate desktop on a rPi v4. I hear people do that and are happy.  There are also multiple-boot setups that have Kodi, Plex, Mame, and a few other rPi specific OSes on a single system.  Those can be useful.  Most of the time, I find I need to fix the partitioning with all setup.

Linux is all about flexibility.  People use it millions of different ways, so finding someone who did it exactly for the reason you are doing it might be possible.  These forums aren't anti-Pi, but the Pi hardware is pretty specific, so help for it usually comes from other forums, especially when it comes to GPU and wifi-networking stuff.

Were I you, I'd load Ubuntu-Mate on the machine, then load Kodi and see how that goes.  I don't have a v4 rPi. Just have a v2 and v3. These are mainly OSMC devices, but I have put other specialized distros onto a spare SD and booted.  They are all Linux, but a little odd. Kinda how Android is Linux, but a little odd.

Thinking way back to when I first started with Linux, I recall that I didn't actually like the OS much for the few 2-3 years. But I was a little odd, in that I'd already been using 10+ OSes for my day job at the time from TSO/ISPF, to OS/2, to MS-DOS, to Win3.x, to MacOS, to about 7 different commercial Unixen (Irix, HP-UX, AIX, SunOS, Solaris, OSF/1, and a few others).  The workstations on my desks had DEC-Ultrix and DEC-OSF/1 running X11/Motif for the GUI.  X11 on Linux on my home PC was pretty amazing - after all, we usually needed $20K workstations to run stuff like that, not a $1000 PC.  Just the fact that a r-Pi v4 is probably faster than my monster PC from back (8MB of RAM) then is pretty amazing.

Wish I knew how to pass on 25 yrs of experience in 2 yrs. I don't. Sorry.

---

### Post by CelticWarrior on 2020-05-25
Also of note is the fact that special purpose distros like OpenELEC do include proper drivers and lots of optimizations for the embedded graphics. They have to because their purpose is to play several different types of media.
A server edition has nothing of that, obviously. Although it should be possible to start with a server (or minimal) edition and then add everything else it needs to work as a useful media player, you would need to know as much as and have the same access to ARM drivers source code as the people publishing those distros. Do you? I know I don't and I haven't.

---

### Post by franciscorc on 2020-05-26
Guys, thank you for your posts.
 
Regarding CPU its actually at ~380%. It´s 4 cores are at around 95% each.


You are 100% right, for stability sake I should use Pi/system for its particular purpose. I´m a windows guy (sorry for the blasphemy), and was trying to use this case for educational purposes.
I´ve installed linux 1000 times in the past 20 years, but after install I always ask myself "Now what?" and then put it aside. To me personally if I don´t have an objective I always tend to abandon things.
But all of you helped a lot in sorting some ideas. You see, the bad thing about google is that sometimes gives me a buffer overflow, and other times its difficult to understand if the guy writing the article does know a thing about the area or just had dumb luck.


Will order a 2nd unit so my wife doesn´t spank me, and given the average life expectancy in Portugal I calculate I have around 40 years to make it work. 


Again thanks all.

---

### Post by TheFu on 2020-05-26
But you don't need another pi, just another micoSD card.

What do you do on Windows?  Do those things on Linux.  The only things i still use Windows to accomplish are:
[LIST]
[*]video editing
[*]personal finance
[*]stock market stuff/analysis
[/LIST]

Everything else and stuff that Windows never did or did poorly are on linux.  The list is endless.
[LIST]
[*]Pi-Hole - if you are tired of ads and tracking
[*]DNS/DHCP - if you want to better manage your LAN
[*]NTP - if you want all systems to have accurate time (Windows can't keep time and MSFT doesn't think it is a bug)
[*]Print server
[*]Storage server
[*]Web server
[*]Nextcloud server / Owncloud / Seafile
[*]Media Center server (players are different)
[*]email server and email gateway
[*]web proxy/filter server
[*]VPN server
[*]Remote desktop server
[*]Identity server
[*]OAuth Server
[*]VM host w/ failover cluster
[*]Network Backup server
[/LIST]

Just a few ideas.  Most of those are easy for a rPi v4 to handle.  Just not the backup/storage stuff.  rPi have terrible disk i/o.

You can run Linux containers on a rPi, so putting each service into a separate container would be smart.

---

