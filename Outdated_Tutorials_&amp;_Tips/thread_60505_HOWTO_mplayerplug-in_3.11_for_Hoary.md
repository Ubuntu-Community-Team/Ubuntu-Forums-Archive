---
title: "HOWTO: mplayerplug-in 3.11 for Hoary"
date: 2005-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by christooss on 2005-08-28
[SIZE=4]**How to install new version of mplayerplug-in under Hoary and Breezy**[/SIZE]

[SIZE=3]0.0 Preinstallation[/SIZE]
0.0.1 Remove any of your mplayerplug-in
If you compiled it.
```
dpkg -r mplayerplug-in
```
or if you apt-get it
```
sudo apt-get remove mozilla-mplayer
```
0.1 Hoary
Make sure that you have all extra repositories in your sources.list
Just to be surtain check if w32codecs and mplayer are installed

0.2 Breezy

You have to enable multiverse repositories

0.2.1 Mplayer
add folowing line in-to /etc/apt/sources.list
```
deb http://si.archive.ubuntu.com/ubuntu breezy multiverse
```
Than install mplayer
```
sudo apt-get instal mplayer-586
sudo apt-get install mplayer-fonts
```
0.2.2 W32codecs
Download package from marillat repositories. I know that this in not best solution but...
```
wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb 
```
Install them with
```
 dpkg -i w32codecs_20050412-0.0_i386.deb
```
0.2.3 gettext
You need this when compiling. Make command needs msgfmt and gettext has this included
```
sudo apt-get install gettext
```

[SIZE=3]1. Installation[/SIZE]

1.1 Grab latest mplayerplug-in source from here:
```
wget http://heanet.dl.sourceforge.net/sourceforge/mplayerplug-in/mplayerplug-in-3.11.tar.gz
```

1.2 Untar the mplayerplug-in source
```
tar -xvzf mplayerplug-in-3.11.tar.gz
``` 

1.3 Prepare dependencies for the build:
```
sudo apt-get install firefox-dev libxpm-dev libgtk2.0-dev build-essential checkinstall

```

1.4 Grab gecko-sdk from here:
```
wget http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.8/gecko-sdk-i686-pc-linux-gnu-1.7.8.tar.gz
```

1.5 Untar gecko-sdk:
```
tar -xvzf gecko-sdk-i686-pc-linux-gnu-1.7.8.tar.gz
``` 

1.6 Compile mplayerplug-in:
```
cd mplayerplug-in
./configure --with-gecko-sdk=../gecko-sdk
make
sudo checkinstall -D

```
1.7.1 This step is my conclusion and I don't know if its tru but it includes some xpt files which you cp with 1.8 step so...

At first prompt press enter. Than tipe YES if you want a list of files which will be included in packages. You exit with q. Than installation program asks you if you want these files included tipe YES. Its smart to include them beacause you don't have to do 1.8 step. If you choose no than don't skip 1.8 step.
1.7.2 Press enter at each prompt until you get to "Enter a number to change any of them or press ENTER to continue:"
5.1 Type "3" without quotes. Press Enter.
5.2 Type "3.11" without quotes. Press Enter
5.3 Press Enter again.

1.8 the "make install" (**you should remove the old mozilla-mplayer package prior this step!**)
```
sudo cp mplayerplug-in*.so /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components
sudo cp mplayerplug-in.types /etc
sudo cp mplayerplug-in.conf /etc
``` 

1.9 Prepare the config file:
```
sudo gedit /etc/mplayerplug-in.conf
```

Edit it like this:
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
As you see we've changed "vo" to "xv,x11", "ao" to "esd,oss,arts" and "cachesize" to "1024".

1.10 Restart Firefox and there you are!!!

