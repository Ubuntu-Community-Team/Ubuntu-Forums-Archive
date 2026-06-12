---
title: "HOWTO: Play 24-bit FLACs in amarok 1.4.10 (amarok14) / Jaunty"
date: 2009-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by ssri on 2009-08-21
When I looked at the steaming remnants left over from my sad attempt at upgrading a perfectly working Kubuntu Intrepid install to KDE 4.3.0 via Kubuntu's PPA, I performed a clean install/upgrade of Kubuntu Jaunty.  I disliked the version of amarok2 that came with the Jaunty, so I found a ppa for amarok 1.4.10 ([https://edge.launchpad.net/~bogdanb/+archive/amarok14/](https://edge.launchpad.net/~bogdanb/+archive/amarok14/)) and promptly installed it.  

I cheered that his amarok 1.4.10 (amarok14) compile played m4a's perfectly and how he fixed the wiki lookup bug from Intrepid's package.  However, I was dismayed how amarok14 reduced several of my 24-bit FLACs to blips and squeaks and m4a's cannot be tagged, especially since their genre tags could not be read.  The lack of m4a tagging is a story for another day.  Anyways, I found out that the FLAC regression was due to the new version of libxine1 used in Jaunty, so I thought the solution was to downgrade jaunty's package to Intrepid's version, where 24-bit FLACs played perfectly.  Okay, there is a bit of CLI work here, so hold your breath.

Note: I tested this using Kubuntu Jaunty running KDE 4.3.0.  Other multimedia programs like vlc or banshee seem to be unaffected by this downgrade.

Discussion about this bug:

