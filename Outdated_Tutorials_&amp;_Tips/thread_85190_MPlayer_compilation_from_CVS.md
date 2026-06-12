---
title: "MPlayer compilation from CVS"
date: 2005-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by bored2k on 2005-11-02
[CENTER][size=1]This is yet another extension of the original [MPlayer PRE]("http://www.ubuntuforums.org/showthread.php?t=78037") compilation guide. I'm separating the CVS compilation method because it's getting buried in all of the pages of the first thread. Props to everyone on the first thread (specially seethru and emendelson).[/size][/CENTER]


**[CENTER]Fasten your seatbelts..**

You **need** a proper *sources.list* file. Here is mine:
[center]```

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```[/center]
```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot gnome-core-devel libpostproc-dev
```

If you have **never** used **cvs** before, do the following command:
```
touch $HOME/.cvspass
```
[/CENTER] 

**Downloading MPlayer CVS**
> 
Issue the following commands to get the latest sources:
```

  cvs -d:pserver:anonymous@mplayerhq.hu:/cvsroot/mplayer login
  cvs -z3 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/mplayer co -P main
```

When asked for a password, just hit enter. A directory named main will be created. You can later update your sources by saying

```
  cvs -z3 update -dPA
```

from within that directory. 

[B]FFmpeg libavcodec/libavutil/libavformat
[/B]
> 
CVS MPlayer is not fully functional without a copy of the libavcodec, libavformat and libavutil libraries from FFmpeg. Get FFmpeg CVS via
```

  cvs -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg login
  cvs -z3 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co -P ffmpeg
```

When asked for a password, just hit enter. A directory named ffmpeg will be created. Copy the libavcodec, libavformat and libavutil subdirectories into the main directory just created from the MPlayer checkout.
```
cp ffmpeg/libav* main/ -rf
```

> In order to include libavcodec and libavutil in CVS updates, add the following lines to main/CVS/Entries:

  ```
gedit main/CVS/Entries
```
  ```

  D/libavcodec////
  D/libavformat////
  D/libavutil////
  
```



> Previously win32 codecs were placed in /usr/lib/win32. Applications like Xine use that directory for the same purpose. If you would like you can either keep both directories or make one linked to the other. If both directories exist you cannot link them.
```
sudo ln -s /usr/lib/win32 /usr/local/lib/codecs 
```This is optional.


**Compiling MPlayer**
> Most users will find the default configuration options adequate. However I recommend the following options. The first option is required to install the GUI. The second option is to allow access to large files over 2GB. Useful to rip DVD's or record Digital Video. The third option is for menus in the OSD (On Screen Display).
```
cd main
```
```
./configure --enable-gui --enable-largefiles --enable-menu --prefix=/usr --confdir=/etc/mplayer
```
If some errors pops up it is most likely due to a missing dependency (hey, I **tried** to include them all). Once it finishes, you should be able to see what you have enabled (ie what you compiled) and you do not. This step is great to see how your compile is piling up.
```
make
```
```
sudo make install
```


**Making your own MPlayer debian package (after it works)**
```
fakeroot debian/rules binary
```

**A summary how-to for getting this contribution to work the first time.**
> 

1. Install the deb package, but don't run the program.

2. Go to a terminal, and run

```
sudo mkdir /usr/local/share/mplayer
sudo mkdir /usr/share/mplayer/Skin

```

3. go to 

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

and download a skin (Blue is the official default); in a sudo terminal, extract the directory from the archive, and copy it to /usr/share/mplayer/Skin ; rename the extracted directory from "Blue" (or whatever) to "default" (cd to the Skindirectory and then try: sudo mv Blue default)

4. Assuming that you've downloaded the Microsoft core fonts (by installing **msttcorefonts**), do this:

```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf

```

NOW, start gmplayer. You can import more skins to ~/.mplayer/Skin in the same way as in step 3.

**Smooth playback**[QUOTE=dradul]
> 
The defaults of MPlayer's A-V sync parameters aren't fine-tuned for perfect files. When looking at timing in such detail, you should take care of video timers, too. Be sure that the hardware RTC timer is used (MPlayer will complain to the standard output if the RTC timer has a value lower than 1024, start mplayer from a terminal window and examine the error messages).

[quote]
First make sure the kernel rtc module is loaded in your kernel permanently:
```

sudo gedit /etc/modules

``` Add
```

rtc

``` at the end of the list. Now set up the rtc timer value at booting up time:
```

sudo gedit /etc/sysctl.conf

``` Add the following
```

dev.rtc.max-user-freq=1024

``` and save the file. For faster loading times, you will need to include the rtc module in your initrd image. Add it to your mkinitramfs configuration file:
```

sudo gedit /etc/mkinitramfs/modules

``` Add the following to the list:
```

rtc

``` and regenerate the initrd file of your running kernel:
```

sudo dpkg-reconfigure linux-image-$(uname -r)

``` In case you have several kernels installed, you will have to specify their version explicitly.

If you want instant gratification, you can set up the rtc values of the running kernel before stating mplayer like this:
```

sudo modprobe rtc
sudo sysctl -w dev.rtc.max-user-freq=1024

```  [/quote] 
**Updating your CVS MPlayer**
> Go to your MPlayer **main** directory and 
```
cvs -z3 **update** -dPA
``` and repeat the compiling steps.
[/QUOTE]

**Extras**
[LIST]
[*][Clearlooks skin.]("http://www.gnomelook.org/content/show.php?content=21745")
[*]Mozilla MPlayer [plugin 3.11]("http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb")
```
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```
[*]ASCII text video (colored):
```
mplayer *video.avi* -vo caca
```

[*]ASCII text video (non colored):
```
mplayer *video.avi* -vo aa
```

[/LIST]
 
[CENTER]**The finished product:**
[[IMG]http://img407.imageshack.us/img407/8325/gtk28eq.th.jpg[/IMG]](http://img407.imageshack.us/my.php?image=gtk28eq.jpg) [[IMG]http://img407.imageshack.us/img407/1313/screenshotpreferences4we.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotpreferences4we.png)  [[IMG]http://img407.imageshack.us/img407/6764/screenshotpreferences15qf.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotpreferences15qf.png)[/CENTER]

---

### Post by bored2k on 2005-11-02
Using this method, some of us have created **x86** compiled packages. Compiling it yourself is the best method, but for those who want a quick way out of this, here are some:
[LIST]
[*][November 1st (2005) build]("http://rapidshare.de/files/7068565/mplayer_1.0cvs_i386.deb.html")
[*][October 31st (2005) build]("http://rapidshare.de/files/7009051/mplayer_1.0cvs_i386.deb.html")
[/list]

[center]If someone compiles this using different architectures, please share the love :)[/center]

---

### Post by gnumerouno on 2005-11-12
Thanks alot, I was having trouble playing some h.264, especially in Matroska mkv files. I tried the Ubuntu packaged mplayer and compiled from source tar. This method seams to have fixed everything.

---

### Post by Technoviking on 2005-11-13
Here are Audio/Video driver configured in mine, also my deb files points to /usr and not /usr/local.
```

  **Enabled optional drivers:**
    Input: ftp network tv-v4l2 tv-v4l edl tv live555 matroska cdda mpdvdkit2 vcd dvb smb
    Codecs: qtx divx5linux xvid libdv libavcodec real dshow/dmo win32 faad2(internal) faac libmpeg2 libdts liba52 mp3lib libtheora tremor(internal) libmad liblzo gif
    Audio output: alsa jack polyp esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl gif89a md5sum pnm jpeg png mpegpes(dvb) fbdev svga caca aa ggi opengl dga xv x11 xover dfbmga directfb tga
    Audio filters: ladspa

  **Disabled optional drivers:**
    Input: vstream tv-bsdbt848 dvdread
    Codecs: divx4linux x264 amr_wb amr_nb xanim musepack speex twolame toolame
    Audio output: sgi sun dxr2 dsound win32
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx vesa xmga mga xvmc tdfx_vid tdfxfb 3dfx
    Audio filters:

```

---

### Post by Hellaxe on 2005-11-18
Sorry for the question but where i can download the libdivx5linux to compile?
I've googled and have no lucky.

Thanks

Edit: I've found that file sorry again

---

### Post by akurashy on 2005-11-18
Well I at last compiled mine. I uploaded the .deb if someone needed it. 

[November 18]("http://davidgonz.com/mplayer_1.0cvs_i386.deb")

Enjoy, and great How-To bored2k :)

---

