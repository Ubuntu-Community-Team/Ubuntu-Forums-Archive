---
title: "Howto: Multimedia in Hoary"
date: 2005-03-17
forum: Outdated Tutorials &amp; Tips
---

### Post by kuleali on 2005-03-17
**MPlayer**

To get mplayer to work simply change youre rep. to:

**sudo gedit /etc/apt/sources.list**

## The following lines pertain to supported packages:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## The following lines pertain to security updates:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

## Uncomment after release to continue getting updates:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## IMPORTANT:
## Software from the following repositories are ENTIRELY UNSUPPORTED by 
## the Ubuntu team, and may not be under a free licence. This means that 
## software in these repositories WILL NOT receive any review or updates 
## from the Ubuntu security team either. These packages are provided as a
## service to our users and nothing more.

## Uncomment the following two lines to add software from the 'universe' and 
## 'multiverse' repositories:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

## Uncomment the following line to add Java software:
deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./

**Sudo apt-get install update**

[B]sudo apt-get install mplayer-386
sudo apt-get install mplayer fonts[/B]

This package contains fonts needed (but not mandatory) by mplayer to
display OSD (onscreen display) and subtitles.

And you want as well get the mozilla-mplayer plug-in
[B]
sudo apt-get install mozilla-mplayer[/B]


[B]To run mplayer type: 
gmplayer[/B]

**And change the Audio to: esd**



**VLC**

For thouse of you that don't know what VLC is: 

VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4, DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimediastreams from various network sources.

To play video files :

[B]apt-get install vlc
apt-get install vlc-plugin-esd[/B]  (since hoaey uses ESD)

In terminal type:

**vlc --aout esd**


Hopefully you will now be able to play all sort of video files.


You can also edit this in the preferences:

Open the Preferences and klikk on "Audio", 
Mark the Advanced option and make EsounD youre default audio output Module.

**To play video streams in mozilla:**

The mozilla VLC  plugin adds support for MPEG, MPEG2, DVD, DivX, Ogg/Vorbis and many more formats to your Mozilla browser. The decoding process is done by VLC
and the output window is embedded in a webpage or directly in the browser
window. There is also support for fullscreen display and javascript control.

**sudo apt-get install mozilla-plugin-vlc**

I tried this with the mozilla browser and it worked. You may have to wait some seconds because it may not show that it is buffering.
[B]

Kaffeine[/B]
Kaffeine is a xine-based media player for KDE 3
Kaffeine has all the features of xine-ui, but is native to KDE.

**sudo apt-get install kaffeine**

If the mozilla-plugins above did not work try: 

**sudo apt-get install kaffeine-mozilla **

This mozilla plugin launches kaffeine, the xine-based media player for KDE,
when a page containing a supported media format is loaded.

**Xmms, To play music files:**


[B]apt-get install xmms
apt-get libmikmod2[/B]
[B]
In Preferences change the Audio output to: eSound

[/B]Enjoy....Tell me if this helped..

---

### Post by telmo on 2005-03-17
It sucks! But thx for the suggestion...

---

### Post by bored2k on 2005-03-17
[QUOTE=telmo]It sucks! But thx for the suggestion...[/QUOTE]
 Rude lol .

It would work on lucky computers with no errors at all on Hoary. But soon enough well see "still doesnt work" postings :P .

---

### Post by telmo on 2005-03-17
[QUOTE=bored2k]Rude lol .

It would work on lucky computers with no errors at all on Hoary. But soon enough well see "still doesnt work" postings :P .[/QUOTE]

Yeah, your right... but it's just that i've never seen such an ugly player!  :lol:

---

### Post by beeldings on 2005-03-17
Thank you for posting this, I can now watch the new Nine Inch Nails video with sound. :lol: 

Alternatively, you can apt-get install xine-ui and the w32codecs package. I find that this method also works with Hoary (using the debian-marillat repositories).

> Yeah, your right... but it's just that i've never seen such an ugly player!

I agree. While VLC isn't much to look it, it does what it was intended for and it does it well.

---

### Post by kuleali on 2005-03-17
[QUOTE=telmo]It sucks! But thx for the suggestion...[/QUOTE]

Skins is a good thing.  :o

---

### Post by dillweed on 2005-03-17
[QUOTE=telmo]It sucks! But thx for the suggestion...[/QUOTE]
Don't want to make a flame war, but vlc is one of the best media players out there.  Yea, it might not look great, but it sure works good.  As the suggestion before "skins!!!"  Mplayer imo looks awful :) I mean what can get worse looking than CLI. :D

Thanks for the suggestion

---

### Post by bored2k on 2005-03-17
[QUOTE=dillweed]Don't want to make a flame war, but vlc is one of the best media players out there.  Yea, it might not look great, but it sure works good.  As the suggestion before "skins!!!"  Mplayer imo looks awful :) I mean what can get worse looking than CLI. :D

Thanks for the suggestion[/QUOTE]
 Flame war or not , VLC is the best Multiplatform Media Player this side of Wonderland .