Based on [Drigloi's post](http://ubuntuforums.org/showpost.php?p=229950&postcount=1)

---

### Post by eivind on 2005-08-28
Hm. Adding backports repositories and using apt-get seems simpler - I've just used the howto on [www.ubuntuguide.org](www.ubuntuguide.org), and it has done the trick for watching videos within Firefox.

Cheers,

Eivind

---

### Post by arnieboy on 2005-08-28
[QUOTE=eivind]Hm. Adding backports repositories and using apt-get seems simpler - I've just used the howto on [www.ubuntuguide.org](www.ubuntuguide.org), and it has done the trick for watching videos within Firefox.

Cheers,

Eivind[/QUOTE]
with apt-get u will get an old version of mplayerplug-in. The objective of this HowTo is to get the latest version. It has a lot of bugfixes and improvements.

---

### Post by monkey89 on 2005-08-31
Meh.  I'm copying this from the other post, but this way you build off of firefox instead of mozilla and reduce some cludge and bloat.
> 
I made a few changes to the above instructions, and 3.05 works on breezy now, and these instructions are probably good for hoary too (and make things, IMO, a little cleaner)

1. Add the hoary-extras repository from backports. This is where I got w32codecs.
2. sudo apt-get update
3. sudo apt-get install mplayer-586 (or 386 if you're on an older computer) w32codecs
4. sudo apt-get install firefox-dev libxpm-dev libgtk2.0-dev build-essential checkinstall

(as you can see, instead of using mozilla-dev and needing to install the whole huge mozilla web browser, this builds the plug in off of firefox, which should already be installed)

5. Download the 3.05 tar.gz as mentioned above, unpack it wherever, and enter the directory where it is unpacked.
6. To get it to use firefox instead of mozilla, do this: sed -i -e "s|mozilla-plugin|firefox-plugin|" configure (special thanks to the ebuild in gentoo's bugzilla for this idea)
7. ./configure
8. make
9. sudo checkinstall -D, do it like above where you only change the version number.
10. Then the package should be installed properly, I don't see a need to add anything to ~/.mozilla/plugins.

Hope this helps,
-Monkey


---

### Post by christooss on 2005-09-01
[QUOTE=monkey89]Meh.  I'm copying this from the other post, but this way you build off of firefox instead of mozilla and reduce some cludge and bloat.[/QUOTE]
 This helps alot

Thanks. I will think how to put it in to HOWTO

---

### Post by jeremytaylor on 2005-09-02
hi there,
I went through these instructions and everything seemed to work but now when I try to go to the apple/trailers site it tells me additional plugins are needed. 

what have i messed up?

thanks
Jeremy

---

### Post by arnieboy on 2005-09-02
[QUOTE=jeremytaylor]hi there,
I went through these instructions and everything seemed to work but now when I try to go to the apple/trailers site it tells me additional plugins are needed. 

what have i messed up?

thanks
Jeremy[/QUOTE]
do u have win32codecs installed?
do a:
```
sudo apt-get install win32codecs
```
and restart your browser again.

---

### Post by jeremytaylor on 2005-09-02
i have w32codecs installed... is that what you meant?

---

### Post by arnieboy on 2005-09-02
[QUOTE=jeremytaylor]i have w32codecs installed... is that what you meant?[/QUOTE]
yeah thats correct. I spelt the package wrong. do a > about:plugins in firefox browser navigation toolbar and see if the mplayerplug-in shows up or not. also make sure u dont have some other plugin which is trying to play quicktime files ABOVE mplayerplug-in. if u find any let me know.

---

### Post by WebbyBabe on 2005-09-03
I get the following error when i type sudo apt-get install mozilla-dev libxpm-dev libgtk2.0-dev build-essential checkinstall:

Errors were encountered while processing:
 xdm
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do I need to do?

---

### Post by WebbyBabe on 2005-09-03
Okay, i figured out that what i had to do was uninstall xdm and reinstall, but now I get this error when I type 'make'

cp Source/nsIScriptableMplayerPlugin.xpt mplayerplug-in-gmp.xpt
make -C po
make[1]: Entering directory `/home/webby/mplayerplug-in/po'
msgfmt -o da.mo da.po
make[1]: msgfmt: Command not found
make[1]: *** [da.mo] Error 127
make[1]: Leaving directory `/home/webby/mplayerplug-in/po'
make: *** [languages] Error 2
 ](*,)

---

### Post by arnieboy on 2005-09-03
[QUOTE=WebbyBabe]Okay, i figured out that what i had to do was uninstall xdm and reinstall, but now I get this error when I type 'make'

cp Source/nsIScriptableMplayerPlugin.xpt mplayerplug-in-gmp.xpt
make -C po
make[1]: Entering directory `/home/webby/mplayerplug-in/po'
msgfmt -o da.mo da.po
make[1]: msgfmt: Command not found
make[1]: *** [da.mo] Error 127
make[1]: Leaving directory `/home/webby/mplayerplug-in/po'
make: *** [languages] Error 2
 ](*,)[/QUOTE]
do this:
```
sudo apt-get install xview-clients
```
and try again

---

### Post by WebbyBabe on 2005-09-03
Nope. I still get the same error when typing make. ](*,)

