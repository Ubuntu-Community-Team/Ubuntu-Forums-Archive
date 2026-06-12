---
title: "HOWTO: Win32 Video Codecs"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-10-13
This HOWTO is aimed at all the users of Ubuntu (both 32 and 64bit although wmv9 files don't work in Ubuntu 64bit) and it is useful because win32 codecs aren't available anymore in the repositories for legal reasons.

This guide is a revised version of a guide of mine specifically aimed at 64bit users. I decided to post this new one in order to avoid misunderstandings.

If you want to watch your movies (avi and wmv) or listen to your music files (wma) which require Win32 codecs this is what you need:

1)You have to OWN A LEGAL COPY of Windows, because these are proprietary codecs (somebody correct me if I'm wrong)

2)Install &#8220;xine-ui&#8221; and &#8220;totem-xine&#8221; in Synaptic or type in the command line: 
sudo apt-get install xine-ui ; totem-xine

3) Launch Xine (or Totem) and try to play a video (this will create a .config file)

4) Download the codecs from this website:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the &#8220;essential codecs package&#8221;)

if the link above is temporarily down try this mirror:
[http://www4.mplayerhq.hu/homepage/design7/dload.html]("http://www4.mplayerhq.hu/homepage/design7/dload.html")

5) Open the command line(&#8220;Konsole&#8221; if you are using KDE, &#8220;Terminal&#8221; if you are using GNOME) and follow these steps:

a) Get to the directory where you have downloaded the file (/home/alberto/downloads in my case)

cd /home/alberto/downloads

b) Create the directory in which you are going to put the codecs (/usr/lib/win32) 

sudo mkdir /usr/lib/win32

c) Now, assuming the file you downloaded is &#8220;essential-20050412.tar.bz2&#8221;:

tar -xjvf essential-20050412.tar.bz2 (this will extract the file)

