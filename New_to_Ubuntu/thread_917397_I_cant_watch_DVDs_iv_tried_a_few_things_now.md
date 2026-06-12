---
title: "I cant watch DVDs iv tried a few things now"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Kedster on 2008-09-11
i tried this and another guide that i cant find
> First, install the following library:

sudo apt-get install ubuntu-restricted-extras

This will install most of the codecs for multimedia (audio and video) playing.

Next, you have to install libdvdcss2 to watch encrypted DVD. The library package is not available in the Ubuntu repository, you have to use the libdvdread3 installer script.

sudo /usr/share/doc/libdvdread3/install-css.sh

This will retrieve and install the libdvdcss2. If it don’t work, download the deb installer at [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb) and click to install it.

Install the xine library

sudo apt-get install libxine1-ffmpeg

Install VLC

sudo apt-get install vlc

Now you should be to watch DVD in your VLC player. and i still cant watch DVDs all it does is sit there and do nothing

---

### Post by SuperSonic4 on 2008-09-11
what does ```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
``` do? The above code works for me

(source: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683))

If this still doesn't work (or you'd rather try this first) type ```
sudo apt-get install regionset
``` and then ```
sudo regionset
``` and press the number corresponding to the region of the DVD you want to watch

---

### Post by Ntweat on 2008-09-11
if everything fails try repo of medbuntu


full manual here

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Kedster on 2008-09-11
```
kedster@kedster-laptop:~$ sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manually installed.
libdvdnav4 is already the newest version.
libdvdnav4 set to manually installed.
vlc is already the newest version.
Suggested packages:
  regionset
The following packages will be upgraded:
  libdvdcss2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.3kB of archives.
After this operation, 36.9kB of additional disk space will be used.
Get:1 http://packages.medibuntu.org hardy/free libdvdcss2 1.2.9-2medibuntu4 [36.3kB]
Fetched 36.3kB in 0s (36.7kB/s)    
(Reading database ... 209156 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using .../libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kedster@kedster-laptop:~$ 

```

---

### Post by crjackson on 2008-09-11
If you are running 32-bit Hardy paste this into a terminal screen.  It always works for me:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

for 64-bit hardy paste this:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w64codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

### Post by SuperSonic4 on 2008-09-11
> **Kedster said:**
> ```
kedster@kedster-laptop:~$ sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manually installed.
libdvdnav4 is already the newest version.
libdvdnav4 set to manually installed.
vlc is already the newest version.
Suggested packages:
  regionset
The following packages will be upgraded:
  libdvdcss2
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.3kB of archives.
After this operation, 36.9kB of additional disk space will be used.
Get:1 http://packages.medibuntu.org hardy/free libdvdcss2 1.2.9-2medibuntu4 [36.3kB]
Fetched 36.3kB in 0s (36.7kB/s)    
(Reading database ... 209156 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using .../libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kedster@kedster-laptop:~$ 

```

Yeah I guessed that was the case, did you have no luck with DVDs after that? If not I'd do what the poster above me suggested

---

### Post by Kedster on 2008-09-11
hey crjakson do i need to restart after this 
> edster@kedster-laptop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
--21:07:57--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

