---
title: "New to Ubuntu. Very laggy running off USB"
date: 2015-04-19
forum: New to Ubuntu
---

### Post by Nick_Francis on 2015-04-19
Hi
I have just installed Ubuntu onto a 8GB memory stick. I used a liveCD, booted it on a Windows laptop and used the "Something Else" install option to install it on to the memory stick.

I have now plugged that memory stick into the machine I want to use Ubuntu on (a [Novatech Foxconn D2500 ITX Atom]("http://www.novatech.co.uk/products/barebones/r30-i4000.html"))

On boot everything seems to be functioning fine, but, the UI is exceptionally laggy. Clicking on a window, typing anything into Terminal, minimizing etc. all of this take ages and the fade in & out is very slow & clunky. The system is shutting down fine and seems to be booting up at a reasonable speed but I'm wondering if there's something I've done wrong, or need to change, to improve what I've got?


Any suggestions would be gratefully received - the system looks great, just still getting my head round it!

Thanks

Nick

P.S. - don't know if it's normal or not but install from LiveCD to the USB took about 2 hours.

---

### Post by TheFu on 2015-04-19
If you care about performance, don't use USB with a heavy GUI/OS.  Even USB3 performance doesn't work too well - this is due to USB having queuing issues when there are too many concurrent requests like an OS has.  At least that has been my experience.  USB storage is fine for 1-2 concurrent tasks, streaming media, backups - that sort of thing.

A small Linux distro can work fast off USB, but only if the entire OS gets loaded into RAM. Then it will be so fast that you'll be shocked. TinyCore and TinyCorePlus are useful for this.

Update: "heavy GUI" is code for Gnome3 or Unity.  Use LXDE or XFCE instead.

---

### Post by Geoffrey_Arndt on 2015-04-19
In a nutshell . . TheFu is right

Xubuntu 14.04 with persistence on a Live USBv3 will run pretty fast (almost HDD speed, but considerably less than SSD speed).   But, I'm not running an atom cpu (am running a 5th gen I7 with 16 GB dd3 ram).   

Still, if you want the best experience for Ubuntu, run a real install (on SSD or HDD) AND if possible, use a fairly decent processor.   Lastly, using Intel graphic is easy/smooth, running Nvidia or AMD mostly requires the install of proprietary drivers from the Software/Updates program (for Ubuntu Unity)

---

### Post by mastablasta on 2015-04-20
it oculd be the intel's ATOM GPU is not well supported. certian versions were actually outsourced by Intel and there are not good Linux drivers for it as a result. and Ubuntu needs good GPU support as it uses hardware acceleration.

and yup - yours has issues:

