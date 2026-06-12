---
title: "Howto: UPnP AV server/client in Ubuntu Breezy/Dapper; Pls Test"
date: 2006-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by sreyan on 2006-04-24
**Universal Plug and Play AV Media Server/Client with Dapper Beta; Testers Wanted.**

In this tutorial is split into two parts. 

In the first part we will setup up a machine running Dapper Beta 1 as a UPnP AV Media Server; In the second part I will demonstrate how to correctly install djmount.

**Part 1**: Ubuntu with uShare. (This will work on Breezy too! no Fuse issues with the server)

First open a shell on the machine you want to have as your UPnP server. I will call it mediaserver from here out.
[LIST=1]
[*]We first make a backup of your sources.list file.
```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.`date +%F`
```

This will move your current sources.list file to the file sources.list.YYYY-MM-DD.
[*]We add the geexbox debian repository. If you are using ssh and don't have access to gedit use your favorite text editor. We also need to add the GeexBox GPG key to apt.
```
$ sudo gedit /etc/apt/sources.list
```
Add the following lines.
```
##GeexBox uShare UPnP media server
deb http://www.geexbox.org/debian/ unstable main
```
Next we add the GPG keys for geexbox. ```
$gpg --keyserver subkeys.pgp.net --recv B892931DA34867EF
$gpg --export --armor B892931DA34867EF | sudo apt-key add -
```
[*]We install uShare.
```
$sudo apt-get update && sudo apt-get install uShare
```
[*]Configuring uShare.

We add a multicast route. This will allow you to controll what machines get your UPnP multicast.
The format is  $sudo route add -net abc.def.geh.0 netmask 255.0.0.0 dev ethX

Where abc.def.geh is your network ip range and X is the ethernet device you with to use. I'm currently at the University of Connecticut (class b, 137.99) and my server is running on my second ethernet card so I might add do the following to add the multicast route.

```
$ sudo route add -net 137.99.0.0 netmask 255.255.0.0 dev eth1
```

Next change directory into the folder you want to share.

```
$ cd /home/username/share
```

Exporting is now just a simple command.
```
$sudo ushare -c ./ -i eth1
```
[/LIST]


uShare will now gather the meta data. Happy UPnP filesharing!

Please if you use this guide and run into errors or you think something could be explained better let me know! I want this to be quite usable and a suitable alternative to windows media connect UPnP AV server!

Part II will be done at a later date!

---

### Post by soze on 2006-05-29
I tried ushare with my OmniFi DMS1 and the DMS1 shows "ushare" as a meda source, but as soon as I select it, the DMS1 hangs.

Any thoughts?

---

### Post by GrammatonCleric on 2006-06-02
Everything installs without a hitch.  I'm using a buffalo linktheater to access the upnp share, the linktheater sees the share but it's flagged as "UNAUTHORIZED."  Any ideas  how to authorize?  When I select the share and try to open it the error message I recieve is that the "Server needs to auathorize cleint access."

Thanks,

---

### Post by rgreves on 2006-06-10
Im using the D-Link DSM-320.  I can play MP3's no problem, look at the kids photos without a hitch, and even play internet media (live365.com, etc.)

But when I try to play a movie off of the server (or tv show) it hangs when the bit-rate gets too high and appears to stall while it "catches-up".

I am assuming that I need to set my multi-cast differently. 

Current setting is: 

$ route add -net 192.168.0.0 netmask 255.255.0.0 dev eth0

Is my netmask too wide and mistakenly set for class B or is my route wrong?

I REALLY want to stick with my Ubuntu and ushare box and stop using MS as my media server. 

Any help would be appreciated.

---

