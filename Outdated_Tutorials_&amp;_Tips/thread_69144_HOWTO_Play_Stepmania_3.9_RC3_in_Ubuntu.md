---
title: "HOWTO: Play Stepmania 3.9 RC3 in Ubuntu"
date: 2005-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Trisa on 2005-09-25
**NOTE - This HOWTO thread is now outdated. The following steps are here for archival purposes only. There are now deb files available specifically for Ubuntu 7.04 that includes working movie playback.**** This will only work on older versions of Ubuntu.**

First of all, download and install the following library files: 

```
sudo apt-get install liblua50 libmad0 liblualib50 libstdc++5 libfaad2-0 liblame0
```

2) You will have to download an older version of ffmpeg in order to get the libavformat and libavcodec files (which Stepmania needs). You can get the file [here.]("http://rpmfind.net/linux/RPM/dag/redhat/8.0/i386/ffmpeg-0.4.8-2.rh80.dag.i386.html") (Click on 'ffmpeg-0.4.8-2.rh80.dag RPM for i386' and the file will download) Once you've downloaded the file, use Alien to convert the rpm file to a deb file:

```
sudo alien ffmpeg-0.4.8-2.rh80.dag.i386.rpm
```Alternately, you can download this file so that you don't have to upgrade ffmpeg (Credits goes to Dreezard):
[http://home.arcor.de/dreezard/libffmpeg.deb](http://home.arcor.de/dreezard/libffmpeg.deb)

3) Install the newly created deb file: 

```
sudo dpkg -i ffmpeg_0.4.8-3_i386.deb
```

4) Now you will have to create a link to the files that Stepmania is looking for. If you try to run Stepmania in the terminal, you will notice that there are errors saying that it can't find the library files. You installed them earlier, and some of them are already detected, but the files are named differently, so you will have to create a link to the following library files: 

```
sudo ln -s /usr/lib/liblualib50.so.5.0 /usr/lib/liblualib.so
``````
sudo ln -s /usr/lib/liblua50.so.5.0 /usr/lib/liblua.so
``````
sudo ln -s /usr/lib/libpng12.so.0.1.2.8 /usr/lib/libpng.so.3
```These were the only ones that I had to create links to. Depending on how you installed Ubuntu, you may have to make links to other files as well. After all that is done, Stepmania should then run and you should be able to play the game. If not, make sure that you installed all the library files the program needs and that you have linked the library files with the ones that Stepmania is looking for. 

That's pretty much it. I hope this will help some people wanting to play Stepmania on Ubuntu. For those curious, here's an image of my desktop running the latest version of Stepmania:

