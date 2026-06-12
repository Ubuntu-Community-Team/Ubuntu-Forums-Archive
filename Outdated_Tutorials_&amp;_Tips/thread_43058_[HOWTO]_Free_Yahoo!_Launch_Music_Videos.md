---
title: "[HOWTO] Free Yahoo! Launch Music Videos"
date: 2005-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by thechitowncubs on 2005-06-20
[IMG]http://a1568.g.akamai.net/7/1568/1600/36c7403d3897c6/launch.yahoo.com/common/resources/skins/us/LAUNCH_hdr_gradient_left.jpg[/IMG] 
Requirements:
Mplayer

```
wget [http://www.thechitowncubs.com/linux/install.sh](http://www.thechitowncubs.com/linux/install.sh)
``` 
```
sudo sh install.sh
```
Now go to [Yahoo! Launch](http://music.yahoo.com/musicvideos/default.asp)  and once you find the music video you want, hover over and find the video ID.

You're all set to watch free music videos now!  :)  :)

---

### Post by thechitowncubs on 2005-06-20
> **thechitowncubs][IMG]http://a1568.g.akamai.net/7/1568/1600/36c7403d3897c6/launch.yahoo.com/common/resources/skins/us/LAUNCH_hdr_gradient_left.jpg[/IMG] 

This HOWTO is for everyone that wants to watch free music videos with no advertisements through mplayer (I've tried to modify the script to work with totem but I can't get it to work, maybe someone with more experience can take a look at it).

All it is, is a simple script that finds the mms link to the video and then plays it through mplayer. 

Requirements:
Mplayer ([https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto))
```
sudo nano yahoolaunch.sh
```

Paste the following:
```
#!/bin/bash

if [ $# -eq 0 ] said:**
>  && [ $1 != 0 ]; then
bandwidth=$1
shift
else
# 56 or 128 or 300
bandwidth=300
fi

file1=$(wget "http://launchtoday.launch.yahoo.com/player/medialog.asp?vid=$videoid&cid=1&pid=4&csid=396500550&p1=&p2=&p3=2&bw=$bandwidth&mf=1&origin=35&pguid=AA388C059C7849D99CCFBC72B6F51E37&uid=42&sk=bad551cd352143eb2da02&z=ms.asx" -q -O -)

if [ $1 == "http" ]; then
file2=$(wget "$file1" -q -O - | sed 's/mms:/http:/g')
shift
else
file2=$(wget "$file1" -q -O -)
fi

mplayer -cache 500 $file2 $@
```

```
sudo chmod +x yahoolaunch.sh
``` 

Now go to [Yahoo! Launch](http://music.yahoo.com/musicvideos/default.asp) and once you find the music video you want, hover over and find the video ID.

```
./yahoolaunch.sh <videoid>
```

[Script Source](http://www.linuxforums.org/forum/topic-37377.html)
 I am currently modifying this to make it more userfriendly and so it can run without the terminal :), standby.

---

### Post by thechitowncubs on 2005-06-20
Script updated!

Let me know how you guys like it :)

---

### Post by SqdnGuns on 2005-06-20
Sweeeet..............works like a charm!!

---

### Post by Quest-Master on 2005-06-20
Haha.. I should've come up with something like this. Awesome :D

---

