---
title: "HOWTO MPlayer plugin 3.11"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by christooss on 2005-10-14
[size=4]Mplayer plugin 3.11 on breezy and x86 proc for Firefox[/size]
[SIZE=3]0.0 Preinstallation[/SIZE]
You have to enable multiverse repositories

0.1 Mplayer
add folowing line in-to /etc/apt/sources.list
```
deb http://si.archive.ubuntu.com/ubuntu breezy multiverse
```
Than install mplayer-586 or 386 depends on your proc.
```
sudo apt-get install mplayer-586
sudo apt-get install mplayer-fonts
```
0.2 W32codecs
Download package from marillat repositories. I know that this in not best solution but...
```
wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb 
```
Install them with
```
 dpkg -i w32codecs_20050412-0.0_i386.deb
```
[SIZE=3]1. Installation[/SIZE]
1.1 Download this deb package
```
wget http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb
```

1.2 install it

```
dpkg -i mplayerplug-in_3.11-1_i386.deb 
```

Please report any errors

---

### Post by Gandalf on 2005-10-14
Sorry for this question but its an mplayer plugin for what?

---

### Post by christooss on 2005-10-14
Firefox 1.0.7 im sure it works with later versions to.

If any one can tell me how can I make this plugin work in Firefox 1.5

---

### Post by Gandalf on 2005-10-14
Doesn't the [HOWTO: run videos on yahoo launchcast website](http://ubuntuforums.org/showthread.php?t=75400) do the same as yours?

---

### Post by christooss on 2005-10-14
mozilla-mplayer package in repositories is  version 3.05. Newer version.

---

### Post by giopas on 2005-10-14
> ```
sudo apt-get instal mplayer-586
sudo apt-get install mplayer-fonts
```

Please report any errors
you missed an "l" in teh first "install" word.

however, thnx! :D

> ```
dpkg -i http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb 
```
it would be:
```
dpkg -i mplayerplug-in_3.11-1_i386.deb
```

enjoy, ;)
giopas

---

### Post by christooss on 2005-10-14
Thanks :P

---

### Post by Roybotnik on 2005-10-14
For me the player works just fine, but for some reason I have no controls (show controls is checked too)?  Thanks for the guide.

---

### Post by christooss on 2005-10-14
With some formats you don't get controls

---

### Post by Koba on 2005-10-14
[QUOTE=christooss][size=4]Mplayer plugin 3.11 on breezy and x86 proc for 
1.1 Download this deb package
```
wget http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb
```

1.2 install it

```
dpkg -i mplayerplug-in_3.11-1_i386.deb 
```

Please report any errors[/QUOTE]
should be ```
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```

---

### Post by jrib on 2005-11-01
[QUOTE=christooss]If any one can tell me how can I make this plugin work in Firefox 1.5[/QUOTE]

I followed your howto on hoary for this plugin and it is working perfectly on ff1.5b2 after the upgrade to breezy.

---

### Post by christooss on 2005-11-01
Yes true. Its working on my breezy to. But i hadto remove some maps etc.

---

### Post by ACK!! on 2005-11-02
[QUOTE=christooss]Yes true. Its working on my breezy to. But i hadto remove some maps etc.[/QUOTE]


It worked on my breezy but no matter what mplayer-plugin I use I get frequent crashes after playing a movie and moving on to another web page.

Am I the only one on this?

---

### Post by ember on 2005-11-02
I had problems with that, too - it seemed to be a metter of sound setting. I think, I set it to 'esd' and it worked.

---

### Post by tedddee on 2005-11-06
any ideas as to why my sound playback is very choppy in firefox?

installed 3.11 over 3.05 hoping it would fix it but nope :(

---

### Post by christooss on 2005-11-06
what is writen in your mplayer-plugin.conf?

---

### Post by tedddee on 2005-11-06
#debug=0
#vo=xv,x11
#ao=alsa,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=1
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer

---

### Post by tedddee on 2005-11-06
ok i fixed it, switched from esd to oss and everything is peachy now :)

my new conf:

debug=0
vo=x11
ao=oss
download=1
dload-dir=$HOME/tmp
keep-download=0
noembed=0
cachesize=1024
use-mimetypes=1
enable-ogg=1
enable-smil=1
enable-helix=1
qt-speed=med
rtsp-use-tcp=0
nomediacache=0
framedrop=0
autosync=1
mc=1
black-background=1
user-agent=NSPlayer

---

### Post by EvilBill on 2005-11-06
[QUOTE=christooss][size=4]Mplayer plugin 3.11 on breezy and x86 proc for Firefox[/size]
[SIZE=3]0.0 Preinstallation[/SIZE]
You have to enable multiverse repositories