### Post by grantjohnston on 2006-12-12
I'm having trouble getting this package installed.. I'm trying it on my AMD64 and my 32bit intel laptop.. On the desktop when I type
```
sudo apt-get update && sudo apt-get install uShare
```
I get
```
Failed to fetch http://www.geexbox.org/debian/dists/unstable/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
(obviously after it runs all the updates on the rest of the repos.


On the laptop when I type
```
sudo apt-get update && sudo apt-get install ushare
```

I get a problem about it not being able to uninstall gmediaserver (only does music, I need video, too).


If anyone has any thought on this, I'd greatly appreciate it.. I'm sorry for bringing up an old thread, but I've been searching for weeks on end for a program to work with my DSM-320. I found TwonkyVision, but I'm not wanting to pay to utilize the program. I've also tried mediatomb and flumotion, neither of which I could seem to get fully installed.



I'm freaking stumped


Anyone??


Thanks


grant

---

### Post by grantjohnston on 2006-12-12
bump... Anyone?

---

### Post by grantjohnston on 2006-12-15
ttt... Anyone?

---

### Post by grantjohnston on 2006-12-16
Help?

---

### Post by andyshack on 2006-12-17
Grant ive just pulled my dsm out of the cupboard yesterday to give it another chance. imo they're rather crap, mainly because of only wep encryption. 

I had it going last year although i eventually just plugged in a laptop instead. 

It was running happily though, using dlinks default software running on xp, which i had pointed to a network drive that was actually a debian box with samba holding all the media.

at the time i was unaware of any decent upnp software to stream directly from the media array itself.

I will be playing with it a bit over the next few days when i find the time and if i come up with some answers for you or an alternative solution i shall let you know.

---

### Post by grantjohnston on 2006-12-17
Awesome. Andy, I appreciate it.. I can understand on disliking the unit because of only WEP encryption. However, with my setup, it works perfectly. My TV sits right under it and all my boxes are in the living room. Plus, when I worked at CompUSA, it went discontinued through us, sat in the warehouse, then when it was time to send it back, I picked it up for 80 dollars, :D. I'm going to try and setup MythTV tonight, from reading another thread a subject close to this, it would be the software to use. I'll try and let  ya know on that if I like it or not.



Thanks again



Grant

---

### Post by SamChameleon on 2006-12-21
I am using Dapper Drake and tried to install the ushare server as described above. But I get an error message when trying 
```

apt-get install ushare

```

I get 

```

WARNUNG: Die folgenden Pakete können nicht authentifiziert werden!
  libupnp2 ushare
Diese Pakete ohne Überprüfung installieren [j/N]? j
Fehl http://www.geexbox.org unstable/main libupnp2 1.3.1-1ubuntu0.1
  404 Not Found
Fehl http://www.geexbox.org unstable/main ushare 0.9.7-0ubuntu1
  404 Not Found
Konnte http://www.geexbox.org/debian/./debian/pool/main/libupnp/libupnp2_1.3.1-1ubuntu0.1_i386.deb nicht holen  404 Not Found
Konnte http://www.geexbox.org/debian/./debian/pool/main/ushare/ushare_0.9.7-0ubuntu1_i386.deb nicht holen  404 Not Found
E: Konnte einige Archive nicht herunterladen, vielleicht »apt-get update« oder mit »--fix-missing« probieren?