21:07:58 (13.47 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

OK
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_CA                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_CA                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_CA               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_CA               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_CA             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_CA         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_CA                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_CA                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_CA            
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_CA        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_CA      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_CA      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_CA                 
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_CA   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Fetched 3B in 5s (1B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
w32codecs is already the newest version.
totem-mozilla is already the newest version.
libdvdcss2 is already the newest version.
libdvdnav4 is already the newest version.
totem-xine is already the newest version.
libdmx1 is already the newest version.
libxine1 is already the newest version.
libxine1 set to manually installed.
libxine1-ffmpeg is already the newest version.
libxinerama1 is already the newest version.
libdvdread3 is already the newest version.
The following extra packages will be installed:
  libmozjs0d
Suggested packages:
  gxineplugin realplayer
The following NEW packages will be installed:
  gxine libmozjs0d non-free-codecs xine-ui
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2381kB of archives.
After this operation, 5812kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmozjs0d 1.8.1.13+nobinonly-0ubuntu1 [368kB]
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free non-free-codecs 1.1 [1900B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe gxine 0.5.901-1ubuntu2 [510kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xine-ui 0.99.5+cvs20070914-2 [1501kB]
Fetched 2381kB in 31s (75.2kB/s)                                               
Selecting previously deselected package libmozjs0d.
(Reading database ... 209156 files and directories currently installed.)
Unpacking libmozjs0d (from .../libmozjs0d_1.8.1.13+nobinonly-0ubuntu1_i386.deb) ...
Selecting previously deselected package gxine.
Unpacking gxine (from .../gxine_0.5.901-1ubuntu2_i386.deb) ...
Selecting previously deselected package xine-ui.
Unpacking xine-ui (from .../xine-ui_0.99.5+cvs20070914-2_i386.deb) ...
Selecting previously deselected package non-free-codecs.
Unpacking non-free-codecs (from .../non-free-codecs_1.1_i386.deb) ...
Setting up libmozjs0d (1.8.1.13+nobinonly-0ubuntu1) ...

Setting up gxine (0.5.901-1ubuntu2) ...

Setting up xine-ui (0.99.5+cvs20070914-2) ...

Setting up non-free-codecs (1.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


---

### Post by crjackson on 2008-09-11
Usually not, but it wouldn't hurt anything.  When in doubt, whip it out...

---

### Post by Kedster on 2008-09-11
so can i just put a dvd in or what 

i tried it in xine (opened it ans when FILE>DVD) 
and (FILE>OPEN and then /media/cdrom0/VIDEO_TS/ ans i tried a few files

---

### Post by crjackson on 2008-09-11
> **Kedster said:**
> so can i just put a dvd in or what 

i tried it in xine (opened it ans when FILE>DVD) 
and (FILE>OPEN and then /media/cdrom0/VIDEO_TS/ ans i tried a few files

You should now try totem xine or VLC if you have it installed.  Then put in th move and tell it to play disc.

As for DVD files, you want the VOB (Video Object Files), but if you want to watch the movie I wouldn't be hopping from VOB to VOB.  You need to Play Disc.  I'm not in front of my system right now, I'm at work.  I'll check back in the morning and if you are still having issues I'll work on it for you.  I generally install MPlayer for most of my DVD needs.

Also, make sure you are using a KNOWN good DVD Pressed movie.  That's the first barrier

---

### Post by nelamvr6 on 2008-09-11
Another thing you could try in switching to Linux Mint.

All of the multimedia codecs are installed and working upon installation.

Just saying...

---

### Post by Kedster on 2008-09-11
ok umm ill try to do that and iv thought about mint but i neverunderstood what its for, is it built upon ubuntu or what and right now im trying to watch "spider-man 2" acctually

---

### Post by nelamvr6 on 2008-09-11
> **Kedster said:**
> ok umm ill try to do that and iv thought about mint but i neverunderstood what its for, is it built upon ubuntu or what and right now im trying to watch "spider-man 2" acctually

Like Ubuntu, it is Debian based, it shares the Ubuntu repositories, but it's not exactly a branch of Ubuntu...

It's kinda hard to describe, but it's really easy to enjoy!
If you like Ubuntu you'll LOVE Mint!

---

### Post by Kedster on 2008-09-11
Does mint use all the same eye candy(themes compiz fusion fonts icons emerald) does it use Gnome or kde or maybe xface does it use firefox as default 

and can i duel boot it with ubuntu and use my Home for both

---

### Post by cdaringe on 2008-09-11
open vlc
file --> open disc
"ok"

---

### Post by Kedster on 2008-09-11
vlc looks like it trys but no picture comes upp and then it "stops"

---

### Post by Tatty on 2008-09-11
Try running VLC from a terminal to see if it outputs an error message when you try to load a disc.

---

### Post by Kedster on 2008-09-11
I did that and this iws what i got
> kedster@kedster-laptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 311B7B6A
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kedster/.dvdnav/DVD_VIDEO.map'
libdvdnav: vm: ifoRead_VTS_ATRT failed

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: vm: ifoRead_VOBU_ADMAP vgmi failed
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000200)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000017a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x000017a0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00012a90
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00012a90)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002df400
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x002df400)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002df420
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002df420)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002e06e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x002e06e0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002e0700
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x002e0700)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003070a0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x003070a0)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003070c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x003070c0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00318f40
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x00318f40)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00318f60
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x00318f60)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0033bf40
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x0033bf40)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0033bf60
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x0033bf60)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00340840
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x00340840)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00340860
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x00340860)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0034c5e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x0034c5e0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0034c600
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x0034c600)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0035b1c0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x0035b1c0)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0035b1e0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x0035b1e0)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00364de0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_0.VOB (0x00364de0)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x00364e00
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x00364e00)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00371240
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_0.VOB (0x00371240)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00371260
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x00371260)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0037db60
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_0.VOB (0x0037db60)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0037db80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_1.VOB (0x0037db80)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x00384700
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_0.VOB (0x00384700)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00384720
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x00384720)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x00392620
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_14_0.VOB (0x00392620)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x00392640
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_14_1.VOB (0x00392640)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x00394e80
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_15_0.VOB (0x00394e80)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x00394ea0
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_15_1.VOB (0x00394ea0)!!
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 3
[00000283] main playlist: nothing to play


