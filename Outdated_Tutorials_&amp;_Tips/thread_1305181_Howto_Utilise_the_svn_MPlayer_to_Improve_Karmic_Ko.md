---
title: "Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package"
date: 2009-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2009-10-29
Over the last few years I have written several guides for the installation of the development version of MPlayer under Ubuntu. This particular version of that long series of guides is intended to bring the benefits of the cutting edge svn MPlayer to users of Karmic Koala by concentrating on upgrading the mplayer-nogui package. I should mention at this time that the mplayer-nogui package from the Karmic Repository is an improvement over packages seen in previous versions of Ubuntu and if the information below looks a little too much you will still be reasonably well served by simply installing the repository package. This guide is perhaps for those who want a little more...

============================
**Some requirements...**
============================

There is a little preparation work required before we actually lay hands on the MPlayer application and this will probably take about 30 minutes and involve a download of about 100 megabytes of extra software. First then for some necessary software:

------------------------
Required tools:
------------------------

Some compiling will be required for this guide so we will be downloading some compiling sotware as well as software to access subversion and git repositories and finally the utility checkinstall which will be used to keep the installation within the Ubuntu package management system. Copy the following and paste into a Terminal window, exclude the '$' marks which among other things demonstrates a *new line* of commands in this guide:

```
$ sudo apt-get install build-essential gcc-4.3 g++-4.3 subversion checkinstall
```

Next to collect some development files:

---------------------------
Development files:
---------------------------

MPlayer works by automatically gathering functionality from various development files installed on your computer. The following list of files has been winnowed out from the standard *sudo apt-get build-dep mplayer-nogui* command in the interests of maintaining a cleaner system.

**Special note concerning vdpau support:** As of r29823 the svn MPlayer requires Version 190.32 (or later) of the NVidia drivers to enable vdpau output, which effectively renders the Karmic NVidia drivers and libvdpau package obsolete. To obtain vdpau output you will now need to obtain the *latest* drivers from NVidia and compile MPlayer against them, no extra options are needed as MPlayer will detect the drivers/libraries and enable vdpau support automagically. 

The following is a single command:

```

sudo apt-get install ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev \
libaudio-dev libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev \
libcaca-dev libcairo2-dev libcdparanoia-dev libcelt0 libdbus-1-dev libdc1394-22 \
libdca-dev libdca0 libdirectfb-dev libdirectfb-extra libdts-dev libesd0-dev \
libexpat1-dev  libffado1 libfontconfig1-dev libfreebob0 libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev \
libgsm1 libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev liblzo2-2 \
liblzo2-dev libmail-sendmail-perl libncurses5-dev libogg-dev liboil0.3-dev \
libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev libpng12-dev \
libpthread-stubs0 libpthread-stubs0-dev libpulse-dev libruby1.8 \
libschroedinger-dev libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libvorbis-dev libvorbisidec-dev libvorbisidec1 libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev \
libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev \
libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev \
libxv-dev libxvidcore4 libxvidcore4-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev vstream-client-dev x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev \
zlib1g-dev libopencore-amrwb-dev libopencore-amrnb-dev libopenjpeg-dev

```

We will also add another useful packages here, a current set of Live555 libraries to enable playback of some streaming audio, although you have no interest in streaming audio simply omit this step, many streams will be processed *natively* by MPlayer anyway:

```

$ sudo apt-get remove liblivemedia-dev
$ cd $HOME
$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo cp -r $HOME/live /usr/lib

```

These libraries are in constant development so come back here from time to time to repeat the process and pick up the updated libraries.

Next however to install a codec package:

-------------
Codecs:
-------------

MPlayer has the ability to use and external library of codecs to playback some media files. Conveniently Medibuntu holds these files and I would suggest that you now read over the following page to understand the implications of utilising this repository which is *not* part of Ubuntu:

Medibuntu - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The actual syntax to add the repository (taken directly from the page above) is as follows, this a single command:

```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update

```

Once the repository is in place the following should download the appropriate codecs, it is a single command:

```

if [ "$(uname -m)" = "x86_64" ]; then
 sudo apt-get install w64codecs
else
 sudo apt-get install w32codecs
fi

```

Now that all of this is done it is time to actually lay hands on the MPlayer files themselves:

==============================
**Downloading & Compiling**
==============================

The development version of MPlayer is held in a subversion repository that allows read access by users, which is to say that you can *download* files from the repository but not *alter* files in this repository. To download our copy of the MPlayer files the following commands are required:

```

$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

```

Now to compile and install the source code, especially note the use of gcc-4.3 in this command. The MPlayer developers believe that there are a few issues compiling under gcc-4.4.1 which is the default under Karmic. If you wish to use gcc-4.4.1 anyway simply omit *--cc=gcc-4.3* and cross your fingers while compiling:

```

$ cd $HOME/mplayer
$ ./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-mencoder --disable-x264
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean

```

It is best to now leave $HOME/mplayer undisturbed as you can return at a later date to run the command *svn up* to download the latest changes in the MPlayer source code, and then recompile. But now to complete the setup:

===========================
**Completing the setup...**
===========================

There are a couple of other small steps that I would recommend you attend to before launching your brand new copy of mplayer-nogui. The first step is to copy the user configuration file to the appropriate location. The following will accomplish that and also backup any existing configuration file:

```

$ mv -v $HOME/.mplayer/config $HOME/.mplayer/config_bak
$ cp -v $HOME/mplayer/etc/example.conf $HOME/.mplayer/config

```

Open the file $HOME/.mplayer/config in your favourite text editor and alter the settings as you see fit. In particular have a look at the settings for video out and audio out, on my own system these are *vo=x11* and *ao=pulse* respectively. Next we will set MPlayer to play media from within Firefox by installing the gecko-mediaplayer. I also include instructions for the removal of the Totem plugin as on my system this prevents a few conflicts:

```

$ sudo apt-get remove totem-mozilla
$ sudo apt-get install gecko-mediaplayer

```

You would be best to add a good quality gui for the commandline MPlayer as well and the best of these is SMPlayer. (I should mention in passing that when you installed the gecko-mediaplayer you also installed another gui: GNOME Mediaplayer, well worth a look at as well.) To get the very best copy of SMPlayer add rvm's PPA as follows:

```

$ sudo add-apt-repository ppa:rvm/smplayer

```

and then install SMPlayer itself:

```

$ sudo apt-get update && sudo apt-get install smplayer

```

This completes the setup for this guide and I wish you all the best with your improved copy of Karmic Koala's mplayer-nogui!

===========================
**Some Resources...**
===========================

[LIST]
[*][MPlayer-users]("https://lists.mplayerhq.hu/mailman/listinfo/mplayer-users") MPlayer mailing list for usage questions, feature requests, bug reports. I would advise lurking for  while on this list before posting, breaches of posting etiquette are dealt with harshly at times.
[*][MPlayer - The Movie Player]("http://www.mplayerhq.hu/DOCS/HTML/en/index.html") The html documentation for MPlayer. Usually kept up to date and well worth reading if problems arise and certainly will need to be read before requesting help on MPlayer-users.
[*] [MPlayer FAQs]("http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ") This page attempts to list all of the frequent questions from the #mplayer irc channel on irc.freenode.net. 
[*][Top 10 Tricks and Tips for the svn MPlayer]("http://ubuntuforums.org/showthread.php?t=1154431") A guide on the Ubuntu Forums that demonstrates some of the magic that can be accomplished with the commandline MPlayer. Written by the author of this guide.
[*][MPlayer/MEncoder Tips and Tricks]("http://forums.debian.net/viewtopic.php?t=17783") A very nicely done guide from the Debian world that is still for the most part relevant to Ubuntu, some great tips for both MPlayer and MEncoder.
[/LIST]

---

### Post by Joeb454 on 2009-10-31
Though I probably won't use it, this looks like a pretty comprehensive guide :) Thanks andrew.46

---

### Post by NTolerance on 2009-10-31
What are the benefits of the nogui version?  A cursory look at the links you posted and a Google search doesn't give me much.  I mainly use mplayer with MythTV.

---

### Post by andrew.46 on 2009-10-31
Hi NTolerance,

> **NTolerance said:**
> What are the benefits of the nogui version?  A cursory look at the links you posted and a Google search doesn't give me much.  I mainly use mplayer with MythTV.

'mplayer-nogui' is a Debian/Ubuntu repackaging of the original MPlayer source code and is the commandline MPlayer only. Other packages created from this source code are include a packaging called simply 'mplayer' which includes the gui gmplayer, another one for the encoder MEncoder and another for the html documentation. I am afraid that I am not familiar with MythTV so I cannot comment on whether it will be of use there. But the benefits of using the *svn MPlayer* for the mplayer-nogui package include:

[LIST=1]
[*]If kept up to date you can obtain support from the MPlayer developers
[*]Playback of amr sound is possible, as this guide compiles against the new libopencore-amr libraries.
[*]Playback of wmapro is possible using the native ffwmapro. This is a huge plus for 64bit users.
[*]Integrates beautifully with the gecko-mediaplayer package to give wide media coverage when browsing with Firefox.
[*]Integrates nicely with the best frontend available for MPlayer: SMPlayer.
[*]You can produce your own version of MPlayer shaped to it *your* needs.
[/LIST]

Plus the benefits and perils of using up to date code that is for the most part updated each and every day. But for MythTV I am not sure of the actual benefits, perhaps another MythTV user could comment here?

All the best,

Andrew

---

### Post by fenian on 2009-10-31
For Mythtv you would certainly want to build mplayer-nogui with the vdpau dev files if you have an Nvidia card series 8 or above.You probably would also want to make sure you have support for x264.

---

### Post by andrew.46 on 2009-10-31
Hi fenian,

> **fenian said:**
> For Mythtv you would certainly want to build mplayer-nogui with the vdpau dev files if you have an Nvidia card series 8 or above.You probably would also want to make sure you have support for x264.

Thanks for that :). I have left out vdpau from the guide except to mention briefly that those fortunate enough to have such cards would benefit from the appropriate dev files which will then automagically be picked up by the MPlayer ./configure process. 

***Edit:** I have finally bowed to a bit of pressure and added in [I]nvidia-185-libvdpau-dev*.[/I]

But h264 playback is well covered with the svn MPlayer with the native *ffh264*. x264 support is of course only required for *encoding* with MEncoder, which is not covered in this guide.

All the best,

Andrew

---

### Post by 5nak3 on 2009-11-01
Firstly, Andrew thanks a lot for this guide.

Although it seems that I must have made a mistake somewhere because whereas the normal SMplayer build would play all my media files except 3gp/amr this SVN build doesn't seem to want to play any of my files and keeps throwing up the following error:

```
mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 81788943 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/peter/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 40 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/<insert path to file here>

Warning unknown option stop-xscreensaver at line 87
Unknown option on the command line: -stop-xscreensaver
Error parsing option on the command line: -stop-xscreensaver
MPlayer SVN-r29809-4.3.4 (C) 2000-2009 MPlayer Team
ID_EXIT=NONE

```

I would like to give this another go, this time without distractions from the outside world, but I just thought I would post the outcome before retrying in case something very obvious was missed out.

And just a thought you mention about the Live555 streaming tools and then mention* "These libraries are in constant development so come back here from time to time to repeat the process and pick up the updated libraries. Or if you have no interest in streaming audio simply omit this step, many streams will be processed natively by MPlayer anyway."*

I would say to move this part above the actual code for the Live555 download so people can see that part first and determine whether or not they want Live555 or not.

Apart from that, great guide and very easy to follow, now I just have to sort out my little issue :D

---

### Post by tlee on 2009-11-01
Greetings--

First of all, thanks, andrew.46, for contributing these great how-to's.  

I've just had a go with this one, but caught a snag in the "Downloading and Compiling" section, specifically with the "sudo checkinstall..." command.  Everything had gone swimmingly before that.  This command stops with the following error:

> (Reading database ... 252465 files and directories currently installed.)
Unpacking mplayer-nogui (from .../mplayer-nogui_3:1.0~svn-r29810-1_i386.deb) ...
dpkg: error processing /home/tobias/mplayer/mplayer-nogui_3:1.0~svn-r29810-1_i386.deb (--install):
 trying to overwrite '/usr/local/bin/mplayer', which is also in package mplayer 3:1.0~svn-r29746-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/tobias/mplayer/mplayer-nogui_3:1.0~svn-r29810-1_i386.deb
/var/tmp/tmp.80jd1hPXTq/dpkginstall.log (END) 


Perhaps this has to do with the previous version of mplayer that I had?  This was the svn version that I'd installed with your Hardy Heron guide.  When I upgraded to Karmic, mplayer would not work. (It complained of a missing library--libdirectfb-1.0.so.0.  I decided to start from scratch when I find this how-to.) Before starting this how-to, I did a "sudo make uninstall" from within the (old) mplayer directory.  When I got this error, I went looking for and deleted /usr/local/bin/mplayer.  I tried again, but this error still comes up.

Any ideas?

Thanks!

---

### Post by andrew.46 on 2009-11-02
Hi 5nak3,

> **5nak3 said:**
> 

```
Warning unknown option stop-xscreensaver at line 87
```



Hmmm.... something must have been missed during compilation as this option works on my own system which was a bare Karmic installation. The easiest way around this is to remove the option from SMPlayer, I attach a screenshot to demonstrate to location of this option.

> I would say to move this part above the actual code for the Live555 download so people can see that part first and determine whether or not they want Live555 or not.

Good point, I have altered the guide as you have suggested, thanks :).

Andrew

---

### Post by andrew.46 on 2009-11-02
Hi tlee,

> **tlee said:**
>  This command stops with the following error:

```
dpkg: error processing /home/tobias/mplayer/mplayer-nogui_3:1.0~svn-r29810-1_i386.deb (--install):
trying to overwrite '/usr/local/bin/mplayer', which is also in package mplayer 3:1.0~svn-r29746-1
```

Normally what should happen is that dpkg *removes* the older version and then *installs* the newer version, which is where the beauty of the naming convention I have suggested comes in (each new revision of MPlayer is a newer version). But this is obviously not happening in your case as instead dpkg is attempting to *overwrite* your previous file and failing. It is possible to get dpkg to force the installation but I suspect a better option is to look in Synaptic and remove *all* instances of mplayer-nogui and then reinstall mplayer-nogui. (I would be interested to hear if it removes cleanly, or if there are several instances of MPlayer installed.) With any luck this will get you out of trouble :).

Andrew

---

### Post by tlee on 2009-11-02
Hi Andrew,

Yes, that did the trick.  There were no other instances of 'mplayer-nogui'--just an 'mplayer' package.  Not sure how I wound up with multiple versions, but anyway, removing this (which did remove cleanly) and repeating the "sudo checkinstall..." command worked.

Thanks again.

Best,

tlee

---

### Post by piousp on 2009-11-02
Hi Andrew,
its me again! :p
Just reporting back with VDPAU results: ¡IT WORKS!
Thanks for this excellent guide again! :KS

---

### Post by andrew.46 on 2009-11-03
Hi tlee,

> **tlee said:**
> Yes, that did the trick.  There were no other instances of 'mplayer-nogui'--just an 'mplayer' package.  Not sure how I wound up with multiple versions, but anyway, removing this (which did remove cleanly) and repeating the "sudo checkinstall..." command worked.

Excellent news :). 

Andrew

---

### Post by andrew.46 on 2009-11-03
Hi piousp,

> **piousp said:**
> Just reporting back with VDPAU results: ¡IT WORKS!

You are now officially ahead of me with MPlayer as I don't have a computer/graphics card capable of vdpau:(. There is still a lot of activity with vdpau so it will be well worth your while to update the svn MPlayer every now and then.

Andrew

---

### Post by piousp on 2009-11-03
> **andrew.46 said:**
> Hi piousp,



You are now officially ahead of me with MPlayer as I don't have a computer/graphics card capable of vdpau:(. There is still a lot of activity with vdpau so it will be well worth your while to update the svn MPlayer every now and then.

Andrew

Nice! And thanks for the tip! I'll keep compiling it until something breaks ;)

---

### Post by Dethecus on 2009-11-04
> svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
svn: Can't connect to host 'svn.mplayerhq.hu': Connection refused

Is there a mirror for this possibly? Tried yesterday and today with the same problem.

---

### Post by andrew.46 on 2009-11-04
Hi Dethecus,

> **Dethecus said:**
> 
```
svn: Can't connect to host 'svn.mplayerhq.hu': Connection refused 
```Is there a mirror for this possibly? Tried yesterday and today with the same problem.

Sounds a little odd, I have tested now and connected with no trouble, and no mirror available as far as I know. Try again later?

Andrew

---

### Post by FakeOutdoorsman on 2009-11-04
> **Dethecus said:**
> Is there a mirror for this possibly? Tried yesterday and today with the same problem.

Perhaps a firewall is interfering.  You can try downloading a [source snapshot](http://www.mplayerhq.hu/MPlayer/releases/mplayer-export-snapshot.tar.bz2) or [SVN snapshot](http://www.mplayerhq.hu/MPlayer/releases/mplayer-checkout-snapshot.tar.bz2) at [MPlayer Downloads](http://www.mplayerhq.hu/design7/dload.html).  I think they are built daily, but I could be wrong.

---

### Post by zackiv31 on 2009-11-04
@andrew.46

You mentioned earlier that this install doesn't have options for x264 (and mencoder).  As a person looking for exactly this feature can you point me in the right direction or help me out a bit?

[http://ubuntuforums.org/showthread.php?t=1314280](http://ubuntuforums.org/showthread.php?t=1314280)

---

### Post by andrew.46 on 2009-11-04
Hi zackiv,

> **zackiv31 said:**
> You mentioned earlier that this install doesn't have options for x264 (and mencoder).  As a person looking for exactly this feature can you point me in the right direction or help me out a bit?

It will not be too difficult to adapt this particular guide to allow for MEncoder and x264 *encoding* (bear in mind that h264 *playback* does not require x264). First install the latest x264 libraries according to Fakeoutdoorsman's guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and then perhaps also install the aac and lame development files (libfaac-dev and libmp3lame-dev) to allow for whatever sound codecs you wish to use. Then simply compile as per this guide but omit the *--disable-mencoder* option from ./configure and alter the checkinstall syntax from *--pkgname mplayer-nogui* to *--pkgname mplayer*. This will build *both* MEncoder and MPlayer and place the executables in /usr/local/bin.

All the best,

Andrew

---

### Post by Arup on 2009-11-05
Andrew,

Good job as usual, upgraded to latest mplayer on my Karmic x64 using your superb guide. Just wanted to add that if one is using nvidia drivers from nvidia and not from repos via ncurses based installer, you don't have to add the libvdpau-dev as mplayer checks for it automatically. Unlike when you install the nvidia driver via repos where the libvdpau-dev file is not installed, in case of the ncurses based nvidia install, the necessary libvdpau files are already installed. VDPAU works nicely on my system here with a cheapo nvidia 8400 card. 

Another point I would like to recommend if I may is to use the latest SMPLAYER instead of the older on in the repos, you can do that by adding the developer rvm's ppa at [https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

This keeps your smplayer up to date.

Thanks again for your good work.

---

### Post by mc4man on 2009-11-06
> the mplayer-nogui package from the Karmic Repository is an immense improvement over packages seen in previous versions of Ubuntu

Having only used hardy (with my own stuff) and now karmic (same thing), it didn't strike me that the decision to strip mplayer's ffmpeg libs was  recent to karmic and i gather the way it will be in the future 

(while not the worst thing for fresh installs may be a bit of issue for up-graders
> 
mplayer (1.0~rc3+svn20090426-1) unstable; urgency=low

  [ fabrice ]
  * Introduce the mplayer-nogui package, that does not depend on GTK+

  [ Reinhard Tartler ]
  * new upstream svn version based on the 1.0rc3 branch
  * various cleanups and refactoring in debian/rules
  * no longer remove mencoder.c: It does hardly contain any "dangerous"
    or patented code. Instead:
  * strip libavcodec similar to how its done in the ffmpeg package. This
    brings the patent policy of the mplayer and ffmpeg package in debian
    finally in sync. c.f. the comments and the "discussion" in #522373.
  * install upstream's version of binary_codecs.sh

 -- Reinhard Tartler <siretart@tauware.de>  Thu, 04 Jun 2009 10:35:52 +0200

---

### Post by Arup on 2009-11-06
[HTML]sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" --provides "mplayer,mencoder" [/HTML]

This is whats needed to install mencoder, the "no gui" is needed as well as the end line --provides "mplayer,mencoder" for mencoder to correctly register in the system. Installing Acid Rip doesnt make it pull mencoder from the repos even though Synaptic shows mencoder as not installed.

---

### Post by andrew.46 on 2009-11-06
Hi mc4man,

> **mc4man said:**
> 
> the mplayer-nogui package from the Karmic Repository is an immense improvement over packages seen in previous versions of Ubuntu
Having only used hardy (with my own stuff) and now karmic (same thing), it didn't strike me that the decision to strip mplayer's ffmpeg libs was  recent to karmic and i gather the way it will be in the future 

I would be amongst the first to say that the best way to experience MPlayer is to install from the svn source rather than rely on the decisions of others who have their own priorities and their own agendas. Having said that I believe the more *modern* version of MPlayer in the Ubuntu repositories is at the very least a step in the right direction. But I take your point, as always, and I will remove the 'immense' from my description in deference to the butchering of the static FFmpeg that *should* be with MPlayer :).

Andrew

---

### Post by andrew.46 on 2009-11-06
Hi Arup,

> **Arup said:**
> Just wanted to add that if one is using nvidia drivers from nvidia and not from repos via ncurses based installer, you don't have to add the libvdpau-dev as mplayer checks for it automatically. Unlike when you install the nvidia driver via repos where the libvdpau-dev file is not installed, in case of the ncurses based nvidia install, the necessary libvdpau files are already installed. VDPAU works nicely on my system here with a cheapo nvidia 8400 card. 

I still have some misgivings about adding the vdpau development files as I prefer to personally test all material in guides I write. But who can resist the tidal wave that is vdpau? 

> Another point I would like to recommend if I may is to use the latest SMPLAYER instead of the older on in the repos, you can do that by adding the developer rvm's ppa at [https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

An interesting point. I will have to say that this guide is aimed primarily at the commandline MPlayer rather than SMPlayer so I suspect the repository offering will be adequate for the guide itself. Of course if somebody wishes to use the newer versions of SMPlayer this would not be a problem and if some disparity arose between the svn MPlayer and the repository SMPlayer I would address this promptly.

All the best,

Andrew

---

### Post by Arup on 2009-11-06
> **andrew.46 said:**
> Hi Arup,



I still have some misgivings about adding the vdpau development files as I prefer to personally test all material in guides I write. But who can resist the tidal wave that is vdpau? 



An interesting point. I will have to say that this guide is aimed primarily at the commandline MPlayer rather than SMPlayer so I suspect the repository offering will be adequate for the guide itself. Of course if somebody wishes to use the newer versions of SMPlayer this would not be a problem and if some disparity arose between the svn MPlayer and the repository SMPlayer I would address this promptly.

All the best,

Andrew

Hi Andrew,

Just make sure to tell those using nvidia drivers from the nvdia site not to add the libvdpau command. The latest nvidia driver is 190.42 so that command will only add to the confusion. I also found out that rvm's ppa for mplayer contains one thats built against the older nvidia 185 series drivers, in case one installs the 192.xx series, the vdpau doesn't function.

The reason I recommend getting the latest mplayer is because the one in the repo has problems with the latest  mplayer when you do a rewind or fast forward. The latest one has no such issues.

---

### Post by andrew.46 on 2009-11-06
Hi Arup,

> **Arup said:**
> Just make sure to tell those using nvidia drivers from the nvdia site not to add the libvdpau command. The latest nvidia driver is 190.42 so that command will only add to the confusion. I also found out that rvm's ppa for mplayer contains one thats built against the older nvidia 185 series drivers, in case one installs the 192.xx series, the vdpau doesn't function.

I have just finished adjusting the vdpau instructions so this should be a little clearer now. As regards SMPlayer, since this guide is really aimed at producing and supporting the commandline MPLayer I have pared down the references to SMPlayer more than a little. The [upcoming morass of NVidia driver versions]("http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-November/062812.html"), MPlayer versions and SMPlayer versions looks very, very messy....

Thanks for your points,

Andrew

---

### Post by bofphile on 2009-11-06
What should I change in your guide if I want to use mplayer with the multithreaded FFmpeg-mt branch ?
Thanks.

---

### Post by andrew.46 on 2009-11-06
Hi bofphile,

> **bofphile said:**
> What should I change in your guide if I want to use mplayer with the multithreaded FFmpeg-mt branch ?

Interesting question. I have never actually used this so I spent a little time testing it out. From my guide omit this:

```

$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ cd $HOME/mplayer

```

and instead run the following:

```

$ cd $HOME
$ wget -N http://just.mooo.com/mplayer-svn-mt.tar.bz2
$ tar xjvf mplayer-svn-mt.tar.bz2
$ cd $HOME/mplayer

```

and continue compiling from there. I gather this file is an svn snapshot and I simply followed the directions of the [MPlayer site]("http://www.mplayerhq.hu/design7/news.html"). Seemed to work well enough with the following options:

```
mplayer -lavdopts threads=4 myfile.mp4
```

and it seemed to work fine but I am pretty new to this side of MPlayer. I would be interested to hear how you went with this?

Andrew

---

### Post by Arup on 2009-11-06
Actually for those without nvidia VDPAU, ffmpeg-mt is an excellent idea as then the cores get to do their job.

---

### Post by andrew.46 on 2009-11-07
Hi Arup,

> **Arup said:**
> Actually for those without nvidia VDPAU, ffmpeg-mt is an excellent idea as then the cores get to do their job.

It seemed fairly straightforward to compile it although I was a little puzzled when I saw that some have been *manually* patching the static FFmpeg that comes with MPlayer. And of course there seems to be not a great deal of information online about the so-called MPlayer-mt. This would be a great opportunity for somebody with a bit of knowledge and working experience with the multi-threaded version the chime in and let me know what mistakes I have made with this technique :).

All the best,

Andrew

---

### Post by mc4man on 2009-11-07
have you glanced thru here
[http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)

(do you have a link to your svn thread handy?

---

### Post by andrew.46 on 2009-11-07
Hi mc4man,

> **mc4man said:**
> have you glanced thru here
[http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)

Oops I have accidentally intruded on another guide I suspect with that little runthrough :redface:. Now I finally remember that there is a wealth of guides for MPlayer on these forums: the one you have mentioned for MPlayer-mt, an excellent guide for MPlayer compiled with CoreAVC and I seem to remember another that deals in some depth with vdpau although my night-duty fatigue is blocking me from finding that one at the moment :). It is great time to be using Ubuntu and MPlayer!

Andrew

---

### Post by cor2y on 2009-11-07
It seems that with the latest svn update Mplayer has dropped support for vdpau with any driver older than 190 series which means using the stock 185 drivers that come with ubuntu 9.10  you will not have vdpau acceleration when compiling mplayer or on playback.
So you will have to manually install the new drivers or use ffmeg-mt for smooth hidef playback.

---

### Post by mc4man on 2009-11-07
give or take an -r (forgot yet again the svn com.) this would provide vdpau with 185 (though I'm sure many who use  it will say upgrade to 190

svn checkout -r29821 svn://svn.mplayerhq.hu/mplayer/trunk mplayer

It would probably only  be viable for a bit, I believe when you co an -r you still get the current ffmpeg sync ( may be wrong there ...,?

---

### Post by Arup on 2009-11-07
> **cor2y said:**
> It seems that with the latest svn update Mplayer has dropped support for vdpau with any driver older than 190 series which means using the stock 185 drivers that come with ubuntu 9.10  you will not have vdpau acceleration when compiling mplayer or on playback.
So you will have to manually install the new drivers or use ffmeg-mt for smooth hidef playback.

By default the libvdpau-dev file isn't installed on Ubuntu, installing it as Andrew suggests should get VDPAU even with latest mplayer compile.

---

### Post by cor2y on 2009-11-07
The only one available in the repos with univers and multiverse enabled is nvidia-185-libvdpau-dev and it doesnt work with mplayer SVN-r29843 you have to install the 190.42 driver to get vdpau output.

---

### Post by Arup on 2009-11-07
This is news to me, I will check with nvidia forums, if someone is on the list of mplayer forums, they should check as well.

The ppa for nvidia-vdpau from Brandon Schneider contains mplayer with vdpau support for 185 drivers so I guess they will compile of probably and most likely he used older mplayer. 

Have to admit that vdpau quality and playback with latest 190 drivers and latest mplayer is the best ever in terms of quality, even on a cheap 8400 series card.

---

### Post by mc4man on 2009-11-07
> .....you have to install the 190.42 driver to get vdpau output. 

As Andrew posted (committed a couple of days ago
[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-November/062838.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-November/062838.html)

---

### Post by Arup on 2009-11-07
Thanks so then for latest mplayer compile requiring vdpau, 190xx series drivers should be a prerequisite then.

---

### Post by andrew.46 on 2009-11-07
Hi Arup,

> **Arup said:**
> Thanks so then for latest mplayer compile requiring vdpau, 190xx series drivers should be a prerequisite then.

Some final confirmation here:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-November/078126.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-November/078126.html)

Interesting times indeed :).

Andrew

---

### Post by Arup on 2009-11-07
> **andrew.46 said:**
> Hi Arup,



Some final confirmation here:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-November/078126.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-November/078126.html)

Interesting times indeed :).