### Post by Rob2687 on 2005-11-19
Heres one compiled on a PIII-M (SSE and MMX)
[http://rapidshare.de/files/7839413/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/7839413/mplayer_1.0cvs_i386.deb.html)

(I'm a noob and all I did was follow the posted guide. I've tested it and it seems to work fine. Don't blame me if this warps your PC to the next dimension :P )

---

### Post by Chrissss on 2005-11-19
Thanks for this guide. Only with this one i was able to compile mplayer with a gtk2 GUI successfully :D

---

### Post by Spider-One on 2005-11-21
For some reason gmplayer isn't being built when I compile, I can't see anything obvious in the configuration log. I've followed the HowTo to the letter, but no matter what I do gmplayer isn't being created. Any ideas on what I could be missing? In the configuration.log is say it yes on the gui check, so I'm baffled.

---

### Post by ollesbrorsa on 2005-11-22
Let me start by saying thanks for the great howto! Worked flawlessly up to the point where I try to set up the mplayer-plugin. 
I'm using ff 1.5rc3 after following another great howto on the forums. The problem is that the mplayer-plugin doesn't show up in about:plugins.

I'm guessing that the .deb installs the plugin to the ubuntu firefox default plugin directory and I should try to move it to the directory where I've installed ff 1.5, right?

Another noobish question is how can I see what actually happens when I install a .deb? What files gets placed where and the like?

Still learning over here! ;) 

Br,
ollesbrorsa

---

### Post by bored2k on 2005-11-22
[QUOTE=ollesbrorsa]The problem is that the mplayer-plugin doesn't show up in about:plugins.[/QUOTE]
It isn't supposed to do so. You just install the deb. Just go to /usr/lib/mozilla-firefox/plugins/ and copy everything.
[QUOTE=ollesbrorsa]
Another noobish question is how can I see what actually happens when I install a .deb? What files gets placed where and the like?[/QUOTE]That's not in the scope of this thread.

---

### Post by bored2k on 2005-11-22
[QUOTE=Spider-One]For some reason gmplayer isn't being built when I compile, I can't see anything obvious in the configuration log. I've followed the HowTo to the letter, but no matter what I do gmplayer isn't being created. Any ideas on what I could be missing? In the configuration.log is say it yes on the gui check, so I'm baffled.[/QUOTE]Did you configure mplayer with the parameters I said? Again, they are:
```
./configure **--enable-gui** --enable-largefiles --enable-menu
```If so, does mplayer from a terminal work? What happens when you type gmplayer ?

---

### Post by mintcoffee on 2005-11-27
Awesome HOWTO. MPlayer has never looked better! :smile:

---

### Post by Mastodront on 2005-11-28
Now I've tried all of the .deb-files built from cvs and all of them generates the same error when I try to run gmplayer:

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
[skin] file ( /usr/local/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

When I try to run it from Audio/Video in the Gnome menu I get the same complaint on the skin. I've checked and the skin seems to be where it should and everything :/

Anyone who knows what might be the trouble?

---

### Post by rune on 2005-11-28
[QUOTE=Mastodront]Now I've tried all of the .deb-files built from cvs and all of them generates the same error when I try to run gmplayer:

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
[skin] file ( /usr/local/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

When I try to run it from Audio/Video in the Gnome menu I get the same complaint on the skin. I've checked and the skin seems to be where it should and everything :/

Anyone who knows what might be the trouble?[/QUOTE]

Have you untarred your skin? I think that is neccesary. What does /usr/share/mplayer/Skin and ~/.mplayer/Skin and /usr/local/share/mplayer/Skin hold?

---

### Post by Mastodront on 2005-11-28
Hmm, I downloaded another skin from mplayerhq and removed the skin included in the debs and now it seems to work.
Thanks anyway :)

Sadly I still have the problem with some .avi-files playing the video way faster than the audio, didn't have that problem in hoary :/

---

### Post by bored2k on 2005-11-28
[QUOTE=Mastodront]Hmm, I downloaded another skin from mplayerhq and removed the skin included in the debs and now it seems to work.
Thanks anyway :)

Sadly I still have the problem with some .avi-files playing the video way faster than the audio, didn't have that problem in hoary :/[/QUOTE]
Did you dist-upgrade? Try reinstalling the w32codecs..

---

### Post by Mastodront on 2005-11-29
[QUOTE=bored2k]Did you dist-upgrade? Try reinstalling the w32codecs..[/QUOTE]


No I've made a clean install. I have the same problem in both of my computers but it's luckily only with a few files I have the problem. I've tried several builds of mplayer and both older and newer w32codecs. The result is always the same, the audio runs att normal speed but the video is like twice the speed. I've also tried to run the same files in VLC but it can only play the audio it seems. To be sure it wasn't the videofiles that had some weird kind of errors I tried to play them in WMP and there wasn't any sync problems :/

---

### Post by bored2k on 2005-11-29
[QUOTE=Mastodront]No I've made a clean install. I have the same problem in both of my computers but it's luckily only with a few files I have the problem. I've tried several builds of mplayer and both older and newer w32codecs. The result is always the same, the audio runs att normal speed but the video is like twice the speed. I've also tried to run the same files in VLC but it can only play the audio it seems. To be sure it wasn't the videofiles that had some weird kind of errors I tried to play them in WMP and there wasn't any sync problems :/[/QUOTE]
That's kinda weird. Do you have any idea how those avi files were encoded?

---

### Post by Mastodront on 2005-11-29
[QUOTE=bored2k]That's kinda weird. Do you have any idea how those avi files were encoded?[/QUOTE]

Nah sadly I don't know anything about video :/

When I checked one of the files properties I found this:

Video:
Dimensions: 320 X 240
Codec: Indeo Video 5 (win32)
Framerate: 25 frames per second
Bitrate: 0 kbps

Audio: 
Bitrate: 1411 kbps
Codec: Linear PCM

Don't know whether it's useful information or not though :/

---

### Post by garba on 2005-11-29
i wonder why the mplayer you get from the repos looks like crap when you can make it look this good with some tinkering...

---

### Post by kdavison007 on 2005-11-29
I agree.  Mplayer has never worked better for me.  One question though...

How do I connect back to CVS to do an update on this?

---

### Post by bored2k on 2005-11-30
[QUOTE=kdavison007]I agree.  Mplayer has never worked better for me.  One question though...

How do I connect back to CVS to do an update on this?[/QUOTE]
> Go to your MPlayer main directory and 

```
cvs -z3 update -dPA
```:)

---

### Post by bored2k on 2005-11-30
[LIST]
[*][November 30th, 2005 **x86** MPlayer CVS build]("http://rapidshare.de/files/8409074/mplayer_1.0cvs_i386.deb.html").
[*][Libtwolame]("http://rapidshare.de/files/8168617/libtwolame0_0.3.3-1_i386.deb.html") (requirement).
[/LIST]

---

### Post by breakthestate on 2005-12-06
[LEFT]I'm using 5.10 freshly installed on a new computer. I've successfully compiled MPlayer from source (1.0pre7) on 5.10 before without a gui. All I did was get the binary codecs from Mplayer and untar them into the /usr/local/lib/codecs directory. After compiling, everything worked perfectly.[/LEFT]
 
Now, I want to use MPlayer (still no gui) with JACK, and hence, I'm looking at the CVS option. Here is my question. The howto says to do the following: 
 
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot
[LEFT]
 
I don't remember apt-getting any of those libraries when I compiled before. Is it the case that all of the above libraries and codecs are only necessary for a gui? I know I'll need build-essential (and debhelper?). Shouldn't I be fine just using the "all" codec package from MPlayerhq.com with the CVS version (with the FFMpeg parts copied into the main directory) and a ./configure; make; make install, if I'm not concerned with a GUI or making a .deb?
 
Just trying to get it all right before I break everything and start over again!;) 
 
PS - I already have JACK up and running. 
PPS - Thanks for this great discussion everyone!
 

[/LEFT]

---

### Post by angrylittleman on 2005-12-06
any advantage to doing a checkinstall over a make install when installing the .deb?

---

### Post by angrylittleman on 2005-12-06
I would like to use acid rip to encode xvids (mplayer handles the encoding).  however xvid is not an option that I can select.  How do I compile my mplayer to use xvid?

