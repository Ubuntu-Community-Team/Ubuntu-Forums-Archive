---
title: "Rip CD to MP3"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by RealG187 on 2008-10-31
[http://ubuntuforums.org/showthread.php?p=6077520#post6077520](http://ubuntuforums.org/showthread.php?p=6077520#post6077520)

I cant rip to MP3. I think as of 8.04 things have changed

---

### Post by Bölvaður on 2008-10-31
if you use the standard rythmbox go to Edit &#8594; Preferences and then change preferred audio format into mp3, when you rip your cds they will be put into your top music folder stated above the place where you pick audio format. hope you'll figure this out

---

### Post by rickycodie on 2008-10-31
first that how -to is out of date. it's for edgy or dapper you want ibex or hardy. so that's problem number 1. try using rhythmbox, it can do this by default.

---

### Post by RealG187 on 2008-10-31
Mp3 does not show up under preferred format and that is the problem!

okay

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
```

shows up (only in Rhythmbox and not Sound Juicer)

but I want

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=64 ! id3mux
```

And PS, I know what bitrate I want, I dont want comments saying that's bad quality. I hardly notice a difference....

---

### Post by lucasl on 2008-10-31
Try installing gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly.
Type this in the terminal:
```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by RealG187 on 2008-10-31
> mpg@Sherpat3md:~$ sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  freepats libcdaudio1 libfaad0 libgmyth0 libiptcdata0 libmms0 
  libmysqlclient15off libopenspc0 libsoundtouch1c2 libwildmidi0 
  mysql-common 
The following packages have been kept back:
  wine 
The following NEW packages will be installed:
  freepats gstreamer0.10-plugins-bad libcdaudio1 libfaad0 libgmyth0 
  libiptcdata0 libmms0 libmysqlclient15off libopenspc0 libsoundtouch1c2 
  libwildmidi0 mysql-common 
0 packages upgraded, 12 newly installed, 0 to remove and 1 not upgraded.
Need to get 32.1MB of archives. After unpacking 41.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe freepats 20060219-1 [29.0MB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libcdaudio1 0.99.12p2-3 [44.9kB] 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libfaad0 2.6.1-2 [167kB]         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main mysql-common 5.0.51a-3ubuntu5 [59.7kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libmysqlclient15off 5.0.51a-3ubuntu5 [1836kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libgmyth0 0.7.debian1-1~hardy1 [52.4kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libiptcdata0 1.0.2-2 [24.4kB]    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libmms0 0.3-6 [25.0kB]           
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libopenspc0 0.3.99a-2 [27.0kB]   
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libsoundtouch1c2 1.3.0-2.2 [26.0kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libwildmidi0 0.2.2-2 [41.9kB]   
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe gstreamer0.10-plugins-bad 0.10.6-5 [850kB]
Fetched 32.1MB in 1min43s (309kB/s)                                             
Selecting previously deselected package freepats.
(Reading database ... 130198 files and directories currently installed.)
Unpacking freepats (from .../freepats_20060219-1_all.deb) ...
Selecting previously deselected package libcdaudio1.
Unpacking libcdaudio1 (from .../libcdaudio1_0.99.12p2-3_i386.deb) ...
Selecting previously deselected package libfaad0.
Unpacking libfaad0 (from .../libfaad0_2.6.1-2_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.51a-3ubuntu5_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.51a-3ubuntu5_i386.deb) ...
Selecting previously deselected package libgmyth0.
Unpacking libgmyth0 (from .../libgmyth0_0.7.debian1-1~hardy1_i386.deb) ...
Selecting previously deselected package libiptcdata0.
Unpacking libiptcdata0 (from .../libiptcdata0_1.0.2-2_i386.deb) ...
Selecting previously deselected package libmms0.
Unpacking libmms0 (from .../libmms0_0.3-6_i386.deb) ...
Selecting previously deselected package libopenspc0.
Unpacking libopenspc0 (from .../libopenspc0_0.3.99a-2_i386.deb) ...
Selecting previously deselected package libsoundtouch1c2.
Unpacking libsoundtouch1c2 (from .../libsoundtouch1c2_1.3.0-2.2_i386.deb) ...
Selecting previously deselected package libwildmidi0.
Unpacking libwildmidi0 (from .../libwildmidi0_0.2.2-2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad.
Unpacking gstreamer0.10-plugins-bad (from .../gstreamer0.10-plugins-bad_0.10.6-5_i386.deb) ...
Setting up freepats (20060219-1) ...
Setting up libcdaudio1 (0.99.12p2-3) ...

Setting up libfaad0 (2.6.1-2) ...

Setting up mysql-common (5.0.51a-3ubuntu5) ...
Setting up libmysqlclient15off (5.0.51a-3ubuntu5) ...

Setting up libgmyth0 (0.7.debian1-1~hardy1) ...

Setting up libiptcdata0 (1.0.2-2) ...

Setting up libmms0 (0.3-6) ...

Setting up libopenspc0 (0.3.99a-2) ...

Setting up libsoundtouch1c2 (1.3.0-2.2) ...

Setting up libwildmidi0 (0.2.2-2) ...

Setting up gstreamer0.10-plugins-bad (0.10.6-5) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
mpg@Sherpat3md:~$ 


Still doesn't show up. I have to go soon and I want this CD ripped so I can listen on the go.......

---

### Post by RealG187 on 2008-11-01
Please help!

I think I did it once on my laptop the way I wanted it, but I don't have it now (out for repair)

---

### Post by pannerrammer on 2008-11-18
**CD ripping with RhythmBox**

From several sources, this got things working for me:

First, you need to enable the Medibuntu repository

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```Then add the appropriate GPG key

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Now you can add the mp3 codecs with one of (for 32 or 64 bit installations)

```

sudo apt-get install w32codecs ubuntu-restricted-extras
sudo apt-get install w64codecs ubuntu-restricted-extras

```The[FONT=Fixedsys][COLOR=Navy] ubuntu-restricted-extras[/COLOR][/FONT] is a load of stuff, most of which is unnecessary, but it's not clear which bits are actually required! I suspect, as lucasl said, you only need the gstreamer-bad and gstreamer-ugly bits, but not sure now I've installed them all!

So, you could try one of these first
```

sudo apt-get install w32codecs gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
sudo apt-get install w64codecs gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

```pannerramer

---

### Post by 3rdalbum on 2008-11-18
All the gstreamer-bad and gstreamer-ugly codecs (ESPECIALLY the Multiverse ones), as well as lame. I think this causes the MP3 option to work, from memory.

---

### Post by starcannon on 2008-11-18
The easiest, and in my opinion nicest mp3 ripper with a gui is ripperx, very similar to cdex for windows. To get it open a terminal and copy/paste the following:
```

sudo apt-get install ripperx lame

```
You'll now find it under:
Applications>Sound & Video>Ripper X

Enjoy.

---

### Post by Dedoimedo on 2008-11-18
Hello,

Did you try audacity?

You may also want to check SoundConverter or audioKonverter.

See if this helps you:
[http://www.dedoimedo.com/computers/audio_conversion_linux.html](http://www.dedoimedo.com/computers/audio_conversion_linux.html)

Dedoimedo

---

### Post by MrWES on 2008-11-18
I'd have to give a shout out for ABCDE - A Better CD Extractor. It's command line and you have to edit the .abcde.config, but it does VBR very nicely. 

[http://lly.org/~rcw/abcde/page/]("http://lly.org/~rcw/abcde/page/")

Bill

---

### Post by RealG187 on 2008-11-18
> **3rdalbum said:**
> All the gstreamer-bad and gstreamer-ugly codecs (ESPECIALLY the Multiverse ones), as well as lame. I think this causes the MP3 option to work, from memory.

I have ubuntu-restricted-extras which should have them and did apt-get install lame.

I can rip to 128 KB/s but no 64 KB/s...

---

### Post by em4r1z on 2008-11-19
> **RealG187 said:**
> I can rip to 128 KB/s but no 64 KB/s...Since this is a quite recent 8.10 64-bit system and I've not installed the multimedia codecs yet, I can't say this is the case but make sure this bug isn't present:
[http://ubuntuforums.org/showthread.php?t=608034&page=3](http://ubuntuforums.org/showthread.php?t=608034&page=3)

It was in 8.04 64-bit and I had to downgrade the GStreamer Multiverse Ugly package to encode as desired. Also, make sure the LAME element properties you're using are correct by checking the output of "gst-ispect lame".

---

### Post by growingneeds on 2008-11-19
Hi,

I am not too sure which dependencies are required to rip mp3s in Rhythmbox, but, that option appeared after I installed the metapackage "restricted extras". The download process will be long. But after the install (with MS TT Core fonts, Java, Flash, mp3 support, and some), you will be able to rip to mp3s. Just make sure you sit by the PC as it installs. You need to answer agree to some EULAs.

Do consider the default ogg rips. I'm using Rockbox 3.0 on my iPod.

---

### Post by starcannon on 2008-11-19
> **RealG187 said:**
> I have ubuntu-restricted-extras which should have them and did apt-get install lame.

I can rip to 128 KB/s but no 64 KB/s...

This is one of the reasons I suggest Ripperx, it allows you to rip at any bitrate.

GL and have fun.

---

### Post by pannerrammer on 2008-11-19
niteshifter (thread [http://ubuntuforums.org/showthread.php?t=938605](http://ubuntuforums.org/showthread.php?t=938605)) reckons you can increase the bit rate by changing the Gstreamer pipeline entry for the mp3 entry in RhythmBox to

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=0 bitrate=320 ! id3v2mux
```so I'd guess that the following will reduce it to 64...
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=0 bitrate=64 ! id3v2mux
```

---

### Post by RealG187 on 2008-11-21
I can't get CBR to work. CBR works at 128+, but not 64

---

### Post by RealG187 on 2008-12-14
I got my Laptop back from repair and figured out I used Banshee 0.13.2 that time I ripped and it worked. I swore I tried Banshee before and it didn't work... Maybe my other PCs had different versions or something.

(I got it back from repair, but they broke it so I can't close the lid, so now I have to send it back again)

---

### Post by sneeks on 2008-12-14
if you have all of the g-streamer bad and ugly sets and lame,you should be able to rip easy,if you still have problems,try asunder it lets you encode all the way,is my fave.
im not sure if it is in the repo's so you may have to go to the site.

---

### Post by kevinshields on 2011-01-13
Why not try this stuff that I wrote [http://nollettnoll.net/ripcd.sh](http://nollettnoll.net/ripcd.sh) ; configure where to put your MP3's, then first run as

# ripcd.sh install

unless you don't have the binaries needed. Then run it from your desktop with a launcher like the one described.

---