[[IMG]http://img319.imageshack.us/img319/1503/screenshot6pv.th.jpg[/IMG]]("http://img319.imageshack.us/my.php?image=screenshot6pv.jpg")

---

### Post by flightcrank on 2005-09-26
Hi i like ddr and will try out this guide.

i dont know what the stepmania icon looks like in the gnu/linux version, but the windows one looks very crap, heres one i made if you want to use it

here it is in action

[IMG]http://maximhome.no-ip.org/images/sm.jpg[/IMG]

you should be able to down load it from here

[http://maximhome.no-ip.org/images/stepmania%20icon.png](http://maximhome.no-ip.org/images/stepmania%20icon.png)

---

### Post by jennhi on 2005-10-04
Thanks, Trisa! How do I keep apt-get and synaptic from bugging me to upgrade ffmpeg, and how do I keep apt-get from trying to upgrade ffmpeg every time I run an apt-get update?

Thanks so much, the tutorial was very helpful!

---

### Post by Trisa on 2005-10-06
[quote=jennhi]Thanks, Trisa! How do I keep apt-get and synaptic from bugging me to upgrade ffmpeg, and how do I keep apt-get from trying to upgrade ffmpeg every time I run an apt-get update?

Thanks so much, the tutorial was very helpful![/quote] 
Hi, jennhi. To keep apt-get and synaptic from upgrading ffmpeg, go to System --> Adminstration --> Synaptic Package Manager. Highlight ffmpeg, and go to Package --> Lock Version. That should keep it from upgrading unless you do a dist-upgrade. Also, if you still want to keep the latest version of ffmpeg, but still want Stepmania to work, you can use Archive Manager by double clicking on the old ffmpeg package, and look for the libavformat and libavcodec files. You can extract those to your home directory, and then move them to /usr/lib. Glad to see that the tutorial was helpful. :smile:

---

### Post by jennhi on 2005-10-06
yay! thanks again, Trisa!

---

### Post by kurisutofaa on 2005-12-06
Has someone got avis work with stepmania? Every song with background video has just a black background. In console I see this error:

WARNING: Unknown movie driver name: FFMpeg

Help anyone?

---

### Post by Trisa on 2005-12-10
[quote=kurisutofaa]Has someone got avis work with stepmania? Every song with background video has just a black background. In console I see this error:

WARNING: Unknown movie driver name: FFMpeg

Help anyone?[/quote] 
Well, according to the Stepmania FAQ for Linux, you need to install the ffmpeg-devel package. After that, you will have to compile Stepmania yourself. I know it's not the most user-friendly way to get movies working, but it's currently the only way for now. Once I look more into this, though, I may write a howto on how to get movies working on Stepmania.

---

### Post by caecus314 on 2005-12-19
[QUOTE=Trisa]Well, according to the Stepmania FAQ for Linux, you need to install the ffmpeg-devel package. After that, you will have to compile Stepmania yourself. I know it's not the most user-friendly way to get movies working, but it's currently the only way for now. Once I look more into this, though, I may write a howto on how to get movies working on Stepmania.[/QUOTE]

Yeah... I've been fiddling around with the StepMania source quite a bit lately, and I think I've gotten pretty much everything to work... except the AVIs.  If you could, a HOWTO on how to get the movies working would be much appreciated!  Thanks.

---

### Post by Trisa on 2005-12-20
Here's my current progress on the issues with movie playback. So far, I've been able to compile Stepmania 3.9 successfully after many failures. However, even though I have ffmpeg-devel, it still doesn't play movies during the game. I looked even further into this, and found out that ffmpeg 0.4.9-pre1 has problems with Stepmania. I'm currently testing another version of ffmpeg (0.4.9 20051207) and I hope the results will be better.

> If you could, a HOWTO on how to get the movies working would be much appreciated!  Thanks. 
No problem. Once I figure out what's wrong with ffmpeg, I'll be sure to write a HOWTO to solve this problem, seeing as many people want this feature working in Ubuntu.

---

### Post by Trisa on 2006-01-03
Sorry for not having an update in a while. As of Stepmania 3.9 final, this howto is no longer needed (except for the first step), as it should work out of the box now. Everything but movie playback works. Older versions will still need this howto.

I've been busy recently, so I haven't had much time trying to figure out the problem with movie playback. I've been looking at [this page]("http://www.stepmania.com/stepmania/mediawiki.php?title=Notes_for_building_in_Linux") trying to compile ffmpeg. However, I've failed a number of time. If anyone wishes to mess with this, feel free to do that. I'll try my best to get this working somehow.

---

### Post by yawie on 2006-05-16
Anything new on playing video under ubuntu?
I have a dapper up to date, the latest 3.9 stepmania, and every song with video make sm crash.

Perhaps we should look around 4.0 cvs. It would be great if somebody could do a .deb working in ubuntu.

---

### Post by wr0x2 on 2006-05-20
If you want to play songs that have video without crashing sm, you can turn just turn off backgrounds instead of deleting / relocating the video files.

---

### Post by Hagbarddenstore on 2006-06-05
[QUOTE=wr0x2]If you want to play songs that have video without crashing sm, you can turn just turn off backgrounds instead of deleting / relocating the video files.[/QUOTE]


I can't get this to work... I have it installed and everything but when i press the icon in games menu nothing happens?! Why

---

### Post by Seveni on 2006-06-15
I am having problems right off the bat.  When I type sudo apt-get install ...  I get a message in the terminal saying "E: Type 'wget' is not known on line 41 in source list /etc/apt/sources.list"  and "E: The list of sources could not be read."  But I checked the source file and everything seems to be fine.  How would I fix this?   And so you know I am a novice when it comes to Linux.

---

### Post by CompShrink on 2006-06-29
Please post your /etc/apt/sources.list file here, and I'll tell you if I see anything wrong with it.

---

### Post by Trisa on 2006-07-31
I decided to go back into messing with Stepmania again when I came across 4.0 CVS. The release is coming along nicely, as I was testing this version (there's some little problems, but it works all right for the most part). If you want movie playwork working on Ubuntu, I suggest download the latest CVS version, as it does work. You probably have to install ffmpeg first, though, but it worked perfectly for me. There's a binary download available at the web site, so go there for the newest CVS version.

---

### Post by cody50 on 2006-09-23
I followed the tutorial and I get an error

```
 

error while loading shared libraries: libmad.so.0: cannot open shared object file: No such file or directory


```

anyone have suggestions?

---

### Post by Simon80 on 2006-12-10
If anyone wants stepmania 3.9 with ffmpeg support working, I've published my packages for stepmania 3.9 in [my webspace]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/").  If you're on edgy i386, you can just grab the binary packages [stepmania]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania_3.9-0ubuntu1_i386.deb") and [stepmania-data]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania-data_3.9-0ubuntu1_all.deb").  Otherwise, you can get the *.dsc, *.orig.tar.gz, and *.diff.gz files, and then build them with dpkg-source and debuild.

---

### Post by Jmccaffrey on 2007-03-09
> **Simon80 said:**
> If anyone wants stepmania 3.9 with ffmpeg support working, I've published my packages for stepmania 3.9 in [my webspace]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/").  If you're on edgy i386, you can just grab the binary packages [stepmania]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania_3.9-0ubuntu1_i386.deb") and [stepmania-data]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania-data_3.9-0ubuntu1_all.deb").  Otherwise, you can get the *.dsc, *.orig.tar.gz, and *.diff.gz files, and then build them with dpkg-source and debuild.

You sir are my hero

---

### Post by sonorone on 2007-04-04
ok I have tried installing stepmania using both of the original tutorial and the two deb packages and with both I am not staring due to a sound card problem. can anyone tell me how to fix this problem. this is the terminal output:

nate@nate-desktop:~$ stepmania 
StepMania 3.9
Log starting 2007-04-04 12:01:04
Loading window: gtk
OS: Linux ver 020620
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.5
Threads library: NPTL 2.5
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
ALSA Driver: 0: M Audio Revolution-7.1 [Revolution71], device 0: ICE1724 [ICE1724], 1/1 subdevices avail
ALSA Driver: 0: M Audio Revolution-7.1 [Revolution71], device 1: IEC1724 IEC958 [IEC1724 IEC958], 1/1 subdevices avail
ALSA Driver: 0: M Audio Revolution-7.1 [Revolution71], device 2: ICE1724 Surrounds [ICE1724 Surround PCM], 3/3 subdevices avail
ALSA Driver: 1: PhotonX25 [PhotonX25], device 0: USB Audio [USB Audio], 1/1 subdevices avail
ALSA Driver: 2: VIA 8237 [V8237], device 0: VIA 8237 [VIA 8237], 4/4 subdevices avail
ALSA Driver: 2: VIA 8237 [V8237], device 1: VIA 8237 [VIA 8237], 1/1 subdevices avail
ALSA: dsnd_pcm_hw_params_set_format: Invalid argument
Couldn't load driver ALSA: SetHWParams failed
ALSA: dsnd_pcm_hw_params_set_format: Invalid argument
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: SetHWParams failed
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: ALSA detected.  ALSA OSS emulation is buggy; use ALSA natively.
Language: english
Theme: default
Error: Couldn't find a sound driver that works

---

### Post by Simon80 on 2007-04-04
> **sonorone said:**
> 
ALSA: dsnd_pcm_hw_params_set_format: Invalid argument
Couldn't load driver ALSA: SetHWParams failed
ALSA: dsnd_pcm_hw_params_set_format: Invalid argument
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: SetHWParams failed

This appears to be your problem - I'm not sure what to do about it, though.

---

### Post by (4M)Stephen on 2007-04-14
> **Simon80 said:**
> If anyone wants stepmania 3.9 with ffmpeg support working, I've published my packages for stepmania 3.9 in [my webspace]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/").  If you're on edgy i386, you can just grab the binary packages [stepmania]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania_3.9-0ubuntu1_i386.deb") and [stepmania-data]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania-data_3.9-0ubuntu1_all.deb").  Otherwise, you can get the *.dsc, *.orig.tar.gz, and *.diff.gz files, and then build them with dpkg-source and debuild.