n8@Peja:~$ mencoder -ovc help
MEncoder dev-CVS-051206-14:17-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP Thoroughbred; Duron Applebred (Family: 6, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE


Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, currently only AVID is supported.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5


xvid should be listed above but it is not.  Any help?  Thanks!

alm

---

### Post by -DarkMind- on 2005-12-08
thaks you

---

### Post by bored2k on 2005-12-08
[QUOTE=angrylittleman]any advantage to doing a checkinstall over a make install when installing the .deb?[/QUOTE]
Don't do checkinstall, use the fakeroot command I used. It's way better.

---

### Post by bored2k on 2005-12-08
[LIST]
[*][December 8th, 2005 **x86** MPlayer CVS build]("http://rapidshare.de/files/8850028/mplayer_1.0cvs_i386.deb.html").
[*][Libtwolame]("http://rapidshare.de/files/8168617/libtwolame0_0.3.3-1_i386.deb.html") (requirement).
[/LIST]

---

### Post by Rob2687 on 2005-12-10
I compiled it on my desktop machine just now and it looks for the skins in /usr/share/mplayer/Skin

Anyways here's the one I did just now.

Compiled on a P4 Northwood HT

> CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


[http://rapidshare.de/files/8960900/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/8960900/mplayer_1.0cvs_i386.deb.html)


*Don't blame me if you install this and wake up the next day on Rigel 7*

---

### Post by bored2k on 2005-12-11
> **breakthestate][LEFT]I'm using 5.10 freshly installed on a new computer. I've successfully compiled MPlayer from source (1.0pre7) on 5.10 before without a gui. All I did was get the binary codecs from Mplayer and untar them into the /usr/local/lib/codecs directory. After compiling, everything worked perfectly.[/LEFT]
 
Now, I want to use MPlayer (still no gui) with JACK, and hence, I'm looking at the CVS option. Here is my question. The howto says to do the following: 
 
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot
[LEFT]
 
I don't remember apt-getting any of those libraries when I compiled before. Is it the case that all of the above libraries and codecs are only necessary for a gui? I know I'll need build-essential (and debhelper?). Shouldn't I be fine just using the "all" codec package from MPlayerhq.com with the CVS version (with the FFMpeg parts copied into the main directory) and a ./configure said:**
> 
The howto works. The extra packages enable more stuff.

---

### Post by Kallewoof on 2005-12-21
[QUOTE=Hellaxe]Sorry for the question but where i can download the libdivx5linux to compile?
I've googled and have no lucky.

Thanks

Edit: I've found that file sorry again[/QUOTE]

Too bad you didn't state WHERE, cause I have no clue where it is. :(

-Kalle.

---

### Post by sup on 2005-12-21
Thanks for the great howto. However it took me some time to enable support for most codecs, I do not really know for sure if I really need them, but the fact that I knew them by name was enaugh for me to want them enabled. 

So, it seems that for xvid support, you need libxvidcore4-dev to have installed (possible via synaptic```
sudo apt-get install libxvidcore4-dev
```). Maybe this package should be included in the first post?

For x264, you (at least I did) have to visit [http://developers.videolan.org/x264.html]("http://developers.videolan.org/x264.html"), download the daily tarball, (there is no stable release yet and the site seems to be a little overloaded) untar it, compile (I needed nasm ```
sudo apt-get install nasm
``` for succesful compilation) and add this option:  --with-x264libdir=<whereever you compiled the codec> to you configuration. Do not forget to copy the compiled codec to the directory where you store other codecs.

---

### Post by vojtek on 2005-12-26
Hi,

I try to compile mplayer from CVS, but still I have problem. When I do "make" i receive error:

```
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmUnmap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmUnmap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmClose'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmOpen'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmGetMagic'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmGetVersion'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmFreeVersion'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmMap'
/usr/lib/libGL.a(glxext.o): In function `__glXInitialize':
: undefined reference to `drmMap'
collect2: ld returned 1 exit status
```

I have all packages, which are listed in this topic. I do everyting with instruction in INSTALL file and now - with instruction from here. On this forum I found description of the same problem, but without solution. Maybe You can help me?

I have Athlon XP 1667MHz and new ATI drivers (ver 8.20.08, Radeon 9000). I use Ubuntu 5.10 (with installed KDE).

What can I do for solve this compilation problem? Thanks for help and sorry for my poor english writing skills.

---

### Post by izmaelis on 2006-01-03
I was using mplayer that I apt-geted from repositories with no problem before I tried watching Matroska type video files (*.mkv). The sound was horrible, like in slow motion... really really slo-o-ow. I dind't find a solution for that even googled arround for a few days.
After following this how-to my mplayer works great and it looks nice too. Thanks bored2k.

---

### Post by no1wantdthisname on 2006-01-09
Small note: adding dev.rtc.max-user-freq=1024 to /etc/sysctl.conf didn't work for me until I did
```
sudo modprobe rtc
```
You have to add rtc to the end of /etc/modules

---

### Post by AntiMattR on 2006-01-09
Does anyone have a .deb pacakge with XVMC enabled?

I need that package for MPEG2 decoding.

Now that I have come all the way and got the Unichrome DRM (kernel recompiled and everything) to work I am afraid that I will do something to break mplayer and end up without video on my MythTV box. :mad: 

Any suggestions?

Thanks!

---

### Post by janfsd on 2006-01-10
hi, thats an excellent howto!! thanks but i got a problem, it compiles for me and install....but whenever i try to run it i get this error:

```
Option vf: pp doesn't exist.
Error parsing option vf=pp=de,hqdn3d at line 46

```

i dont know what does it mean, i try to search for it but nothing...plz somebody can help me?


****Nevermind, now it works... thanks again for the guide! now mplayer looks really cool and plays without probs mkv files :)

---

### Post by foxy123 on 2006-01-12
I followed this HOWTO a couple of months ago and it worked fine. However, today I decided to update it. Update was fine, but now I've  got the following error when try 'gmplayer':
```
This codecs.conf is too old and incompatible with this MPlayer release! at line 6
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

```
I have no idea about codecs.conf. Regarding the second problem, I've got my skin in /usr/local/share/mplayer, while it looks in /usr/share/mplayer I wonder why in the HOWTO prefix is /usr but skins are in /usr/local?

---

### Post by arnieboy on 2006-01-12
borked2k please make the following corrections in your howto:
1) Please replace
```
sudo mkdir /usr/local/share/mplayer
sudo mkdir /usr/local/share/mplayer/Skin/
```
**with **
```
sudo mkdir /usr/share/mplayer
sudo mkdir /usr/share/mplayer/Skin/
```

2) Please replace 
> copy it to /usr/local/share/mplayer/Skin/
**with** > copy it to /usr/share/mplayer/Skin/

3) Please replace
```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf

```
**with**
```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/share/mplayer/subfont.ttf
```

Nice Howto by the way :)

---

### Post by janfsd on 2006-01-12
thx again for this excellent guide! now everything works for me, exept that when i watch any videos in mplayer, they dont seem to be smooth... its kind of laggy. With the version from synaptic i didnt get this problem... and if i play the same in video in Totem, i dont get this problem, they play smooth enough that i dont feel it...so plz can somebody help me?? Thx in advance!

---

### Post by PenguinZdravko on 2006-01-14
Hi! I have a problem with gmplayer: it can't load because of the skins. I've downloaded Blue skin, un tarred it to /usr/share/mplayer/Skin and renamed the directory of Blue to 'default'. But I get this:
```
penguinzdravko@ghostwheel:~/main$ gmplayer
MPlayer 1.0pre7try2-3.3.6 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE


vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
[skin] file ( /usr/local/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

```
I checked about the 'skin' file, it can be readed by all users. What should I do?

---

### Post by foxy123 on 2006-01-14
[QUOTE=PenguinZdravko]Hi! I have a problem with gmplayer: it can't load because of the skins. I've downloaded Blue skin, un tarred it to /usr/share/mplayer/Skin and renamed the directory of Blue to 'default'. But I get this:
```
penguinzdravko@ghostwheel:~/main$ gmplayer
MPlayer 1.0pre7try2-3.3.6 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE


vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
[skin] file ( **[COLOR="Red"]/usr/local/share/mplayer/Skin/default/skin[/COLOR]** ) not found.
Skin not found (default).

```
I checked about the 'skin' file, it can be readed by all users. What should I do?[/QUOTE]

as you can see, it looks for skins in 
```
/usr/local/share/mplayer/Skin/default/skin
```

---

### Post by foxy123 on 2006-01-14
I've got a strange problem myself. If I play an AVI filr with gmplayer, the playback is jerky, however it is smooth if I play it from command line with 'mplayer'. Why is that and is there a way to fix it?

---

### Post by foxy123 on 2006-01-19
[QUOTE=foxy123]I've got a strange problem myself. If I play an AVI filr with gmplayer, the playback is jerky, however it is smooth if I play it from command line with 'mplayer'. Why is that and is there a way to fix it?[/QUOTE]
so what about the above? Any idea? I also cannot play wav files for some reasons:
```
$ mplayer wreath01.wav
MPlayer dev-CVS-060112-14:10-4.0.2 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2



This codecs.conf is too old and incompatible with this MPlayer release! at line 6
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing wreath01.wav.
Audio file file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, u8, 88.2 kbit/100.00% (ratio: 11025->11025)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 11025Hz/1ch/u8 -> 0Hz/0ch/??...
AO: [oss] 11025Hz 1ch u8 (1 bytes per sample)
Building audio filter chain for 11025Hz/1ch/u8 -> 11025Hz/1ch/u8...
Video: no video
Starting playback...
A:  -0.0 (unknown) of 0.5 (00.4) ??,?%

Exiting... (End of file)

```

and what does this line mean:
```
This codecs.conf is too old and incompatible with this MPlayer release! 
```

---

### Post by valaraukar on 2006-01-21
Maybe you should add "CC=gcc-3.4 DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary" to "Making your own MPlayer debian package (after it works)" section ?

---

### Post by cor2y on 2006-01-26
hello all I just tired to reinstall Mplayer only to get this message after typing in "make"
> 
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1


What could I be doing wrong?
configure had no problems.

---

### Post by Sethiano on 2006-01-30
Hi all!

I've cheated a bit and installed a pre-compiled .deb package of mplayer.

Now, when I try to start mplayer I'll get this error message:

```
mplayer: error while loading shared libraries: libdivxdecore.so.0: cannot open shared object file: No such file or directory

```

Okey, so I'll have to install DivX codec package (divx4linux) then.
**But where???**
The [www.divx.com/divx/linux]("http://www.divx.com/divx/linux") link is broken and nothing can be found in the package manager.

Help please!

---

### Post by bored2k on 2006-01-30
[QUOTE=Sethiano]Hi all!

I've cheated a bit and installed a pre-compiled .deb package of mplayer.

Now, when I try to start mplayer I'll get this error message:

```
mplayer: error while loading shared libraries: libdivxdecore.so.0: cannot open shared object file: No such file or directory

```

Okey, so I'll have to install DivX codec package (divx4linux) then.
**But where???**
The [www.divx.com/divx/linux]("http://www.divx.com/divx/linux") link is broken and nothing can be found in the package manager.

Help please![/QUOTE]
[http://download.divx.com/divx/divx4linux-std-20030428.tar.gz](http://download.divx.com/divx/divx4linux-std-20030428.tar.gz)
[http://216.239.51.104/search?q=cache:6ROUJ5H1fTgJ:www.divx.com/divx/linux/+divx+linux&hl=es&gl=do&ct=clnk&cd=1&client=firefox-a](http://216.239.51.104/search?q=cache:6ROUJ5H1fTgJ:www.divx.com/divx/linux/+divx+linux&hl=es&gl=do&ct=clnk&cd=1&client=firefox-a) ;)

---

### Post by UbunT00L on 2006-02-08
Anyone know a full list of codec options I can use for mplayer?  Right now I'm using the packaged mplayer for ubuntu from the universe repositories but that mplayer doesn't support DTS sound.  I'd like to compile my own mplayer with support for EVERYTHING.  And I want to know what I have to enable before hand.  Has anyone done this yet?

---

### Post by bored2k on 2006-02-08
[QUOTE=UbunT00L]Anyone know a full list of codec options I can use for mplayer?  Right now I'm using the packaged mplayer for ubuntu from the universe repositories but that mplayer doesn't support DTS sound.  I'd like to compile my own mplayer with support for EVERYTHING.  And I want to know what I have to enable before hand.  Has anyone done this yet?[/QUOTE]
dts Enables libdts (DTS Coherent Acoustics decoder) support
[http://developers.videolan.org/libdca.html](http://developers.videolan.org/libdca.html)
[http://gentoo-wiki.com/HOWTO_Emerge_MPlayer](http://gentoo-wiki.com/HOWTO_Emerge_MPlayer)

---

### Post by nrwilk on 2006-02-11
Hi there!  I've gotten farther than ever on this howto tonight, but when running make, I get this error:```
cc: libavcodec/libpostproc/libpostproc.a: No such file or directory
make: *** [mplayer] Error 1

```

I looked in that directory, and that file doesn't exist just like it says.  What can I do?

I copied the libavcodec directory into the main directory and it's contents are as follows:

```
fealos@DeepThought:~/ffmpeg/libavcodec/libpostproc$ ls
CVS       mangle.h                        postprocess.c  postprocess_internal.h
Makefile  postprocess_altivec_template.c  postprocess.h  postprocess_template.c
```

That's also the contents of ~/main/libavcodec/libpostproc

EDIT: I just re-updated that directory with cvs and I still do not have that file.

I checked on the Mplayer site and the links for the cvs downloads are still the same as in your guide.

---

### Post by Manny C on 2006-02-12
Got the same error.

---

### Post by NeoChaosX on 2006-02-12
sudo apt-get install libpostproc-dev

---

### Post by casualprogrammer on 2006-02-12
Good HowTo, thanks for sharing it,

works for me just fine ( Ubuntu 5.10, Sony Vaio Notebook ). Only Mplayer expects "/usr/share/mplayer/" instead of "/usr/local/share/mplayer/" for the skin and font files.

Casual

---

### Post by casualprogrammer on 2006-02-12
Addenda:

<Making your own MPlayer debian package (after it works)

Code: fakeroot debian/rules binary>

Works also, but after installing it with dpkg -i mplayer_1.0cvs_i386.deb, it tells me the mplayer has been compiled without GUI support.

What am I doing wrong here ?

Casual

---

### Post by GTvulse on 2006-02-12
[QUOTE=casualprogrammer]Addenda:
[snip]
Works also, but after installing it with dpkg -i mplayer_1.0cvs_i386.deb, it tells me the mplayer has been compiled without GUI support.

What am I doing wrong here ?

Casual[/QUOTE]
You need the development packages:
```

sudo apt-get install gnome-core-devel

```
and be done with it :-)

---

### Post by johannes on 2006-02-12
Nice guide. It seems to work fine, except I got a font error when I started gmplayer even though I followed the guide and other users advices:

```
/usr/share/mplayer/subfont.ttf doesn't look like a font description, ignoring.
Cannot load font: /usr/share/mplayer/subfont.ttf
```

It seems like either I missed something essential, or the mplayer code has changed so it doesn't support ttf fonts any longer.

I had to download a font package from the mplayer site (Arial - Western), extract it and place some ".raw" fonts and "fonts.desc" in ~/.mplayer/fonts.

```
$ ls ~/.mplayer/fonts
font.desc         iso-8859-1-b.raw   osd-mplayer-b.raw
iso-8859-1-a.raw  osd-mplayer-a.raw
```

I then had to open Preferences > Fonts and change the path to "~/.mplayer/font/font.desc"

After that subtitles worked fine. :)

Also, "sudo apt-get install gnome-core-devel libpostproc-dev" should be included in the guide.

---

### Post by bored2k on 2006-02-12
[QUOTE=johannes]
Also, "sudo apt-get install gnome-core-devel libpostproc-dev" should be included in the guide.[/QUOTE]I have never needed it (even on fresh installs), but added them.

---

### Post by Manny C on 2006-02-13
[QUOTE=NeoChaosX]sudo apt-get install libpostproc-dev[/QUOTE]

Did that. Didn't help. What did help was updating the source using the following command in the source folder (main):
```
cvs -z3 update -dPA 
```

The CVS version was probably wacked out when I downloaded it. IT's compiling great.

---

### Post by UbuntuLinuxUser on 2006-02-13
:confused:

---

### Post by maitreya on 2006-02-13
```
make -C libavcodec/libpostproc LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/username/main/libavcodec/libpostproc'
Makefile:22: ../common.mak: No such file or directory
make[1]: *** No rule to make target `../common.mak'.  Stop.
make[1]: Leaving directory `/home/username/main/libavcodec/libpostproc'
make: *** [libavcodec/libpostproc/libpostproc.a] Error 2
```

Anyone know whats wrong.

---

### Post by Manny C on 2006-02-14
[QUOTE=maitreya]```
make -C libavcodec/libpostproc LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/username/main/libavcodec/libpostproc'
Makefile:22: ../common.mak: No such file or directory
make[1]: *** No rule to make target `../common.mak'.  Stop.
make[1]: Leaving directory `/home/username/main/libavcodec/libpostproc'
make: *** [libavcodec/libpostproc/libpostproc.a] Error 2
```

Anyone know whats wrong.[/QUOTE]

Run 
```
cvs -z3 update -dPA 
```
in the "main" directory.

---

### Post by maitreya on 2006-02-14
[QUOTE=Manny C]Run 
```
cvs -z3 update -dPA 
```
in the "main" directory.[/QUOTE]

Already tried that. Still didn't work.

---

### Post by maitreya on 2006-02-14
Managed to compile mplayer. Thank you for the help and this howto.

---

### Post by darknightuk on 2006-02-14
hey maitreya how did u fix it? I'm receiving the same error as your where am getting nowhere despite following the guide?
edit:-fixed it copied full ffmpeg folder to main and did a deb install had problems since font n skin directories where not the same as the guide? needed to install mplayer-font from apt? all seems well so far

---

### Post by Trojan1313 on 2006-02-14
Great howto, has worked on my stationary PC several times, on my laptop however I get this problem:
```
make -C libavcodec LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/kaminix/main/libavcodec'
Makefile:405: ../common.mak: No such file or directory
make[1]: *** No rule to make target `../common.mak'.  Stop.
make[1]: Leaving directory `/home/kaminix/main/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
```

Any idea why?
It's configuring for pentium-m when my processor is a inten celeron m btw, could that be it? If so, how do I solve it?

EDIT:
Just noticed the same problem was already posted, I'm still waiting for the solution though. :p

---

### Post by darknightuk on 2006-02-14
[QUOTE=Trojan1313]Great howto, has worked on my stationary PC several times, on my laptop however I get this problem:
```
make -C libavcodec LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/kaminix/main/libavcodec'
Makefile:405: ../common.mak: No such file or directory
make[1]: *** No rule to make target `../common.mak'.  Stop.
make[1]: Leaving directory `/home/kaminix/main/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
```

Any idea why?
It's configuring for pentium-m when my processor is a inten celeron m btw, could that be it? If so, how do I solve it?

EDIT:
Just noticed the same problem was already posted, I'm still waiting for the solution though. :p[/QUOTE]i posted what i did above! dunno what file was missing n am to idle to find out right now but there ya go

don't think it matters about the celeron since it's a butchered pentium it'll use nearest to it..i think?

---

### Post by Trojan1313 on 2006-02-15
[QUOTE=darknightuk]i posted what i did above! dunno what file was missing n am to idle to find out right now but there ya go

don't think it matters about the celeron since it's a butchered pentium it'll use nearest to it..i think?[/QUOTE]
Oh, I missed the edit. :p
I'll try that, thanks! :)

EDIT:
It worked, thanks alot! :)

---

### Post by derrumbe on 2006-02-16
```

make[1]: Leaving directory `/download/mp/main/libavcodec/libpostproc'
cc -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium-m -mtune=pentium-m -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT    -I./libavutil -I./libavcodec   -o mplayer mplayer.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o  unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o  libvo/libvo.a libao2/libao2.a libmenu/libmenu.a vidix/libvidix.a Gui/libgui.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a input/libinput.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit libavcodec/libavcodec.a  libavformat/libavformat.a  libavutil/libavutil.a  libavcodec/libpostproc/libpostproc.a  -lmad -ldv -ltheora -logg     -lmp3lame   -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread      -lfaac -lfreetype -lz -lncurses  -lnsl  -lungif    -lfontconfig    libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0   -laa -lGL -ldl  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread      -L/usr/lib -lcaca -lslang -lX11 -L/usr/X11R6/lib -lncurses -lncurses   -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm   -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic   -lm  
libao2/libao2.a(audio_out.o):(.data+0x1c): undefined reference to `audio_out_openal'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1






```


looks like something with libao2 and the libavcodec, but can't pin it down.  thoughts?

---

### Post by nrwilk on 2006-02-19
Got it working, thanks alot everyone!

---

### Post by pek on 2006-02-19
2/20/2006
[mplayer cvs]("http://rapidshare.de/files/13671568/mplayer_1.0cvs_i386.deb.html")
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE

---

### Post by mogliii on 2006-02-19
Hi,

I have Kubuntu 5.10 and followed the guide exactly. (except installing "gnome-core-devel" as its not installable on kubuntu.

Anyway, I installed all packages, I compiled and created a .deb package. No error so far.

But then I came to the step where I am supposed to install the compiled .deb package or to have **msttcorefonts** installed. So I used apt to install. But it seems to be stuck by libcaca-dev. Here is my output 
Note: I also dont understand what it means that packages are kept back. But this is secondary.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview khelpcenter kicker klaptopdaemon
  klipper kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror
  konqueror-nsplugins konsole kontact kooka kopete korganizer kpdf kpf kppp
  krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksvg kuser
  kwalletmanager kwifimanager kwin libkcddb1 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1
The following packages will be upgraded:
  libungif4g
1 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
Need to get 0B/55.7kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libungif4g_4.1.3-2ubuntu0.1_i386.deb (--unpack):
 files list file for package `libcaca-dev' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libungif4g_4.1.3-2ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Trying to remove libcaca-dev results in the same massage.

One more question: In one post [http://www.ubuntuforums.org/showpost.php?p=650634&postcount=41]("http://www.ubuntuforums.org/showpost.php?p=650634&postcount=41") it is stated you should use ```
/usr/share
``` instead of ```
/usr/local/share/
``` but didnt see an answer from bored2k.

---

### Post by pek on 2006-02-20
sudo apt-get dist-upgrade

you have a lot of packages that are "old"

---

### Post by mogliii on 2006-02-20
Hi,

I solved the problem, and apt is working fine.

I found a guide on 
[http://fink.sourceforge.net/faq/usage-fink.php]("http://fink.sourceforge.net/faq/usage-fink.php")
(Q5.19)

The issue with kept back packages seems to be not so important. Its just that the required libs are not in the stable repositories. At least thats what I was told in an other forum.

---

### Post by barn63 on 2006-02-20
Hello. I am sorta new to Ubuntu and linux. I followed the quide and Mplayer installed right except when I go to play a movie with an extension such as .wmv I get an error message saying "Cannot find codec matching selected -vo and video format 0x33564d57" I am not sure what to do for this problem. When I click ok the file plays but only with audio. What should I do. I am guessing its because there are no codecs installed for that file format.

---

### Post by bored2k on 2006-02-21
[QUOTE=barn63]Hello. I am sorta new to Ubuntu and linux. I followed the quide and Mplayer installed right except when I go to play a movie with an extension such as .wmv I get an error message saying "Cannot find codec matching selected -vo and video format 0x33564d57" I am not sure what to do for this problem. When I click ok the file plays but only with audio. What should I do. I am guessing its because there are no codecs installed for that file format.[/QUOTE]
You need to install wmv9 codecs. Use automatix for that.

---

### Post by barn63 on 2006-02-21
Well I ran Automatix and selected "Multimedia Codecs" and I still have the same problem.

Edit: I got mplayer to play but the plugin for firefox will not work.

---

### Post by mogliii on 2006-02-22
Hi,

I tried two plugins and both worked.

1) [http://www.webfreetv.com/linux/]("http://www.webfreetv.com/linux/")
its just an .so file, you have to copy into your /firefox/plugins/ folder.

But I think this plugin is not so very good, as it doesnt show controls (you can control by the standard mplayer keys) and, if I used the "back" button of the browser before the video finished, it was still playing in the background (sound playing).

2) [http://mplayerplug-in.sf.net/]("http://mplayerplug-in.sf.net/")

I am using this one. But after installation it didnt work and in my /home directory a new user was created. Something with /home/ma* containing only one folder (mplyerplug-in) with .so and other files (I dont remember the other file ending and I can not check now). What you have to do is: copy all .so files into the /firefox/plugin folder, and all other files into /firefox/extension.

This works for me with .mov, .avi and .wmv. Didnt try .rm yet, but should work. You can also switch to fullscreen mode. I really recommend that.

also the playback stopps when using "back" button

All other plugins can be found under [http://mplayerhq.hu/homepage/design7/projects.html ]("http://mplayerhq.hu/homepage/design7/projects.html")-> Browser plugins

---

### Post by casualprogrammer on 2006-02-25
Hi bored2k,

I redid the whole process today on another box running dapper. It occurred to me, that the line 
```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot gnome-core-devel libpostproc-dev
```
needs some attention. For whatever reason apt-get decided it would rather use libquicktime0 over libquicktime1, no problem, I "apt-got" libquicktime0 and proceeded. Everything went fine until...

Mplayer GUI wouldn't run and refused to tell me why, just a small messagebox shouted ERROR and disappeared.

So I went through all of it again, until suddenly it dawned on me that apt-get just breaks off after the first mishap.

So I re-issued the above command with libquicktime1 to libquicktime0 and it worked.

I bet there are more uninitiated people like me out there who will be grateful for a remark of caution here.

Casual

---

### Post by bored2k on 2006-02-25
[QUOTE=casualprogrammer]Hi bored2k,

I redid the whole process today on another box running dapper. It occurred to me, that the line 
(...)
Casual[/QUOTE]
This HOWTO is in the 
**Ubuntu Forums > Ubuntu [color=red]Breezy Badger 5.10[/color]  > Customization Tips & Tricks**
section of our forums. I have not tested it on Dapper and I will not change it for dapper. I have done it on fresh Breezy installs and it works. Period.

---

### Post by Trojan1313 on 2006-02-25
```
install build-essential debhelper libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime1 libquicktime-dev libmjpegtools0 fakeroot gnome-core-devel libpostproc-dev
```

Is there any way to put these dependencies into the debpackage?

---

### Post by casualprogrammer on 2006-03-02
[QUOTE=bored2k]This HOWTO is in the 
**Ubuntu Forums > Ubuntu [color=red]Breezy Badger 5.10[/color]  > Customization Tips & Tricks**
section of our forums. I have not tested it on Dapper and I will not change it for dapper. I have done it on fresh Breezy installs and it works. Period.[/QUOTE]

Sorry, bored2k,

my comment was NOT on Dapper at all, but rather on the possible results of putting all packages in one line. Breezy will ask for the newer version just as well, as other packages will change also.

I forgot, that in the Linux World it's more important to categorize a thought correctly, than just make a helpful comment to help people avoid a trapdoor.

Casual

---

### Post by mogliii on 2006-03-08
Hi,

maybe it has been stated somewhere.

I followed the how-to and mplayer works nice. But gmplayer tells me I didnt compile with gui.

The point is maybe that I have Kubuntu (KDE) and I can not install gnome-core-devel...

What package ,available for KDE, can be used instead? Would be very nice to have gmplayer.

---

### Post by Trojan1313 on 2006-03-08
[QUOTE=mogliii]Hi,

maybe it has been stated somewhere.

I followed the how-to and mplayer works nice. But gmplayer tells me I didnt compile with gui.

The point is maybe that I have Kubuntu (KDE) and I can not install gnome-core-devel...

What package ,available for KDE, can be used instead? Would be very nice to have gmplayer.[/QUOTE]
I don't think it's possible to compile mplayer gui with KDE-stuff. However I don't understand the reason why you wouldn't be able to install gnome-core and gnome-core-devel?

Well, anyway, KDEs corresponding package to gnome-core is kdebase, making the corresponding one the gnome-core-devel the one named kdebase-dev. I'm not sure, but you might also need kdelibs with it's dev-package.
Allthough I'm rather confident it won't work without the gnome-core-package, this would be your best shot if you want to try it with KDE ones.

---

### Post by nrwilk on 2006-03-08
[QUOTE=mogliii] Would be very nice to have gmplayer.[/QUOTE]

Why not try Kmplayer?  Lots of people here run it, and are happy with it.  Just search the forums, I know there are a couple howtos about it here.

---

### Post by mogliii on 2006-03-08
hmmm... could install gnome-core-devel...

I dont know if I was a complete blind dumb*** before or if anything miraculously changed in my system? mplayer and gmplayer works now fine, BUT:

when I start gmplayer from console, he complains:

```
xscreensaver_disable: Could not find XScreenSaver window.
/usr/local/share/mplayer/subfont.ttf doesn't look like a font description, ignoring.
Cannot load font: /usr/local/share/mplayer/subfont.ttf

```

About the font: I downloaded msttcorefonts, I created the link as in the how-to, and the font and the link exist (checked with filebrowser)
But: In the player I tried a DVD and subtitles are working

About xscreensaver: checked that option in the configuration dialog. Screensaver is active during playback. How can you fix this?

Thanks until now for all help and my mplayer is a godess!

---

### Post by dashed on 2006-03-10
after i compile... i wnated to put mozilla plugin mplayer thingie... 

in the synaptic magager... when i mark it for instalation...it marks another mplayer package... i didn't want to get rid or replace the mplayer i jsut compiled...

is there other ways to install the mozilla mplayer plugin?

---

### Post by nrwilk on 2006-03-10
Use the one which bored2k suggests at the end of the howto instead.

Also in the following quote is an example of what code to use to install it after you download it.  issue the command while inside the directory where you downloaded the file.  :D 

[QUOTE=bored2k]

Mozilla MPlayer [plugin 3.11]("http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb")
```
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```
[/QUOTE]

---

### Post by ndhskp on 2006-03-11
Hi bored2k.

I just compiled mplayerplugin 3.21.  I recently compiled an updated mplayer from your howto and noticed a lot of people posting deb's for mplayer but not for the plugin.  I compiled the pluging using firefox-dev that's in the main repo's.

Plugin link at bottom of post.

Edit: I have attached an tar.gz file containing mplayerplugin 3.21.  This is not an deb package and was compiled for my computer so may not and probably will not work for you.  I am doing alot of guessing here.  You will need to extract the files **"*.so and *.xpt to /home/username/.mozilla/plugins"**.  Then put the **mplayerplug-in.conf and the mplayerplug-in.types in "/home/username/.mozilla"**.

[mplayerplugin_3.21.tar.gz](http://www.nathaniel-homier.net/misc-files/mplayerplugin_3.21.tar.gz)

---

### Post by mrgnash on 2006-03-14
I'm getting a few errors :(

```
fakeroot debian/rules binary
dh_testdir
make: dh_testdir: Command not found
```

```
/usr/share/mplayer/Skin$ sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
ln: creating symbolic link `/usr/local/share/mplayer/subfont.ttf' to `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf': No such file or directory

```

This second one occurs even though I confirmed the location of the Arial ttf with the 'locate' command.

Lastly, when trying to run gmplayer:

```
mrgnash@smg:/usr/share/mplayer/Skin$ Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.

```

:(

---

### Post by xiaoxin on 2006-03-16
I have compiled mplayer succsfully before using this guide.
Today i did it on another pc, it compiled fine but when i tried to run gmplayer
the gui came up but with an error.
```
MPlayer interrupted by signal 11 in module: unknown
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

I discovered that when i run it as root there was no problem, i checked permissions on the mplayer files but that seems to be ok.

Any suggestions?

---

### Post by danhm on 2006-03-18
[QUOTE=mrgnash]I'm getting a few errors :(

```
fakeroot debian/rules binary
dh_testdir
make: dh_testdir: Command not found
```

```
/usr/share/mplayer/Skin$ sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
ln: creating symbolic link `/usr/local/share/mplayer/subfont.ttf' to `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf': No such file or directory

```

This second one occurs even though I confirmed the location of the Arial ttf with the 'locate' command.

Lastly, when trying to run gmplayer:

```
mrgnash@smg:/usr/share/mplayer/Skin$ Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.

```

:([/QUOTE]


I have the same problem.

---

### Post by Jvaldezjr on 2006-03-24
In the original post it is quoted that you have to install mplayer skins in /usr/local/share/mplayer/Skin.

In the original post it also mentions that the prefix used to configure mplayer is /usr.

When I followed the instructions mplayer crashed becuse it could not find the default skin.  So if you install mplayer in /usr, then the skins are installed in /usr/share/mplayer/Skin.

Just to correct a minor error in an otherwise excellent HOW-TO.

---

### Post by bored2k on 2006-03-24
[QUOTE=Jvaldezjr]In the original post it is quoted that you have to install mplayer skins in /usr/local/share/mplayer/Skin.

In the original post it also mentions that the prefix used to configure mplayer is /usr.

When I followed the instructions mplayer crashed becuse it could not find the default skin.  So if you install mplayer in /usr, then the skins are installed in /usr/share/mplayer/Skin.

Just to correct a minor error in an otherwise excellent HOW-TO.[/QUOTE]
Corrected. Thanks :D.

---

### Post by ndhskp on 2006-03-28
Hello everybody.  Got a mplayer cvs problem.  Using Dapper.  I get this warning every time I start to play video.  The warning only happens when starting video not starting program.  "Failed to open /home/username/.mplayer/default.sub".

Any ideas?

---

### Post by rapala61 on 2006-03-29
i cant go beyong the first step.. it doesnt log me into cvs so i cant even download it :(

---

### Post by xiaoxin on 2006-03-29
I had this problem too before, just try again later it will work again.

---

### Post by Lut!n on 2006-03-29
Thanks alot :D
It works perfectly here:), with today's CVS

---

### Post by Hellaxe on 2006-03-30
[QUOTE=ndhskp]  The warning only happens when starting video not starting program.  "Failed to open /home/username/.mplayer/default.sub".

Any ideas?[/QUOTE]

I compiled right now and appears this error also. I'm using Breezy. 

[COLOR="DarkGreen"]Edit: It only happens with files that don't have subtitles.[/COLOR]

---

### Post by ndhskp on 2006-03-30
[quote=Hellaxe]I compiled right now and appears this error also. I'm using Breezy. 

[COLOR=DarkGreen]Edit: It only happens with files that don't have subtitles.[/COLOR][/quote]Solved!  Open up your favorite text editor and leaving it completely blank, don't put any thing in the text file.  Now save the file as **default.sub** and save to **/home/username/.mplayer**.

Remember to leave the file blank.  It's just a blank text file acting as a place holder.  Hope this helps.

---

### Post by nrwilk on 2006-04-09
I'm trying to install on a new partition.

I'm getting this error from make:
```
Gui/libgui.a(interface.o): In function `guiInit':interface.c:(.text+0xae0): undefined reference to `vo_setwindow'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

Anyone know how I can fix this? :)

---

### Post by Toadicus on 2006-04-17
[QUOTE=nrwilk]I'm trying to install on a new partition.

I'm getting this error from make:
```
Gui/libgui.a(interface.o): In function `guiInit':interface.c:(.text+0xae0): undefined reference to `vo_setwindow'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

Anyone know how I can fix this? :)[/QUOTE]

I went to compile mplayer from CVS today, and ran into this error, as well.  I've been successfully compiling mplayer from the CVS weekly or more for a few months now, both in Breezy and Dapper, and haven't ever seen this before. :)

If it helps at all, here's my configure output.  I use the flags --enable-largefiles --enable-gui --enable-menu.  It compiles fine without --enable-gui, and compiles fine from the official release source, but not from CVS.

**edit**

So, trying to get it to work this morning, I deleted all my old source and downloaded it fresh, and it compiled just fine.  Go figure...

---

### Post by nrwilk on 2006-04-18
[QUOTE=Toadicus]I went to compile mplayer from CVS today, and ran into this error, as well.  I've been successfully compiling mplayer from the CVS weekly or more for a few months now, both in Breezy and Dapper, and haven't ever seen this before. :)
So, trying to get it to work this morning, I deleted all my old source and downloaded it fresh, and it compiled just fine.  Go figure...[/QUOTE]

