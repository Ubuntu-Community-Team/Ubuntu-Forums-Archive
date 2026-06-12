---
title: "Tip/how to:video recording,converting,editing"
date: 2007-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Amazona aestiva on 2007-08-19
[COLOR="Red"][SIZE="5"]**Thread closed, use it at your own risk!**[/SIZE][/COLOR]

Hi! Let's start video editing!
I'll give You a few tips and a little information about this.

**[COLOR="Red"]I've only tested the x86 packages, of Feisty Fawn and Gutsy Gibbon.[/COLOR]**

[COLOR="SeaGreen"]**Last updated: 02-03-2008**[/COLOR]

I use the followings: Avidemux, Kino, Kdenlive, DeVeDe, MPlayer, Kaffeine, Amarok and Audacity.

**[COLOR="Navy"]I think the most reliable video editor and player: Avidemux & VLC media player[/COLOR]**

[COLOR="Red"]_**[SIZE="4"]Before start:[/SIZE]**_
It is recommended to install ffmpeg, mencoder, libxvidcore4, Xine, w32codecs and GStreamer because these are used by many programs![/COLOR](players and encoders)
[COLOR="RoyalBlue"]**Easy way to install these:**[/COLOR]
**Feisty:**
```
sudo apt-get install gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-misc gstreamer0.10-alsa gstreamer0.10-doc gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-gnonlin-dev gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-sdl gstreamer0.10-tools gstreamer0.10-x gstreamer-tools irb1.8 liba52-0.7.4 libbreakpoint-ruby1.8 libcdaudio1 libcmdparse2-ruby1.8 libdaemonize-ruby1.8 libdvdnav4 libdvdread3 libdvdplay0 libfaac0 libfaad2-0 libfreebob0 libgems-ruby1.8 libglib2-ruby libgsm1 libgstreamer0.8-0 libgstreamer0.8-ruby libgstreamer0.10-0 libgstreamer0.10-0-dbg libgstreamer0.10-ruby1.8 libgstreamer-gconf0.8-0 libgstreamer-perl libgstreamer-plugins0.8-0 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-pulse0.10-0 libid3tag0 libjack0.100.0-0 libjinglebase0.3-0 libjinglep2p0.3-0 libjinglexmllite0.3-0 libjinglexmpp0.3-0 liblame0 liblog4r-ruby1.8 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libncurses-ruby1.8 libopenssl-ruby1.8 libpulse0 libquicktime0 libreadline-ruby1.8 libruby1.8 libruby1.8-dbg libruby1.8-extras libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxvidcore4 libxvidcore4-dev rdoc1.8 ruby1.8 ruby ffmpeg mencoder mplayer xvid4conf libxine-extracodecs libxine1-ffmpeg libxine1 mozilla-mplayer
```
**Gutsy:**
```
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-gnonlin-dev gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-schroedinger gstreamer0.10-sdl gstreamer0.10-x libgstreamer0.10-0 irb1.8 liba52-0.7.4 libcdaudio1 libdvdnav4 libdvdread3 libfaac0 libfaad2-0 libfreebob0 libid3tag0 libjack0.100.0-0 libjinglebase0.3-0 libjinglep2p0.3-0 libjinglexmllite0.3-0 libjinglexmpp0.3-0 liblame0 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libncurses-ruby1.8 libopenssl-ruby1.8 libpulse0 libquicktime0 libreadline-ruby1.8 libruby1.8 libruby1.8-dbg libruby1.8-extras libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxvidcore4 libxvidcore4-dev rdoc1.8 ruby1.8 ruby ffmpeg mencoder mplayer xvid4conf libxine1-ffmpeg libxine1 mozilla-mplayer
```
[COLOR="Red"]**Install libdvdcss2:**[/COLOR]
[libdvdcss2 1.2.9 - x86]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2%2bbuild1_i386.deb")
[libdvdcss2 1.2.9 - amd64]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_amd64.deb")

[COLOR="Red"]**and install w32codecs too:**[/COLOR]
[w32codecs - x86]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb")
Under 64 bit it's difficult a bit:
Download and unpack these files from [this]("ftp://ftp4.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2"), to /usr/lib/win32/
[COLOR="Red"]Permission[/COLOR] to do this:
Type:
```
gksudo nautilus
```
**[COLOR="Red"][SIZE="3"]!Warning![/SIZE][/COLOR]** A window should appear, and You'll have permission to anything in it, so _[COLOR="Red"]BE CAREFUL![/COLOR]_ **[COLOR="Red"][SIZE="3"]!Warning![/SIZE][/COLOR]**

[COLOR="Red"]
**[SIZE="3"]Note 1:[/SIZE]** MEncoder has a serious bug, that makes the output sound HORRIBLE(when encoding)! I advise to check it using DeVeDe's preview option. Don't install this fix if needn't.[/COLOR]
[COLOR="RoyalBlue"]**Install:**[/COLOR]
[mplayer_fixed.tar.bz2]("http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2")
Install steps:
1.Unpack it
2.Open terminal
3.type cd (directory where you extracted) Example: cd '/home/nandor/Desktop/mplayer_fixed'
4.Type:```
sudo ./install.sh
```
5.Than You should see "Done. MPlayer and Mencoder downgraded." which means success!


**[COLOR="DarkRed"][SIZE="3"][CENTER]_______________________________________[/CENTER][/SIZE][/COLOR]**



[SIZE="5"]**[COLOR="DarkOrange"]Movie collection managers:[/COLOR]**[/SIZE]
[SIZE="3"][COLOR="DarkRed"]**Griffith:**[/COLOR] [/SIZE]
It's really nice!:)
**Feisty:**
```
sudo apt-get install griffith
```
**Gutsy:**
[Griffith 0.9.6 - x86 and amd64]("http://www.getdeb.net/app.php?name=Griffith")


[SIZE="3"][COLOR="DarkRed"]**GCstar:**[/COLOR] [/SIZE]
**Gutsy:**
[GCstar 1.3.2 - x86 and amd64]("http://www.getdeb.net/app/GCstar")

[SIZE="5"]
[COLOR="DarkOrange"]**Video/Audio players:**[/COLOR][/SIZE]
[SIZE="3"][COLOR="DarkRed"]**Totem:**[/COLOR] [/SIZE][COLOR="RoyalBlue"]**(default)**[/COLOR]
It's codec(GStreamer) is buggy, because it's under development.
Example: Seek Slider go mad when playing .mpg, and error message.
There is another version of Totem, which uses the Xine codec. You have to choose, because totem-gstreamer and totem-xine cannot be installed same time.
[COLOR="RoyalBlue"]**Install: **[/COLOR]
```
sudo apt-get install totem-xine
```