[http://askubuntu.com/questions/168253/installation-problem-with-atom-d2500-cedarview](http://askubuntu.com/questions/168253/installation-problem-with-atom-d2500-cedarview)

> This Chipset are NOT actually functional with Unity 3D, and make some problem (in some case) during the installation.

another one here: [https://gist.github.com/Aissen/2925633](https://gist.github.com/Aissen/2925633)

i would say go with Xubutnu use software acceleration. i hope you didn't plan on doing anything serious on the ITX. if you did then you will be better off using Windows on it.

---

### Post by Nick_Francis on 2015-04-20
I was planning on using it as a headless media server running something like Media Tomb or similar dlna. Have spent the last month trying to get Nas4Free to work but kept hitting walls so thought I'd try something different. Turns out this Atom GPU isn't good for a lot (very thankful I didn't buy it for myself!) Will look at Xubuntu.

Now wondering if I'd be better off getting something like a raspberry pi and just networking in my hard drives...

Or would I be better off running Ubuntu server?

---

### Post by TheFu on 2015-04-20
IMHO ... 

Plex Media Server on a headless box is probably the easiest DLNA server around - provided you are willing to avoid transcoding due to the CPU limitations you have and have a clean directory structure for media. Plex demands - DEMANDS - a specific structure similar to XMBC/Kodi for media TV/, Movies/, Music/.  For years, I used samba as a streaming server - all my clients supported CIFS mounts. Ran XMBC with CIFS access to the media for a few years before switching to Plex (as more clients were added to my network).  Wish I'd have gone with PlexMS years earlier.  No need for a Plex paid account - I don't even have a free login on the plex site.

The issue with DLNA servers for most people is the complete lack of security. If there is media and Plex sees it, it is made available to any - ANY - DLNA client allowed on the same network. For me, that meant adding a guest wifi network, which everyone should have anyway, that is completely separate from the "parents network."  Don't want the visiting kids or other relatives accidentally seeing the "romance" content.

With the CPU you have, no GUI would be smart, but if your skills aren't ready for that, installing a very lite GUI might be worth it - or just run a remote X-session when on the LAN (no video/audio streaming over X11).

So - it really comes down to what equipment you have, what clients need to connect, which media formats each client supports, and what you'd like to share.

Until last month, my Plex server was running on an AMD E350 (about the same perf as your Atom D2500). It was serving video, music, audiobooks, photos (about 40K) and I added a Calibre ebook server for the network.  If course everything is backed up (big time) to disks on other machines on the network. The amount of time put into this media and the servers costs way more than a $200 4TB HDD needed for backups.  My E350 also ran Kodi/XBMC with the PlexBMC plugin to connect to the local Plex Server.  The AMD APU has a nice Radeon GPU built-in, unlike your D2550, so playback of h.264/ac3/aac hidef content is next to zero CPU.  On your CPU, any video playback over about 600p resolution will stutter and have other issues.  With your CPU, definitely avoid transcoding too. The Plex settings to control transcodes are unclear - dumbed down too much, IMHO - so it is impossible to really control when/if transcoding happens or not.  I ended up completely disabling transcoding and putting up with playback errors for chromecast and roku devices if the content had unsupported video or audio codecs.  AC3 isn't supported by those devices - most TV recordings arrive with AC3 audio. Idiots (not sure who I should blame, but someone is an idiot). ;)

In the end, I spent $126 to get a new CPU+MB that can transcode easily and moved the disks into the new box (everything for this build was from parts I had laying around).  The G3258 CPU has plenty of power to transcode 1080p content - actually it can do multiple streams concurrently.  My AMD E350 is now the edge router for the network here blowing away what a $200 commercial router can do thanks to pfSense.  The case for the E350 is one of those small "media center" cases and only holds 1 drive. That makes it bad as a NAS plus it only has 4 SATA ports.  The G3258 cases has room for 7 HDDs, but the MB only has 6 SATA ports. ;(  ... 6 x 4TB ... that should be plenty (only have 4tb and 2tb disks today), but I'm planning ahead.  Plus 150G for the OS and Plex metadata files ... 

You can use the same D2550 machine as an NFS and/or CIFS server if you like. It has plenty of power for that too - just know that when large files are transfered (like backups) the GUI will definitely slow down - if you have a GUI.  It won't matter for streaming playback at all.

FreeNAS (or any of those) want to use ZFS and ZFS loves RAM - 8G min. I have friends with 32G of RAM in their ZFS NAS boxes to get the performance similar to enterprises.  They are deep in the IT architecture world (I was before retirement), so having hands on knowledge is part of their ongoing re-training efforts. They run openstack across 5+ physical machines with about 40 VMs ... just for learning.

Of course, there are details about your situation we don't know, so a different answer might be better.

---

### Post by Nick_Francis on 2015-04-20
Wow, that's quite an answer - thank you! Will read it through several times to digest fully. My first initial response, and one of the reasons I abandoned trying Plex on N4F is I have been led to believe Plex is 64-bit only, yet my (now realising more & more) slightly underpowered box is only 32 bit. Unless of course I find some sort of legacy install and avoid any updates to it.

Am I right in thinking the best way to do this (if I did want to head down the Plex route) would be to install Ubuntu server instead of what I currently have?

---

### Post by mastablasta on 2015-04-21
you can use Atom as pure healdess server and then add an RPi for viewing the content (is that called streaming?!). so you would save files on your Atom server and then see them via Rpi and Kodi (or Openelec).

if had an older different Atom then GPU support would be good, but for these there is an issue since osoene else prepared architecture and i think also Windows drivers for Intel.

another option owuld be Windows server + Kodi.

Ubuntu server definitelly uses a lot less ram fromt he starting install than any desktop out there. also the CPU usage is usually quite low. i mean consider this that i can easilly run it in virtualbox in Windows XP on a single core CPU and i usually give it 256MB ram only. which is plenty for some basic LAMP server things. i then use this for testing the websites, applicaitons etc. 

it all works even better on new multicore CPU but you get the point.

if you plan a headless server there is no need for desktop anyway.

---

### Post by Nick_Francis on 2015-04-21
Thanks for that. Spoke to my dad last night and it turns out that whilst I've been investigating this he's gone off and bought me a raspberry pi, so, problem solved. Atom to become headless server & Rpi for Kodi.

Thank you for all the help and advice guys - really appreciated.

---

### Post by user_of_gnomes on 2015-04-21
I have good results running Ubuntu on USB sticks, use it very often. It sounds like your videochip isn't supported properly.

---

### Post by TheFu on 2015-04-21
You'll probably need transcoding to do video on a RaspberryPi.  If you are going that direction, there are cheap streaming playback devices like a chromecast, amazon fire-stick, roku stick, etc. WD makes some things that playback many more kinds of content too.  I'd avoid the chromecast - no remote provided and the android control apps are buggy.  I have a full-sized roku ($80) - don't use it much. Prefer Kodi on a real PC that can handle **any** codec/content I have.  This small devices can't playback AVI files with xvid codecs.  They only handle h.264/aac - and nothing else.

You will learn.

R-Pis are good at so many different things, it would suck to dedicate it just to playback of videos.

---

### Post by mastablasta on 2015-04-21
i have an old Pi and works great as media center. maybe not as fast but it will do. so far it ran all i loaded on it.

remote issue is solved with CEC TV remote. as well as i got my self one of those chgeap chinese mini USB wireless keyboards.

Rpi can download torrents durign night for example. it can play you tube, vairous other online services and channels. anyway all i need...

---