I'll try it again.  I, as well, have compiled it using this guide about six times on both Breezy and Dapper.  I've never gotten this before.

Oh well, here goes...

---

### Post by Treviño on 2006-05-02
I get the same error... Downloaded sources from CVS yesterday and I always get that error... No way to fix it?

Thanks!

---

### Post by hamil on 2006-05-10
Hello!

I manage to get Mplayer to partially work...
I get sound and video, but also a naggy popup for every video I try to open...

This is the errormessage in the terminal:
```

MPlayer dev-CVS-060510-21:38-4.0.3 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.

```

To get rid of this, I copied the arial.ttf to /home/lasse/.mplayer
and renamed it to subfont.ttf

Is this a solution, or am I just fooling myself and mplayer??

Brgds
Lasse

---

### Post by rubbrduck on 2006-05-15
Weird errors:

I configure with ```
./configure --enable-gui --enable-largefiles --enable-menu --language=it --prefix=/usr --confdir=/etc/mplayer
```
and I get this:
```
Config files successfully generated by ./configure !

  Install prefix: /usr
  Data directory: /usr/share/mplayer
  Config direct.: /etc/mplayer

  Byte order: little-endian
  Optimizing for: pentium4 mmx mmxext sse sse2 mtrr

  Languages:
    Messages/GUI: it
    Manual pages:  it en

  Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l tv mpdvdkit2 vcd dvb
    Codecs: qtx libdv libavcodec real dshow/dmo win32 faad2(internal) faac libmpeg2 libdts liba52 mp3lib libtheora tremor(internal) libmad
    Audio output: alsa esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl md5sum pnm jpeg png mpegpes(dvb) fbdev caca aa opengl xv x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream tv-bsdbt848 live555 cdda dvdread smb
    Codecs: opendivx x264 xvid amr_wb amr_nb xanim musepack speex twolame toolame liblzo gif
    Audio output: sgi sun openal jack polyp dxr2 dsound win32
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx vesa gif89a svga ggi xmga mga dga xvmc directfb tdfx_vid tdfxfb 3dfx
    Audio filters: ladspa

'config.h' and 'config.mak' contain your configuration options.
```

