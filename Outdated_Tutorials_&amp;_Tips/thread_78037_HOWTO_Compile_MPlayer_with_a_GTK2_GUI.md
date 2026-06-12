---
title: "HOWTO: Compile MPlayer with a GTK2 GUI"
date: 2005-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by seethru on 2005-10-17
I've always hated the MPlayer GUI, but could never bring myself to change players because I like having the controls and the movie seperated. After a little bit of googling, I managed to find a patch for the newest version. This is a very simple HOWTO, and I've also included how to compile the mplayer plugin with GTK2, which requires no patching.

Lets start off with the essentials, the source, and the build tools (for those who have never compiled before)

You can grab the source from here [ftp://ftp.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre7try2.tar.bz2]("ftp://ftp.mplayerhq.hu/MPlayer/releases/MPlayer-1.0pre7try2.tar.bz2").

Once that has downloaded, extract it by either opening nautilus and browsing to it's location and opening it with archive manager, or run this command.
```
tar xjfv MPlayer-1.0pre7try2.tar.bz2
```

Once thats extracted we'll get all the dependencies and build tools, although if you're reading this it's possible you've used MPlayer before and hate the GTK1 GUI as much as I did.

```
sudo apt-get install build-essential
sudo apt-get install gcc-3.4
sudo apt-get install libx11-dev
sudo apt-get install libxv-dev
sudo apt-get install libpng12-0
sudo apt-get install libpng12-dev
sudo apt-get install checkinstall
sudo apt-get install libavcodec-dev
```
and any other codecs you need

Now, one more thing to download, the patch from here [http://seethrubuntu.ath.cx/MPlayer-1.0pre7-gtk2.patch.bz2]("http://seethrubuntu.ath.cx/MPlayer-1.0pre7-gtk2.patch.bz2")

Make sure to download that to the same directory that you downloaded MPlayer-1.0pre7.tar.bz2 to.

Once the download is done, do the following.
```
cd /location/to/MPlayer-1.0pre7try2
bzcat ../MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1
```
This will patch two files, and after this it's time to start building.
In the MPlayer-1.0pre7try2 directory run the configure command.
```
./configure --enable-gui --enable-gtk2
```

It'll go through the usual configure bit, and you might see it check your GTK version :).

Once configure is done, just run
```
make && sudo checkinstall
```
This will make MPlayer, build a deb, and install the deb for you.
KNOWN ISSUES: Right click on the movie window does not work every time, I've found however if you double click it fast, it does work. I'll be looking into this tonight as there is a patch for a previous version of mplayer that fixes this.


Now, once thats installed, onto MPlayer plugin.
You can grab the source from here [http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-3.11.tar.gz?download]("http://prdownloads.sourceforge.net/mplayerplug-in/mplayerplug-in-3.11.tar.gz?download") and you'll also need the mozilla gecko-sdk which can be found here [http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.8b1/gecko-sdk-i686-pc-linux-gnu-gtk2+xft-1.8b1.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.8b1/gecko-sdk-i686-pc-linux-gnu-gtk2+xft-1.8b1.tar.gz)

Once that is downloaded, extract it, just like we did MPlayer, then browse to the directory it made and run configure again, this time with the following options.
```
./configure --with-gecko-sdk=/path/to/gecko-sdk --enable-gtk2
```

Once configure is done, just run
```
make && sudo checkinstall
```
and again, it will compile, build a deb file, and install the deb file for you.

---

### Post by LaSSarD on 2005-10-17
Other packages you need:
libpng
libpng-dev

I think libavcodec**-dev** would be the right package when you mean libavcodec. Another mistake here:
bzcat ../MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1
It should be:
bzcat MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1

When executing:
./configure --with-gecko-sdk=/path/to/gecko-sdk --enable-gtk2
I've got an error:
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... not found
Checking for gcc-3.2 version ... not found
Checking for gcc-3.1 version ... not found
Checking for gcc3 version ... not found
Checking for gcc-3.0 version ... not found
Checking for cc version ... 4.0.2, bad

I think the problem is the new breezy gcc version... Then I did:
./configure --enable-gui --enable-gtk2 --disable-gcc-checking

OK, but...

Error: X11 support required for GUI compilation

---

### Post by seethru on 2005-10-17
[QUOTE=LaSSarD]I think libavcodec**-dev** would be the right package. Another mistake here:
bzcat ../MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1
It should be:
bzcat MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1

When executing:
./configure --with-gecko-sdk=/path/to/gecko-sdk --enable-gtk2
I've got an error:
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... not found
Checking for gcc-3.2 version ... not found
Checking for gcc-3.1 version ... not found
Checking for gcc3 version ... not found
Checking for gcc-3.0 version ... not found
Checking for cc version ... 4.0.2, bad

I think the problem is the new breezy gcc version...
Thanks for the tut anyway[/QUOTE]

sudo apt-get gcc-3.4
you also need to change /path/to/hecko-sdk to whatever /path/to is.

I'll be sure to add that into the HOWTO.

---

### Post by scourge on 2005-10-17
Okay, once I installed gcc-3.4 it compiled with quite a few warnings. It worked somewhat well, except that the right-click menu stopped working and I had only two video drivers to choose from. The difference in appearance was stunning though.

---

### Post by seethru on 2005-10-17
[QUOTE=scourge]Okay, once I installed gcc-3.4 it compiled with quite a few warnings. It worked somewhat well, except that the right-click menu stopped working and I had only two video drivers to choose from. The difference in appearance was stunning though.[/QUOTE]
Yeah, the right click issue is annoying, there's a patch for pre5 which includes a fix for that so I'm going to comb through it tonight and see if I can't add that to the patch.

---

### Post by seethru on 2005-10-17
[QUOTE=LaSSarD]Error: X11 support required for GUI compilation[/QUOTE]

sudo apt-get install libx11-dev

Can't believe I've missed these, thats what I get for assuming...lol

---

### Post by vaskark on 2005-10-17
Thank god! Great work, seethru. Any chance of doing the same thing for Xine?

---

### Post by Azrael on 2005-10-17
This is a nice howto and compiling and installing went without problems, but:

This method doesn't seem to compile with xv support!

**mplayer -vo help | grep xv** 

...verifies this, because a line similar to this should appear:      xv      X11/Xv But it doesn't (for me at least). 

I definitely need xv for my S3 Savage video card. Anyone know what's going wrong?

---

### Post by NeoChaosX on 2005-10-17
You want to install libxv-dev to get xv support compiled.

---

### Post by Azrael on 2005-10-18
[quote=NeoChaosX]You want to install libxv-dev to get xv support compiled.[/quote]
Oh, I guess I missed that one. Thank you!

---

### Post by seethru on 2005-10-18
I've given it all I can atm, I unfortunately do not understand the patch syntax well enough. If anyone else reading this knows patches, here is the link.

[http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2]("http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2")

[QUOTE=vaskark]Thank god! Great work, seethru. Any chance of doing the same thing for Xine?[/QUOTE]
I will look into that, never personally used xine.

---

### Post by jevanroe on 2005-10-18
i am having trouble finding the libavcodec.  What should I add to my sources list to get it?

---

### Post by seethru on 2005-10-18
[QUOTE=jevanroe]i am having trouble finding the libavcodec.  What should I add to my sources list to get it?[/QUOTE]
meant to remove it from the list, you'll only need libavcodec-dev

---

### Post by paulicat on 2005-10-18
hat about someone hosting these debs somewhere so that everyone can skip the compiling part...I personally don't mind compiling, but considering that there are plenty of new linux users using Ubuntu it would be greatly helpful...only a suggestion, don't shoot me for it! :p
P.S You are missing libgtk2.0-dev which will link up a bunch of other -dev packages neccessary to compile this.

---

### Post by sbassett on 2005-10-18
Be glad to, I will work at getting these up tonight. See my sig.

---

### Post by paulicat on 2005-10-18
sbassett, you're a good man! :D 
I also had to install xlibs-dev to get the plugin to compile...
Package isnt building, heres the log:
dpkg-deb - error: (upstream) version (`in') doesn't contain any digits
dpkg-deb: 1 errors in control file
This happens right at the end, but I'll admit, I suck at creating deb's and I might be missing something...
Edit: I suck...[in] was in the package version option #3 changed to software version instead...

---

### Post by sbassett on 2005-10-18
Paulicat -

It happens to the best of us. Changing the name of the folder after extraction also does the trick.

---

### Post by paulicat on 2005-10-18
lol, never thought of that one!
Thanks...

---

### Post by arnieboy on 2005-10-18
[QUOTE=seethru]I've given it all I can atm, I unfortunately do not understand the patch syntax well enough. If anyone else reading this knows patches, here is the link.

[http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2]("http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2")


I will look into that, never personally used xine.[/QUOTE]
seethru: a patch file is the result of the "diff" command between 2 files. so the patch file has the difference between the 2 files. now this generated patch file can be used to add these differences into any original file elsewhere and generate a modified file. for example, u have modified ur xorg.conf and u do a "diff" between the original and the modified and create a "patch" file. now u can use the "patch" command and this patch file to modify any "original xorg.conf". 
do a 
man diff
and 
man patch 
to know more
a few words of caution:
u shd use the patch command for a certain patch file **ONLY on a file which is IDENTICAL to the original file** (or u will end up borking that file)
u should not edit a patch file by hand. whatever changes u wanna make, make it in the modified file and then do a diff between the original and modified files to create the patch file
Hope this helps.

---

### Post by seethru on 2005-10-18
[QUOTE=arnieboy]seethru: a patch file is the result of the "diff" command between 2 files. so the patch file has the difference between the 2 files. now this generated patch file can be used to add these differences into any original file elsewhere and generate a modified file. for example, u have modified ur xorg.conf and u do a "diff" between the original and the modified and create a "patch" file. now u can use the "patch" command and this patch file to modify any "original xorg.conf". 
do a 
man diff
and 
man patch 
to know more
a few words of caution:
u shd use the patch command for a certain patch file **ONLY on a file which is IDENTICAL to the original file** (or u will end up borking that file)
u should not edit a patch file by hand. whatever changes u wanna make, make it in the modified file and then do a diff between the original and modified files to create the patch file
Hope this helps.[/QUOTE]

Thank you arnie, I didn't even think of that. I've finished making the patch, going to compile it and test it before I put the patch out there though.

---

### Post by sbassett on 2005-10-18
I really need to check these things. Well I guess I will be working on a new amarok package.

---

### Post by seethru on 2005-10-18
[QUOTE=seethru]Thank you arnie, I didn't even think of that. I've finished making the patch, going to compile it and test it before I put the patch out there though.[/QUOTE]
Encountered errors while patching, hopefully later tonight I'll have some good news.

---

### Post by quai_k8 on 2005-10-19
Hi 

I've followed all the instructions ... but I have a problem that i've never had before with 'make' !!!

> quaik8@KQ8:~/Downloadz/MPlayer-1.0pre7try2$ make 
config.mak:23: *** missing separator.  Stop.

please help !!

---

### Post by seethru on 2005-10-19
[QUOTE=quai_k8]Hi 

I've followed all the instructions ... but I have a problem that i've never had before with 'make' !!!



please help !![/QUOTE]

for some reason there is a space at the beginning for line 23 in that file for you..

---

### Post by nszabolcs on 2005-10-20
get the cvs version of mplayer:
[http://www.mplayerhq.hu/homepage/design7/dload.html#cvs](http://www.mplayerhq.hu/homepage/design7/dload.html#cvs)

it alredy has gtk2 support (--enable-gui) and compiles with gcc-4.0.2

if you want to build a debian package then u only need to:
```

cd main
fakeroot debian/rules binary
cd ..
sudo dpkg -i  mplayer_1.0cvs_i386.deb

```

don't forget: ffmpeg, skin, font

---

### Post by mtron on 2005-10-20
can someone post a screenshot of the gtk2 gui from this howto, and / or from the cvs version please?

---

### Post by drummer on 2005-10-20
This didn't work for me, don't know exactly why, but I compiled the CVS and it works nicely, with GTK2 and all :D

---

### Post by nszabolcs on 2005-10-20
[QUOTE=mtron]can someone post a screenshot of the gtk2 gui from this howto, and / or from the cvs version please?[/QUOTE]

i dont think there is much difference
here is mine: (cvs version)
[[img]http://xs51.xs.to/pics/05424/Screenshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs51&d=05424&f=Screenshot.png)

---

### Post by seethru on 2005-10-20
[QUOTE=mtron]can someone post a screenshot of the gtk2 gui from this howto, and / or from the cvs version please?[/QUOTE]
[[IMG]http://img295.imageshack.us/img295/3858/200510182ld.th.jpg[/IMG]](http://img295.imageshack.us/my.php?image=200510182ld.jpg)

---

### Post by quai_k8 on 2005-10-20
It's ok now ... the 23th line of conf.mak was about gtk2 !!!

I didn't got GTK2 dev ^^

THX all ... Mplayer is very beautiful with gtk2

---

### Post by bored2k on 2005-10-20
[QUOTE=nszabolcs]get the cvs version of mplayer:
[http://www.mplayerhq.hu/homepage/design7/dload.html#cvs](http://www.mplayerhq.hu/homepage/design7/dload.html#cvs)

it alredy has gtk2 support (--enable-gui) and compiles with gcc-4.0.2

if you want to build a debian package then u only need to:
```

cd main
fakeroot debian/rules binary
cd ..
sudo dpkg -i  mplayer_1.0cvs_i386.deb

```

don't forget: ffmpeg, skin, font[/QUOTE]
Could you upload a .deb somewhere? Like, rapidshare.de?

---

### Post by bored2k on 2005-10-20
**OSS** audio works, but I'd like **eSound.** What's the command to add that in ./configure ?

By the way, thanks to the guy who posted the CVS link, I didn't think it would be this easy.

---

### Post by bored2k on 2005-10-20
[img]http://img477.imageshack.us/img477/5144/screenshoterror12lj.png[/img]
The strange part is, Audio works!

---

### Post by seethru on 2005-10-20
[QUOTE=bored2k]Could you upload a .deb somewhere? Like, rapidshare.de?[/QUOTE]

I can upload a CVS deb to my webspace, I built the CVS this morning after it was pointed out that it included gtk2 :)

[mplayer_1.0cvs_i386.deb]("http://seethrubuntu.ath.cx/mplayer_1.0cvs_i386.deb")

---

### Post by bored2k on 2005-10-21
[QUOTE=seethru]I can upload a CVS deb to my webspace, I built the CVS this morning after it was pointed out that it included gtk2 :)

[mplayer_1.0cvs_i386.deb]("http://seethrubuntu.ath.cx/mplayer_1.0cvs_i386.deb")[/QUOTE]
Thanks. I noticed it doesn't have ESD support? I'm going to try to compile one with esd.

---

### Post by bored2k on 2005-10-21
```
./configure --enable-gui --enable-largefiles --enable-menu
```

> Most users will find the default configuration options adequate. However I recommend the following options. The first option is required to install the GUI. The second option is to allow access to large files over 2GB. Useful to rip DVD's or record Digital Video. The third option is for menus in the OSD (On Screen Display).

I compiled using that modification. It's working allright so some might want this.

---

### Post by bored2k on 2005-10-21
[http://prdownloads.sourceforge.net/cygnome/esound-devel-0.2.29-1.tar.bz2?download](http://prdownloads.sourceforge.net/cygnome/esound-devel-0.2.29-1.tar.bz2?download)

With **THAT** file, it compiles with ESD X-D.

---

### Post by scourge on 2005-10-21
I managed to compile it with esd support after I installed libsdl1.2-dev and libsdl1.2debian-all. I don't remember what other packages were installed in the process.

---

### Post by emendelson on 2005-10-21
Any chance someone can package this as a .deb package??

---

### Post by bored2k on 2005-10-21
[QUOTE=emendelson]Any chance someone can package this as a .deb package??[/QUOTE]
[http://seethrubuntu.ath.cx/mplayer_1.0cvs_i386.deb](http://seethrubuntu.ath.cx/mplayer_1.0cvs_i386.deb)

---

### Post by bored2k on 2005-10-21
Just uploaded my newly created package (after I managed to compile with esd, alsa and others).

> [**MPlayer dev-CVS-051021-15:57-4.0.2**]("http://rapidshare.de/files/6588394/mplayer_1.0cvs_i386.deb.html")    : October 21st (2005) build of CVS MPlayer with GTK2 GUI, OSD support, Big files (>2GB) support and most of the audio/video outputs. Compiled on Ubuntu 5.10 Breezy Badger for x86 CPU with extensions: MMX MMX2 SSE SSE2.

---

### Post by Technoviking on 2005-10-21
[QUOTE=bored2k]Just uploaded my newly created package (after I managed to compile with esd, alsa and others).[/QUOTE]
Your bandwidth is gone.

Mike

---

### Post by emendelson on 2005-10-21
If someone will email the deb to me (address below) I'll post it on a university server that won't have any bandwidth problems. Here's the address:

emendelson -at- compuserve -dot- com

---

### Post by emendelson on 2005-10-21
Posted here:

[http://www.columbia.edu/~em36/mplayer_1.0cvs_i386.deb](http://www.columbia.edu/~em36/mplayer_1.0cvs_i386.deb)

Can't promise it will be there forever, because I'm close to my limit on disk space, but you can certainly find it there for the next few days (unless the network people ask me to remove it, which is always at least possible).

---

### Post by Technoviking on 2005-10-21
[QUOTE=bored2k]Just uploaded my newly created package (after I managed to compile with esd, alsa and others).[/QUOTE]
I'm getting this problem;
[skin] file ( /usr/local/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

---

### Post by emendelson on 2005-10-21
After posting the file for upload at columbia.edu, I tried installing it. It installs, but when I try to run mplayer, all that happens is that an error message pops up too briefly to read, and then it shuts down. Is this possibly the same problem with the skin reported above?

---

### Post by bored2k on 2005-10-21
The only thing my pkg doesn't provide is a skin. Download one from mplayer HQ and place it that directory AND/or $HOME/.mplayer/Skin

So basically, it's trying to load the "default" skin, so download one, rename its folder to default and place it in /usr/local/share/mplayer/Skin/

I still don't know how to include one.

---

### Post by bored2k on 2005-10-21
@emendelson
Most likely. mplayer commands loads a video from a terminal, gmplayer loads the skin.. but it needs the steps above.


From MPlayer's README:
> 
____________________________
**STEP6: Installing a GUI skin**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Unpack the archive and put the contents in /usr/local/share/mplayer/Skin/ or
~/.mplayer/Skin/. MPlayer will use the skin in the subdirectory named default
of /usr/local/share/mplayer/Skin/ or ~/.mplayer/Skin/ unless told otherwise via
the '-skin' switch. You should therefore rename your skin subdirectory or make
a suitable symbolic link.


---

### Post by j_baer on 2005-10-21
I installed the deb package and when I run gmplayer from the command line I get the following error.

MPlayer dev-CVS-051021-15:57-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Duron/Athlon 4/MP/XP Palomino (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Illegal instruction

I am running an Athlon system.

---

### Post by bored2k on 2005-10-21
```
**Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2**
```

I compiled it in a x86 ie Pentium 4 machine. You need to get an AMD build.

---

### Post by ow50 on 2005-10-21
For public distribution, it would be best to build mplayer the way Marillat does it. Separate packages for all architectures with predefined optimization flags instead of one package with optimization flags autodetected on the package builder's machine. I believe Marillat's package also installs a skin.

---

### Post by bored2k on 2005-10-21
I just compiled mine primarily for my own use and decided to share it ;). So alert: the one I compile will work on x86 *machinas* only.

---

### Post by manicka on 2005-10-21
[QUOTE=bored2k]I just compiled mine primarily for my own use and decided to share it ;).[/QUOTE]
I can't download the link. Page not found error

---

### Post by j_baer on 2005-10-21
bored2k,

I suspected as much. Being a noob I'm not sure I'm up to compiling a copy for AMD but if some else is willing to assist I would greatly appreciate it. With the current state of totem gstreamer a ubuntu enhanced Mplayer would be very popular.

Thanks ...

---

### Post by bored2k on 2005-10-21
[QUOTE=manicka]I can't download the link. Page not found error[/QUOTE]
[http://rapidshare.de/files/6588394/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6588394/mplayer_1.0cvs_i386.deb.html)

Wao. You guys burned my 500mb freewebs account, apparently burned the other link too ?lol.

---

### Post by emendelson on 2005-10-21
OK, downloading a skin and renaming its directory "default" in ~./mplayer/Skin did let the program start, but with an error message about not finding its font.
The message is "New_Face failed. Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf)" I tried installing mplayer-fonts, but that didn't help.

Is there another easy step we can take?

This is worth working toward, because the gnome interface is *very* nice - thank you!

---

### Post by bored2k on 2005-10-21
```
ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf ~/.mplayer/subfont.ttf
```
That could work.

---

### Post by manicka on 2005-10-22
[QUOTE=bored2k]```
ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf ~/.mplayer/subfont.ttf
```
That could work.[/QUOTE]
Spot on... solves the problem. Thanks to you and seethru for this package :)

---

### Post by bored2k on 2005-10-22
[QUOTE=manicka]Spot on... solves the problem. Thanks to you and seethru for this package :)[/QUOTE]
No probs. Check this thread periodically, I might create new CVS Mplayer packages every couple of days. As we speak I'm playing with it (ie adding more codec support for my next upload).

If someone knows how to include a Skin I would really appreciate a PM (want to enable the Clearlooks skin as default).

---

### Post by bored2k on 2005-10-22
[QUOTE=bored2k]No probs. Check this thread periodically, I might create new CVS Mplayer packages every couple of days. As we speak I'm playing with it (ie adding more codec support for my next upload).

If someone knows how to include a Skin I would really appreciate a PM (want to enable the Clearlooks skin as default).[/QUOTE]
> ** Enabled optional drivers:**
    Input: ftp network tv-v4l2 tv-v4l edl tv **matroska** mpdvdkit2 vcd dvb
    Codecs: qtx **xvid** libavcodec real xanim dshow/dmo win32 faad2(internal)** faac l**ibmpeg2 **libdts** liba52 mp3lib **libtheora** tremor(internal) libmad **liblzo**
    Audio output: alsa esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl md5sum pnm png mpegpes(dvb) fbdev aa opengl xv x11 xover tga
    Audio filters:
**  Disabled optional drivers:**
    Input: vstream tv-bsdbt848 live555 cdda dvdread smb
    Codecs: opendivx x264 libdv amr_wb amr_nb musepack twolame toolame gif
    Audio output: sgi sun jack polyp dxr2 dsound win32
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx vesa gif89a jpeg svga caca ggi xmga mga dga xvmc directfb tdfx_vid tdfxfb 3dfx
    Audio filters: ladspa

I added support for the bold ones (haven't uploaded it).
I'm still trying to include musepack, toolame and if possible x.264 support. If anyone knows how, buzz.

---

### Post by manicka on 2005-10-22
will do :)

mozilla-mplayer breaks with this cvs version (sound no pictures). Any thoughts?

---

### Post by manicka on 2005-10-22
[QUOTE=manicka]will do :)

mozilla-mplayer breaks with this cvs version (sound no pictures). Any thoughts?[/QUOTE]

Sorry I've been playing with 1.5 beta so I have a mix up of paths somewhere. 
Works fine in epiphany

---

### Post by bored2k on 2005-10-22
[QUOTE=manicka]will do :)

mozilla-mplayer breaks with this cvs version (sound no pictures). Any thoughts?[/QUOTE]
Just tested it. Amazed at how fast it crashed Firefox lol. I'll see what happens if I try a newer mozilla-mplayer (I'd really like to avoid compiling that.. it would need a gazillion mozilla packages).

---

### Post by bored2k on 2005-10-22
[QUOTE=manicka]Sorry I've been playing with 1.5 beta so I have a mix up of paths somewhere. 
Works fine in epiphany[/QUOTE]
I'm on regular Firefox and it crashed.. incredibly fast.

---

### Post by bored2k on 2005-10-22
```
 wget -c http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb
```
That works!! With shiny new toolbars INSIDE firefox! Wao. Ok I'm dork..ish today.

---

### Post by NeoChaosX on 2005-10-22
With the CVS deb, I initally had stuttering problems with WMVs, but enabling Extra Stereo in audio options managed to fix this. Otherwise, this has been awesome and has replaced VLC as my player of choice. Man, I can't wait for a GTK2-enabled official release of MPlayer.

---

### Post by bored2k on 2005-10-22
I don't have WMV at hand to try, but I'll keep that in mind. Compiling a new MPlayer as we speak (with a couple of more native codec support.. nothing fancy).

---

### Post by bored2k on 2005-10-22
[http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html)

More support for a couple of things. Compiled for x86 boxes. **No AMD64 love.**

Edit: I think tomorrow I'll figure out how to make a deb package with a Skin. I got an idea on how to do it.

---

### Post by seethru on 2005-10-22
[QUOTE=bored2k][http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html)

More support for a couple of things. Compiled for x86 boxes. **No AMD64 love.**

Edit: I think tomorrow I'll figure out how to make a deb package with a Skin. I got an idea on how to do it.[/QUOTE]
What options did you compile into this one?

---

### Post by soul_rebel on 2005-10-22
I simlply compiled from cvs and done a real deb using debian/rules.

---

### Post by bored2k on 2005-10-22
[QUOTE=seethru]What options did you compile into this one?[/QUOTE]
```
./configure --enable-gui --enable-largefiles --enable-menu
```

---

### Post by emendelson on 2005-10-22
**A summary how-to for getting this terrific contribution to work the first time...**

Just to clear things up for anyone who hasn't been following this thread. The key to making this superb contribution by bored2k work smoothly is this (the rest is entirely borrowed from bored2k's advice and slightly modified so that it works for all users, not just you):

1. Install the deb package, but don't run the program.

2. Go to a terminal, and run

```
sudo mkdir /usr/local/share/mplayer
sudo mkdir /usr/local/share/mplayer/Skin/

```

3. EDITED 24 OCT: Go to

[http://www.gnomelook.org/content/show.php?content=21745](http://www.gnomelook.org/content/show.php?content=21745)

and download the clearlook theme, which is absolutely the best for this version of the player. Alternatively, you can go to 

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

and download the official default Blue skin or anything else; in a sudo terminal, extract the directory from the downloaded archive, and copy it to /usr/local/share/mplayer/Skin/ ; rename the extracted directory from "Clearlook" (or whatever) to "default" (cd to the Skindirectory and then try: sudo mv Clearlook default)

4. Assuming that you've downloaded the Microsoft core fonts, do this:

```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/ share/mplayer/subfont.ttf

```

NOW, start mplayer. You can import more skins to ~/.mplayer/Skin in the same way as in step 3; another good one on the mplayerhq.hu page is bluecurve, but Clearlook is very, very nice.

Corrections welcomed, but I think this is more or less guaranteed to work and minimize frustration.

---

### Post by emendelson on 2005-10-22
**How to get the mplayer plugin working in Firefox?**

I downloaded and installed the mplayer plugin mentioned in a post above this, but when I try to play videos in Firefox, they open in a separate gxine window. How do I persuade Firefox to use mplayer and embed the window?

Many thanks for any help with this...

---

### Post by NeoChaosX on 2005-10-22
Remove the gxine plugin files from /usr/lib/mozilla-firefox/plugins.

---

### Post by emendelson on 2005-10-22
Thanks - that told me how to solve it. It turned out there weren't any gxine plugins in /usr/lib/mozilla-firefox/plugins, but there was a gxine plugin in ~/.mozilla/plugins. I moved that one out, and mplayer now works as a plugin!

---

### Post by j_baer on 2005-10-22
Wow ...

This thread has a lot going on. Can someone restate the steps.

Thanks ...

---

### Post by j_baer on 2005-10-22
I am also having problems with the "make" command. I don't know how to fix the problem at line 23.

Any help is appreciated.

---

### Post by Thiago on 2005-10-23
emendelson, thanks bro, now mplayer is working fine. ;)
i dont have arial font here so i use another one from /usr/share/fonts

j_baer, get the .deb file made by bored2k and do what emendelson say...

---

### Post by emendelson on 2005-10-23
To see whether or not you have an Arial font, do this:

sudo updatedb
locate Arial

You'll have to wait a while for the updatedb command to finish before you can give the locate command. You'll see various paths. Any one will do. You can also download the Arial font from the same page where you download the skins (cited in my how-to post up above).

And the person to thank for this is bored2k, who did all the work!!

---

### Post by bored2k on 2005-10-23
[QUOTE=bored2k][http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6593654/mplayer_1.0cvs_i386.deb.html)

More support for a couple of things. Compiled for x86 boxes. **No AMD64 love.**[/QUOTE]
Below is the current state of out of the box supported files by this package. With those and w32codecs I would be surprised if anyone would want anything else, but in such case, if anyone wants some of the options I'm missing and knows how to add them, post how to do it here (I haven't bothered enabling more Video/Audio outputs because 99% of us use the ones already enabled).

>  [LIST=1]
[*][B]Enabled optional drivers:
[/B]
    [LIST]
[*]Input: 
[INDENT]ftp network tv-v4l2 tv-v4l edl 
tv matroska mpdvdkit2 vcd dvb[/INDENT]
[*]Codecs: 
[INDENT]qtx xvid libdv libavcodec real 
xanim dshow/dmo win32 faad2(internal)  
faac libmpeg2 libdts liba52 mp3lib 
libtheora tremor(internal) libmad liblzo gif [/INDENT]
[*]Audio output: 
[INDENT]alsa esd arts oss nas sdl mpegpes(dvb)[/INDENT]
[*]Video output: 
[INDENT]xvidix cvidix sdl gif89a md5sum 
pnm jpeg png mpegpes(dvb) 
fbde v aa opengl xv x11 xover tga caca[/INDENT]
[*]Audio filters:
[/LIST]


[*]**Disabled optional drivers:**
    [LIST]
[*]Input: 
[INDENT]vstream tv-bsdbt848 live555 
cdda dvdread smb[/INDENT]
[*]Codecs: 
[INDENT]opendivx x264 amr_wb amr_nb 
musepack twolame toolame[/INDENT]
[*]Audio output: 
[INDENT]sgi sun jack polyp dxr2 dsound win32[/INDENT]
[*]Video output: [INDENT]
winvidix bl zr zr2 dxr3 dxr2 
directx vesa svga caca ggi 
xmga m ga dga xvmc directfb 
tdfx_vid tdfxfb 3dfx[/INDENT]
[*]Audio filters:
 [INDENT]ladspa[/INDENT]
[/LIST]
[/LIST]



---

### Post by 23meg on 2005-10-23
Very nice! Thanks for the effort, seethru, bored2k and emendelson. 

One question though: drag and drop doesn't seem to be working; did it actually work in the original mplayer build? It's been ages since I used mplayer so I don't remember..

---

### Post by bored2k on 2005-10-23
23meg, I don't think it ever worked. If it did, I did not find any documentation saying how to do it (not even a mention).

---

### Post by Thiago on 2005-10-23
[QUOTE=emendelson]
And the person to thank for this is bored2k, who did all the work!!
[/QUOTE]

indeed, thanks bored2k for all your effort on this ;) finally can watch some (hd) trailers on apple site.

---

### Post by bored2k on 2005-10-23
seethru, sorry for high-jacking your thread. It really was not my intention :-s. Now, why don't I see anyone making AMD64/PPC packages?! Share the love people!

---

### Post by j_baer on 2005-10-23
bored2k,

Loaded MPlayer on my Dell laptop and everything worked great. Thanks ...

My desktop is an AMD Athlon 1700 {32 bit}. I am happy to compile it for this platform but I need a little help.

The "make" command errors @ line 23 and I don't know how to fix it.

Thanks ...

---

### Post by bored2k on 2005-10-23
Argh. I'm not really good at compiling stuff. In fact, I've hardly done compiling.. I just sometimes  learn stuff so fast that it's even silly. I know how to tackle ./configure problems, but not make ones.

---

### Post by bored2k on 2005-10-23
If you have x86 kernels it'll work fine. The ones with troubles will be the amd64 people.

---

### Post by bored2k on 2005-10-23
[CVS MPlayer build for x86]("http://www.ubuntuforums.org/showpost.php?p=437960&postcount=80")

I've got a fresh baked package out of the oven :).

**[CENTER][http://rapidshare.de/files/6683165/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6683165/mplayer_1.0cvs_i386.deb.html)[/CENTER]**
**Changes:**
Enabled the [color=red]**caca**[/color] video output.

Why do I even bother enabling this? Open a terminal and type
```
mplayer video.avi -vo caca
```

ASCII video with colors? yes.. it **ROCKS.** It even plays from command line interfaces (ALT+CTRL+F1). *-vo aa* is also enabled, but that one plays the video with no colors.

---

### Post by seethru on 2005-10-24
[QUOTE=j_baer]bored2k,

Loaded MPlayer on my Dell laptop and everything worked great. Thanks ...

My desktop is an AMD Athlon 1700 {32 bit}. I am happy to compile it for this platform but I need a little help.

The "make" command errors @ line 23 and I don't know how to fix it.

Thanks ...[/QUOTE]
open the file "Makefile" in whatever directory it's giving you that error and make sure there is no space at the beginning of line 23.

@bored2k, no worries. I should probably edit the first page to reflect the cvs version now, lol

---

### Post by bored2k on 2005-10-24
[QUOTE=bored2k]I've got a fresh baked package out of the oven :).[/QUOTE]
I have to thank 23meg for helping me with some bugs I made previously :D.

---

### Post by 23meg on 2005-10-24
right, caca and aa are actually working now! but they seem to ignore the -fs (full screen) option when running from command line and they aren't listed in the  video section of the gui version.

---

### Post by A-star on 2005-10-24
I just installed the latest version from Bored2k and when I try to start gmplayer i get this error:
I have a Athlon XP 1800 processor.
```

filip@star1:~$ gmplayer
MPlayer dev-CVS-051022-13:31-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Duron/Athlon 4/MP/XP Palomino (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2



Illegal instruction

```

---

### Post by bored2k on 2005-10-24
[QUOTE=A-star]I just installed the latest version from Bored2k and when I try to start gmplayer i get this error:
I have a Athlon XP 1800 processor.
```

filip@star1:~$ gmplayer
MPlayer dev-CVS-051022-13:31-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Duron/Athlon 4/MP/XP Palomino (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2



Illegal instruction

```[/QUOTE]
Did the old ones work? This is weird..

---

### Post by bored2k on 2005-10-24
[QUOTE=23meg]right, caca and aa are actually working now! but they seem to ignore the -fs (full screen) option when running from command line and they aren't listed in the  video section of the gui version.[/QUOTE]
I noticed that. I'm not sure what I can do to fix it as I made sure I installed the files needed so, ATM .. :/ .

I'll try asking in #mplayer

---

### Post by A-star on 2005-10-24
[QUOTE=bored2k]Did the old ones work? This is weird..[/QUOTE]
Trying now, will let you know if it works.

---

### Post by bored2k on 2005-10-24
What kernel are you on?
[http://www.ubuntuforums.org/showpost.php?p=438465&postcount=85](http://www.ubuntuforums.org/showpost.php?p=438465&postcount=85) <-- That guy's AMD has it running.

---

### Post by A-star on 2005-10-24
I'm using the standard kernel that is provided with ubuntu, nothing fancy.

But I'm going to try the k7 kernel and see if that solves the problem.

---

### Post by A-star on 2005-10-24
with a k7 kernel I get the same message.
I have no idea what's causing it, and even less ideas how to fix it.

---

### Post by A-star on 2005-10-24
sorry for the quick updates, but I'm going to try and compile it from my system.
Bored2k, can you give me some guidelines (or the source from which you are compiling it from + the commands used).

Thanks for the help.

---

### Post by bored2k on 2005-10-24
**[CENTER]Fasten your seatbelts..[/CENTER]**
```
sudo apt-get install build-essential libx11-dev libxv-dev libpng12-0 libpng12-dev checkinstall libavcodec-dev aalib1 libaa1-dev libaa1 caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2debian libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs
```I was not sure if all those packages were in the Breezy repositories, but if some isn't, skip it. There are a few more I can give you, but first we need to make sure it compiles with those.

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

In order to include libavcodec and libavutil in CVS updates, add the following lines to main/CVS/Entries:

  D/libavcodec////
  D/libavformat////
  D/libavutil////

> Previously win32 codecs were placed in /usr/lib/win32. Applications like Xine use that directory for the same purpose. If you would like you can either keep both directories or make one linked to the other. If both directories exist you cannot link them.
 
```
ln -s /usr/lib/win32 /usr/local/lib/codecs 
```This is optional.

**Compiling MPlayer**
> Most users will find the default configuration options adequate. However I recommend the following options. The first option is required to install the GUI. The second option is to allow access to large files over 2GB. Useful to rip DVD's or record Digital Video. The third option is for menus in the OSD (On Screen Display).
```
./configure --enable-gui --enable-largefiles --enable-menu
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

**A summary how-to for getting this terrific contribution to work the first time...**
> 

1. Install the deb package, but don't run the program.

2. Go to a terminal, and run

```
sudo mkdir /usr/local/share/mplayer
sudo mkdir /usr/local/share/mplayer/Skin/

```

3. go to 

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

and download a skin (Blue is the official default); in a sudo terminal, extract the directory from the archive, and copy it to /usr/local/share/mplayer/Skin/ ; rename the extracted directory from "Blue" (or whatever) to "default" (cd to the Skindirectory and then try: sudo mv Blue default)

4. Assuming that you've downloaded the Microsoft core fonts (by installing **msttcorefonts**), do this:

```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/ share/mplayer/subfont.ttf

```

NOW, start gmplayer. You can import more skins to ~/.mplayer/Skin in the same way as in step 3.

**Extras**
[LIST]
[*][Clearlooks skin.]("http://www.gnomelook.org/content/show.php?content=21745")
[*]ASCII text video (colored):
```
mplayer *video.avi* -vo caca
```

[*]ASCII text video (non colored):
```
mplayer *video.avi* -vo aa
```
[/LIST]

---

### Post by Technoviking on 2005-10-24
[QUOTE=bored2k]
./configure --enable-gui --enable-largefiles --enable-menu
[/QUOTE]

Have you trying compiling with the following options?
--prefix=/usr  --confdir=/etc

---

### Post by bored2k on 2005-10-24
[QUOTE=Mike Basinger]Have you trying compiling with the following options?
--prefix=/usr  --confdir=/etc[/QUOTE]
I haven't. Any advantages?

---

### Post by cwf on 2005-10-24
Hi,

Will this work in Kubuntu?  The thread was originally about compiling Mplayer with GTK2 GUI.  I figure that's for Gnome only.  How does this apply to Kubuntu?

Thanks for supporting us noobs!
CWF

---

### Post by bored2k on 2005-10-24
iT should work. If it doesn't, it's because it's needing some libraries that kubuntu lacks. An apt-get -f install would solve that. Let us know.

---

### Post by Technoviking on 2005-10-24
[QUOTE=bored2k]I haven't. Any advantages?[/QUOTE]
I added 
```
--prefix=/usr --confdir=/etc/mplayer
```
to the configure line. This should make it install to and use the same /etc directory as the Universe mplayer deb. Also, uses /usr/share/mplayer rather than /usr/local/share/mplayer.

Mike

---

### Post by NeoChaosX on 2005-10-24
The deb already uses /etc/mplayer and /usr/share/mplayer according to the package properties in Synaptic. It's not necessary to add those configure options.

---

### Post by Technoviking on 2005-10-24
[QUOTE=NeoChaosX]The deb already uses /etc/mplayer and /usr/share/mplayer according to the package properties in Synaptic. It's not necessary to add those configure options.[/QUOTE]
Without that, mine points to /usr/local/share/mplayer for Skins and font and /usr/local/etc for base config. Must be something funky at my end.

Mike

---

### Post by Technoviking on 2005-10-24
I'm still getting these errors, but mplayer does work.
```

Cannot load font: /usr/share/mplayer/font/Vera.ttf
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

```

---

### Post by bored2k on 2005-10-24
With my deb file? did you ln -s ?

---

### Post by bored2k on 2005-10-24
[QUOTE=Mike Basinger]I'm still getting these errors, but mplayer does work.
```

Cannot load font: /usr/share/mplayer/font/Vera.ttf
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

```[/QUOTE]
With my deb file? did you ln -s ?

---

### Post by Technoviking on 2005-10-24
[QUOTE=bored2k]With my deb file? did you ln -s ?[/QUOTE]
yes, no love.

edit: I think I have tried so many different mplayer .deb, my .mplayer config was screwed up. Deleted and all is happy.

Mike

---

### Post by bored2k on 2005-10-24
[QUOTE=Mike Basinger]yes, no love.

edit: I think I have tried so many different mplayer .deb, my .mplayer config was screwed up. Deleted and all is happy.

Mike[/QUOTE]
Awsome :D. I kinda get worried when my deb fails :(

---

### Post by j_baer on 2005-10-24
bored2k,

Compiled MPlayer  GTK2 on an AMD 2100 and it looks great. The Clear Looks theme is a nice addition.

In addition, I installed w32codec and the libdvdcss packages. When I insert a DVD into my player I get prompted by gnome to burn audio, photo, or data cd. I hit cancel to close the dialog. 

When I tell MPlayer to play the DVD I get a signal 11 error and it closes. The curious thing is the Xine GUI performs this operation perfectly.

Otherwise a great how-to. Ubunutu desparately needs a solid multimedia solution and I believe MPlayer or Xine has the muscle to do with a little TLC.

Cheers ...

---

### Post by bored2k on 2005-10-24
There are some packages that I did not include in my guide because defaut breezy doesn't have them. libdvdcss2 and libdvdcss2-dev being two of them. Install those two and see if you get DVD playback.

compare your ./configure enabled packages with mine here: [http://www.ubuntuforums.org/showthread.php?p=437960#post437960](http://www.ubuntuforums.org/showthread.php?p=437960#post437960)

I think we need to enable dvdread. I don't have DVDs to test though :s.

j_baer, so my guide worked ? :D. So happy.

---

### Post by j_baer on 2005-10-24
bored2k,

I'll give it a try and let you know ...

Thanks  :)

---

### Post by bored2k on 2005-10-25
Another day, another CVS build.

[http://rapidshare.de/files/6725233/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6725233/mplayer_1.0cvs_i386.deb.html)

---

### Post by bored2k on 2005-10-25
Yet another build, this time I added more support, most noticeably in audio outputs.

[http://rapidshare.de/files/6726874/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6726874/mplayer_1.0cvs_i386.deb.html)

---

### Post by Technoviking on 2005-10-25
[QUOTE=bored2k]Yet another build, this time I added more support, most noticeably in audio outputs.

[http://rapidshare.de/files/6726874/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6726874/mplayer_1.0cvs_i386.deb.html)[/QUOTE]
Did you add new dev libraries?

---

### Post by j_baer on 2005-10-25
Just download the lastest "deb" package.

I don't know what was added but I get a "can't load stream" when I try to open a DVD movie.

Thanks ...

---

### Post by bored2k on 2005-10-25
[QUOTE=j_baer]Just download the lastest "deb" package.

I don't know what was added but I get a "can't load stream" when I try to open a DVD movie.

Thanks ...[/QUOTE]
Did the others work? I might have added a funky -dev but I'm not sure atm.

---

### Post by Technoviking on 2005-10-25
You can get my version of Mplayer CVS [here]("http://mikesplanet.net/deb/mplayer_1.0cvs~breezy_i386.deb").

It is built the same as Bored2k's but I point my files to /usr/bin, /usr/share, and /etc/mplayer and added all but one (ecm8000 BAD!!!) of the video/sound libraries included in mplayer deb by the Ubuntu devs.

Works great for me, but only been tested on x86/Pentium M machines.

Mike

---

### Post by j_baer on 2005-10-25
Mike,

Thanks ... I'll give it a try later. My development box is all jazzed up so it time to re-install :(

---

### Post by emendelson on 2005-10-25
Mike Basinger - quick question: does your deb use the same directories as the default universe version? I haven't checked if this is the case with bored2k's version.

---

### Post by bored2k on 2005-10-25
I really don't see what the difference is because even mplayer-fonts from apt-get works with my deb, which means its installed the default way. If it isn't.. that's how I roll.

---

### Post by kdavison007 on 2005-10-25
Does anyone have an updated link for the gtk2 patch?  Seems the link on the first post of this thread is dead.

---

### Post by Technoviking on 2005-10-25
[QUOTE=kdavison007]Does anyone have an updated link for the gtk2 patch?  Seems the link on the first post of this thread is dead.[/QUOTE]
The bored2k CVS instructions works better, and gtk2 is already enable.
[http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100](http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100)

---

### Post by scourge on 2005-10-26
[QUOTE=Mike Basinger]The bored2k CVS instructions works better, and gtk2 is already enable.
[http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100](http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100)[/QUOTE]

I tried the CVS version, and it just crashes way too often to be usable. I guess that's what I should expect from a CVS build. The patched stable version works fine though.

---

### Post by soul_rebel on 2005-10-26
cvs it's a matter of luck. mine is working fine. I also needed cvs to play a strange x264-ac6-mkv file

---

### Post by j_baer on 2005-10-26
bored2k,

Now that we have an enhanced mplayer what is your fav.

VLC or MPlayer? If your answer is VLC have you gotten the firefox plug-in to work? All I ever get is a black screen ...

Thanks

---

### Post by bored2k on 2005-10-26
[QUOTE=j_baer]bored2k,

Now that we have an enhanced mplayer what is your fav.

VLC or MPlayer? If your answer is VLC have you gotten the firefox plug-in to work? All I ever get is a black screen ...

Thanks[/QUOTE]
**VLC** has always been my love, but it's lacking in the codecs department, specially NOW that the Ubuntu builds are getting compiled even more stripped off ("sad, sad situation"). WMV9? Latest Quicktime files? I never got them working (no, don't say "Who uses wmv anyway?" because there are .AVI files out there with a wmv "shell"). Mozilla-VLC plugin? That's a joke. I might sound like I hate VLC, but It has been my prefered since the Windows era (not really that long ago).

The more I use MPlayer (and Totem-xine has backup), the more I get used to it (duh..). It's light as a feather and does what I want it to do. Sometimes, on slow ram *machinas* I've noticed MPlayer would sometimes get slightly out of synch (a/v) while VLC never did this, but when this occurs, Totem-xine comes into play.

I don't even have it installed because that gtk1.2 is a joke which by the way has gotten fixed but no offocial Ubuntu build has been made.

 * VLC and MPlayer rock at dealing with subtitle files. The VLC gui is better (IMO), but the inability to inject codecs into it hurts (still not sure if compiling one would make it work with all 'em codecs).

---

### Post by Turambar on 2005-10-27
I just succesfully built Mplayer from CVS, but the problem with it is that Mplayer crashes when I enable subtitles in a H264 matroska video (SSA subs). All matroskas I have are in H264 format so I don't know if the bug affects other video codecs or not. When I run gmplayer in console it outputs segmentation fault when crashing. Really annoying, any solutions?

---

### Post by bored2k on 2005-10-27
[QUOTE=Turambar]I just succesfully built Mplayer from CVS, but the problem with it is that Mplayer crashes when I enable subtitles in a H264 matroska video (SSA subs). All matroskas I have are in H264 format so I don't know if the bug affects other video codecs or not. When I run gmplayer in console it outputs segmentation fault when crashing. Really annoying, any solutions?[/QUOTE]
I don't think you have h264 enabled. When you ./configure it most likely appears as disabled. I did not include how to compile the CVS with h264 because the repositories do not have the necessary files.

---

### Post by Turambar on 2005-10-28
I had the latest X264 codec compiled, and the video played perfectly, but softsubs crashed mplayer. I found a solution myself, I changed video output from gl to gl2, and no more crashes. The last thing that doesn't work is audio track changing. How do I change it? I read somewhere that # changes the track, but nothing happens.

---

### Post by Arktis on 2005-10-28
> Does anyone have an updated link for the gtk2 patch?  Seems the link on the first post of this thread is dead. 
> I tried the CVS version, and it just crashes way too often to be usable. I guess that's what I should expect from a CVS build. The patched stable version works fine though. 
I am in agreement in that I would rather patch the stable release than muck with cvs. Any chance on getting that patch? I've searched for it but it is nowhere to be found [by me].

At the very least, I'm wondering how soon the mplayer dev team is going to be releasing another stable version.

---

### Post by christooss on 2005-10-28
Can someone post a screnshot of this  gtk2 gui mplayer

Thanks

---

### Post by bored2k on 2005-10-28
[QUOTE=christooss]Can someone post a screnshot of this  gtk2 gui mplayer

Thanks[/QUOTE][CENTER]
[[IMG]http://img407.imageshack.us/img407/8325/gtk28eq.th.jpg[/IMG]](http://img407.imageshack.us/my.php?image=gtk28eq.jpg) [[IMG]http://img407.imageshack.us/img407/1313/screenshotpreferences4we.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotpreferences4we.png)  [[IMG]http://img407.imageshack.us/img407/6764/screenshotpreferences15qf.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screenshotpreferences15qf.png)[/CENTER]

---

### Post by christooss on 2005-10-28
Thanks bored2k

This is what I want. I will for shure use this how to.

What about xine can I make this change to xine :) ?

---

### Post by bored2k on 2005-10-28
[QUOTE=christooss]Thanks bored2k

This is what I want. I will for shure use this how to.

What about xine can I make this change to xine :) ?[/QUOTE]
Me and xine are not friends so I don't know nor care.

---

### Post by Rob2687 on 2005-10-29
Edit: Okay so when I try to install some of the debs posted here. I get

```
sudo dpkg -i /home/robert/Desktop/mplayer_1.0cvs~breezy_i386.deb
Selecting previously deselected package mplayer.
(Reading database ... 101488 files and directories currently installed.)
Unpacking mplayer (from .../mplayer_1.0cvs~breezy_i386.deb) ...
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libdivxdecore0 (>= 1:5.0.1); however:
  Package libdivxdecore0 is not installed.
 mplayer depends on libdivxencore0 (>= 1:5.0.1); however:
  Package libdivxencore0 is not installed.
dpkg: error processing mplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mplayer

```

---

### Post by christooss on 2005-10-29
sudo apt-get -f install

---

### Post by bored2k on 2005-10-31
Monday, **October 31st** (2005) **x86** CVS MPlayer build.

[INDENT]*Notable changes*:
[LIST]
[*]Switched from libdivx**4**linux to libdivx**5**linux.
[*]libdivx**5**linux enabled (or disabled the need for) opendivx.
[*]Enabled twolame.
[/LIST][/INDENT]

[CENTER]**[http://rapidshare.de/files/7009051/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/7009051/mplayer_1.0cvs_i386.deb.html)**[/CENTER]

* **Note**: as usual, keep the previous build at hand (just in case this one's pure crap).

---

### Post by Arktis on 2005-10-31
Any extra steps to make the .deb work on most i386 machines?  I'm thinking of doing this for the patched stable version.

---

### Post by christooss on 2005-10-31
I will put them on my page.

---

### Post by christooss on 2005-10-31
Please try this one

They are made from pre release

[http://www.ahacic.5gigs.com/ubuntu/mplayer-1.0pre7try2-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayer-1.0pre7try2-1_i386.deb)

---

### Post by Nonno Bassotto on 2005-10-31
Why is the standard mplayer version included in the repositories stuck with the old gtk1 gui? I'll surely have a look to bored2k's build, but it would be preferable to have a nice version in the repos, to make upgrades easier. Please don't look at this as a complaint: I appreciate the work of both bored2k and the backports team. I just wanted to understand what is the matter with mplayer. For example I remember the version in the repos didn't work for some time, at the beginnig of Hoary. Thanks
Andrea

---

### Post by Technoviking on 2005-10-31
[QUOTE=Nonno Bassotto]Why is the standard mplayer version included in the repositories stuck with the old gtk1 gui? I'll surely have a look to bored2k's build, but it would be preferable to have a nice version in the repos, to make upgrades easier. Please don't look at this as a complaint: I appreciate the work of both bored2k and the backports team. I just wanted to understand what is the matter with mplayer. For example I remember the version in the repos didn't work for some time, at the beginnig of Hoary. Thanks
Andrea[/QUOTE]

I think Ubuntu is following Gnome lead and putting there efforts into gstreamer and Totem. I don't think the Ubuntu devs pu much work in MPlayer do to this other than simple compiling and security issues.

Mike

---

### Post by Arktis on 2005-11-01
[quote=christooss]Please try this one

They are made from pre release

[http://www.ahacic.5gigs.com/ubuntu/mplayer-1.0pre7try2-1_i386.deb]("http://www.ahacic.5gigs.com/ubuntu/mplayer-1.0pre7try2-1_i386.deb")[/quote]Apparently that site is still up, but whoever owns it has taken down the mplayer deb.
[quote=christooss]I will put them on my page.[/quote]Are you saying you'll host the patched deb for 1.0pre7try2? I've got one that I made which handles dependancies.

**Edit:** Here are the specs:

Optimized for: pentium4 mmx mmx2 sse sse2 mtrr

Enabled optional drivers:
    Input: ftp network edl tv matroska mpdvdkit2 vcd dvb smb
Codecs: qtx libdv libavcodec real xanim dshow/dmo win32 faad2(internal) libmpeg2 libdts liba52 mp3lib libtheora tremor(internal) libmad
    Audio output: alsa esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl vesa md5sum pnm png mpegpes(dvb) fbdev caca aa opengl xv x11 xover dfbmga directfb tga
    Audio filters: ladspa
  Disabled optional drivers:
    Input: vstream tv-v4l2 tv-v4l tv-bsdbt848 live.com cdda dvdread
    Codecs: opendivx x264 xvid amr_wb amr_nb toolame liblzo gif
    Audio output: sgi sun jack polyp dxr2 dsound win32 macosx
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx gif89a jpeg svga ggi xmga mga dga xvmc tdfx_vid tdfxfb 3dfx quartz
    Audio filters:

Works great, has dvd support and of course the gtk2 gui.  Will someone host this or do I have to muck with rapidshare (not preferable)?

---

### Post by christooss on 2005-11-01
Hm deb package is still on the page.

---

### Post by Arktis on 2005-11-01
> Not Found The requested URL /ubuntu/mplayer-1.0pre7try2-1_i386.deb was not found on this server.  
Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request. Additionally, viewing [http://www.ahacic.5gigs.com/ubuntu/]("http://www.ahacic.5gigs.com/ubuntu/") shows that the package is not there.

 >  Parent Directory        07-Oct-2005 13:19      -  
1-ubuntu.si.png         22-Sep-2005 13:46     1k  
English2.tar.gz         27-Aug-2005 05:32    13k  
Screenshot-3.png        05-Aug-2005 15:05   858k  
Slovenian.tar.gz        15-Aug-2005 04:33    13k  
mplayerplug-in_3.11-..> 22-Sep-2005 15:24   779k  
quemu.jpeg              03-Oct-2005 15:09    96k  
ubuntu.si               14-Aug-2005 15:01     2k  
ubuntu.txt              14-Aug-2005 15:01     2k  
unde_construction_lo..> 03-Aug-2005 12:15    44k  
unde_construction_lo..> 03-Aug-2005 12:19    15k  
unde_construction_lo..> 03-Aug-2005 12:21    34k

---

### Post by christooss on 2005-11-01
This is my screenshot.

DO a ctrl + F5 whille lookong in ubuntu dir

---

### Post by bored2k on 2005-11-01
Arktis, install divx5linux from the divx.com website and download the "googeable" x264 -dev debian package to enable opendivx and x264 ;).

---

### Post by bored2k on 2005-11-01
[http://rapidshare.de/files/7068565/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/7068565/mplayer_1.0cvs_i386.deb.html)

Nov 1 build.

---

### Post by kakashi on 2005-11-02
these are the last few lines of the messages i get when i enter 
> fakeroot debian/rules binary
could somebody look through them and see if i have a problem. 
also i us./configure  --prefix=/home/m/guimplayer --enable-gui --enable-largefiles ed this command to compile 
> 


> dh_installdebconf
dh_installdocs --exclude=CVS --exclude=mplayer.1 DOCS/*
dh_installexamples etc/example.conf etc/dvb-menu.conf etc/input.conf etc/menu.conf
dh_installmenu
dh_installmime
dh_installinfo
dh_installchangelogs
#ChangeLog
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_perl
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libdha (soname 1.0, path /usr/lib/libdha.so.1.0, dependency field Depends)
dh_gencontrol
dh_md5sums
dh_builddeb
dpkg-deb: building package `mplayer' in `../mplayer_1.0cvs_i386.deb'.


so is the deb i created ok or do i have to remake it.
thanks gor your help

---

### Post by Arktis on 2005-11-02
I got that same error when creating my deb from patched 1.0pre7try2.  Everything seems okay, but I would be curious to know the answer as well.

---

### Post by GrammatonCleric on 2005-11-02
bored2k:  I get a dependency error when installing the Nov 1 update....

```


gcleric@ares:~/Downloads$ sudo dpkg -i mplayer_1-3.0cvs_i386.deb
(Reading database ... 85685 files and directories currently installed.)
Unpacking mplayer (from mplayer_1-3.0cvs_i386.deb) ...
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libtwolame0; however:
  Package libtwolame0 is not installed.
dpkg: error processing mplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mplayer



``` 
Trying to install libtwolame0 get's the following error:


```


gcleric@ares:~/Downloads$ sudo apt-get install libtwolame0
Reading package lists... Done
Building dependency tree... Done
Package libtwolame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libtwolame0 has no installation candidate


``` 
Thanks,
GC

---

### Post by agentpt on 2005-11-02
Slightly off the topic, but I have been struggling with this for weeks. (Bit of a Linux noobie) I am trying to play 3gp files with Mplayer, I have MPlayer 1.0pre7try2-3.3.5 installed on Hoary , I can see the video but not sound the error I keep getting:

Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'amr_nb' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.


I have googled and searched forums but can't find anything to solve this, I don't know how and where to install this annonying codec. Does anyone have any ideas? :confused:

---

### Post by bored2k on 2005-11-02
[QUOTE=GrammatonCleric]bored2k:  I get a dependency error when installing the Nov 1 update....

```


gcleric@ares:~/Downloads$ sudo dpkg -i mplayer_1-3.0cvs_i386.deb
(Reading database ... 85685 files and directories currently installed.)
Unpacking mplayer (from mplayer_1-3.0cvs_i386.deb) ...
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libtwolame0; however:
  Package libtwolame0 is not installed.
dpkg: error processing mplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mplayer



``` 
Trying to install libtwolame0 get's the following error:


```


gcleric@ares:~/Downloads$ sudo apt-get install libtwolame0
Reading package lists... Done
Building dependency tree... Done
Package libtwolame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libtwolame0 has no installation candidate


``` 
Thanks,
GC[/QUOTE]
I might have to disable twolame. I compiled that one.

---

### Post by kakashi on 2005-11-04
[QUOTE=agentpt]Slightly off the topic, but I have been struggling with this for weeks. (Bit of a Linux noobie) I am trying to play 3gp files with Mplayer, I have MPlayer 1.0pre7try2-3.3.5 installed on Hoary , I can see the video but not sound the error I keep getting:

Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'amr_nb' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.


I have googled and searched forums but can't find anything to solve this, I don't know how and where to install this annonying codec. Does anyone have any ideas? :confused:[/QUOTE]


hmm for a problem like this your probably better off opening a new thread. 
if you post here the ppl here will get pissed at you and you wont get any help. 
if you have searched then i commend you for bieng a really efficient noob. i for one and many other noobs don't use search and simply post. 
congrats.

---

### Post by agentpt on 2005-11-04
[QUOTE=kakashi]hmm for a problem like this your probably better off opening a new thread. 
if you post here the ppl here will get pissed at you and you wont get any help. 
if you have searched then i commend you for bieng a really efficient noob. i for one and many other noobs don't use search and simply post. 
congrats.[/QUOTE]

Thanks for the advice . I'll do just that

---

### Post by bored2k on 2005-11-04
[QUOTE=GrammatonCleric]bored2k:  I get a dependency error when installing the Nov 1 update....

Thanks,
GC[/QUOTE]
Use the attached file.

---

### Post by Vertical on 2005-11-05
Where I can get libfaac0 (version 1.24clean) ? deb package

---

### Post by bored2k on 2005-11-05
You're better off compiling faac.

---

### Post by quai_k8 on 2005-11-05
Hi all !! 

No prob with the installation of the deb !!
But I got a problem ...

> root@KQ8:~/Downloadz# gmplayer
gmplayer: error while loading shared libraries: libdivxdecore.so.0: cannot open shared object file: No such file or directory


what can I do ???

---

### Post by bored2k on 2005-11-05
could try NOT running it as root? Using what deb exactly? do you have win32 codecs installed? get those working.

---

### Post by quai_k8 on 2005-11-05
using your .deb 1nov build !!
win32 codecs installed !!
same as no root ^^ !!

codecs in /usr/local/lib/codecs/ ... it's ok ???

I dunno what's the problem !

---

### Post by quai_k8 on 2005-11-06
it's okey now .. i've found a package with the missing codecs ^^

THX for ur help

---

### Post by jonny on 2005-11-07
I've had trouble downloading the .deb files posted on the site but compilation is really straightforward if you follow the instructions in post 100.  The only caveat is that you also need to install cvs (sudo apt-get install cvs).

Those instructions combine the important parts of 99 other posts.  They're so clear, simple and concise that they should be posted to the wiki and appear at the start of their own thread.  Thanks to everyone who's worked out how to do this.

---

### Post by kakashi on 2005-11-07
i'd like to add that you need to add font if your going to view any subtitles.

---

### Post by chambis on 2005-11-09
dear seethru
i am afraid i can't access this link for the patch you posted [http://seethrubuntu.ath.cx/MPlayer-1...gtk2.patch.bz2](http://seethrubuntu.ath.cx/MPlayer-1...gtk2.patch.bz2)
because it is broken
can you please help me thank you in advance 
:)

---

### Post by bored2k on 2005-11-09
[QUOTE=chambis]dear seethru
i am afraid i can't access this link for the patch you posted [http://seethrubuntu.ath.cx/MPlayer-1...gtk2.patch.bz2](http://seethrubuntu.ath.cx/MPlayer-1...gtk2.patch.bz2)
because it is broken
can you please help me thank you in advance 
:)[/QUOTE]
[http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2](http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2)

---

### Post by bored2k on 2005-11-09
[QUOTE=jonny]I've had trouble downloading the .deb files posted on the site but compilation is really straightforward if you follow the instructions in post 100.  The only caveat is that you also need to install cvs (sudo apt-get install cvs).

Those instructions combine the important parts of 99 other posts.  They're so clear, simple and concise that they should be posted to the wiki and appear at the start of their own thread.  Thanks to everyone who's worked out how to do this.[/QUOTE]
fixed the cvs step.

And btw, I did post it in a separate thread, but this one's good :)

---

### Post by mutenroid on 2005-11-09
[QUOTE=quai_k8]using your .deb 1nov build !!
win32 codecs installed !!
same as no root ^^ !!

codecs in /usr/local/lib/codecs/ ... it's ok ???

I dunno what's the problem ![/QUOTE]

Hi...not working for me:

```

mutenroid@ubuntu:~$ gmplayer
MPlayer dev-CVS-051101-18:47-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2



Instrucción ilegal (translate: illegal instruction)

```

---

### Post by nszabolcs on 2005-11-09
your processor doesn't have SSE2 instruction set support

the best solution is to build mplayer yourself
(you'll need mplayer source, build tools and dev packages then run make and enjoy your custom mplayer)

---

### Post by bored2k on 2005-11-09
[QUOTE=mutenroid]Hi...not working for me:

```

mutenroid@ubuntu:~$ gmplayer
MPlayer dev-CVS-051101-18:47-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2



Instrucción ilegal (translate: illegal instruction)

```[/QUOTE]
[http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100](http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100)

---

### Post by mutenroid on 2005-11-09
[QUOTE=nszabolcs]your processor doesn't have SSE2 instruction set support

the best solution is to build mplayer yourself
(you'll need mplayer source, build tools and dev packages then run make and enjoy your custom mplayer)[/QUOTE]

hmm...too very complicated for me, but i'll try :cool:

---

### Post by christooss on 2005-11-09
What about this error. Every thing elese is working flavlesly. Thank you bored2k

---

### Post by bored2k on 2005-11-09
It's just mplayer telling you that it doesn't have any fonts for OSD and Subs.

I **think** you can ```
sudo apt-get install mplayer-fonts
``` without downgrading, but if you can't, follow the step in the guide:
> 4. Assuming that you've downloaded the Microsoft core fonts (by installing **msttcorefonts**), do this:

```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/ share/mplayer/subfont.ttf

```Note: Arial.ttf or any other .ttf you want. To get the dirs of yours simply do a locate *.ttf and grab one.

---

### Post by christooss on 2005-11-10
I had to install msttcorefonts first. Argh I thought I have installed them already. so now every thing works perfectly

Thanks again

---

### Post by mutenroid on 2005-11-10
[QUOTE=mutenroid]hmm...too very complicated for me, but i'll try :cool:[/QUOTE]

Ok...i made my Athlon XP version with the great bored2k tutorial...and runs very well :razz: :razz: 

```

  Byte order: little-endian
  Optimizing for: athlon-4 mmx mmx2 3dnow 3dnowex sse mtrr

  Languages:
    Messages/GUI: en
    Manual pages:  en

  Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l edl tv matroska mpdvdkit2 vcd dvb
    Codecs: qtx divx5linux libdv libavcodec real xanim dshow/dmo win32 faad2(internal) faac libmpeg2 libdts liba52 mp3lib libtheora tremor(internal) libmad
    Audio output: alsa esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl md5sum pnm jpeg png mpegpes(dvb) fbdev caca aa opengl xv x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream tv-bsdbt848 live555 cdda dvdread smb
    Codecs: divx4linux x264 xvid amr_wb amr_nb musepack speex twolame toolame liblzo gif
    Audio output: sgi sun jack polyp dxr2 dsound win32
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx vesa gif89a svga ggi xmga mga dga xvmc directfb tdfx_vid tdfxfb 3dfx
    Audio filters: ladspa

```

deb file here: [http://www.filefactory.com/get/f.php?f=2c338bbcbc15abdb92f27cb9]("http://www.filefactory.com/get/f.php?f=2c338bbcbc15abdb92f27cb9")

...Play video files through ESD driver not work :???: but with the OSS driver plays well but a with a little asynch. How configure to play through ESD??

Thanks for all..

---

### Post by mutenroid on 2005-11-10
bad news...

-win32 codecs installed
-mplayerplug-in_3.11-1_i386.deb installed

This url to play a simple mov file:[apple.com/trailers/sony_pictures/the_gospel/low.html]("apple.com/trailers/sony_pictures/the_gospel/low.html")

"(no picture)" message in mozilla

Firefox output....
```

mutenroid@ubuntu:~/.mplayer$ mozilla
*** loading the extensions datasource
*** loading the extensions datasource
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat /home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov
No existe el fichero o el directorio
libdvdnav: vm: faild to open/read the DVD
[00000287] main input error: no suitable access module for `:///home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov'
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat /home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov
No existe el fichero o el directorio
libdvdnav: vm: faild to open/read the DVD
[00000292] main input error: no suitable access module for `:///home/mutenroid/.mozilla/firefox/ei0djr4a.default/Cache/the_gospel_m240.mov'
[00000269] main playlist: nothing to play

```

---

### Post by bored2k on 2005-11-10
[QUOTE=mutenroid]Ok...i made my Athlon XP version with the great bored2k tutorial...and runs very well :razz: :razz: 

```

  Byte order: little-endian
  Optimizing for: athlon-4 mmx mmx2 3dnow 3dnowex sse mtrr

  Languages:
    Messages/GUI: en
    Manual pages:  en

  Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l edl tv matroska mpdvdkit2 vcd dvb
    Codecs: qtx divx5linux libdv libavcodec real xanim dshow/dmo win32 faad2(internal) faac libmpeg2 libdts liba52 mp3lib libtheora tremor(internal) libmad
    Audio output: alsa esd arts oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl md5sum pnm jpeg png mpegpes(dvb) fbdev caca aa opengl xv x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream tv-bsdbt848 live555 cdda dvdread smb
    Codecs: divx4linux x264 xvid amr_wb amr_nb musepack speex twolame toolame liblzo gif
    Audio output: sgi sun jack polyp dxr2 dsound win32
    Video output: winvidix bl zr zr2 dxr3 dxr2 directx vesa gif89a svga ggi xmga mga dga xvmc directfb tdfx_vid tdfxfb 3dfx
    Audio filters: ladspa

```

deb file here: [http://www.filefactory.com/get/f.php?f=2c338bbcbc15abdb92f27cb9]("http://www.filefactory.com/get/f.php?f=2c338bbcbc15abdb92f27cb9")

...Play video files through ESD driver not work :???: but with the OSS driver plays well but a with a little asynch. How configure to play through ESD??

Thanks for all..[/QUOTE]
No idea. If it's enabled it should work .. at least on paper :-s. 

Note to all compiling: To get more enabled codecs and stuff (like h264 etc), some google+fetch+compiling is needed.

---

### Post by mutenroid on 2005-11-10
Hmm....

invoking gmplayer as root, esd not work, but as a normal user works great. Sorry. Now, mplayer as a solo-player runs very very well.

The quicktime format in firefox stills not work.

I have vlc (and mozilla-vlc plugin) installed too..

Could be the problem??

Deinstall vlc and plugin??

Thanks and "saludos" ;)

---

### Post by bored2k on 2005-11-10
did you install mplayer plugin 3.11 ? do you have win32 codecs?

you dont need to remove vlc. you might want to get rid of th plugin tho

---

### Post by inechita on 2005-11-12
[QUOTE=bored2k]```
**Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2**
```

I compiled it in a x86 ie Pentium 4 machine. You need to get an AMD build.[/QUOTE]


Where can we get an AMD deb ?

---

### Post by bored2k on 2005-11-12
[QUOTE=inechita]Where can we get an AMD deb ?[/QUOTE]
When you build & upload one ;).

---

### Post by Nego on 2005-11-13
[QUOTE=bored2k][http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2](http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2)[/QUOTE]

I downloaded the patch from that link and when I use it i get:

```
nego@ubuntu:~/MPlayer-1.0pre7try2$ bzcat ../mplayer1.0pre5-gtk2-20040730.patch.bz2 |patch -p1
patching file Gui/Makefile
patching file Gui/cfg.c
Hunk #1 succeeded at 174 (offset 17 lines).
patching file Gui/cfg.h
Hunk #1 succeeded at 41 (offset 9 lines).
patching file Gui/interface.c
Hunk #1 succeeded at 32 with fuzz 2 (offset 2 lines).
Hunk #2 succeeded at 212 with fuzz 1 (offset 28 lines).
Hunk #3 succeeded at 256 (offset 28 lines).
Hunk #4 succeeded at 546 (offset 28 lines).
Hunk #5 FAILED at 635.
Hunk #6 succeeded at 922 (offset 75 lines).
1 out of 6 hunks FAILED -- saving rejects to file Gui/interface.c.rej
patching file Gui/mplayer/gtk/about.c
patching file Gui/mplayer/gtk/common.c
patching file Gui/mplayer/gtk/common.h
patching file Gui/mplayer/gtk/eq.c
patching file Gui/mplayer/gtk/eq.h
patching file Gui/mplayer/gtk/fs.c
Hunk #2 FAILED at 15.
1 out of 2 hunks FAILED -- saving rejects to file Gui/mplayer/gtk/fs.c.rej
patching file Gui/mplayer/gtk/fs.h
patching file Gui/mplayer/gtk/mb.c
patching file Gui/mplayer/gtk/menu.c
Hunk #1 succeeded at 65 (offset 43 lines).
Hunk #2 FAILED at 76.
Hunk #3 FAILED at 103.
Hunk #4 succeeded at 172 (offset 101 lines).
Hunk #5 succeeded at 294 (offset 101 lines).
Hunk #6 succeeded at 306 (offset 101 lines).
Hunk #7 succeeded at 350 (offset 101 lines).
Hunk #8 FAILED at 389.
Hunk #9 FAILED at 589.
4 out of 9 hunks FAILED -- saving rejects to file Gui/mplayer/gtk/menu.c.rej
patching file Gui/mplayer/gtk/mp_pl.c
patching file Gui/mplayer/gtk/mp_pl.h
patching file Gui/mplayer/gtk/opts.c
Hunk #4 succeeded at 101 (offset 1 line).
Hunk #5 succeeded at 146 with fuzz 1 (offset 1 line).
Hunk #6 succeeded at 159 with fuzz 1 (offset -4 lines).
Hunk #7 FAILED at 203.
Hunk #8 succeeded at 254 (offset -4 lines).
Hunk #9 succeeded at 305 (offset -4 lines).
Hunk #10 succeeded at 332 (offset -4 lines).
Hunk #11 succeeded at 362 (offset -4 lines).
Hunk #12 FAILED at 460.
Hunk #13 succeeded at 525 (offset -8 lines).
Hunk #14 FAILED at 568.
Hunk #15 succeeded at 607 (offset -7 lines).
Hunk #16 succeeded at 627 (offset -7 lines).
Hunk #17 FAILED at 689.
Hunk #18 succeeded at 711 (offset -6 lines).
Hunk #19 FAILED at 806.
Hunk #20 succeeded at 857 (offset -7 lines).
Hunk #21 succeeded at 877 (offset -7 lines).
Hunk #22 succeeded at 903 (offset -7 lines).
Hunk #23 succeeded at 951 (offset -6 lines).
Hunk #24 succeeded at 959 (offset -6 lines).
Hunk #25 succeeded at 1066 (offset -6 lines).
Hunk #26 succeeded at 1131 (offset -6 lines).
Hunk #27 succeeded at 1188 (offset -6 lines).
Hunk #28 FAILED at 1290.
Hunk #29 FAILED at 1352.
Hunk #30 FAILED at 1359.
Hunk #31 FAILED at 1384.
Hunk #32 FAILED at 1413.
Hunk #33 FAILED at 1430.
Hunk #34 FAILED at 1561.
Hunk #35 FAILED at 1592.
Hunk #36 FAILED at 1617.
Hunk #37 FAILED at 1639.
Hunk #38 succeeded at 1743 (offset 54 lines).
Hunk #39 succeeded at 1761 (offset 54 lines).
Hunk #40 succeeded at 1786 (offset 54 lines).
Hunk #41 succeeded at 1811 (offset 54 lines).
Hunk #42 succeeded at 1820 (offset 54 lines).
Hunk #43 succeeded at 1836 with fuzz 2 (offset 54 lines).
Hunk #44 succeeded at 1881 (offset 54 lines).
Hunk #45 succeeded at 1898 (offset 54 lines).
15 out of 45 hunks FAILED -- saving rejects to file Gui/mplayer/gtk/opts.c.rej
patching file Gui/mplayer/gtk/pl.c
Hunk #1 FAILED at 17.
1 out of 1 hunk FAILED -- saving rejects to file Gui/mplayer/gtk/pl.c.rej
patching file Gui/mplayer/gtk/playlist.c
patching file Gui/mplayer/gtk/playlist.h
patching file Gui/mplayer/gtk/playlist_create.c
patching file Gui/mplayer/gtk/playlist_create.h
patching file Gui/mplayer/gtk/sb.c
patching file Gui/mplayer/gtk/sb.h
patching file Gui/mplayer/gtk/support.h
patching file Gui/mplayer/gtk/url.c
patching file Gui/mplayer/pixmaps/about.xpm
patching file Gui/mplayer/play.c
patching file Gui/mplayer/widgets.c
Hunk #3 succeeded at 68 with fuzz 1.
patching file Gui/mplayer/widgets.h
patching file configure
Hunk #1 succeeded at 150 (offset 1 line).
Hunk #2 succeeded at 359 (offset 25 lines).
Hunk #3 succeeded at 1833 (offset 191 lines).
Hunk #4 succeeded at 6408 (offset 569 lines).
Hunk #5 succeeded at 6454 (offset 569 lines).
Hunk #6 succeeded at 6864 with fuzz 1 (offset 621 lines)
```

---

### Post by bored2k on 2005-11-13
I recommend building from CVS, but if you want to use the .7PRE, I've never used the patch :/.

---

### Post by mutenroid on 2005-11-13
> 
Where can we get an AMD deb ?

here [http://www.filefactory.com/get/f.php?f=2c338bbcbc15abdb92f27cb9]("http://www.filefactory.com/get/f.php?f=2c338bbcbc15abdb92f27cb9")

---

### Post by Arktis on 2005-11-14
[QUOTE=Nego]I downloaded the patch from that link and when I use it i get:

```
nego@ubuntu:~/MPlayer-1.0pre7try2$ bzcat ../mplayer1.0pre5-gtk2-20040730.patch.bz2 |patch -p1
patching file Gui/Makefile
patching file Gui/cfg.c
Hunk #1 succeeded at 174 (offset 17 lines).
patching file Gui/cfg.h
Hunk #1 succeeded at 41 (offset 9 lines).
patching file Gui/interface.c
Hunk #1 succeeded at 32 with fuzz 2 (offset 2 lines).
Hunk #2 succeeded at 212 with fuzz 1 (offset 28 lines).
Hunk #3 succeeded at 256 (offset 28 lines).
Hunk #4 succeeded at 546 (offset 28 lines).
Hunk #5 FAILED at 635.
Hunk #6 succeeded at 922 (offset 75 lines).
1 out of 6 hunks FAILED -- saving rejects to file Gui/interface.c.rej
patching file Gui/mplayer/gtk/about.c
patching file Gui/mplayer/gtk/common.c
patching file Gui/mplayer/gtk/common.h
patching file Gui/mplayer/gtk/eq.c
patching file Gui/mplayer/gtk/eq.h
patching file Gui/mplayer/gtk/fs.c
Hunk #2 FAILED at 15.
1 out of 2 hunks FAILED -- saving rejects to file Gui/mplayer/gtk/fs.c.rej
patching file Gui/mplayer/gtk/fs.h
patching file Gui/mplayer/gtk/mb.c
patching file Gui/mplayer/gtk/menu.c
Hunk #1 succeeded at 65 (offset 43 lines).
Hunk #2 FAILED at 76.
Hunk #3 FAILED at 103.
Hunk #4 succeeded at 172 (offset 101 lines).
Hunk #5 succeeded at 294 (offset 101 lines).
Hunk #6 succeeded at 306 (offset 101 lines).
Hunk #7 succeeded at 350 (offset 101 lines).
Hunk #8 FAILED at 389.
Hunk #9 FAILED at 589.
4 out of 9 hunks FAILED -- saving rejects to file Gui/mplayer/gtk/menu.c.rej
patching file Gui/mplayer/gtk/mp_pl.c
patching file Gui/mplayer/gtk/mp_pl.h
patching file Gui/mplayer/gtk/opts.c
Hunk #4 succeeded at 101 (offset 1 line).
Hunk #5 succeeded at 146 with fuzz 1 (offset 1 line).
Hunk #6 succeeded at 159 with fuzz 1 (offset -4 lines).
Hunk #7 FAILED at 203.
Hunk #8 succeeded at 254 (offset -4 lines).
Hunk #9 succeeded at 305 (offset -4 lines).
Hunk #10 succeeded at 332 (offset -4 lines).
Hunk #11 succeeded at 362 (offset -4 lines).
Hunk #12 FAILED at 460.
Hunk #13 succeeded at 525 (offset -8 lines).
Hunk #14 FAILED at 568.
Hunk #15 succeeded at 607 (offset -7 lines).
Hunk #16 succeeded at 627 (offset -7 lines).
Hunk #17 FAILED at 689.
Hunk #18 succeeded at 711 (offset -6 lines).
Hunk #19 FAILED at 806.
Hunk #20 succeeded at 857 (offset -7 lines).
Hunk #21 succeeded at 877 (offset -7 lines).
Hunk #22 succeeded at 903 (offset -7 lines).
Hunk #23 succeeded at 951 (offset -6 lines).
Hunk #24 succeeded at 959 (offset -6 lines).
Hunk #25 succeeded at 1066 (offset -6 lines).
Hunk #26 succeeded at 1131 (offset -6 lines).
Hunk #27 succeeded at 1188 (offset -6 lines).
Hunk #28 FAILED at 1290.
Hunk #29 FAILED at 1352.
Hunk #30 FAILED at 1359.
Hunk #31 FAILED at 1384.
Hunk #32 FAILED at 1413.
Hunk #33 FAILED at 1430.
Hunk #34 FAILED at 1561.
Hunk #35 FAILED at 1592.
Hunk #36 FAILED at 1617.
Hunk #37 FAILED at 1639.
Hunk #38 succeeded at 1743 (offset 54 lines).
Hunk #39 succeeded at 1761 (offset 54 lines).
Hunk #40 succeeded at 1786 (offset 54 lines).
Hunk #41 succeeded at 1811 (offset 54 lines).
Hunk #42 succeeded at 1820 (offset 54 lines).
Hunk #43 succeeded at 1836 with fuzz 2 (offset 54 lines).
Hunk #44 succeeded at 1881 (offset 54 lines).
Hunk #45 succeeded at 1898 (offset 54 lines).
15 out of 45 hunks FAILED -- saving rejects to file Gui/mplayer/gtk/opts.c.rej
patching file Gui/mplayer/gtk/pl.c
Hunk #1 FAILED at 17.
1 out of 1 hunk FAILED -- saving rejects to file Gui/mplayer/gtk/pl.c.rej
patching file Gui/mplayer/gtk/playlist.c
patching file Gui/mplayer/gtk/playlist.h
patching file Gui/mplayer/gtk/playlist_create.c
patching file Gui/mplayer/gtk/playlist_create.h
patching file Gui/mplayer/gtk/sb.c
patching file Gui/mplayer/gtk/sb.h
patching file Gui/mplayer/gtk/support.h
patching file Gui/mplayer/gtk/url.c
patching file Gui/mplayer/pixmaps/about.xpm
patching file Gui/mplayer/play.c
patching file Gui/mplayer/widgets.c
Hunk #3 succeeded at 68 with fuzz 1.
patching file Gui/mplayer/widgets.h
patching file configure
Hunk #1 succeeded at 150 (offset 1 line).
Hunk #2 succeeded at 359 (offset 25 lines).
Hunk #3 succeeded at 1833 (offset 191 lines).
Hunk #4 succeeded at 6408 (offset 569 lines).
Hunk #5 succeeded at 6454 (offset 569 lines).
Hunk #6 succeeded at 6864 with fuzz 1 (offset 621 lines)
```[/QUOTE]

[QUOTE=bored2k]I recommend building from CVS, but if you want to use the .7PRE, I've never used the patch :/.[/QUOTE]

---> [http://www.ubuntuforums.org/showthread.php?t=83595](http://www.ubuntuforums.org/showthread.php?t=83595)

---

### Post by Hellaxe on 2005-11-16
Hello people:
I'm having a problem compiling Mplayer. I've followed the how-to but now just at the beggining i've this:
```
Unknown parameter: --enable-gtk2 
```

I've installed the gtk2 libs that i thought it would work but nothing happens.
Could you tell me what are the libs that i need?

Thank you

---

### Post by christooss on 2005-11-16
./configure --enable-gui --enable-largefiles --enable-menu is in cvs howto build

[http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100](http://www.ubuntuforums.org/showpost.php?p=439490&postcount=100)

---

### Post by Turambar on 2005-11-16
If you have the CVS version, it already uses GTK2, and the switch is unnecessary. Plus I think you may want to use the --enable-gui switch.

EDIT: too slow

---

### Post by Folken on 2005-11-16
[http://seethrubuntu.ath.cx/MPlayer-1.0pre7-gtk2.patch.bz2](http://seethrubuntu.ath.cx/MPlayer-1.0pre7-gtk2.patch.bz2) link is broken.

---

### Post by johannes on 2005-11-16
Here is a new link for [MPlayer-1.0pre7-gtk2.patch]("http://phaeronix.net/files/MPlayer-1.0pre7-gtk2.patch").

---

### Post by Hellaxe on 2005-11-16
[QUOTE=Turambar]If you have the CVS version, it already uses GTK2, and the switch is unnecessary. Plus I think you may want to use the --enable-gui switch.

EDIT: too slow[/QUOTE]

If this is an answer to my post, Thanks.

But i'm not using the cvs.
i'm using the downloads from the mplayer site.

---

### Post by Hellaxe on 2005-11-17
Sorry again but i have some doubts.
If i compile through CVS there might be a package or program not very stable,, right?
So if i want to have a very stable version i should compile using that patch, right?

I´ve readed (i think that´s the right past form of the verb read if not sorry i don´t remember) all thread and could find the solution for the:

**[COLOR="DarkRed"]Unknown parameter: --enable-gtk2[/COLOR]**

Can you tell me a solution for this one? I'm a little noob so i'm in the dark about CVS. 

Thanks.

---

### Post by bored2k on 2005-11-17
[QUOTE=Hellaxe]Sorry again but i have some doubts.
If i compile through CVS there might be a package or program not very stable,, right?
So if i want to have a very stable version i should compile using that patch, right?

I´ve readed (i think that´s the right past form of the verb read if not sorry i don´t remember) all thread and could find the solution for the:

**[COLOR="DarkRed"]Unknown parameter: --enable-gtk2[/COLOR]**

Can you tell me a solution for this one? I'm a little noob so i'm in the dark about CVS. 

Thanks.[/QUOTE]
The CVS is not unstable at all. The CVS guide I put up is very easy to follow.

---

### Post by PenguinZdravko on 2005-11-29
penguinzdravko@ghostwheel:~/MPlayer-1.0pre7try2$ sudo checkinstall

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
make[1]: Entering directory `/home/penguinzdravko/MPlayer-1.0pre7try2/libdha'
mkdir -p /usr/local/lib
install -m 755 -s -p libdha.so.1.0  /usr/local/lib/libdha.so.1.0
rm -f /usr/local/lib/libdha.so
ln -sf libdha.so.1.0  /usr/local/lib/libdha.so.1
ldconfig
make[1]: Leaving directory `/home/penguinzdravko/MPlayer-1.0pre7try2/libdha'
make[1]: Entering directory `/home/penguinzdravko/MPlayer-1.0pre7try2/vidix'
make[2]: Entering directory `/home/penguinzdravko/MPlayer-1.0pre7try2/vidix/drivers'
mkdir -p /usr/local/lib/mplayer/vidix
install -m 755 -s -p *.so /usr/local/lib/mplayer/vidix
make[2]: Leaving directory `/home/penguinzdravko/MPlayer-1.0pre7try2/vidix/drivers'
make[1]: Leaving directory `/home/penguinzdravko/MPlayer-1.0pre7try2/vidix'
if test ! -d /usr/local/bin ; then mkdir -p /usr/local/bin ; fi
install -m 755 -s mplayer /usr/local/bin/mplayer
ln -sf mplayer /usr/local/bin/gmplayer
if test ! -d /usr/local/man/man1 ; then mkdir -p /usr/local/man/man1; fi
mkdir: cannot create directory `/usr/local/man': File exists
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.

Why???

---

### Post by mutenroid on 2005-11-30
Few days ago, i compile mplayer-plugin 3.15 and install succesfully!! (with an existing post in the forums). Quicktime videos works great :p 

Now, with the new firefox 1.5, i'll need to compile mplayer and mplayer-plugin  again to work????

Thanks

---

### Post by christooss on 2005-11-30
No need to compile again you just have to link plugin folder to your new firefox. Check Firefox install Howto

---

### Post by Axios on 2005-12-04
Could one of you gurus compile into a deb? perhaps make a repository, so that I don't have to get my hands all dirty ? ;)

I would love having a gtk2 interface on mplayer, but don't have the time or patience to compile it my self.

Hope gtk2 in mplayer gets standard.

---

### Post by vvlaw on 2005-12-04
[QUOTE=NeoChaosX]You want to install libxv-dev to get xv support compiled.[/QUOTE]

but i have no alsa option ,it doesn't support the alsa drivers.so what need i to install ?

only just to need sudo apt install? 

install what? :)

---

### Post by manicka on 2005-12-04
[QUOTE=Axios]Could one of you gurus compile into a deb? perhaps make a repository, so that I don't have to get my hands all dirty ? ;)

I would love having a gtk2 interface on mplayer, but don't have the time or patience to compile it my self.

Hope gtk2 in mplayer gets standard.[/QUOTE]

bored2k's deb is here 
[http://rapidshare.de/files/6588394/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6588394/mplayer_1.0cvs_i386.deb.html)

---

### Post by bored2k on 2005-12-04
[QUOTE=manicka]bored2k's deb is here 
[http://rapidshare.de/files/6588394/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/6588394/mplayer_1.0cvs_i386.deb.html)[/QUOTE]
Updated package: [http://rapidshare.de/files/8409074/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/8409074/mplayer_1.0cvs_i386.deb.html)

Requirement:  [http://rapidshare.de/files/8409074/mplayer_1.0cvs_i386.deb.html](http://rapidshare.de/files/8409074/mplayer_1.0cvs_i386.deb.html)

---

### Post by smeager on 2005-12-05
I must say thank you for all you've done. It works great and looks great now that its using GTK2. Thanks again.

---

### Post by NeoChaosX on 2005-12-05
```
gmplayer: error while loading shared libraries: libdivxdecore.so.0: cannot open shared object file: No such file or directory
```
I got this message trying to run your latest build, bored2k. What package do I need to install to fix this, because apt is saying there's not libdivxdecore0 package to install.

---

### Post by NeoChaosX on 2005-12-05
[QUOTE=vvlaw]but i have no alsa option ,it doesn't support the alsa drivers.so what need i to install ?

only just to need sudo apt install? 

install what? :)[/QUOTE]
libasound2-dev is the package you want to install. Then, just recompile your mplayer again.

---

### Post by PsychoTrauma on 2005-12-05
[QUOTE=NeoChaosX]```
gmplayer: error while loading shared libraries: libdivxdecore.so.0: cannot open shared object file: No such file or directory
```
I got this message trying to run your latest build, bored2k. What package do I need to install to fix this, because apt is saying there's not libdivxdecore0 package to install.[/QUOTE]

you need to get the divx4linux package from the divx site.
[http://www.divx.com/divx/linux/]("http://www.divx.com/divx/linux/")

---

### Post by bored2k on 2005-12-05
[QUOTE=PsychoTrauma]you need to get the divx4linux package from the divx site.
[http://www.divx.com/divx/linux/]("http://www.divx.com/divx/linux/")[/QUOTE]
Exactly. I compiled it using divx5linux which is arguably better than divx4linux or opendivx.

---

### Post by Treviño on 2005-12-05
Hello, I'd like to compile mplayer with a gtk2 gui, but I can't download the patch file MPlayer-1.0pre7-gtk2.patch.bz2. I get a dns error. Is there a mirror for this file?
I'm sorry if it has just been posted, but my searches ended with no success.

Bye & Thanks!

---

### Post by dabeej on 2005-12-08
[QUOTE=Treviño]Hello, I'd like to compile mplayer with a gtk2 gui, but I can't download the patch file MPlayer-1.0pre7-gtk2.patch.bz2. I get a dns error. Is there a mirror for this file?
I'm sorry if it has just been posted, but my searches ended with no success.

Bye & Thanks![/QUOTE]


The answer to that is:

[QUOTE=bored2k][http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2](http://www.win.net/~ardneh/patches/mplayer1.0pre5-gtk2-20040730.patch.bz2)[/QUOTE]

---

### Post by Treviño on 2005-12-08
Many thanks man! :)

---

### Post by Haegin on 2005-12-09
Hmm, I have installed the latest deb and it just cuts out with an Illegal Instruction error when I try to run "gmplayer". This doesn't seem to be working so how do I get back to the original mplayer as it seems to have overwritten what I can download from the normal breezy repos. How do I get access to the old mplayer package? It may be ugly but it works...

This is the full error when I run "gmplayer"
```

MPlayer dev-CVS-051031-10:30-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

```

---

### Post by Sargonmetal on 2005-12-15
[QUOTE=seethru]sudo apt-get install libx11-dev

Can't believe I've missed these, thats what I get for assuming...lol[/QUOTE]

I still get the same error: 

> Error: X11 support required for GUI compilation

I'm stuck on this, I haven't found any solution. I will appreciate any help, I'm newbie on this!

Thanks!

---

### Post by lucas on 2005-12-15
[QUOTE=Human Prototype]Hmm, I have installed the latest deb and it just cuts out with an Illegal Instruction error when I try to run "gmplayer". This doesn't seem to be working so how do I get back to the original mplayer as it seems to have overwritten what I can download from the normal breezy repos. How do I get access to the old mplayer package? It may be ugly but it works...

This is the full error when I run "gmplayer"
```

MPlayer dev-CVS-051031-10:30-4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

```[/QUOTE]

I get the same error, this is beacuse its compiled with SSE2, which we don't have. To get the old mplayer back remove deb you installed with **sudo apt-get remove mplayer** then install the repo version with **sudo apt-get install mplayer-586**.

---

### Post by Patrol on 2005-12-15
Hello guys !
This how-to seems to be great, but I have got a problem...

When I type > make && sudo checkinstall, I get an error : no *config.mak* found... I must make a mistake...

---

### Post by abyssspecter on 2005-12-25
okay, im being a noob, but, i can get the how-to aboput halfway, but then, when it says:

> bzcat ../MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1

i mess up. i read where it says to do:

> bzcat /MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1

or

bzcat MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1

and neither work. can someone please help.

---

### Post by cybrjackle on 2005-12-25
```

 bzcat ../MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1

```

Your missing the **..** in your example, the **..** tells it to look in the dir before it.

---

### Post by abyssspecter on 2005-12-25
> specter@Specter:~/MPlayer-1.0pre7try2$ bzcat ../MPlayer-1.0pre7-gtk2.patch.bz2 |patch -p1
bzcat: Can't open input file ../MPlayer-1.0pre7-gtk2.patch.bz2: No such file or directory.


thats what i got this time.

---

### Post by egon spengler on 2005-12-28
[QUOTE=abyssspecter]thats what i got this time.[/QUOTE]
It looks like it cant find the file "MPlayer-1.0pre7-gtk2.patch.bz2"

Have you moved or deleted this file?

---

### Post by fabs0028 on 2005-12-28
Well i have it on my computer so i include it in my post for all that can't find the patch.

---

### Post by Fredde on 2006-05-12
~/MPlayer-1.0pre7try2$ make && sudo checkinstall
config.mak:23: *** separator saknas.  Stannar.

edit: I also need 'MPlayer-1.0pre7-gtk2.patch.bz2' file.The error might accour because I used uploaded files from variouse users.

---

### Post by octoberdan on 2007-04-14
This thread needs to be updated to match their new repository (now svn!)

Install svn:
```
sudo apt-get install subversion
```
Get the source:
```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk/ mplayer
```
To update:
```
svn up
```

---