---

### Post by Tatty on 2008-09-12
Did you follow SuperSonic4's advice on "regionset" on the last page?

The output from VLC looks like the same I was getting once when i had not set the region properly.

---

### Post by Kedster on 2008-09-12
ok so i live in canada and it the movie spiderman 2 so what region do i set it to

---

### Post by Tatty on 2008-09-12
According to Wikipedia, you should set it to region 1:

[http://en.wikipedia.org/wiki/Dvd_region](http://en.wikipedia.org/wiki/Dvd_region)

---

### Post by mike1234 on 2008-09-12
Try this. Assuming the DVD itself is okay. I have a box set that require w32codecs even with VLC properly installed. Don't ask me, ask Warner Bros. Just a suggestion I haven't seen posted yet.

1. Add the Medibuntu repository address to /etc/apt/sources.list
Edit as root the /etc/apt/sources.list file (e.g. sudo nano /etc/apt/sources.list or kdesu kate /etc/apt/sources.list) and add the following two lines:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

2. Update the packages list
Issue the following command:

sudo apt-get update

3. Install the w32codecs and libdvdcss2 packages
To install those two packages, just type in the command:

sudo apt-get install w32codecs libdvdcss2

It should be done now. The codecs will be installed in /usr/lib/codecs/ and the DVD library in /usr/lib/libdvdcss2.so.2.0.8.

M.

---

### Post by nelamvr6 on 2008-09-12
> **Kedster said:**
> Does mint use all the same eye candy(themes compiz fusion fonts icons emerald) does it use Gnome or kde or maybe xface does it use firefox as default 

and can i duel boot it with ubuntu and use my Home for both

Mint Main Elyssa uses Gnome, Mint Elyssa KDE is in development, Mint Elyssa Xfce CE is stable (what I use) and ALL eye candy is available in Main and Xfce editions, Compiz, Emerald, the newest sphere deformations, the whole shebang.

---

### Post by Tuning_In on 2008-09-12
Hi.

If you're still unable to play dvd's follow [URL="https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"]this guide
[/URL]. This is how it worked out for me:)

Hope it helps!

---

### Post by crjackson on 2008-09-12
> **mike1234 said:**
> Try this. Assuming the DVD itself is okay. I have a box set that require w32codecs even with VLC properly installed. Don't ask me, ask Warner Bros. Just a suggestion I haven't seen posted yet.

1. Add the Medibuntu repository address to /etc/apt/sources.list
Edit as root the /etc/apt/sources.list file (e.g. sudo nano /etc/apt/sources.list or kdesu kate /etc/apt/sources.list) and add the following two lines:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

2. Update the packages list
Issue the following command:

sudo apt-get update

3. Install the w32codecs and libdvdcss2 packages
To install those two packages, just type in the command:

sudo apt-get install w32codecs libdvdcss2

It should be done now. The codecs will be installed in /usr/lib/codecs/ and the DVD library in /usr/lib/libdvdcss2.so.2.0.8.

M.

Skim back a few posts and you'll see I already had him install those packages.  He needs to try a different DVD and see if he has the same problem.

I actually have a few movies myself that won't play in Linux due to css keys.  He may have one of few that aren't yet supported.

---

### Post by mike1234 on 2008-09-12
> **crjackson said:**
> Skim back a few posts and you'll see I already had him install those packages.  He needs to try a different DVD and see if he has the same problem.

I actually have a few movies myself that won't play in Linux due to css keys.  He may have one of few that aren't yet supported.


 Yea, sorry. I just kinda skimmed through quickly. All I can figure is it's one of those weird DVD's like mine ( A Warner Bros. Looney Tunes box set) that doesn't play without w32codecs. Or his DVD is a bum disk.

M.

---