### Post by angrykeyboarder on 2005-06-21
[QUOTE=thechitowncubs][img]http://a1568.g.akamai.net/7/1568/1600/36c7403d3897c6/launch.yahoo.com/common/resources/skins/us/LAUNCH_hdr_gradient_left.jpg[/img] 
Requirements:
Mplayer[/QUOTE] Just Mplayer works? Not Totem? :-(

---

### Post by thechitowncubs on 2005-06-21
[QUOTE=angrykeyboarder]Just Mplayer works? Not Totem? :-([/QUOTE]
 You can try to modify the script to get totem to work, but I haven't had any success.

Script is at: /usr/local/bin/yahoo

---

### Post by moment on 2005-06-21
thanks very much. it's handy.

---

### Post by luvthepenguin on 2005-06-21
Very cool tip... Quick and easy, that's how I like it. Thanks alot Chitown.

---

### Post by bored2k on 2005-06-21
This is probably the only reason why I would install MPlayer. Thanks Chitown.

---

### Post by Poul on 2005-06-22
You can also use a plugin for firefox

---

### Post by spockrock on 2005-06-22
i have tried the firefox plugin doesnt work for me, but this script does thanks chitown......

---

### Post by angrykeyboarder on 2005-06-22
[QUOTE=bored2k]This is probably the only reason why I would install MPlayer. Thanks Chitown.[/QUOTE]

exactly......

---

### Post by darknuala on 2005-06-22
[QUOTE=thechitowncubs]Script updated!

Let me know how you guys like it :)[/QUOTE]


Can someone please explain how this works?  I cannot get it to do anything, but then again, I'm not sure what the ID is for a song, so I don't know what to put in.

---

### Post by thechitowncubs on 2005-06-23
if you hover over the link for the music video, there will be about a 7 digit number i think ... type that in and you're off  ;-)

---

### Post by darknuala on 2005-06-23
[QUOTE=thechitowncubs]if you hover over the link for the music video, there will be about a 7 digit number i think ... type that in and you're off  ;-)[/QUOTE]

thats what i did, then the launch box disappears

---

### Post by coram deo on 2005-07-04
I have followed the instructions from this post yet when I go to yahoo and copy the link for a video into the box and click through the menu, nothing happens.  I have mplayer installed, plus the plugin.  Am I missing something here?  Also, I don't see the info for the video when I hover over the link, so I have just copied the link into the box :?

---

### Post by thechitowncubs on 2005-07-04
to get the video id there will be a number within the link, extract that link into the video id field and your off :)

---

### Post by berserker on 2005-07-06
I got the Yahoo! videos to work with mplayer and mplayerplug-in 2.85 that I compiled myself along with the Play Launch 0.2.2 plugin.

Strange but it works just by clicking on the video link.

---

### Post by nilegomez on 2005-07-08
doesn't seem to be working for me... I had a tough time installing mplayer... could that be it? If I open mplayer, it opens fine. When I open the music video app, it appears to work fine until right after I enter the video number... it asks me a few more questions... the last one is http or mms, I think & then it opens a window & crashes...

help!

---

### Post by thechitowncubs on 2005-07-09
[QUOTE=nilegomez]doesn't seem to be working for me... I had a tough time installing mplayer... could that be it? If I open mplayer, it opens fine. When I open the music video app, it appears to work fine until right after I enter the video number... it asks me a few more questions... the last one is http or mms, I think & then it opens a window & crashes...

help![/QUOTE]
 sounds like you need to specify which video driver mplayer uses, try changing it to xv i think it is

---

### Post by ykpaiha on 2005-07-09
Just some small adds on your post:

VLC work fine with the batch in /usrlocal/bin/yahoo