---

### Post by jeremytaylor on 2005-09-03
hi again,
```
about:plugins
``` lists mplayer but doesn't have in associated with quicktime movies. Any suggestions?
thanks for the help
Jeremy

---

### Post by jeremytaylor on 2005-09-03
ahah! figured it out. Needed to copy all the .so and .xpt files to the plugins and components directory.

i.e. 
replace the commands
```

sudo cp mplayerplug-in.so /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in.xpt /usr/lib/mozilla-firefox/components
sudo cp mplayerplug-in.types /etc
sudo cp mplayerplug-in.conf /etc
```

with 

```

sudo cp mplayerplug-in.*so /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components
sudo cp mplayerplug-in.types /etc
sudo cp mplayerplug-in.conf /etc
```

thanks for all the help.... it's so much better than the old mplayer plugin!

jeremy

---

### Post by jeremytaylor on 2005-09-03
me again....sigh
for some reason the video runs far too fast, the audio stream seems fine.
any suggestions?
jeremy

---

### Post by WebbyBabe on 2005-09-03
Can anyone help me? Why doi I keep getting this error?

cp Source/nsIScriptableMplayerPlugin.xpt mplayerplug-in-gmp.xpt
make -C po
make[1]: Entering directory `/home/webby/mplayerplug-in/po'
msgfmt -o da.mo da.po
make[1]: msgfmt: Command not found
make[1]: *** [da.mo] Error 127
make[1]: Leaving directory `/home/webby/mplayerplug-in/po'
make: *** [languages] Error 2

I even went as far as uninstalling and reinstalling Breezy. ](*,)

---

### Post by arnieboy on 2005-09-03
[QUOTE=WebbyBabe]Can anyone help me? Why doi I keep getting this error?

cp Source/nsIScriptableMplayerPlugin.xpt mplayerplug-in-gmp.xpt
make -C po
make[1]: Entering directory `/home/webby/mplayerplug-in/po'
msgfmt -o da.mo da.po
make[1]: msgfmt: Command not found
make[1]: *** [da.mo] Error 127
make[1]: Leaving directory `/home/webby/mplayerplug-in/po'
make: *** [languages] Error 2

I even went as far as uninstalling and reinstalling Breezy. ](*,)[/QUOTE]
do a:
```
sudo apt-get install gettext
```
and then do a configure and make again.
gettext contains msgfmt which make cannot find in your compilation.

---

### Post by WebbyBabe on 2005-09-03
thanks! That got rid of the error, but the videos won't play after the install. I restarted firefox and had no luck.

---

### Post by arnieboy on 2005-09-03
[QUOTE=WebbyBabe]thanks! That got rid of the error, but the videos won't play after the install. I restarted firefox and had no luck.[/QUOTE]
follow step 8 in the HowTo .

---

### Post by WebbyBabe on 2005-09-03
I found out what the problem is. It's trying to play the videos with totem-xine instead of the mplayer plugin. Don't know how to fix this problem though.  ](*,)

---

### Post by WebbyBabe on 2005-09-03
I finally got it working.  ](*,) Whoo. I just had to install the mozilla mplayer even though the hot to tells me to remove it.

---

### Post by arnieboy on 2005-09-03
[QUOTE=WebbyBabe]I found out what the problem is. It's trying to play the videos with totem-xine instead of the mplayer plugin. Don't know how to fix this problem though.  ](*,)[/QUOTE]
remove the plugin which uses totem xine from the plugins folder in firefox

---

### Post by WebbyBabe on 2005-09-03
Okay, i removed it. It helped increase the speed of the video and make the speed normal. :) thanks!