niiiice package... 1 problem though... WHERE DO THE SONGS GO!!!?!??!?!?!?

thank you for your time....

---

### Post by Simon80 on 2007-04-14
Either in /usr/share/games/stepmania for system wide stuff, or ~/.stepmania if you don't want them to be shared between users.  I also briefly mentioned this in /usr/share/doc/stepmania/README.debian, but I don't expect a lot of people to check there :)

---

### Post by Dr_Deadmeat on 2007-04-23
Thank you very much, those packages did my life a lot easier =D

---

### Post by Polygon on 2007-05-03
> **sonorone said:**
> ok I have tried installing stepmania using both of the original tutorial and the two deb packages and with both I am not staring due to a sound card problem. can anyone tell me how to fix this problem. this is the terminal output:

nate@nate-desktop:~$ stepmania 
StepMania 3.9
Log starting 2007-04-04 12:01:04
Loading window: gtk
OS: Linux ver 020620
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.5
Threads library: NPTL 2.5
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
ALSA Driver: 0: M Audio Revolution-7.1 [Revolution71], device 0: ICE1724 [ICE1724], 1/1 subdevices avail
ALSA Driver: 0: M Audio Revolution-7.1 [Revolution71], device 1: IEC1724 IEC958 [IEC1724 IEC958], 1/1 subdevices avail
ALSA Driver: 0: M Audio Revolution-7.1 [Revolution71], device 2: ICE1724 Surrounds [ICE1724 Surround PCM], 3/3 subdevices avail
ALSA Driver: 1: PhotonX25 [PhotonX25], device 0: USB Audio [USB Audio], 1/1 subdevices avail
ALSA Driver: 2: VIA 8237 [V8237], device 0: VIA 8237 [VIA 8237], 4/4 subdevices avail
ALSA Driver: 2: VIA 8237 [V8237], device 1: VIA 8237 [VIA 8237], 1/1 subdevices avail
ALSA: dsnd_pcm_hw_params_set_format: Invalid argument
Couldn't load driver ALSA: SetHWParams failed
ALSA: dsnd_pcm_hw_params_set_format: Invalid argument
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: SetHWParams failed
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: ALSA detected.  ALSA OSS emulation is buggy; use ALSA natively.
Language: english
Theme: default
Error: Couldn't find a sound driver that works

