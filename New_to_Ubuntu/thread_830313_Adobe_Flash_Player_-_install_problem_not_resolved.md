---
title: "Adobe Flash Player - install problem not resolved"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Johnnie_Walker on 2008-06-15
I've read tons of threads about installing this stuff, but none of it helped. Most of them tell it is installed, but it is either messed up or missing. I reckon that the closest to success method is this one:
> In order to obviate to this problem, it will be possible to install from finishes them Flash Player 9 typing these 4 commandos:

```
TAILS:

   1.
      wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
   2.
      tar zxvf install_flash_player_9_linux.tar.gz
   3.
      cd install_flash_player_9_linux
   4.
      I sudo ./flashplayer-installer
```

One will set off in finishes them the procedure of installation of player the Flash. To the demand for the distance of the browser firefox to insert like path /usr/lib/firefox.

Adobe Flash Player 9 will be installed in the following directory:
Browser installation directory = /usr/lib/firefox
Proceed with the installation? (y/n/q): y
Installation complete.
The installation is completed. Al riavvio of browser the flash player would have to work correctly.

It is all fine until the console shows one of the messages:
> Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): *...usr*/lib/mozilla

WARNING: /home/nadelin/install_flash_player_9_linux/*...usr*/lib/mozilla is not a directory.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): home/*...usr*/lib/mozilla

WARNING: /home/*...usr*/install_flash_player_9_linux/home/nadelin/lib/mozilla is not a directory.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): home/*...usr*/lib/firefox

WARNING: /home/*...usr*/install_flash_player_9_linux/home/nadelin/lib/firefox is not a directory.


When I was first asked, which one of the three options for flash player to choose I chose something different from Adobe Flash Player. I guess it was something like the *blue pill* in "The Matrix":). I will know in future that chosing Adobe Flash player, when asked for the first time, is not recommended, but obligatory. 

I hope that the developers will make it possible for us to install somehow Adobe flash player and enjoy flash without reinstalling Firefox this decade. Thanks in advance!

---

### Post by wormser on 2008-06-15
Flash is really easy to install from the repositories.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by st33med on 2008-06-15
You don't need that script. Just go to [www.youtube.com]("www.youtube.com") and view a vid. The bar should drop down and say you need a plugin for this page.

OR, you could do this:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Johnnie_Walker on 2008-06-15
> **wormser said:**
> 

```
sudo apt-get install flashplugin-nonfree
```
As I said, I've tried all this and it doesn't work. Says it is complete, but it is not.

---

### Post by philinux on 2008-06-15
In the firefox address bar type this

```
about:plugins
```

Post the output.

---

### Post by ibuclaw on 2008-06-15
You could to it manually.
cd into the installflashplayer folder and run:
```
sudo cp libflashplayer.so /usr/lib/firefox-3.0/plugins

```
Then reset everyone's pluginreg.dat file.
```
for i in $(sudo locate pluginreg.dat); do rm "$i"; done
```

[EDIT]
If it still doesn't work, check for the existance of the mozilla folder and put it in there too.
```
ls /usr/lib/mozilla/plugins && sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```
and remove the pluginreg.dat files again.

Regards
Iain

---

### Post by kansasnoob on 2008-06-15
Do you have the Medibuntu repo installed?

You can tell just by opening synaptic and clicking settings>repos>third party ................ or just go to software sources and check "third party". BTW I never do "source code" since I got tired of breaking things that i'm not snmart enough to fix.

If no then do so.  

If yes then install:
 acroread
 acroread-escript
 acroread-plugins ---- and 
 mozilla-acroread ---- if you're using Firefox.

You can dl Medibuntu here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Remember the gpg key!

---

### Post by aysiu on 2008-06-15
You keep typing ```
home/...usr/lib/firefox
``` or something like that. Forget the home and all the dot-dot-dots. Type ```
/usr/lib/firefox
``` when asked.

More details here:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by SandmanXC on 2008-06-16
You might try typing **/usr/lib/firefox-3.0**. I did that and it worked, but, after starting FF i still got the message on youtube. Weird. Any other feedback?

---