---

### Post by zep24 on 2005-03-17
You don't need to

 > apt-get install vlc-esd

it's deprecated and now it's just a dummy package, you just need to

 > apt-get install vlc-plugin-esd

Then you can also chose esd audio output in VLC audio advanced prefs.

---

### Post by jsgotangco on 2005-03-18
VLC in Hoary looks incredibly old-school IMO but it gets the job done.

Oh, I got sound running back again here on VLC. It's my favorite player in Warty, and I hope the performance in Hoary will improve on the freeze date. Thanks for the tips.

---

### Post by Julius on 2005-03-18
[QUOTE=kuleali]
In Preferences change the Audio output to: eSound
[/QUOTE]

That's very importar :P I realised that I had to change that option a while ago... I wasn't able to play MP3 and XMMs. Why isn't eSound set as audio output by default?

---

### Post by kuleali on 2005-03-18
[QUOTE=zep24]You don't need to

 

it's deprecated and now it's just a dummy package, you just need to

 

Then you can also chose esd audio output in VLC audio advanced prefs.[/QUOTE]


Thank's for that tip.

---

### Post by j_baer on 2005-03-18
kuleali,

I would like to try VLC on a fresh install of Hoary. What do I need to install to get the same functionality as MPlayer and the MPlayer Mozilla Plugin.

Thanks ...

---

### Post by kuleali on 2005-03-18
[QUOTE=j_baer]kuleali,
I would like to try VLC on a fresh install of Hoary. What do I need to install to get the same functionality as MPlayer and the MPlayer Mozilla Plugin.
Thanks ...[/QUOTE]
 

Vlc plays MPEG, MPEG2, MPEG4,DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, without any further configuration needed.

You could try:

sudo apt-get install mozilla-plugin-vlc

This plugin adds support for MPEG, MPEG2, DVD, DivX, Ogg/Vorbis and many
more formats to your Mozilla browser. The decoding process is done by VLC
and the output window is embedded in a webpage or directly in the browser
window. There is also support for fullscreen display and javascript control.

I tried this with the mozilla browser and it worked. You may have to wait some seconds because it may not show that it is buffering.

---

### Post by dangparker on 2005-03-19
Hello,

I've gotten mplayer compiled and installed, along with totem-xine.  I'm now trying to get mozplugger to work properly.

Mozplugger plays files well, but I have one question....

At sites like [www.ifilm.com](www.ifilm.com) where they check for media type installed, it shows windows media and quicktime are not installed... How do I get firefox to report that these media players are installed?

Thanks in advance for your help

Daniel Parker

---

### Post by clparker on 2005-03-19
how do i change the audio in MPLAYER to ESD?

---

### Post by kuleali on 2005-03-19
[QUOTE=clparker]how do i change the audio in MPLAYER to ESD?[/QUOTE]

Right click in the mplayer window and select Preferences, Know click on the Audio tab and select esd. 

Remember to restart mplayer

---

### Post by madzzoni on 2005-03-19
[QUOTE=kuleali]MPlayer

To get mplayer to work simply change youre rep. to:

sudo gedit /etc/apt/sources.list

## The following lines pertain to supported packages:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## The following lines pertain to security updates:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

## Uncomment after release to continue getting updates:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## IMPORTANT:
## Software from the following repositories are ENTIRELY UNSUPPORTED by 
## the Ubuntu team, and may not be under a free licence. This means that 
## software in these repositories WILL NOT receive any review or updates 
## from the Ubuntu security team either. These packages are provided as a
## service to our users and nothing more.

## Uncomment the following two lines to add software from the 'universe' and 
## 'multiverse' repositories:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

## Uncomment the following line to add Java software:
deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./


sudo apt-get install mplayer-386

And you want as well get the mozilla-mplayer plug-in

sudo apt-get install mozilla-mplayer


To run mplayer type: 
gmplayer

And change the Audio to: esd


[/QUOTE]
I follow these instruction exactly, but mozilla-mplayerplug-in still dosn't work in Firefox, for streaming video/audio. 
The plugin shows up but stops after 25% download, where it use to start the streaming!
Before i use mplayer-custom in warty and it works perfectly, what happens in Hoary??? #-o

---

### Post by kuleali on 2005-03-20
[QUOTE=madzzoni]I follow these instruction exactly, but mozilla-mplayerplug-in still dosn't work in Firefox, for streaming video/audio. 
The plugin shows up but stops after 25% download, where it use to start the streaming!
Before i use mplayer-custom in warty and it works perfectly, what happens in Hoary??? #-o[/QUOTE]


You could try kaffeine.
Kaffeine is a media player for KDE. While it supports multiple player
engines, its default engine is Xine, giving Kaffeine a wide variety of
supported media types and letting Kaffeine access CDs, DVDs, and
network streams easily.

sudo apt-get install kaffeine
sudo apt-get install kaffeine-mozilla

Tell me if it worked, and remember to remov the "other" mozilla video plugins.