had a similiar problem. i solved it by running the command (i installed it with the deb)

aoss stepmania

it makes it so that stepmania uses OSS instead of ALSA, and it works perfectly.

---

### Post by ipodox on 2007-07-13
I am trying to use the deb packages.  The data package installs just fine but when I try to install the stepmania_3.9 package it cant find libavcodec0d.  I had previously installed the libffmpeg.ded with the older version of ffmpeg. How do I get the package to recognize libavcodec?  Does this package need the older version of libavcodec or can you just use the newest libavcode0d?

Thanks

---

### Post by Simon80 on 2007-07-13
I removed the binary versions of the packages a couple of weeks ago to avoid problems like this (it's basically the fault of the ffmpeg developers for not bothering to handle library compatibility in a graceful way). My webspace doesn't have enough room to upload binary packages for every version of Ubuntu I could support.  It's inconvenient, but if you grab the source packages, you should be able to build them on your own machine.  You can get them with one command by running:
```
dget http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania-data_3.9-0sruggier1.dsc http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania_3.9-0sruggier1.dsc
```

If you aren't comfortable building debian packages from source, you might look at [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto).  Off hand, I don't know of a guide for building packages against the running system, but pbuilder is probably easier anyway.

---

### Post by brittney on 2007-08-19
How do you get the dancematts to work??
and/or is there a new howto for feisty?


-bri

---

### Post by Simon80 on 2007-08-19
Assuming your dance mat is plugged in and working, you have to bind the controls to your dance pad's buttons in StepMania's options menu.  As for getting it working on feisty, probably the easiest thing to do would be to build and install the source packages I've published.  In case you need a rough step by step guide, I guess you can consider this to be a new howto of sorts:
```
sudo apt-get install pbuilder debootstrap devscripts
sudo pbuilder create
mkdir /tmp/stepmania.tmp
cd /tmp/stepmania.tmp
dget http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania-data_3.9-0sruggier1.dsc http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania_3.9-0sruggier1.dsc
sudo pbuilder build --buildresult . stepmania-data_3.9-0sruggier1.dsc
sudo pbuilder build --buildresult . stepmania_3.9-0sruggier1.dsc
gdebi-gtk stepmania-data_*.deb
gdebi-gtk stepmania_*.deb

```

Make sure to pay attention to to how each command exited before you run the next one, to make sure that it was successful.  Also note that "pbuilder create" creates a large file at /var/cache/pbuilder/base.tgz containing a minimal install of Ubuntu, so if you're short on space you might want to delete that file, and run ```
sudo pbuilder clean
``` to get rid of the packages pbuilder downloads when building stepmania.

---