```

I fear something is wrong with the .deb dependencies in Ubuntu Dapper Drake.
Has anybody any suggestions?

Chris

---

### Post by grantjohnston on 2006-12-26
From the nearest I can tell, my problem is that it doesn't have a 64 bit package, even, though , I try on my laptop, it still won't get the files.. Does this program have a problem with gmediaserver? That program IS having troubles uninstalling on both machines... I am truly stumped on this.. I tried using MythTV, and, even that was no help.. Am I going to have a build a windows machine just to get my media to my TV??? Anyone please help.

---

### Post by Tragos on 2006-12-27
> **grantjohnston said:**
> On the laptop when I type
```
sudo apt-get update && sudo apt-get install ushare
```

I get a problem about it not being able to uninstall gmediaserver (only does music, I need video, too).


Try to delete /etc/init.d/gmediaserver first. I noticed that there's something wrong with that script and apt-get stops when command "gmediaserver stop" fails during uninstallation.

-T

---

### Post by ntrusbak on 2006-12-29
I am using Ubuntu Server 6.06 LTS, and getting the following error message:

The following packages have unmet dependencies:
  ushare: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages

Hope someone can help me. 

br,
Niels.

---

### Post by rigreves on 2007-01-03
It's been awhile since I visited this thread...There is a new version of Ushare 0.9.8 and libupnp which is 1.4 (I believe). 

I had to update Ushare manually, but the libupnp came up in an update manager notification.

I am pleased to report that my system which consists of a Sempron 2800, 512MB, 250GB HD, plays everything like a champ now. 

Much, much faster response on the DSM-320 when paging through the file list,  and no and I mean zero buffering issues. I have removed all instances of the Dlink software from other machines (which keep the peace between the wife and I -- a la Bill McWindoze).

I do not have any advice for the AMD64 crowd as of yet as my first AMD64 machine arrives today! (And I'm stuck at work!)

---

### Post by rigreves on 2007-01-03
BTW - I just tried to install Ushare from Geexbox and didn't have any issues...Here are my steps:

Add the source list to your  /etc/apt/sources.list

sudo gedit /etc/apt/sources.list

Insert this line: deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main

Save and then update:

sudo apt-get update

sudo apt-get install ushare

You should see the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libupnp2
The following NEW packages will be installed:
  libupnp2 ushare
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 123kB of archives.
After unpacking 434kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libupnp2 ushare
Install these packages without verification [y/N]? y
Get:1 [http://www.geexbox.org](http://www.geexbox.org) unstable/main libupnp2 1.4.1-1ubuntu0.1 [85.4kB]
Get:2 [http://www.geexbox.org](http://www.geexbox.org) unstable/main ushare 0.9.8-0ubuntu1 [37.3kB]
Fetched 123kB in 1s (72.1kB/s)   
Preconfiguring packages ...
Selecting previously deselected package libupnp2.
(Reading database ... 106849 files and directories currently installed.)
Unpacking libupnp2 (from .../libupnp2_1.4.1-1ubuntu0.1_i386.deb) ...
Selecting previously deselected package ushare.
Unpacking ushare (from .../ushare_0.9.8-0ubuntu1_i386.deb) ...
Setting up libupnp2 (1.4.1-1ubuntu0.1) ...

Setting up ushare (0.9.8-0ubuntu1) ...
 * Starting uShare UPnP A/V Media Server: ushare                                 * No shares avalaible ...
                                                                         [ ok ]


(why it screws up the available spelling, I have no idea...)

Then following the manual at: [http://ushare.geexbox.org/](http://ushare.geexbox.org/) you should be ready and on your way! I was about to plunk down $40 for twonkyvision, when the updates happened over Christmas. This was my second day back at work and I was killing time during a Edgy desktop install for an IP based CCTV system I am working on...

Not sure if my steps helped, but it worked ok on my POS Presario 2171us laptop running Edgy.

I'll help any that I can - as Ushare is now one of my favorite things about my personal complete switch to Ubuntu from Windoze!

---

### Post by grantjohnston on 2007-01-04
> **Tragos said:**
> Try to delete /etc/init.d/gmediaserver first. I noticed that there's something wrong with that script and apt-get stops when command "gmediaserver stop" fails during uninstallation.

-T

I try that and I get



```
The following packages will be REMOVED:
  gmediaserver
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 311kB disk space will be freed.
Do you want to continue [Y/n]? Y 
(Reading database ... 96565 files and directories currently installed.)
Removing gmediaserver ...
Stopping gmediaserver: invoke-rc.d: initscript gmediaserver, action "stop" failed.
dpkg: error processing gmediaserver (--remove):
 subprocess pre-removal script returned error exit status 1
Starting gmediaserver: Errors were encountered while processing:
 gmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
grant@threeve:~$ 