---

### Post by arnieboy on 2005-09-03
[QUOTE=WebbyBabe]I finally got it working.  ](*,) Whoo. I just had to install the mozilla mplayer even though the hot to tells me to remove it.[/QUOTE]
mozilla-mplayer is the older version of the mplayer plugin. if u installed that, u basically defeated the whole purpose of configuring and installing the newer version. so what that means is that the older version of mplayer overwrote the files that u copied on to the plugins directory in mozilla.

---

### Post by jeremytaylor on 2005-09-04
arghh this is really annoying me. Some videos seem to play fine others at about double speed, much as this was amusing at first it is wearing a little thin,
Are there any settings in mplayer-plugin that control this?
jeremy

---

### Post by arnieboy on 2005-09-04
[QUOTE=jeremytaylor]arghh this is really annoying me. Some videos seem to play fine others at about double speed, much as this was amusing at first it is wearing a little thin,
Are there any settings in mplayer-plugin that control this?
jeremy[/QUOTE]
gime me an example of a website where u see the plugin playing it at double speed.

---

### Post by jeremytaylor on 2005-09-04
well for example just on the apple trailers site

[http://www.apple.com/trailers/universal/doom/large.html](http://www.apple.com/trailers/universal/doom/large.html)

plays fine

but....

[http://www.apple.com/trailers/independent/wherethetruthlies.html](http://www.apple.com/trailers/independent/wherethetruthlies.html)

plays at a silly speed (audio still at the correct speed)

jeremy

---

### Post by arnieboy on 2005-09-04
[QUOTE=jeremytaylor]well for example just on the apple trailers site

[http://www.apple.com/trailers/universal/doom/large.html](http://www.apple.com/trailers/universal/doom/large.html)

plays fine

but....

[http://www.apple.com/trailers/independent/wherethetruthlies.html](http://www.apple.com/trailers/independent/wherethetruthlies.html)

plays at a silly speed (audio still at the correct speed)

jeremy[/QUOTE]
please paste the contents of the following:
/etc/mplayerplug-in.conf

---

### Post by jeremytaylor on 2005-09-04
oh crap. sorry for wasting your time. Just figured out that when fixing another problem i'd over written the plugin.conf file with something else. grrr.

using the settings suggested in the very first post all works fine.

well thanks for idenitifying my problem, or rather the evidence of my stupidity  O:) 

jeremy

---

### Post by Caboto on 2005-09-05
[QUOTE=christooss]
8. the "make install" (**you should remove the old mozilla-mplayer package prior this step!**)
```
sudo cp mplayerplug-in.*so /usr/lib/mozilla-firefox/plugins
sudo cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components
sudo cp mplayerplug-in.types /etc
sudo cp mplayerplug-in.conf /etc
``` 
[/QUOTE]
That's not correct. the first line needs to be corrected a bit. It has to be mplayerplug-in-*.so. The complete line:
```
sudo cp mplayerplug-in-*.so /usr/lib/mozilla-firefox/plugins
```
After changing this line, everything worked like a charme. Finally I've got a working GUI. It's just beautiful...
Big thanks for all who worked at this how-to!

---

### Post by christooss on 2005-09-06
[QUOTE=Caboto]That's not correct. the first line needs to be corrected a bit. It has to be mplayerplug-in-*.so. The complete line:
```
sudo cp mplayerplug-in-*.so /usr/lib/mozilla-firefox/plugins
```
After changing this line, everything worked like a charme. Finally I've got a working GUI. It's just beautiful...
Big thanks for all who worked at this how-to![/QUOTE]
 Caboto Thanks for reporting a mistake. I changed the line

---

### Post by BoomShake007 on 2005-09-10
QuickTime Plug-in 6.0

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes

mplayerplug-in 3.05

    File name: mplayerplug-in.so
    mplayerplug-in 3.05

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes

When I go to that apple.com/trailers and try to view one, it says it loads then says "playing filename", but nothing is actually playing.  No "get plugin" error or anything, w32codecs installed.

---

### Post by christooss on 2005-09-10
Try to exit the page and than visit it again. movie stays in tmp dir and it will load than corectly. i think :)

It works with me if one of the films doesn't play corectly

---

### Post by Vidar on 2005-09-10
By the way, it seems the w32codecs-package is no longer avaliable in the hoary repositories...

---

### Post by BoomShake007 on 2005-09-10
[QUOTE=christooss]Try to exit the page and than visit it again. movie stays in tmp dir and it will load than corectly. i think :)

It works with me if one of the films doesn't play corectly[/QUOTE]
 nope, still doesn't work

---

### Post by randcoop on 2005-09-15
I took a different approach.  Downloaded the mozilla-mplayer deb package from Debian unstable.  Ran dpkg -i mozilla-mplayer*.deb as root.

Now I have mplayerplug-in 3.05 working on Firefox.

---

### Post by carney1979 on 2005-09-20
With the Apple links provided above, I get video but no sound. I followed all the steps. I am running a Breezy system that is up to date.

If I try to watch any videos from CNN ([http://www.cnn.com/)]("http://www.cnn.com/%29"), all I get is about 3-4 words (so sound is working somewhat) and no video. Then all playback stops.

Any ideas?? ](*,)

David

---

### Post by arnieboy on 2005-09-20
[QUOTE=carney1979]With the Apple links provided above, I get video but no sound. I followed all the steps. I am running a Breezy system that is up to date.

If I try to watch any videos from CNN ([http://www.cnn.com/)]("http://www.cnn.com/%29"), all I get is about 3-4 words (so sound is working somewhat) and no video. Then all playback stops.

Any ideas?? ](*,)

David[/QUOTE]
do a :
```
sudo apt-get install w32codecs

```and try again

---

### Post by christooss on 2005-09-21
Vreezy don't have a w32codecs :P

You can try intalling them from hoary backports repozitories.

add them to sources.list and than sudo apt-get update and sudo apt-get install w32codecs.

---

### Post by Pheylan on 2005-09-21
**Having trouble installing the mplayer plugin.  when I run checkinstall I am getting**



checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
mkdir: cannot create directory `/usr/share/doc/mplayerplug-in': Permission denied

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

**Any idea of what is happening here?**

---

### Post by jeremytaylor on 2005-09-21
are you doing 
```
sudo checkinstall
```
jeremy

---

### Post by carney1979 on 2005-09-21
Can't thank you enough! Online video clips are here again!

Any way to increase brightness a bit?

David

---

### Post by Pheylan on 2005-09-21
Ok "sudo checkinstall - D" worked like a charm
However, now whenever I go to play embedded media it will not bring it up for me.  It says downloading and such but then is comes up with a gray screen and will not play the movie even though it says playing.

Have tried Quicktime at Apple's movie trailer site and Media player clips via Eve-Onlines newest movie.

Anyidea why these are not playing?

URL for wmv media = [http://ccp.vo.llnwd.net/o2/video/2/EVENeverFadesLarge.wmv](http://ccp.vo.llnwd.net/o2/video/2/EVENeverFadesLarge.wmv)

URL for quicktime media = [http://movies.apple.com/movies/miramax/the_warrior/the_warrior_m320.mov](http://movies.apple.com/movies/miramax/the_warrior/the_warrior_m320.mov)

Other then this everything else went fine no erros or anything.

---

### Post by jeremytaylor on 2005-09-22
Did you remember to edit you
```
/etc/mplayerplug-in.conf
``` 
file as described in post one of this thread? I had similar  problems until I set the video output to the right setting. You can also try playing the the video out preferences in mplayer itself to figure out which ones work best for you.
thanks
Jeremy
p.s. the two links you gave both worked for me though the first .wmv file had a lot of artifacts in.

---

### Post by christooss on 2005-09-22
This howto have changed

What has changed?

1. I changed 3.05 version beacause 3.05 is in breezy repositories. I changed version to 3.11
2. Added preinstallation
3. Removed mozilla-dev and added firefox-dev to reduce installation. 40 MB is alot.

So if you find something wrong report please.

Till next version of mplayerplug-in

Bye

---

### Post by christooss on 2005-09-22
Can someone try this package
install it with dpkg -i

[http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

---

### Post by christooss on 2005-09-22
I changed 1.7 step to 1.7.1 and 1.7.2 steps.

---

### Post by Hellaxe on 2005-09-23
Hello everybody:

i've done the how-to but it doesn't work with me.
There's one thing diferent - the firefox-dev wasn't found by the apt-get. The only one finded was mozilla-firefoz-dev.
Can you help me please.

By the way i'm using hoary.

Thanks in advance.

Hellaxe

---

### Post by jrib on 2005-09-23
Your HowTo worked great.  Thank you.

[QUOTE=christooss]
So if you find something wrong report please.
[/QUOTE]

in Step 1.6 can you change "checkinstall -D" to "sudo checkinstall - D".  Took me a few tries to figure that out.  (I should have read the whole thread as it was mentioned earlier on this page but I think it would help others if it was mentioned in the first post).  If it isn't always necessary to sudo then can you make some kind of mention of it?

---

### Post by christooss on 2005-09-24
You can all try instaling this package. Its package which is build at checkinstall. This package is for breezy.

---

### Post by jrib on 2005-09-24
[QUOTE=Hellaxe]Hello everybody:

i've done the how-to but it doesn't work with me.
There's one thing diferent - the firefox-dev wasn't found by the apt-get. The only one finded was mozilla-firefoz-dev.
Can you help me please.

By the way i'm using hoary.

Thanks in advance.

Hellaxe[/QUOTE]


I couldn't find firefox-dev also, instead I installed: **mozilla-firefox-dev**.  That worked fine, but be sure to grab the rest of the packages on that step.

---

### Post by Hellaxe on 2005-10-03
Well guys.........

I´ve done everything, again and compiled, ........again but the result is the same.
It doesn't show the live stream.
Any ideas?????? please.

Ps: If i open the url directly from mplayer i see it perfectly.

---

### Post by christooss on 2005-10-04
Give us a sample of stream.

---

### Post by frodon on 2005-10-04
I never met someone who get live video stream working with mplayer plugin and it seems that nobody can answer to this question, however i can save the video stream but it's not what i expect of a video stream plugin.
Exemple of stream which doen't work : [http://www.abrutis-videos.com/video.php?id=889](http://www.abrutis-videos.com/video.php?id=889).

---

### Post by Hellaxe on 2005-10-04
[QUOTE=christooss]Give us a sample of stream.[/QUOTE]

Here is a sample but i think you won't be able to see it because it's my ISP private feed for it's users:

mms://espalhabrasas.sapo.pt/SICradical - 256

I´ve tried also CNN and it doesn't work.

---

### Post by jrib on 2005-10-04
> **Hellaxe]Here is a sample but i think you won't be able to see it because it's my ISP private feed for it's users:
mms://espalhabrasas.sapo.pt/SICradical - 256
I&#180 said:**
> 
The mms:// link is not embedded so mplayer-plugin isn't going to be associated with it.  The cnn videos work fine for me.  Specifically, this one worked: [http://www.cnn.com/video/player/player.html?url=/video/us/2005/10/04/intv.franklin.graham.affl](http://www.cnn.com/video/player/player.html?url=/video/us/2005/10/04/intv.franklin.graham.affl).

[QUOTE=frodon]I never met someone who get live video stream working with mplayer plugin and it seems that nobody can answer to this question, however i can save the video stream but it's not what i expect of a video stream plugin.
Exemple of stream which doen't work : [http://www.abrutis-videos.com/video.php?id=889](http://www.abrutis-videos.com/video.php?id=889).

[http://www.abrutis-videos.com/video.php?id=889](http://www.abrutis-videos.com/video.php?id=889) (NSFW) did not seem to work at first.  However if you right click and press "play" the video will play perfectly.  The ads on that site are NSFW.  Please let people know that ;).

---

### Post by frodon on 2005-10-05
[QUOTE=_jason]click and press "play" the video will play perfectly.  The ads on that site are NSFW.  Please let people know that ;).[/QUOTE]Absolutely not, try it and you will see that doesn't work, also it's not a live video streaming solution, so i'm starting to think that mplayer-plugin is far to be a good live streaming plugin because the link i gave works without any problems with totem and mozplugger.
The problem is not to see the video because you can save it on the disk but to have a live video streamming, i'm looking forward the latest version of totem which will contain an official plugin for video streaming.

However thanks for the input

---

### Post by foxy123 on 2005-10-05
[QUOTE=Hellaxe]Here is a sample but i think you won't be able to see it because it's my ISP private feed for it's users:
mms://espalhabrasas.sapo.pt/SICradical - 256
I´ve tried also CNN and it doesn't work.[/QUOTE]
CNN works fine for me...

---

### Post by jrib on 2005-10-05
[QUOTE=frodon]Absolutely not, try it and you will see that doesn't work, also it's not a live video streaming solution, so i'm starting to think that mplayer-plugin is far to be a good live streaming plugin because the link i gave works without any problems with totem and mozplugger.
[/QUOTE]

I posted my reply after trying; it worked.  Are you using the 3.11 version of the plugin?

---

### Post by frodon on 2005-10-05
I'm not sure maybe 3.10, but wait the end of the download and then press play button is not video streaming and does not fit with what i expect of a video streaming plugin.
So i think i will compile the latest version of totem and use its embedded plugin and will stay open if someone can tell me how to get true video streamming with mplayer-plugin.

---

### Post by smeager on 2005-10-10
I went to update to mplayerplug-in 3.11 and complied and installed without a hitch. The problem is that when I do an about:plugins I still have the 2.85 version listed. I went through and physically removed every plugin and its still there. My question is how do I remove the mplayerplug-in 2.85 so I can use the 3.11 version (whenever I open a streaming media file the 2.85 runs and not the 3.11 one). This is how it looks in firefox

QuickTime Plug-in 6.0, Windows Media Player Plugin are supported by mplayerplug-in

    File name: mplayerplug-in.so
    mplayerplug-in 2.85

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using X Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
video/x-ms-asf-plugin 	Windows Media 	asf,asx 	Yes
video/x-msvideo 	AVI 	avi 	Yes
video/msvideo 	AVI 	avi 	Yes
application/x-mplayer2 	WMV 	wmv 	Yes
video/x-ms-wm 	MSNBCPlayer 	asf 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv 	Yes
video/x-ms-asf 	MS ASF video 	asf,asx 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv 	Yes
video/x-ms-wmp 	Windows Media 	wmp 	Yes
video/x-ms-wvx 	Windows Media 	wvx 	Yes
audio/x-ms-wax 	Windows Media 	wax 	Yes
audio/x-ms-wma 	Windows Media 	wma 	Yes
application/x-drm-v2 	Windows Media 	asx 	Yes
audio/wav 	Microsoft wave file 	wav 	Yes
audio/x-wav 	Microsoft wave file 	wav 	Yes
application/smil 	SMIL 	smil 	Yes
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
Google VLC multimedia plugin 1.0

    File name: mplayerplug-in-gmp.so
    mplayerplug-in 3.11

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using X Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/x-google-vlc-plugin 	Google Video 		Yes
QuickTime Plug-in 6.0

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.11

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using X Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.11

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using X Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.11

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using X Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes

---

### Post by smeager on 2005-10-10
Never mind I figured it out.

---

### Post by Hellaxe on 2005-10-14
[QUOTE=_jason]The mms:// link is not embedded so mplayer-plugin isn't going to be associated with it.  The cnn videos work fine for me.  Specifically, this one worked: [http://www.cnn.com/video/player/player.html?url=/video/us/2005/10/04/intv.franklin.graham.affl](http://www.cnn.com/video/player/player.html?url=/video/us/2005/10/04/intv.franklin.graham.affl).[quote]

Well still not working.
I'm getting without ideas.
Any help?


[COLOR="DarkRed"]EDIT: Solved. i&#180;ve copied the plugins to the ~./mozilla/plugins directory and then it worked perfectly.[/COLOR]

---

### Post by bionnaki on 2005-11-16
thanks for this HOWTO. worked great.

---

### Post by CHUCKYCHUCK on 2005-12-28
Hi ! Can anyone read without bugs the High-Definition Trailers on apple website ?
With standards trailers i have no problems, but with HD Trailers, the loading hangs on at 99% ...

thanks

---

### Post by foxy123 on 2005-12-29
same here, never was able to watch HD trailers...

---