---

### Post by ACK!! on 2005-03-20
[QUOTE=madzzoni]I follow these instruction exactly, but mozilla-mplayerplug-in still dosn't work in Firefox, for streaming video/audio. 
The plugin shows up but stops after 25% download, where it use to start the streaming!
Before i use mplayer-custom in warty and it works perfectly, what happens in Hoary??? #-o[/QUOTE]

Hold on. 

Am I just doing something wrong?  I just followed the Unofficial Ubuntu Starter Guide:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

Ok mostly I subb'ed the word Warty with Hoary and edited out the repos that failed to do crap.

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)  sounds like that what you need.  

Might be wrong though.

I just followed the ubuntuguide and every well ... worked.  

The only odd thing I noticed is that I found and oh my god people are going to trip on this --- totem gstreamer seemed to play dvds more smoothly than totem-xine.

I know this is the exact opposite behavior to everyone else in the known universe so don't rip me on this.  

But the only thing gstreamer seems to be missing is a hook to use the win32 codecs for quicktime stuff.  I can tell because it jitters and does the no sound on the proprietary movie trailors.  Totem-xine handles those just fine which is the main reason I need quicktime support anyway so I stuck with totem-xine.

---

### Post by beeldings on 2005-03-20
I did this...

```
sudo apt-get install mplayer-386
```

and...


```
spikentm@ubuntu:~$ sudo apt-get install mplayer-386
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libarts (>= 4:2.2.2-1) but it is not installable or
                        libarts-alsa (>= 4:2.2.2-1) but it is not installable
               Depends: libdvdread2 but it is not installable
               Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
E: Broken packages
``` 

Has anyone else received this error message?

---

### Post by madzzoni on 2005-03-20
[QUOTE=beeldings]I did this...

```
sudo apt-get install mplayer-386
```

and...


```
spikentm@ubuntu:~$ sudo apt-get install mplayer-386
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libarts (>= 4:2.2.2-1) but it is not installable or
                        libarts-alsa (>= 4:2.2.2-1) but it is not installable
               Depends: libdvdread2 but it is not installable
               Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
E: Broken packages
``` 

Has anyone else received this error message?[/QUOTE]


Try the sources.list from this HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=20588](http://www.ubuntuforums.org/showthread.php?t=20588)

I installed and use the Totem-xine, for watching streaming-video embedded in Mozilla-Firefox 1.0.1 and it works perfectly.
Follow this very nice HOWTO:
[http://ubuntuforums.org/showthread.php?p=99897](http://ubuntuforums.org/showthread.php?p=99897)

Only problem with Totem-xine is that it's not playing DVD video smooth. I think i will try using gstreamer for playing DVDs instead.

---

### Post by NeoChaosX on 2005-03-20
Beeldings:

If you do want to install Mplayer, go into Synaptic, find whichever Mplayer package you want to install, then force the version to one with "ubuntu" in the version number. If you have the Marillat repositories in your sources.list, selecting an mplayer package will download it from those repositories, and they're dependent on Debian-only packages (which brings up the problems you're having about other packages that need to be, but can't be, installed). Selecting a version from an Ubuntu repository guarantees it'll be downloaded properly.

---

### Post by madzzoni on 2005-03-20
[QUOTE=NeoChaosX]Beeldings:

If you do want to install Mplayer, go into Synaptic, find whichever Mplayer package you want to install, then force the version to one with "ubuntu" in the version number. If you have the Marillat repositories in your sources.list, selecting an mplayer package will download it from those repositories, and they're dependent on Debian-only packages (which brings up the problems you're having about other packages that need to be, but can't be, installed). Selecting a version from an Ubuntu repository guarantees it'll be downloaded properly.[/QUOTE]

I have installed only Ubuntu-versions of mplayer (i386, i586 and mplayer-custom), without any success!

---

### Post by Monika on 2005-03-20
Can someone help me with Realplayer?

I followed the guidelines for warty in the Starter Guide, but when I try to open Realplayer, I have the following error message:

> Cannot launch entry

Details: Failed to execute child process "realplay" (No such file or directory)

---

### Post by Monika on 2005-03-21
Wow, I really love the VLC player (I like when things look simple and clear ;) ) - is there any way to install more codecs for it?

---

### Post by ACK!! on 2005-03-21
[QUOTE=Monika]Can someone help me with Realplayer?

I followed the guidelines for warty in the Starter Guide, but when I try to open Realplayer, I have the following error message:[/QUOTE]
That means realplay is not in your path.

Take my example.  I followed the same instructions which has me installed RealPlayer in /opt and then making a link from /opt/RealPlayer/realplay to /usr/bin/realplay.


For example:

ls -la /usr/bin/realplay
lrwxrwxrwx  1 root root 24 2005-02-25 15:38 /usr/bin/realplay -> /opt/RealPlayer/realplay

Alright the real question is where did you install RealPlayer?

Now, I followed the same instructions right?

 $ cd browse_to_your_download_folder
$ chmod +x realplay-10.0.2.608-linux-2.2-libc6-gcc32-i586.bin
$ sudo ./realplay-10.0.2.608-linux-2.2-libc6-gcc32-i586.bin

Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/chua/RealPlayer]: /opt/RealPlayer