Andrew

Thanks Andrew, will be watching that thread.

---

### Post by bofphile on 2009-11-07
Andrew, I've successfully compiled mplayer with ffmpeg-mt but I have some problems. When I play Bluray files, frames are dropped while my dual core CPU is not fully used and the load is not spread evenly between the 2 cores. By default the governor is set to ondemand but even when I fix the frequency of my 2 cores at their maximum speed, the problem remains.

I've tried several options like noframedrop and cache size, but the issue remains. Here is a screenshot to show the CPU load when playing a m2ts file: [http://bofphile.free.fr/Images/Capture-1.jpg]("http://bofphile.free.fr/Images/Capture-1.jpg")

I'm using a Thinkpad T500 with a 2,67GHz dual core CPU and an integrated intel 4500MHD graphic card.

Any idea what could be the problem ?

---

### Post by andrew.46 on 2009-11-07
Hi bofphile,

> **bofphile said:**
> Andrew, I've successfully compiled mplayer with ffmpeg-mt but I have some problems. When I play Bluray files, frames are dropped while my dual core CPU is not fully used and the load is not spread evenly between the 2 cores. By default the governor is set to ondemand but even when I fix the frequency of my 2 cores at their maximum speed, the problem remains.

I am afraid that my knowledge of MPlayer-mt is confined to the single time I have successfully compiled it, and to tell the truth I immediately returned to the *standard* MPlayer once I was satisfied of my success. Perhaps there are some dedicated MPlayer-mt users here or on the thread dedicated to the subject that can help out? This thread is here:

HOWTO: Compiling mplayer with multi-core decoding support
[http://ubuntuforums.org/showthread.php?t=1049449](http://ubuntuforums.org/showthread.php?t=1049449)

I note on this thread there is a manual replacement of the static FFmpeg with FFmpeg-mt files, a technique I have not tried myself.

My apologies,

Andrew

---

### Post by bofphile on 2009-11-07
Thanks for your help anyway  ;).
I'll try to ask on the thread you suggested above.

---

### Post by zackiv31 on 2009-11-09
This might be outside the scope of this guide, but I want to compile mine with mencoder as well.  You listed:

```

$ cd $HOME/mplayer
$ ./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-mencoder
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean

```

I changed the configure line to this:
```

./configure --cc=gcc-4.3 --confdir=/etc/mplayer

```

Do I need to alter the checkinstall line (or have two?).  Example appreciated!

---

### Post by Arup on 2009-11-09
I have mencoder working here with Acidrip, during the compilation omit the --disable mencoder from ./configure line and then for install use 

sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" --provides "mplayer,mencoder"

---

### Post by zackiv31 on 2009-11-09
Well that got mencoder installed... but I'm having trouble with the encoding itself... mencoder is Skipping Frames like crazy on my video.  This use to happen on both mplayer/mencoder with the 9.10 builds...

Funny thing is, mplayer can play the file fine now (which is a step in the right direction), but mencoder is still choking.

---

### Post by Arup on 2009-11-09
> **zackiv31 said:**
> Well that got mencoder installed... but I'm having trouble with the encoding itself... mencoder is Skipping Frames like crazy on my video.  This use to happen on both mplayer/mencoder with the 9.10 builds...

Funny thing is, mplayer can play the file fine now (which is a step in the right direction), but mencoder is still choking.

Try using all the cores of your CPU, also can you tell me what video card you have on your system.

---

### Post by andrew.46 on 2009-11-10
Hi zackiv,

> **zackiv31 said:**
> Well that got mencoder installed... but I'm having trouble with the encoding itself... mencoder is Skipping Frames like crazy on my video.

I will admit that I gave up on MEncoder a while back and pretty much exclusively use FFmpeg. I am not sure what level of commitment the MPlayer developers still give to MEncoder...

Andrew

---

### Post by andrew.46 on 2009-11-10
Hi Arup,

> **Arup said:**
> 
```
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" --provides "mplayer,mencoder"
```

A small note to this checkinstall syntax is that, although I use it myself, the *--fstrans=no* option is redundant. Not because the root problem has been fixed but because the option is duplicated in the checkinstall rc file from Jaunty onwards. I have left it there because it causes no harm and if somebody duplicates the syntax with an older version of Ubuntu they will not run into trouble :).

Andrew

---

### Post by bofphile on 2009-11-10
andrew, what should I do if I want to completely remove the compiled mplayer from my system ? Use apt-get remove mplayer ?

Thanks.

---

### Post by andrew.46 on 2009-11-10
Hi bofphile,

> **bofphile said:**
> andrew, what should I do if I want to completely remove the compiled mplayer from my system ? Use apt-get remove mplayer ?

If you have used the suggested checkinstall syntax from the *original* guide you could use:

```
sudo apt-get remove mplayer-nogui
```

or simply use synaptic.

Andrew

---

### Post by sdowney717 on 2009-11-10
does this give mp3 support for mencoder?
i am trying to convert and getting error with synaptiv version of mencoder
 
scott@scott-desktop:~/Videos$ ./mencoder test.mpg -o output.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=2:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac mp3lame cbr:br=128
MEncoder SVN-r29375-4.4.1 (C) 2000-2009 MPlayer Team
MPlayer was compiled without libmp3lame support.
scott@scott-desktop:~/Videos$

i got it modifying your guide to include mencoder.
And you have to add a bunch of development files such as libmp3lame dev, etc... 

> scott@scott-desktop:~/Videos$ mencoder test.mpg -o output.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=2:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac mp3lame 
MEncoder SVN-r29882-4.3.4 (C) 2000-2009 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xa0c71f
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.970  ftime:=0.0334
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 0
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Forcing output FourCC to 58564944 [DIVX].
MP3 audio selected.
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: libavcodec (720x480 fourcc=58564944 [DIVX])
[VE_LAVC] High quality encoding selected (non-realtime)!
Writing header...1f ( 4%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.7s     22f ( 7%)  0.00fps Trem:   0min   2mb  A-V:0.068 [0:182]
Skipping frame!
Pos:  14.3s    431f (100%) 148.21fps Trem:   0min   2mb  A-V:0.055 [1106:182]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1106.079 kbit/s  (138259 B/s)  size: 1979093 bytes  14.314 secs  431 frames

Audio stream:  182.865 kbit/s  (22858 B/s)  size: 328608 bytes  14.376 secs
scott@scott-desktop:~/Videos$

---

### Post by andrew.46 on 2009-11-10
Hi sdowney,

> **sdowney717 said:**
> does this give mp3 support for mencoder?
i am trying to convert and getting error with synaptiv version of mencoder
 [...]
i got it modifying your guide to include mencoder.
And you have to add a bunch of development files such as libmp3lame dev, etc...

This guide really does not deal with MEncoder, but normally to compile MEncoder as well as MPlayer you would have to add in a few more dev files. These would normally include the development files for aac, mp3 and h264 encoding plus a few more according to need. Perhaps others on this thread can lend assistance here? I no longer compile MEncoder on my own setup and no longer incorporate it into any guides I write having been convinced that FFmpeg is the way to go.

Andrew

---

### Post by Arup on 2009-11-10
Yep I get far better results using latest ffmpeg from Fake Outdoorsman's thread. The only reason I compile mencoder is to satisfy Acid Rip's requirements, otherwise it tends to pull the older mplayer from the repos to get the mencoder.

---

### Post by andrew.46 on 2009-11-10
Hi Arup,

> **Arup said:**
> Yep I get far better results using latest ffmpeg from Fake Outdoorsman's thread. The only reason I compile mencoder is to satisfy Acid Rip's requirements, otherwise it tends to pull the older mplayer from the repos to get the mencoder.

I suspect that when I get to thinking about 'yet another MPlayer guide' for Lucid I might have a look at producing both an mplayer-nogui package *and* a mencoder package. It would be nice to do something quite comprehensive for Lucid since it will be an LTS release.

Andrew

---

### Post by Arup on 2009-11-10
Famous last words but I do intend to stay with Lucid for a long while. Actually I would have stayed with Hardy but using Skype with cam shoots shoots all my 8 cores of the CPU to insanely high levels, from 8.10 onwards no such issue.

---

### Post by nishant.singh28 on 2009-11-12
Before make:

  Enabled optional drivers:
    Input: dvdnav(internal) vstream ftp pvr tv-v4l2 tv-v4l tv live555 cddb cdda libdvdcss(internal) dvdread(internal) vcd dvb smb network 
    Codecs: libschroedinger xvid libopencore_amrwb libopencore_amrnb libavcodec(internal) real xanim faad2(internal) faac libdca libmpeg2(internal) liba52(internal) mp3lib(internal) libtheora speex tremor(internal) liblzo gif 
    Audio output: alsa openal jack pulse nas esd oss v4l2 sdl mpegpes(dvb) 
    Video output: v4l2 sdl gif89a pnm jpeg png opengl mpegpes(dvb) fbdev svga caca aa xvidix cvidix dga xv x11 xover dfbmga directfb yuv4mpeg md5sum tga 

  Disabled optional drivers:
    Input: radio tv-dshow nemesi 
    Codecs: libdirac x264 libdv qtx win32 musepack toolame twolame libmad 
    Audio output: sun arts ivtv dxr2 
    Video output: zr zr2 ivtv dxr3 dxr2 vesa ggi xmga mga winvidix 3dfx vdpau xvmc bl xvr100 tdfx_vid wii s3fb tdfxfb 

'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML//video.html#mtrr)

NOTE: Win32 codec DLLs are not supported on your CPU (x86_64) or your
operating system (Linux). You may encounter a few files that cannot
be played due to missing open source video/audio codec support.

Check configure.log if you wonder why an autodetection failed (make sure
development headers/packages are installed).

NOTE: The --enable-* parameters unconditionally force options on, completely
skipping autodetection. This behavior is unlike what you may be used to from
autoconf-based configure scripts that can decide to override you. This greater
level of control comes at a price. You may have to provide the correct compiler
and linker flags yourself.
If you used one of these options (except --enable-gui and similar ones that
turn on internal features) and experience a compilation or linking failure,
make sure you have passed the necessary compiler/linker flags to configure.

If you suspect a bug, please read DOCS/HTML//bugreports.html.



When I issue make, the last few lines:

allformats.c:(.text+0x32): undefined reference to `ac3_muxer'
allformats.c:(.text+0x154): undefined reference to `dirac_muxer'
allformats.c:(.text+0x168): undefined reference to `dnxhd_muxer'
allformats.c:(.text+0x186): undefined reference to `dts_muxer'
allformats.c:(.text+0x1cc): undefined reference to `eac3_muxer'
allformats.c:(.text+0x262): undefined reference to `h261_muxer'
allformats.c:(.text+0x276): undefined reference to `h263_muxer'
allformats.c:(.text+0x28a): undefined reference to `h264_muxer'
allformats.c:(.text+0x30c): undefined reference to `m4v_muxer'
allformats.c:(.text+0x33e): undefined reference to `mjpeg_muxer'
allformats.c:(.text+0x352): undefined reference to `mlp_muxer'
allformats.c:(.text+0x3e8): undefined reference to `mpeg1video_muxer'
allformats.c:(.text+0x406): undefined reference to `mpeg2video_muxer'
allformats.c:(.text+0x4a6): undefined reference to `null_muxer'
allformats.c:(.text+0x4ec): undefined reference to `pcm_alaw_muxer'
allformats.c:(.text+0x500): undefined reference to `pcm_mulaw_muxer'
allformats.c:(.text+0x514): undefined reference to `pcm_f64be_muxer'
allformats.c:(.text+0x528): undefined reference to `pcm_f64le_muxer'
allformats.c:(.text+0x53c): undefined reference to `pcm_f32be_muxer'
allformats.c:(.text+0x550): undefined reference to `pcm_f32le_muxer'
allformats.c:(.text+0x564): undefined reference to `pcm_s32be_muxer'
allformats.c:(.text+0x578): undefined reference to `pcm_s32le_muxer'
allformats.c:(.text+0x58c): undefined reference to `pcm_s24be_muxer'
allformats.c:(.text+0x5a0): undefined reference to `pcm_s24le_muxer'
allformats.c:(.text+0x5b4): undefined reference to `pcm_s16be_muxer'
allformats.c:(.text+0x5c8): undefined reference to `pcm_s16le_muxer'
allformats.c:(.text+0x5dc): undefined reference to `pcm_s8_muxer'
allformats.c:(.text+0x5f0): undefined reference to `pcm_u32be_muxer'
allformats.c:(.text+0x604): undefined reference to `pcm_u32le_muxer'
allformats.c:(.text+0x618): undefined reference to `pcm_u24be_muxer'
allformats.c:(.text+0x62c): undefined reference to `pcm_u24le_muxer'
allformats.c:(.text+0x640): undefined reference to `pcm_u16be_muxer'
allformats.c:(.text+0x654): undefined reference to `pcm_u16le_muxer'
allformats.c:(.text+0x668): undefined reference to `pcm_u8_muxer'
allformats.c:(.text+0x6a4): undefined reference to `rawvideo_muxer'
allformats.c:(.text+0x6d6): undefined reference to `roq_muxer'
allformats.c:(.text+0x794): undefined reference to `truehd_muxer'
libavcodec/libavcodec.a(allcodecs.o): In function `avcodec_register_all':
allcodecs.c:(.text+0x50f): undefined reference to `zlib_decoder'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


Now what?????

---

### Post by andrew.46 on 2009-11-12
Hi nishant,

> **nishant.singh28 said:**
> Now what?????

There have been a lot of changes over the last day or so and I suspect you have caught a broken svn that has since been rectified. Certainly I have just compiled today:

```
andrew@skamandros:~/Desktop$ mplayer | head -n 1
MPlayer SVN-r29906-4.3.4 (C) 2000-2009 MPlayer Team
```

and there were no problems on Karmic. My suggestion is to run:

```
$ make distclean
$ svn up
```

from your mplayer source files and then compile again.

All the best,

Andrew

---

### Post by Bachstelze on 2009-11-13
Just to drop a note for nvidia users wanting to use VDPAU: some features added by the 190 NVidia drivers were recently added fo ffmpeg, so recent SVN builds of ffmpeg and mplayer require that version of the drivers if you want to use VDPAU. If "vdpau" appears in the "Disabled optional drivers" list in the ./configure output, upgrade your drivers.

---

### Post by andrew.46 on 2009-11-13
As has previously been suggested to me both on this thread and via some private email I have just now added in details of rvm's PPA for SMPlayer. Thanks again to rvm for making this available :).

Abdrew

---

### Post by helpdeskdan on 2009-11-16
Hum... I've never seen this before!  Help?

(Reading database ... 227977 files and directories currently installed.)
Unpacking mplayer-nogui (from .../mplayer-nogui_3:1.0~svn-r29920-1_i386.deb) ...
dpkg: error processing /home/dan/mplayer/mplayer-nogui_3:1.0~svn-r29920-1_i386.deb (--install):
 trying to overwrite '/usr/local/bin/mplayer', which is also in package mplayer 3:1.0~svn-r29768-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/dan/mplayer/mplayer-nogui_3:1.0~svn-r29920-1_i386.deb
/var/tmp/tmp.SGERwrayzc/dpkginstall.log (END)

---

### Post by andrew.46 on 2009-11-17
Hi helpdeskdan,

> **helpdeskdan said:**
> Hum... I've never seen this before!  Help?

Normally dpkg upgrades the copy of MPlayer automagically but obviously this is not working in this case. Try uninstalling MPlayer through Synaptic instead and the run the install again, it should install cleanly after this.

All the best,

Andrew

---

### Post by helpdeskdan on 2009-11-17
Turns out I had to uninstall the last svn mplayer I had installed.  One of the options in aptitude was to replace it with mplayer-nogui which I did, for no other reason than to keep it from uninstalling many of the dep's like smplayer.  After doing this, it worked fine!

Thanks again for your continued work on the excellent Mplayer guide!!

---

### Post by andrew.46 on 2009-11-17
Hi helpdeskdan,

> **helpdeskdan said:**
> Turns out I had to uninstall the last svn mplayer I had installed.  One of the options in aptitude was to replace it with mplayer-nogui which I did, for no other reason than to keep it from uninstalling many of the dep's like smplayer.  After doing this, it worked fine!

Excellent news :).

> Thanks again for your continued work on the excellent Mplayer guide!!

I keep saying that this guide will be the last but I guess I will continue for a while longer while I am still enjoying the challenge :).

Andrew

---

### Post by helpdeskdan on 2009-11-17
By the way, that ppa for smplayer should be:

deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) karmic main

---

### Post by andrew.46 on 2009-11-17
Hi helpdeskdan,

> **helpdeskdan said:**
> By the way, that ppa for smplayer should be:

deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) karmic main

Exactly what I thought :). This works of course but I have used the new cool syntax suggested here:

[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

All the best,

Andrew

---

### Post by viking_maniac on 2009-11-23
I've decided to try this guide out! :)
 
I have one question though: when you are about to compile this, is it possible to make your own deb or any sort of package that makes is easier to install again later? Or do you need to enter all these commands each time you install?
 
Thanks for your work!

---

### Post by Bachstelze on 2009-11-23
> **viking_maniac said:**
> I've decided to try this guide out! :)
 
I have one question though: when you are about to compile this, is it possible to make your own deb or any sort of package that makes is easier to install again later? Or do you need to enter all these commands each time you install?
 
Thanks for your work!

Why would you want to install the same version "later"? By defnition, it will be outdated.

---

### Post by Arup on 2009-11-23
> **viking_maniac said:**
> I've decided to try this guide out! :)
 
I have one question though: when you are about to compile this, is it possible to make your own deb or any sort of package that makes is easier to install again later? Or do you need to enter all these commands each time you install?
 
Thanks for your work!

viking_maniac,

The last line checkinstall will create a .deb file for you and install it from there, the mplayer.deb file would be on your desktop and you can install it later but the whole purpose of this exercise is to have the latest, greatest Mplayer installed and therefore updating is the way, I do it every month or so and stay with the cutting edge mplayer.

---

### Post by zanadou on 2009-11-23
This dosn't work for me:

```
$ sudo apt-get install ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev \
libaudio-dev libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev \
libcaca-dev libcairo2-dev libcdparanoia-dev libcelt0 libdbus-1-dev libdc1394-22 \
libdca-dev libdca0 libdirectfb-dev libdirectfb-extra libdts-dev libesd0-dev \
libexpat1-dev  libffado1 libfontconfig1-dev libfreebob0 libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev \
libgsm1 libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev liblzo2-2 \
liblzo2-dev libmail-sendmail-perl libncurses5-dev libogg-dev liboil0.3-dev \
libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev libpng12-dev \
libpthread-stubs0 libpthread-stubs0-dev libpulse-dev libruby1.8 \
libschroedinger-dev libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libvorbis-dev libvorbisidec-dev libvorbisidec1 libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev \
libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev \
libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev \
libxv-dev libxvidcore4 libxvidcore4-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev vstream-client-dev x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev \
zlib1g-dev libopencore-amrwb-dev libopencore-amrnb-dev
```
It just outputs:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa-glx (= 7.6.0-1ubuntu4) but 7.6.1~git20091107.9348ac03-0ubuntu0~xup~1 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 7.6.0-1ubuntu4) but 7.6.1~git20091107.9348ac03-0ubuntu0~xup~1 is to be installed
E: Broken packages

```How can I get around this? I'm running x64, btw.

---

### Post by Arup on 2009-11-23
> **zanadou said:**
> This dosn't work for me:

```
$ sudo apt-get install ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev \
libaudio-dev libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev \
libcaca-dev libcairo2-dev libcdparanoia-dev libcelt0 libdbus-1-dev libdc1394-22 \
libdca-dev libdca0 libdirectfb-dev libdirectfb-extra libdts-dev libesd0-dev \
libexpat1-dev  libffado1 libfontconfig1-dev libfreebob0 libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev \
libgsm1 libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev liblzo2-2 \
liblzo2-dev libmail-sendmail-perl libncurses5-dev libogg-dev liboil0.3-dev \
libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev libpng12-dev \
libpthread-stubs0 libpthread-stubs0-dev libpulse-dev libruby1.8 \
libschroedinger-dev libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libvorbis-dev libvorbisidec-dev libvorbisidec1 libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev \
libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev \
libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev \
libxv-dev libxvidcore4 libxvidcore4-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev vstream-client-dev x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev \
zlib1g-dev libopencore-amrwb-dev libopencore-amrnb-dev
```
It just outputs:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa-glx (= 7.6.0-1ubuntu4) but 7.6.1~git20091107.9348ac03-0ubuntu0~xup~1 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 7.6.0-1ubuntu4) but 7.6.1~git20091107.9348ac03-0ubuntu0~xup~1 is to be installed
E: Broken packages