### Post by Johnnie_Walker on 2008-06-16
All versions of location I've typed and tried don't help. Here is the info about my plugins:
```
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.2, the GNU Flash Player. Copyright © 2006, 2007, 2008 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see http://www.gnu.org/software/gnash. Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by Johnnie_Walker on 2008-06-16
That's ridiculous! I even can't uninstall and re-isnstall Firefox in the standard way to get the nasty player like after the install of ubuntu :mad:. After trying everything I realise that the only possible way is getting another browser, because ubuntu made it impossible to use flash with the best browser to me:(

---

### Post by markbuntu on 2008-06-16
The proper location for flashplayer in Ubuntu Hardy is: 

usr/lib/flashplugin-nonfree/. 

Check in there and see if there is a file called 

libflashplayer.so.

Also check in 

/usr/lib/firefox/plugins 

and see if there is a link called 

flashplugin-alternative.so 

to

etc/alternatives/firefox-flashplugin 

that is a link to 

/usr/lib/flashplugin-nonfree/libflashplayer.so


I know that it is a long way around but that is how firefox looks for flash. 

If you have the libflashplayer.so somewhere else you could just move it to 

usr/lib/flashplugin-nonfree/ 

and it will work. You can make the directory and the links if you need to.

That way updates will work properly.

You could always just put libflashplayer.so in /plugins but that may cause problems for you in the future.

Also, if you have libflashplayer.so in the wrong directory there is a good chance that any other browser like Opera or Epiphany will not be able to find it either.


So, if you already have downloaded flash to somewhere and it is not working for you try the above. If you got flash 10 it should be put in the same place and replace the libflashplayer.so that is already there which is probably flash 9,

---

### Post by Johnnie_Walker on 2008-06-17
10x. I got some progress. At lest I can watch youtube and flashes like this, but some other kind of sites again require flash player, while for others it is working properly. That's strange...

---

### Post by markbuntu on 2008-06-17
There are also a bunch of other links that I forgot to mention yesterday but flash should work anyway without these.

There should be a link folder called plugins in 

usr/lib/firefox3.0 that links to 

usr/lib/firefox-addons

and a link in

usr/lib/firefox-addons /plugins called

link to libflashplayer.so 

that links directly to

/usr/lib/flashplugin-nonfree/libflashplayer.so

If my last post did not help, check for these links also though firefox should find it anyway after you put it in the proper folder.

Some sites may require flash 10 now which should be available soon,

---

### Post by bvidinli on 2008-12-03
i was also unable to remove gnu flash player (gnash),

i managed to remove as follows:


open firefox, 
on address bar: about:plugins

find file name which handles swf, for example  libswfdecmozilla.so for my case,

on console:
 find / -name libswfdecmozilla.so

find that file and delete it..
rm -rvf /usr/lib/swfdec-mozilla

then restart firefox, you have reset it... 
this is way that i found, maybe there is a better way...


this way did not work for me !!:
sudo aptitude remove gnash

---

### Post by Wartooth on 2008-12-09
> **aysiu said:**
> You keep typing ```
home/...usr/lib/firefox
``` or something like that. Forget the home and all the dot-dot-dots. Type ```
/usr/lib/firefox
``` when asked.

More details here:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

Just a note about using this really good tutorial for folks like me who are kind of fumbling around with installing Flash.

I have a brand new installation of 8.10.

I did not get the typical Firefox slide-down prompt that normally tells me there's a plug-in I need to install, I only got the message from YouTube saying that I either didn't have Java enabled (went and took care of that) or needed to download the latest Flash Player.

I started following the above linked tutorial, but made it only to the step where I had to enter an installation path, and was told that /usr/lib/firefox is not a valid installation path. 

Also tried /usr/lib/firefox-3.0 as well as the suggestion in the prompt of /usr/lib/mozilla and got the same message. 

So, I navigated around and found that I had a firefox-3.0.4 folder.  I made /usr/lib/firefox-3.0.4 the installation path, and SUCCESS!  

There is probably an update explaining this somewhere, but since I had come across this thread and was using it and that tutorial to try my hand at manually installing, I figured I'd post something about what actually worked for me in my situation.

Thanks for all the great info, asyiu!

---

### Post by hamlet_42 on 2008-12-12
hello to all of you, 
 
i´m trying since days to install flash on Ubuntu_8.04(!)-Live-CD in all ways described here and elsewhere. Each one of them for several times. As it`s been said, its usually quite simple.
Firefox3beta5 is the Version which is running on my CD, but it doesn`t work for Epiphany or Konqueror either. 

The ones who are using either Intrepid or Hardy since a few months doesn`t seem to have got the problems, so they think: how dump might one be who can`t do that kind of operation.

I have had never no problems in installing Flash nowhere else. Even not with Kubuntu_8.04 a few month ago.

The only way i got it running was by downloading it from adobe copying files in the way described and making use of firefox-2. 

I only wanted to mark that the problem doesn`t seem to exist for all versions, so each idea should work in a brand-new hardy installation too.
It might be a point to think about, but i`m just a one-year-old linux-child and can`t find the solution.:confused: 
Thanks to the gods it`s just a favor for a friend, else i might loose my humor.

have a nice time
hamlet

---

### Post by psycosmyth on 2008-12-12
The last update broke the path for the flashplayer or something.
I have three boxes with 8.04 and all stoped reading flash at the same time. I installed the .deb file from Adobe. Duh, just say you agree not to screw it up and make money from it and it's all yours!
gdeb is handy.

---

### Post by hamlet_42 on 2008-12-13
well, psychosmyth, 
thats a new dimension.
If:
if you tell me how i might make money of it, i will give you any  promise you want. 
 
Else:
sure i won`t. 

greetings,
hamlet

quote johnny_walker:
As I said, I've tried all this and it doesn't work. Says it is complete, but it is not.

quote me:
The ones who are using either Intrepid or Hardy since a few months doesn`t seem to have got the problems, so they think: how dump might one be who can`t do that kind of operation.

At least its a Live-CD or a new installation, as i`ve said.

---

### Post by hamlet_42 on 2008-12-13
hello to all of you, 
at least i cant say what exactly was going wrong, but thats way i got it running, as easy as it is described everywhere:

-i installed ubuntu_8.04 in virtualox and added multi- and universe
 so i could 
-install all the recommended security and hardy updates 
 (! the only thing i didnt do from Live-CD)
- installed the flashplayer from adobe (select Version: .deb for Ubuntu_8.04). 
- not a single problem 

Its  just a guess: any part of the updates must be necessary to get flash running.

Perhaps that info might be useful for someone having this problem, thats why i added it.
(If its true someone might tell it in better words, so that its nice and easy. Sorry im not able to do so)

at least thanks to all of you for all the info everyone has added, 
all of them are very fine for me.

greetings:p
hamlet

---

### Post by psycosmyth on 2008-12-13
Awesome! I have reset my updates to security only now. Hopefully nothing else freaks out.

---