You have selected the following RealPlayer configuration:
Destination:            /opt/RealPlayer
Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: Y

enter the prefix for symbolic links [/usr]: /usr

Dig that last part man?

A symbolic link is the original shortcut right?  If you follow these instructions you should have /opt/RealPlayer and a symbolic link for the binary needed to run realplay in the /usr/bin dir.

Do a 

ls -la /usr/bin/realplay

What is there?

Do you have a /opt/RealPlayer dir?

If not, then its time to figure out where you installed RealPlayer and work back from there.  

To get it to work it should be as simple as:

sudo ln -s <path_to_where_you_installed>/RealPlayer/realplay /usr/bin/realplay

---

### Post by PaTTeX on 2005-03-21
hello all 

i have no sound with mplayer

```
[AO ESD] esd_open_sound failed: Success
Could not open/initialize audio device -> no sound.
Audio: no sound

```

any idea ?

---

### Post by Monika on 2005-03-21
[QUOTE=ACK!!]To get it to work it should be as simple as:

sudo ln -s <path_to_where_you_installed>/RealPlayer/realplay /usr/bin/realplay[/QUOTE]

Thanks!
I typed in 
sudo ln -s /opt/RealPlayer/realplay /usr/bin
and I can now open it :)

But I still have trouble :(
I tried to open some *.rm files and it tells me the input is not supported :( Anyone have any ideas why that might be?

But I'm loving VLC! :) Wish it supported RealMedia, would be so cool if it did!

---

### Post by beeldings on 2005-03-21
[QUOTE=NeoChaosX]Beeldings:

If you do want to install Mplayer, go into Synaptic, find whichever Mplayer package you want to install, then force the version to one with "ubuntu" in the version number. If you have the Marillat repositories in your sources.list, selecting an mplayer package will download it from those repositories, and they're dependent on Debian-only packages (which brings up the problems you're having about other packages that need to be, but can't be, installed). Selecting a version from an Ubuntu repository guarantees it'll be downloaded properly.[/QUOTE]

What I did was copy the list of repositories from this thread, made a back up of my sources.list, and made a new file from the repositories copied from this thread.

Here is my terminal's output:

```

spikentm@ubuntu:~$ sudo apt-get install mplayer-386
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  libdirectfb-0.9-20 libggi2 libgii0 libgii0-target-x libsvga1 libungif4g
  libxvidcore4
Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 mplayer-doc
Recommended packages:
  libggi-target-x libggi-target mplayer-fonts
The following NEW packages will be installed:
  libdirectfb-0.9-20 libggi2 libgii0 libgii0-target-x libsvga1 libungif4g
  libxvidcore4 mplayer-386
0 upgraded, 8 newly installed, 0 to remove and 89 not upgraded.
Need to get 4893kB/4950kB of archives.
After unpacking 11.5MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com hoary/main libdirectfb-0.9-20 0.9.20-4 [475kB]
Get:2 http://archive.ubuntu.com hoary/main libgii0-target-x 1:0.8.5-2 [17.4kB]
Get:3 http://archive.ubuntu.com hoary/main libgii0 1:0.8.5-2 [126kB]
Get:4 http://archive.ubuntu.com hoary/main libggi2 1:2.0.5-1ubuntu1 [193kB]
Get:5 http://archive.ubuntu.com hoary/universe libsvga1 1:1.4.3-20ubuntu2 [307kB]
Get:6 http://archive.ubuntu.com hoary/multiverse libxvidcore4 2:1.0.3-0.0 [192kB]
Get:7 http://archive.ubuntu.com hoary/multiverse mplayer-386 1:1.0-pre6-0.3ubuntu6 [3583kB]
Fetched 4893kB in 18s (268kB/s)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package libdirectfb-0.9-20.
(Reading database ... 69540 files and directories currently installed.)
Unpacking libdirectfb-0.9-20 (from .../libdirectfb-0.9-20_0.9.20-4_i386.deb) ...Selecting previously deselected package libgii0-target-x.
Unpacking libgii0-target-x (from .../libgii0-target-x_1%3a0.8.5-2_i386.deb) ...
Selecting previously deselected package libgii0.
Unpacking libgii0 (from .../libgii0_1%3a0.8.5-2_i386.deb) ...
Selecting previously deselected package libggi2.
Unpacking libggi2 (from .../libggi2_1%3a2.0.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-20ubuntu2_i386.deb) ...
Selecting previously deselected package libungif4g.
Unpacking libungif4g (from .../libungif4g_4.1.3-1_i386.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.0.3-0.0_i386.deb) ...
Selecting previously deselected package mplayer-386.
Unpacking mplayer-386 (from .../mplayer-386_1%3a1.0-pre6-0.3ubuntu6_i386.deb) ...
Setting up libdirectfb-0.9-20 (0.9.20-4) ...

Setting up libsvga1 (1.4.3-20ubuntu2) ...

Setting up libungif4g (4.1.3-1) ...

Setting up libxvidcore4 (1.0.3-0.0) ...

Setting up libgii0-target-x (0.8.5-2) ...
Setting up libgii0 (0.8.5-2) ...

Setting up libggi2 (2.0.5-1ubuntu1) ...

Setting up mplayer-386 (1.0-pre6-0.3ubuntu6) ...

W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
spikentm@ubuntu:~$ sudo ln -s /opt/RealPlayer/realplay /usr/bin
spikentm@ubuntu:~$ gmplayer
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Celeron Covington/Pentium II Deschutes,Tonga/Pentium II Xeon (Family: 6, Stepping: 2)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for Debian.

Creating config file: /home/spikentm/.mplayer/config

vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
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
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.

```

I can run MPlayer with the "gmplayer" command, but I receive an error message related to this font business. It doesn't seem to affect playback issues as I can play my videos with sound. Also, when I updated my sources.list, I received this error:

```

spikentm@ubuntu:~$ sudo apt-get update
Ign http://jrfonseca.dyndns.org ./ Release.gpg
Hit http://jrfonseca.dyndns.org ./ Release
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://archive.ubuntu.com hoary-updates Release.gpg
Hit http://jrfonseca.dyndns.org ./ Packages
Hit http://security.ubuntu.com hoary-security Release
Get:3 http://archive.ubuntu.com hoary Release [19.9kB]
Ign http://archive.ubuntu.com hoary-updates Release
Ign http://archive.ubuntu.com hoary-updates/main Packages
Ign http://archive.ubuntu.com hoary-updates/restricted Packages
Err http://archive.ubuntu.com hoary-updates/main Packages
  404 Not Found
Hit http://security.ubuntu.com hoary-security/main Packages
Err http://archive.ubuntu.com hoary-updates/restricted Packages
  404 Not Found
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Get:4 http://archive.ubuntu.com hoary/main Packages [488kB]
Hit http://security.ubuntu.com hoary-security/restricted Sources
Get:5 http://archive.ubuntu.com hoary/restricted Packages [4584B]
Get:6 http://archive.ubuntu.com hoary/main Sources [173kB]
Get:7 http://archive.ubuntu.com hoary/restricted Sources [1315B]
Get:8 http://archive.ubuntu.com hoary/universe Packages [2171kB]
Get:9 http://archive.ubuntu.com hoary/multiverse Packages [87.2kB]
Get:10 http://archive.ubuntu.com hoary/universe Sources [863kB]
Get:11 http://archive.ubuntu.com hoary/multiverse Sources [48.8kB]
Fetched 3857kB in 25s (148kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  404 Not Found
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Apparently the hoary-updates repository is down. Has anyone else had this occur?

---

### Post by digby on 2005-03-21
Yeah, I couldn't access those repositories yesterday either.  I'm at school right now, so I can't try using apt.  But, they seem to be accessible via http at least.

---

### Post by kuleali on 2005-03-21
Posted by beeldings:

I can run MPlayer with the "gmplayer" command, but I receive an error message related to this font business. It doesn't seem to affect playback issues as I can play my videos with sound. Also, when I updated my sources.list, I received this error:



Sorry i forgot

sudo apt-get install mplayer fonts

This package contains fonts needed (but not mandatory) by mplayer to
display OSD (onscreen display) and subtitles.

I will add this in the Howto.

---

### Post by madzzoni on 2005-03-21
[QUOTE=ACK!!]That means realplay is not in your path.

Take my example.  I followed the same instructions which has me installed RealPlayer in /opt and then making a link from /opt/RealPlayer/realplay to /usr/bin/realplay.


For example:

ls -la /usr/bin/realplay
lrwxrwxrwx  1 root root 24 2005-02-25 15:38 /usr/bin/realplay -> /opt/RealPlayer/realplay

Alright the real question is where did you install RealPlayer?

Now, I followed the same instructions right?

 $ cd browse_to_your_download_folder
$ chmod +x realplay-10.0.2.608-linux-2.2-libc6-gcc32-i586.bin
$ sudo ./realplay-10.0.2.608-linux-2.2-libc6-gcc32-i586.bin

Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/chua/RealPlayer]: /opt/RealPlayer

You have selected the following RealPlayer configuration:
Destination:            /opt/RealPlayer
Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: Y

enter the prefix for symbolic links [/usr]: /usr

Dig that last part man?

A symbolic link is the original shortcut right?  If you follow these instructions you should have /opt/RealPlayer and a symbolic link for the binary needed to run realplay in the /usr/bin dir.

Do a 

ls -la /usr/bin/realplay

What is there?

Do you have a /opt/RealPlayer dir?

If not, then its time to figure out where you installed RealPlayer and work back from there.  

To get it to work it should be as simple as:

sudo ln -s <path_to_where_you_installed>/RealPlayer/realplay /usr/bin/realplay[/QUOTE]

I have done exactly as written above!
I got the /usr/bin/Realplay
I got the /opt/RealPlayer
RealPlayer is added in the menu and the browser-plugin is OK in Firefox

But i will Not start.... i don't know what is happening here... I even try the .deb for Linspire 5.0 without success!

In Warty i got no problem with RealPlayer at all.

What can i do to make it work?

---

### Post by Anubis on 2005-03-21
[QUOTE=digby]Yeah, I couldn't access those repositories yesterday either.  I'm at school right now, so I can't try using apt.  But, they seem to be accessible via http at least.[/QUOTE]
No there are not.

They are still down.

---

### Post by beeldings on 2005-03-21
[QUOTE=madzzoni]I have done exactly as written above!
I got the /usr/bin/Realplay
I got the /opt/RealPlayer
RealPlayer is added in the menu and the browser-plugin is OK in Firefox

But i will Not start.... i don't know what is happening here... I even try the .deb for Linspire 5.0 without success!

In Warty i got no problem with RealPlayer at all.

What can i do to make it work?[/QUOTE]

I am having the same problem with RealPlayer. However, if you go to the RealPlayer/Helix Player web site, download and install the Helix Player using the same instructions you used to install RealPlayer (as noted on the Unofficial Ubuntu Guide), and then restart GNOME, Helix Player will be available on the applications menu under Sound & Video. Next, click the icon to launch Helix and you should see the setup assistant, do your thing in that, and then you should have a fully configured, ready-to-use Helix Player.

---

### Post by digby on 2005-03-21
[QUOTE=Anubis]No there are not.

They are still down.[/QUOTE]

Actually, the archive.ubuntu.com server is up, but for some reason, some of the paths are bad.  For instance, apt was looking for a package list on [http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/), but the directory /ubuntu/dists/hoary-updates doesn't seem to exist.   If you head over to [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") it works fine

---

### Post by kuleali on 2005-03-22
[QUOTE=beeldings]I am having the same problem with RealPlayer. However, if you go to the RealPlayer/Helix Player web site, download and install the Helix Player using the same instructions you used to install RealPlayer (as noted on the Unofficial Ubuntu Guide), and then restart GNOME, Helix Player will be available on the applications menu under Sound & Video. Next, click the icon to launch Helix and you should see the setup assistant, do your thing in that, and then you should have a fully configured, ready-to-use Helix Player.[/QUOTE]

Nice, do you think i could add this in the HOWTO ?

---

### Post by Monika on 2005-03-22
Yes, but Helix doesn't play Real Media video and audio files from its description and isn't that the main reason why most people would want realplayer in addition to mplayer and vlc? Or is that just me? :mrgreen:

---

### Post by beeldings on 2005-03-22
[QUOTE=kuleali]Nice, do you think i could add this in the HOWTO ?[/QUOTE]

If you would like to, yes you may.

---

### Post by madzzoni on 2005-03-22
[QUOTE=beeldings]I am having the same problem with RealPlayer. However, if you go to the RealPlayer/Helix Player web site, download and install the Helix Player using the same instructions you used to install RealPlayer (as noted on the Unofficial Ubuntu Guide), and then restart GNOME, Helix Player will be available on the applications menu under Sound & Video. Next, click the icon to launch Helix and you should see the setup assistant, do your thing in that, and then you should have a fully configured, ready-to-use Helix Player.[/QUOTE]

Now i installed the HELIXPLAYER instead. It start up OK, but will not play!

I get this ERROR when trying watching BBC News or [www.ifilm.com:](www.ifilm.com:)

Bad Transport (rtsp://ifilm.rmod.llnwd.net/a65/o1/portalnav/getnext.rm)

What does that mean???????

---

### Post by jonny on 2005-03-22
[QUOTE=NeoChaosX]Beeldings:

If you do want to install Mplayer, go into Synaptic, find whichever Mplayer package you want to install, then force the version to one with "ubuntu" in the version number. If you have the Marillat repositories in your sources.list, selecting an mplayer package will download it from those repositories, and they're dependent on Debian-only packages (which brings up the problems you're having about other packages that need to be, but can't be, installed). Selecting a version from an Ubuntu repository guarantees it'll be downloaded properly.[/QUOTE]
I've unsuccessfully tried to install mplayer on 4 different ubuntu boxes; each time I failed miserably.  Just as I'd decided to try something easier like unicorn hunting, this tip came along.

And it works! mplayer actually exists!  It's real!  Awsome.  Thanks.

---

### Post by andradelipe on 2005-03-23
This works to KUBUNTU?
Because my Kaffeine start when i click on a srtream, but, don't do nothing!

---

### Post by ChaperonNoir on 2005-03-23
What the....

I replaced my sources.list with the one provided.

And.... I lost my registry ??

GStreamer-ERROR **: No default scheduler name - do you have a registry ?
aborting...

When i try to run rythmbox, it says i should run gst-register !

But i dont have this command !

And my apt-get doesnt work anymore ! Because of their servers i dont know ! I even put my file back to the old one and it doesnt work !

```
apt-get update
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable Release.gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable Release
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/main Packages
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/restricted Packages
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/main Packages
  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/restricted Packages
  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Ign http://luca.pca.it ./ Release.gpg
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://ca.archive.ubuntu.com hoary Release.gpg [189B]
Hit http://security.ubuntu.com hoary-security Release
Hit http://ca.archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://luca.pca.it ./ Release
Hit http://ca.archive.ubuntu.com hoary/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://ca.archive.ubuntu.com hoary/restricted Packages
Hit http://ca.archive.ubuntu.com hoary/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://ca.archive.ubuntu.com hoary/restricted Sources
Hit http://ca.archive.ubuntu.com hoary/universe Packages
Hit http://ca.archive.ubuntu.com hoary/universe Sources
Ign http://luca.pca.it ./ Packages
Ign http://luca.pca.it ./ Sources
Hit http://luca.pca.it ./ Packages
Hit http://luca.pca.it ./ Sources
Fetched 2B in 2s (1B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217)]/dists/unstable/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217)]/dists/unstable/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Reading Package Lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20amd64%20Binary-1%20(20050217)_dists_unstable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217) unstable/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Alpha%20amd64%20Binary-1%20(20050217)_dists_unstable_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by ChaperonNoir on 2005-03-23
Wow i definately don't understand.