make gives me this:
```
./version.sh `cc -dumpversion`
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT    -I./libavutil -I./libavcodec   -o mplayer.o mplayer.c
In file included from libmpdemux/dvbin.h:11,
                 from mplayer.c:117:
libmpdemux/dvb_defaults.h:73:3: warning: #warning No DVB-T country defined in dvb_defaults.h, defaulting to UK. Ignore this if using Satellite or Cable.
mplayer.c: In function 'main':
mplayer.c:2899: warning: pointer targets in passing argument 2 of 'vobsub_set_from_lang' differ in signedness
mplayer.c:2963: warning: pointer targets in passing argument 2 of 'stream_read' differ in signedness
mplayer.c:2982: warning: pointer targets in passing argument 2 of 'dvd_aid_from_lang' differ in signedness
mplayer.c:2984: warning: pointer targets in passing argument 2 of 'dvd_sid_from_lang' differ in signedness
mplayer.c:3027: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3027: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3027: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3027: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
mplayer.c:3038: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
mplayer.c:3043: warning: pointer targets in passing argument 2 of 'strcat' differ in signedness
mplayer.c:3050: warning: pointer targets in passing argument 2 of 'play_tree_add_file' differ in signedness
mplayer.c:3643: warning: pointer targets in passing argument 2 of 'decode_audio' differ in signedness
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT    -I./libavutil -I./libavcodec   -o vobsub.o vobsub.c
vobsub.c: In function 'vobsub_set_from_lang':
vobsub.c:1220: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of 'strncmp' differ in signedness
cc -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT    -I./libavutil -I./libavcodec   -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o  unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o  libvo/libvo.a libao2/libao2.a input/libinput.a libmenu/libmenu.a vidix/libvidix.a Gui/libgui.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit libavcodec/libavcodec.a  libavformat/libavformat.a  libavutil/libavutil.a  libavcodec/libpostproc/libpostproc.a  -lmad -ldv -ltheora -logg     -lmp3lame   -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread      -lfaac -lfreetype -lz -lncurses  -lnsl   -lfontconfig   libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0   -laa -lGL -ldl  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread      -L/usr/lib -lcaca -lslang -lX11 -L/usr/X11R6/lib -lncurses -lncurses   -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm   -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic  -lm
mplayer.o: In function `main':
mplayer.c:(.text+0xa3a9): undefined reference to `load_termcap'
mplayer.o:(.data+0x3f64): undefined reference to `tv_param_alsa'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