sudo mv essential-20050412/* /usr/lib/win32 (this command will move the files to the desired folder)

d) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!


[COLOR="Red"]NOTE: It seems wmv9 don't work with my HOWTO if you use Ubuntu 64bit.[/COLOR] 

Alberto

---

### Post by emendelson on 2005-10-13
I've got Gxine playing audio .wma files very nicely, following these instructions, but I can't get those .wma files to play in Totem. When I looked at your instructions, I neglected to run Totem before installing the w32 codecs, and I wonder if that was the problem. Do you know where the config file is so that I could try deleting it and starting over???

EDIT: Found the answer: needed to install gstreamer0.8-ffmpeg from universe.

---

### Post by Drakx on 2005-10-13
or add

```
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```

to your sources.list

sudo apt-get update
sudo apt-get install w32codecs

---

### Post by fortytwo on 2005-10-13
When I try to do an update with that repository added, I get:

```
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
```

---

### Post by Stealth-X on 2005-10-13
Grrr [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html) is down!

---

### Post by jarrett.wold on 2005-10-13
Mirror 

[http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2)

---

### Post by BLTicklemonster on 2005-10-13
[QUOTE=jarrett.wold]Mirror 

[http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2)[/QUOTE]

Thank you, I came in here to ask if someone would get a mirror for that.

---

### Post by BLTicklemonster on 2005-10-13
Well, I got them in /usr/lib/win32 but neither totem nor xine will play a dvd

---

### Post by stateq2 on 2005-10-13
you need libdvdcss2
[ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/)

---

### Post by 51mmz0rz on 2005-10-14
Both the first set of directions and the download from the repo didn't do it for me.  Weird because I installed lame and couldn't play mp3 files.  My solution was to install and then uninstall VLC player.  

Now it seems like I can play everything in totem fine, except DVDs.  With libdvdcss DVD playback is a little choppy in totem, watchable but distracting.  In VLC, DVD playback is smooth.

---

### Post by doood81 on 2005-10-14
HOWTO worked fine for me, it's how i've always done it in the past as well. Mplayer used to be my main media player.

A pile of avi's mpeg2/3 I have would play fine but have no audio. However my system was lacking libac52, which does not get installed with previous package dependencies.

my 2cents.

---

### Post by manicka on 2005-10-14
[QUOTE=Drakx]or add

```
deb ftp://ftp.nerim.net/debian-marillat/ sarge main
```

to your sources.list

sudo apt-get update
sudo apt-get install w32codecs[/QUOTE]


We are encouraging people to not use this repo as it will cause serious damage to your system.

to install the w32codecs please download this file

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb)

and install it with

sudo dpkg -i w32codecs_20050412-0unofficialubuntu2_i386.deb


libdvdcss2 can be downloaded here and installed with dpkg in the same way

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)

---

### Post by BLTicklemonster on 2005-10-14
[QUOTE=manicka]We are encouraging people to not use this repo as it will cause serious damage to your system.

to install the w32codecs please download this file

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb)

and install it with

sudo dpkg -i w32codecs_20050412-0unofficialubuntu2_i386.deb


libdvdcss2 can be downloaded here and installed with dpkg in the same way

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)[/QUOTE]

Thank you! Sort of. In Hoary, I had no problems getting my dvd player to work, but in Breezy, I couldn't use it until just now thanks to your post. But I am having the same problem in Breezy as I was having in Hoary, and that is that the dvd is horrible. It is real jumpy. 

VLC is about as confounding a device as I think I have seen yet. 

Can't wait til some resolution comes about.

---

### Post by manicka on 2005-10-14
try totem-xine

---

### Post by manicka on 2005-10-14
As well as trying totem-xine you'll need to have DMA enabled

[http://doc.ubuntu.com/gnome/faqi386/C/ch04.html#id3152618](http://doc.ubuntu.com/gnome/faqi386/C/ch04.html#id3152618)

---

### Post by Jujimufu on 2005-10-14
Worked great! THANKS!

---

### Post by webbie180 on 2005-10-15
Link to libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb
doesnt seems to work.

---

### Post by BLTicklemonster on 2005-10-15
I have totem-xine, and dma is on.

---

### Post by Segovia on 2005-10-15
[QUOTE=BLTicklemonster]I have totem-xine, and dma is on.[/QUOTE]
I've never been very successful playing DVDs with totem-xine, however xine-ui works nicely.

---

### Post by manicka on 2005-10-15
[QUOTE=webbie180]Link to libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb
doesnt seems to work.[/QUOTE]
in what way?

---

### Post by Muhammad on 2005-10-15
The [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html) is down :/

---

### Post by tseliot on 2005-10-15
[QUOTE=Muhammad]The [http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html) is down :/[/QUOTE]
You're right. Try this mirror [http://www4.mplayerhq.hu/homepage/design7/dload.html]("http://www4.mplayerhq.hu/homepage/design7/dload.html")

---

### Post by pelago on 2005-10-15
Maybe the DVD stuff in this thread should be split off into a different thread, to keep this one Win32codes-only.

---

### Post by angrykeyboarder on 2005-10-16
[QUOTE=manicka]We are encouraging people to not use this repo as it will cause serious damage to your system.

to install the w32codecs please download this file

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb)

and install it with

sudo dpkg -i w32codecs_20050412-0unofficialubuntu2_i386.deb


libdvdcss2 can be downloaded here and installed with dpkg in the same way

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)[/QUOTE]

This is the first I've seen of this.  These packages are [b[]very important to most everyone and I would encourage those in the "we" group you mentioned to document these URLs in the Wiki.

With Breezy being just released the "usual sources" of information aren't up to speed as of yet, leaving people hanging.

One of these days I'll follow my own advice and wait 30 days to install a newly released Linux distro when everything is "really" ready.

---

### Post by manicka on 2005-10-16
[QUOTE=angrykeyboarder]
One of these days I'll follow my own advice and wait 30 days to install a newly released Linux distro when everything is "really" ready.[/QUOTE]

Don't forget that you're talking about packages that aren't in the main distro or  supported by Canonical, so you won't see reference to them on the main wiki. Everything on their part was ready to go from day one.

As for the rest (like info on where to get these packages), the community is doing it's best to get everything up to date. Just be patient and use the forums and how-tos. There's lots of people here willing to help. :D

---

### Post by tseliot on 2005-10-16
[QUOTE=angrykeyboarder]With Breezy being just released the "usual sources" of information aren't up to speed as of yet, leaving people hanging.[/QUOTE]

My guide is thought to overcome the problem. The result is the same and it also works with 64bit systems (the package "w32codecs" is available only for 32bit systems).

Now, I don't think my guide is difficult to follow (even for newbies) and the package "w32codecs" can't be included for legal reasons (this has been discussed over and over). This means that there's no reason to complain about Breezy (at least not for the codecs)

I suggest you (and any other user) to follow my guide and enjoy your codecs ;)

---

### Post by angrykeyboarder on 2005-10-16
[QUOTE=manicka]Don't forget that you're talking about packages that aren't in the main distro or  supported by Canonical, so you won't see reference to them on the main wiki. Everything on their part was ready to go from day one.

As for the rest (like info on where to get these packages), the community is doing it's best to get everything up to date. Just be patient and use the forums and how-tos. There's lots of people here willing to help. :D[/QUOTE]

I'm fully aware of all of this, but thanks.

I've not looked at the Wiki in a while, but I recall there has been reference to how to install libdvdcss and w32codecs previously.

The documentation in the Wiki is "user Documentation". Any Tom, Dick or Harry can contribute to it.

I myself, edited a section on Opera recently.

---

### Post by angrykeyboarder on 2005-10-16
[QUOTE=tseliot]My guide is thought to overcome the problem. The result is the same and it also works with 64bit systems (the package "w32codecs" is available only for 32bit systems).

Now, I don't think my guide is difficult to follow (even for newbies) and the package "w32codecs" can't be included for legal reasons (this has been discussed over and over). This means that there's no reason to complain about Breezy (at least not for the codecs)

I suggest you (and any other user) to follow my guide and enjoy your codecs ;)[/QUOTE]

Pardon me,  I'd forgotten about your guide....

I'd actually just installed the files in question from the dreaded Debian-Marillat repository.  I figured everything was cool until I read otherwise a little while ago.

I've since added 
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main
to my sources.list file and replaced the files in question.

---

### Post by angrykeyboarder on 2005-10-16
[quote=manicka]Don't forget that you're talking about packages that aren't in the main distro or supported by Canonical, so you won't see reference to them on the main wiki.[/quote] 

Define "the main wiki".  I'm referring to [this part]("https://wiki.ubuntu.com/UserDocumentation") which any Tom, Dick or Harry can contribute to. 

Here is an example of the kind of stuff I've been referring to:
[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

> Everything on their part was ready to go from day one. 
I wasn't referring to Ubuntu......

> As for the rest (like info on where to get these packages), the community is doing it's best to get everything up to date. Just be patient and use the forums and how-tos. There's lots of people here willing to help. :D 
Like I said, next time I'll take my own advice and wait a month to upgrade...... :-)

---

### Post by manicka on 2005-10-16
OK, I should have said the 'main part' of the wiki :D

The advice on the wiki looks OK. The important part is following the advice in bold type and making sure that the repo is commented out after use (I wouldn't add the cypherfunk repo to my list either if I was new to ubuntu).
Downloading the individual packages and using dpkg avoids that (in this case).

Better still, following tselliot's how-to avoids the whole process completely :)

---

### Post by angrykeyboarder on 2005-10-16
> **manicka]OK, I should have said the 'main part' of the wiki :D[/quote] 
Aah but the main part of the wiki doesn't really have any documentation/howto type stuff (from the Ubuntu folks) per se. :-)

[quote=manicka]The advice on the wiki looks OK. The important part is following the advice in bold type and making sure that the repo is commented out after use (I wouldn't add the cypherfunk repo to my list either if I was new to ubuntu).[/quote] 
True. Mixing repos is never a good idea.  I learned the hard way a year or so ago with Fedora core.  said:**
>  Downloading the individual packages and using dpkg avoids that (in this case). 
True. but I find it's easier to manage the packages if I avoid doing "dpkg -i" as much as possible. I've run into less dependancy issues that way.

---

### Post by manicka on 2005-10-16
Debins may interest you

[http://programmer-art.org/debins](http://programmer-art.org/debins)

---

### Post by Panthios on 2005-10-17
I haven't got (K)Ubuntu to play wmv files (media files that normally requires Windows Media Player).

It worked before on my Debian Testing machine with the w32codecs.

Xine just says that the media is encryptet or scrambled.
Help?? I've done exactly what this guide said.

Anyone who got this working?

---

### Post by tseliot on 2005-10-17
[QUOTE=Panthios]I haven't got (K)Ubuntu to play wmv files (media files that normally requires Windows Media Player).

It worked before on my Debian Testing machine with the w32codecs.

Xine just says that the media is encryptet or scrambled.
Help?? I've done exactly what this guide said.

Anyone who got this working?[/QUOTE]
Try to install "mplayer" (from Synaptic/kynaptic) and use it to play the file

---

### Post by Segovia on 2005-10-17
[QUOTE=Panthios]I haven't got (K)Ubuntu to play wmv files (media files that normally requires Windows Media Player).

It worked before on my Debian Testing machine with the w32codecs.

Xine just says that the media is encryptet or scrambled.
Help?? I've done exactly what this guide said.

Anyone who got this working?[/QUOTE]
I don't have the win32codecs installed and I'm able to play them just fine using Kaffeine (with xine backend instead of GStreamer).  Are you using xine-ui?

---

### Post by Panthios on 2005-10-17
Sorry, it does work! The wmv files I tried out were bad.

Thanks.

---

### Post by DisposableMike on 2005-10-20
Not to insult your intelligence, but be sure to enable DMA on your DVD drive " /sbin/hdparm -d 1 <your device> " to ensure smooth playback.

---

### Post by fut21 on 2005-10-20
W32codec is NOT a problem anymore. Add these serveres, from PLF ubuntu, to your source list:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by manicka on 2005-10-20
PLF have been around for years with mandrake/mandriva.

Now they've started up a Ubuntu repo last week... very interesting

I'd have to say they were a trustworthy source when I used Mandrake, but it's been a while.

---

### Post by fut21 on 2005-10-20
If tou have tecknical skills, and want to spent some time making packages, then PLF ubuntu is a good place to do it.

---

### Post by teaker1s on 2005-11-02
chech out wilki dma
 ENABLE DMA AND IT WILL PLAY SMOOTH

---

### Post by ThomThom on 2005-11-12
Is the Totem Movie Player that's installed by default the same as this Totem-Xine you are talking about?

I've installed the W32codec, but I can't play wma files.

---

### Post by tseliot on 2005-11-12
[QUOTE=ThomThom]Is the Totem Movie Player that's installed by default the same as this Totem-Xine you are talking about?

I've installed the W32codec, but I can't play wma files.[/QUOTE]

Totem-Xine is just an engine which Totem uses.

If Totem-xine doesn't work for you:
Open Synaptic and install "Mplayer"
Then open the file in Mplayer

---

### Post by arnieboy on 2005-11-12
the easiest way to install all codecs and get totem running wma files (and get full multimedia in ur breezy box), run the following:
install and run **[COLOR="Red"][automatix]("http://ubuntuforums.org/showthread.php?t=66563")[/COLOR]**.
install options **1,2,12,13,30**

---

### Post by Aphorism on 2005-11-15
Okie... first the HOWTO has lost the part on adjusting the config file.  Further, it needs to be edited to reflect where those little files are (~/.gnome2/ and .xine respectively)

Now, having said that, I cannot get the blasted totem-xine nor xine to play avi files.  It is still failing with the Indeo 4.1 codec not installed.  Soooo... if anyone can enlighten me, please let me know... 

Here is the sample avi I have been trying to play (which plays fine on 32bit land):

[http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi](http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi)

Thanks for anyone who can shed a little light.

---

### Post by tseliot on 2005-11-15
[QUOTE=Aphorism]Okie... first the HOWTO has lost the part on adjusting the config file.  Further, it needs to be edited to reflect where those little files are (~/.gnome2/ and .xine respectively)[/QUOTE]

That's absolutely true but also absolutely useless. The point is that you have to edit the config file ONLY if you put the codecs in a folder other than the default one, which is /usr/lib/win32.

[QUOTE=Aphorism]Now, having said that, I cannot get the blasted totem-xine nor xine to play avi files.  It is still failing with the Indeo 4.1 codec not installed.  Soooo... if anyone can enlighten me, please let me know... 

Here is the sample avi I have been trying to play (which plays fine on 32bit land):

[http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi](http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi)

Thanks for anyone who can shed a little light.[/QUOTE]

Try this thing (so as to figure out what kind of problem is yours):

```
sudo rm -f /usr/lib/win32
```

Then:

```
sudo gedit /etc/apt/sources.list 
OR 
sudo nano /etc/apt/sources.list)
```

Add the following lines:

```
## FTP mirror from http://free.fr (french ISP)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
```

Then:

```
sudo apt-get update

sudo apt-get install w32codecs
```

Then try to play the file.

---

### Post by Aphorism on 2005-11-15
Tried that. 

I am currently running the amd64 version on the box I am trying to get the codecs to work.  The w32codecs works fine on the 32 bit box, but again, I am trying to get some support in 64 bit land.

Needless to say, the repository in question did not have 64 bit images available.


Thanks for any further help.

---

### Post by tseliot on 2005-11-16
[QUOTE=Aphorism]Tried that. 

I am currently running the amd64 version on the box I am trying to get the codecs to work.  The w32codecs works fine on the 32 bit box, but again, I am trying to get some support in 64 bit land.

Needless to say, the repository in question did not have 64 bit images available.


Thanks for any further help.[/QUOTE]
I have used Ubuntu 64bit for a while and I know that this method is fundamental because no AMD64 package of w32codecs is available.

Please do the following things:

1) ```
cd /usr/lib/win32
ls
```

and post the output

2) Open a supported video file (one which you can play without the codecs)
then:

```
sudo gedit /home/your_username/.xine/config
```

and uncomment (i.e. remove the # before the last line) this part:

```
# path to Win32 codecs
# string, default: /usr/lib/win32
[COLOR="#ff0000"]#decoder.external.win32_codecs_path:/usr/lib/win32[/COLOR]
```

i.e.

make it look like this:

```
# path to Win32 codecs
# string, default: /usr/lib/win32
[COLOR="Red"]decoder.external.win32_codecs_path:/usr/lib/win32[/COLOR]
```

Save the file and exit.

Now try to open the file you had problems with before.

Tell me if it works. In that case I would put this step back to the guide.

---

### Post by Aphorism on 2005-11-16
Nope.

```

The stream 'flame.avi' use an unsupported codec:  Video Codec:  Indeo Video 4.1 (IV41) Start playback anyway?
```

And of course, nothing happens.  Here are the contents of the good old /usr/lib/win32 directory:

```
acelpdec.ax          lhacm.acm                    vdowave.drv
alf2cd.acm           lsvxdec.dll                  vid_3ivX.xa
aslcodec_dshow.dll   m3jp2k32.dll                 ViVD2.dll
atrac3.acm           mi-sc4.acm                   vivog723.acm
atrc.so.6.0          msh261.drv                   vmnc.dll
AvidQTAVUICodec.qtx  msms001.vwp                  voxmsdec.ax
BeHereiVideo.qtx     msscds32.ax                  vp4vfw.dll
CLRVIDDC.DLL         nsrt2432.acm                 vp5vfw.dll
clrviddd.dll         qpeg32.dll                   vp6vfw.dll
cook.so              qtmlClient.dll               vssh264core.dll
CtWbJpg.DLL          QuickTimeEssentials.qtx      vssh264dec.dll
DECVW_32.DLL         QuickTimeInternetExtras.qtx  vssh264.dll
drvc.so              QuickTime.qts                vsslight.dll
dspr.so.6.0          README                       vsswlt.dll
iac25_32.ax          rt32dcmp.dll                 wma9dmod.dll
icmw_32.dll          sipr.so.6.0                  wmadmod.dll
imc32.acm            tm20dec.ax                   wmsdmod.dll
ir41_32.dll          tokf.so.6.0                  wmspdmod.dll
ir50_32.dll          tokr.so.6.0                  wmv9dmod.dll
ivvideo.dll          tsd32.dll                    wmvadvd.dll
jp2avi.dll           tssoft32.acm                 wmvdmod.dll
LCMW2.dll            tvqdec.dll                   wnvwinx.dll
LCODCCMW2E.dll       VDODEC32.dll

```

Thanks for your help.  I have no idea why it is flunking.  Can you make the avi play [http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi](http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi) ?

---

### Post by bored2k on 2005-11-16
Weird, I downloaded the video and it's loading perfectly here. Try the w32codecs from PLF. 

[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/non-free/w32codecs/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/non-free/w32codecs/)

For extra stuff, try installing divx5linux too. [http://www.divx.com/divx/linux/](http://www.divx.com/divx/linux/)

---

### Post by Aphorism on 2005-11-16
Thanks Bored2K, but I am specifically trying to deal with the amd64 distro.

---

### Post by tseliot on 2005-11-17
[QUOTE=Aphorism]Nope.

```

The stream 'flame.avi' use an unsupported codec:  Video Codec:  Indeo Video 4.1 (IV41) Start playback anyway?
```

And of course, nothing happens.  Here are the contents of the good old /usr/lib/win32 directory:

```
acelpdec.ax          lhacm.acm                    vdowave.drv
alf2cd.acm           lsvxdec.dll                  vid_3ivX.xa
aslcodec_dshow.dll   m3jp2k32.dll                 ViVD2.dll
atrac3.acm           mi-sc4.acm                   vivog723.acm
atrc.so.6.0          msh261.drv                   vmnc.dll
AvidQTAVUICodec.qtx  msms001.vwp                  voxmsdec.ax
BeHereiVideo.qtx     msscds32.ax                  vp4vfw.dll
CLRVIDDC.DLL         nsrt2432.acm                 vp5vfw.dll
clrviddd.dll         qpeg32.dll                   vp6vfw.dll
cook.so              qtmlClient.dll               vssh264core.dll
CtWbJpg.DLL          QuickTimeEssentials.qtx      vssh264dec.dll
DECVW_32.DLL         QuickTimeInternetExtras.qtx  vssh264.dll
drvc.so              QuickTime.qts                vsslight.dll
dspr.so.6.0          README                       vsswlt.dll
iac25_32.ax          rt32dcmp.dll                 wma9dmod.dll
icmw_32.dll          sipr.so.6.0                  wmadmod.dll
imc32.acm            tm20dec.ax                   wmsdmod.dll
ir41_32.dll          tokf.so.6.0                  wmspdmod.dll
ir50_32.dll          tokr.so.6.0                  wmv9dmod.dll
ivvideo.dll          tsd32.dll                    wmvadvd.dll
jp2avi.dll           tssoft32.acm                 wmvdmod.dll
LCMW2.dll            tvqdec.dll                   wnvwinx.dll
LCODCCMW2E.dll       VDODEC32.dll

```

Thanks for your help.  I have no idea why it is flunking.  Can you make the avi play [http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi](http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi) ?[/QUOTE]

I can play the avi file but I don't know how to help you. I know you're not the only one to have this problem but I haven't found a solution yet. When I used Ubuntu 64bit this worked on my PC so I fear I can't troubleshoot.

---

### Post by TheCondor on 2005-11-25
Hello people :) 

I read and followed this guide's instructions and I solved some of my problems so far. 

What I wanted to ask though is why whenever i double click on a wmv file i get the following popup box : 

The filename "00017796.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


If I rename the file's extension to asf, it works fine. Also, it works by right clicking on the file, selecting open with and then choosing any media player. Ive had this issue since Warty and I just wanted to know why it happens. Im using Breezy at the moment. 

Thanks in advance for any help :)

---

### Post by tseliot on 2005-11-26
[QUOTE=TheCondor]Hello people :) 

I read and followed this guide's instructions and I solved some of my problems so far. 

What I wanted to ask though is why whenever i double click on a wmv file i get the following popup box : 

The filename "00017796.wmv" indicates that this file is of type "Microsoft WMV video". The contents of the file indicate that the file is of type "Microsoft ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "Microsoft ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


If I rename the file's extension to asf, it works fine. Also, it works by right clicking on the file, selecting open with and then choosing any media player. Ive had this issue since Warty and I just wanted to know why it happens. Im using Breezy at the moment. 

Thanks in advance for any help :)[/QUOTE]
I don't know the reason of the warning. I think it is just a precaution. Don't you worry and enjoy your codecs

---

### Post by TheCondor on 2005-11-26
[QUOTE=tseliot]I don't know the reason of the warning. I think it is just a precaution. Don't you worry and enjoy your codecs[/QUOTE]

Im not worrying, I was just asking if you knew of a possible reason to bypass it thats all. :razz:

---

### Post by madmusiq on 2005-11-30
great HOWTO. It worked the first time for me with no problem.

---

### Post by Aphorism on 2005-12-01
What architecture are you running?  amd64?  I would be interested in what you did if you are...

---

### Post by tseliot on 2005-12-01
[QUOTE=Aphorism]What architecture are you running?  amd64?  I would be interested in what you did if you are...[/QUOTE]
If the question is addressed to me: I used to run Hoary 64bit on my previous computer (and the codecs worked fine) but now I run a 32bit only (mainly because more packages are available for 32bit systems).

---

### Post by duffman25 on 2005-12-10
[QUOTE=tseliot]If the question is addressed to me: I used to run Hoary 64bit on my previous computer (and the codecs worked fine) but now I run a 32bit only (mainly because more packages are available for 32bit systems).[/QUOTE]

Hi

I can't play wma videos with the plf win32codecs package. Does anybody have the same problem?

---

### Post by tseliot on 2005-12-10
[QUOTE=duffman25]Hi

I can't play wma videos with the plf win32codecs package. Does anybody have the same problem?[/QUOTE]
1) Did you install totem-xine?

2) If you did it then try to install "mplayer" from synaptic or kynaptic or adept.
Then right click on the wma file and select "Open with Mplayer" or "Open with other application" and then select "Mplayer"

Tell me if it works

---

### Post by duffman25 on 2005-12-10
[QUOTE=tseliot]1) Did you install totem-xine?

2) If you did it then try to install "mplayer" from synaptic or kynaptic or adept.
Then right click on the wma file and select "Open with Mplayer" or "Open with other application" and then select "Mplayer"

Tell me if it works[/QUOTE]

I'm was using totem-xine with w32codecs from plf. Wma files didn't work. Then I went to mplayer website, downloaded the lastest codec pack & extracted them to /usr/local/lib/win32/ After that wma file worked. So, I assume, the w32codec pack from plf is missing something...

---

### Post by tseliot on 2005-12-10
[QUOTE=duffman25]I'm was using totem-xine with w32codecs from plf. Wma files didn't work. Then I went to mplayer website, downloaded the lastest codec pack & extracted them to /usr/local/lib/win32/ After that wma file worked. So, I assume, the w32codec pack from plf is missing something...[/QUOTE]
I did't get it:razz: . I don't know the reason of the problem (which is weird). Thanks for reporting. I hope we can rely on gstreamer 0.10 on Dapper when it's released and avoid to mess with w32codec too much.

---

### Post by izzydahedgehog on 2005-12-21
Is there a way to get VLC to read these codecs?

I installed all the mplayer codecs into the proper location, and mplayer uses them fine, but I wanted to make it so that I only have to use one media player for everything (and I like VLC more).  Looking in /usr/lib/vlc, I can't find any obvious place where it might be searching.

Thanks!

---

### Post by kaamos on 2005-12-21
[QUOTE=izzydahedgehog]Is there a way to get VLC to read these codecs?

I installed all the mplayer codecs into the proper location, and mplayer uses them fine, but I wanted to make it so that I only have to use one media player for everything (and I like VLC more).  Looking in /usr/lib/vlc, I can't find any obvious place where it might be searching.

Thanks![/QUOTE]
[quote=http://www.videolan.org/]VLC is a free cross-platform media player.

    * It **supports a large number of multimedia formats, without the need for additional codecs**
    * It is available for almost every OS
    * It needs little CPU power
[/quote]
:)

---

### Post by izzydahedgehog on 2005-12-22
Kaamos:

It obviously does need other codecs, because VLC as it stands now won't play .wmv's that mplayer will.  I understand that they probably didn't include these for legal reasons, but I was wondering if there was a way that I could get it to use mplayer's codec package.

---

### Post by tseliot on 2005-12-22
[QUOTE=izzydahedgehog]Kaamos:

It obviously does need other codecs, because VLC as it stands now won't play .wmv's that mplayer will.  I understand that they probably didn't include these for legal reasons, but I was wondering if there was a way that I could get it to use mplayer's codec package.[/QUOTE]
Sorry, I really don't know.

---

### Post by Aphorism on 2005-12-23
Anyone got avi's working on amd64 yet?  If so, I'd love to hear about it...

---

### Post by tseliot on 2005-12-23
[QUOTE=Aphorism]Anyone got avi's working on amd64 yet?  If so, I'd love to hear about it...[/QUOTE]
Only wmv9 don't work on AMD64.  avi files work in 64bit if you follow my guide

---

### Post by linuxninja on 2005-12-23
Thanks for all the info on win32 codecs. :KS

---

### Post by tseliot on 2005-12-23
You're welcome :)

---

### Post by ShirishAg75 on 2005-12-23
Pardon me for barging in like this but does the win32 codecs also include the divx as well as the xvid codecs. I saw in Automatrix 2 different packages for codecs although not sure which one is right.

---

### Post by tseliot on 2005-12-23
[QUOTE=shirishag75]Pardon me for barging in like this but does the win32 codecs also include the divx as well as the xvid codecs. I saw in Automatrix 2 different packages for codecs although not sure which one is right.[/QUOTE]
w32codecs include divx and xvid. However if you want to watch DVDs you have to install libdvdcss.
If you use Automatix you can install both of them. Don't you worry: Automatix just works :)

---

### Post by elemental666 on 2005-12-23
mkay, I got it all working, cept my audio is like 1-3 seconds ahead of the video...

using alsa drivers on a Thinkpad A31...

any suggestions?

---

### Post by tseliot on 2005-12-24
[QUOTE=elemental666]mkay, I got it all working, cept my audio is like 1-3 seconds ahead of the video...

using alsa drivers on a Thinkpad A31...

any suggestions?[/QUOTE]
That's a gstreamer issue.
Please install "xine" and "totem-xine" from synaptic.

---

### Post by kaamos on 2005-12-24
[QUOTE=izzydahedgehog]Kaamos:

It obviously does need other codecs, because VLC as it stands now won't play .wmv's that mplayer will.  I understand that they probably didn't include these for legal reasons, but I was wondering if there was a way that I could get it to use mplayer's codec package.[/QUOTE]

This blog entry has a link to a deb of VLC compiled with wmv9 support, and it worked for me at least. Give it a try.. And sorry for my foolish post earlier.
[http://nanocrew.net/2005/09/01/compiling-vlc/](http://nanocrew.net/2005/09/01/compiling-vlc/)

---

### Post by elemental666 on 2005-12-24
[QUOTE=tseliot]That's a gstreamer issue.
Please install "xine" and "totem-xine" from synaptic.[/QUOTE]

Thanks man, all good now.

---

### Post by gangalee on 2005-12-29
Anyone able to view any of these videos in Hoary or Breezy?- [http://www.muzikmedia.com/videotop.aspx](http://www.muzikmedia.com/videotop.aspx)

---

### Post by Rory on 2005-12-29
.

---

### Post by Rory on 2005-12-29
[QUOTE=gangalee]Anyone able to view any of these videos in Hoary or Breezy?- [http://www.muzikmedia.com/videotop.aspx](http://www.muzikmedia.com/videotop.aspx)[/QUOTE]

Yes, I can view them.  Adding backports and PLF should do the trick for you:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories.3F](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories.3F)

To install codecs, libdvdcss, real player 10 and just about everything else, follow these instructions:
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs.3F](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs.3F)

This is the new Breezy version of the much loved/hated UbuntuGuide.  The difference this time is that ANYONE can made additions/changes to it.  It's turning out to be quite the handy documentation.

Enjoy!!

Rory

---

### Post by aj123 on 2006-01-08
[QUOTE=manicka]We are encouraging people to not use this repo as it will cause serious damage to your system.

to install the w32codecs please download this file

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb)

and install it with

sudo dpkg -i w32codecs_20050412-0unofficialubuntu2_i386.deb


libdvdcss2 can be downloaded here and installed with dpkg in the same way

[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb)[/QUOTE]

I did the steps on a fresh install yet totem cannot play any wmv/mp3 files (no decoders to handle the stream).  So why is that? I don't want to start messing about with the system as that usually means it get's cluttered up and I only have limited hd space.
I even tried reinstalling totem and then installing the w32codecs again. :(

---

### Post by tseliot on 2006-01-09
[QUOTE=aj123]I did the steps on a fresh install yet totem cannot play any wmv/mp3 files (no decoders to handle the stream).  So why is that? I don't want to start messing about with the system as that usually means it get's cluttered up and I only have limited hd space.
I even tried reinstalling totem and then installing the w32codecs again. :([/QUOTE]
install "totem-xine" from Synaptics

---

### Post by aj123 on 2006-01-09
Thank you. It works now. I just wish I understood why.

---

### Post by tseliot on 2006-01-09
[QUOTE=aj123]Thank you. It works now. I just wish I understood why.[/QUOTE]
You were supposed to read the entire guide.

Anyhow Totem-xine is the xine engine for Totem. Xine uses the w32codecs. Gstreamer (the other engine you were using) has its plugins (and codecs are included in its plugins)

---

### Post by dcstar on 2006-02-09
[QUOTE=fut21]W32codec is NOT a problem any more. Add these servers, from PLF ubuntu, to your source list:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)[/QUOTE]
One thing I found on my system installing the w32codec package from this site was that all the codecs were actually installed in /usr/lib/codecs, but my /usr/lib/win32 directory was empty.

As root I deleted /usr/lib/win32 and then manually made a link from that name to /usr/lib/codecs, then it all was fine and Totem (using totem-xine) played all the stuff it should have.

---

### Post by gabbar_singh on 2006-04-04
I have amd64. How do I make it work?

---

### Post by tseliot on 2006-04-05
[QUOTE=gabbar_singh]I have amd64. How do I make it work?[/QUOTE]
The method works also on AMD64. However you won't be able to play wmv9.

---

### Post by cberman on 2006-04-05
Okay, so I got Xine working (its quite nice, and thank you so much -- your kernel compilation and nvidia driver howto's both worked for me). Only issue is totem... it players the video it didn't used to but there's still no sound. Everything else has sound working including running the system tests with Cedega. no sound at all from totem.... Any ideas? Anyone know?? I installed the win32codecs as well as whatever was in mplayerhq's essentials pack newest to todays date. Thanks!

****UPDATE**** okay so i just noticed that some videos play fine with sound but there are still a few that work fine through XINE and not totem. Also I've noticed with both totem and xine the sound comes unsynced from the video. am i crazy?


****UPDATE AGAIN***** YES!!! TOTEM-XINE FOR THE WIN! sorry to waste forum space =P I have a question about cedega performance but ill take that to your nvidia guide, thanks!

---

### Post by craftywizard on 2006-04-11
For some reason whenever I type those commands I get "cannot access archive: no such file or directory".  I've tried other ways of getting the compressed files into the /usr/lib/win32, but totem player still won't play my avi's.

---

### Post by tseliot on 2006-04-12
[QUOTE=craftywizard]For some reason whenever I type those commands I get "cannot access archive: no such file or directory".  I've tried other ways of getting the compressed files into the /usr/lib/win32, but totem player still won't play my avi's.[/QUOTE]
Can you explain you problem more in detail?

---

### Post by issueperson on 2006-04-17
[QUOTE=manicka]We are encouraging people to not use this repo as it will cause serious damage to your system.
[/QUOTE]
why doesn't a mod just get rid of this thread then?  it messed up my sources list.  wasn't hard to fix... but yeah.
issueperson

---

### Post by DavidFourer on 2006-04-18
On some videos I'm getting no sound.  On others the picture and sound are good but there is a minor problem with synchronization.

For example, today I'm getting New York Times web site videos with sound but Washington Post web site videos still have no sound.  The video sample at:
[http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi](http://www.engr.colostate.edu/me/facil/dynamics/files/flame.avi)
is playing but no sound.  When I click on the link, it plays in MPlayer plug-in for firefox.  Can I make it play in something else?

MPlayer started working with sound in New York Times web site video before I loaded the win32 codecs or xine-ui or tetem-xine.  I had just installed Mozilla-MPlayer with Synaptic but no codecs.  

I have a real hard time knowing what is going to run, whether it knows about the codecs, what format the video is in, etc.  I'm inexperienced with video.  I can launch xine-ui and totem-xine OK but don't have files to test them with.  (xine-ui does not appear in the Applications menu in Ubuntu, but I launched it from Terminal)

I mostly view videos on-line, preferrably in the browser plug-in.  So far I only know how to view these with the Mozilla/Firefox plug-in, which is not xine but MPlayer.

Does anyone recommend some how-to's for background reading?

Thanks

---

### Post by drytear on 2006-05-05
i installed the codesc but when i open movies in totem it will only play the audio of the movie .. no video .... what should i do? help :)

---

### Post by tseliot on 2006-05-05
[QUOTE=drytear]i installed the codesc but when i open movies in totem it will only play the audio of the movie .. no video .... what should i do? help :)[/QUOTE]
Install Automatix (you can find it on this forum)

---

### Post by rajaiskandarshah on 2006-05-11
ok worked for me on an amd pc and celeron notebook.
dont mind me, this is just me tracking useful stuff i have found from this forum.

---

### Post by davidyin on 2006-05-11
It is good for the newbie like me.
Thnk you.

---

### Post by 4ebees on 2006-05-12
Hi all,

Without being aware of all the politics behind all this (well, to an extent the issues relating to the proprietary nature of some elements I have some comprehension of), I have found the following site useful in setting up 5.10:

[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs)

---

### Post by dpm on 2006-06-27
Having read this thread and the "restricted formats" ubuntu wiki page, I've got a question:

I am more or less aware of the legal issues of **using** the codecs hosted at the websites indicated ([http://www4.mplayerhq.hu/homepage/design7/dload.html](http://www4.mplayerhq.hu/homepage/design7/dload.html) or [http://www.debian-multimedia.org/)](http://www.debian-multimedia.org/)), but what about **distributing** Windows binaries for free? 

Will the webmasters of those sites not run into legal troubles by making win32 binaries available to everyone?

---

### Post by walkerx on 2006-06-27
thanks for this how to

i tried this because i had issues with kaffeine not decoding the audio for my dvb-t stream, but it didn't make any difference.

It did make the audio for my xvid files work, everything else was fine

In the end I got the audio for my dvb-t stick working by following the automatix thread

regards
walkerx

---

### Post by SonWon on 2006-10-04
Any ideas why Paul Harvey will not play?  I have the W32 codecs installed.  I am using Dapper Drake with Firefox and Totem.  You can try for yourself at [www.paulharvey.com](www.paulharvey.com), jus click on the day of the week name to play.

Thank you,
SonWon

---

### Post by Flawed77 on 2006-10-23
Thanks, TS.  This helped me more than anything else that I've been able to find on the subject.  I was thinking for awhile that it was going to be impossible for someone like me (new to Ubuntu) to install such codecs with such ease.  Thank you kindly.

---

### Post by agenkin on 2006-11-21
How much of this HOWTO is still relevant for the Ubuntu Edgy, 1 year past the article was written?

Thanks!

---

### Post by OmegaNine on 2006-11-24
Just get the ALL, it has more codecs and its only like 3 megs more.

[http://www3.mplayerhq.hu/MPlayer/releases/codecs/all-20060501.tar.bz2](http://www3.mplayerhq.hu/MPlayer/releases/codecs/all-20060501.tar.bz2)

---

### Post by charliebrownau on 2008-07-12
Is there any quick and easy way without needing 
a billion files using apt-get to just
add XviD video codec and MP3 sound codec
to Ubuntu Linux without using these AIO codec packs ?

Or am I asking the impossible ?

On Windows I have a small XviD Codec install file
which gets me up and running and I use Portable MPC
to play back the files

---

### Post by narutoxela on 2009-02-01
What about .mp4 .m4v .flv...

---

### Post by 4ebees on 2009-02-03
Have a look here:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html)

Check under:
Install libdvdcss2 and w32 video codecs in Ubuntu 8.04 (Hardy Heron)

Or, whack a disk in your machine and try to play an audio file (windows anything or quicktime). You'll be asked if you want to install the appropriate codecs.

---

### Post by 4ebees on 2009-02-03
edited due to double posting

---

### Post by Deardead on 2009-11-04
> **tseliot said:**
> 

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!


[COLOR=Red]NOTE: It seems wmv9 don't work with my HOWTO if you use Ubuntu 64bit.[/COLOR] 

Alberto

Ok..some problem remain..  files *.wma even in rhytmbox play "NOPROBLEM"..BUT!!! Some *.wma -refuse!!! How can I play these files? May I send "good" and "bad" files to you ?

---