0.1 Mplayer
add folowing line in-to /etc/apt/sources.list
```
deb http://si.archive.ubuntu.com/ubuntu breezy multiverse
```
Than install mplayer-586 or 386 depends on your proc.
```
sudo apt-get install mplayer-586
sudo apt-get install mplayer-fonts
```
0.2 W32codecs
Download package from marillat repositories. I know that this in not best solution but...
```
wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb 
```
Install them with
```
 dpkg -i w32codecs_20050412-0.0_i386.deb
```
[SIZE=3]1. Installation[/SIZE]
1.1 Download this deb package
```
wget http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb
```

1.2 install it

```
dpkg -i mplayerplug-in_3.11-1_i386.deb 
```

Please report any errors[/QUOTE]

"requested .....requires superuser priviledge"


How do I get it to give me this priviledge. I got those 2 things d/l'ed & ready.

---

### Post by berserker on 2005-11-07
[QUOTE=EvilBill]"requested .....requires superuser priviledge"


How do I get it to give me this priviledge. I got those 2 things d/l'ed & ready.[/QUOTE]

```
sudo dpkg -i w32codecs_20050412-0.0_i386.deb

sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```

---

### Post by cefola on 2005-11-26
Thanks Christoos !
Good thing that cut-n-paste works in terminal !
Works great !

---

### Post by Mudbream on 2005-12-19
Hi,
While following the instructions I get the following error when running the last command:

jeremy@mudders:~$ sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
dpkg: regarding mplayerplug-in_3.11-1_i386.deb containing mplayerplug-in:
 mozilla-mplayer conflicts with mplayerplug-in
  mplayerplug-in (version 3.11-1) is to be installed.
dpkg: error processing mplayerplug-in_3.11-1_i386.deb (--install):
 conflicting packages - not installing mplayerplug-in
Errors were encountered while processing:
 mplayerplug-in_3.11-1_i386.deb

All the other parts worked great. Any idea what the problem could be?

Thanks,
Mudbream

---

### Post by tjabri on 2005-12-19
[QUOTE=Mudbream]Hi,
While following the instructions I get the following error when running the last command:

jeremy@mudders:~$ sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
dpkg: regarding mplayerplug-in_3.11-1_i386.deb containing mplayerplug-in:
 mozilla-mplayer conflicts with mplayerplug-in
  mplayerplug-in (version 3.11-1) is to be installed.
dpkg: error processing mplayerplug-in_3.11-1_i386.deb (--install):
 conflicting packages - not installing mplayerplug-in
Errors were encountered while processing:
 mplayerplug-in_3.11-1_i386.deb

All the other parts worked great. Any idea what the problem could be?

Thanks,
Mudbream[/QUOTE]


Someone please correct me if I'm wrong, but it seems like you might need to remove mozilla-mplayer before install mplayerplug-in_3.11-1_i386

Hope this helps!

---

### Post by christooss on 2005-12-19
Mudbream what does the sudo apt-get install mplayer-586 tells you?

---

### Post by Mudbream on 2005-12-19
[QUOTE=christooss]Mudbream what does the sudo apt-get install mplayer-586 tells you?[/QUOTE]

jeremy@mudders:~$ sudo apt-get install mplayer-586
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libdvdcss mplayer-doc
The following packages will be REMOVED:
  mplayer-386
The following NEW packages will be installed:
  mplayer-586
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/3759kB of archives.
After unpacking 348kB disk space will be freed.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: mplayer-386: dependency problems, but removing anyway as you request:
 mozilla-mplayer depends on mplayer (>= 1.0-pre5) | mplayer-custom (>= 1.0-pre5) | mplayer-386 (>= 1.0-pre5) | mplayer-586 (>= 1.0-pre5) | mplayer-686 (>= 1.0-pre5) | mplayer-k6 (>= 1.0-pre5) | mplayer-k7 (>= 1.0-pre5) | mplayer-powerpc (>= 1.0-pre5) | mplayer-g4 (>= 1.0-pre5) | mplayer-amd64 (>= 1.0-pre5) | mplayer-nogui (>= 1.0-pre5); however:
  Package mplayer is not installed.
  Package mplayer-custom is not installed.
  Package mplayer-386 is to be removed.
  Package mplayer-586 is not installed.
  Package mplayer-686 is not installed.
  Package mplayer-k6 is not installed.
  Package mplayer-k7 is not installed.
  Package mplayer-powerpc is not installed.
  Package mplayer-g4 is not installed.
  Package mplayer-amd64 is not installed.
  Package mplayer-nogui is not installed.
 mozilla-mplayer depends on mplayer (>= 1.0-pre5) | mplayer-custom (>= 1.0-pre5) | mplayer-386 (>= 1.0-pre5) | mplayer-586 (>= 1.0-pre5) | mplayer-686 (>= 1.0-pre5) | mplayer-k6 (>= 1.0-pre5) | mplayer-k7 (>= 1.0-pre5) | mplayer-powerpc (>= 1.0-pre5) | mplayer-g4 (>= 1.0-pre5) | mplayer-amd64 (>= 1.0-pre5) | mplayer-nogui (>= 1.0-pre5); however:
  Package mplayer is not installed.
  Package mplayer-custom is not installed.
  Package mplayer-386 is to be removed.
  Package mplayer-586 is not installed.
  Package mplayer-686 is not installed.
  Package mplayer-k6 is not installed.
  Package mplayer-k7 is not installed.
  Package mplayer-powerpc is not installed.
  Package mplayer-g4 is not installed.
  Package mplayer-amd64 is not installed.
  Package mplayer-nogui is not installed.
 mplayer-fonts depends on mplayer; however:
  Package mplayer is not installed.
  Package mplayer-586 which provides mplayer is not installed.
  Package mplayer-386 which provides mplayer is to be removed.
