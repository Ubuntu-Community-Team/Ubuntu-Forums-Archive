---
title: "Tip (small): mplayerplug-in"
date: 2005-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by gasparov on 2005-04-09
Hi,
   before upgrading to Hoary I had compiled mplayerplug-in by myself and after a few configurations it was running.Installed the plug-in with apt here  in Hoary but playing videos for any reason are missing controls, I couldn't switch to fulscreen for example.I haven't find out how to show these controls but at least I worked problem around by editing plugin specific option:
```
sudo gedit /etc/mplayerplug-in.conf
 
```

You'll find a few all commented out lines,probably because the plug-in was supposed to rely on mplayer configuration, but is worthy to change something for example my .conf is as follows:

```
#debug=0
#logfile=$HOME/mpp.log
#vo=x11,xv  #commented out cause my mplayer is perfectly working
#ao=esd,oss #the same
download=1
dload-dir=$HOME/tmp
#keep-download=0
noembed=1
fileonly-embed=1
#cachesize=256
#use-mimetypes=0
enable-real=1
enable-wm=1
enable-qt=1
enable-mpeg=1
enable-ogg=1
qt-speed=med #adsl speed
#rtsp-use-tcp=0
#nomediacache=0

```

With this configuration mplayer starts as separate windows and you can use keyboard controls on it ( f = fullscreen :) the only reason i actually changed all this stuff).
I haven't tested it but now you should be able to play real and download streams...
When you comment out or add line with "enable" in it you have to remove pluingreg.dat from firefox profile/main directory in order to make it rebuilt,mine was in "$HOME/.mozilla/firefox" but I think this is jusy my case.

[mplayerplug-in options explained](http://mplayerplug-in.sourceforge.net/config.php)
[Testing Page](http://fredrik.hubbe.net/plugger/test.html)

---

### Post by samushka on 2005-04-24
hi, i followed ur config file, and fullscreen does indeed work... but the aspect of the stream is kept to the default...

any knowledge on how to stretch the movie to fill the "full screen" ???

thx.

---

### Post by Paul Atreides on 2005-04-24
Same problem for me... F shortcut flush the screen with black but the video remains to the same size... Does a shortcut exist to expand the video to the entire screen ?
 :-?

---

### Post by kuleali on 2005-04-24
Try the mplayer with no gui, worked for me

---

### Post by Cimmerian on 2005-04-24
If you get a black screen with the video staying the same size and you are unable to resize it in any way, you are probably using x11 as the video output driver. Ways to fix this is either to add vo=xv or zoom=1 to your ~/.mplayer/config file. Try vo=xv first, if all is good, excellent. If not, try adding zoom=1. I had some trouble with xv using twinview and also when running xcompmgr. 

C

EDIT: Looking at that config-file in the first post (/etc/mplayerplug-in.conf), I assume you could just as well add these options there. Having them for all mplayer uses is probably smart though, so you might want them in your mplayer config as well.

EDIT2: Just thought I'd mention that if you prefer to use alsa (which you should =), adding alsa to the ao=esd,oss line (ao=alsa,esd,oss), or adding such a line to your mplayer config, would accomplish this.

---

### Post by gasparov on 2005-04-24
[QUOTE=Cimmerian]
C

EDIT: Looking at that config-file in the first post (/etc/mplayerplug-in.conf), I assume you could just as well add these options there. Having them for all mplayer uses is probably smart though, so you might want them in your mplayer config as well.
[/QUOTE]

Yep, thats the plug-in config and if no configs are presents it looks at mplayer config file...considering mplayer config file (/home/user/.mplayer/config) these lines should lets
 you go fullscreen

```


fs=no # Enlarges movie window to your desktop's size,yes if you want                fullscreen from start



zoom=yes# Enable software scaling (powerful CPU needed)
# Used by drivers: svga, x11, vesa------>!!!here's the key!!!!



```

---

### Post by Paul Atreides on 2005-04-24
Eureka !
This is the solution (thanks to Cimmerian for orienting me) ; it works for me with this the /etc/mplayerplug-in.conf file :

```
#debug=0
#logfile=$HOME/mpp.log
#vo=xv
vo=x11
#ao=arts,esd,oss
download=1
dload-dir=/data1/trailers
keep-download=1
noembed=1
fileonly-embed=1
fs=1
#cachesize=256
#use-mimetypes=0
enable-real=1
enable-wm=1
enable-qt=1
enable-mpeg=1
enable-ogg=1
qt-speed=high
#rtsp-use-tcp=0
#nomediacache=0
``` 

With this settings, I have just to hit "f" key and the video is in fullscreen ; all the others shortcuts are active (FF and RW with the R&L arrows and so on...)
Apparently, my graphic card (ATI 9200 SE) needs vo=x11. The download parameters permit to save the video at realtime in a directory of your choice.
noembed parameter permits to have the video in a different window within the browser (Firefox for me) and fs parameter permits the fullscreen...

I hope this helps !!!

Paul Atreides

---

### Post by NTolerance on 2005-04-25
Thanks for posting this.  I was having lots of problems with the totem-xine/mozplugger setup and the other method of using the mplayerplug-in not wanting to play some/all videos.  This appears to work with everything I throw at it.  

The only problem I'm having is with the fullscreen option.  I end up with the large black border and original size video.  I have tried all of the above suggestions to stretch the size of the video, but no luck.  My video chip is an ATI Mobility M6.

---

### Post by gasparov on 2005-04-26
Does your mplayer have the same behaviour? If not try to uncomment everything in mplayer plugin config (not mplayer)...
If yes try changing mplayer config vo=xv or x11,add zoom=yes and then try to find out how to have fullscreen with mplayer,then it should be easy to config the plugin

---

### Post by rickwood on 2005-05-02
Thanks for this tip!  I've been wondering for a long time how to get mplayerplug-in not to embed videos.  Following these instructions, it's now working exactly how I had hoped.

---

### Post by viuks on 2005-05-04
Thank you for wery usefull tip!
This has to be HOWTO.

---