```


Every time I try and remove it, it fails. I tried starting it to see if it will stop it in the process of uninstalling it and remove it... Even stopped it won't uninstall... I hate this thing, I just want it off my machine, haha... Right now I'm streaming the media through samba (which I'm having permissions hell right now) to a winblows machine that has the d-link server put on it.. However, it gets rather laggy on the video feed on occasion due to streaming through the network... 


Anyway.. Anyone have any idea as to what i can do to get this off my machine and to maybe get ushare working?

---

### Post by grantjohnston on 2007-01-13
> **grantjohnston said:**
> I try that and I get



```
The following packages will be REMOVED:
  gmediaserver
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 311kB disk space will be freed.
Do you want to continue [Y/n]? Y 
(Reading database ... 96565 files and directories currently installed.)
Removing gmediaserver ...
Stopping gmediaserver: invoke-rc.d: initscript gmediaserver, action "stop" failed.
dpkg: error processing gmediaserver (--remove):
 subprocess pre-removal script returned error exit status 1
Starting gmediaserver: Errors were encountered while processing:
 gmediaserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
grant@threeve:~$ 

```


Every time I try and remove it, it fails. I tried starting it to see if it will stop it in the process of uninstalling it and remove it... Even stopped it won't uninstall... I hate this thing, I just want it off my machine, haha... Right now I'm streaming the media through samba (which I'm having permissions hell right now) to a winblows machine that has the d-link server put on it.. However, it gets rather laggy on the video feed on occasion due to streaming through the network... 


Anyway.. Anyone have any idea as to what i can do to get this off my machine and to maybe get ushare working?


TTT, anyone know? I've got samba streaming to a Winblows box running the D-link software, however, it hogs up the bandwidth on my network greatly.. Anyone have any ideas?

---

### Post by dormant on 2007-01-17
> **ntrusbak said:**
> I am using Ubuntu Server 6.06 LTS, and getting the following error message:

The following packages have unmet dependencies:
  ushare: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages

Hope someone can help me. 

br,
Niels.

I have exactly the same problem using Ubuntu Server 6.06 LTS. 

Any suggestions?

---

### Post by grantjohnston on 2007-01-28
> **grantjohnston said:**
> TTT, anyone know? I've got samba streaming to a Winblows box running the D-link software, however, it hogs up the bandwidth on my network greatly.. Anyone have any ideas?

TTT, I really need a fix for this.. Anyone?

---

### Post by Blues- on 2007-03-30
You could use mediatomb as an alternative ..
I've written a howto here => [http://ubuntuforums.org/showthread.php?t=397026](http://ubuntuforums.org/showthread.php?t=397026)

---

### Post by serifos00 on 2007-07-24
Sorry for visiting a rather old topic, but I was registered just for it, so allow me. :)

My comments address a number of the posts in this topic; I would welcome comments from you too. Also, I have  a couple of questions too, so please answer them, if you can. 

1)  When I first tried to install ushare, I did it on a Virtual Ubuntu machine. It failed, I do not recall what were the exact error messages, very likely the ones with the necessary libc. Then I decided to take the plunge on my actual Ubuntu installation; there it installed without any major problems. Since then, it works (almost) perfectly.

2) For the person who asked about the DSM320 (well, one year ago, I am afraid). The ushare program does not do any transcoding. If the video is supported by the DSM320, it will play there, if not, it will not. (Supported video formats are DivX5, XViD and possibly VOBs. The audio stream on the video has to be the appropriate one. MP3 with CBR 96-160 will play, MP3 with ABR/VBR will not. Straight Dolby5.1 should work.)
If you need transcoding (and internet streaming) there is this nice (and free!) application (Tversity), but, unfortunately, there is no linux version yet, only Windows.

Here are the questions:
3) The ushare says that it supports subtitles (.srt files). However, I have not managed to see the subtitles when I select the file. How could I manage to get the subtitles?

4) When I do apt-get dist-upgrade, I get the message  " The following packages have been kept back:      ushare "
   Any idea why?

Thanks

---

### Post by yug23 on 2007-08-17
Hi, this is my first post on the ubuntu forums! :)

I spent ages trying to sort out this problem and I found the best way to install ushare was to uninstall libupnp0:

```
sudo aptitude remove libupnp0
```

then download the following two .debs:

[ushare_0.9.10]("http://www.mirrorservice.org/sites/download.sourceforge.net/pub/sourceforge/u/us/ushare/ushare_0.9.10-0ubuntu1_i386.deb")

and [libupnp 2]("http://linux.vanvalkinburgh.org/files/libupnp/libupnp2_1.4.2-1ubuntu0.1_i386.deb")

install (by double-clicking) on libupnp2 then ushare 0.9.10.

This seems to be the only way to do it without 'dependency hell' - you have to ignore the warnings about there being newer versions in the repositories etc- but it works! :guitar:

---

### Post by jaw1959 on 2007-09-05
Sorry to butt in, but I just got this to work on my 7.04 install, with only 1 minor flaw.  I have around 200gb of .mp4 movies, and a few .avi videos.  For some reason, when using my DSM 520 with uShare, it displays .avi files perfectly, but it tries to play my .mp4 files as audio.  is there any fix?  I'm quite new to uShare, and all I've done is do my best to follow the tutorial at the beginning of this thread.  Any help would be appreciated.

---

### Post by yug23 on 2007-09-05
according to[ this page]("http://http://linux.vanvalkinburgh.org/2007/05/25/stream-videos-to-xbox-360-with-patched-ushare/"), you can rename the extension to .mov and it will work. My geexbox does play mp4s as video properly so it may be an issue with your player rather than uShare.

---

### Post by Kokuyou on 2008-09-06
Hi guys,

I'm trying to get ushare working with Ubuntu 8.04.  I can't see any useful errors; nonetheless, nobody on the network can auto-detect or connect to the server.  

Network: Linksys WRT54G Router (latest bios, UPnP enabled), Ubuntu 8.04, Macbook, Xbox360.

> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:20:28:80
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ffff::fff:ffff:ffff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1910628 errors:0 dropped:77793634696 overruns:0 frame:0
          TX packets:1172459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2616642431 (2.4 GB)  TX bytes:313556432 (299.0 MB)
          Interrupt:250 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:266217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13386599 (12.7 MB)  TX bytes:13386599 (12.7 MB)
 
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

$ cat /etc/ushare.conf
USHARE_NAME=uShare
USHARE_IFACE=eth0
USHARE_PORT=
USHARE_TELNET_PORT=
USHARE_DIR=/usr/local/share/videos
USHARE_OVERRIDE_ICONV_ERR=
ENABLE_WEB=no
ENABLE_TELNET=no
ENABLE_XBOX=yes
ENABLE_DLNA=no

$ sudo ushare -xv                               
Interface eth0 is down.                                                
Recheck uShare's configuration and try again !                         
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.   
Benjamin Zores (C) 2005-2007, for GeeXboX Team.                        
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.                            
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.104:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /usr/local/share/videos
...
Found 27 files and subdirectories.

My macbook on the network can nmap the port on the Ubuntu box:
> $ nmap 192.168.1.104 -p 49152

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-09-06 14:23 MST
Interesting ports on 192.168.1.104:
PORT      STATE SERVICE
49152/tcp open  unknown


(The ip addresses: router = 192.168.1.1, ubuntu = 192.168.1.104, xbox360 = 192.168.1.101, macbook = 192.168.1.102)

In addition to ushare, I've also tried running gmediashare with similar results (nobody can find or connect to my UPnP share).  

I've tried connecting to the share using the Xbox360 and the Macbook w/ mediacloud.  No luck finding it with either.  



Any ideas?  I admittedly know zero about UPnP.  Any good way to troubleshoot it?  Looks like it's just broke on my network :)  Let me know if I can provide any additional details. 

Thanks in advance for any help!

---

### Post by clauguia on 2008-10-27
thank you.  it worked fine.  I just had a misunderstanding in the route command line and I had to figure out that, if my ip range is something like abc.def.ghi.0 my netmask must be 255.255.255.0  .  After that, all was fine.

Thank you very much, now I can stream and copy my videos from my file server directly into my n95 through wifi.

---