This shitty operation changed my menu.lst config too.

I had changed this menu.lst file not so long ago to erase older kernels.... So when my grub booted i saw less things..

I don't understand how to put things back to normal... I guess i should wait for the servers to work ?

Or do you have a solution for me ?

---

### Post by capitan.harlock on 2005-03-24
Mplayer is installed, but when I try to launch it, I get this error message

MPlayer 1.0pre5-3.3.4 (C) 2000-2004 MPlayer Team

CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred 2148 MHz (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Reading config file /etc/mplayer/mplayer.conf
Illegal instruction

Here's /etc/mplayer/mplayer.conf

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

Any ideas...?

---

### Post by MetalMusicAddict on 2005-03-26
I use xine and since goin to Hoary I get this error: "xine: There is no mrl."

I have zero clue what that means even though I did Google it. Any Ideas?

---

### Post by Tichondrius on 2005-03-27
Just installed VLC on hoary (i386) and it works GREAT !!!!!!! great player.  I actually like the simple interface as opposed to "cool" skins which usually are counter intuitive. The playback is superb, smooth, no hickups, sound is also great. Couldn't ask for more.

---

### Post by RU63 on 2005-03-27
i have installed VLC and then Mplayer, both have video lag.  Mplayer is worse.  Now even Totem has sound lag, and it didn't before.  I am not sure why (I also did an upgrade during the same session).  Can anyone know how to fix it?

Thanks

---

### Post by telmo on 2005-03-27
Xine works great for me! I like it better than Mplayer or that ugly vlc.

---

### Post by Pointwood on 2005-03-28
I can get sound, but not video when I try to play .mov files with VLC.

Update: It appears to only be some .mov files...

---

### Post by Happy on 2005-03-29
I too only get sound when playing certain .mov with every video player I've tried (Totem, Mplayer, Xine, VLC and a linux quicktime player)
I've isolated the codec to the SVQ3 sorenson codec but can't seem to get any further than that

---

### Post by trentonjray on 2005-03-31
```
 vlc --aout esd
VLC media player 0.8.1 Janus
Segmentation fault

```

Anyone else getting this? Hoary (testing) i686

---

### Post by Marble2 on 2005-04-04
Does anyone know how I can get Mplayer to use an actual full screen instead of the normal video size with black around it when I choose fullscreen? It's very annoying.

---

### Post by gil-galad on 2005-04-04
[QUOTE=Marble2]Does anyone know how I can get Mplayer to use an actual full screen instead of the normal video size with black around it when I choose fullscreen? It's very annoying.[/QUOTE]

use the x11 video driver instead of xv

---

### Post by coldturkey on 2005-04-05
Hmmppffff, this is wierd! I've tried to isntall xmmz, vlc, realplayer, mplayer (The first one in this faq) but none is working. I get errors or "wrong" messages all the time! 
Im following exactly what the FAQ is saying but it still wont work...
Could somebody help me? At the moment i can't do nothing, i changed the .list file :(
Please, i really need it :) 