What gives?

---

### Post by Mistervmr on 2006-05-15
I get the same errors ](*,) 

```
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3036: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
mplayer.c:3038: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
mplayer.c:3043: warning: pointer targets in passing argument 2 of 'strcat' differ in signedness
mplayer.c:3050: warning: pointer targets in passing argument 2 of 'play_tree_add_file' differ in signedness
mplayer.c:3643: warning: pointer targets in passing argument 2 of 'decode_audio' differ in signedness
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium-m -mtune=pentium-m -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT      -o vobsub.o vobsub.c
vobsub.c: In function 'vobsub_set_from_lang':
vobsub.c:1220: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of '__builtin_strcmp' differ in signedness
vobsub.c:1223: warning: pointer targets in passing argument 2 of 'strncmp' differ in signedness
cc -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium-m -mtune=pentium-m -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT      -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o  unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o  libvo/libvo.a libao2/libao2.a input/libinput.a libmenu/libmenu.a vidix/libvidix.a Gui/libgui.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit -lavcodec -ldts -lz -ldl -lvorbis -lm -ltheora -lavutil -logg      -lavutil    -lpostproc  -lmad -ldv -ltheora -logg     -lmp3lame   -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread      -lfaac -lfreetype -lz -lncurses  -lnsl       -lfontconfig   libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0   -laa -lGL -ldl  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread      -L/usr/lib -lcaca -lslang -lX11 -L/usr/X11R6/lib -lncurses -lncurses   -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm   -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic  -lm
mplayer.o: In function `main':
mplayer.c:(.text+0xa921): undefined reference to `load_termcap'
mplayer.o:(.data+0x220c): undefined reference to `lavc_decode_opts_conf'
mplayer.o:(.data+0x3f64): undefined reference to `tv_param_alsa'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

---

### Post by govedarov on 2006-05-21
> ivan@120-196:~$ cvs -d:pserver:anonymous@mplayerhq.hu:/cvsroot/mplayer login
Logging in to :pserver:anonymous@mplayerhq.hu:2401/cvsroot/mplayer
CVS password:
cvs [login aborted]: connect to mplayerhq.hu(192.190.173.45):2401 failed: No route to host
ivan@120-196:~$


I get this message , is the ftp server changed or ? I can enter the web site normally ....

---

### Post by nemesa on 2006-05-24
[http://mplayerhq.hu/pipermail/mplayer-users/2006-May/060551.html](http://mplayerhq.hu/pipermail/mplayer-users/2006-May/060551.html)

sad...

---

### Post by vvlaw on 2007-01-06
i compile it from source.not cvs.

but i got these error messages:

   1.
      cc -shared cyberblade_vid.o -L../../libdha -ldha -lm -Wl,-soname,cyberblade_vid.so -o cyberblade_vid.so
   2.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o radeon_vid.o radeon_vid.c
   3.
      cc -shared radeon_vid.o -L../../libdha -ldha -lm -lXinerama -lXext -lX11 -lpthread -Wl,-soname,radeon_vid.so -o radeon_vid.so
   4.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -DRAGE128 -o rage128_vid.o radeon_vid.c
   5.
      cc -shared rage128_vid.o -L../../libdha -ldha -lm -lXinerama -lXext -lX11 -lpthread -Wl,-soname,rage128_vid.so -o rage128_vid.so
   6.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o mach64_vid.o mach64_vid.c
   7.
      cc -shared mach64_vid.o -L../../libdha -ldha -Wl,-soname,mach64_vid.so -o mach64_vid.so
   8.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o nvidia_vid.o nvidia_vid.c
   9.
      cc -shared nvidia_vid.o -L../../libdha -ldha -lm -Wl,-soname,nvidia_vid.so -o nvidia_vid.so
  10.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o mga_vid.o mga_vid.c
  11.
      cc -shared mga_vid.o -L../../libdha -ldha -lm -Wl,-soname,mga_vid.so -o mga_vid.so
  12.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -DCRTC2 -o mga_crtc2_vid.o mga_vid.c
  13.
      cc -shared mga_crtc2_vid.o -L../../libdha -ldha -lm -Wl,-soname,mga_crtc2_vid.so -o mga_crtc2_vid.so
  14.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o pm3_vid.o pm3_vid.c
  15.
      cc -shared pm3_vid.o -L../../libdha -ldha -Wl,-soname,pm3_vid.so -o pm3_vid.so
  16.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o sis_vid.o sis_vid.c
  17.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o sis_bridge.o sis_bridge.c
  18.
      cc -shared sis_vid.o sis_bridge.o -L../../libdha -ldha -Wl,-soname,sis_vid.so -o sis_vid.so
  19.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o unichrome_vid.o unichrome_vid.c
  20.
      cc -shared unichrome_vid.o -L../../libdha -ldha -lm -Wl,-soname,unichrome_vid.so -o unichrome_vid.so
  21.
      cc -c -I. -I.. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -fPIC -o savage_vid.o savage_vid.c
  22.
      savage_vid.c:550:2: warning: #warning enable this again
  23.
      savage_vid.c:578:2: warning: #warning is this needed?
  24.
      cc -shared savage_vid.o -L../../libdha -ldha -lm -Wl,-soname,savage_vid.so -o savage_vid.so
  25.
      rm pm3_vid.o mach64_vid.o
  26.
      make[2]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix/drivers'
  27.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix'
  28.
      make -C libmpdvdkit2
  29.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdvdkit2'
  30.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o css.o css.c
  31.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o device.o device.c
  32.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o dvd_input.o dvd_input.c
  33.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o dvd_reader.o dvd_reader.c
  34.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o dvd_udf.o dvd_udf.c
  35.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o error.o error.c
  36.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o ifo_print.o ifo_print.c
  37.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o ifo_read.o ifo_read.c
  38.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o ioctl.o ioctl.c
  39.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o libdvdcss.o libdvdcss.c
  40.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o nav_print.o nav_print.c
  41.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o nav_read.o nav_read.c
  42.
      cc -I. -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -DHAVE_MPLAYER -DSYS_LINUX -D__USE_UNIX98 -D_REENTRANT -D_GNU_SOURCE -DHAVE_DVDCSS_DVDCSS_H -DSTDC_HEADERS -DHAVE_LIMITS_H -DHAVE_ERRNO_H -DHAVE_INTTYPES_H -DHAVE_UNISTD_H -c -o md5.o md5.c
  43.
      ar rc libmpdvdkit.a css.o device.o dvd_input.o dvd_reader.o dvd_udf.o error.o ifo_print.o ifo_read.o ioctl.o libdvdcss.o nav_print.o nav_read.o md5.o
  44.
      true libmpdvdkit.a
  45.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdvdkit2'
  46.
      make -C libass
  47.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libass'
  48.
      cc -c -I. -I.. -I../libmpcodecs -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -D_GNU_SOURCE -o ***.o ***.c
  49.
      cc -c -I. -I.. -I../libmpcodecs -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -D_GNU_SOURCE -o ***_cache.o ***_cache.c
  50.
      cc -c -I. -I.. -I../libmpcodecs -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -D_GNU_SOURCE -o ***_fontconfig.o ***_fontconfig.c
  51.
      cc -c -I. -I.. -I../libmpcodecs -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -D_GNU_SOURCE -o ***_render.o ***_render.c
  52.
      cc -c -I. -I.. -I../libmpcodecs -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -D_GNU_SOURCE -o ***_utils.o ***_utils.c
  53.
      cc -c -I. -I.. -I../libmpcodecs -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -D_GNU_SOURCE -o ***_mp.o ***_mp.c
  54.
      cc -c -I. -I.. -I../libmpcodecs -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -D_GNU_SOURCE -o ***_bitmap.o ***_bitmap.c
  55.
      ar r libass.a ***.o ***_cache.o ***_fontconfig.o ***_render.o ***_utils.o ***_mp.o ***_bitmap.o
  56.
      ar: creating libass.a
  57.
      true libass.a
  58.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libass'
  59.
      cc -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -I. -I./libavutil -I./libavcodec -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a stream/stream.a libswscale/libswscale.a osdep/libosdep.a -Wl,-z,noexecstack -Llibmpdvdkit2 -lmpdvdkit libavformat/libavformat.a libavcodec/libavcodec.a libavutil/libavutil.a libpostproc/libpostproc.a -lpng -lz -lz -lpthread -ldl -rdynamic -lm libfaad2/libfaad2.a mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a libass/libass.a -lfontconfig -lfreetype -lz -lXinerama -lXext -lX11 -lpthread vidix/libvidix.a
  60.
      mp_msg.o: In function `mp_msg':
  61.
      mp_msg.c:(.text+0x1f7): undefined reference to `guiMessageBox'
  62.
      libvo/libvo.a(video_out.o):(.data+0x20): undefined reference to `video_out_xv'
  63.
      collect2: ld returned 1 exit status
  64.
      make: *** [mplayer] Error 1
  65.
      vvlaw@vvlaw-laptop:~/tools/player/MPlayer-1.0rc1$ make remove
  66.
      make: *** No rule to make target `remove'. Stop.
  67.
      vvlaw@vvlaw-laptop:~/tools/player/MPlayer-1.0rc1$ sudo make remove
  68.
      make: *** No rule to make target `remove'. Stop.
  69.
      vvlaw@vvlaw-laptop:~/tools/player/MPlayer-1.0rc1$ make install
  70.
      make -C loader
  71.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader'
  72.
      make[1]: Nothing to be done for `all'.
  73.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader'
  74.
      make -C loader/dshow
  75.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dshow'
  76.
      make[1]: `libDS_Filter.a' is up to date.
  77.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dshow'
  78.
      make -C loader/dmo
  79.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dmo'
  80.
      make[1]: `libDMO_Filter.a' is up to date.
  81.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dmo'
  82.
      make -C libavformat LIBPREF=lib LIBSUF=.a
  83.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavformat'
  84.
      make[1]: Nothing to be done for `all'.
  85.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavformat'
  86.
      make -C libavcodec LIBPREF=lib LIBSUF=.a
  87.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavcodec'
  88.
      make[1]: Nothing to be done for `all'.
  89.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavcodec'
  90.
      make -C libavutil LIBPREF=lib LIBSUF=.a
  91.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavutil'
  92.
      make[1]: Nothing to be done for `all'.
  93.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavutil'
  94.
      make -C libmpdemux
  95.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdemux'
  96.
      make[1]: Nothing to be done for `all'.
  97.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdemux'
  98.
      make -C stream
  99.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/stream'
 100.
      make[1]: Nothing to be done for `all'.
 101.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/stream'
 102.
      make -C libmpcodecs
 103.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpcodecs'
 104.
      make[1]: Nothing to be done for `all'.
 105.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpcodecs'
 106.
      make -C libao2
 107.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libao2'
 108.
      make[1]: `libao2.a' is up to date.
 109.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libao2'
 110.
      make -C osdep
 111.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/osdep'
 112.
      make[1]: `libosdep.a' is up to date.
 113.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/osdep'
 114.
      make -C libswscale LIBPREF=lib LIBSUF=.a
 115.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libswscale'
 116.
      make[1]: Nothing to be done for `all'.
 117.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libswscale'
 118.
      make -C input
 119.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/input'
 120.
      make[1]: `libinput.a' is up to date.
 121.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/input'
 122.
      make -C libvo
 123.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libvo'
 124.
      make[1]: `libvo.a' is up to date.
 125.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libvo'
 126.
      make -C libaf
 127.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libaf'
 128.
      make[1]: `libaf.a' is up to date.
 129.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libaf'
 130.
      make -C mp3lib
 131.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/mp3lib'
 132.
      make[1]: Nothing to be done for `all'.
 133.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/mp3lib'
 134.
      make -C liba52
 135.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/liba52'
 136.
      make[1]: `liba52.a' is up to date.
 137.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/liba52'
 138.
      make -C libmpeg2
 139.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpeg2'
 140.
      make[1]: `libmpeg2.a' is up to date.
 141.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpeg2'
 142.
      make -C libfaad2
 143.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libfaad2'
 144.
      make[1]: `libfaad2.a' is up to date.
 145.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libfaad2'
 146.
      make -C libdha
 147.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libdha'
 148.
      make[1]: `libdha.so.1.0' is up to date.
 149.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libdha'
 150.
      make -C vidix
 151.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix'
 152.
      make -C drivers
 153.
      make[2]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix/drivers'
 154.
      make[2]: Nothing to be done for `all'.
 155.
      make[2]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix/drivers'
 156.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix'
 157.
      make -C libmpdvdkit2
 158.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdvdkit2'
 159.
      make[1]: Nothing to be done for `all'.
 160.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdvdkit2'
 161.
      make -C libass
 162.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libass'
 163.
      make[1]: Nothing to be done for `all'.
 164.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libass'
 165.
      cc -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -I. -I./libavutil -I./libavcodec -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a stream/stream.a libswscale/libswscale.a osdep/libosdep.a -Wl,-z,noexecstack -Llibmpdvdkit2 -lmpdvdkit libavformat/libavformat.a libavcodec/libavcodec.a libavutil/libavutil.a libpostproc/libpostproc.a -lpng -lz -lz -lpthread -ldl -rdynamic -lm libfaad2/libfaad2.a mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a libass/libass.a -lfontconfig -lfreetype -lz -lXinerama -lXext -lX11 -lpthread vidix/libvidix.a
 166.
      mp_msg.o: In function `mp_msg':
 167.
      mp_msg.c:(.text+0x1f7): undefined reference to `guiMessageBox'
 168.
      libvo/libvo.a(video_out.o):(.data+0x20): undefined reference to `video_out_xv'
 169.
      collect2: ld returned 1 exit status
 170.
      make: *** [mplayer] Error 1
 171.
      vvlaw@vvlaw-laptop:~/tools/player/MPlayer-1.0rc1$ sudo make install
 172.
      make -C loader
 173.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader'
 174.
      make[1]: Nothing to be done for `all'.
 175.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader'
 176.
      make -C loader/dshow
 177.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dshow'
 178.
      make[1]: `libDS_Filter.a' is up to date.
 179.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dshow'
 180.
      make -C loader/dmo
 181.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dmo'
 182.
      make[1]: `libDMO_Filter.a' is up to date.
 183.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/loader/dmo'
 184.
      make -C libavformat LIBPREF=lib LIBSUF=.a
 185.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavformat'
 186.
      make[1]: Nothing to be done for `all'.
 187.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavformat'
 188.
      make -C libavcodec LIBPREF=lib LIBSUF=.a
 189.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavcodec'
 190.
      make[1]: Nothing to be done for `all'.
 191.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavcodec'
 192.
      make -C libavutil LIBPREF=lib LIBSUF=.a
 193.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavutil'
 194.
      make[1]: Nothing to be done for `all'.
 195.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libavutil'
 196.
      make -C libmpdemux
 197.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdemux'
 198.
      make[1]: Nothing to be done for `all'.
 199.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdemux'
 200.
      make -C stream
 201.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/stream'
 202.
      make[1]: Nothing to be done for `all'.
 203.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/stream'
 204.
      make -C libmpcodecs
 205.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpcodecs'
 206.
      make[1]: Nothing to be done for `all'.
 207.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpcodecs'
 208.
      make -C libao2
 209.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libao2'
 210.
      make[1]: `libao2.a' is up to date.
 211.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libao2'
 212.
      make -C osdep
 213.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/osdep'
 214.
      make[1]: `libosdep.a' is up to date.
 215.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/osdep'
 216.
      make -C libswscale LIBPREF=lib LIBSUF=.a
 217.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libswscale'
 218.
      make[1]: Nothing to be done for `all'.
 219.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libswscale'
 220.
      make -C input
 221.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/input'
 222.
      make[1]: `libinput.a' is up to date.
 223.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/input'
 224.
      make -C libvo
 225.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libvo'
 226.
      make[1]: `libvo.a' is up to date.
 227.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libvo'
 228.
      make -C libaf
 229.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libaf'
 230.
      make[1]: `libaf.a' is up to date.
 231.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libaf'
 232.
      make -C mp3lib
 233.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/mp3lib'
 234.
      make[1]: Nothing to be done for `all'.
 235.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/mp3lib'
 236.
      make -C liba52
 237.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/liba52'
 238.
      make[1]: `liba52.a' is up to date.
 239.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/liba52'
 240.
      make -C libmpeg2
 241.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpeg2'
 242.
      make[1]: `libmpeg2.a' is up to date.
 243.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpeg2'
 244.
      make -C libfaad2
 245.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libfaad2'
 246.
      make[1]: `libfaad2.a' is up to date.
 247.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libfaad2'
 248.
      make -C libdha
 249.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libdha'
 250.
      make[1]: `libdha.so.1.0' is up to date.
 251.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libdha'
 252.
      make -C vidix
 253.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix'
 254.
      make -C drivers
 255.
      make[2]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix/drivers'
 256.
      make[2]: Nothing to be done for `all'.
 257.
      make[2]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix/drivers'
 258.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/vidix'
 259.
      make -C libmpdvdkit2
 260.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdvdkit2'
 261.
      make[1]: Nothing to be done for `all'.
 262.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libmpdvdkit2'
 263.
      make -C libass
 264.
      make[1]: Entering directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libass'
 265.
      make[1]: Nothing to be done for `all'.
 266.
      make[1]: Leaving directory `/home/vvlaw/tools/player/MPlayer-1.0rc1/libass'
 267.
      cc -Wdeclaration-after-statement -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include/freetype2 -I. -I./libavutil -I./libavcodec -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a stream/stream.a libswscale/libswscale.a osdep/libosdep.a -Wl,-z,noexecstack -Llibmpdvdkit2 -lmpdvdkit libavformat/libavformat.a libavcodec/libavcodec.a libavutil/libavutil.a libpostproc/libpostproc.a -lpng -lz -lz -lpthread -ldl -rdynamic -lm libfaad2/libfaad2.a mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a libass/libass.a -lfontconfig -lfreetype -lz -lXinerama -lXext -lX11 -lpthread vidix/libvidix.a
 268.
      mp_msg.o: In function `mp_msg':
 269.
      mp_msg.c:(.text+0x1f7): undefined reference to `guiMessageBox'
 270.
      libvo/libvo.a(video_out.o):(.data+0x20): undefined reference to `video_out_xv'
 271.
      collect2: ld returned 1 exit status
 272.
      make: *** [mplayer] Error 1

:( 

anybody know what's going on?thanks

---