(Reading database ... 127679 files and directories currently installed.)
Removing mplayer-386 ...
Selecting previously deselected package mplayer-586.
(Reading database ... 127584 files and directories currently installed.)
Unpacking mplayer-586 (from .../mplayer-586_1%3a1.0-pre7cvs20050716-0.1ubuntu9_i386.deb) ...
Setting up mplayer-586 (1.0-pre7cvs20050716-0.1ubuntu9) ...

So it seems that it first removes the 386 version that is there then installs the 586.
I'm off to bed now so will take a look again tomorrow evening.

Thanks for the help guys.

---

### Post by ArmadaEnder on 2005-12-20
I Had the same issue as Mudbream at the end. Could FF 1.5 be at fault for the problem? Also, I still cannot play embedded MOV format files in FF. Any ideas as to why?

---

### Post by antidrugue on 2005-12-20
[quote=christooss]Firefox 1.0.7 im sure it works with later versions to.

If any one can tell me how can I make this plugin work in Firefox 1.5[/quote] 
I guess you figured out by now, but still here is how I do it.

I manualy installed Firefox 1.5 in /usr/share/firefox (that doesn't matter, wherever you installed it).


The trick is to modify Firefox 1.5 plugins directory to be a symlink to Firefox 1.07 plugins directory (by deleting it and creating a symlink instead):
```

cd firefox
rm -r plugins
ln -s /usr/lib/mozilla-firefox/plugins plugins

``` 
So by "cd Firefox" I mean "cd <your Firefox 1.5 directory>".

Works perfectly for me...

---

### Post by elemental666 on 2005-12-23
mmkay, so from a fresh install I've done the following: 

replaced Java VM with Sun's restriced j2re
upgraded Firefox to 1.5 from mozilla.org
install Mplayer plugin 3.11 per this guide
then install win32 codecs [per this guide]("http://www.ubuntuforums.org/showthread.php?p=600321") 

My only problem now is my audio is not in sync with my video...

I use alsa drivers on a thinkpad a31

---

### Post by abyssspecter on 2005-12-26
if someoen would tell me how to  use this, id be veryhappy

---

### Post by nusigmaforce on 2006-01-13
How can I add a line in-to /etc/apt/sources.list?? I looked the filed up, opened it and notice that I can't edit it. Please help this noob. Thanks.

---

### Post by Rob2687 on 2006-01-13
sudo nano /etc/apt/sources.list

I think the mplayer plugin in the repos is at like 3.17 now anyways so this is kinda pointless.

---

### Post by christooss on 2006-01-14
trully this howto doesn't help any more. Maybe it will be a new version of mplayer soon. Than there will be a new howto

---

### Post by nusigmaforce on 2006-01-16
Yep, I bit too late I guess, but anyways the command line is helpful for next. I'm still playing with the mv, rm, cp commnads, etc.. Thanks.

---

### Post by thoffmeyer on 2006-01-23
Works fine here, thanks for the howto :)

---

### Post by Lary Grant on 2006-03-14
I had that problem and solved it with
$ sudo dpkg -r mozilla-mplayer

then I retried the -i and it worked

---

### Post by Lary Grant on 2006-03-14
Wow... big improvement! Thanks!

---

### Post by montguy on 2006-03-15
Hello,
I get a big list of broken depedencies when I try this. Anybody have a hint as to what I am doing wrong:

daemmon@latitude2:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libaa1 (>= 1.2) but it is not installable
               Depends: libasound2 (> 1.0.9) but 1.0.8-1 is to be installed
               Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
               Depends: libdirectfb-0.9-22 but it is not installable
               Depends: libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not going to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libgcc1 (>= 1:4.0.1) but 1:4.0-0pre6ubuntu7 is to be installed
               Depends: libglib2.0-0 (>= 2.8.0) but 2.6.3-1 is to be installed
               Depends: libncurses5 (>= 5.4-5) but 5.4-4 is to be installed
               Depends: libpolyp0 but it is not going to be installed
               Depends: libslang2 (>= 2.0.1-1) but it is not installable
               Depends: libstdc++6 (>= 4.0.1) but it is not going to be installed
               Depends: libsvga1 but it is not going to be installed or
                        svgalib-dummyg1 but it is not installable
               Depends: libungif4g (>= 4.1.3) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but it is not going to be installed
E: Broken packages

---