Thanks in advance,
ct

edit: Finally! I've installed VLC, I've got RealPlayer too but when i klick on the icon i get "the folder wasn't found" message and i have to stop!.. Wierd :/ Atm I'm listening to music through VLC but it sometimes "hacks".

---

### Post by Perfect Storm on 2005-04-07
[QUOTE=RU63]i have installed VLC and then Mplayer, both have video lag.  Mplayer is worse.  Now even Totem has sound lag, and it didn't before.  I am not sure why (I also did an upgrade during the same session).  Can anyone know how to fix it?

Thanks[/QUOTE]

Could be diffrent things. One thing is to enable DMA of your CD/DVD drives, other thing could be to change Audio to Esound in VLC. Also I changed Video output modules X11 instead of default helped alot.


Edit: Another thing. To automatically start the DVD movie when inserting it the DVD drive with VLC. Go to System ---> Preferences and open 'removable drives and media'. Under 'Multimedia' change the commandline of 'Video DVD discs' to:

wxvlc dvd:///dev/dvd

---

### Post by defkewl on 2005-04-07
How come I can't hear mp3 using xmms?

---

### Post by MetalMusicAddict on 2005-04-07
[QUOTE=defkewl]How come I can't hear mp3 using xmms?[/QUOTE]
If your trying to play over a network you need to "Mount" the drive 1st. If not you probally need to install "mpg123". Use Synaptic to find it.