[SIZE="3"][COLOR="DarkRed"]**Kaffeine:**[/COLOR] [/SIZE][COLOR="Purple"]**One of my favorites!**[/COLOR]
This is a very nice player. It plays almost everything! So If You want to use only one player, this is what You need!
[COLOR="RoyalBlue"]**Install:**[/COLOR] 
1. Download and install from here: ([COLOR="Red"]Don't[/COLOR] start Kaffeine until I say!)
[Kaffeine 0.8.5 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Kaffeine")
**Gutsy:**```
sudo apt-get install kaffeine
```

2. Install libdvdcss2 and w32codecs, if you haven't done it.

3. Now start Kaffeine. The first window checks the codecs and other things. Everything should be OK.

[SIZE="3"]
[COLOR="DarkRed"]**Mplayer:**[/COLOR][/SIZE] [COLOR="Purple"]**One of my favorites!**[/COLOR]
Many supported formats to play.
It has  a lot of extra features, like equalizer and skins.
[COLOR="RoyalBlue"]**The first Code installs it, and it's Mozilla Firefox plug-in.**[/COLOR]
[There is a newer one for Gutsy.]("http://www.getdeb.net/app.php?name=MPlayer")
If it cannot initialize video output device:
Preferences->Video
There I chose "gl2 X11 (OpenGL) - multiple textures version".

[SIZE="3"][COLOR="DarkRed"]**VLC media player:**[/COLOR][/SIZE]
Really nice, with many and useful features.
Supported formats: .avi/.mpg/.mp3/.ogg(vorbis audio)/etc.
Something special: VLC converts video and audio files into other format!
[COLOR="RoyalBlue"]**Install:**[/COLOR]
```
sudo apt-get install vlc
```

[SIZE="3"]**[COLOR="DarkRed"]Songbird:[/COLOR]**[/SIZE]
Songbird is a desktop Web player, a digital jukebox and Web browser mash-up. Like Winamp, it supports extensions and skins feathers.
[COLOR="RoyalBlue"]**Install:**[/COLOR]
[Songbird 0.4 - x86 and amd64 - Gutsy]("http://www.getdeb.net/app.php?name=Songbird")
[Songbird 0.2.5 - x86 - Feisty]("http://www.getdeb.net/app.php?name=Songbird")


[SIZE="3"][COLOR="DarkRed"]**User interface (GUI) for Xine:**[/COLOR] [/SIZE]"Xine Player"
[COLOR="RoyalBlue"]**Install:**[/COLOR]
```
sudo apt-get install xine-ui
```

[SIZE="5"]
[COLOR="DarkOrange"]**Audio players:**[/COLOR][/SIZE]
[SIZE="3"][COLOR="DarkRed"]**Amarok:**[/COLOR][/SIZE] [COLOR="Purple"]**One of my favorites!**[/COLOR]
Beautiful and stable with many extra features!:D
Winamp like player. (I think Amarok is much better than Winamp.)
It can:
-connect to URL
-equalizer, visualizations and much much more!
[COLOR="RoyalBlue"]**Install:**[/COLOR]
```
sudo apt-get install amarok
```
[A special applet for Amarok.]("http://www.getdeb.net/app.php?name=Kirocker")

[SIZE="3"][COLOR="DarkRed"]
**Banshee:**[/COLOR][/SIZE]
Good music player, try it!
[COLOR="RoyalBlue"]**Install:**[/COLOR]
[Banshee 0.13.1 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Banshee")
**Gutsy:**```
sudo apt-get install banshee
```


[SIZE="3"][COLOR="DarkRed"]**Exaile!:**[/COLOR][/SIZE]
Amarok like audio player for Gnome.
[COLOR="RoyalBlue"]**Install:**[/COLOR]
[Exaile! 0.2.10 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Exaile")
**Gutsy:**```
sudo apt-get install exaile
```


[SIZE="3"][COLOR="DarkRed"]**Rhythmbox:**[/COLOR] [/SIZE][COLOR="RoyalBlue"]**(default)**[/COLOR]
It works very well, but Amarok much better!


[COLOR="DarkOrange"]
[SIZE="5"]**DVD ripping:**[/SIZE][/COLOR]
[SIZE="3"][COLOR="DarkRed"]**Acidrip:**[/COLOR][/SIZE]
Quite well featured program. Easy to use and install.
Uses xvid, x264 and others.
More: crop, scale.
I advise this for everybody.
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://www.linuxtopia.org/online_books/linux_beginner_books/debian_linux_desktop_survival_guide/AcidRip_Simple.shtml") 
```
sudo apt-get install acidrip
```


[SIZE="3"][COLOR="DarkRed"]**Thoggen DVD ripper:**[/COLOR][/SIZE]
It exports to ogg theora video only.
[COLOR="RoyalBlue"]**Install:**[/COLOR]
```
sudo apt-get install thoggen
```


[SIZE="3"][COLOR="DarkRed"]**DVD95:**[/COLOR][/SIZE]
Works fine, but I don't know how to change language to English.
[COLOR="RoyalBlue"]**Install:**[/COLOR]
```
sudo apt-get install dvd95
```


[SIZE="3"][COLOR="DarkRed"]**DVD::rip:**[/COLOR][/SIZE]
This is the advanced tool for ripping. There are a lot of features in it:
-export to ogg,avi,mpg(uses ffmpeg, xvid and others)
-uses mp3&ac3 audio codec, with multiple audio tracks
-rip subtitles
-crop frame
I advise this to skilled people.
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://www.exit1.org/dvdrip/doc/gui.cipp") 
```
sudo apt-get install dvdrip subtitleripper
```
[COLOR="RoyalBlue"]**_and_ install the attached .deb!(needed for subtitles)**[/COLOR]

[COLOR="DarkOrange"][SIZE="5"]
**Creating a video disc:**[/SIZE][/COLOR]
[SIZE="3"][COLOR="DarkRed"]**DeVeDe:**[/COLOR][/SIZE] [COLOR="Purple"]**One of my favorites!**[/COLOR]
It makes DVD, VCD, SVCD, CVD and DivX from mpg/avi/perhaps more. It is simple to use! Automatic menu creation.
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://www.my-guides.net/en/content/view/75/") 
[DeVeDe 3.2 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=DeVeDe")
[DeVeDe 3.6 - x86 and amd64 - Gutsy]("http://www.getdeb.net/app.php?name=DeVeDe")


[SIZE="3"][COLOR="DarkRed"]**ManDVD:**[/COLOR][/SIZE]
.mpg/.avi(divx,xvid)/(perhaps more)->DVD+advanced,customizable menu
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://www.dvd-guides.com/content/view/208/59/") 
[ManDVD 2.4 - x86 and amd64 - Gutsy and Feisty]("http://www.getdeb.net/app.php?name=ManDVD")


[SIZE="3"][COLOR="DarkRed"]**QDVDAuthor:**[/COLOR][/SIZE]
A DVD, slideshow, etc. maker program.
[COLOR="RoyalBlue"]**Install:**[/COLOR] 
[QDVDAuthor 1.0.0 - x86 and amd64 - Gutsy]("http://www.getdeb.net/app.php?name=QDVDAuthor")


[SIZE="3"][COLOR="DarkRed"]**DVDStyler:**[/COLOR][/SIZE]
.mpg->DVD-video(Video_TS/.iso)
Creates menu.
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://docs.pclinuxos.com/CreatingVideoDVDCreate") 
[DVDStyler 1.4 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=DVDStyler")


[SIZE="3"][COLOR="DarkRed"]**Tovid:**[/COLOR][/SIZE]
It is a collection of video disc authoring tools.
Lots of options(4:3/16:9,menu-submenu,customizable colors, backgrounds,etc.)
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://tovid.wikia.com/wiki/Using_the_tovid_GUI") 
[Tovid 0.31 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Tovid")


[COLOR="DarkOrange"][SIZE="5"]**Video converting, compressing , editing:**[/SIZE][/COLOR]
[SIZE="3"][COLOR="DarkRed"]**Avidemux:**[/COLOR][/SIZE] [COLOR="Purple"]**One of my favorites!**[/COLOR]
It's a very good video file compressing/converting program.
.mpg->avi/.dv->.avi and much more, with many options!;)

Lots of filters:
-transform:crop,resize,rotate,fade,etc.
-interlacing:yadif,mcDeinterlace,Deinterlace,DGBob,etc.
-colors:Mplayer eq2,Mplayer hue,contrast,luma equalizer,etc.
-noise:Mplayer denoise3d,Mplayer hqdn3d,FluxSmooth,etc.
-sharpness:Sharpen,MSharpen,asharp,etc.
-subtitles:Subtitler,Vobsub,etc.
-misc:Blend remover,Hard pulldown removal,etc.

[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://avidemux.org/admWiki/index.php?title=Main_Page#Using_Avidemux") 
[Avidemux 2.4 - x86 and amd64 - Gutsy, Feisty]("http://www.getdeb.net/app.php?name=Avidemux")


[SIZE="3"]**[COLOR="DarkRed"]ConvertIT:[/COLOR]**[/SIZE]
If I want to be simple, this is a GUI, which uses MEncoder, ffmeg, w32codecs, etc. It converts audio too.
Extremely lots of file types are supported!
[COLOR="RoyalBlue"]**Install steps**[/COLOR] and [COLOR="DarkSlateBlue"]**guide:**[/COLOR]
[http://ubuntuforums.org/showthread.php?t=567016]("http://ubuntuforums.org/showthread.php?t=567016")


[SIZE="3"]**[COLOR="DarkRed"]QTTube:[/COLOR]**[/SIZE]
This can download any film from You Tube.
[COLOR="RoyalBlue"]**Install:**[/COLOR]
[QTTube 0.2pre1 - x86 and amd64 - Feisty, Gutsy]("http://www.getdeb.net/app.php?name=QTTube")


[SIZE="3"][COLOR="DarkRed"]**Gmencoder:**[/COLOR][/SIZE]
It is a gnome-2 front-end(GUI) to mplayer/mencoder. It's a video converter.
[COLOR="RoyalBlue"]**Install:**[/COLOR]
[Gmencoder 0.1.0 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Gmencoder")


[SIZE="3"]**[COLOR="DarkRed"]Converting ogg to avi:[/COLOR]**[/SIZE](recordMyDesktop's ogg files)
**Output audio is MP3, video is ???:**
```
mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc
```
**Output audio is MP3, video is x.264:** This is rally good, but a little unsupported format. (DVD Players can't play it for example)
```
mencoder /inputfilepath.ogg -o /outputfilepath.avi -oac mp3lame -ovc x264
```
**Output audio is MP3, video is XviD:** Hard supported and high quality in a small file. My favorite.
NOTE:This only converts the ogg to a compatible file. So make the final output with Avidemux. For example you might need to change resolution. (This doesn't modify it)
```
mencoder -idx input.ogg -ovc xvid -xvidencopts bitrate=4500 -oac mp3lame -srate 44100 -o output.avi
```


[SIZE="5"][B][COLOR="DarkOrange"]
Video recording and editing:[/COLOR][/B][/SIZE]
[SIZE="3"][COLOR="DarkRed"]**Kino:**[/COLOR][/SIZE] [COLOR="Purple"]**One of my favorites!**[/COLOR]
This captures from miniDV camcoders by using IEEE 1394.
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://www.kinodv.org/docbook/") 
[Kino 1.1.1 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Kino")
[Kino 1.3.0 - x86 and amd64 - Gutsy]("http://www.getdeb.net/app.php?name=Kino")

[COLOR="Red"]Giving permissions to Kino:[/COLOR]
[COLOR="RoyalBlue"]If Kino wants raw1394 to be loaded and permissions to it, type:[/COLOR]
```
sudo chown 666 /dev/raw1394
```
Might need to type [COLOR="Red"]every time[/COLOR] after reboot.

Kino can:
-capture in 4:3 or 16:9, PAL or NTSC
-capture from firewire port(IEEE 1394)
-edit the captured files
-save projects in SMIL 2.0/Kino 0.9.1 XML/MJPEG Tools ELI/SRT subtitle
-add effects
-import .mpg/.avi/.ogg Theora Video files/perhaps more (import is unstable sometimes)

I advise to use Avidemux to compress the recorded dv files.

Kino captures in .dv so you need approximately 30GB to record 120min and more space to export! And don't capture more than 120min into one file. Kino might make a mistake.


[SIZE="3"][COLOR="DarkRed"]**Cinelerra:**[/COLOR][/SIZE]
Multitrack video editor and recorder.
Open: .vob/.mpg/.avi[COLOR="Red"]*[/COLOR]/m2v/.m1v/.mov/.mp2/.mp3/.wav/.ifo/.xml
Render(export): .avi/.ogg(theora/vorbis)/.mov/ !I couldn't get every working!
[COLOR="Red"]* Not all of the avi files can be opened![/COLOR]

Cinelerra can:
-capture in many formats and options from many sources(It's VERY difficult to configure them right)
-Many kinds of overlay video track: normal, addition, subtract, multiply, etc.
-Many kinds of effects and transitions

[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://cv.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_toc.html#SEC_Contents")
[Gutsy]("http://ubuntuforums.org/showthread.php?t=596160")


[SIZE="3"][COLOR="DarkRed"]**Kdenlive:**[/COLOR][/SIZE]
A really nice non-linear video editor with hard container support. It supports DV and HDV recording too.
Open: .avi/.mpg/.rm/.mp4/"Quicktime"/.wav/.ogg/.mp3/.jpg/.tiff/.png etc.
Export: Flash/ Real Video/ Quicktime/ mpeg/ mpeg-4(AVI)/Xvid / DVD/ DV/ HDV/ AC3/ MP3/ WAV/ OGG Vorbis in many options (quality, resolution)
It has effects, subtitles and transitions.
It will capture from Firewire if You install dvrgrab or ffplay too.
[COLOR="Red"]If Kdenlive 0.4 is installed need to uninstall it: (The following installs the 0.5!)[/COLOR]
```
sudo apt-get remove mlt mlt++ kdenlive
```

[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://en.wikibooks.org/wiki/Kdenlive/Quickstart#Meeting_the_Kdenlive_interface") 
**Gutsy:**```
sudo apt-get install kdenlive
```[B]

Feisty:[/B]
[COLOR="RoyalBlue"]**x86:**[/COLOR]
-First step:
Download&install:[mlt 0.2.3]("http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/mlt_0.2.3+svn20070720~3v1ubuntu0_i386.deb")

-Second step:
Download&install:[mlt++ 0.2.2]("http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/mlt++_0.2.2+svn20070612~3v1ubuntu0_i386.deb")

-Third step:
Download&install:[Kdenlive 0.5]("http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/kdenlive_0.5+svn20070909~3v1ubuntu0_i386.deb")

[COLOR="RoyalBlue"]**amd64:**[/COLOR][http://ubuntuforums.org/showthread.php?t=196093]("http://ubuntuforums.org/showthread.php?t=196093")

Extra step: (Kdenlive works without this)
To capture from Firewire download&install: (Perhaps already installed)
[dvgrab 1.8-4 - x86]("http://ftp3.nrc.ca/debian/pool/main/d/dvgrab/dvgrab_1.8-4_i386.deb")
[dvgrab 1.8-4 - amd64]("http://ftp3.nrc.ca/debian/pool/main/d/dvgrab/dvgrab_1.8-4_amd64.deb")


[SIZE="3"][COLOR="DarkRed"]**LIVES:**[/COLOR][/SIZE]
Linear and non-linear video editor. DV and HDV recording from Firewire. I think it's slow a bit and quite difficult to use! Lots of effects, features, container support and it uses JACK.
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://lives.sourceforge.net/index.php?do=tutorial-wiki")
[LiVES 0.9.8.6 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=LiVES")
[LiVES 0.9.8.7 - x86 and amd64 - Gutsy]("http://www.getdeb.net/app.php?name=LiVES")


[COLOR="DarkOrange"][SIZE="5"]**Audio recording, mixing, editing, converting:**[/SIZE][/COLOR]
[SIZE="3"][COLOR="DarkRed"]**Ardour:**[/COLOR][/SIZE]
Ardour is a very advanced tool for audio mixing and editing. See [this]("http://www.getdeb.net/media.php?id=281&type=screens&w=425&h=350")!
I advise this to skilled peaple!
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://ardour.org/files/manual/index.html") 
[Ardour 2.0.5 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Ardour")
[Ardour 2.2 - x86 and amd64 - Gutsy]("http://www.getdeb.net/app.php?name=Ardour")
[SIZE="3"][COLOR="DarkRed"]


**Audacity:**[/COLOR][/SIZE] [COLOR="Purple"]**One of my favorites!**[/COLOR]
Works quite well.
Audacity likes Jack, but I found that Jack makes issues.(short pauses during record)
So I advise to use ALSA for recording and playing.
You can select these at:Edit->Preferences->Audio I/O
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://audacity.sourceforge.net/manual-1.2/") 
[Audacity 1.3.3 - x86 and amd64 - Feisty]("http://www.getdeb.net/app.php?name=Audacity")
**Gutsy:**```
sudo apt-get install audacity
```

If Audacity says this when you try to capture:
> Error while opening sound device. Please check the input device settings and the project sample rate.
-You should close other opened recorders like gtk-recordMyDesktop.
-Try to choose other devices (Audio I/O).(I uses "ALSA: Ensoniq AudioPCI: ES1371 DAC2/ADC (hw:0,0)" for recording, and "ALSA: Ensoniq AudioPCI: ES1371 DAC1 (hw:0,1)" for playing)
-48000Hz usually good for sample rate

[SIZE="3"][COLOR="DarkRed"]**LMMS:**[/COLOR][/SIZE]
This is a mixer, editor.
Many kinds of plug-ins...(see the YouTube video at the install link)
[COLOR="RoyalBlue"]**Install:**[/COLOR] [[COLOR="DarkSlateBlue"]**Guide**[/COLOR]]("http://lmms.sourceforge.net/wiki/index.php?title=Main_Page") 
[LMMS 0.3.0 - x86 - Feisty]("http://www.getdeb.net/app.php?name=LMMS")
**Gutsy:**```
sudo apt-get install lmms
```

[SIZE="3"][COLOR="DarkRed"]**SoundConverter:**[/COLOR][/SIZE]
It knows .ogg Vorbis/.mp3/.flac/.wav formats.
Simple, easy to use and it works!
[COLOR="RoyalBlue"]**Install:**[/COLOR]
```
sudo apt-get install soundconverter
```


[SIZE="3"]**[COLOR="DarkRed"]Converting wav to aac:[/COLOR]**[/SIZE]
As I know most mobile phones use this(aac) file type. I found that wav is more compatible with FAAC than mp3. However it's your choice.
[COLOR="RoyalBlue"]**Install:**[/COLOR]
```
sudo apt-get install faac
```
Than use this command:
```
faac -c 8000 -q 90 -o OUTPUT.aac INPUT.wav
```
-c 8000 is the sample rate(might use higher)
-q 90 is the quality(100 is the best)
type "faac --help" for more options


[SIZE="5"]**[COLOR="DarkOrange"]Appendix:[/COLOR]**[/SIZE]
[COLOR="DarkRed"]**MythTV:**[/COLOR]
[Information about it.]("http://www.mythtv.org/docs/mythtv-HOWTO-1.html#ss1.1")
[COLOR="RoyalBlue"]**Someone has found an easy way to install it:**[/COLOR]
[http://ubuntuforums.org/showthread.php?t=536555]("http://ubuntuforums.org/showthread.php?t=536555")
**Gutsy:** In the repository.


**[COLOR="DarkRed"][SIZE="3"][CENTER]_______________________________________[/CENTER][/SIZE][/COLOR]**



**[SIZE="4"][COLOR="RoyalBlue"]At the end of this:[/COLOR][/SIZE]**

[COLOR="RoyalBlue"][B]Now You know which program is needed for You. Only have to learn how to use it!

If You use a good multimedia software, and I haven't written about it, PLEASE post Its name and a short description!
However I've written "I advise this to skilled people!" many times, nobody gets skills without trying out things!;)
I advise to try many options with a short film (1-2min), and check what are the results of different options.
Get error message? Have question? Post it!
And sorry for grammar... I'm learning English.[/B][/COLOR]

**[SIZE="3"][COLOR="DarkOrange"]Best regards, Nándor[/COLOR][/SIZE]**

---

### Post by strungoutfan78 on 2007-08-24
Thanks for the breakdown.  Very informative post.  I've used Kino in the past to create DVD's from avi files, but that was back when I used KDE.  Now that I'm using Gnome I wonder are there any issues with Kino and Gnome?  Or does it work just fine?

---

### Post by Amazona aestiva on 2007-08-24
:)Kino is perfect I think.Just a few errors, but can repair them.:)

---

### Post by celafon on 2007-08-24
> **strungoutfan78 said:**
> Thanks for the breakdown.  Very informative post.  I've used Kino in the past to create DVD's from avi files, but that was back when I used KDE.  Now that I'm using Gnome I wonder are there any issues with Kino and Gnome?  Or does it work just fine?

I am not sure who spread the idea that kde and gnome are incompatible. An application either a KDE or a Gnome one is just a normal X window application that is using different libs for their desktop needs to show you things and do things, but there is nothing unusual going on here. Im using bunch of KDE apps on Gnome and vice versa (I am switching WMs from time to time)...

So remember KDE app does not bite :) It only needs more libraries and KDE specific things to be present in the system.

I actually had an idea that Kino was gtk based, but than I realized there is that K in here :lolflag:

EDIT: BTW that is a nice summary for the movie/cam things. But have you got an idea which app would be best for joining and cutting video? Kino? Haven't used it much so not sure if it will work...

EDIT2: HEY! Kino is GTK based! (at least in here:) )

---

### Post by chrome307 on 2007-08-26
Excellent thread ........... newbie proof :)

---

### Post by Amazona aestiva on 2007-08-27
If You use a good multimedia software, and I haven't written about it, PLEASE post Its name and a short description!

---

### Post by Dark Star on 2007-08-27
Thanks or this wonderful guide :)

---

### Post by eldragon on 2007-08-27
i was in the search of an adobe premiereish type of editor...

i actually use kino for video processiong, and dvd authoring (nothing fancy). but right now i need to do some multitrack editing..

so cinelerra is too bugy? i was hoping it would work.

how about main actor? how does its linux version stands? i know its not free :(

---

### Post by Amazona aestiva on 2007-08-27
I have used Cinelerra a little. You should try it.

---

### Post by Mahyar on 2007-08-28
I convert .avi files to DVD-compliant .mpg files with Tovid, and then create DVDs with DVD Styler.  The GUI is easy and you can add nice background images and fonts, etc.  I then burn the .iso with k3b.

I never could get Devede, ManDVD or some of the others to work properly for some reason.

---

### Post by mariaclara on 2007-08-28
thanks for Kino.

---

### Post by ashishgoel on 2007-08-29
thanx alot... 

awesome guide...

---

### Post by dabl on 2007-08-31
Great post -- thanks for laying all that out!

Using Avidemux and Kdenlive, I've got to the point where I can take my edited .mpg file, put a title on it, make an ISO and burn a DVD that will auto-start in any Windows or Linux computer.  But, on a standard DVD player, it just sits and "searching for menu".  Guess I need a menu, huh?  Or I'm still missing a step in the final process?  :confused:

---

### Post by Amazona aestiva on 2007-08-31
Everything (Windows,Linux,DVD Player) plays my DVDs. I've not created menu for DVD.
I use DeVeDe 3.01.

---

### Post by patambrosio on 2007-08-31
For the gnome user, [Diva: Video editing for the Gnome desktop]("http://www.diva-project.org/").

---

### Post by dabl on 2007-08-31
> **Amazona aestiva said:**
> 

I use DeVeDe 3.01.



Thanks -- I will try it that way.  Any special tricks needed?

---

### Post by Amazona aestiva on 2007-08-31
> Thanks -- I will try it that way. Any special tricks needed?
Under Feisty, YES!
Find DeVeDe in the first page. I wrote the fix down.

---

### Post by dabl on 2007-08-31
Aha -- the mencoder downgrade thing.  OK, got it -- thank you very much!  :)

---

### Post by Amazona aestiva on 2007-09-01
That's it! Good luck!

---

### Post by cotcot on 2007-09-03
After learning cinelerra carefully with the cinelerra manual it became my favorite editor. The level of possibilities is clearly higher than the others I have checked (pitivi, lives, kino, kdenlive). My advise is to judge cinelerra only if you have spent enough time in undertsanding it. 
I agree with the author that capturing and rendering is less easy as with the others. I keep cinelerra as default and kdenlive as fall back.

---

### Post by Amazona aestiva on 2007-09-05
So in Cinelerra I have to configure something before render. To .avi for example?
And what should I do? Where is the manual that You have read?

I'm interested with Cinelerra. Please post a few answer cotcot.

---

### Post by eldragon on 2007-09-05
> **Amazona aestiva said:**
> I have used Cinelerra a little. You should try it.

im using cinelerra in the end.....great piece of software.

although its a bit buggy and from time to time it segdumps, or just disappears.....its got a great backup utility.......hard to lose your work with it....

im definately recommending it

---

### Post by wersdaluv on 2007-09-08
> **Amazona aestiva said:**
> If Audacity says this when you try to capture: 

Error while opening sound device. Please check the input device settings and the project sample rate.

-You should close other opened recorders like gtk-recordMyDesktop.
-Try to choose other devices (Audio I/O).(I uses "ALSA: Ensoniq AudioPCI: ES1371 DAC2/ADC (hw:0,0)" for recording, and "ALSA: Ensoniq AudioPCI: ES1371 DAC1 (hw:0,1)" for playing)
-48000Hz usually good for sample rate

[/COLOR]

I got the > Error while opening sound device. Please check the input device settings and the project sample rate. error message. 

I set ALSA VIA 8235: VIA 8235 (hw:0,0) as my recording device and ALSA VIA 8235: VIA 8235 (hw:0,1) as my playback device and 48000Hz  as my default sample rate. That way, I did not get the error message but the sound still was not recorded.

My mic is working because I can hear my voice coming out of my speaker whenever I speak on the mic but audacity does not record the audio.

What do i do to record voice?

:guitar:

---

### Post by Amazona aestiva on 2007-09-08
> **wersdaluv said:**
> 
I set ALSA VIA 8235: VIA 8235 (hw:0,0) as my recording device and ALSA VIA 8235: VIA 8235 (hw:0,1) as my playback device and 48000Hz  as my default sample rate. That way, I did not get the error message but the sound still was not recorded.

My mic is working because I can hear my voice coming out of my speaker whenever I speak on the mic but audacity does not record the audio.

What do i do to record voice?

:guitar:

Yes I know the problem...
Quite difficult to explain...
Wait please...

---

### Post by Amazona aestiva on 2007-09-08
Unfortunately I haven't got a mic.:(
So don't know the exact answer.

BUT see this:

Now see the attached snapshot!

So You need a "Mix" enabled in Volume Control. (to add it edit->properties)
Switch the device to MIX and check the sample rate!

[COLOR="DarkOrange"]
**ANSWER:**[/COLOR]
1.Try my options!;)(this should work)
or
2.Open Volume Control and add Mic and Mic record and... so try these things.

Could I help You?

---

### Post by southernman on 2007-09-08
From the peanut galleries - video encoding section:

I've tried a few of the gui apps, avidemux and a few others I forget, but none of them allow the control (or so I've found) that you get by using mencoder / mplayer. Ok, it's a command line thing, but it works flawlessly if you spend a good amount of time reading the docs. The docs for mplayer and mencoder can be found [here]("http://www.mplayerhq.hu/DOCS/"), just pick your language and prepare to read for a while ;)

Using these two tools you can very effectively turn a 4+GB movie into a 700+/-MB file that will fit on a cd... with very little loss in quality. The key here is to spend some time encoding small samples until you get the command tweaked for best quality. Once you have your tweaks dialed in, create an bash script and run it before going to bed.

[This Howto]("http://ubuntuforums.org/showthread.php?t=273635&highlight=mencoder+usage") gives a pretty good although brief tutuorial on doing this.

CLI rules! :p

---

### Post by Amazona aestiva on 2007-09-08
> **southernman said:**
> From the peanut galleries - video encoding section:

I've tried a few of the gui apps, avidemux and a few others I forget, but none of them allow the control (or so I've found) that you get by using mencoder / mplayer. Ok, it's a command line thing, but it works flawlessly if you spend a good amount of time reading the docs. The docs for mplayer and mencoder can be found [here]("http://www.mplayerhq.hu/DOCS/"), just pick your language and prepare to read for a while ;)

Using these two tools you can very effectively turn a 4+GB movie into a 700+/-MB file that will fit on a cd... with very little loss in quality. The key here is to spend some time encoding small samples until you get the command tweaked for best quality. Once you have your tweaks dialed in, create an bash script and run it before going to bed.

[This Howto]("http://ubuntuforums.org/showthread.php?t=273635&highlight=mencoder+usage") gives a pretty good although brief tutuorial on doing this.

CLI rules! :p

Now It can be true that the gui apps don't give You everything that these encoders (mencoder, x264 etc.) can do. Guies need to be more complex, advanced, customizable etc.
However the easy-to-use and guied apps are liked by more people than the Command line.

---

### Post by southernman on 2007-09-09
Well, I am far from a command line pro but in the short time I've been using ONLY linux I've found that the command line tools are often more powerful and better. Is it daunting for a brand new user to use these? perhaps. Is it hard to figure out? perhaps. Should a new user learn to use the command line? It isn't required, but she'll be better off for it.

As for your arugment that GUI apps need to be more complex, advanced, customizable... heck why not learn the CLI way, if your aim is to make the GUI more complex.

---

### Post by Amazona aestiva on 2007-09-09
I agree. Perhaps need to learn more commands. But I'm learning programming, so I'll try to write well featured GUI apps one day.

However till it I agree again. Terminal is a GREAT power!

---

### Post by maruchan on 2007-09-19
Kdenlive Tuxfamily deb link is dead :-(

This one seems to work: [http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/kdenlive_0.5+svn20070909~3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/kdenlive_0.5+svn20070909~3v1ubuntu0_i386.deb)

---

### Post by Amazona aestiva on 2007-09-19
> **maruchan said:**
> Kdenlive Tuxfamily deb link is dead :-(

This one seems to work: [http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/kdenlive_0.5+svn20070909~3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/feisty/3v1n0/kdenlive_0.5+svn20070909~3v1ubuntu0_i386.deb)

Thanks I haven't noticed it.

---

### Post by beyond2moro on 2007-09-21
I am not sure if you can help me, but this is something that I have been trying to work out for about a year and a half now. Very frustrating.

Kino recognises my dv camera, the AV controls can control the camera, (I can watch the picture playing, FF RW, etc. on the camera's screen, but not in Kino itself) but when I try to capture it always tells me "capture failed".

Nobody has ever been able to give me any advice so far. Any ideas?

---

### Post by Amazona aestiva on 2007-09-21
> **beyond2moro said:**
> I am not sure if you can help me, but this is something that I have been trying to work out for about a year and a half now. Very frustrating.

Kino recognises my dv camera, the AV controls can control the camera, (I can watch the picture playing, FF RW, etc. on the camera's screen, but not in Kino itself) but when I try to capture it always tells me "capture failed".

Nobody has ever been able to give me any advice so far. Any ideas?

I don't really know what should you do...

It MIGHT can be because:
-There is broken or corrupt or incompatible library in your system
-Kino doesn't like your Firewire device
-Firewire device configured or recognized bad
-etc...

You need an expert...

You might reinstall Ubuntu if you haven't tried it...

Sorry, above my experience.

However could you post here what terminal says? (start Kino from terminal and post it if there is something when says capture failed)

[COLOR="Red"]An important thing:[/COLOR]
You should try Kdenlive. It records from Firewire too.
And if it works We'll know that it is Kino's issue.
Or if it doesn't work We'll know that Your hardware or something else is the problem.

---

### Post by questpro on 2007-09-22
First of all, Thanks very much for the author for the nice how-to. I am a total noobie in ripping kinda things. I am trying to install the packages listed. 

I am using AMD64-bit. I tried to install devede player from the website listed in the HOW-TO.  It has many dependencies shown in the terminal.

Following is my terminal output: 

```

:~/Desktop$ sudo dpkg -i devede_3.2-1~getdeb1_all.deb 
Selecting previously deselected package devede.
(Reading database ... 135618 files and directories currently installed.)
Unpacking devede (from devede_3.2-1~getdeb1_all.deb) ...
dpkg: dependency problems prevent configuration of devede:
 devede depends on python-glade-1.2; however:
  Package python-glade-1.2 is not installed.
 devede depends on dvdauthor; however:
  Package dvdauthor is not installed.
 devede depends on vcdimager; however:
  Package vcdimager is not installed.
dpkg: error processing devede (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 devede


```


After this I tried to install the given dependencies. And again I got some more dependecies listed.

```


:~/Desktop$ sudo apt-get install python-glade-1.2 dvdauthor vcdimager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-glade-1.2: Depends: python-gtk-1.2 (= 0.6.12-8) but it is not going to be installed
                    Depends: libglade0 but it is not going to be installed
                    Depends: libxml1 (>= 1:1.8.14-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

Shall I install the dependencies again. Or shall I use 'apt-get -f install' . Is this command ignores the dependecies? then I might get problems. right?

Do you recommend any otherway to install devede . Please help. Thanks in advance.
(And sorry for my english. I am not a native speaker)

---

### Post by Amazona aestiva on 2007-09-22
Hmmm...
Type:
```
sudo apt-get update
```

Now try again to install DeVeDe or the dependencies.

What can You see now?

---

### Post by questpro on 2007-09-22
I posted that output in the earlier one. any ways, I apt-get updated as u said. And did

sudo apt-get install python-glade-1.2 dvdauthor vcdimager


```


:~/Desktop$ sudo apt-get install python-glade-1.2 dvdauthor vcdimager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-glade-1.2: Depends: python-gtk-1.2 (= 0.6.12-8) but it is not going to be installed
                    Depends: libglade0 but it is not going to be installed
                    Depends: libxml1 (>= 1:1.8.14-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```

EDIT: Ok ok Wait a sec I will do install it entirely

---

### Post by questpro on 2007-09-22
I got the same output. No change after updating the packages. Any other suggestion??!!

---

### Post by questpro on 2007-09-22
I got it working now. So posting this for future reference.

I did this:

```

sudo apt-get install -f

```

It installed all the dependencies required. 

Thanks

---

### Post by Amazona aestiva on 2007-09-22
> **questpro said:**
> I got it working now. So posting this for future reference.

I did this:

```

sudo apt-get install -f

```

It installed all the dependencies required. 

Thanks

I've found it out a minute ago... You was faster...
Good luck!:)

---

### Post by questpro on 2007-09-22
I tested devede player just now. I used preview of 60 sec to make a vcd of a movie. It went smoothly. No problem with that. :)

But I tried with the terminal, I got this 

```

:~/Desktop$ devede
Psyco not installed, the program will just run slower
DeVeDe 3.2
/home/don/
/home/don/
Temp Directory is:  /var/tmp
home load:  /home/don/.devede
linea:  video_format:pal

linea:  temp_folder:/var/tmp/

linea:  menu_format:pal
linea:  
Traceback (most recent call last):
  File "/usr/bin/devede", line 2640, in <module>
    gtk.main()
KeyboardInterrupt



```
Of course the program is running well, I interrupted using keyboard. As shown in the above code.

Any idea about how to install 'Psyco'??

I checked the Synaptic Package Manager and I found a package called "dpsyco".  Any suggestions??

---

### Post by Amazona aestiva on 2007-09-22
I know nothing about Psyco or dpsyco. Sorry.

VCD's resolution is low that's why it went smoothly.

---

### Post by questpro on 2007-09-22
Ok.  Thanks anyway.

Thats really a great effort.

---

### Post by koer on 2007-09-22
Help!   i have tried to import video i recorded from beryl vidcap and transformed it with mancoder, to Kino video editor, but it says that it couldnt do so :

```
"/media/JAIME/BerylVideo.avi" is not a DV file. Do you want to import it?
ok
i do it as PAL or NTSC
and then shows:

Failed to load media file "/media/JAIME/BerylVideo.avi.dv"


```

please help ?

---

### Post by Amazona aestiva on 2007-09-22
> **koer said:**
> Help!   i have tried to import video i recorded from beryl vidcap and transformed it with mancoder, to Kino video editor, but it says that it couldnt do so :

```
"/media/JAIME/BerylVideo.avi" is not a DV file. Do you want to import it?
ok
i do it as PAL or NTSC
and then shows:

Failed to load media file "/media/JAIME/BerylVideo.avi.dv"


```

please help ?

However it should work, and I don't know what do you want to do, but I suggest to edit videos with other than kino. Kino is for record and, so that's all. For editing use Avidemux, Kdenlive. (perhaps Cinelerra)

Sorry... I really don't know the problem.
Perhaps check the dependencies:
```
sudo apt-get install --reinstall liboggflac3 libsamplerate0 vorbis-tools
```

---

### Post by koer on 2007-09-23
i installed kdenlive , i allredy tried cincelerra and its no good , i followed the instruccions for kdenlive step by step and when i tried to run it this is what it showed :
```
There was an error setting up inter-process comunications for KDE. the message returned by the system was:
could not open network socket
plese check that "dcopserver"program is running!

```

and then

```
Will not save configuration.
Configuration file "/home/jaime/.kde/share/config/kdenliverc" not writable.
Configuration file "/home/jaime/.kde/share/config/kdeglobals" not writable.
Please contact your system administrator.
```

and then

```
Could not find mime type
application/octet-stream
```

and then.....

```
No mime types installed.
```

and then 

```
Malformed URL
file:///home/jaime
```

:confused:   what do i do ????!!!
 im running Ubuntu feisty 7.04 by the way 

hope someone can help me 
its my last video editing resource !!!

---

### Post by Amazona aestiva on 2007-09-24
First try to start dcopserver before start Kdenlive:
```
dcopserver
```
```
kdenlive
```

Is It already running?

---

### Post by koer on 2007-09-24
this is what i get:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
Error: Can not create link from "/home/jaime/.kde/cache-UBUNTU" to "/var/tmp/kdecache-jaime"
Error: Can not create link from "/home/jaime/.kde/cache-UBUNTU" to "/var/tmp/kdecache-jaimeJREJ3X"
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
Error: Can not create link from "/home/jaime/.kde/socket-UBUNTU" to "/tmp/ksocket-jaime"
Error: Can not create link from "/home/jaime/.kde/socket-UBUNTU" to "/tmp/ksocket-jaimer2ef4a"
trying to create local folder /home/jaime/.kde/socket-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/socket-UBUNTU: Permission denied
kdeinit: Aborting. bind() failed: : No such file or directory
Could not bind to socket '/home/jaime/.kde/socket-UBUNTU/kdeinit__0'
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/share/config: Permission denied
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
trying to create local folder /home/jaime/.kde/cache-UBUNTU: Permission denied
jaime@UBUNTU:~$ 


```

:confused:

---

### Post by koer on 2007-09-24
ahahahah!! it worked , i just took a look at the errors and ran kdenlive as root


thank you for all the help !!!!!

:guitar:

---

### Post by Amazona aestiva on 2007-09-24
> **koer said:**
> ahahahah!! it worked , i just took a look at the errors and ran kdenlive as root


thank you for all the help !!!!!

:guitar:

Hooray!:)

---

### Post by koer on 2007-09-25
just another tiny thing , i made my video , put in some nice mp3 song and when i try to render the whole video , the music cuts and skips and goes way fast ..... any setting i might need to change for this to be fixed?

---

### Post by Amazona aestiva on 2007-09-26
> **koer said:**
> just another tiny thing , i made my video , put in some nice mp3 song and when i try to render the whole video , the music cuts and skips and goes way fast ..... any setting i might need to change for this to be fixed?

Make a new thread for this...

I don't know. I've not used Kdenlive really much.

---

### Post by wrongo on 2007-09-27
Dvd95 purports to compress DVD-DL to DVD, but in actuality just converts one title at a time.

EXAMPLE

Using todisc, I create a double-layer DVD with the following features:

     *7.9 Gb VIDEO_TS or .iso file size
     *9 hours, 56 minutes, and 23 seconds RUNNING TIME
     *Main menu with the first 20 seconds of each title being displayed

I open Dvd95, open my DVD-Drive, and all the titles come up in the "Video" panel, along with the single Audio track. There are no subtitles.

I click "Evaluer" (Evaluate) and get the following error message:

     "PLEASE SELECT A VIDEO TRACK"

Here is the problem: Dvd95 now restricts me to working with a single track at a time. I cannot select them all and "evaluate" the whole disc.

Dvd95 would be a great program if it only had a "select all" option.

[email]jerit@handdrawnstars.net[/email]

---

### Post by _newbie on 2007-10-03
Hi!

I managed to import video from my cam via Kino into DV format. The big question is how should I export from Kino if I want to achieve DivX like compression with high picture quality. 

Please do not just name the programs but share the exact settings to be used!

Thanks

---

### Post by futare on 2007-10-03
thx for this great guide!

---

### Post by Amazona aestiva on 2007-10-03
> **_newbie said:**
> Hi!

I managed to import video from my cam via Kino into DV format. The big question is how should I export from Kino if I want to achieve DivX like compression with high picture quality. 

Please do not just name the programs but share the exact settings to be used!

Thanks



Hmmm... [COLOR="Red"]Don't export from Kino, it's waste of time![/COLOR]

Open and compress the DV file with Avidemux. You should use DV AVI type 2 and OpenDML AVI capture options in Kino, because of the compatibility with Avidemux.

It uses a REALLY nice XviD codec (my favorite), which makes good quality in a small file. Avidemux also has filters, that can be quite useful.

**[SIZE="3"][COLOR="SeaGreen"]A good configuration:[/COLOR][/SIZE]**
Now it isn't so simple.

I advise to find it out by Yourself, because who wants to save a video to DVD "forever", needs a lot of own experience. I've been recording from VHS for 3 years, and I always find a better way. So I've restarted capturing 4 times, and my family has got about 200 VHS!

**[COLOR="DarkRed"]However a few tips:[/COLOR]**

**[COLOR="RoyalBlue"]Video compression:[/COLOR]**
Use MPEG-4 ASP (Xvid4) in Avidemux (MPEG-4 ASP usually means a very good codec)
I uses "Single pass bitrate", but you might try the others too.
Bitrate in Kb/s:
4500 and above is usually more than you need
3500-4500 really high quality
2500-3500 high quality
1800-2500 med-high quality
1200-1800 low-med quality
1200 and less is lower quality
You have to know that this is a variable birate, so it can be 300Mb or 600Mb with a same options. It depends on the video's quality and compression ability.
I uses 3500Kb/s and it's usually about 450-600Mb.
Quantization:
H.263 is for lower bitrates and MPEG for higher. I advise H.263.
[B]
[COLOR="RoyalBlue"]Audio compression:[/COLOR][/B]
I advise MP3 (lame), because it is heavily supported by everything.
Channel mode should be Stereo I think.
CBR or ABR is your choose: I can't find big difference between them.
Quality 0=best(use this), 9=awful
Bitrate: I use 224. However it is usually needn't to be high so much. I advise (I've not tried 128 yet) 160-244.


At the end of this I advise to try many options with a short film (1-2min), and check what are the results of different options.

[COLOR="RoyalBlue"]Have a good time![/COLOR];)

---

### Post by _newbie on 2007-10-04
> **Amazona aestiva said:**
> Hmmm... [COLOR="Red"]Don't export from Kino, it's waste of time![/COLOR] ....... (1-2min), and check what are the results of different options.

=D>

Thanks very much for giving me a hand!! Truly appreciated.

---

### Post by kung fu buntu on 2007-10-06
ahhh... I must be missing something really obvious, but **essential-amd64-20061203** only has 4 *.so files, there are no .dlls.
I still put those files in /usr/lib/win32 but kaffeine says it will not play win32 files

Any ideas?
Thanks

---

### Post by Amazona aestiva on 2007-10-06
> **kung fu buntu said:**
> ahhh... I must be missing something really obvious, but **essential-amd64-20061203** only has 4 *.so files, there are no .dlls.
I still put those files in /usr/lib/win32 but kaffeine says it will not play win32 files

Any ideas?
Thanks

Link modified... Try again.[COLOR="Red"] AND please send a feedback to me(here) if it is or isn't working!!!![/COLOR]

Kaffeine's dependency check won't run again until You remove this file:
> /home/USERNAME/.kde/share/apps/kaffeine/wizard_stamp_v0.7.1

---

### Post by kung fu buntu on 2007-10-06
Thanks! That one is solved.

Although I have another error (already had it):
"Can't check DMA mode. Permission denied or no such device: "/dev/dvd""

I have /dev/dvd1 and I tried creating a link to /dev/dvd but it didn't help.

Any ideas?

---

### Post by Amazona aestiva on 2007-10-06
> **kung fu buntu said:**
> Thanks! That one is solved.

Although I have another error (already had it):
"Can't check DMA mode. Permission denied or no such device: "/dev/dvd""

I have /dev/dvd1 and I tried creating a link to /dev/dvd but it didn't help.

Any ideas?

[COLOR="Silver"]Ahmmm...
Can I get you fstab?[/COLOR]

[COLOR="Red"]**I'm typing the solution check it 10 mins later.**[/COLOR];)

---

### Post by Amazona aestiva on 2007-10-06
> **kung fu buntu said:**
> Thanks! That one is solved.

Although I have another error (already had it):
"Can't check DMA mode. Permission denied or no such device: "/dev/dvd""

I have /dev/dvd1 and I tried creating a link to /dev/dvd but it didn't help.

Any ideas?

Start Kaffeine and

Settings -> Xine Engine Parameters

and go to Media, and change the "dvd.device"'s parameter
to "/dev/dvd1"

If it isn't working post Your /etc/fstab file.

---

### Post by kung fu buntu on 2007-10-06
It works! I don't why, but it works.

cat /etc/fstab
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

l /dev/dvd1
lrwxrwxrwx 1 root root 4 2007-10-06 15:53 /dev/dvd1 -> scd0

l /dev/scd0
brw-rw---- 1 root cdrom 11, 0 2007-10-06 15:53 /dev/scd0


So fstab says the device is named /dev/hda but the device tree (and kaffeine) say it is /dev/dvd1... :-k

---

### Post by Amazona aestiva on 2007-10-06
> **kung fu buntu said:**
> It works! I don't why, but it works.

cat /etc/fstab
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

l /dev/dvd1
lrwxrwxrwx 1 root root 4 2007-10-06 15:53 /dev/dvd1 -> scd0

l /dev/scd0
brw-rw---- 1 root cdrom 11, 0 2007-10-06 15:53 /dev/scd0


So fstab says the device is named /dev/hda but the device tree (and kaffeine) say it is /dev/dvd1... :-k

Till it works I usually don't have questions.;)

I'm glad that I could help You!:)

---

### Post by Hhkmac on 2007-10-13
Awesome How To post... cheers for taking the time to do it!!

---

### Post by Amazona aestiva on 2007-10-14
Today I've rewritten the how-to and I have inserted new links of manuals. (I call these "Guide")

---

### Post by Speedoo on 2007-10-14
I don't do much with video files, but I have a need to burn files collected (via WinXP) from Tivo To Go.  Apparently these mpeg files won't translate directly to DVD, but need to be output as .vob files, then renamed to .mpg and burned.  Has anyone had success doing this in Ubuntu Feisty (AMD64)?  What program would you recommend.  Getting ready to experiment with Avidemux and DeVeDe, but I was hoping someone could eliminate the trial-and-error aspects.
Thanks!

Speedoo

---

### Post by Amazona aestiva on 2007-10-14
> **Speedoo said:**
> ...Apparently these mpeg files won't translate directly to DVD, but need to be output as .vob files, then renamed to .mpg and burned....
Speedoo

Why do you need .vob first? Why don't you convert simply to .mpg?

---

### Post by Speedoo on 2007-10-14
Not sure.  I managed to burn programs to disc using Windoze, following step by step directions found on a Tivo community forum.  It instructed me to use DVDStyler to create menus, then Video ReDo to convert from .mpg to .vob, then rename the .vob file to .mpg, then create .iso output to burn to a DVD.   Is there a linux program that will convert a .tivo file to an .mpeg ? (My trial version of Video ReDo expired, and I'm trying to avoid buying it if there's an open source program that will do the same thing.)
As I said, don't work much with video files....

---

### Post by hagiviz on 2007-10-14
boss... salamat sa post nyo... so informative... tamang taman sa mga baguhan... at sa mga pro narin... thanks alot boss......

---

### Post by skipbarker on 2007-10-15
> **Speedoo said:**
> Not sure.  I managed to burn programs to disc using Windoze, following step by step directions found on a Tivo community forum.  It instructed me to use DVDStyler to create menus, then Video ReDo to convert from .mpg to .vob, then rename the .vob file to .mpg, then create .iso output to burn to a DVD.   Is there a linux program that will convert a .tivo file to an .mpeg ? (My trial version of Video ReDo expired, and I'm trying to avoid buying it if there's an open source program that will do the same thing.)
As I said, don't work much with video files....
Check out [tivodecode]("http://tivodecode.sourceforge.net/"). It does not have a gui but does a great job of going .tivo to mpeg.

---

### Post by Speedoo on 2007-10-16
Thanks.  That's just what I've been looking for.  Unfortunately, being a noob, I doubt I'll get it to work from the command line.  But I'll give it a shot.

---

### Post by Vicfred on 2007-10-19
is avisynth available on ubuntu?

---

### Post by Amazona aestiva on 2007-10-19
> **Vicfred said:**
> is avisynth available on ubuntu?

No, it isn't. You must compile it from [source]("http://avisynth3.unite-video.com/avisynth-3.0.tar.gz").

Maybe I'll try it, and write it down.

---

### Post by cyneuron on 2007-10-23
such an awesome post.....keep up the good work....should bemade a sticky

---

### Post by Amazona aestiva on 2007-10-24
> **cyneuron said:**
> such an awesome post.....keep up the good work....should bemade a sticky

Wow! Thanks!
I love helping other people!

---

### Post by rod40cool on 2007-11-06
Excellent post.
I've tried Kino for mini DV capture under Gutsy and this seems to work fine but does anyone know why KDEnlive can't capture DV from firewire. I get this message - see attached screen shot.

---

### Post by Amazona aestiva on 2007-11-07
> **rod40cool said:**
> Excellent post.
I've tried Kino for mini DV capture under Gutsy and this seems to work fine but does anyone know why KDEnlive can't capture DV from firewire. I get this message - see attached screen shot.

Do you use 1.8?
If yes then:
For Gutsy [this]("http://ftp.no.debian.org/debian/pool/main/d/dvgrab/dvgrab_3.0-1_i386.deb")(3.0) might be better.

Does it work?

---

### Post by rod40cool on 2007-11-08
> **Amazona aestiva said:**
> Do you use 1.8?
If yes then:
For Gutsy [this]("http://ftp.no.debian.org/debian/pool/main/d/dvgrab/dvgrab_3.0-1_i386.deb")(3.0) might be better.

Does it work?

Unfortunately the package installer for your link to  dvgrab_3.0 says "Same version is already installed" and would I like to re-install? So I guess the answer is no it doesn't work. 

What now? 

Whilst I can use Kino for DV capture over firewire but I would like to be able to do everything in the one program plus when I upgrade my current old pc which has firewire onboard, newer pc's don't have this unless you buy a firewire card and USB capture seems to be the way to go. (I know other Ubuntu users would like to know about capture over USB and Kino wont do this.) I tried USB capture in Kdenlive too but it failed as well with the same message. It's like KDEnlive is compiled and packaged for a different version of dvgrab. The ver of Kdenlive I have is 0.5. The ver of dvgrab I have is 3.0.
```
rod@rod-desktop:~$ dvgrab -v
dvgrab 3.0
rod@rod-desktop:~$
```

---

### Post by Amazona aestiva on 2007-11-09
> **rod40cool said:**
> Unfortunately the package installer for your link to  dvgrab_3.0 says "Same version is already installed" and would I like to re-install? So I guess the answer is no it doesn't work. 

What now? 

Whilst I can use Kino for DV capture over firewire but I would like to be able to do everything in the one program plus when I upgrade my current old pc which has firewire onboard, newer pc's don't have this unless you buy a firewire card and USB capture seems to be the way to go. (I know other Ubuntu users would like to know about capture over USB and Kino wont do this.) I tried USB capture in Kdenlive too but it failed as well with the same message. It's like KDEnlive is compiled and packaged for a different version of dvgrab. The ver of Kdenlive I have is 0.5. The ver of dvgrab I have is 3.0.
```
rod@rod-desktop:~$ dvgrab -v
dvgrab 3.0
rod@rod-desktop:~$
```

I still use Feisty which has DVGrab1.8 only.(3.0 requests newer libc)

I don't know Gutsy's repo but Kdenlive works for me with 1.8. You might try this older version. If you don't find for Gutsy try Feisty's package, it should work.

[Here is a DVGrab 1.8 link.]("http://ftp.kfki.hu/linux/ubuntu/pool/universe/d/dvgrab/dvgrab_1.8-4_i386.deb") (I use this)

---

### Post by rod40cool on 2007-11-09
> **Amazona aestiva said:**
> I still use Feisty which has DVGrab1.8 only.(3.0 requests newer libc)

I don't know Gutsy's repo but Kdenlive works for me with 1.8. You might try this older version. If you don't find for Gutsy try Feisty's package, it should work.

[Here is a DVGrab 1.8 link.]("http://ftp.kfki.hu/linux/ubuntu/pool/universe/d/dvgrab/dvgrab_1.8-4_i386.deb") (I use this)

Ok thankyou. I will check out ver 1.8 and see if that works.
Thanks for your help.

---

### Post by NJC on 2007-11-15
> **Amazona aestiva said:**
> 

So You need a "Mix" enabled in Volume Control. (to add it edit->properties)
Switch the device to MIX and check the sample rate!

[COLOR="DarkOrange"]
**ANSWER:**[/COLOR]
1.Try my options!;)(this should work)
or
2.Open Volume Control and add Mic and Mic record and... so try these things.



Nice! THANKS for the help. Recently installed Ubuntu 7.10 and could only get very minimal sound. =D>

---

### Post by TheTank on 2007-11-21
My thanks to Amazona aestiva for this great guide.
Again Ubuntu and the great people supporting it like you show how great and ease of use it can be.

The apt-get lib line complained a lot about packages that it could not find.
But otherwise it worked friggin great!
Installed Kino, added the chown line and recorded my stuff.
One note: I ran out of hd space and Kino just hung.
Avidemux also worked great.

---

### Post by Amazona aestiva on 2007-11-21
You're welcome!
The first apt-get might be wrong under Gutsy because I still use Feisty.

---

### Post by Amazona aestiva on 2007-12-20
> **TheTank said:**
> My thanks to Amazona aestiva for this great guide.
Again Ubuntu and the great people supporting it like you show how great and ease of use it can be.

The apt-get lib line complained a lot about packages that it could not find.
But otherwise it worked friggin great!
Installed Kino, added the chown line and recorded my stuff.
One note: I ran out of hd space and Kino just hung.
Avidemux also worked great.

I repaired the apt-get.

---

### Post by michaelzap on 2008-01-06
Since this seems like an active thread and my questions are related to the topic I'll ask them here...

I'm trying to work out a simple process for ripping DVDs to high-quality xvid files with separate subtitle files. I have a fairly large collection that I would like to convert, and I'd like to standardize the process. I'd also like to end up with files that I can play on my current DVD player, which will play xvid files burned onto a rewritable CD (so ideally I'd like the files to be under 700MB each, although I can split them if necessary).

Anyway, I thought that AcidRip would be the best way to rip right from the DVD to xvid, but I'm not getting very good quality even at very high bit rates (over 1000) with very large files (1.2GB for a 90-minute movie) using two passes. Avidemux seems to do a much better job at making smaller and better-looking xvids, but I need to rip and combine the VOB files first in order to use that (which takes longer). Anyone have a recommendation as to how I can get better-quality files without this extra step?

I'm also looking for a way to convert idx/sub files into srt text subtitle files on Ubuntu, and so far I haven't found any native software to do this.

Thanks in advance for your replies and suggestions.

---

### Post by Amazona aestiva on 2008-01-07
You should see** DVD::rip**. It's much more advanced than Acidrip.
The only thing I haven't done so far is ripping8-[, but **DVD::rip** looks cool definitely. Try it!

Perhaps someone will send more useful information than me.:)

Good luck!

---

### Post by cotcot on 2008-02-16
I is a pity that kdenlive is not listed in the poll.

---