just open it ; sudo gedit
and change on the last line from mplayer to vlc (totem and xine didn't work for me --very bad sound)
The ease of vlc is that it can easly change the output (Iknow you can as well save a stream with mplayer but not that easy )
By ex: 

vlc $file2 $@ --sout file/avi:[file.avi]  

on the last line will save the stream encoded in avi as file.avi in your home. (you can change the stout encod with mpg or else...)
By the way why ubuntu does not provide vlc 0.82???

In order to get the proper Number of the file in Yahoo you just to copy - past the link provided into the opened window and then remove the adress, just keep the code..

I don't know if all of this is legal but it is at least usable.

Thanks

---

### Post by chz on 2005-07-12
I got it working with gxine

do the same as above:
sudo gedit /usr/local/bin/yahoo

and edit the line with mplayer to:
gxine $file2 $@

i only got it to work with 128 bit...300 bit won't work for sum reason.
also i havent got totem to work yet, but i like gxine better anyway.

---

### Post by Mr. Electric Wizard on 2005-07-12
[QUOTE=thechitowncubs]sounds like you need to specify which video driver mplayer uses, try changing it to xv i think it is[/QUOTE]

Ahh, I see...
Thanks!

---

### Post by super on 2005-07-12
any chance of writing something similar for aol videos?

---

### Post by Kevlar on 2005-07-17
A question and a contribution:

First the question.  How would one edit the file so that it would automatically use 300 and mms as the option on the second and third boxes (that is, I don't even want to see those boxes, I just want the first one asking for the video number).  

Second, my contribution.  To copy the stream to your home directory, use this for the last line of the script:

```
mplayer -dumpstream $file2 $@ -dumpfile try1.avi
```

That will dump the stream as a file named try1.avi.  Seems to work nicely.  Totem doesn't always play the stream nicely for me, but mplayer works fine.  May be an encoding thing.  Though it is a direct dump of the stream as it comes from yahoo, so that could explain why others haven't gotten totem to play it correctly.

Also, a second contribution, this one minor.  I modified the last line of my script so that the windows is placed on my screen where I want it and will remain on top so I can see the video while still web browsing.

```
mplayer -ontop -geometry 97%:85% -cache 500 $file2 $@
```

On my screen, this puts the window near the bottom right corner, just back far enough that I can still use my scroll bar when firefox is full screen.  Plus it remains on top of all other apps.  

Just want to thank the author of this script.  It is amazing what you can do in Linux.

---

### Post by arnieboy on 2005-07-17
[QUOTE=Kevlar]First the question.  How would one edit the file so that it would automatically use 300 and mms as the option on the second and third boxes (that is, I don't even want to see those boxes, I just want the first one asking for the video number).[/QUOTE]

```
sudo gedit /usr/local/bin/yahoo
```

**Replace** the contents of the file with the following code:
```
#!/bin/bash
videoid=$(zenity --title="Yahoo! Launch" --entry --text="Music Video ID")
shift

file1=$(wget "http://launchtoday.launch.yahoo.com/player/medialog.asp?vid=$videoid&cid=1&pid=4&csid=396500550&p1=&p2=&p3=2&bw=300&mf=1&origin=35&pguid=AA388C059C7849D99CCFBC72B6F51E37&uid=42&sk=bad551cd352143eb2da02&z=ms.asx&" -q -O -)

#if [ $(zenity --title="Yahoo! Launch" --entry --text="Protocol (http or mms[default])" --entry-text="mms") == "http" ]; then
#file2=$(wget "$file1" -q -O - | sed 's/mms:http/g')
#else
file2=$(wget "$file1" -q -O -)
#fi

mplayer -cache 1024 $file2 $@
```

Save and exit. Enjoy!

---

### Post by arnieboy on 2005-07-17
[QUOTE=berserker]I got the Yahoo! videos to work with mplayer and mplayerplug-in 2.85 that I compiled myself along with the Play Launch 0.2.2 plugin.

Strange but it works just by clicking on the video link.[/QUOTE]
Tested and confirmed. This works. 
For all u out there who want to play launchcast videos in **firefox** merely by clicking on the video: first make sure u have mplayerplug-in 2.85 installed. If its not there, follow this HOWTO:
[http://ubuntuforums.org/showthread.php?t=44560](http://ubuntuforums.org/showthread.php?t=44560)
Then go to the following link in **firefox**
[http://www.extensionsmirror.nl/lofiversion/index.php/t3137.html](http://www.extensionsmirror.nl/lofiversion/index.php/t3137.html)
and click on "install"
After the extension gets installed restart firefox and enjoy the launchcast videos merely by clicking on them.

---

### Post by johnmc on 2005-07-19
Thanks, great script! :)

---

### Post by thechitowncubs on 2005-07-20
[QUOTE=arnieboy]```
sudo gedit /usr/local/bin/yahoo
```

**Replace** the contents of the file with the following code:
```
#!/bin/bash
videoid=$(zenity --title="Yahoo! Launch" --entry --text="Music Video ID")
shift

file1=$(wget "http://launchtoday.launch.yahoo.com/player/medialog.asp?vid=$videoid&cid=1&pid=4&csid=396500550&p1=&p2=&p3=2&bw=300&mf=1&origin=35&pguid=AA388C059C7849D99CCFBC72B6F51E37&uid=42&sk=bad551cd352143eb2da02&z=ms.asx&" -q -O -)

#if [ $(zenity --title="Yahoo! Launch" --entry --text="Protocol (http or mms[default])" --entry-text="mms") == "http" ]; then
#file2=$(wget "$file1" -q -O - | sed 's/mms:http/g')
#else
file2=$(wget "$file1" -q -O -)
#fi

mplayer -cache 1024 $file2 $@
```

Save and exit. Enjoy![/QUOTE]
 that works, good job on the contributions guys


long live ubuntu :)

---

### Post by Mr. Electric Wizard on 2005-07-20
[QUOTE=Mr. Electric Wizard]Ahh, I see...
Thanks![/QUOTE]


Still doesn't work, any other ideas?
When MPlayer opens, the only thing that happens is that the window comes up, then it freezes and won't play the video.

---

### Post by arnieboy on 2005-07-20
[QUOTE=Mr. Electric Wizard]Still doesn't work, any other ideas?
When MPlayer opens, the only thing that happens is that the window comes up, then it freezes and won't play the video.[/QUOTE]
Can u paste the contents of etc/mplayer/mplayer.conf ?

---

### Post by Mr. Electric Wizard on 2005-07-20
Sure thing, here ya go...

```
##
## MPlayer config file
##
## This file can be copied to /etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

vo=x11,			# To specify default video driver (see -vo help for
			# list)

ao=alsa,		# To specify default audio driver (see -ao help for
			# list)

fs=no			# Enlarges movie window to your desktop's size.
			# Used by drivers: all

vm=no			# Tries to change to a different videomode
			# Used by drivers: dga2, x11, sdl

bpp=0			# Force changing display depth.
			# Valid settings are: 0, 15, 16, 24, 32
			# may need 'vm=yes' too.
			# Used by drivers: fbdev, dga2, svga

zoom=no			# Enable software scaling (powerful CPU needed)
			# Used by drivers: svga, aalib

double=yes		# use double-buffering (recommended for xv with
			# SUB/OSD usage)

# x=800			# scale movie to <x> pixels width
# y=600			# scale movie to <y> pixels height

osdlevel=1		# don't display OSD at stratup

monitoraspect=4:3	# standard monitor size, with square pixels
# monitoraspect=16:9	# use this for widescreen monitor! non-square pixels

cache = 1024		# Disk cache 1 MB

##
## Specify your preferred default skin here
## (skins are searched in /usr/share/mplayer/Skin/yourskin
##  and ~/.mplayer/Skin/yourskin)
##

skin = default


##
## Multiple languages are available :)
##
## Hungarian	igen	nem
## English	yes	no
## German	ja	nein
## Spanish	si	no
## Binary	1	0
##
## You can also use spaces and/or tabs.
##

#sound		= 1
#nosound	= nein
#mixer		= /dev/mixer

##
## resample the fonts' alphamap
## 0	plain white fonts
## 0.75	very narrow black outline (default)
## 1	narrow black outline
## 10	bold black outline
##

#ffactor = 0.75

##
## FBdev driver: 

# fb = /dev/fb0				# framebuffer device to use
# fbmode = 640x480-120			# use this mode (read from fb.modes!)
# fbmodeconfig = /etc/fb.modes		# the fb.modes file

## VESA and FBdev driver: specify your monitor's timings
## 
## (see for example /etc/X11/XF86Config for timings!)
## ** CAUTION! IF YOUR DISPLAY DOESN'T SUPPORT AUTOMATICALLY TURNING OFF WHEN
##    OVERDRIVED (AND EVEN IF IT DOES), THIS MAY CAUSE DAMAGE TO YOUR DISPLAY!
##    WE AREN'T RESPONSIBLE, IT'S YOUR DECISION! **
##
## k, K : means multiply by 1000
## m, M : means multiply by 1.000.000
##
# monitor_hfreq = 31.5k-50k,70k		# horizontal frequency range
# monitor_vfreq = 50-90			# vertical frequency range
# monitor_dotclock = 30M-300M		# dotclock (or pixelclock) range

##
## SDL driver
##

# vo = sdl:aalib	# use SDL video driver by default
			# use "vo = sdl:aalib" or "vo sdl:dga" and so on,
			# for specifying SDL subdrivers
# ao = sdl:esd		# use SDL audio driver by default
			# use "ao = sdl:esd" to use SDL's ESD driver
# noxv = no		# whether to use XVideo hardware acceleration or not
# forcexv = yes		# force XVideo even if not detected

##
## Other (preferred to be default from configfile) switches
##

framedrop=no		# drop frames, when not in sync (slow CPU, videocard,
			# etc)

#vfm=ffmpeg		# use FFmpeg's libavcodec video codec family
			# See "mplayer -vfm help" for all available codecs

#bps=yes		# use this method for playing AVIs (if have problems,
			# try removing this)

# slang= en		# DVD : display english subtitles if available
# alang= en		# DVD : play english audio tracks if available

## This is the correct way to use "subconfig" type options in the
## configuration file. In the command line you use :
## -aop list=resample:fout=44100 , but here it is :
# aop=list=resample:fout=44100

# From Fedora
# the default mpeg audio decoder is currently broken, let's try libmad
# first:
afm=libmad

# get a default OSD font from fontconfig
#fontconfig = yes
#font = "Sans"
#subfont-text-scale = 3

```

---

### Post by arnieboy on 2005-07-20
ok try this and it should work.
set "ao=esd"
Its currently set to "alsa"
Mplayer has known issues with the alsa sound driver.
tell me if this works for u or not.

---

### Post by Mr. Electric Wizard on 2005-07-20
Your the man... That worked like a charm!

---

### Post by lightseeker on 2005-07-23
hi
the mplayer opened and the video run smoothly but no sound

---

### Post by lightseeker on 2005-07-23
don't bother 
solve the prob  :)

---

### Post by geearf on 2005-07-24
Hello,

i'm sorry but i cannot understand how this works :(

---

### Post by Kevlar on 2005-07-24
Which part are you not understanding?  The basics are that once you install the program, you run /usr/local/bin/yahoo.  It will pop up a dialog box which asks you for the Music Video ID.  Now, if you go to [http://launch.yahoo.com](http://launch.yahoo.com) and start browsing the music videos.  When you find one you want to view, hold your mouse over the link to it.  At the bottom of your browser (assuming you use firefox), you will see the link address as javascript:playVideos(21815195).  With the exception of the number in parenthesis, the link will always look like that.  Now, type the number in parenthesis into the dialog box asking for the Music Video ID.  Do not type anything other than the number.  Do not type the javascript:playVideos() part.  Just the number.  If you are on broadband, just accept the defaults on the next two dialog boxes and enjoy your videos.

---

### Post by geearf on 2005-07-25
Hello,

welll the thing is, first I did not get i had to start the script, i tried only within ff :D

Then I tried the script, but it does not start anything, i just get some mplayer error (the same you have if you do not give it enough parameters) and something not found : 

/usr/local/bin/yahoo: line 2: zenity: command not found
/usr/local/bin/yahoo: line 5: zenity: command not found
/usr/local/bin/yahoo: line 9: zenity: command not found
/usr/local/bin/yahoo: line 9: [: ==: unary operator expected


Thanks for answering,

edit : i've just tried apt-get install zenity and it works now :D

---

### Post by rimmer on 2005-07-25
Very nice!  works straight out of the box.  :grin:
thnx

---

### Post by geearf on 2005-07-25
This work trully well thank you :)

---

### Post by Mr. Electric Wizard on 2005-07-26
[QUOTE=arnieboy]ok try this and it should work.
set "ao=esd"
Its currently set to "alsa"
Mplayer has known issues with the alsa sound driver.
tell me if this works for u or not.[/QUOTE]


A wierd thing happened last night when I went to Apple.com to view new movie trailers.
This used to work fine, but last night when the Trailers page comes up, it tries to spawn MPlayer, and a bunch of little windows appear, then disappear, then Mozilla shuts down?

Does this sound like it could be an issue with me changing ao=esd ?

---

### Post by arnieboy on 2005-07-27
[QUOTE=Mr. Electric Wizard]A wierd thing happened last night when I went to Apple.com to view new movie trailers.
This used to work fine, but last night when the Trailers page comes up, it tries to spawn MPlayer, and a bunch of little windows appear, then disappear, then Mozilla shuts down?

Does this sound like it could be an issue with me changing ao=esd ?[/QUOTE]
I have not been on my linux box for the past few days (as I am traveling)  but from memory u can solve this problem by setting ao=esd in /etc/mplayerplug-in.conf. I am not too sure of the location of this conf file. u might wanna search for it in case u dont find it in /etc.

---

### Post by Mr. Electric Wizard on 2005-07-27
I think I was misunderstood, Yahoo videos works fine when I cahnge **ao=esd**, but when I go to Apple.com movie trailers, I get the little windows popping up and disappearing.

---

### Post by arnieboy on 2005-07-27
[QUOTE=Mr. Electric Wizard]I think I was misunderstood, Yahoo videos works fine when I cahnge **ao=esd**, but when I go to Apple.com movie trailers, I get the little windows popping up and disappearing.[/QUOTE]
u have not been misunderstood at all. u run yahoo videos with the help of **mplayer** while the videos on [www.apple.com/trailers](www.apple.com/trailers) run with the help of a firefox plugin called mplayerplug-in which helps launch mplayer. I was referring to the conf file of this plugin (not the player itself). My guess is that mplayer is crashing on apple.com trailers because of the conflict between the mplayerplug-in.conf and mplayer.conf files. u need to change to ao=esd in "mplayerplug-in.conf". if u havent installed mplayerplug-in and some other plugin is trying to launch the media files on webpages u shd install mplayerplug-in 2.85 pronto (because its the best). search for the howto on the same forum.

---

### Post by Mr. Electric Wizard on 2005-07-27
gotcha, I'll try it tonight.
thanks!

---

### Post by Mr. Electric Wizard on 2005-07-29
My mplayerplug-in.conf:

```
#debug=0
#logfile=$HOME/mpp.log
vo=xv,x11
ao=esd,oss,arts
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
cachesize=1024
#use-mimetypes=0
#enable-real=0
#enable-wm=1
#enable-qt=1
#enable-mpeg=1
#enable-ogg=1
#enable-smil=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
```

---

### Post by Mr. Electric Wizard on 2005-07-29
Ok, this is really wierd.
The trailers page will come up fine and all is good, trailers play using mplayerplug-in fine. ([www.apple.com/trailers](www.apple.com/trailers))
but for some reason [www.apple.com/quicktime](www.apple.com/quicktime) freaks out on me?
Very strange, the /quicktime page does not even have any videos playing on it?

---

### Post by arnieboy on 2005-07-29
[QUOTE=Mr. Electric Wizard]Ok, this is really wierd.
The trailers page will come up fine and all is good, trailers play using mplayerplug-in fine. ([www.apple.com/trailers](www.apple.com/trailers))
but for some reason [www.apple.com/quicktime](www.apple.com/quicktime) freaks out on me?
Very strange, the /quicktime page does not even have any videos playing on it?[/QUOTE]
The reason why its freaking out is because [www.apple.com/quicktime](www.apple.com/quicktime) needs quicktime 6.5 installed which currently is only available for windows. mplayer can handle quicktime media files but not all formats (some of them graphical).. hence this problem I think.. I havent used my ubuntu box in a week but shd be able to report back to u on sunday with some possible solution if i face the same problem when i get back home.

---

### Post by wh0rd on 2005-08-15
i really missed watching launch vidoes. 

arnieboy & thechitowncubs thanks a lot guys.

---

### Post by thechitowncubs on 2005-08-16
[QUOTE=wh0rd]i really missed watching launch vidoes. 

arnieboy & thechitowncubs thanks a lot guys.[/QUOTE]
 glad i could help

---

### Post by arnieboy on 2005-08-16
[QUOTE=wh0rd]i really missed watching launch vidoes. 

arnieboy & thechitowncubs thanks a lot guys.[/QUOTE]
enjoy!
-arnieboy

---

### Post by WebbyBabe on 2005-08-31
[QUOTE=arnieboy]Tested and confirmed. This works. 
For all u out there who want to play launchcast videos in **firefox** merely by clicking on the video: first make sure u have mplayerplug-in 2.85 installed. If its not there, follow this HOWTO:
[http://ubuntuforums.org/showthread.php?t=44560](http://ubuntuforums.org/showthread.php?t=44560)
Then go to the following link in **firefox**
[http://www.extensionsmirror.nl/lofiversion/index.php/t3137.html](http://www.extensionsmirror.nl/lofiversion/index.php/t3137.html)
and click on "install"
After the extension gets installed restart firefox and enjoy the launchcast videos merely by clicking on them.[/QUOTE]

Thanks! :grin:

---

### Post by berserker on 2005-09-26
[QUOTE=berserker]I got the Yahoo! videos to work with mplayer and mplayerplug-in 3.11 that I compiled myself along with the Play Launch 0.2.4 plugin.[/QUOTE]

The Play Launch 0.2.4 plugin no longer works.  

Go to [http://gc-group.dk/play-launch/](http://gc-group.dk/play-launch/) to install 0.2.5.

---

### Post by arnieboy on 2005-09-26
[QUOTE=berserker]The Play Launch 0.2.4 plugin no longer works.  

Go to [http://gc-group.dk/play-launch/](http://gc-group.dk/play-launch/) to install 0.2.5.[/QUOTE]
gee thanks dude. the updated ext works like charm :)

---

### Post by sunshine82 on 2005-10-12
it DIDNOT  work for me i did exactly how u said. it still give the error:


To use this application with Netscape, you must use a 4.7x or 7.1 version. Download now.

Please use the following error code when writing to Yahoo! Help. (Error Code: 12)

---

### Post by sunshine82 on 2005-10-12
sORRY My mistake it does work it end up in sounds tab i did not realize that where i had to go use it.


sorry it cool..:cool: :KS

---

### Post by arnieboy on 2005-10-12
[QUOTE=sunshine82]sORRY My mistake it does work it end up in sounds tab i did not realize that where i had to go use it.


sorry it cool..:cool: :KS[/QUOTE]
peace :)

---

### Post by sunshine82 on 2005-10-12
sORRY My mistake it does work it end up in sounds tab i did not realize that where i had to go use it.


sorry it cool..:cool: :KS

---

### Post by christooss on 2005-10-23
Hm where can I find Movie ID

---

### Post by christooss on 2005-10-23
Never mind my question I completly read this forum and I saw that I have to install Play-launch

Thank you guys

---

### Post by minh on 2005-10-23
hi,
i've tried your command, but there's an error
> 05 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP/XP-M Barton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for Debian.


86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
choosen bandwidth 300, mms protocol

---

### Post by moe2da on 2005-10-23
I'm not sure if you guys know about this, but you can add this plug-in to firefox and view most of the videos from Launch.  I just tried it.  Let me know if you had any luck.

[http://gc-group.dk/play-launch/](http://gc-group.dk/play-launch/)

---

### Post by jchaparr on 2005-10-29
OK. I've been using the super cool program by chitown up until today. Then it just didn't work. Looks kinda like yahoo changed their structure for getting the videos or something. I don't really know. Should I change something in the program or try to move to the pluggins people keep mentioning?

---

### Post by bmk789 on 2005-10-30
What repository do I need for getting mplayer?  It's not in my list.

---

### Post by christooss on 2005-10-30
multiverse

---

### Post by berserker on 2005-11-10
[Play Launch]("http://gc-group.dk/play-launch/") no longer works as the maintainer is tired of keeping up with Yahoo's changes.

Go [here]("http://www.pooyak.com/p/pklaunch/") for an alternate method.

---

### Post by rykel on 2005-12-16
hi, mine isn't working... it installed OK, then it asked me for music ID. i gave it the ID, then it asked me for default speed (300) and type (mms). after i said Yes to both options, the program simply disappears. no mplayer, no nothing.

please advise?

---

### Post by manicka on 2005-12-29
I get this error message. I'm using a cvs version of mplayer

```
This codecs.conf is too old and incompatible with this MPlayer release! at line 6
```

---

### Post by vladuz976 on 2006-02-13
i get an error message saying that i at least need netscape 7.1 for this to work

---

### Post by Pinoy915 on 2006-03-09
How do I uninstall this? I'm on xubuntu and menu editing is a bit tricky.

---

### Post by Pinoy915 on 2006-03-09
Nevermind, I just figured it out. Disregard the question I posted.

---

### Post by super on 2006-03-13
i am wondering if anyone has figured out a way to steam the videos to file rather than playing them using the greasemonkey pklaunch script

---

### Post by venky80 on 2006-04-19
how do u uninstall this script

---

### Post by balloons on 2006-07-09
to "uninstall" type this at console

```
sudo rm /user/bin/yahoo
```

---

### Post by H.E. Pennypacker on 2006-09-16
The Greasemonkey script works well, at least for me.  Use these instructions to get Launch.com to work:

Why do all this when you can follow the following instructions:

1.  Install Greasemonkey.
2.  Install [http://www.pooyak.com/p/pklaunch/pklaunch-0.8.1.user.js](http://www.pooyak.com/p/pklaunch/pklaunch-0.8.1.user.js).  Just click on the link, and Greasemonkey will know what to do, and will ask you if you want to install it.  Install it.
3.  Go to Launch.com, and watch any video.

I am telling Yahoo to play nice or people will look for alternatives.  They should be flattered we're using their website.

Thanks go to this website:

[http://buhsnarf.net/wordpress/2006/01/06/howto-play-launchcom-music-videos-in-firefox/](http://buhsnarf.net/wordpress/2006/01/06/howto-play-launchcom-music-videos-in-firefox/)

Note these instructions may only work for certain version of Firefox.  Try anyway.

---

### Post by iseebluuue on 2006-09-28
i have greasemonkey installed and pklaunch installed as well. however, when i go to view a video on yahoo! the new window pops up ready to load the video (which is further than i was getting before i installed pklaunch) but then firefox says i'm missing a plugin, but it can't determine what the missing plugin is. i can view other wmvs just fine, so that's not what's missing. any ideas what the missing plugin might be?

---