---

### Post by coldturkey on 2005-04-08
Why doesnt RealPlayer start when i klick on the ikon? It installed without problem but it wont start...

---

### Post by jobezone on 2005-04-08
**gxine** - the xine video player, GTK user interface

This application will work the same as totem-xine, xine-ui, it's a different frontend for xine, and it exists in the Universe repository.

---

### Post by eyal on 2005-04-08
[QUOTE=Marble2]Does anyone know how I can get Mplayer to use an actual full screen instead of the normal video size with black around it when I choose fullscreen? It's very annoying.[/QUOTE]

start as 'mplayer -zoom ...'

---

### Post by Marble2 on 2005-04-10
Hmm, this is weird. For any video file I play, no matter what player I use or what type of file, the audio lags behind the video 2-3 seconds. I'm running a ATI Radeon 9200 Sapphire video card and onboard sound for my Shuttle AN35N Ultra. Any ideas?

---

### Post by Cyberkef on 2005-04-10
[QUOTE=kuleali]
[B]To run mplayer type: 
gmplayer[/B]

**And change the Audio to: esd**
[/QUOTE]
Very strange... ESD isn't in my audiolist.

All my MM-Sounds didn't work after the update from Warty (where it all worked!) to Hoary (MultiMedia chaos O:))

[SIZE=1]I got XMMS fixed by changing my "outgoing sounds plugin" (sorry for bad translation, it's dutch overhere :p) into eSound Plugin, but I really can't find it in MPlayer :( [/SIZE]

I'll try the VLC, but I thing that will fail to :/

** edit **

VLC works like a charm... 
Byebye MPlayer, welcome VLC ;)

Ow, just 2 noobie questions now:

1. Is there a way to remove a downloaded and compiled MPlayer (I followed [this howto](http://www.ubuntuforums.org/showthread.php?t=94&highlight=mplayer))? Via Synaptic doesn't work :p
Or just deleting all MPlayer files? (in windows this wasn't a good solution at all, dunno about ubuntu...)

2. And is there a way to open Movies always with VLC? 
I get an error when I try to open a avi file with another application: VLC...

"Could not add application to the application database" :-? 

** /edit **

---

### Post by dabeej on 2005-04-10
Does anyone else have issues listening to windows media player audio using totem with xine? Audio is heavily heavily distorted.

---

### Post by andlinux21 on 2005-07-02
Haven't tried it yet dabeej I will this weekend though heh :)

---

### Post by thagame on 2005-07-02
its a sad day in the computer world when people judge an applications worth by how "pretty" it looks on thier desktop. thats why windows is still #1 because people dont care about stability and features, they just want something with skins and look.

---

### Post by thagame on 2005-07-02
[QUOTE=telmo]Yeah, your right... but it's just that i've never seen such an ugly player!  :lol:[/QUOTE]


its a sad day in the computer world when people judge an applications worth by how "pretty" it looks on thier desktop. thats why windows is still #1 because people dont care about stability and features, they just want something with skins and look.

---

### Post by MetalMusicAddict on 2005-07-02
[QUOTE=thagame]its a sad day in the computer world when people judge an applications worth by how "pretty" it looks on thier desktop. thats why windows is still #1 because people dont care about stability and features, they just want something with skins and look.[/QUOTE]
I think today stability is a 2nd thought because the know/expect it to work well. So if they know it works well why not have it look nice. Lots of "purists" seem to shun eye-candy. I say then whats the point of having all this horsepower of modern pc's? To just encode a 5min song to mp3 in 1/2 a sec? Why is there no really good skinnable app like Winamp 5? I say bring on the eye-candy. We can take it. Even if it might come slower to linux. ;)

---

### Post by raptorsl on 2005-07-02
VLC supports skins. "[http://www.videolan.org/vlc/skins.html](http://www.videolan.org/vlc/skins.html)"

just use add " -I Skins2" to end of the command

eg:
vlc -I Skins2 <filename>
or
wxvlc -I Skins2 <filename>

[ -I is not 'l' (simple L), its capital 'i' , I for Interface]

enjoy...

---