[http://bugs.xine-project.org/show_bug.cgi?id=221](http://bugs.xine-project.org/show_bug.cgi?id=221)

###############
1. libcaca0 conflicts with the version of libcucul0 found in Intrepid (< 0.99.beta15), so install the libculul0 version in jaunty (0.99.beta16-1).
```
sudo apt-get install libculul0
```

2. Back up your apt sources.list in /etc/apt/ to sources.list~jaunty.  Then use my intrepid sources.list that I attached here (tar xvzf intrepid-sources.tar.gz).  _Note_: Those who have both Jaunty and Intrepid repos in their sources.list can ignore this step.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list~jaunty
sudo mv (download dir)/sources.list-intrepid /etc/apt/sources.list
```

3. Update your packages and you should see a steady stream of intrepid repos
```
sudo apt-get update
```

4. Now is the time to **_downgrade_** libxine1
```
sudo apt-get install libxine1-misc-plugins=1.1.15* libxine1-plugins=1.1.15* libxine1-ffmpeg=1.1.15* libxine1-bin=1.1.15* libxine1-x=1.1.15* libxine1-console=1.1.15* libxine1=1.1.15*
```

4a.  Here's a list of what's happening
```
The following extra packages will be installed:
  libavcodec-unstripped-51 libmagick10 libx264-59 libxine1 libxine1-bin
  libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins
  libxine1-x
Suggested packages:
  gxine xine-ui libxine1-doc libxine-doc libxine1-gnome
The following NEW packages will be installed:
  libavcodec-unstripped-51 libmagick10 libx264-59 libxine1-plugins
The following packages will be **_DOWNGRADED_**:
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg
  libxine1-misc-plugins libxine1-x
0 upgraded, 4 newly installed, 6 downgraded, 0 to remove and 7 not upgraded.
Need to get 9144kB of archives.
After this operation, 20.3MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

5. Now you have to pin the packages in apt preferences or in synaptic.  I will only give instructions for apt since I mainly use that to manage my packages.  For synaptic (I think), simply enter the names of those downgraded packages and go to packages->lock version.  Now here's my apt preferences (/etc/apt/preferences).  If you do not have a preferences file, simply enter ```
kdesudo kate /etc/apt/preferences or gksudo gedit /etc/apt/preferences
```

5a. Now enter the packages we want to pin in /etc/apt/preferences
```
Package: libxine1
Pin: version 1.1.15-0ubuntu3.3
Pin-Priority: 1001

Package: libxine1-bin
Pin: version 1.1.15-0ubuntu3.3
Pin-Priority: 1001

Package: libxine1-console
Pin: version 1.1.15-0ubuntu3.3
Pin-Priority: 1001

Package: libxine1-ffmpeg
Pin: version 1.1.15-0ubuntu3.3
Pin-Priority: 1001

Package: libxine1-misc-plugins
Pin: version 1.1.15-0ubuntu3.3
Pin-Priority: 1001

Package: libxine1-x
Pin: version 1.1.15-0ubuntu3.3
Pin-Priority: 1001

Package: libxine1-plugins
Pin: version 1.1.15-0ubuntu3.3
Pin-Priority: 1001


``` 

6.  If you are still in /etc/apt (if not, then "cd /etc/apt/"), then you have to move your Jaunty sources.list back
```
$sudo rm sources.list
$sudo cp sources.list~jaunty sources.list
```

7.  Now update your package list to jaunty repos.  If you run upgrade, you can see that none of your downgraded xine libraries are upgraded back to their jaunty versions.  Fire up amarok and enjoy your 24-bit FLACS! :guitar:

8.  To revert, simply unlock those packages in synaptic or remove the entries in /etc/apt/preferences.  Then simply refresh/update your packages, and the Jaunty versions should be upgraded automatically.

---

### Post by gadje on 2009-08-21
Thanks, your solution is really clean and complete, and it works fine for me. :guitar:

I've seen that the bug about 24bits FLAC and libxine has been reported to libxine dev but not corrected yet.

---

### Post by ssri on 2009-08-21
> **gadje said:**
> Thanks, your solution is really clean and complete, and it works fine for me. :guitar:

I've seen that the bug about 24bits FLAC and libxine has been reported to libxine dev but not corrected yet.

Yeah, this guide is merely a stopgap solution till the 24-bit FLAC bug gets fixed.

---

### Post by bogdanb on 2010-02-16
Hi ssri!

Nice tracking for those packages. I just tried them, and it seems that 24 bit FLACs play now.

However, I'm noticing a few tiny “clicks” and even some worse noises on some files (Megasfear from *Doom II Delta-Q-Delta*, for example).

I was wondering: Is that only my problem or if it happens to others, too?

---

### Post by ssri on 2010-02-22
> **bogdanb said:**
> Hi ssri!

Nice tracking for those packages. I just tried them, and it seems that 24 bit FLACs play now.

However, I'm noticing a few tiny “clicks” and even some worse noises on some files (Megasfear from *Doom II Delta-Q-Delta*, for example).

I was wondering: Is that only my problem or if it happens to others, too?

I've noticed my FLACs, at least the ones I've tried, seem to have no problems.  Then again, I was running Jaunty at the time I wrote this guide.  The only bug I found from my guide is the inability to use the seekbar bar when playing my FLACs.  Then again, I had the same problem in Intrepid.  I've been trying out Arch lately, so I do not know if I can help diagnose your problem all that much.  Did you try to play around with different backends?  You could also try the fix that someone recently posted here: [http://bugs.xine-project.org/show_bug.cgi?id=221](http://bugs.xine-project.org/show_bug.cgi?id=221)

---

### Post by ssri on 2010-06-02
The latest plain vanilla xine engine seems to use libFLAC rather than ffmpeg to play them, or so I read.  Anyways, 24-bit FLACs now play flawlessly without the dirty hack I presented in the OP.  Seeking works fine too!  Here are the relevant packages (I hope) that I'm running with Pana (1.4.16) in Arch x86_64:

xine-lib 1.1.18.1
phonon-xine 4.4.1
flac 1.2.1

Now, the question is whether one could get the newest xine libs from launchpad ppa's.

---

### Post by mthomson1 on 2010-08-06
Switching to GStreamer gives perfect playback in Amarok for all my file types, including 24-bit flac.
There are step-by-step instructions available at [http://mstenberg.com/blog/2010/08/04/amarok-flac-mp3-wma-codecs/](http://mstenberg.com/blog/2010/08/04/amarok-flac-mp3-wma-codecs/)

---

### Post by ssri on 2010-08-07
> **mthomson1 said:**
> Switching to GStreamer gives perfect playback in Amarok for all my file types, including 24-bit flac.
There are step-by-step instructions available at [http://mstenberg.com/blog/2010/08/04/amarok-flac-mp3-wma-codecs/](http://mstenberg.com/blog/2010/08/04/amarok-flac-mp3-wma-codecs/)

Yes, but GStreamer is not supported in Amarok 1.4.10

---

### Post by mc4man on 2010-08-08
>  ... GStreamer is not supported in Amarok 1.4.10While I don't see any advantage to using it, the yauap engine seems to be gstreamer based (using pana here

Edit: though  yauap does handle 24 bit flac fine

---

### Post by ssri on 2010-08-08
> **mc4man said:**
> While I don't see any advantage to using it, the yauap engine seems to be gstreamer based (using pana here

Edit: though  yauap does handle 24 bit flac fine

Well, first, Pana was several months away when I first posted this guide and the only precompiled binary was amarok(14)-xine.  Second, I believe one has to recompile Amarok 1.4.10 in order to use yauap, which shouldn't be too hard to do, but then again I am not the maintainer of amarok14.  Someone suggested that gapless playback with yauap was borked, but I do not use it so I cannot verify its veracity.  Lastly, the guide you posted is for the 2.x editions of amarok.

I tried pana two months ago and soon found out that it utilized my cpu(s) like crazy (core2duo), whereas amarok 1.4.10 (self-compiled) worked smoothly.  Furthermore, there are one or two scripts that I like to use with amarok, and I did not feel like refactoring them to work with pana, especially after the cpu incident.  It shouldn't be too difficult though (replacing "amarok" with "pana" among other things), but I had no inclination to do so.  In the end, to each his own.

---