```How can I get around this? I'm running x64, btw.

Enable medibuntu repos and check all the repos in synaptic.

---

### Post by zanadou on 2009-11-23
> **Arup said:**
> Enable medibuntu repos and check all the repos in synaptic.

Hmm, I have "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free" in my sources.list, I've updated and it still gives the same error. From Synaptic, when I go to install "libgl1-mesa-dev", it gives me a similar error:
```
libgl1-mesa-dev:
  Depends: libgl1-mesa-glx (=7.6.0-1ubuntu4) but 7.6.1~git20091107.9348ac03-0ubuntu0~xup~1 is to be installed
```Why the hell is it talking about a git version??

---

### Post by mc4man on 2009-11-23
> Why the hell is it talking about a git version??

You apparently have updated those libs past the karmic versions, most likely thru a ppa and then removed/disabled the source.

(and not that long ago, look at the date

Your best bet, considering the libs involved, is to re-enable the source, update and then proceed.

This seems like a possible ppa where you may have got the updated mesa libs

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages)

---

### Post by andrew.46 on 2009-11-24
Hi viking_maniac,

> **viking_maniac said:**
> I've decided to try this guide out! :)
 
I have one question though: when you are about to compile this, is it possible to make your own deb or any sort of package that makes is easier to install again later? Or do you need to enter all these commands each time you install?

I hope you have fun with the guide, it is a fascinating exercise to build a program like this from source :). The guide uses checkinstall to create a debian package that you can save if you wish for reinstallation later but it is often a better idea to return to the MPlayer source every week or so and issue the command *svn up* and then recompile to gain improvements and new functionality.

All the best,

Andrew

---

### Post by drewlong on 2009-11-24
Hi Andrew a couple of questions if I may

I was wondering why Gecko rather than the mplayer mozilla plugin ?
From what I can see in mozilla's plugins they both seam to serve the same media types.

On a slightly different tack why mplayer rather than VLC ?
I have no real preference so long as it works ..... 

Would appreciate your guidance so I dont mess my system up again. PM would be fine if you prefer so as not to fill up the forum.

Thanks     ;)

---

### Post by andrew.46 on 2009-11-24
Hi drew,

> **drewlong said:**
> I was wondering why Gecko rather than the mplayer mozilla plugin ? From what I can see in mozilla's plugins they both seam to serve the same media types.

The [same man]("http://kdekorte.googlepages.com/home") created both plugins. The [MPlayer plugin ]("http://mplayerplug-in.sourceforge.net/")was last released on June 24th 2008 while the gecko-mediaplayer was [last released]("http://code.google.com/p/gecko-mediaplayer/downloads/list") on September of this year. So or me this was an easy choice :).

> On a slightly different tack why mplayer rather than VLC ?
I have no real preference so long as it works ..... 

They are certainly 2 sides of the same coin but attract a subtly different clientele. Perhaps try vlc first before launching into MPlayer, it may very well meet all of your needs without the pain of compiling :). The version in the Ubuntu repositories is more than reasonable...

> Would appreciate your guidance so I dont mess my system up again.

I still mess my own system from time to time so perhaps you are talking to the wrong person :).

Andrew

---

### Post by Bachstelze on 2009-11-24
> **drewlong said:**
> 
On a slightly different tack why mplayer rather than VLC ?
I have no real preference so long as it works ..... 

VLC is much more complicated to compile than MPlayer, so if you want the latest codecs, MPlayer is a better choice. However, if you don't feel the need to compile, both are pretty much equivalent, the only differences I can remember being that VLC doesn't support VDPAU (yet), and MPlayer does not support playing a DVD directly from an ISO, and has also very poor support for some MKV features like subchapters (though on this, both are quite poor and don't support the most advanced of them, like ordered chaptering and editions).

---

### Post by Arup on 2009-11-24
Plus for nvidia users, there is no vdpau support in VLC yet so it makes sense to use mplayer.

---

### Post by drewlong on 2009-11-24
thanks guys

---

### Post by rvm4000 on 2009-11-24
> **Bachstelze said:**
> and MPlayer does not support playing a DVD directly from an ISO,

mplayer can play a dvd from an ISO.

> **Bachstelze said:**
>  and has also very poor support for some MKV features like subchapters (though on this, both are quite poor and don't support the most advanced of them, like ordered chaptering and editions).

The multi-threaded version of (the one that can be downloaded from the git repo) has support for ordered chapters in mkv.

---

### Post by viking_maniac on 2009-11-24
> **Bachstelze said:**
> Why would you want to install the same version "later"? By defnition, it will be outdated.
 
It might be that I want to install several Ubuntu/Kubuntu installations over a short period of time, or something could go wrong and I need to reinstall my system (you see, I'm still experimenting with Linux), thus it would be much easier to have a deb or any install package to double click from all these commands.
 
Of course, when I'm about to install 10.04, or if I should get any problems with mplayer that need an update, I could always redo these steps.
 
:)

---

### Post by Bachstelze on 2009-11-24
> **rvm4000 said:**
> 
The multi-threaded version of (the one that can be downloaded from the git repo) has support for ordered chapters in mkv.

GIT repo? I thought MPlayer used SVN. O.o If there's an unofficial GIT somewhere, well, it's unofficial.

---

### Post by rvm4000 on 2009-11-24
It's unofficial but it was mentioned in the mplayer web site. Now I see they updated the page and the git repo is not mentioned anymore, now they point to this link [http://just.mooo.com/mplayer-svn-mt.tar.bz2](http://just.mooo.com/mplayer-svn-mt.tar.bz2)

---

### Post by iRounak on 2009-11-24
I am not exactly sure what I did to get mplayer working.. Basically, I did not know that non-gui mplayer came along with Karmic. I installed mplayer first from Ubuntu Software Centre. Then I ran the command apt-get install mplayer. It would be better if I first remove mplayer completely and then use this:
Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

How should I completely remove mplayer from my system?

---

### Post by andrew.46 on 2009-11-25
Hi iRounak,

> **iRounak said:**
>  It would be better if I first remove mplayer completely and then use this:
Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

How should I completely remove mplayer from my system?

We meet again :). Probably the easiest way is to simply open up synaptic and search for MPlayer and remove or keep as you deem suitable. My own Karmic setup is the mplayer-nogui package created in this guide and SMPlayer from rvm's PPA and this has been sufficient for my needs under Ubuntu. But there are certainly alternatives, rvm maintains a PPA for MPlayer as well which will produce a much more polished packaging of MPlayer and of course the repository MPlayer is a little better than previous Ubuntu offerings. And then there is vlc, CoreAVC, mplayer-mt, lots of choice...

Andrew

---

### Post by iRounak on 2009-11-25
Many thanks again, Andrew. I think at this moment I will keep everything as it is since the movie files are playing in Smplayer. Once I get a proper understanding of repositories, synaptic, ppa, rvm etc, I will try to clean my mess and do a fresh install of mplayer.

---

### Post by andrew.46 on 2009-11-25
Hi iRounak,

> **iRounak said:**
> Many thanks again, Andrew. I think at this moment I will keep everything as it is since the movie files are playing in Smplayer. Once I get a proper understanding of repositories, synaptic, ppa, rvm etc, I will try to clean my mess and do a fresh install of mplayer.

Sounds like a great plan. These resources for the most part will always be here in one form or the other, although I should perhaps point out that rvm is a person rather than a resource :).

All the best,

Andrew

---

### Post by viking_maniac on 2009-11-25
I have one question: 

As I've been into earlier regarding the deb package that gets created after this process; if I want to install this jumbo mplayer package on another computer, can I just use this deb package on the other computer, without needing to run any commands that I've already run?

---

### Post by andrew.46 on 2009-11-26
Hi viking,

> **viking_maniac said:**
> As I've been into earlier regarding the deb package that gets created after this process; if I want to install this jumbo mplayer package on another computer, can I just use this deb package on the other computer, without needing to run any commands that I've already run?

Unfortunately no. The deb package produced by checkinstall is a little primitive and not suited to this purpose. To create such a package you would need to look into creating a formal package and for this most would look at modifying the files in the debian/ section of the source code. Unfortunately I have no experience in the creation of such packages, perhaps others on this thread can guide you?

Andrew

---

### Post by viking_maniac on 2009-11-26
Now I've gone trough your whole guide and everything went smooth. FINALLY I can play cell phone video files again with sound! :) And it seems like this version of mplayer is able to play almost every file out there. I write almost since it actually crashed on an old .rm file. Though, VLC was able to play that one fine. So I guess the combination of this mplayer and VLC 1.0.2 is a winner in total. The only thing I miss in smplayer is the A-B loop playback, like in VLC. I still think that I can write _success_ at this point! Thanks to andrew.46!

I hope that you'll stick around in here for a long time! :D

---

### Post by andrew.46 on 2009-11-26
Hi viking,

> **viking_maniac said:**
> I still think that I can write _success_ at this point! Thanks to andrew.46!

Excellent news :). And thanks for your kind words!

Andrew

---

### Post by brandon88tube on 2009-11-27
Is it just me or does the new version of mplayer seem to get out of sync with the audio and video?

---

### Post by viking_maniac on 2009-11-30
I just discovered that SMPlayer has been removed from Wikipedia.

I don't hope they're pulling the plug on this GUI project?

---

### Post by andrew.46 on 2009-12-01
Hi brandon,

> **brandon88tube said:**
> Is it just me or does the new version of mplayer seem to get out of sync with the audio and video?

I have not experienced this, is this all videos or just some? **Edit:** Hmmm.... just saw the 'burnt beans', hope you can clear that up.......

Andrew

---

### Post by andrew.46 on 2009-12-01
Hi viking,

> **viking_maniac said:**
> I just discovered that SMPlayer has been removed from Wikipedia.

Indeed it appears the page has been deleted:

[http://en.wikipedia.org/wiki/SMPlayer](http://en.wikipedia.org/wiki/SMPlayer)

But I guess the way is open for any enthusiast to add the page back in?

Andrew

---

### Post by Linuxforall on 2009-12-01
The SM Player website is working fine and RVM regularly posts at this thread so maybe we will hear from him.

---

### Post by rvm4000 on 2009-12-01
The smplayer page in the wikipedia has already been deleted several times. It seems they don't like it.

---

### Post by viking_maniac on 2009-12-01
> **rvm4000 said:**
> The smplayer page in the wikipedia has already been deleted several times. It seems they don't like it.

Strange! :confused:

---

### Post by andrew.46 on 2009-12-02
Hmmm.... I did not realise that Karmic has a little script called as:

```
sudo add-apt-repository ppa:xxxxx
```

but it certainly simplifies adding PPA's and I have added this syntax to the guide for calling rvm's PPA + SMPlayer.

Andrew

---

### Post by viking_maniac on 2009-12-06
andrew.46, I see that you recommend Pulse audio, as in ao=pulse, in the mplayer config.

I can see in the SMPlayer's configuration that Alsa is the default. I can also choose Alsa 0.0-0.4 Creative X-Fi. The default Also makes the mplayer crash sometimes, but it doesn't crash on e.g. Pulse and the Alsa setting 0.0 Creative X-Fi. What are these settings and why have you recommended Pulse?

I'm also wondering about the x11 video output, because I see a lot to choose from, and some makes the mplayer crash. Not x11 though! :)

---

### Post by andrew.46 on 2009-12-07
Hi viking_maniac,

I have placed those 2 settings in the guide not so much because I believe that they are the best options but because it seems to me that on Karmic Koala these are the settings most likely to work with no problems. I will admit that on another distro that I run with the svn MPlayer I use xv and alsa. xv in particular seems broken in Karmic and I am not entirely sure why...

All the best,

Andrew

---

### Post by Bachstelze on 2009-12-07
> **andrew.46 said:**
> xv in particular seems broken in Karmic and I am not entirely sure why...

Works fine here.

---

### Post by macey on 2009-12-09
Hello again Andrew, can this guide be used on Ubuntu Moblin Remix Developer Edition 9.10?
Thanks.

---

### Post by andrew.46 on 2009-12-10
Hi macey,

> **macey said:**
> can this guide be used on Ubuntu Moblin Remix Developer Edition 9.10?

I am afraid that up until now I had not heard of this version of Ubuntu :). Perhaps someone on this thread might know a little more about the svn MPlayer and this Ubuntu variant?

Andrew

---

### Post by macey on 2009-12-10
> **andrew.46 said:**
> Hi macey,



I am afraid that up until now I had not heard of this version of Ubuntu :). Perhaps someone on this thread might know a little more about the svn MPlayer and this Ubuntu variant?

Andrew



[URL="http://cdimage.ubuntu.com/ubuntu-moblin-remix/daily-live/current/"]http://cdimage.ubuntu.com/ubuntu-moblin-remix/daily-live/current/ 
[/URL]

[[URL="http://ubuntuforums.org/forumdisplay.php?f=376"]http://ubuntuforums.org/forumdisplay.php?f=376]("http://moblin.org/community/blogs/imad/2009/moblin-v20-beta-netbooks-and-nettops-its-here")      

[http://moblin.org/community/blogs/imad/2009/moblin-v20-beta-netbooks-and-nettops-its-here](http://moblin.org/community/blogs/imad/2009/moblin-v20-beta-netbooks-and-nettops-its-here)
[/URL] I think these last two links are referring to 9.04


[http://ubuntuforums.org/showthread.php?t=1279907]("http://ubuntuforums.org/showthread.php?t=1279907")

---

### Post by stevenpusser on 2009-12-12
> **andrew.46 said:**
> Hi viking,



Unfortunately no. The deb package produced by checkinstall is a little primitive and not suited to this purpose. To create such a package you would need to look into creating a formal package and for this most would look at modifying the files in the debian/ section of the source code. Unfortunately I have no experience in the creation of such packages, perhaps others on this thread can guide you?

Andrew

I do a lot of packaging for the Mepislovers community repo, and once you get the hang of it, doing a "proper" deb package is much easier and works better than a checkinstall deb.

You can use this for a reference:  [http://www.mepis.org/docs/en/index.php/Mepis_Package_Building_Guide#3.__Backporting_from_Ubuntu_Repository](http://www.mepis.org/docs/en/index.php/Mepis_Package_Building_Guide#3.__Backporting_from_Ubuntu_Repository)

and ignore all the stuff about GPG signing and changing the name of the maintainer if you are just building personal proper debs.

The important things are installing the packaging tools, getting and extracting the source files (.dsc, .diff.gz, and the orig.tar.gz), installing the build-depends with the pbuilder command, then building the package(s).  If you are making a new package from a new svn pull, rename the new source folder to reflect an update from the older one, then use the /debian folder from the older extracted source in the new source tarball, and update the /debian/changelog file to the new versioning.   Since the source code may be different, patches in /debian/patches may no longer apply, and you will have to disable broken ones, or refresh them (but that's another topic).

Just use the "debuild binary" command to create the packages, since you don't need new source packages.

---

### Post by Bachstelze on 2009-12-13
For a more Ubuntu-centric guide:

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

### Post by stevenpusser on 2009-12-17
Thanks for the Ubuntu Guide---once you know what to type in, you can get a new package started building in less than a minute.

---

### Post by andrew.46 on 2009-12-23
Hi,

A question from me for a change :). Has anybody tried compiling the svn MPlayer against the external libass libraries [here]("http://code.google.com/p/libass/")? I will admit that I am not entirely clear of the relationship between this external library and the internal libass that ships with the svn source. Any comments?

Andrew

---

### Post by t.alex on 2009-12-23
hi,

according to this 
-> [http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-December/078440.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-December/078440.html)
those libraries (and a lot more) are already in git mplayer, which is fairly easy to build
```

git clone git://repo.or.cz/mplayer-build.git
cd mplayer-build/
./enable-mt
./init --shallow
make

```

---

### Post by StivnC on 2009-12-23
Hi
Thanks for the Howto, but i have a problem that the video plays too fast and the sound plays at the right speed.
if you could help it would be great.
Thanks
StivnC

---

### Post by Bachstelze on 2009-12-23
> **StivnC said:**
> Hi
Thanks for the Howto, but i have a problem that the video plays too fast and the sound plays at the right speed.
if you could help it would be great.
Thanks
StivnC

Where does the video come from? A/V desynchronization usually means it has VFR which has not been handled correctly.

---

### Post by andrew.46 on 2009-12-23
Hi t.alex,

> **t.alex said:**
> according to this 
-> [http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-December/078440.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-December/078440.html)
those libraries (and a lot more) are already in git mplayer, which is fairly easy to build


It would be nice if the MPlayer developers could reach an understanding and absorb these changes into a *single* development stream...

Andrew

---

### Post by StivnC on 2009-12-23
> **Bachstelze said:**
> Where does the video come from? A/V desynchronization usually means it has VFR which has not been handled correctly.

The video comes from my phone, it a .3gp file

---

### Post by andrew.46 on 2009-12-23
Hi StivnC,

> **StivnC said:**
> The video comes from my phone, it a .3gp file

Is this file small enough to post somewhere?

Andrew

---

### Post by mc4man on 2009-12-23
> compiling the svn MPlayer against the external libass libraries

Only because I happened to have a recent static libass for testing with vlc 1.0.4 I tried a quick build of todays svn which failed on libass. 

The git mplayer mentioned previously  appears to use 0.9.8 libass and does build ok (but it is a fairly older -r of mplayer

The whole script build of the git is interesting though, as a side note amr will not be enabled in it and by default in karmic uses the 4.4 gcc.
(though there are config files for both ffmpeg and mplayer where these things can be addressed.

On an even further side note the lucid gstreamer ugly plug in will support amr, though ironically the lucid libavcodec probably will not and by extension any repo player that uses libavcodec

---

### Post by andrew.46 on 2009-12-23
Hi mc4man,

> **mc4man said:**
> Only because I happened to have a recent static libass for testing with vlc 1.0.4 I tried a quick build of todays svn which failed on libass.

Indeed it does :(. I have queried the[ MPlayer-users]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-December/078636.html")....

Andrew

---

### Post by mc4man on 2009-12-23
> Indeed it does...

What's sorta interesting is that from your previous link you come upon a 'patched' mplayer to use with the current libass.

The bump in the road there is it has no   ffmpeg sources, so you'd need to provide them in the source tree. Seems a bit of a pita to me, how you'd know what ffmpeg -r to use without building to see if sync was maintained..?

(obviously T&E would work, though I quess one could match the git to a date, ect.

---

### Post by StivnC on 2009-12-24
Hi Andrew
> **andrew.46 said:**
> 
Is this file small enough to post somewhere?
Andrew
I tried uploading one to the forums but it says invalid file type but you can download a .3gp file from here
[http://www.free-3gp-video.com/3gp/2008/06/20/beat-bearing.html](http://www.free-3gp-video.com/3gp/2008/06/20/beat-bearing.html)
Thanks
StivnC

---

### Post by andrew.46 on 2009-12-24
Hi StivnC,

> **StivnC said:**
> I tried uploading one to the forums but it says invalid file type but you can download a .3gp file from here
[http://www.free-3gp-video.com/3gp/2008/06/20/beat-bearing.html](http://www.free-3gp-video.com/3gp/2008/06/20/beat-bearing.html)


To upload to these forums just compress the file and it should be ok, the 'Upload' section will show what size the forums allow and the different formats. I was actually after the *specific* file that was causing you trouble rather than a generic 3gp sample :). 

Andrew

---

### Post by andrew.46 on 2009-12-24
Hi mc4man,

> **mc4man said:**
> Only because I happened to have a recent static libass for testing with vlc 1.0.4 I tried a quick build of todays svn which failed on libass. 

Looks like the MPlayer developers have attended to this issue and it now compiles cleanly. Now to play with it a little :).

Andrew

---

### Post by mc4man on 2009-12-24
> MPlayer developers have attended to this issue and it now compiles cleanly

that seemed like best solution rather than using older, patched -r's

I'd suggest (if doing on ubuntu), to build libass static only, if no issues then support will be built-in and no deps on a shared lib.

---

### Post by helpdeskdan on 2009-12-24
Bother!  Now, somehow mencoder is broken.  

dan@dan-desktop:~/temp$ mencoder
mencoder: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory

Can I build mencoder with these instructions?  Any suggestions greatly appreciated!

---

### Post by helpdeskdan on 2009-12-24
Oops!  I'm sorry!  This guide doesn't even INSTALL x264!  Apologies!  Nevertheless, I would be interested to hear if anybody got mencoder compiled.

---

### Post by Linuxforall on 2009-12-25
Mencoder works fine here with Acidrip.

don't put disable --mencoder during ./compile and for install the line should read 

sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`" --provides "mplayer,mencoder"

---

### Post by andrew.46 on 2009-12-25
Hi helpdeskdan,

> **helpdeskdan said:**
> dan@dan-desktop:~/temp$ mencoder
mencoder: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory

Can I build mencoder with these instructions?  Any suggestions greatly appreciated!

You can build MEncoder by simply omitting the  *--disable-mencoder* option and best to install a newer copy of libx264. I am running:
```

andrew@skamandros~$ x264 --version
x264 0.80.131 3feaec2
built on Dec 17 2009, gcc: 4.3.3
```

so that copy of x264 on your system is fairly dated. You would also be best to add the development libraries for lame and faac so encoding to mp3 and aac respectively is possible. So with a bit of fiddling it is possible :).

Andrew

---

### Post by mc4man on 2009-12-31
Andrew - 
A few things I noticed w/ the vlc-git that I'd thought I'd mention if you haven't already seen, ect.

( on 12-30

if you open the playlist I don't yet see a way to then not have vlc open on playlist.
If there isn't a gui setting, can be reset in ~/.config/vlc/vlc-qt-interface.conf w/ playlist-visible=0

Another handy thing is vlc's save playlist to file in either .m3u, .m3u8, .xspf
For it to work the default qt interface needs to be changed, default and gtk are no good, cleanlooks and probably the rest are
```
sudo apt-get install qt4-qtconfig
```
found in System -> Preferences

For cddb retreival on audio cd's the 'Album art download policy' should be set to 'as soon as track is added'
(glad to see they accepted adding cddb2 to 1.0.3 in lucid

the dmo loader is dying a slow death, has regressed a bit further from 1.0.4, fortunately the much more useful wma3 is in avcodec.
While i found a workaround for wmal, it's a bit unwieldly and none too important.

--http-caching seems to also be not as good as it should be, but that has happened since 1.0.X

For a few weeks about a month or so the latest live555 would not load in 1.0.3 or 4.
It was possible to revert the patch that caused it, then live555 itself semi reverted and changed so reverting wasn't possible.

Are you finding the livemedia plugin for current loading properly ( vlc -vv will show if not

Also I believe ( have to ck.) that the new libass3 won't build in 1.0.X,, did you get it into the git?


Edit: what also could prove interesting is that the skins2 interface could prove useful for some who have issues with the qt4 one - though there are obviously limitations based on individual skin chosen

---

### Post by andrew.46 on 2010-01-01
Hi mc4man,

Looks like I am without an Ubuntu installation for at least a little while and may be a little less active on these forums for a while as well. However I will build the git vlc on my remaining distro and investigate...

Andrew

---

### Post by mc4man on 2010-01-01
for 2 of them
Ctrl+l to close playlist

By default the audio cd device will be set to /dev/dvd, which while it will work tends to load tracks in wrong order. Needs to be changed in prefs. to /dev/cdrom or /dev/sr0 (or dev/cdrom1 or /dev/sr1
> Looks like I am without an Ubuntu installation for....

That is unfortunate for the folks here, sounds like equipment failure ..?

---

### Post by andrew.46 on 2010-01-02
Hi mc4man,

Only just now managed to get Slackware set with the git vlc and it is not a very fully featured one yet. Still working on the installation script which needs the various static libs sorted out...

> **mc4man said:**
> Are you finding the livemedia plugin for current loading properly ( vlc -vv will show if not

So far so good:

```

andrew@skamandros~$ **[COLOR="Red"]cvlc -l | grep 'live555'[/COLOR]**
VLC media player 1.1.0-git The Luggage
  live555                RTP/RTSP/SDP demuxer (using Live555)
  live555                RTSP/RTP access and demux

```

but I did note a segmentation fault with the following:

[http://www.abc.net.au/classic/ftgws/audio/ftgws_27122009.ram](http://www.abc.net.au/classic/ftgws/audio/ftgws_27122009.ram)

although the stream itself:

rtsp://media1.abc.net.au/classic/ftgws/ftgws_2012_2856ISDN2LAN1.rm

played well enough. I would be interested to see if you could reproduce this with you vcl 1.0?

> Also I believe ( have to ck.) that the new libass3 won't build in 1.0.X,, did you get it into the git?

Well, I compiled against libass 0.9.8, which I built from source, and the configure process picked it up and make did not complain. libass3 is a Debian/Ubuntu repackaging of the older version? (Excuse my ignorance of this one!)

```

andrew@skamandros~$ **[COLOR="Red"]cvlc -l | grep 'libass'[/COLOR]**
VLC media player 1.1.0-git The Luggage
  libass                 Subtitle renderers using libass

```

I have not had the opportunity to test the actual subtitles yet....

All the best,

Andrew

---

### Post by mc4man on 2010-01-02
> libass3 is ...
Yeah, that's the ubuntu package name (0.9.6), so good to know the newer ver. is good in the git.

> this with your vcl 1.0?
Will try later with a new live555 and git clone and current build (using a live555 from about 8 wks. ago

(generally speaking if vlc -vv doesn't report any plug-ins not loaded then things are good, ie. vlc will quite happily build modules even if they don't work
(Though occasionally also load ones that don't quite work.


From my prev. post, the issue with the filelist not toggling from the 'view' tab has resolved itself w/ a new build this morning.
Points to one thing that will arise - behaviour using a 1.1-git can and will vary from ver. to ver.

That may present some 'challenges' in terms of support of a how-to..

(possibly using a nightly build from trunk would provide some repeatability in terms of a date.

Did a build today using your ffmpeg PKG_CONFIG method, worked fine, I like it for this and well, overall

---

### Post by andrew.46 on 2010-01-02
Hi mc4man,

> **mc4man said:**
> Did a build today using your ffmpeg PKG_CONFIG method, worked fine, I like it for this and well, overall

Strictly speaking not actually my idea :). If you have a look at [alienBOB's script]("http://connie.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild") you will see that he installs just about  *all* of the vlc dependencies not available in a stock Slackware installation into $VLCDEPSDIR:

```

# We will be installing static libs into the following directory:
mkdir -p $TMP/tmp-$PRGNAM/vlcdeps/usr/{bin,doc,include,lib,man}
VLCDEPSDIR="$TMP/tmp-$PRGNAM/vlcdeps"

```

and then loads this directory from the vlc ./configure:

```
PKG_CONFIG_PATH="$VLCDEPSDIR/usr/lib${LIBDIRSUFFIX}/pkgconfig"
```

(LIBDIRSUFFIX is to cater for 64bit installation). I use the same idea for x264 and FFmpeg but I will extend the idea a little I think. You will see on this page where I stole the FFmpeg configure syntax from as well :).

Andrew
Andrew

---

### Post by mc4man on 2010-01-02
As far as the stream- will need to look at/listen again - have to go out, but...

the 1st link (http
mplayer - perfect
vlc 1.1- git with older live - segfaults
vlc 1.0.4 - perfect

the 2nd link
all 3 play but no audio is heard (even though blocks are decoded) but if I use this instead, then plays perfectly

```
rtsp://media1.abc.net.au/classic/ftgws/ftgws_2[COLOR="Blue"]7[/COLOR]12_2856ISDN2LAN1.rm

```

So definitely an issue with the http link in 1.1, though on a positive note it will play the rtsp

---

### Post by andrew.46 on 2010-01-03
Hi mc4man,

Actually I will admit that I was not really aware how much of a 'beta' the development version of vlc truly is. Anyway it has been a fascinating exercise building it from source and I suspect I will keep tinkering with it :).

Andrew

---

### Post by helpdeskdan on 2010-01-03
> **andrew.46 said:**
> Hi helpdeskdan,



You can build MEncoder by simply omitting the  *--disable-mencoder* option and best to install a newer copy of libx264. I am running:
```

andrew@skamandros~$ x264 --version
x264 0.80.131 3feaec2
built on Dec 17 2009, gcc: 4.3.3
```

so that copy of x264 on your system is fairly dated. You would also be best to add the development libraries for lame and faac so encoding to mp3 and aac respectively is possible. So with a bit of fiddling it is possible :).

Andrew

Sorry to post so late, but I wanted to say thanks to you and Linuxforall for the advice!  I did not try it yet, I actually removed medibuntu and then reinstalled ffmpeg which removed/reinstalled a bunch of packages.  This solved my problem.  (Medibuntu has never given me problems before, how odd - I wonder if anybody else is having that problem.  Medibuntu removed mencoder from their repo)  I plan to try it when I get some time to compile, thanks guys!

---

### Post by Linuxforall on 2010-01-03
> **helpdeskdan said:**
> Sorry to post so late, but I wanted to say thanks to you and Linuxforall for the advice!  I did not try it yet, I actually removed medibuntu and then reinstalled ffmpeg which removed/reinstalled a bunch of packages.  This solved my problem.  (Medibuntu has never given me problems before, how odd - I wonder if anybody else is having that problem.  Medibuntu removed mencoder from their repo)  I plan to try it when I get some time to compile, thanks guys!

The credit fully goes to andrew46 and his superb guide, I just added the lines but glad it worked out for you.

---

### Post by andrew.46 on 2010-01-05
Hi mc4man,

> **mc4man said:**
> So definitely an issue with the http link in 1.1, though on a positive note it will play the rtsp

I left [a note]("http://forum.videolan.org/viewtopic.php?f=13&t=70103") on the vlc forums although I am not sure if this is the right place.

On another note I compiled against libfluidsynth which had no problem but I gather midi playback is still not possible in 1.1.0?

Andrew

---

### Post by mc4man on 2010-01-05
> but I gather midi playback is still not possible in 1.1.0?

Not sure - here's a [thread]("http://forum.videolan.org/viewtopic.php?f=7&t=37097") that spans a year+ that seems to imply that it can

Some sample [midi's]("https://www.hitbit.com/titel/%5Eo/T:Titel+O/C:f8c7bd71ad66f3e") (demo's
By habit I've always disabled since 0.9.X so can't try atm

As far as the wmal, it works here also but only 1 track per vlc instance, if for example I put 2 in a folder and opened the folder in vlc - track 1 plays, track 2 plays but no audio...

wmas seems totally broken here in 1.0.X and 1.1

I'm **somewhat** tempted to try one last time to request a higher ffmpeg ver. in lucid than the current same as karmic one, guess I'll wait till alpha2, though the window will close very quickly.
Seeing as though it was rejected in karmic for fears of regressions I may not bother.
Though they could of gone up to -r 19777 before anything broke. (r 19778+ broke native wma3 in vlc 1.0.2, restored in 1.0.3) and could easily go higher in lucid

(would be a boon to 32 and 64 bit users of both the repo versions of vlc and mplayer, dmo for vlc in lucid isn't going to happen - made 3 requests for the lucid vlc, 2 were implemented but dmo wasn't.

---

### Post by andrew.46 on 2010-01-05
Hi mc4man,

> **mc4man said:**
> 
Some sample [midi's]("https://www.hitbit.com/titel/%5Eo/T:Titel+O/C:f8c7bd71ad66f3e") (demo's
By habit I've always disabled since 0.9.X so can't try atm

Thanks for that. Well I certainly can't get midi files to play, I shall continue to investigate...

> wmas seems totally broken here in 1.0.X and 1.1

All wmas? I tried the following:

[http://samples.mplayerhq.hu/A-codecs/WMA/Bangles](http://samples.mplayerhq.hu/A-codecs/WMA/Bangles) 01 - Walk Like An Egyptian.wma

and it worked well enough, my apologies for inflicting The Bangles on you :). The current vlc has a problem letting go of the sound system I have noted which is a bit painful but the price of the bleeding edge I guess, this could be the problem when playing 2 wmals? BTW I attach (yet another) screenshot to show this playing only because I have managed to get goom to roar into life :).

> (would be a boon to 32 and 64 bit users of both the repo versions of vlc and mplayer, dmo for vlc in lucid isn't going to happen - made 3 requests for the lucid vlc, 2 were implemented but dmo wasn't.

The limitations imposed on by a distro seem to be 50% of the work of the media section of this forum. I understand the need for some of these limitations but it can be very frustrating.

BTW [http://www.abc.net.au/classic/ftgws/audio/ftgws_27122009.ram](http://www.abc.net.au/classic/ftgws/audio/ftgws_27122009.ram) now plays with no error. Not sure how much credit my post has with this one...

**Edit:** Woo hoo! Looks like it was [my report]("http://forum.videolan.org/viewtopic.php?f=13&t=70103") that did it.


All the best,

Andrew

---

### Post by mc4man on 2010-01-05
> All wmas? I tried....

Sorry, my way of saying wma speech or maybe more properly wma voice - 
[http://samples.mplayerhq.hu/A-codecs/WMSP/](http://samples.mplayerhq.hu/A-codecs/WMSP/)

wma2 is always good - (avcodec

.......................................

Am running page 1 on a lucid install, probably way too premature for various reasons, the least of which is no working lucid repo support as of yet for nvidia

Only change on the one that's making now was removing the 4 from the libxvidcore4-dev and not using libgl1-mesa-dev

Edit: works fine on this lucid install, while have to try on another that's using diff.  nvidia drivers ( this one has what may be similar to what's released - where atm, while the vdpau headers and lib is installed, mplayer can't find/use properly

only oddity from cli that had no effect - 
> bt_audio_service_open: connect() failed: Connection refused (111)


---

### Post by andrew.46 on 2010-01-06
Hi mc4man,

> **mc4man said:**
> Am running page 1 on a lucid install, probably way too premature for various reasons, the least of which is no working lucid repo support as of yet for nvidia

Only change on the one that's making now was removing the 4 from the libxvidcore4-dev and not using libgl1-mesa-dev-

Sounds good, I suspect I will have nothing of great note to add to the svn MPlayer under Lucid, probably the compiler will be greater than 4.4.1 so that will lessen complication.

BTW midi playback is in place now with vlc, I did not realise that I had to manually add some soundfonts and then source them from within vlc. Some decent links for anybody ever researching this one:

MIDI with VLC media player
[http://www.remlab.net/op/vlc-midi.shtml](http://www.remlab.net/op/vlc-midi.shtml)

Soundfonts for Linux 
[http://www.personalcopy.com/home.htm](http://www.personalcopy.com/home.htm)

Andrew

---

### Post by mc4man on 2010-01-07
> this could be the problem when playing 2 wmals?
It's 'difficulty' in that area seems to be a bit different in the 1.1 than 1.0.X, 
In 1.1. I get playback everytime if it's a new instance of vlc, if it's the same instance then it's every other attempt. (sound, no sound, sound. ect.
So in 1.1 it seems could be related to the sound device, (at least in part.

In the 1.0.X it also varies from release to release, though 1 instance per track always works, the qt4 interface also seems to be a factor there.
( if I ever 'lose' the playback, removing the geometry=@ByteArray lines in ~/.config/vlc/vlc-qt-interface.conf usually restores it. (or just deleting the file itself.

> aware how much of a 'beta' the development version of vlc truly is

The little ups and downs don't seem to be of major consequence, and it's certainly an interesting and ambitious version

Though possibly many would find the predictability of a release more suitable. (And if you're inclined to do a how-to of sorts depending on interest/time it certainly would be 'valid' for both method wise.

Edit: you post did bring about the http > rtsp fix, I'm going to have to ck. out the commit, curious to see what it was, (though may be greek to me

---

### Post by andrew.46 on 2010-01-07
Hi mc4man,

> **mc4man said:**
> In 1.1. I get playback everytime if it's a new instance of vlc, if it's the same instance then it's every other attempt. (sound, no sound, sound. ect.
So in 1.1 it seems could be related to the sound device, (at least in part.

I believe I have solved this one after having noticed the same effect. Caught an error message about alsa-lib versions and the failure of vlc 1.1.0-git to 're-initialise' sound. The solution was to compile vlc against [the latest alsa-lib]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2") and this rectified the problem completely on my system. I would be very interested to see if this fix also works for you?

> Edit: you post did bring about the http > rtsp fix, I'm going to have to ck. out the commit, curious to see what it was, (though may be greek to me

Always a little exciting :). If you run the following from your local vlc git:

```
git show 5cf2bcd602bdae96ec59c47773fb8332d3a23bff
```

the details will be revealed :).

Andrew

---

### Post by mc4man on 2010-01-07
> if this fix also works for you?
Atm no change to the previous behavior, though the 1.1 debug does show something not seen in 1.0.X

first play of any track - in this case wmal, sound is output
> 0xb7500618] main input debug: Stream buffering done (371 ms in 0 ms)
[0xb7500618] main input debug: [COLOR="Blue"]creating aout[/COLOR]
[0x942ea88] main audio output debug: looking for audio output module: 6 candidates


2nd track of any format - in this case wmap - with sound

> [0xb2402130] main input debug: Stream buffering done (586 ms in 0 ms)
[0xb2402130] main input debug: [COLOR="Blue"]reusing[/COLOR] aout
[0x942ea88] main audio output debug: looking for audio output module: 6 candidates

now trying a wmal again - no sound output
> [0xb24041f8] main input debug: Stream buffering done (371 ms in 0 ms)
[0x93e3b40] dmo decoder debug: ProcessInput(): not accepting
[0x93e3b40] dmo decoder debug: ProcessInput(): not accepting

Again trying wmal - sound is output
> [0x867fd28] main input debug: Stream buffering done (371 ms in 0 ms)
[0x867fd28] main input debug: [COLOR="Blue"]reusing aout
[/COLOR]

I'm going to try again tom. on diff. machine

> completely on my system.
Is there any quick description of the system, do you have pulseaudio involved, ect.
Did you do a static alsa-lib or replace the system libs, -dev ?

---

### Post by andrew.46 on 2010-01-08
Hi mc4man,

> **mc4man said:**
> Is there any quick description of the system, do you have pulseaudio involved, ect.
Did you do a static alsa-lib or replace the system libs, -dev ?

A quick reply as work calls.... The system is the one I have retreated to at least temporarily: Slackware 13.0 and thus there are no dev files. Replaced the system alsa-lib with a fresh install using [the existing slackbuild script]("http://slackware.osuosl.org/slackware-current/source/l/alsa-lib/alsa-lib.SlackBuild") updated with new version number. I will investigate further on days off, I note the gui still has a few hiccups while commandline failure free. 

Andrew

---

### Post by andrew.46 on 2010-01-10
Hi mc4man,

When using cvlc I have been using *--play-and-exit* set as an alias in ~/.bashrc:

```
alias cvlc='cvlc --play-and-exit'
```

This seems to get around the sound problems from the commandline. But as you have also mentioned there are some odd sound issues for me *from the gui* i.e. no sound for the 2nd file. 

Andrew

---

### Post by e_man on 2010-01-10
I tried to follow this tutorial but I ran into some problems.
After trying to compile, I got an error message.

```
./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-mencoder
make
```This is the error message at the end:

```
libavcodec/libavcodec.a(snow.o): In function `encode_init':
snow.c:(.text.unlikely+0x78f): undefined reference to `h263_encode_init'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```Then, I wasnt able to install.

```
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"

libavcodec/libavcodec.a(snow.o): In function `encode_init':
snow.c:(.text.unlikely+0x78f): undefined reference to `h263_encode_init'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```Hope anyone can help

---

### Post by mc4man on 2010-01-10
> After trying to compile, I got an error message.

Typically when you see those type of errors "undefined reference..." it's because mplayer has fell out of snyc with ffmpeg

Just wait awhile and try again, it's usually fixed quickly

For instance just tried and all seems well with revision 30271.(or higher

Either checkout a new source or just cd to your mplayer folder and first clean the source
```
make distclean
```
and then update the sources and proceed with the configure and make
```
svn up
```

Ex. 
> doug@doug-laptop:~/Desktop/mplay11/mplayer$ svn up
U............
A listing of files updated
.............ect.
Updated to revision 30271.
doug@doug-laptop:~/Desktop/mplay11/mplayer$ ./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-mencoder


---

### Post by mc4man on 2010-01-10
> When using cvlc I have been using --play-and-exit.....

I had been using something similar since 1.0.0, just for a nautilus action. (r. click on file.
Atm w/ 1.1 and 1.0.4 the gui works in the same vein - but only once for sure.

So while there has been some improvement since 1.0.0 for the most part it's the same as when we posted about on the vlc forum a ways back - basically 1 play per vlc instance will always work, after that less likely.

Spent some time seeing how changes to the mesa-libs would affect vlc (1.0.4, 1.1) amd mplayer builds on lucid. -  vlc 1.0.4 and mplayer both needed a little help enabling openGl output (which I don't use myself), vlc 1.1 didn't  - Though not really up on what xcb wrappers are anyway

I remember seeing you may have had issues xv output, what does 1.1 give you ( as seen in the debug output, not in settings

---

### Post by e_man on 2010-01-10
> **mc4man said:**
> Typically when you see those type of errors "undefined reference..." it's because mplayer has fell out of snyc with ffmpeg

Just wait awhile and try again, it's usually fixed quickly

For instance just tried and all seems well with revision 30271.(or higher

Either checkout a new source or just cd to your mplayer folder and first clean the source
```
make distclean
```and then update the sources and proceed with the configure and make
```
svn up
```Ex.

I just tried and it didnt work. I'll wait and try again tomorrow.

---

### Post by andrew.46 on 2010-01-11
Hi e_man,

> **e_man said:**
> I just tried and it didnt work. I'll wait and try again tomorrow.

Hmmm.... should definitely be ok now as like mc4man I have just successfully compiled:

```

andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r30271-4.3.3 (C) 2000-2009 MPlayer Team
```

If troubles persist try simply removing the svn MPlayer source code and starting again with:

```
$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

I note that you ran checkinstall as well and on a few occasions I have found a failed checkinstall run can produce a bit of a mess in the source tree.

Andrew

---

### Post by andrew.46 on 2010-01-11
Hi mc4man,

> **mc4man said:**
> So while there has been some improvement since 1.0.0 for the most part it's the same as when we posted about on the vlc forum a ways back - basically 1 play per vlc instance will always work, after that less likely.

Looks like I misunderstood what you meant with the second playing of the wmal file. Certainly on the most recent git on my system this file fails consistently on the commandline when the request is to play it *twice*. I have crossed my fingers and posted again:

[http://forum.videolan.org/viewtopic.php?f=13&t=70420](http://forum.videolan.org/viewtopic.php?f=13&t=70420)

Just noticed the forum software snipped the title :(. Anyway I suspect the magic part of the title is 'vlc 1.1.0-git' which I suspect is skimmed for by the developers. There is something more going on with the dmo issue of course but this seems like a nice solid bug report that will hopefully get seen and acted upon...

> I remember seeing you may have had issues xv output, what does 1.1 give you ( as seen in the debug output, not in settings

I had some issues with the Ubuntu MPlayer and xv output, although this is running on VirtualBox so I am not sure if this is the culprit. This problem persists on Karmic via VirtualBox with the git vlc:

```

[0x9e09c10] xcb_xv generic debug: connected to X11.0 server
[0x9e09c10] xcb_xv generic debug:  vendor : The X.Org Foundation
[0x9e09c10] xcb_xv generic debug:  version: 10604000
[0x9e09c10] xcb_xv generic debug: using screen 0xff
[0x9e09c10] xcb_xv generic debug: using XVideo extension v2.2
[0x9e09c10] xcb_xv generic error: no available XVideo adaptor

```

while on the host system of Slackware there is no trouble:

```

[0x82c99b8] xcb_xv generic debug: connected to X11.0 server
[0x82c99b8] xcb_xv generic debug:  vendor : The X.Org Foundation
[0x82c99b8] xcb_xv generic debug:  version: 10603000
[0x82c99b8] xcb_xv generic debug: using screen 0x10b
[0x82c99b8] xcb_xv generic debug: using XVideo extension v2.2
[0x82c99b8] xcb_xv generic debug: cannot grab port 80
[0x82c99b8] xcb_xv generic debug: using adaptor Intel(R) Textured Video
[0x82c99b8] xcb_xv generic debug: using port 81
[0x82c99b8] xcb_xv generic debug: using image format 0x30323449

```

I am not sure the exact problem but I suspect my video adapter and the Ubuntu kernel or perhaps just an odd quirk of virtualisation...

Andrew

---

### Post by mc4man on 2010-01-11
> There is something more going on with the dmo issue
It may just be one of those 'unknowns' that could inadvertantly be resolved or never.

I even tried seeing if a fully buffered stream would play twice - still only the first time, after playback clicking the play button - still no go

```
vlc --http-caching 6000 http://download.linnrecords.com/test/wma/recit24bit.aspx
```

More for curiosity sake - these play fine on vlc 1.0.4, 1.1 has a bit of a problem here  - seems to be pulse
(A little extra caching seems needed even though they're short demo clips

```
vlc --http-caching 6000 http://download.linnrecords.com/test/flac/ForUntoUsSurround88.aspx

```
```
vlc --http-caching 6000 http://download.linnrecords.com/test/flac/test192.aspx
```

of small note:
they've finally updated liblivemedia-dev to a fairly current version (11/27) in lucid, what's interesting is the repo vlc is build depend (built off of) on liblivemedia-dev, but a repo mplayer isn't

---

### Post by e_man on 2010-01-11
Hi andrew.46,

> **andrew.46 said:**
> Hi e_man,



Hmmm.... should definitely be ok now as like mc4man I have just successfully compiled:

```

andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r30271-4.3.3 (C) 2000-2009 MPlayer Team
```If troubles persist try simply removing the svn MPlayer source code and starting again with:

```
$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```I note that you ran checkinstall as well and on a few occasions I have found a failed checkinstall run can produce a bit of a mess in the source tree.

Andrew

  I'm still having trouble. I just tried to install nogui and got this error:

```
emil@emil-htpc:~$ mplayer -vo vdpau -vc ffh264vdpau movie.mkv
The program 'mplayer' is currently not installed.  You can install it by typing:
sudo apt-get install mplayer-nogui
mplayer: command not found
emil@emil-htpc:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: mplayer-nogui but it is not going to be installed
           Depends: libasound2 (> 1.0.22) but 1.0.20-3ubuntu6.1 is to be installed
           Depends: libatk1.0-0 (>= 1.29.3) but 1.28.0-0ubuntu1 is to be installed
           Depends: libesd0 (>= 0.2.35)
           Depends: libjack0 (>= 0.118+svn3796) but 0.116.1-4ubuntu2 is to be installed
E: Broken packages
```How do I remove the svn source code?

---

### Post by andrew.46 on 2010-01-11
Hi e_man,

> **e_man said:**
> How do I remove the svn source code?

If you have followed this guide exactly the MPlayer svn code should be in $HOME/mplayer.

Andrew

---

### Post by mc4man on 2010-01-11
@ eman
none-withstanding your issue with building mplayer (though possibly related)
you're showing an attempted repo mplayer install that's depending on lucid versions of some libs...?

If you're not on lucid A1+ then possibly this may prove informative
```

cat /etc/apt/sources.list
```

and possibly this also
```
ls /etc/apt/sources.list.d
```

---

### Post by vidkun on 2010-01-11
I'm running on Linux Mint 8 x86_64 and followed the guide regarding building the svn mplayer. I've checked out multiple times throughout the day, making sure that I am getting updated revisions. I can config and make just fine, but when I run sudo make install (I haven't been using the checkinstall, call me old fashioned) I keep getting failures with the following:

```
vidkun@tyr ~/mplayer $ sudo make install
[sudo] password for vidkun: 
make -C libavformat
make[1]: Entering directory `/home/vidkun/mplayer/libavformat'
gcc-4.3 -DHAVE_AV_CONFIG_H -I.. -I..  -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2  -I/usr/local/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o os_support.o os_support.c
In file included from os_support.c:42:
network.h:71:6: warning: "HAVE_STRUCT_SOCKADDR_STORAGE" is not defined
In file included from os_support.c:42:
network.h:72: error: redefinition of 'struct sockaddr_storage'
network.h:77:6: warning: "HAVE_STRUCT_ADDRINFO" is not defined
network.h:78: error: redefinition of 'struct addrinfo'
network.h:135:6: warning: "HAVE_GETADDRINFO" is not defined
os_support.c:63:6: warning: "HAVE_GETADDRINFO" is not defined
os_support.c:182:5: warning: "HAVE_GETADDRINFO" is not defined
make[1]: *** [os_support.o] Error 1
make[1]: Leaving directory `/home/vidkun/mplayer/libavformat'
make: *** [libavformat/libavformat.a] Error 2
vidkun@tyr ~/mplayer $ 

```

Any ideas what the issue may be? I have been looking for a few hours now and not having any luck find much useful. Thanks!

---

### Post by e_man on 2010-01-11
> **mc4man said:**
> @ eman
none-withstanding your issue with building mplayer (though possibly related)
you're showing an attempted repo mplayer install that's depending on lucid versions of some libs...?

If you're not on lucid A1+ then possibly this may prove informative
```

cat /etc/apt/sources.list
```and possibly this also
```
ls /etc/apt/sources.list.d
```

Ok this is what I get.

```
emil@emil-htpc:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
emil@emil-htpc:~$ ls /etc/apt/sources.list.d
medibuntu.list                     rvm-smplayer-karmic.list
medibuntu.list.save                rvm-smplayer-karmic.list.save
nvidia-vdpau-ppa-karmic.list       team-xbmc-ppa-karmic.list
nvidia-vdpau-ppa-karmic.list.save  team-xbmc-ppa-karmic.list.save

```

---

### Post by mc4man on 2010-01-11
e_man

As far as your sudo apt-get install mplayer attempt - 
the mplayer .deb is being provided from here
> deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) lucid main

Why you have the lucid ppa enabled you'd know I guess ((unless it was done inadvertently - you won't be able to satisfy the install deps from what is basically a karmic install.

---

### Post by andrew.46 on 2010-01-11
Hi vidkun,

> **vidkun said:**
> Any ideas what the issue may be? I have been looking for a few hours now and not having any luck find much useful. Thanks!

Compilation is broken for me as well at the moment. Best advice is to restore your backup from a previous install and sit tight for a day...

Andrew

---

### Post by mc4man on 2010-01-11
Andrew - happened to just notice something, though I may be mis- understanding.
The disable-mencoder doesn't prevent building in libx264 support if the headers are present. (fairly likely

I've taken to adding --disable-x264 to the configure

---

### Post by andrew.46 on 2010-01-12
Hi mc4man,

> **mc4man said:**
> I've taken to adding --disable-x264 to the configure

Thanks, I have added this to the guide.

Andrew

---

### Post by mc4man on 2010-01-12
This may be the trac relating to wmal,  dmo in general
[http://trac.videolan.org/vlc/ticket/2945](http://trac.videolan.org/vlc/ticket/2945)

( at least it hasn't received Bugs Paradize

---

### Post by e_man on 2010-01-12
> **mc4man said:**
> e_man
 
As far as your sudo apt-get install mplayer attempt - 
the mplayer .deb is being provided from here
 
 
Why you have the lucid ppa enabled you'd know I guess ((unless it was done inadvertently - you won't be able to satisfy the install deps from what is basically a karmic install.
 
Thanks for the tip. I didnt realize it. ...sorry I'm atotal noob in this

---

### Post by vidkun on 2010-01-12
> **andrew.46 said:**
> Hi vidkun,



Compilation is broken for me as well at the moment. Best advice is to restore your backup from a previous install and sit tight for a day...

Andrew

Just an update, late last night it got to the point where make was failing. Today, I am back to successfully completing make, but make install still fails with the same error. It is strange to me that the make is fine, but make install fails. Annoying.

---

### Post by mc4man on 2010-01-12
Re: current errors
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-January/078804.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-January/078804.html)

---

### Post by vidkun on 2010-01-12
> **mc4man said:**
> Re: current errors
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-January/078804.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-January/078804.html)

Yeah I just found that a few minutes ago. There is a suggested hack of adding to your libavformat/network.h:
```
#define HAVE_STRUCT_SOCKADDR_STORAGE 1
#define HAVE_STRUCT_ADDRINFO 1
#define HAVE_GETADDRINFO 1


#if HAVE_WINSOCK2_H

```
Doing so gets me further than before. Now I get failures at the following during make:
```
tream/stream_ffmpeg.o libmpcodecs/ad_libdca.o libdvdcss/css.o libdvdcss/device.o libdvdcss/error.o libdvdcss/ioctl.o libdvdcss/libdvdcss.o libmpcodecs/ad_libmad.o libmpcodecs/vd_libmpeg2.o libmpeg2/alloc.o libmpeg2/cpu_accel.o libmpeg2/cpu_state.o libmpeg2/decode.o libmpeg2/header.o libmpeg2/idct.o libmpeg2/motion_comp.o libmpeg2/slice.o libmpeg2/idct_mmx.o libmpeg2/motion_comp_mmx.o libmpcodecs/vf_pp.o stream/stream_smb.o libmpcodecs/vd_theora.o libmpdemux/demux_mng.o libmpcodecs/ad_mp3lib.o mp3lib/sr1.o mp3lib/decode_mmx.o mp3lib/dct64_sse.o stream/stream_rtsp.o stream/freesdp/common.o stream/freesdp/errorlist.o stream/freesdp/parser.o stream/librtsp/rtsp.o stream/librtsp/rtsp_rtp.o stream/librtsp/rtsp_session.o osdep/shmem.o stream/stream_netstream.o stream/asf_mmst_streaming.o stream/asf_streaming.o stream/cookies.o stream/http.o stream/network.o stream/pnm.o stream/rtp.o stream/udp.o stream/tcp.o stream/stream_rtp.o stream/stream_udp.o stream/realrtsp/asmrp.o stream/realrtsp/real.o stream/realrtsp/rmff.o stream/realrtsp/sdpplin.o stream/realrtsp/xbuffer.o libmpcodecs/vd_mpng.o stream/stream_pvr.o libmpcodecs/ad_realaud.o libmpcodecs/vd_realvid.o libmpcodecs/ad_speex.o stream/cache2.o tremor/bitwise.o tremor/block.o tremor/codebook.o tremor/floor0.o tremor/floor1.o tremor/framing.o tremor/info.o tremor/mapping0.o tremor/mdct.o tremor/registry.o tremor/res012.o tremor/sharedbook.o tremor/synthesis.o tremor/window.o stream/stream_tv.o stream/tv.o stream/frequencies.o stream/tvi_dummy.o stream/tvi_v4l.o stream/audio_in.o stream/tvi_v4l2.o unrar_exec.o stream/stream_vcd.o libmpcodecs/ad_libvorbis.o libmpdemux/demux_ogg.o stream/stream_vstream.o libmpcodecs/vd_xanim.o libmpcodecs/vd_xvid4.o libavformat/libavformat.a libavcodec/libavcodec.a libavutil/libavutil.a libpostproc/libpostproc.a libswscale/libswscale.a -Wl,-z,noexecstack  -ffast-math   -lncurses -lsmbclient -lpng -lz -lmng -lz -ljpeg -lungif -lasound -ldl -lpthread -lcdda_interface -lcdda_paranoia -lfreetype -lz -lfontconfig  -lfribidi -lz -llzo2 -lmad -lspeex -L/usr/local/lib -ltheora -logg   -ldca -lopencore-amrnb -lopencore-amrwb -lxvidcore -lm -lschroedinger-1.0 -lpthread -loil-0.3 -lm -lrt   -lvstream-client -lpthread -ldl -rdynamic -L/usr/lib  -lm  -ldirectfb -lXext -lX11 -lpthread -lXv -lvdpau -lXinerama -lXxf86vm -lXxf86dga -laa -lcaca -lvga -lGL -ldl -lSDL -lesd -laudio -lXt -lpulse -ljack -lopenal -lfaac -lx264 -lpthread
libavcodec/libavcodec.a(snow.o): In function `encode_init':
snow.c:(.text.unlikely+0x79f): undefined reference to `h263_encode_init'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

EDIT: Got it working. The culprit was the --disable-mencoder. I removed that from the configure line and it worked like a freaking charm!

---

### Post by BwackNinja on 2010-01-12
I had the same problem, and did the first part the same, but instead of removing '--disable-mencoder' I changed:

#define CONFIG_SNOW_ENCODER 1

to

#define CONFIG_SNOW_ENCODER 0

---

### Post by mc4man on 2010-01-13
> #define CONFIG_SNOW_ENCODER 1

to

#define CONFIG_SNOW_ENCODER 0 

if anybody's looking but doesn't know where it's in config.h after you run the configure
(not the decoder define

---

### Post by andrew.46 on 2010-01-14
It has been an unusually long period of compilation breakage for the svn MPlayer, being now several days, but looks like the latest revision has MPlayer again up and running.

```
andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r30302-4.3.3 (C) 2000-2009 MPlayer Team
```

Andrew

---

### Post by mc4man on 2010-01-16
> in this particular clip I believe that ffwmv3 playback is superior to wmv9dmo
from another thread, but possibly more 'relevant' here 

I've come to think that most wmv3 decoding is better thru ff than dmo (when applicable
It seems though that mplayer tends to default to dmo for video, - is there anyway to change that other than on a per play basis with -vc ...

Side note - at least here thru yesterday, all attempts to build with a disable mencoder result in a snow error as seen in a few posts back (last good was -r 30271 or so

It's actually occurring about a 1/2 sec. before the build would normally complete

Tried on karmic, lucid, hardy, and a live cd (karmic

While changing the define as mentioned does work - it also creates new warnings during the build and doesn't seem quite right

Did you try on a ubuntu or slackware build

---

### Post by andrew.46 on 2010-01-16
Hi mc4man,

> **mc4man said:**
> I've come to think that most wmv3 decoding is better thru ff than dmo (when applicable
It seems though that mplayer tends to default to dmo for video, - is there anyway to change that other than on a per play basis with -vc ...

I guess one way is to place:

```
vfm=ffmpeg
```

in $HOME/.mplayer/config and of course the following shows the allowed entries:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vfm help[/COLOR]**
MPlayer SVN-r30337-4.3.3 (C) 2000-2009 MPlayer Team
Available (compiled-in) video codec families/drivers:
   vfm:    info:  (comment)
    null  Null video decoder (no decoding)
  ffmpeg  FFmpeg's libavcodec codec family (native codecs)
  theora  Theora/VP3 (Theora project's VP3 codec)
   dshow  DirectShow video codecs (win32 codecs)
     dmo  DMO video codecs (win32 codecs)
     vfw  Win32/VfW video codecs (win32 codecs)
   vfwex  Win32/VfWex video codecs (win32 codecs)
     lzo  LZO compressed Video (based on liblzo: http://www.oberhumer.com/opensource/lzo/)
     raw  RAW Uncompressed Video (uncompressed)
  hmblck  Hauppauge Macroblock/NV12/NV21 Decoder (uncompressed)
   xanim  XAnim codecs (binary codec plugins)
    mpng  PNG Images decoder (uses libpng, 8bpp modes not supported yet)
    ijpg  JPEG Images decoder (uses Independent JPEG Group's jpeglib)
    mtga  TGA Images decoder (only 24bpp and 32bpp RGB targa files support so far)
     sgi  SGI Image decoder ()
libmpeg2  libmpeg2 MPEG 1/2 Video decoder (native)
 mpegpes  MPEG 1/2 Video passthrough (for hw decoders)
 realvid  RealVideo decoder (binary real video codecs)
    xvid  XviD 1.0 decoder (No Comment)
   libdv  Raw DV Video Decoder (native codec)
 qtvideo  Quicktime Video decoder (win32)

```

> Side note - at least here thru yesterday, all attempts to build with a disable mencoder result in a snow error as seen in a few posts back (last good was -r 30271 or so
[...]

Did you try on a ubuntu or slackware build

Oops.... in fact my success was on Slackware where I also routinely build MEncoder. Sometimes I forget which distro I am on :(. I believe a message has arrived about this error on mplayer-users.

Andrew

---

### Post by mc4man on 2010-01-16
> I guess one way is to place:
while have to try

I was curious because for wma3 mplayer defaults to ffmpeg over dmo, while for wmv3 it is just the opposite. (am not inclined to search thru the code looking to see if this is 'predetermined' somewhere.
> 
message has arrived
will watch with some curiousity also - even when mencoder is disabled there have been 3 encoders always defined (enabled..?)
Figure there is /was a reason for that

---

### Post by andrew.46 on 2010-01-16
Hi mc4man,

> **mc4man said:**
> I was curious because for wma3 mplayer defaults to ffmpeg over dmo, while for wmv3 it is just the opposite. (am not inclined to search thru the code looking to see if this is 'predetermined' somewhere.

I guess much of this is hard-wired with the source etc/codecs.conf which the -vfm and -afm options change. I guess if you were really keen you could copy this file to $HOME/.mplayer/codecs.conf and then start working on your own settings, as you probably know details of the file are again in the source in DOCS/tech/codecs.conf.txt

All the best,

Andrew

---

### Post by mc4man on 2010-01-16
> 
Code:

vfm=ffmpeg


works just fine, dmo is now the override - thanks.

---

### Post by andrew.46 on 2010-01-22
Hi,

Those compiling against x264 might be interested to see that the MPlayer developers have raised the bar again:

```

------------------------------------------------------------------------
r30383 | cehoyos | 2010-01-21 21:37:35 +1100 (Thu, 21 Jan 2010) | 1 line

x264 version 0.83 is required.
------------------------------------------------------------------------

```

The relevant section of the configure script is:

```

echocheck "x264"
if test "$_x264" = auto ; then
  cat > $TMPC << EOF
#include <inttypes.h>
#include <x264.h>
[B][COLOR="Red"]#if X264_BUILD < 83
#error We do not support old versions of x264. Get the latest from git.[/COLOR][/B]
#endif

```

As far as I know this is the closest MPlayer / MEncoder has sailed near the bleeding edge of x264 development...

Andrew

---

### Post by Jose Catre-Vandis on 2010-01-26
Help ;)

Trying to recompile mplayer to get vdpau support.

I have nvidia 190.53 drivers installed

After an svn update, ./configure tells me that vdpau is not there

Checking for vdpau = no

Do I need to put something in the right place so it will compile with vdpau?

---

### Post by Linuxforall on 2010-01-26
> **Jose Catre-Vandis said:**
> Help ;)

Trying to recompile mplayer to get vdpau support.

I have nvidia 190.53 drivers installed

After an svn update, ./configure tells me that vdpau is not there

Checking for vdpau = no

Do I need to put something in the right place so it will compile with vdpau?

How have you installed the nvidia drivers, if via synaptic, make sure the vdpau dev files are installed as well. If you have installed via ncurses based installed from nvidia site, the vdpau dev files are already installed.

---

### Post by Jose Catre-Vandis on 2010-01-27
I used the nvidia ppa as found on the forum.

For now have worked round my main svn mplayer by installing the mplayer-vdpau from same ppa. vdpau now works, but can't say I can see any difference in smoothness of mkv 264 video? My Asus EB1012 Nvidia Ion is supposed to be capable of 1080p.

Maybe Andrew can give a run down on everything you need to enable vdpau properly, and also what parameters are needed for mkv / HD playback? ;)

---

### Post by andrew.46 on 2010-01-27
Hi Jose,

> **Jose Catre-Vandis said:**
> Maybe Andrew can give a run down on everything you need to enable vdpau properly, and also what parameters are needed for mkv / HD playback?

Unfortunately I do not have a supported card for vdpau and thus do not use it so I am of little help with such matters :(.

All the best,

Andrew

---

### Post by cor2y on 2010-01-27
To have vdpau enable at compiling time make sure you have the latest nvidia drivers or beta drivers (190.22 and above) to make this easy on yourself add the nvidia vdpau binary ppa  [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa) or you can compile it yourself ( a lot of hassle since you will have to reinstall the driver for every new kernel update that comes through)
Next you can either add that repos version of mplayer/smplayer or compile mplayer yourself and also you have to configure mplayer/smplayer to use vdpau, the easiest way is by selecting vdpau via the smplayer interface, otherwise you will have to enable vdpau support by editing the mplayer config file located in your .mplayer folder like this
```

# Write your default config options here!
vo=vdpau,xv,
ao=pulse,alsa,
vc=ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,
ac=dts,fftruehd,
autoq=100
#vf=pp=de,hqdn3d
font='Bitstream Vera Serif'
#lavdopts=threads=2
```
These settings listed are all available via smplayer preferences.

---

### Post by Linuxforall on 2010-01-28
To go the repos way just add this ppa and all is done automatically including latest driver and mplayer. [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by Jose Catre-Vandis on 2010-01-28
@ cor2y

I tried it that way and ./configure was reporting vdpau not found

@ Linuxforall

I installed the vdpau ppa mplayer and can playback with -vo vdpau but it doesn't seem to make any difference to smoothness of playback, and I cannot use any of the -vc options, no video playback.


I'll got back and start again, see if that makes any difference

---

### Post by industrai on 2010-02-05
with the default packages mplayer-nogui, i am able to play video files from within a rar archive by executing the following:

```
unrar p -inul file.rar | mplayer -
```

However, using the svn mplayer-nogui compiled with the instructions from this thread, I get errors and it won't play.

Can anyone else confirm this behavior?  Is there something missing from the package made here that is in the official mplayer-nogui package?  Is there a way to determine what was configured in that package, and possibly compare it to this package?  Error log below:

```
MPlayer SVN-r30495-4.3.4 (C) 2000-2010 MPlayer Team

Playing -.
Reading from stdin...
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
libavformat file format detected.
Cannot seek backward in linear streams!
Seek failed
[ac3 @ 0x1662910]max_analyze_duration reached
[ac3 @ 0x1662910]Estimating duration from bitrate, this may be inaccurate
[lavf] Audio stream found, -aid 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[ac3 @ 0x1663d70]frame sync error
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
    Last message repeated 3 times 0.6% 
[ac3 @ 0x1663d70]frame CRC mismatch
[ac3 @ 0x1663d70]frame sync error
    Last message repeated 1 times 0.7% 
[ac3 @ 0x1663d70]frame CRC mismatch
[ac3 @ 0x1663d70]frame sync error
[ac3 @ 0x1663d70]Additional substreams not implemented. Update your FFmpeg version to the newest one from SVN. If the problem still occurs, it means that your file has a feature which has not been implemented.If you want to help, upload a sample of this file to ftp://upload.ffmpeg.org/MPlayer/incoming/ and contact the ffmpeg-devel mailing list.
[ac3 @ 0x1663d70]unsupported frame type : skipping frame
[ac3 @ 0x1663d70]frame sync error
^C   1.1 (01.0) of 0.0 (unknown)  0.8% 

MPlayer interrupted by signal 2 in module: play_audio
A:   1.2 (01.2) of 0.0 (unknown)  0.8% 
Exiting... (Quit)
```

---

### Post by andrew.46 on 2010-02-05
Hi industrai,

> **industrai said:**
> with the default packages mplayer-nogui, i am able to play video files from within a rar archive by executing the following:

```
unrar p -inul file.rar | mplayer -
```

However, using the svn mplayer-nogui compiled with the instructions from this thread, I get errors and it won't play.

There has been a small change in MPlayer which now requires something like the following:

```

unrar p -inul file.rar | mplayer **[COLOR="Blue"]-cache 2048[/COLOR]** -

```

All the best,

Andrew

---

### Post by Bachstelze on 2010-02-05
> **Jose Catre-Vandis said:**
> @ cor2y

I tried it that way and ./configure was reporting vdpau not found


You need the 195 nvidia drivers to use VDPAU with the recent revisions of MPlayer.

---

### Post by industrai on 2010-02-05
> **andrew.46 said:**
> Hi industrai,



There has been a small change in MPlayer which now requires something like the following:

```

unrar p -inul file.rar | mplayer **[COLOR=Blue]-cache 2048[/COLOR]** -

```All the best,

Andrew

I'll give that a shot, thanks Andrew.

---

### Post by andrew.46 on 2010-02-05
Hi industrai,

> **industrai said:**
> I'll give that a shot, thanks Andrew.

I forgot to mention that this little snippet and a great deal more is actually contained in one of my most neglected guides:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

I will not reveal how much time I spent on that guide which has not been a big hit at all :(.

Andrew

---

### Post by Jose Catre-Vandis on 2010-02-06
> **Bachstelze said:**
> You need the 195 nvidia drivers to use VDPAU with the recent revisions of MPlayer.

I finally figured it out. I had a vf line in my config to deal with de-interlace-ing dvb video. I created some profiles for different file types and now vdpau works properly and handles the vc lines in mplayer.

Also found that I can't include "menu=yes" in the [default] section when trying to use vdpau.

---

### Post by industrai on 2010-02-08
> **andrew.46 said:**
> Hi industrai,



There has been a small change in MPlayer which now requires something like the following:

```

unrar p -inul file.rar | mplayer **[COLOR=Blue]-cache 2048[/COLOR]** -

```All the best,

Andrew


It works well.  Also, cache=2048 can be added to $HOME/.mplayer/config and $HOME/.mplayer/mencoder.conf so that mplayer/mencoder automatically cache the files before playback.

Thanks again for this.

---

### Post by andrew.46 on 2010-02-09
Hi industrai,

> **industrai said:**
> It works well.  Also, cache=2048 can be added to $HOME/.mplayer/config and $HOME/.mplayer/mencoder.conf so that mplayer/mencoder automatically cache the files before playback.

Thanks again for this.

No problems :). I wish I could pinpoint where and why this change came into being...

All the best,

Andrew

---

### Post by andrew.46 on 2010-02-13
64bit users in particular might be interested to see that the FFmpeg Summer of Code is, amongst other things, taking aim at Windows Media Audio Lossless:

[http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_Of_Code_2010#WMA_lossless](http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_Of_Code_2010#WMA_lossless)

If this becomes reality it will mean that wma is pretty well covered by FFmpeg and by extension MPlayer and vlc, with decoders recently in place for wmapro and wmavoice.

Andrew

---

### Post by SuperSonic4 on 2010-02-13
> **Joeb454 said:**
> Though I probably won't use it, this looks like a pretty comprehensive guide :) Thanks andrew.46

I concur.


I just wanted to add that the no-gui package is good if you want to put a different frontend on too, for example I compile mplayer without a GUI and instead compile smplayer from svn.


Furthermore, although beyond the scope of this guide, it is useful if you want to compile menconder without mplayer

---

### Post by SuperSonic4 on 2010-02-13
> **andrew.46 said:**
> 64bit users in particular might be interested to see that the FFmpeg Summer of Code is, amongst other things, taking aim at Windows Media Audio Lossless:

[http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_Of_Code_2010#WMA_lossless](http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_Of_Code_2010#WMA_lossless)

If this becomes reality it will mean that wma is pretty well covered by FFmpeg and by extension MPlayer and vlc, with decoders recently in place for wmapro and wmavoice.

Andrew

I hope so, even though I have no WMA lossless it's still gonna be useful, like the WMA voice recently implemented

---

### Post by bryce123 on 2010-02-15
Thanks for the comprehensive howto. When using the backports repos, apt-get always wants to upgrade my svn mplayer package.
Is there maybe something wrong (incomatible) with your checkinstall version parameter?

---

### Post by Linuxforall on 2010-02-15
> **bryce123 said:**
> Thanks for the comprehensive howto. When using the backports repos, apt-get always wants to upgrade my svn mplayer package.
Is there maybe something wrong (incomatible) with your checkinstall version parameter?

In synaptic lock the existing mplayer package that you installed via checkinstall and the updates wont touch that anymore.

---

### Post by mc4man on 2010-02-15
> When using the backports repos, apt-get always wants to upgrade my svn mplayer package
This guide is building mplayer-nogui and the version 3:1.0~svn-rxxxxx-1 would be/is higher than any ubuntu repo mplayer-nogui 

Are you sure you're not getting an update to 'mplayer' which in ubuntu is the old frontend package - gmplayer. (and basically worthless to have with a current svn.

Or is a ppa involved? - don't see an updated mplayer package in karmic backports anyway

---

### Post by bryce123 on 2010-02-15
ok then its not backports. i have the medibuntu repo, but this did not overwrite the mplayer-nogui package in past installations.
here is my sources.list

```
# deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
# deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
# deb http://security.ubuntu.com/ubuntu karmic-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic universe
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://download.virtualbox.org/virtualbox/debian karmic non-free

# Remastersys
deb http://www.geekconnection.org/remastersys/repository karmic/

```

---

### Post by andrew.46 on 2010-02-18
Some excellent news: mplayer now has native playback of wma speech:

```

andrew@skamandros~$ mplayer -ac help | grep wma
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]
ffwmav1     ffmpeg    untested  DivX audio v1 (FFmpeg)  [wmav1]
ffwmav2     ffmpeg    untested  DivX audio v2 (FFmpeg)  [wmav2]
ffwmapro    ffmpeg    untested  WMA Pro audio (FFmpeg)  [wmapro]
**[COLOR="Red"]ffwmavoice  ffmpeg    untested  WMA Voice audio (FFmpeg)  [wmavoice][/COLOR]**

```

Some great benefits from being close to the bleeding edge of MPlayer and FFmpeg :).

Andrew

---

### Post by Pahoo69 on 2010-02-19
Bonjour Andrews,

Thanks a lot for this very useful tuto, i make register only for thank's you, 
because my english is very poor    and i since register on french forum.
But i change my hardy for karmic and all Takes place well, only problems
with mplayer that is my favorite player. And i found your post and now all
is very good, all i try before don't work. The smlayer is stil more great than mplayer.
Thank's you         ;)

---

### Post by andrew.46 on 2010-02-19
Hi Pahoo69,

I am glad that this guide has worked for you and *extra *glad that you have made such an effort to convey your thanks :).

All the best,

Andrew

---

### Post by gillza on 2010-02-24
Andrew

Thanks again for your tutorial! I have just reinstalled ubuntu and followed your tutorial to the letter! Everything worked perfectly! Just wanted to let you know that your work is GREATLY appreciated.

Thank you very much!
Igor

---

### Post by andrew.46 on 2010-02-25
Hi Igor,

> **gillza said:**
> I have just reinstalled ubuntu and followed your tutorial to the letter! Everything worked perfectly!

Excellent news, and thank you for your kind words :).

Andrew

---

### Post by gillza on 2010-02-25
> **andrew.46 said:**
> Hi Igor,



Excellent news, and thank you for your kind words :).

Andrew

Andrew,

I think I might have jinxed it :( I have noticed that if I pause / unpause the playback of a video file twice, it will not resume playing after the second time. The picture will twitch and stop (won't resume after 3rd time, won't even twitch :)) It will only resume if I fast-forward or rewind using arrow keys.

I have compiled it following your instructions. My laptop is Fujitsu E8210 with ATI x1400 mobility radeon (ubuntu open-source driver), 2.0Ghz Core 2 duo cpu, 2gb ram. 

Any hints to what I should look at in settings maybe?

P.S. VLC does not seem to have this issue.
P.P.S. If I open the video without gui it works but sometime slows down during playback to almost freezing.  

Thank you!

---

### Post by andrew.46 on 2010-02-25
Hi gillza,

> **gillza said:**
> Any hints to what I should look at in settings maybe?

I have not personally experienced this problem but I have read that others who have encountered this have resolved the issue by altering the output driver for sound to pulse.

Andrew

---

### Post by gillza on 2010-02-26
> **andrew.46 said:**
> Hi gillza,



I have not personally experienced this problem but I have read that others who have encountered this have resolved the issue by altering the output driver for sound to pulse.

Andrew

Andrew, 

Thanks again! Changing audio output solved the problem.

Thank you.

---

### Post by daffinito on 2010-02-26
Hello,

I followed your instructions when I installed Karmic, and they worked perfectly! Thanks!

However.. I've upgraded to 10.04 now, and I wanted to recompile mplayer. I deleted my ~mplayer directory and did sudo apt-get install --reinstall on the prerequisites in your guide, but I get this error when I run make:

```
gcc-4.3 -Wmissing-prototypes -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -D__STDC_LIMIT_MACROS -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2    -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3   -I/usr/lib/live/liveMedia/include                   -I/usr/lib/live/UsageEnvironment/include                   -I/usr/lib/live/BasicUsageEnvironment/include                   -I/usr/lib/live/groupsock/include -c -o libmpdemux/demux_rtp.o libmpdemux/demux_rtp.cpp
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-std=gnu99" is valid for C/ObjC but not for C++
In file included from libmpdemux/demux_rtp.h:29,
                 from libmpdemux/demux_rtp.cpp:27:
libmpdemux/demuxer.h: In function 'demux_packet_t* new_demux_packet(int)':
libmpdemux/demuxer.h:264: error: invalid conversion from 'void*' to 'demux_packet_t*'
libmpdemux/demuxer.h:275: error: invalid conversion from 'void*' to 'unsigned char*'
libmpdemux/demuxer.h: In function 'void resize_demux_packet(demux_packet_t*, int)':
libmpdemux/demuxer.h:286: error: invalid conversion from 'void*' to 'unsigned char*'
libmpdemux/demuxer.h: In function 'demux_packet_t* clone_demux_packet(demux_packet_t*)':
libmpdemux/demuxer.h:301: error: invalid conversion from 'void*' to 'demux_packet_t*'
libmpdemux/demux_rtp.cpp: At global scope:
libmpdemux/demux_rtp.cpp:89: warning: 'typedef' was ignored in this declaration
make: *** [libmpdemux/demux_rtp.o] Error 1

```

Any idea what I've done wrong? Thank you.

---

### Post by daffinito on 2010-02-26
I was able to complete the installation by running:
```
./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-live
```

I followed the instructions on installing live555, I wonder what could be wrong?

---

### Post by andrew.46 on 2010-02-26
Hi daffinito,

I am afraid that I have not really looked at Lucid yet and I suspect that I will wait for the release version which historically will be delayed as was the previous LTS. However I note that Lucid is using gcc 4.4.2 which the MPlayer developers have declared safe for MPlayer compilation so I would definitely omit:

```
--cc=gcc-4.3
```

and allow the *default* compiler to do the work. Perhaps try this first and see if the problem disappears otherwise I believe mc4man has been building MPlayer on Lucid with no problems and may have some input.

**Edit:** And I am experiencing the same error so I suspect compilation is temporarily broken, I note that mplayer-users has a report of the same. Just a matter of either patching the problem or waiting...

All the best,

Andrew

---

### Post by mc4man on 2010-02-27
Haven't built mplayer in a bit, but a temporary fallback for live55 could be to just use the new lucid source. (though mplayer is pretty quick to fix things.

(Something similar came up this fall with live555 and vlc, it took several weeks to resolve. Since then I've gotten in the habit of saving some sources till I know the newer versions are good (compressed.

Anyway lucid updated it's live555 to 02/10 (mainly for vlc 1.0.5

So I guess one could use the lucid package - liblivemedia-dev, though if needed I'd just grab the source ( IIRC vlc won't find the package if installed for building - ironic...

```
wget http://archive.ubuntu.com/ubuntu/pool/universe/libl/liblivemedia/liblivemedia_2010.02.10.orig.tar.gz
```

---

### Post by andrew.46 on 2010-02-27
Certainly for Karmic the compilation issue has been resolved in the latest svn....

Andrew

---

### Post by dot2kode on 2010-03-06
Excellent guide man...Worked perfectly! Thanks for putting this together! =D>

---

### Post by andrew.46 on 2010-03-06
Hi dot2code,

> **dot2kode said:**
> Excellent guide man...Worked perfectly! Thanks for putting this together! =D>

Excellent news, I hope you enjoy using the very latest MPlayer :).

Andrew

---

### Post by rifter on 2010-03-08
Thanks a lot for your informative howto.
I had been having really bad audio sync problems with hd videos in mplayer (the same video was fine in totem or vlc) and for unrelated reasons I was trying to see if I could use mplayer instead of those other player.  Autosync gave me no joy.

After following your directions I now have smplayer working and the videos sync perfectly.  There are a few things I did differently:

I installed FFmpeg and x264 first using [thread=786095]these directions[/thread].

I didn't get why you were disabling mencoder and x264 in your configure arguments except that maybe in the case of the latter you didn't include installing it.  I did

./configure --cc=gcc-4.3 --confdir=/etc/mplayer

instead.

I also ran into some trouble with checkinstall that I am sure was my fault.  What was happening was that I would run the command and it would just hang, with no instance of checkinstall showing up in ps.  Very odd.  I had used a different path to the mplayer sources and package than your instructions advise and that may have been the source of my troubles.  In any event I rebooted and then tried a path that did not have the hyphens my original path had, so it was more like:

checkinstall -D --install=yes --fstrans=no --pakdir "/home/myusername/Downloads/mplayernew/mplayer/package" --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default --pkgversion "3:1.0~svn-r30861"

where myusername was of course my user name and r30861 was the output of 

grep "#define VERSION" version.h | cut -d"-" -f2

I am sure the command works fine the way you had it, with the paths you recommend, and that something weird was happening with my system, but I am including this in case someone else runs into the same problem I did.

Anyway I like the smplayer gui better than gmplayer, and all the problems I had with my videos are gone now thanks to your help.

EDIT:

A couple of other things ...

I didn't find the config file in the place you specified but when mplayer installed I got 

/etc/mplayer/mplayer.conf

which is the system-wide conf file and copied it into

~/.mplayer/config

like you said, editing that version as opposed to the system-wide one.

Here are some interesting things from my config file:

```

#use this if you have a widescreen monitor
monitoraspect=16:9

#video out setting
vo=x11
framedrop = yes
# cache settings
#
# Use 8MB input cache by default.
cache = 8192
#
# Prefill 20% of the cache before starting playback.
cache-min = 20.0
#
# Prefill 50% of the cache before restarting playback after the cache emptied.
cache-seek-min = 50

#fix sync issues
autosync=30
mc=2.0


# Use pulse, then alsa, then SDL video with the aalib subdriver by default.
ao=pulse,alsa,sdl:aalib


```

The audio setting was already there .. I actually wanted to play with alsa as the output because it was not working with the stock mplayer and was given as as a solution for sync issues.  I haven't been having them now so I haven't tried alsa yet as a setting.

Update:

As it turns out, I did get some sync issues later on with some files.  Switching the output to alsa fixed that and I did not get the pcm errors I had previously received trying to use alsa output with the stock mplayer.

---

### Post by andrew.46 on 2010-03-08
Hi rifter,

> **rifter said:**
> Thanks a lot for your informative howto.

It is my pleasure :).

> I didn't get why you were disabling mencoder and x264 in your configure arguments except that maybe in the case of the latter you didn't include installing it.  I did

./configure --cc=gcc-4.3 --confdir=/etc/mplayer

instead.

This guide was only ever intended to provide a *starting* point and I have always hoped that users of the guide would make their own additions and changes. x264 an MEncoder were disabled in part because they are not part of the Ubuntu package mplayer-nogui but mainly because:

[LIST=1]
[*]I really did not want to enter the world of x264 compilation in Ubuntu where a tangled mess of dependencies exist.
[*]h264 playback, which is what most people are after, does not depend on x264.
[*]MEncoder is not heavily developed any more and I believe that FFmpeg is a much better choice.
[/LIST]

If you have built MEncoder as well you might be best to add in the dependencies for faac and lame when you recompile so aac and mp3 encoding are available to you.

> I didn't find the config file in the place you specified

Have a look in the svn MPlayer source, in the *etc* directory and you will see it there along with a set of other interesting configuration files :).

All the best,

Andrew

---

### Post by Aerospaztic on 2010-03-08
I'm a real noob, so I don't know if this helps:

For this section:

$ mv -v $HOME/.mplayer/config $HOME/.mplayer/config_bak
$ cp -v $HOME/mplayer/etc/example.conf $HOME/.mplayer/config

I simply used /mplayer in place of the /.mplayer

It was the only way it worked for me.  Not sure if this is right.

---

### Post by andrew.46 on 2010-03-09
Hi Aerospaztic,

> **Aerospaztic said:**
> It was the only way it worked for me.  Not sure if this is right.

Whatever has worked for you :). MPlayer works perfectly well *without* this file anyway. If you decide to have one it the default name is $HOME/.mplayer/config which is what MPlayer looks for on startup. Believe it or not the file can also have many other names and if you are interested the MPlayer man pages goes into great details under 'CONFIGURATION FILES'...

All the best,

Andrew

---

### Post by cchhrriiss121212 on 2010-03-10
This was a very nice guide, but Mplayer gives me this error via smplayer:

 p, li { white-space: pre-wrap; }  Warning unknown option stop-xscreensaver at line 87
 Unknown option on the command line: -nostop-xscreensaver
 Error parsing option on the command line: -nostop-xscreensaver
 MPlayer SVN-r30881-4.3.3 (C) 2000-2010 MPlayer Team
 ID_EXIT=NONE

---

### Post by andrew.46 on 2010-03-10
Hi cchhrriiss,

> **cchhrriiss121212 said:**
> 
```
 Unknown option on the command line: -nostop-xscreensaver
```


This one has come up before and is a bit of a puzzle, I suspect that something is missing in your MPlayer installation as this is a legitimate MPlayer option. The bandaid solution is to alter the option in SMPlayer and this can be found at Options --> General --> Video --> Disable Screensaver, but at some stage I would definitely attempt a reinstall of the dependencies, svn up and recompile.

All the best,

Andrew

---

### Post by yorgmeister on 2010-03-13
My mplayer was working I had already updated it to the svn version, but I was having sound issues on my hdmi connection so I went through the how-to on upgrading alsa ([[SOLVED] (all varients) fixing scratching/poping noise on ubuntu 9.10 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=8789064#post8789064"))
Now all I get from Mplayer is : "Mplayer has finished expectantly. exit code 1"

I 'apt-get purge'ed Mplayer   and followed you how-to again to no avail.

LOG:
 p, li { white-space: pre-wrap; }  mplayer -noquiet -nofs -nomouseinput -afm hwac3 -lavdopts skiploopfilter=all -sub-fuzziness 1 -identify -slave -vo xv -ao alsa:device=hw=0.1 -nokeepaspect -framedrop -autosync 100 -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 62914575 -monitorpixelaspect 1 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 50 -nocache -ss 6417 -osdlevel 0 -vf-add screenshot -slices -channels 2 -softvol -softvol-max 120 /home/yorgie/Downloads/Movies/The.Hangover.2009.UNRATED.BluRay.1080p.DTS.x264-CHD/The.Hangover.2009.UNRATED.BluRay.1080p.DTS.x264-CHD.mkv
 
 MPlayer SVN-r30886-4.3.4 (C) 2000-2010 MPlayer Team
 Terminal type `unknown' is not defined.
 
 Playing /home/yorgie/Downloads/Movies/The.Hangover.2009.UNRATED.BluRay.1080p.DTS.x264-CHD/The.Hangover.2009.UNRATED.BluRay.1080p.DTS.x264-CHD.mkv.
 ID_VIDEO_ID=0
 ID_VID_0_NAME=The.Hangover.2009.Extended.Cut
 [mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "The.Hangover.2009.Extended.Cut", -vid 0
 ID_AUDIO_ID=0
 ID_AID_0_NAME=DTS-5.1CH 1536K
 ID_AID_0_LANG=eng
 [mkv] Track ID 2: audio (A_DTS) "DTS-5.1CH 1536K", -aid 0, -alang eng
 [mkv] Will play video track 1.
 Matroska file format detected.
 VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
 ID_FILENAME=/home/yorgie/Downloads/Movies/The.Hangover.2009.UNRATED.BluRay.1080p.DTS.x264-CHD/The.Hangover.2009.UNRATED.BluRay.1080p.DTS.x264-CHD.mkv
 ID_DEMUXER=mkv
 ID_VIDEO_FORMAT=avc1
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=1920
 ID_VIDEO_HEIGHT=800
 ID_VIDEO_FPS=23.976
 ID_VIDEO_ASPECT=2.4000
 ID_AUDIO_FORMAT=8193
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=6
 ID_LENGTH=6473.49
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 Opening video filter: [screenshot]
 ==========================================================================
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
 ==========================================================================
 ID_VIDEO_CODEC=ffh264
 ==========================================================================
 Trying to force audio codec driver family hwac3...
 Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
 hwac3: switched to DTS, 1536000 bps, 48000 Hz
 AUDIO: 48000 Hz, 2 ch, ac3le, 1536.0 kbit/100.00% (ratio: 192000->192000)
 ID_AUDIO_BITRATE=1536000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [hwdts] afm: hwac3 (DTS through S/PDIF)
 ==========================================================================
 [AO_ALSA] alsa-lib: conf.c:3843:(parse_args) Unknown parameter AES0
 [AO_ALSA] alsa-lib: conf.c:3969:(snd_config_expand) Parse arguments error: No such file or directory
 [AO_ALSA] alsa-lib: pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AES0=6
 AO: [alsa] 48000Hz 2ch ac3le (2 bytes per sample)
 ID_AUDIO_CODEC=hwdts
 [Mixer] No hardware mixing, inserting volume filter.
 [format] Sample format little-endian AC3 not yet supported 
 Starting playback...
 
 
 MPlayer interrupted by signal 11 in module: decode_audio
 ID_SIGNAL=11
 - MPlayer crashed by bad usage of CPU/FPU/RAM.
   Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
   disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
 - MPlayer crashed. This shouldn't happen.
   It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
   gcc version. If you think it's MPlayer's fault, please read
   DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
   won't help unless you provide this information when reporting a possible bug.

---

### Post by andrew.46 on 2010-03-13
Hi yorgmeister,

Certainly there are some audio errors there. Have a look at:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -ao help[/COLOR]**
MPlayer SVN-r30886-4.3.3 (C) 2000-2010 MPlayer Team
Available audio output drivers:
	oss	OSS/ioctl audio output
	alsa	ALSA-0.9.x-1.x audio output
	esd	EsounD audio output
	sdl	SDLlib audio output
	mpegpes	DVB audio output
	v4l2	V4L2 MPEG Audio Decoder output
	null	Null audio output
	pcm	RAW PCM/WAVE file writer audio output

```

and see if you have some alternatives to experiment with. If so you can launch your file from the commandline in the following fashion:

```

mplayer -ao oss **[COLOR="Red"]<my_file>[/COLOR]**

```

where of course *my_file* is the real name and path to your own file.

Andrew

---

### Post by margemoosh on 2010-03-19
I use Gnome mplayer but it freeze random when playing video or audio files and just show a black screen without sound and if i simply press backward or forward button to send it 10 sec forward or backward it will continue to play video until it freeze again.(in audio files i should kill gnome-mplayer process)
sometimes it takes seconds to freeze and sometimes half an hour or more.

---

### Post by andrew.46 on 2010-03-19
Hi margemoosh,

Can I ask which version of MPlayer you are using? This can be seen in the following fashion:
```

andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r30931-4.3.3 (C) 2000-2010 MPlayer Team
```

Some confusion sometimes exists between the Totem Movie Player, which is the default player for GNOME, and MPlayer which is a 3rd party offering. Could you have a look at the results of Help --> About for the player that is giving you trouble and confirm which version and which player?

All the best,

Andrew

---

### Post by margemoosh on 2010-03-20
> **andrew.46 said:**
> Hi margemoosh,

Can I ask which version of MPlayer you are using? This can be seen in the following fashion:
```

andrew@skamandros~$ **[COLOR=Red]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r30931-4.3.3 (C) 2000-2010 MPlayer Team
```Some confusion sometimes exists between the Totem Movie Player, which is the default player for GNOME, and MPlayer which is a 3rd party offering. Could you have a look at the results of Help --> About for the player that is giving you trouble and confirm which version and which player?

All the best,

Andrew

```
margemoosh@Sisto:~$ mplayer | head -n 1
MPlayer SVN-r30858-4.3.4 (C) 2000-2010 MPlayer Team

```and in help-> about: gnome-mplayer 0.9.9

i think problem is audio because when audio playing and mplayer freeze you sholud quit it and reopen it but in video you should just press backward button to send it a few seconds back or forward and it will continue playing!

---

### Post by andrew.46 on 2010-03-21
Hi margemoosh,

> **margemoosh said:**
> i think problem is audio because when audio playing and mplayer freeze you sholud quit it and reopen it but in video you should just press backward button to send it a few seconds back or forward and it will continue playing!

You could possibly be having a problem with either video or audio out devices and if you are keen I would suggest a little experimentation with both. Perhaps to start with run all of your audio as *-ao pulse* and this perhaps might be enough, if not try something like *-vo gl* to test video output problems. A bit of trial and error?

Andrew

---

### Post by margemoosh on 2010-03-22
> **andrew.46 said:**
> Hi margemoosh,



You could possibly be having a problem with either video or audio out devices and if you are keen I would suggest a little experimentation with both. Perhaps to start with run all of your audio as *-ao pulse* and this perhaps might be enough, if not try something like *-vo gl* to test video output problems. A bit of trial and error?

Andrew

how i can do this?
in gnome-mplayer in terminal i dont see any -ao option.

---

### Post by andrew.46 on 2010-03-22
Hi margemoosh,

> **margemoosh said:**
> how i can do this?
in gnome-mplayer in terminal i dont see any -ao option.

I was referring to MPlayer, sorry I was less than clear :).

Andrew

---

### Post by yorgmeister on 2010-03-26
Thanks andrew

I tried your suggestion 'mplayer -ao oss' and mplayer works great from the command line, so my problem must be with smplayer, as it still outputs the same 'exit code 1' error. I tried mplayer with several different sound options, they all worked, but I am still left with my original problem of the sound cutting in and out on my hdmi output to my tv. sound works great on my computer speakers. any ideas?

george

---

### Post by andrew.46 on 2010-03-26
Hi George,

> **yorgmeister said:**
> I tried your suggestion 'mplayer -ao oss' and mplayer works great from the command line, so my problem must be with smplayer, as it still outputs the same 'exit code 1' error. 

And of course SMPlayer has very easily configurable audio out options seen from Options --> Preferences --> General --> Audio --> Output Driver.

> I tried mplayer with several different sound options, they all worked, but I am still left with my original problem of the sound cutting in and out on my hdmi output to my tv. sound works great on my computer speakers. any ideas?

I am afraid that my experience with sound output from MPlayer is my computer speakers and headphones when I feel like getting a little fancy :). Hopefully somebody with some experience in this area can help out on this thread...

All the best,

Andrew

---

### Post by andrew.46 on 2010-04-05
A brief note just before Lucid Lynx rolls out, perhaps some would be interested in trying the following:

How To Build Uoti's git MPlayer Branch on Linux
[http://www.linuxtech.net/tips+tricks/How_To_Build_Uotis_git_MPlayer_Branch.html](http://www.linuxtech.net/tips+tricks/How_To_Build_Uotis_git_MPlayer_Branch.html)

I would personally not use:

```
sudo apt-get build-dep mplayer-nogui
```

as it gets all rather messy doing this but it is not my guide after all :).

Andrew

---

### Post by tux99 on 2010-04-05
> **andrew.46 said:**
> A brief note just before Lucid Lynx rolls out, perhaps some would be interested in trying the following:

How To Build Uoti's git MPlayer Branch on Linux
[http://www.linuxtech.net/tips+tricks/How_To_Build_Uotis_git_MPlayer_Branch.html](http://www.linuxtech.net/tips+tricks/How_To_Build_Uotis_git_MPlayer_Branch.html)

I would personally not use:

```
sudo apt-get build-dep mplayer-nogui
```as it gets all rather messy doing this but it is not my guide after all :).

Andrew

Huh? :confused: What do you mean by it gets rather messy?

All that command does is it installs all the required dev packages, necessary to build mplayer from source, if you don't run it you won't be able to build mplayer-git.

How else would you do it?

Edit: Oh I just saw the initial post of this thread, TBH the way you suggest (to manually type out and install each single package required) looks much less elegant (and prone to errors) to me and it won't necessarily work for every distro release when package names might change.

'sudo apt-get build-dep' is a very useful and clever command, why not make use of it? :)

---

### Post by Bachstelze on 2010-04-05
> **tux99 said:**
> 
All that command does is it installs all the required dev packages, necessary to build mplayer from source, if you don't run it you won't be able to build mplayer-git.

Not true. It installs all the -dev packages required to build MPlayer *with the same features as the Ubuntu package*, which is far more than any given person would need. It makes perfect sense to not install a -dev package if you don't need the feature it provides.

---

### Post by tux99 on 2010-04-05
> **Bachstelze said:**
> Not true. It installs all the -dev packages required to build MPlayer ***with the same features as the Ubuntu package*, which is far more than any given person would need.** It makes perfect sense to not install a -dev package if you don't need the feature it provides.


Which features would that be that we don't need? The GUI maybe?
The few extra dev packages installed that might not be needed do no harm to anyone, other than taking up a little disk space (hardly a problem with today's Giga/Terabyte hard disks). The advantage is that this command works  regardless of the specific distro version used, even if dev package names have changed (which happens occasionally between distro releases).

---

### Post by mc4man on 2010-04-05
> The few extra dev packages installed that might not be needed do no harm to anyone

In karmic and lucid the repo mplayer has build depends on the shared ffmpeg libs, so build deps will install those and probably the repo libx264-dev, and possibly nvidia-185-libvdpau-dev (karmic), maybe a few others.

Many that build mplayer also build ffmpeg, x264 and possibly some sources of of them. In those cases you don't want these installed with the exception of an applicable libvdpau-dev which can be added when desired,

The provided deps work quite well for most, and with a name change or 2 should be good for lucid. (and possibly 1 or 2 removed

---

### Post by tux99 on 2010-04-05
> **mc4man said:**
> 
Many that build mplayer also build ffmpeg, x264 and possibly some sources of of them. In those cases you don't want these installed with the exception of an applicable libvdpau-dev which can be added when desired

Fair point, but I guess that those people who have already built their own ffmpeg and x264 libs from source don't really need the instructions mentioned above on how to build mplayer-git (or rather they are experienced enough to modify them to their own needs).

Also building their own libs without packaging them up (and following distro standard packaging naming and versioning convention) is very bad practice too and will break lots of dependencies.
On the other hand if their are packaged up correctly then 'sudo apt-get build-dep' won't do any harm as it will just skip all those dev packages that are installed already.

The mplayer-git build how-to on linuxtech.net is targeted mainly at people who don't have much experience at building their own binaries (but are interested in it), so it's kept as simple as possible.

---

### Post by Bachstelze on 2010-04-05
> **tux99 said:**
> 
Also building their own libs without packaging them up (and following distro standard packaging naming and versioning convention) is very bad practice too and will break lots of dependencies.
On the other hand if their are packaged up correctly then 'sudo apt-get build-dep' won't do any harm as it will just skip all those dev packages that are installed already.

Creating valid packages is a bit more work, though. Not really worth it for something as simple as MPlayer.

---

### Post by tux99 on 2010-04-05
> **Bachstelze said:**
> Creating valid packages is a bit more work, though. Not really worth it for something as simple as MPlayer.


Agreed, it's not worth it for mplayer, but for libraries with a lot of dependencies like ffmpeg and x264 it's certainly worth it, to avoid messing up dependencies and distro package updates.

---

### Post by andrew.46 on 2010-04-05
Hi tux99,

I almost regret making a small aside concerning *apt-get build-dep* :). This command does have a specialised use which is to rebuild an existing ubuntu package and for this purpose it is *very* useful. Have a look at [this example]("http://ubuntuforums.org/showpost.php?p=8320034&postcount=16") where I rebuild the Ubuntu gFtp package with an additional option, the build-dep process is integral to such a rebuild. 

All the best,

Andrew

---

### Post by tux99 on 2010-04-05
> **andrew.46 said:**
> 
I almost regret making a small aside concerning *apt-get build-dep* :).

No problem, a good debate like this one helps less experienced users who read this, learn about something they might not have known about.

> **andrew.46 said:**
> 
This command does have a specialised use which is to rebuild an existing ubuntu package and for this purpose it is *very* useful. 

True that's it's main purpose, but it can be handy in other situations too.

---

### Post by mc4man on 2010-04-05
> I almost regret making a small aside concerning apt-get build-dep...
You never know where such things lead, though info is generally a useful thing.

Anyway built mplayer on lucid for a 'for real' install (p4, no vdpau), used this for build-deps (very similar to p.1, the blue are name changes, the red I used but I don't think is needed (or is it?
```
sudo apt-get install ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev \
libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev \
libcaca-dev libcairo2-dev libcdparanoia-dev libdbus-1-dev libdc1394-22 \
libdca-dev libdirectfb-dev libdirectfb-extra libdts-dev libesd0-dev \
libexpat1-dev libfontconfig1-dev libfreebob0 libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev \
libgsm1 libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev liblzo2-2 \
liblzo2-dev libmail-sendmail-perl libncurses5-dev libogg-dev liboil0.3-dev \
libopencore-amrwb-dev libopencore-amrnb-dev libopenjpeg-dev libopenal-dev \
libpango1.0-dev libpixman-1-dev libpng12-dev libpthread-stubs0-dev libpulse-dev libruby1.8 \
libschroedinger-dev libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libvorbis-dev libvorbisidec-dev libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev \
libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev \
libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev \
libxv-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev vstream-client-dev x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev \
yasm zlib1g-dev [COLOR="Blue"]libxvidcore-dev libffado-dev libcelt-dev[/COLOR] [COLOR="Red"]liba52-0.7.4-dev [/COLOR]
```

---

### Post by yorgmeister on 2010-04-08
Thanks for all your help Andrew, you have been a big help.

George

---

### Post by andrew.46 on 2010-04-08
Hi George,

> **yorgmeister said:**
> Thanks for all your help Andrew, you have been a big help.

It is my pleasure :). I am taking a break from Ubuntu for a while and I will miss much of the interaction on the Forums :(. 

All the best,

Andrew

---

### Post by piousp on 2010-04-10
Andrew,
thanks for everything!

---

### Post by macey on 2010-04-12
> **mc4man said:**
> You never know where such things lead, though info is generally a useful thing.

Anyway built mplayer on lucid for a 'for real' install (p4, no vdpau), used this for build-deps (very similar to p.1, the blue are name changes, the red I used but I don't think is needed (or is it?
```
sudo apt-get install ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev \
libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev \
libcaca-dev libcairo2-dev libcdparanoia-dev libdbus-1-dev libdc1394-22 \
libdca-dev libdirectfb-dev libdirectfb-extra libdts-dev libesd0-dev \
libexpat1-dev libfontconfig1-dev libfreebob0 libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev \
libgsm1 libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev liblzo2-2 \
liblzo2-dev libmail-sendmail-perl libncurses5-dev libogg-dev liboil0.3-dev \
libopencore-amrwb-dev libopencore-amrnb-dev libopenjpeg-dev libopenal-dev \
libpango1.0-dev libpixman-1-dev libpng12-dev libpthread-stubs0-dev libpulse-dev libruby1.8 \
libschroedinger-dev libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libvorbis-dev libvorbisidec-dev libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev \
libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev \
libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev \
libxv-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev vstream-client-dev x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev \
zlib1g-dev libopencore-amrwb-dev libopencore-amrnb-dev libopenjpeg-dev \
[COLOR="Blue"]libxvidcore-dev libffado-dev libcelt-dev[/COLOR] [COLOR="Red"]liba52-0.7.4-dev [/COLOR]
```


Hi, do you fancy knocking up a quick guide on this? I'm not sure whether
need all other sections of page one as well as these 'Development files'

Thanks.

---

### Post by mc4man on 2010-04-12
> do you fancy knocking up ...

No need, basically just follow the guide for karmic. (for a build as described - no mencoder

The build dep's I posted are the same with some needed name changes and possibly one or 2 additions. (just edited out some inadvertent  dupes.
Otherwise just use the guide with the other exceptions that you can use the default gcc in lucid so the posted ./configure can be changed to 

./configure --confdir=/etc/mplayer --disable-mencoder --disable-x264

and the initial apt-get you could remove the gcc packages

sudo apt-get install build-essential  subversion checkinstall

Edit:
just noticed that lucid is no longer building a gui version so "mplayer-nogui" has become a transistional package - mplayer is again mplayer.
While it won't particularly matter with the 3:, it may make more sense in the checkinstall command to change to 

 --pkgname mplayer


An alternate build method/source is mentioned in post #231

---

### Post by macey on 2010-04-16
> **mc4man said:**
> No need, basically just follow the guide for karmic. (for a build as described............


Done, worked a treat, thanks.

---

### Post by elmad on 2010-04-22
I used your guide for Lucid Lynx. After install, with SMplayer i have an  error: 

 Warning unknown option stop-xscreensaver at line 87
 Unknown option on the command line: -stop-xscreensaver
 Error parsing option on the command line: -stop-xscreensaver
 MPlayer SVN-r31057-4.4.3 (C) 2000-2010 MPlayer Team
 ID_EXIT=NONE
 

If I uncheck option in Options --> General --> Video --> Disable Screensaver , I have another error:
 

 Warning unknown option  stop-xscreensaver at line 87
  Unknown option on the command line: -nostop-xscreensaver
 Error parsing option on the  command line: -nostop-xscreensaver
 MPlayer SVN-r31057-4.4.3 (C)  2000-2010 MPlayer Team
 ID_EXIT=NONE


:lolflag: 
What can I do?


EDIT: ok, my problem. Now works with apt-get list from mc4man.

Thank u

---

### Post by Linuxforall on 2010-05-01
I installed it today with the minor tweaks from mac4man, used inbuilt gcc on Lucid, works brilliantly, running with nvidia driver installed via the run file, vdpau works fine.

---

### Post by TheAlien on 2010-05-08
Hi, andrew.

Can we use the gcc for Lucid to compile? Or should we still use version 4.3?

---

### Post by Bachstelze on 2010-05-08
> **TheAlien said:**
> Hi, andrew.

Can we use the gcc for Lucid to compile? Or should we still use version 4.3?

gcc from Lucid is fine.

---

### Post by cor2y on 2010-05-08
Should i be worried about this error?
```


bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r31142-4.4.3 (C) 2000-2010 MPlayer Team

```
"ao=pulse,alsa," in the config file

---

### Post by TheAlien on 2010-05-09
Medibuntu has mplayer-gui for Lucid. How does that one compare to the one we can compile in this thread?

Does the Win32 DLL codecs work on Lucid 64 bit?

[http://packages.medibuntu.org/lucid/mplayer-gui.html](http://packages.medibuntu.org/lucid/mplayer-gui.html)

[COLOR=Red]Edit:[/COLOR] It seems to miss AMR.

---

### Post by Linuxforall on 2010-05-10
> **TheAlien said:**
> Medibuntu has mplayer-gui for Lucid. How does that one compare to the one we can compile in this thread?

Does the Win32 DLL codecs work on Lucid 64 bit?

[http://packages.medibuntu.org/lucid/mplayer-gui.html](http://packages.medibuntu.org/lucid/mplayer-gui.html)

[COLOR=Red]Edit:[/COLOR] It seems to miss AMR.

The one you will compile and subsequently update is far newer and cutting edge than the one in Lucid.

---

### Post by andrew.46 on 2010-05-12
Hi,

I feel a little bad that I have lessened my work substantially with MPlayer + Ubuntu of late but that is the way it goes I guess, there is only so much time available.... But I do miss the fun of building MPlayer under Ubuntu....

Anyway a quick note for the keen, there will be a new mp3 decoder arriving soon which some might be interested in trialing. There is some discussion here:

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2010-May/064447.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2010-May/064447.html)

and a patch on the second post which applies cleanly on the current svn. I have not tested on Karmic/Lucid but I would imagine the required dev file here is *libmpg123-dev*, I note karmic has a slightly older version. This certainly works nicely on my system compiled against mpg123 1.2.1:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -ac help | grep mpg123[/COLOR]**

mpg123      mpg123    working   MPEG 1.0/2.0/2.5 layers I, II, III

```
```

andrew@skamandros~/Desktop$**[COLOR="Red"] mplayer -ac mpg123 test.mp3 [/COLOR]**
MPlayer SVN-r31168-4.3.3 (C) 2000-2010 MPlayer Team

Playing test.mp3.
Audio only file format detected.
==========================================================================
Forced audio codec: mpg123
Opening audio decoder: [mpg123] MPEG 1.0/2.0/2.5 layers I, II, III
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mpg123] afm: mpg123 (MPEG 1.0/2.0/2.5 layers I, II, III)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:1310.1 (21:50.0) of 1310.0 (21:50.0)  0.8% 

Exiting... (End of file)

```

It is certainly the most complete patch that I have ever seen offered to mplayer-dev-eng :). Hopefully it will be committed soon and perhaps mp3lib will be gone as well.

All the best,

Andrew

---

### Post by andrew.46 on 2010-05-13
And in a final note I encourage everybody to try the new 'matrixview' :).

Andrew

---

### Post by mocha on 2010-05-14
For Lucid, your dependencies list has a few errors, these are the correct package names.

libcelt0-0
libffado2
libxvidcore-dev

---

### Post by m45t3r on 2010-05-16
> **andrew.46 said:**
> A brief note just before Lucid Lynx rolls out, perhaps some would be interested in trying the following:

How To Build Uoti's git MPlayer Branch on Linux
[http://www.linuxtech.net/tips+tricks/How_To_Build_Uotis_git_MPlayer_Branch.html](http://www.linuxtech.net/tips+tricks/How_To_Build_Uotis_git_MPlayer_Branch.html)

I would personally not use:

```
sudo apt-get build-dep mplayer-nogui
```as it gets all rather messy doing this but it is not my guide after all :).

Andrew
Thanks.

I used these instructions to compile a MPlayer on Lucid Lynx with the latest libass and Matroska's ordered chapters support (not much useful for normal people, but for everyone who likes to watch animes like me it's essential) and now my MPlayer rocks:guitar:.
[B]
I strongly recommend who needs decent SubStation Alpha/Advance SubStation alpha subtitles support on Linux to compile MPlayer from this git.[/B]

One note: I had to use build-dep because I wanted NVIDIA's VDPAU support. But of course, you can just install libvdpau-dev:P.

---

### Post by NTHQ on 2010-05-24
This may be a nooby mistake on my part but after compiling, I don't have a ./mplayer directory...
Is it crucial?

---

### Post by andrew.46 on 2010-05-24
Hi NTHQ,

> **NTHQ said:**
> This may be a nooby mistake on my part but after compiling, I don't have a ./mplayer directory...
Is it crucial?

It is not crucial and you can run MPlayer quite happily without it :). Bear in mind if you create it the file is actually ~/.mplayer

Andrew

---

### Post by Lockheed on 2010-05-28
I used to use smplayer compiled according to your instructions from another HOWTO of yours (great work, btw) but after upgrading from 9.04 to 10.04 picture became transparent and invisible, so I went ahead and tried following this one. However, right at the beginning, I am getting this error:

```
~/live$ make
cd liveMedia ; make
make[1]: Entering directory `/home/juha/live/liveMedia'
ar cr libliveMedia.a  \
		Media.o MediaSource.o FramedSource.o FramedFileSource.o FramedFilter.o ByteStreamFileSource.o ByteStreamMultiFileSource.o BasicUDPSource.o DeviceSource.o AudioInputDevice.o WAVAudioFileSource.o MPEG1or2Demux.o MPEG1or2DemuxedElementaryStream.o MPEGVideoStreamFramer.o MPEG1or2VideoStreamFramer.o MPEG1or2VideoStreamDiscreteFramer.o MPEG4VideoStreamFramer.o MPEG4VideoStreamDiscreteFramer.o H264VideoStreamFramer.o MPEGVideoStreamParser.o MPEG1or2AudioStreamFramer.o MPEG1or2AudioRTPSource.o MPEG4LATMAudioRTPSource.o MPEG4ESVideoRTPSource.o MPEG4GenericRTPSource.o MP3FileSource.o MP3HTTPSource.o MP3Transcoder.o MP3ADU.o MP3ADUdescriptor.o MP3ADUinterleaving.o MP3ADUTranscoder.o MP3StreamState.o MP3Internals.o MP3InternalsHuffman.o MP3InternalsHuffmanTable.o MP3ADURTPSource.o MPEG1or2VideoRTPSource.o MPEG2TransportStreamMultiplexor.o MPEG2TransportStreamFromPESSource.o MPEG2TransportStreamFromESSource.o MPEG2TransportStreamFramer.o ADTSAudioFileSource.o H263plusVideoRTPSource.o H263plusVideoStreamFramer.o H263plusVideoStreamParser.o AC3AudioStreamFramer.o AC3AudioRTPSource.o DVVideoStreamFramer.o DVVideoRTPSource.o JPEGVideoSource.o AMRAudioSource.o AMRAudioFileSource.o InputFile.o MediaSink.o FileSink.o BasicUDPSink.o AMRAudioFileSink.o H264VideoFileSink.o HTTPSink.o MPEG1or2AudioRTPSink.o MP3ADURTPSink.o MPEG1or2VideoRTPSink.o MPEG1or2VideoHTTPSink.o MPEG4LATMAudioRTPSink.o MPEG4GenericRTPSink.o MPEG4ESVideoRTPSink.o H263plusVideoRTPSink.o H264VideoRTPSink.o DVVideoRTPSink.o AC3AudioRTPSink.o GSMAudioRTPSink.o JPEGVideoRTPSink.o SimpleRTPSink.o AMRAudioRTPSink.o OutputFile.o uLawAudioFilter.o RTPSource.o MultiFramedRTPSource.o SimpleRTPSource.o H261VideoRTPSource.o H264VideoRTPSource.o QCELPAudioRTPSource.o AMRAudioRTPSource.o JPEGVideoRTPSource.o RTPSink.o MultiFramedRTPSink.o AudioRTPSink.o VideoRTPSink.o RTPInterface.o RTCP.o rtcp_from_spec.o RTSPServer.o RTSPOverHTTPServer.o RTSPClient.o RTSPCommon.o SIPClient.o MediaSession.o ServerMediaSession.o PassiveServerMediaSubsession.o OnDemandServerMediaSubsession.o FileServerMediaSubsession.o MPEG4VideoFileServerMediaSubsession.o H263plusVideoFileServerMediaSubsession.o WAVAudioFileServerMediaSubsession.o AMRAudioFileServerMediaSubsession.o MP3AudioFileServerMediaSubsession.o MPEG1or2VideoFileServerMediaSubsession.o MPEG1or2FileServerDemux.o MPEG1or2DemuxedServerMediaSubsession.o MPEG2TransportFileServerMediaSubsession.o ADTSAudioFileServerMediaSubsession.o DVVideoFileServerMediaSubsession.o QuickTimeFileSink.o QuickTimeGenericRTPSource.o AVIFileSink.o MPEG2IndexFromTransportStream.o MPEG2TransportStreamIndexFile.o MPEG2TransportStreamTrickModeFilter.o DarwinInjector.o BitVector.o StreamParser.o DigestAuthentication.o our_md5.o our_md5hl.o Base64.o Locale.o
ar: libliveMedia.a: File format not recognized
make[1]: *** [libliveMedia.a] Error 1
make[1]: Leaving directory `/home/juha/live/liveMedia'
make: *** [all] Error 2

```

---

### Post by andrew.46 on 2010-05-28
Hi Lockheed,

I have to confess that I am between Ubuntu installations at the moment so I cannot test this directly with any Ubuntu distro :(. But I have just downloaded the latest live555 libraries, which came out today or yesterday by the look of it, and they compiled fine on my current distro and worked well with the most recent MPlayer.

My suggestion would be to simply omit this step for the moment, MPlayer will compile without live555 support which is not the end of the world, and just wait to see if somebody with a working Ubuntu installation can test this.

BTW it is again an exciting time to be compiling the latest MPlayer as I see that [VP8]("http://en.wikipedia.org/wiki/VP8") decoding has just been added:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -vc help | grep -i 'vp8'[/COLOR]**
fflibvpx    ffmpeg    working   FFmpeg wrapper for libvpx/VP8  [libvpx]

```

Sorry to not have been more help :(.

Andrew

---

### Post by Lockheed on 2010-05-28
Thanks for replying. I tried compiling today's version and it worked without errors. However, it did not solve my underlying problem.

Your post mentions VDPAU as the output driver to use but if I use it, SMplayer crashes immidiately after starting playback:
```
mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao oss -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 104857968 -monitorpixelaspect 1 -noass -subfont-autoscale 1 -subfont-text-scale 5 -subcp CP1250 -subcc -vid 0 -aid 1 -subpos 100 -volume 50 -cache 2000 -ss 11 -osdlevel 0 -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 310 af=volume=10:0 /media/d/#Downloaded/Nip.Tuck.S07E09.HDTV.XviD-LOL.avi

MPlayer SVN-r31248-4.3.4 (C) 2000-2010 MPlayer Team

Playing af=volume=10:0.
File not found: 'af=volume=10:0'
Failed to open af=volume=10:0.


Playing /media/d/#Downloaded/Nip.Tuck.S07E09.HDTV.XviD-LOL.avi.

Cache fill:  0.00% (0 bytes)   
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  892.2 kbps (108.9 kbyte/s)
Clip info:
 Software: transcode-1.0.6
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=transcode-1.0.6
ID_CLIP_INFO_N=1
ID_FILENAME=/media/d/#Downloaded/Nip.Tuck.S07E09.HDTV.XviD-LOL.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=892248
ID_VIDEO_WIDTH=624
ID_VIDEO_HEIGHT=352
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=130088
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=2826.49
ID_SEEKABLE=1
ID_CHAPTERS=0
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mp3
[Mixer] No hardware mixing, inserting volume filter.
Video: no video
Starting playback...


MPlayer interrupted by signal 11 in module: seek
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```


and if I use "xv" which used to work for me splendidly before upgrading to 10.04, the result is this:
[[IMG]http://img99.imageshack.us/img99/597/image1ox.th.jpg[/IMG]](http://img99.imageshack.us/i/image1ox.jpg/)
The movie is being played but the picture frame is invisible.
At the same time, VLC plays everything with no problem.

---

### Post by gillza on 2010-05-28
> **m45t3r said:**
> Thanks.

I used these instructions to compile a MPlayer on Lucid Lynx with the latest libass and Matroska's ordered chapters support (not much useful for normal people, but for everyone who likes to watch animes like me it's essential) and now my MPlayer rocks:guitar:.
[B]
I strongly recommend who needs decent SubStation Alpha/Advance SubStation alpha subtitles support on Linux to compile MPlayer from this git.[/B]

One note: I had to use build-dep because I wanted NVIDIA's VDPAU support. But of course, you can just install libvdpau-dev:P.

Could you please explain how you installed latest libass and matroshka's ordered chapters support? 

P.S. I assume you have downloaded, compiled and installed LibASS from here but would like to make sure: [http://sourceforge.net/projects/libass/](http://sourceforge.net/projects/libass/)

---

### Post by mc4man on 2010-05-28
> Could you please explain how you installed latest libass and matroshka's ordered chapters support? 

go 
```
git clone git://repo.or.cz/mplayer-build.git
```

look inside the resultant mplayer-build folder for a readme, fairly straightfoward

(it will get the latest libass from git for you - you can add additional ffmpeg and or mplayer configure options if desired in the individual options file, though you probably won't need to.

---

### Post by Lockheed on 2010-05-29
Great. After this procedure my mplayer is so screwed it won't even play internet radio.

---

### Post by mc4man on 2010-05-29
>  ... as I see that VP8 decoding has just been added:

you will need to add libvpx-dev 
(don't see it as of yet in the ubuntu repos,  (will be in 10.10), available for lucid, karmic here
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by andrew.46 on 2010-05-31
And while I am again fiddling with MPlayer..... Has anybody experimented with rtmp support? I have just finished building [rtmpdump]("http://rtmpdump.mplayerhq.hu/") and MPlayer builds nicely against this to give support for rtmp streams. Not so many of these around but I tested against rtmp://peakbroadcasting.streamguys.org:80/vod/pepsi.flv, I attach a screenshot.

Andrew

---

### Post by Lockheed on 2010-05-31
andrew, would you have any idea why my smplayer shows no picture with XV and VDPAU results with: 
```
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```

---

### Post by Linuxforall on 2010-05-31
> **Lockheed said:**
> andrew, would you have any idea why my smplayer shows no picture with XV and VDPAU results with: 
```
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```

Hi,

Did you add libvdpau from synaptic if your driver was installed via hardware drivers, if you installed via nvidia's run file then its not necessary.

---

### Post by Lockheed on 2010-05-31
I am using newest drivers from nvidia installed manually.

---

### Post by Linuxforall on 2010-05-31
> **Lockheed said:**
> I am using newest drivers from nvidia installed manually.

Then VDPAU shouldn't be an issue at all but I suggest you add RVM's PPA to get latest SMPLAYER, I have always compiled mplayer using andrew's excellent instructions and am yet to run into issues, I also compile the latest ffmpeg and x264 following Fake Outdoorsman's excellent guide here.

---

### Post by Lockheed on 2010-05-31
> **Linuxforall said:**
> I suggest you add RVM's PPA to get latest SMPLAYER, I have always compiled mplayer using andrew's excellent instructions and am yet to run into issues.

But this is exactly what I am doing 4th time in a row.


Do you mind sharing a link to this Fake Outdoorsman's guide?

---

### Post by Linuxforall on 2010-05-31
> **Lockheed said:**
> But this is exactly what I am doing 4th time in a row.


Do you mind sharing a link to this Fake Outdoorsman's guide?

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Lockheed on 2010-05-31
> **Linuxforall said:**
> [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
Thanks, but still smplayer in unusable to me :(

---

### Post by Linuxforall on 2010-05-31
> **Lockheed said:**
> Thanks, but still smplayer in unusable to me :(

Is this version .69?

---

### Post by andrew.46 on 2010-06-01
Hi Lockheed,

> **Lockheed said:**
> andrew, would you have any idea why my smplayer shows no picture with XV and VDPAU results with: 
```
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```

I am sorry you are having such a frustrating time with MPlayer and I must add to your frustration a little as I do not have Ubuntu installed at the moment.... One of the reasons as well that I did not continue my MPlayer guides is that I was falling behind a little with vdpau in particular as well as git-mplayer and all the other 'extras' now associated with MPlayer :(.

Perhaps it would be a good time to remove *all* copies of MPlayer from your system and install both MPlayer and SMPlayer from RVM's PPA? This should eliminate a lot of possible compilation / configuration problems and should pretty much guarantee a decent working copy of both. The vdpau errors might point to a system error though...

All the best,

Andrew

---

### Post by Lockheed on 2010-06-01
Yes, I have the newest smplayer 0.6.9

> **andrew.46 said:**
> Perhaps it would be a good time to remove *all* copies of MPlayer from your system and install both MPlayer and SMPlayer from RVM's PPA? This should eliminate a lot of possible compilation / configuration problems and should pretty much guarantee a decent working copy of both.

Thanks for replying, Andrew. The thing is, I already did that twice and then installed everything from scratch using your guide. I am really fed up with ubuntu and planning to switch to Arch ASAP but it will still be some time before it's possible and in the meantime using VLC on Lucid feels so backward after using SMplayer for so long on Jaunty.

---

### Post by Linuxforall on 2010-06-01
Funny, SM player here works like a charm on Lucid as it did before on Jaunty, Karmic and Intrepid as well as Hardy, I always follow andrew's guide or install from RVM's repo which has fairly newer version than the ones included in Ubuntu repos. Arch won't be the panacea to your blues but its well worth a try.

---

### Post by Lockheed on 2010-06-04
An interesting development. Mplayers plays movies fine. It is just when I use SMplayer on the same files, it crashes.

---

### Post by andrew.46 on 2010-06-06
I forgot to add a screenshot of the current svn MPlayer playing a demonstration WebM VP8 file, so here it is. Looks like you can ignore guides that suggest patching MPlayer now, no patch is required with the current MPlayer and git libvpx. Demo files here: [http://www.webmfiles.org/demo-files/](http://www.webmfiles.org/demo-files/)

Andrew

---

### Post by Linuxforall on 2010-06-13
> **Lockheed said:**
> An interesting development. Mplayers plays movies fine. It is just when I use SMplayer on the same files, it crashes.

Did you select VDPAU in SMPLAYER video out ptions?

---

### Post by Linuxforall on 2010-06-13
> **andrew.46 said:**
> I forgot to add a screenshot of the current svn MPlayer playing a demonstration WebM VP8 file, so here it is. Looks like you can ignore guides that suggest patching MPlayer now, no patch is required with the current MPlayer and git libvpx. Demo files here: [http://www.webmfiles.org/demo-files/](http://www.webmfiles.org/demo-files/)

Andrew

Thanks Andrew, plays beautifully here with compiled mplayer under Lucid x64, thanks to your instructions.

---

### Post by Lockheed on 2010-06-13
> **Linuxforall said:**
> Did you select VDPAU in SMPLAYER video out ptions?
As I said, it crashes with VDPAU and shows invisible movie frame with XV.

---

### Post by Linuxforall on 2010-06-13
> **Lockheed said:**
> As I said, it crashes with VDPAU and shows invisible movie frame with XV.

Just compiled latest mplayer today and used it with latest smplayer from rvm's repos, vdpau works fine, so does webm movie on the demo. This is on Lucid x64. 

Can you try another mplayer shell like gnomeplayer etc.

---

### Post by Linuxforall on 2010-06-13
> **mc4man said:**
> you will need to add libvpx-dev 
(don't see it as of yet in the ubuntu repos,  (will be in 10.10), available for lucid, karmic here
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

I didn't add these libraries and yet mplayer compiled fine with vp8 support.

---

### Post by Lockheed on 2010-06-13
> **Linuxforall said:**
> Just compiled latest mplayer today and used it with latest smplayer from rvm's repos, vdpau works fine, so does webm movie on the demo. This is on Lucid x64. 

Can you try another mplayer shell like gnomeplayer etc.

Gnome Mplayer works just fine, so clearly the problem is with SMplayer.

---

### Post by Linuxforall on 2010-06-13
> **Lockheed said:**
> Gnome Mplayer works just fine, so clearly the problem is with SMplayer.

Yes in your case thats the culprit so if gnome player works with vdpau, I would stick to it even though its not as full featured as SMPLAYER, did you try to do a --purge remove smplayer and delete the smplayer folder in home and reinstall method?

---

### Post by mc4man on 2010-06-13
> didn't add these libraries and yet mplayer compiled fine with vp8 support.
I think you have to have vpx somewhere - 
Take a look in /mplayer/configure.log and search for libvpx, 

Ex. with a static build in /usr/local
> ============ Checking for libvpx ============

#include <vpx/vpx_decoder.h>
#include <vpx/vp8dx.h>
int main(void) { vpx_codec_dec_init(NULL, &vpx_codec_vp8_dx_algo, NULL, 0); return 0; }
clipped....
/usr/local/lib/libvpx.a(extend.c.o): In function `vp8_extend_mb_row':
Result is: yes

or with the packaged versions as supplied by either chromiun browser (daily ppa) or current gstreamer-bad plugin

> ============ Checking for libvpx ============

#include <vpx/vpx_decoder.h>
#include <vpx/vp8dx.h>
int main(void) { vpx_codec_dec_init(NULL, &vpx_codec_vp8_dx_algo, NULL, 0); return 0; }
clipped...
-L/usr/lib -lcaca -lvga -lSDL -lGL -ldl -lesd   -laudio -lXt -lpulse   -ljack -lopenal  -ltwolame -o /tmp/mplayer-conf--20458 -lvpx
Result is: yes 

Would be interested to see what yours shows

---

### Post by Linuxforall on 2010-06-13
> **mc4man said:**
> I think you have to have vpx somewhere - 
Take a look in /mplayer/configure.log and search for libvpx, 

Ex. with a static build in /usr/local


or with the packaged versions as supplied by either chromiun browser (daily ppa) or current gstreamer-bad plugin



Would be interested to see what your's shows

I don't have Chromium installed but do have Google Chrome, also I haven't added the Gstreamer ppa to my distro. I do have the gstreamer bad installed from repos, I have medibuntu enabled.

---

### Post by mc4man on 2010-06-13
Well I can say that mplayer isn't suppling so you're getting it from somewhere (and log should show

---

### Post by Lockheed on 2010-06-13
> **Linuxforall said:**
> Yes in your case thats the culprit so if gnome player works with vdpau, I would stick to it even though its not as full featured as SMPLAYER, did you try to do a --purge remove smplayer and delete the smplayer folder in home and reinstall method?

How do you check/change what GnomeMplayer is using? I cant find anything in options.

Purging smplayer made no difference. XV = invisible picture.

---

### Post by mc4man on 2010-06-13
I only have a laptop that can use vdpau and don't use it or gnome-mplayer much for video.
Anyway it seems gnome-mplayer uses a slightly different option set for vdpau based on some limited tests.

There is a place to input options for mplayer in edit - preferences but I find this better ->

There should be a separate gnome-mplayer section in ~/.mplayer/config

Using this allows vdpau w/ ffh264vdpau when used on a hd h264 vid,

> [gnome-mplayer]
ao=pulse
msglevel=all=5
vfm=ffmpeg
vo=vdpau

(when using mplayer itself I need to specify ffh264vdpau, gnome-mplayer just vfm=ffmpeg suffices.
Check by running gnome-mplayer from terminal with a -v option.

---

### Post by Linuxforall on 2010-06-13
> **mc4man said:**
> Well I can say that mplayer isn't suppling so you're getting it from somewhere (and log should show

Checked everywhere so unless Google Chrome bought it with its install, there is no other source here. I have compiled x264 and ffmpeg as well as installed libvpx using Fake Outdoorsman's guide and that could be the reason.

---

### Post by andrew.46 on 2010-06-14
Hi linuxforall,

> **Linuxforall said:**
> Thanks Andrew, plays beautifully here with compiled mplayer under Lucid x64, thanks to your instructions.

All we need now is a few more webm files in the wild :). Hopefully an explosion of these files will be coming our way over the next few months...

Andrew

---

### Post by Linuxforall on 2010-06-14
> **andrew.46 said:**
> Hi linuxforall,



All we need now is a few more webm files in the wild :). Hopefully an explosion of these files will be coming our way over the next few months...

Andrew

Also html5 so I can get rid of dreaded flash x32 from Adobe.

---

### Post by andrew.46 on 2010-07-06
Exciting times ahead:

```

------------------------------------------------------------------------
r31631 | ben | 2010-07-06 03:04:46 +1000 (Tue, 06 Jul 2010) | 4 lines

Support for unencrypted Blu-ray playback through libbluray.
  Use it through: mplayer br:////path/to/disc


```

Now if only I had a blue ray player.....

Andrew

---

### Post by sailor420 on 2010-07-07
Very interesting! I thought libbluray was effectively dead... Guess there's been some movement on that front!

I'll give this a shot once I get mplayer recompiled on my new system. Not sure from the release notes if it's looking for an actual unencrypted disk, folder structure (i.e. decrypted file structure as generated by AnyDVD), or an ISO image. Will have to tinker...

---

### Post by andrew.46 on 2010-07-07
Hi sailor,

> **sailor420 said:**
> Very interesting! I thought libbluray was effectively dead... Guess there's been some movement on that front!

Some activity here for sure:

[http://ns0.videolan.org/?p=libbluray.git;a=summary](http://ns0.videolan.org/?p=libbluray.git;a=summary)

Andrew

---

### Post by sailor420 on 2010-07-07
> **andrew.46 said:**
> Hi sailor,



Some activity here for sure:

[http://ns0.videolan.org/?p=libbluray.git;a=summary](http://ns0.videolan.org/?p=libbluray.git;a=summary)

Andrew

Well, this is going to have to wait a bit--I can't get that source to build. No config or make files included (just the automake files) and when I try to generate with automake, it bombs out.

Next question--I can get passthrough dts/ac3 working over spdif in mplayer with -ao alsa:device=spdif -ac hwac3, but I cannot for the life of me get spdif passthrough working in smplayer. Any ideas? I've tried enabling AC3/DTS passthrough in the smplayer menu, but it doesn't seem to be doing anything.

---

### Post by sailor420 on 2010-07-07
> **sailor420 said:**
> Well, this is going to have to wait a bit--I can't get that source to build. No config or make files included (just the automake files) and when I try to generate with automake, it bombs out.

Next question--I can get passthrough dts/ac3 working over spdif in mplayer with -ao alsa:device=spdif -ac hwac3, but I cannot for the life of me get spdif passthrough working in smplayer. Any ideas? I've tried enabling AC3/DTS passthrough in the smplayer menu, but it doesn't seem to be doing anything.

Of course, as soon as I post about it, I get it working. Here's what I did:

1. Change the driver to ALSA in smplayer config. Pulse doesn't support spdif passthrough from what I can tell.
2. Disable all audio filters in smplayer: uncheck the boxes "Enable the audio equalizer", "global volume", "use software volume control" and "volume normalization by default".

---

### Post by andrew.46 on 2010-07-08
Hello Sailor :)

Glad you worked out spdif thing as I have no idea! libblueray worked well enough for me with the single problem being that I am between Ubuntu installations at the moment and I ran it on slackware :(. This only required:

```

git clone git://git.videolan.org/libbluray --depth 1
cd libbluray
./bootstrap
./configure
make

```

and I did not install this to the system as I do not have a bluray drive after all, however checkinstall should make a decent package pretty easily for ubuntu...

Andrew

---

### Post by sailor420 on 2010-07-08
> **andrew.46 said:**
> Hello Sailor :)

Glad you worked out spdif thing as I have no idea! libblueray worked well enough for me with the single problem being that I am between Ubuntu installations at the moment and I ran it on slackware :(. This only required:

```

git clone git://git.videolan.org/libbluray --depth 1
cd libbluray
./bootstrap
./configure
make

```

and I did not install this to the system as I do not have a bluray drive after all, however checkinstall should make a decent package pretty easily for ubuntu...

Andrew

Well that worked. I missed the ./bootstrap script--I saw the configure.ac script and jumped straight to autoconf. Additionally, I needed the libtool packages, but that was easily solved as they are in the ubuntu repositories.

I'll recompile mplayer tonight and see how it goes...

---

### Post by sailor420 on 2010-07-09
Got blu-ray working last night! It's still in it's infant stages--menus dont work for instance, and you obviously have to have a valid blu-ray structure that has had the DRM removed (such as AnyDVD would create), but it works! It's a big step for Blu-Ray on Linux.

Here's what I had to do to get it working:

[LIST=1]
[*]apt-get install libtool
[*]Compile libbluray with ./bootstrap, ./configure, make, checkinstall.
[*]Config, compile, and checkinstall mplayer with --enable-bluray config flag
[*]Edit /etc/ld.so.conf to add line "Include /usr/local/lib" at bottom of file
[*]Run ldconfig
[*]Run mplayer with command mplayer br:////path/to/valid/bluray/folder/structure
[/LIST]

---

### Post by andrew.46 on 2010-07-09
Hello Sailor,

I am a little jealous, one day I will have to get a bluray drive :(. My only query is if you really have to specify *--enable-blueray*, normally with MPlayer libraries such as these are best left to autodetection:
```

andrew@skamandros~/source/mplayer/mplayer$ ./configure --help | grep 'bluray'
  --disable-bluray       disable Blu-ray support **[COLOR="Red"][autodetect][/COLOR]**
```

I agree with you completely, very exciting times are coming :).

Andrew

---

### Post by ron999 on 2010-07-25
Thanks for a great tutorial andrew.
I've installed mplayer-nogui and smplayer from SVN without problem. :D

Afterwards I found that the old version of tovid (0.31) that's available through Synaptic seemed to insist on using an old version of mplayer. :rolleyes:
So I've installed the current version of tovid (0.33) from their website.

Everthing's hunky dory. :guitar:

> ron@ubuntu:~$ mplayer
MPlayer SVN-r31800-4.3.4 (C) 2000-2010 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

---

### Post by andrew.46 on 2010-07-26
Hi Ron,

Glad to hear the guide worked for you :). 

Andrew

---

### Post by mc4man on 2010-07-26
In another interesting flip-flop with mplayer - maverick atm has gone back to using mplayer with the internal ffmpeg enabled, to bad it's a 15 month old version belatedly released in may (MPlayer 1.0rc3
So baring either a change in normal policy (releases over a svn version) or a newer mplayer 'release', building or ppa's will continue to hold great advantage

---

### Post by ron999 on 2010-07-26
> **mc4man said:**
> 
So baring either a change in normal policy (releases over a svn version) or a newer mplayer 'release', building or ppa's will continue to hold great advantage

Is this tutorial valid for other Ubuntu releases, not just Karmic?

---

### Post by mc4man on 2010-07-26
> Is this tutorial valid for other Ubuntu releases, not just Karmic?
Sure - you can use the basis of this guide for lucid or maverick.

The main difference is  there have been some dependency changes - mainly name changes for the same libs.
(also just keep informed if any new libs can be added for added support

I outlined this to some extent in post # 241

Also I'd adjust the checkinstall command in lucid and maverick to name it just mplayer instead of mplayer-nogui

Andrew's guides all present solid 'methods' that should be good for quite some time with minor adjustments if needed.


Edit: atm my laptop, which has the most enabled mplayer (lucid, nvidia), is unavailable till later today - thankfully the gpu burned out - the tech should be here today to replace the mobo - I'll ck. then to see what deps I used or added, if any, from prior posted list

---

### Post by andrew.46 on 2010-07-26
Hi mc4man,

> **mc4man said:**
> 
Andrew's guides all present solid 'methods' that should be good for quite some time with minor adjustments if needed.

I still regret a little not working on these guides and I have been thinking of writing a new one in my upcoming 2 months holiday, courtesy of Virtualbox, that would focus on the svn mplayer and *the most recent release* of Ubuntu in a 'rolling release' fashion. This would be a lot easier on my time while still giving a forum for those interested in the cutting edge MPlayer. This would be somewhat against the Ubuntu policy of support for older versions of the distro but it would certainly work better for usage of my time in front of a computer, which recently has had many constraints. 

Things missing at the moment from the guide at the moment include use of libvpx, easily added in by following Fakeoutdoorsman's guide, use of the external libass and perhaps rtmp support by compiling rtmpdump and a few other bits and pieces. If a new guide springs from the ashes I would again be constrained by my lack of a suitable card for vdpau and my considerable lack of interest in vaapi, -mt etc :).

Andrew

---

### Post by FakeOutdoorsman on 2010-07-26
> **andrew.46 said:**
> I still regret a little not working on these guides and I have been thinking of writing a new one in my upcoming 2 months holiday, courtesy of Virtualbox, that would focus on the svn mplayer and *the most recent release* of Ubuntu in a 'rolling release' fashion.
I like this idea and would prefer to this this myself as well.  Juggling the many Ubuntu revisions is a task in itself, and one that I have been falling behind on (no *libvpx* on any of the < Karmic FFmpeg guides for example).

---

### Post by andrew.46 on 2010-07-29
Hi mc4man,

> **mc4man said:**
> In another interesting flip-flop with mplayer - maverick atm has gone back to using mplayer with the internal ffmpeg enabled, to bad it's a 15 month old version belatedly released in may (MPlayer 1.0rc3

Some interesting times ahead, you may have already read this post:

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2010-July/065560.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2010-July/065560.html)

Sounds good?

Andrew

---

### Post by mc4man on 2010-07-29
> read this post:
If I'm reading correctly these packages will be in a ppa, the 'official' will do whatever it tends to do. (being nice
It is a real positive thing that Mr. Tartler does see the need for current mplayer builds and could be a great ppa for people.

For videos I've pretty much moved back to mplayer here - one setup supports vdpau and mplayer implements it very nicely.

(( I noticed you updated your vlc to the 0.6 (and 0.6 amd patch), too bad that need to patch isn't going away - though 0.6 is a pretty solid 'base' for vlc.

Though looking thru a script for something else I think one could   'sandbox' a shared ffmpeg just for vlc,  more of an exercise than practical...

---

### Post by andrew.46 on 2010-07-30
Hi mc4man,

> **mc4man said:**
> If I'm reading correctly these packages will be in a ppa, the 'official' will do whatever it tends to do. (being nice
It is a real positive thing that Mr. Tartler does see the need for current mplayer builds and could be a great ppa for people.

It will be good to see yet another option available under Ubuntu for those who need a more recent snapshot. Hopefully licensing constraints will not take some of the joy away from these changes.

> For videos I've pretty much moved back to mplayer here - one setup supports vdpau and mplayer implements it very nicely.

I gather MPlayer still requires at least the 190 version of the NVidia drivers? The svn MPlayer mega-thread I am toying with must make at least a reference to the required version but I am keen not to be involved in support for installation of display drivers.

> (( I noticed you updated your vlc to the 0.6 (and 0.6 amd patch), too bad that need to patch isn't going away - though 0.6 is a pretty solid 'base' for vlc.

That guide has not proven to be a big hit on these forums which is a pity when I think of the work I put into it :(. Still it taught me a lot about building vlc-git and vlc release, my own personal copy of vlc 1.1.1 is now built very specifically to my own needs and with a little more tinkering should be almost perfect :).

> Though looking thru a script for something else I think one could   'sandbox' a shared ffmpeg just for vlc,  more of an exercise than practical...


On a distro without the considerable constraints of dependency tracking a shared FFmpeg is no great drama. On my Slackware setup I compile vlc 1.1.1 against a shared FFmpeg and it works beautifully, even the ability to transcode to h264/aac etc works better, although I am not entirely clear why this should work better with shared rather than static...

Andrew

---

### Post by andrew.46 on 2010-07-30
Hi Fakeoutdoorsman,

> **FakeOutdoorsman said:**
> I like this idea and would prefer to this this myself as well.  Juggling the many Ubuntu revisions is a task in itself, and one that I have been falling behind on (no *libvpx* on any of the < Karmic FFmpeg guides for example).

Well in a fit of insomnia brought on by nightshift I have completed the threatened guide and posted it in tutorials and tips. Moderation can be a little variable so could be appearing soon or not so soon :). A few changes in approach in this guide that will hopefully make it more inviting to less technically-minded users...

Andrew

---

### Post by mc4man on 2010-07-30
> I gather MPlayer still requires at least the 190 version of the NVidia drivers? The svn MPlayer mega-thread I am toying with must make at least a reference to the required version but I am keen not to be involved in support for installation of display drivers

Anyone with a vdpau capable card will  be using nvidia-current or self installed from nvidia so that's not an issue at all starting in lucid onwards. Mplayer will autodetect support, at least here with nvidia-current that's just libvdpau-dev.
(have yet to use the nvidia site drivers, so don't know if they provide the headers or not, - I'm sure someone could say.

Other than that it would just be implementation - here I set mplayer to do so automatically thru a vc= line in the config 
It would be nice if mplayer could force/autoset a vo based on the vc, vdpau for the supported codecs, a default choice for the rest, xv here.
 - maybe it can and I don't see the way...

(though I tend to use mplayer from the right click menu where one can have as many 'different' named/configured mplayers as needed.

---

### Post by ron999 on 2010-07-31
> It is best to now leave $HOME/mplayer undisturbed as you can return at a later date to **run the command svn up** to download the latest changes in the MPlayer source code, and then recompile.

Hi
Please can you explain how to use **svn up** when I come to update mplayer-nogui.
What's the update procedure?

---

### Post by mc4man on 2010-07-31
> What's the update procedure? 
just cd to your mplayer source folder, make sure your source is clean,
(if you didn't do after previous build then run 
make distclean
to update simply this - will update any changed files

svn up 

Then, if desired, do a new build starting at the 
./configure <whatever you used or now want to use>

---

### Post by ron999 on 2010-07-31
Thanks mc4man

I understand.
Mission accomplished.:D
> MPlayer SVN-r31878-4.3.4 (C) 2000-2010 MPlayer Team

---

### Post by andrew.46 on 2010-07-31
Hi,

Once again despite my many claims that I will no longer write MPlayer guides for Ubuntu a 'new improved' version has landed :). Aimed specifically at Lucid Lynx the plan is that it will track the most recent release version of Ubuntu rather than remain locked at a single Ubuntu version. Feel free to use and comment:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Andrew

---

### Post by ron999 on 2011-02-15
Hi andrew.46
I still update mplayer regularly using SVN with this guide.
But I've seen a post by qyot27 explaining about git.
Here:- [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10462391&postcount=1513]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10462391&postcount=1513")

If I use git instead, please will you look through these commands to see if they're OK.

```
git clone git://repo.or.cz/mplayer-build.git && cd mplayer-build && ./init && ./disable-mt
make
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default --pkgversion "3:1.0~git-`date +%Y%m%d%H%M`"

```
I've got two questions.
With my SVN version I had a command:-
```
./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-mencoder --disable-x264
```
Do you recommend that I still use that command, or can I modify it or drop it altogether?

The checkinstall command. Can I tidy it up and is this the correct package version?:-
```
--pkgversion "3:1.0~git-`date +%Y%m%d%H%M`"
```

---

### Post by andrew.46 on 2011-02-17
Hi Ron,

My involvement in these Forums is winding down somewhat I am afraid so I will only tracking this and other guides rarely :(. As for that git repository, this belongs to Uoti Urpala who maintains a fork of MPlayer and I am afraid that I have never really tried his work, except of course for all of his work that is already included in MPlayer :). As for the syntax, the warning remains concerning the gcc version so I would tend to leave this in place, the checkinstall naming convention is simply to avoid the repository MPlayer overwriting your compiled version.

All the very best,

Andrew

---

### Post by ron999 on 2011-02-17
> **andrew.46 said:**
> the checkinstall naming convention is simply to avoid the repository MPlayer overwriting your compiled version.


Hi Andrew
I don't know what the naming convention is for this git version of mplayer.
This was just a guess:- [B]--pkgversion "3:1.0~git-`date +%Y%m%d%H%M`"
[/B]
Should I ask someone else about the version number?

---

### Post by andrew.46 on 2011-02-18
> **ron999 said:**
> I don't know what the naming convention is for this git version of mplayer.
This was just a guess:- [B]--pkgversion "3:1.0~git-`date +%Y%m%d%H%M`"
[/B]

The naming conventions I have used for the checkinstall packages of MPlayer have always had 2 purposes:

[LIST=1]
[*]To have a higher version number than the repository MPlayer and thus prevent the older repository version overwriting the local, compiled copy.
[*]To give a quick idea, by looking at the package name, when the remote repository has been accessed.
[/LIST]

The pkgversion syntax you have suggested should do just that. You can always attempt to catch to catch the git commit number if you wish to get fancy but simple is often better :).

---

### Post by ron999 on 2011-02-18
> **andrew.46 said:**
> ... You can always attempt to catch to catch the git commit number if you wish to get fancy ...

Hi Andrew
That's what I tried to do.


My version of mPlayer from this git is:-
MPlayer git-cba6d60-4.4.1 (C) 2000-2011 MPlayer Team

So I've used:- --pkgversion "4.4.1-git-`date +%Y%m%d`"
to give:- mplayer-nogui_4.4.1-git-20110217-1_i386.deb

With ffmpeg we use --pkgversion="5:$(./version.sh)"
To give:- ffmpeg_5:git-5b54d4b-1_i386.deb
But this method doesn't seem to work for the mPlayer git.

---

### Post by andrew.46 on 2011-02-18
BTW Ron if you are running a 32bit installation you would be best to pick up the [new assemblage of codecs]("http://www.mplayerhq.hu/MPlayer/releases/codecs/") that the MPlayer developers have put together end of January 2011, they have added in a few extra codecs that were kicking around the MPlayer site. I note that Medibuntu is still using an older package...

---

### Post by ron999 on 2011-02-18
Hi Andrew
Yes, I have a 32 bit system.

Those codecs are already there in my usr/local/lib/codecs folder.
They are all dated Sat 05 Feb 2011.

---

