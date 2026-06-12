---
title: "Compiling MPlayer on a fresh Dapper install, wmv, mp4, etc."
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by sapo on 2006-06-03
Well, i just installed dapper here and while trying to compile mplayer i noticed that the cvs is down (bored2k said that they are migrating to svn) anyway, i cant stay without mplayer with mp4, and other codecs support.. so i m making this first "scratch" of a howto, so people can just read it instead of solving the problems i had to solve.


[COLOR="Blue"][SIZE="6"]GETTING THE DEPENDENCIES[/SIZE][/COLOR]

First we need to enable the universe and multiverse repos, if you are lazy, just replace the contents of the /etc/apt/sources.list with this:

```

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

After saving the new sources.list:

```
sudo apt-get update
```

After the update just paste it on the terminal:

```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion
```

It will download a LOT of stuff, dont be scared its just about 47MB.


[COLOR="Blue"][SIZE="6"]GETTING THE CODECS[/SIZE][/COLOR]

Now you need to get the codecs from here:

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Grab the Essential codecs package

To install the Win32 codecs, extract the w32codecs you can double click the package and select extract or in the terminal type:

```
tar xjvf essential-20060501.tar.bz2
```

And after that enter the directory you have extracted the package and remove the .deb package rm *.deb on a terminal should do the trick :p

Still inside the essential codecs dir you have just extracted, do it:

```
sudo mkdir /usr/lib/win32
sudo cp * /usr/lib/win32
```

[COLOR="Blue"][SIZE="6"]x264 CODEC[/SIZE][/COLOR]

Do it on a terminal:
```

svn co svn://svn.videolan.org/x264/trunk x264
cd x264
./configure
make
sudo make install
cd ..

```

[COLOR="Blue"][SIZE="6"]GETTING AND COMPILING MPLAYER FROM SVN[/SIZE][/COLOR]

Now you just have to extract the mplayer package and compile it, to do it

In a terminal go to the directory you have just downloaded the Mplayer Package and type the following:

```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer

```

For Dapper Drake use:
```

./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid --enable-x264

```

In Edgy Eft use:
```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --win32codecsdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa
```

And the, compile and install ;)
```

make
sudo make install
```

Now you can try it out using mplayer on the command line, to use the it with the GUI you need to run gmplayer, but first you need to install a default skin.


[SIZE="6"][COLOR="Blue"]INSTALLING A SKIN[/COLOR][/SIZE]

Now the last step is install a Skin:

Go to: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) and download a skin, Blue is the Default, but i like the QuickSilver skin :twisted: 

Download, extract the contents of the skin package and rename the extracted folder to **default**

If you downloaded the Blue Skin, do this:
```

tar xjvf Blue-1.5.tar.bz2
mv Blue default
sudo cp -R default/ /usr/share/mplayer/Skin/
```


[COLOR="Blue"][SIZE="5"]SPECIAL THANKS[/SIZE][/COLOR]
Special thanx to bored2k for his [Mplayer Howto](http://ubuntuforums.org/showthread.php?t=85190) that i ve always used, and the help he gave me on the gtalk, i love you biba :mrgreen:



[i]**Updates:**
Updated the links
Now mplayer fom SVN compiles with GCC 4.0 so i updated the commands and the apt-get command to not download gcc-3.4 anymore.
x264 is working now with the SVN version![/i]

---

### Post by philetus on 2006-06-03
Did it work for you?

---

### Post by zahidism on 2006-06-03
so, being the noob that i am, i installed m-player using apt get.  is compiling it that much better?  i would really love to reap the best quality for my xvids etc

---

### Post by daschl on 2006-06-04
[QUOTE=zahidism]so, being the noob that i am, i installed m-player using apt get.  is compiling it that much better?  i would really love to reap the best quality for my xvids etc[/QUOTE]
well the point is, that when you install mplayer with apt-get you install it from an official repository and the guys from ubuntu have troubles with the law when they put some codecs in.

if you compile it for yourself you may put the codecs in mplayer which you prefer most

btw: mplayer > * ;)

---

### Post by buildid on 2006-06-04
i did compile but get this message :

gmplayer: error while loading shared libraries: libjack-0.80.0.so.0: cannot open shared object file:

any idears ?

---

### Post by sapo on 2006-06-04
[QUOTE=buildid]i did compile but get this message :

gmplayer: error while loading shared libraries: libjack-0.80.0.so.0: cannot open shared object file:

any idears ?[/QUOTE]
Thats weird, did you install all dependencies? are you running a flesh dapper install or did you upgrade from breezy?

btw, this lib is on the breezy reps but it seens that dapper doesnt have it, i ll try finding a link so you can install it.

---

### Post by shaul26 on 2006-06-04
Hey, thanks for the howto :)

About the x264 - I remember that in some post (can't find it) someone put instructions to change something in "codecs.conf" (i'm not sure about the file name) and when I did those instructions I had h264 decoding... and very good, more then in totem...

Hope I've helped..and sorry for my english, I'm not a native speaker..

---

### Post by geearf on 2006-06-04
I have no problem using ffmpeg  and mplayer last cvs version with x264.

---

### Post by sapo on 2006-06-04
[QUOTE=geearf]I have no problem using ffmpeg  and mplayer last cvs version with x264.[/QUOTE]
The x264 in the cvs works fine, but currently the mplayer cvs is down, they are migrating to svn.

---

### Post by geearf on 2006-06-04
I know, though ffmpeg is back.

---

### Post by buildid on 2006-06-04
[QUOTE=sapo]Thats weird, did you install all dependencies? are you running a flesh dapper install or did you upgrade from breezy?

btw, this lib is on the breezy reps but it seens that dapper doesnt have it, i ll try finding a link so you can install it.[/QUOTE]


upgrade from breezy

---

### Post by angkor on 2006-06-04
Very nice howto, just what I was looking for. Worked flawlessly

I have a two questions though.

I made a .deb (never made a .deb before :))that I want to install. Do I use fakeroot in stead of 'make install' or after make install?

Secondly when I run mplayer I get this warning:

```
Compiled with runtime CPU detection - WARNING - this is not optimal!
To get best performance, recompile MPlayer with --disable-runtime-cpudetection.
```

What is that about?


Edit: I installed the .deb (got that fakeroot part from the bored2k howto) but the update manager wanted me to 'upgrade' to the repo version so I pinned and locked the compiled version.

---

### Post by sc30317 on 2006-06-05
How do you get MPlayer to be the deafult player for all videos?

---

### Post by angkor on 2006-06-05
[QUOTE=sc30317]How do you get MPlayer to be the deafult player for all videos?[/QUOTE]

You need to right-click one of your videos (e.g. an .avi) go to Properties-> Open with... and select mplayer. 

Since I don't know of a way to do this for all video formats at once I repeat this procedure for every format I want played by mplayer.

---

### Post by lostdata on 2006-06-06
i installed the quicksilver skin and i get the following error...

New_Face failed, maybe the font path is wrong
please supply the text font file
/mplayer/sbfont.ttf

---

### Post by mtn on 2006-06-07
Does this work for AMD64? I have had big problems with "make" and "make install". I gat tons of lines like this...

pe_image.c:81: warning: cast to pointer from integer of different size

and this about half way through loads of lines...

wine/winnt.h:625:2: #error You need to define a CONTEXT for your CPU

I'm new to Linux so have no idea what this means?

All the dependancies seem to install fine. Checked again and they all say "latest version"

---

### Post by micke1m on 2006-06-08
I use amd64 and got the same problem as mtn.

---

### Post by mtn on 2006-06-08
I got Mplayer and libdvdcss2 (for playing encrypted DVDs) working on Ubuntu 6.06 AMD64. Here is how I did it...

Mplayer
I added these repositories in Synaptic. I'm not sure now which one/s I needed  as I tried all of them and it didn't seem to work until I noticed the check boxes in Synaptic "Show unsupported applications" and " Show commercial application" after ticking these Mplayer was available for install and worked like a charm.

I also had to disable a couple repositories (see below)

REPOSITORIES I ADDED IN SYNAPTIC
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multivers

# REPOSITORIES THAT I HAD TO DISABLE
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

[EDIT] This is nonsense. I think it might have got Alien working but this is how I got WINE going: [http://www.ubuntuforums.org/showthread.php?t=185557&highlight=wine+64](http://www.ubuntuforums.org/showthread.php?t=185557&highlight=wine+64)

JUST OUT OF INTEREST I ADDED THIS REPOSITORY TO GET Alien AND WINE FOR AMD64
deb [http://brcha.no-ip.org/apt/](http://brcha.no-ip.org/apt/) unstable/
[END EDIT]

libdvdcss2
To get DVDs working I followed these instructions here
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
under the heading "Playing DVDs" again worked great for me, I can now watch encrypted DVDs no problem.

Hope this helps someone in the future!

P.S. It dose not look like the Win32codec pack works for AMD64 yet! I didn't manage to install that though I have no problem playing most AVI and MPEG movies.

---

### Post by Myndmelder on 2006-06-09
...

I followed your instructions, but when I click on mplayer it doesn't start.
A small window pops up for a split second and that is it...

---

### Post by angkor on 2006-06-09
[QUOTE=Myndmelder]...

I followed your instructions, but when I click on mplayer it doesn't start.
A small window pops up for a split second and that is it...[/QUOTE]

what happens if you start mplayer from the command line?

```
mplayer {path/to/video/file}
```

---

### Post by Myndmelder on 2006-06-09
This is what I got...

```

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

```

---

### Post by angkor on 2006-06-09
[QUOTE=Myndmelder]This is what I got...

```

Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

```[/QUOTE]

Is that all, no video playback at all? Cause that error will not stop playback.

For that error read this thread. It won't fix it if you're unable to play video's though.

[http://www.ubuntuforums.org/showthread.php?t=187885&page=4](http://www.ubuntuforums.org/showthread.php?t=187885&page=4)

---

### Post by Myndmelder on 2006-06-09
Nada, nothing, zilch, zero...

No video...:confused:

---

### Post by Myndmelder on 2006-06-10
Okay.
I managed to fix my problem, but I seem to have the same problem as lostdata:

```

New_Face failed, maybe the font path is wrong
please supply the text font file
/mplayer/sbfont.ttf

```

Is there a solution?

---

### Post by nischg on 2006-06-12
[QUOTE=Myndmelder]Okay.
I managed to fix my problem, but I seem to have the same problem as lostdata:

```

New_Face failed, maybe the font path is wrong
please supply the text font file
/mplayer/sbfont.ttf

```

Is there a solution?[/QUOTE]

sudo apt-get install mplayer-fonts

---

### Post by helpdeskdan on 2006-06-12
Actually, what you want to do is download the Arial Western font from the Mplayer page.  [http://www.mplayerhq.hu/design7/dload.html#fonts]("http://www.mplayerhq.hu/design7/dload.html#fonts")

Then, as root (or sudo all these if that's your style)

tar -jvxf font-arial-iso-8859-1.tar.bz2 -C /usr/share/mplayer/font
chown -v -R root:root /usr/share/mplayer/font
cd /usr/share/mplayer/font
ln -v -sf font-arial-iso-8859-1/font-arial-[font size]-iso-8859-1/* .

This worked great for me. A thanks to linuxfromscratch.org for these instructions, which I slightly modified. 

A special thanks to sapo for posting these excellent instructions!  I'd like to see this all up on the wiki!

---

### Post by helpdeskdan on 2006-06-13
I just installed the mplayer plugin.  Combined with my compiled mplayer, it works better than anything I've ever seen on linux. 

Very quick/dirty  instructions (after you have downloaded the source):
1. sudo apt-get firefox-dev (will also install libnss-dev, libnspr-dev)
 
2.  Get gecko-sdk [http://developer.mozilla.org/en/docs/Gecko_SDK#Downloading]("http://developer.mozilla.org/en/docs/Gecko_SDK#Downloading")

3.  tar -xzf it in your home dir (for lack of not being sure where to put it)

4.  ./configure --with-gecko-sdk=~/gecko-sdk
(If I were smarter, I could tell you the proper way to do this, but this works)

5.  make

6.  su or sudo:
cp mplayerplug-in*.so /usr/lib/mozilla-firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components
Just to be sure, I also did:
cp mplayerplug-in*.so /usr/lib/firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/firefox/components
(not sure why there are two directories.  Again, if I were smarter...)

7.  Restart firefox and enjoy!

Perhaps somebody may find this information usefull; will be happy to clarify vague details if needed.

---

### Post by psychicdragon on 2006-06-13
Great guide sapo. :KS 

I'll have to get on this when I have a bit of time.

---

### Post by DagMan on 2006-06-13
[QUOTE=angkor]```
Compiled with runtime CPU detection - WARNING - this is not optimal!
To get best performance, recompile MPlayer with --disable-runtime-cpudetection.
```

What is that about?
[/QUOTE]
Where the instructions, in the first post and just before the "make" command, say this
```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-external-faad --enable-menu --enable-tv-v4l --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid --disable-divx4linux
```
add also "--disable-runtime-cpudetection" to it so it says this:
```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-external-faad --enable-menu --enable-tv-v4l --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid --disable-divx4linux --disable-runtime-cpudetection
```
I'm glad I read your post because I wouldn't have noticed it until later and would have been frustrated with my install when I finally did later on.

Funny thing, I had been using the thing of hitting the queue button in acid rip then copying to a shell script and editing out the little ":" and did so again after this install but just now also found when encoding an xvid file, mencoder now finds the syntax valid so this **has made acidrip work for me again.**  I didn't know that I really wanted it working that badly until it did.  Thanks sapo!

I copied over the mplayer and mencoder files manually because it didn't seem to want to install them over the old ones but just as well and the package manager isn't complaining at all, since it doesn't know, when usually there would be dependancy problems... for things using mencoder when I did this on Breezy anyway.

Also, I don't know if I'll find it a problem later on or not but so far it hasn't been. There was something removed at the beginning with all the things installed.  I copied and pasted it to look at reinstalling it when the build was done and I did.  So far so good with it.  I don't remember what the package was now though.. an alsa library I think.

---

### Post by Peturrr on 2006-06-13
Any reason for not compiling with GCC 4 but with 3.4?

Also, this compiles with a very awful looking menus. The pre-compiled dapper one comes with a gtk2 menu which looks WAY better.

---

### Post by sapo on 2006-06-13
[QUOTE=Peturrr]Any reason for not compiling with GCC 4 but with 3.4?

Also, this compiles with a very awful looking menus. The pre-compiled dapper one comes with a gtk2 menu which looks WAY better.[/QUOTE]
The only reason is that MPlayer REFUSES to compile with GCC 4

---

### Post by angkor on 2006-06-13
[QUOTE=DagMan]
add also "--disable-runtime-cpudetection" to it so it says this:[/QUOTE]

@Sapo, any reason you didn't include this parameter? Should I recompile it for better playback?

---

### Post by Peturrr on 2006-06-14
MPlayer v1.0pre8 has been released. 
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

---

### Post by nrwilk on 2006-06-17
Thanks so much, Sapo, for the excellent howto!

I'd been using bored2k's howto for breezy too.

I just wanted to say a couple things:

1.  I, like Peturrr, also had terrible looking menus and stuff in mplayer, but after installing mplayer-fonts from the repositories, it was fixed.  I suggest you include this in the list of dependencies to download.

2.  You might want to include a link to the latest mplayer-mozilla plugin deb for those who want embedded mplayer capabilities in firefox and mozilla.

Also, a quick compiling question.

Say they release a new version ( like they have with v1.0pre8 ).  If go through this process again with the new version, must I do something to first get rid of the old version, or will make install replace the old version for me?

nrwilk

---

### Post by sapo on 2006-06-17
[QUOTE=nrwilk]Thanks so much, Sapo, for the excellent howto!

I'd been using bored2k's howto for breezy too.

I just wanted to say a couple things:

1.  I, like Peturrr, also had terrible looking menus and stuff in mplayer, but after installing mplayer-fonts from the repositories, it was fixed.  I suggest you include this in the list of dependencies to download.

2.  You might want to include a link to the latest mplayer-mozilla plugin deb for those who want embedded mplayer capabilities in firefox and mozilla.

Also, a quick compiling question.

Say they release a new version (like they have with v1.0pre8).  If go through this process again with the new version, must I do something to first get rid of the old version, or will make install replace the old version for me?

nrwilk[/QUOTE]
Thanx for the tips, i ll update the howto.

And about your question, make install should do the trick, at least i dont uninstall the previous version when this happens, i just do a make install again.

---

### Post by nrwilk on 2006-06-17
Thank you!

---

### Post by DagMan on 2006-06-18
[QUOTE=sapo]
**Note: x264 codec isnt working, but i m trying to figure out how to make it work, any help is welcome.**[/QUOTE]
Hi sapo.
I was able to get this going.  The main thing was to apt-get nasm in order for x264 to compile.  

Also, I don't know if it would be relevant, but this was a compile of the newest Mplayer as per the link above (the one in your first post is broken now btw).  Additionally, in a past compile I couldn't get it to -work unless I compiled x264 and Mplayer in the same terminal without closing it out, I wasn't able to find the instructions in this newer version of mplayer to see how to set the path to the codec and didn't much care since ./configure found it by itself though it may be important to include what needs to be passed to it.. so reading the documentation will be helpfull to clear that up.

The following are things I did that are most likely irrelevant but that I tried before looking at the compile errror and realising that I was missing the nasm package:
-Exported gcc to what the Mplayer compile is in your guide.
-Exported CFLAGS and CXXFLAGS to nothing.
-Had an older version than the latest of x264 by the time I had figured out the error and compiled that.



The newer version of Mplayer, as posted shortly above, doesn't work with my acidrip btw.  The last version, in the how to, did.


Edit: It appears now that the newer version is detecting it and the older one cannot detect it even when it's told where to look

---

### Post by sapo on 2006-06-18
[QUOTE=DagMan]Hi sapo.
I was able to get this going.  The main thing was to apt-get nasm in order for x264 to compile.  

Also, I don't know if it would be relevant, but this was a compile of the newest Mplayer as per the link above (the one in your first post is broken now btw).  Additionally, in a past compile I couldn't get it to -work unless I compiled x264 and Mplayer in the same terminal without closing it out, I wasn't able to find the instructions in this newer version of mplayer to see how to set the path to the codec and didn't much care since ./configure found it by itself though it may be important to include what needs to be passed to it.. so reading the documentation will be helpfull to clear that up.

The following are things I did that are most likely irrelevant but that I tried before looking at the compile errror and realising that I was missing the nasm package:
-Exported gcc to what the Mplayer compile is in your guide.
-Exported CFLAGS and CXXFLAGS to nothing.
-Had an older version than the latest of x264 by the time I had figured out the error and compiled that.



The newer version of Mplayer, as posted shortly above, doesn't work with my acidrip btw.  The last version, in the how to, did.


Edit: It appears now that the newer version is detecting it and the older one cannot detect it even when it's told where to look[/QUOTE]
Thanx,

I tried to download and compile x264 from svn but it wasnt working with the pre7, i had nasm installed, it compiled but the mplayer didnt recognized it even forcing with --enable-x264.

But now i downloaded the pre8 version, compiled the x264 codec from svn, and it worked on the first try!

btw, i alread added it to the howto!

---

### Post by sapo on 2006-06-18
Thanx for all the help fellows!

I updated the howto, now it works with SVN!

---

### Post by DagMan on 2006-06-18
I might have done something that previously removed it, but I had to add the subversion package to download like that.

Thanks again for writing the how to.

---

### Post by sapo on 2006-06-18
[QUOTE=DagMan]I might have done something that previously removed it, but I had to add the subversion package to download like that.

Thanks again for writing the how to.[/QUOTE]
Sorry, my bad, i forgot to add the subversion on the apt-get command, thanx!

---

### Post by cor2y on 2006-06-18
hey i need some help everything gpes fine up until i type make
i get this error

Makefile:7: config.mak: No such file or directory
make: *** No rule to make target `config.mak'.  Stop

why is it happening?
since its svn source is there something else to be done?
saw you had to do that for vlc when compiling.

---

### Post by DagMan on 2006-06-18
I think you've just forgotten to copy and paste the line above it in.
```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-menu --enable-tv-v4l --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid --disable-divx4linux --enable-x264
```

---

### Post by cor2y on 2006-06-19
ok i got that fixed now "make" and "sudo make install" works.

However after all of that any attempt to launch mplayer or gmplayer results in this NEW error.

gmplayer: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory

Any ideas?
It looks like something to do with libiconv which it recognised during ./configure and that file libiconv.so.2 is a linked file and not a real one its linked to libiconv.so.2.2.0

---

### Post by DagMan on 2006-06-19
Did you install a skin.  I don't know if that's it but if so and if it's not anoying to be a little dirty:

If you stll have the folder you built in you can try what I did which was install mplayer-fonts and mplayer-skins through apt or synaptic.  That will pull in mplayer as well if you haven't installed it yet and will overwrite what you've built.  Then in a terminal inside the mplayer directory where you built, if make install doesn't copy it over properly you can sudo cp mencoder $(which mencoder) and sudo cp mplayer $(which mplayer).  I did this because it handles the skin, fonts and dependant packages are aware of it being there, so all I had to do was build it and didn't worry about the skin part.

I think it's less dirty for the reason that dependant packages won't pull in and overwrite the install.

---

### Post by crossev on 2006-06-21
Hey all.  I have followed the how to for installing mplayer and everything installed ok.  However when I play a video using gmplayer or right clicking on the video it opens and I only hear sound.  It does not play the picture.  Any possible solutions to this?

---

### Post by sapo on 2006-06-21
[QUOTE=crossev]Hey all.  I have followed the how to for installing mplayer and everything installed ok.  However when I play a video using gmplayer or right clicking on the video it opens and I only hear sound.  It does not play the picture.  Any possible solutions to this?[/QUOTE]
Try running mplayer your_video_filename.avi on a terminal, and paste the output here.. it for sure will have the reason why your video isnt showing up.

---

### Post by crossev on 2006-06-21
$ gmplayer home.mpg
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.



91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/crossev/Desktop/home.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  320x240  (aspect 1)  29.970 fps  550.0 kbps (68.8 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 48.0 kbit/3.12% (ratio: 6000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 320 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12
A:   8.8 V:   8.8 A-V:  0.006 ct:  0.207 243/243  1%  2%  0.2% 8 0
  =====  PAUSE  =====


This is the output from trying to run gmplayer on an mpeg called home.  I get the sound but I do not get the video.


Thanks

---

### Post by blackjack6.21.91 on 2006-06-29
Really wierd problems compiling mplayer.  Running ./configure (with the parameters in the how-to) gave a great return until the end.  Here's the good part of the return:
> Config files successfully generated by ./configure !

  Install prefix: /usr
  Data directory: /usr/share/mplayer
  Config direct.: /etc/mplayer

  Byte order: little-endian
  Optimizing for: pentium-m mmx mmxext sse sse2 mtrr

  Languages:
    Messages/GUI: en
    Manual pages:  en

  Enabled optional drivers:
    Input: ftp network tv-v4l2 tv-v4l tv mpdvdkit2 vcd dvb
    Codecs: qtx x264 libavcodec real win32 faad2 faac musepack libmpeg2 libdts l iba52 mp3lib libtheora tremor(internal) libmad
    Audio output: alsa esd oss nas sdl mpegpes(dvb)
    Video output: xvidix cvidix sdl md5sum pnm jpeg png mpegpes(dvb) fbdev caca opengl xv x11 xover tga
    Audio filters:
  Disabled optional drivers:
    Input: vstream live555 cdda dvdnav dvdread smb
    Codecs: opendivx xvid libdv amr_wb amr_nb xanim speex twolame toolame liblzo  gif
    Audio output: sun openal jack polyp arts dxr2
    Video output: winvidix bl zr zr2 dxr3 dxr2 vesa gif89a svga aa ggi xmga mga dga xvmc directfb tdfx_vid s3fb tdfxfb 3dfx
    Audio filters: ladspa


And then JUST UNDER IT is:

> 'config.h' and 'config.mak' contain your configuration options.
Note: If you alter theses files (for instance CFLAGS) MPlayer may no longer
      compile *** DO NOT REPORT BUGS if you tweak these files ***

'make' will now compile MPlayer and 'make install' will install it.
Note: On non-Linux systems you might need to use 'gmake' instead of 'make'.

Please check mtrr settings at /proc/mtrr (see DOCS/HTML/en/video.html#mtrr)


Check configure.log if you wonder why an autodetection failed (check whether
the development headers/packages are installed).
Do not report compilation errors if you used any of the --enable-* options
(except --enable-gui and maybe --enable-debug).

If you suspect a bug, please read DOCS/HTML/en/bugreports.html.


If anyone knows a solution to this problem, give me a holler!  Thanks for the howto!

---

### Post by sapo on 2006-06-29
[QUOTE=blackjack6.21.91]Really wierd problems compiling mplayer.  Running ./configure (with the parameters in the how-to) gave a great return until the end.  Here's the good part of the return:


And then JUST UNDER IT is:



If anyone knows a solution to this problem, give me a holler!  Thanks for the howto![/QUOTE]
I dont see any problems in your output, this is the default message, you just have to type: make and then make install

---

### Post by blackjack6.21.91 on 2006-06-29
Gotcha.  I remember trying to just make after that and it failing..  but it worked this time.  Probably just a stupid error on my part.  But under installing a skin where you say to do this:
> sudo cp -R default/ /usr/share/mplayer/Skin/
I think you're supposed to be doing this:
> sudo cp -R default/ /usr/share/mplayer/skins/
or at least that's what it was for me. The "Skin" folder didn't exist.  

Also, when I launch mplayer I get an error:
> New_Face failed.  Maybe the font path is wrong.  Please supply the text font file )~/.mplayer/subfont.ttf
Anyway thanks again for the howto.  Should I just install the mplayer plugin for mozilla in the repos or what??

peace,
blackjack

---

### Post by originaluoc on 2006-06-30
Hello guys from a Dapper 6.06 user.

Has anybody succesfully installed the tovid 0.25? I go through all the process and when I had to strike ./setup.sh, I am asked for root password, and when I put it, it appears authentication failed.

I follow the instructions from here [http://tovid.berlios.de/en/install.html](http://tovid.berlios.de/en/install.html) 

Thank you for your time.

---

### Post by Barts_706 on 2006-07-01
Hi,

I tried to install MPlayer in the way you described, and that is what I get at the compilation stage :

```
mplayer/gtk/menu.c: In function 'create_PopUpMenu':
mplayer/gtk/menu.c:403: error: 'MSGTR_MENU_AboutMPlayer' undeclared (first use in this function)
mplayer/gtk/menu.c:403: error: (Each undeclared identifier is reported only oncemplayer/gtk/menu.c:403: error: for each function it appears in.)
mplayer/gtk/menu.c:403: error: syntax error before string constant
mplayer/gtk/menu.c:405: error: 'MSGTR_MENU_Open' undeclared (first use in this function)
mplayer/gtk/menu.c:406: error: 'MSGTR_MENU_PlayFile' undeclared (first use in this function)
mplayer/gtk/menu.c:406: error: syntax error before string constant
mplayer/gtk/menu.c:408: error: 'MSGTR_MENU_PlayVCD' undeclared (first use in this function)
mplayer/gtk/menu.c:411: error: 'MSGTR_MENU_PlayDVD' undeclared (first use in this function)
mplayer/gtk/menu.c:413: error: 'MSGTR_MENU_PlayURL' undeclared (first use in this function)
mplayer/gtk/menu.c:414: error: 'MSGTR_MENU_LoadSubtitle' undeclared (first use in this function)
mplayer/gtk/menu.c:414: error: syntax error before string constant
mplayer/gtk/menu.c:415: error: 'MSGTR_MENU_DropSubtitle' undeclared (first use in this function)
mplayer/gtk/menu.c:416: error: 'MSGTR_MENU_LoadExternAudioFile' undeclared (first use in this function)
mplayer/gtk/menu.c:417: error: 'MSGTR_MENU_Playing' undeclared (first use in this function)
mplayer/gtk/menu.c:418: error: 'MSGTR_MENU_Play' undeclared (first use in this function)
mplayer/gtk/menu.c:418: error: syntax error before string constant
mplayer/gtk/menu.c:419: error: 'MSGTR_MENU_Pause' undeclared (first use in this function)
mplayer/gtk/menu.c:420: error: 'MSGTR_MENU_Stop' undeclared (first use in this function)
mplayer/gtk/menu.c:421: error: 'MSGTR_MENU_NextStream' undeclared (first use in this function)
mplayer/gtk/menu.c:422: error: 'MSGTR_MENU_PrevStream' undeclared (first use in this function)
mplayer/gtk/menu.c:433: error: 'MSGTR_MENU_VCD' undeclared (first use in this function)
mplayer/gtk/menu.c:434: error: 'MSGTR_MENU_PlayDisc' undeclared (first use in this function)
mplayer/gtk/menu.c:436: error: 'MSGTR_MENU_Titles' undeclared (first use in this function)
mplayer/gtk/menu.c:442: error: 'MSGTR_MENU_Title' undeclared (first use in this function)
mplayer/gtk/menu.c:449: error: 'MSGTR_MENU_None' undeclared (first use in this function)
mplayer/gtk/menu.c:454: error: 'MSGTR_MENU_DVD' undeclared (first use in this function)
mplayer/gtk/menu.c:455: error: syntax error before string constant
mplayer/gtk/menu.c:475: error: 'MSGTR_MENU_Chapters' undeclared (first use in this function)
mplayer/gtk/menu.c:481: error: 'MSGTR_MENU_Chapter' undeclared (first use in this function)
mplayer/gtk/menu.c:491: error: 'MSGTR_MENU_AudioLanguages' undeclared (first use in this function)
mplayer/gtk/menu.c:511: error: 'MSGTR_MENU_SubtitleLanguages' undeclared (first use in this function)
mplayer/gtk/menu.c:533: error: 'MSGTR_MENU_AspectRatio' undeclared (first use in this function)
mplayer/gtk/menu.c:534: error: 'MSGTR_MENU_Original' undeclared (first use in this function)
mplayer/gtk/menu.c:549: error: 'MSGTR_MENU_AudioTrack' undeclared (first use in this function)
mplayer/gtk/menu.c:554: error: 'MSGTR_MENU_Track' undeclared (first use in this function)
mplayer/gtk/menu.c:564: error: 'MSGTR_MENU_VideoTrack' undeclared (first use in this function)
mplayer/gtk/menu.c:579: error: 'MSGTR_MENU_Subtitles' undeclared (first use in this function)
mplayer/gtk/menu.c:590: error: 'MSGTR_MENU_Mute' undeclared (first use in this function)
mplayer/gtk/menu.c:592: error: 'MSGTR_MENU_PlayList' undeclared (first use in this function)
mplayer/gtk/menu.c:593: error: 'MSGTR_MENU_SkinBrowser' undeclared (first use in this function)
mplayer/gtk/menu.c:594: error: 'MSGTR_MENU_Preferences' undeclared (first use in this function)
mplayer/gtk/menu.c:595: error: 'MSGTR_Equalizer' undeclared (first use in this function)
mplayer/gtk/menu.c:609: error: 'MSGTR_MENU_HalfSize' undeclared (first use in this function)
mplayer/gtk/menu.c:610: error: 'MSGTR_MENU_NormalSize' undeclared (first use in this function)
mplayer/gtk/menu.c:610: error: syntax error before string constant
mplayer/gtk/menu.c:611: error: 'MSGTR_MENU_DoubleSize' undeclared (first use in this function)
mplayer/gtk/menu.c:612: error: 'MSGTR_MENU_FullScreen' undeclared (first use in this function)
mplayer/gtk/menu.c:623: error: 'MSGTR_MENU_Exit' undeclared (first use in this function)
make[1]: *** [mplayer/gtk/menu.o] Error 1
make[1]: Leaving directory `/home/barts_706/mplayer/Gui'
make: *** [Gui/libgui.a] Error 2

```

Now I haven't yet seen this kind of errors, so if any of you has any idea as to what I can do about it, I would be very grateful for your help.

---

### Post by sapo on 2006-07-01
[QUOTE=Barts_706]Hi,

I tried to install MPlayer in the way you described, and that is what I get at the compilation stage :

```
mplayer/gtk/menu.c: In function 'create_PopUpMenu':
mplayer/gtk/menu.c:403: error: 'MSGTR_MENU_AboutMPlayer' undeclared (first use in this function)
mplayer/gtk/menu.c:403: error: (Each undeclared identifier is reported only oncemplayer/gtk/menu.c:403: error: for each function it appears in.)
mplayer/gtk/menu.c:403: error: syntax error before string constant
mplayer/gtk/menu.c:405: error: 'MSGTR_MENU_Open' undeclared (first use in this function)
mplayer/gtk/menu.c:406: error: 'MSGTR_MENU_PlayFile' undeclared (first use in this function)
mplayer/gtk/menu.c:406: error: syntax error before string constant
mplayer/gtk/menu.c:408: error: 'MSGTR_MENU_PlayVCD' undeclared (first use in this function)
mplayer/gtk/menu.c:411: error: 'MSGTR_MENU_PlayDVD' undeclared (first use in this function)
mplayer/gtk/menu.c:413: error: 'MSGTR_MENU_PlayURL' undeclared (first use in this function)
mplayer/gtk/menu.c:414: error: 'MSGTR_MENU_LoadSubtitle' undeclared (first use in this function)
mplayer/gtk/menu.c:414: error: syntax error before string constant
mplayer/gtk/menu.c:415: error: 'MSGTR_MENU_DropSubtitle' undeclared (first use in this function)
mplayer/gtk/menu.c:416: error: 'MSGTR_MENU_LoadExternAudioFile' undeclared (first use in this function)
mplayer/gtk/menu.c:417: error: 'MSGTR_MENU_Playing' undeclared (first use in this function)
mplayer/gtk/menu.c:418: error: 'MSGTR_MENU_Play' undeclared (first use in this function)
mplayer/gtk/menu.c:418: error: syntax error before string constant
mplayer/gtk/menu.c:419: error: 'MSGTR_MENU_Pause' undeclared (first use in this function)
mplayer/gtk/menu.c:420: error: 'MSGTR_MENU_Stop' undeclared (first use in this function)
mplayer/gtk/menu.c:421: error: 'MSGTR_MENU_NextStream' undeclared (first use in this function)
mplayer/gtk/menu.c:422: error: 'MSGTR_MENU_PrevStream' undeclared (first use in this function)
mplayer/gtk/menu.c:433: error: 'MSGTR_MENU_VCD' undeclared (first use in this function)
mplayer/gtk/menu.c:434: error: 'MSGTR_MENU_PlayDisc' undeclared (first use in this function)
mplayer/gtk/menu.c:436: error: 'MSGTR_MENU_Titles' undeclared (first use in this function)
mplayer/gtk/menu.c:442: error: 'MSGTR_MENU_Title' undeclared (first use in this function)
mplayer/gtk/menu.c:449: error: 'MSGTR_MENU_None' undeclared (first use in this function)
mplayer/gtk/menu.c:454: error: 'MSGTR_MENU_DVD' undeclared (first use in this function)
mplayer/gtk/menu.c:455: error: syntax error before string constant
mplayer/gtk/menu.c:475: error: 'MSGTR_MENU_Chapters' undeclared (first use in this function)
mplayer/gtk/menu.c:481: error: 'MSGTR_MENU_Chapter' undeclared (first use in this function)
mplayer/gtk/menu.c:491: error: 'MSGTR_MENU_AudioLanguages' undeclared (first use in this function)
mplayer/gtk/menu.c:511: error: 'MSGTR_MENU_SubtitleLanguages' undeclared (first use in this function)
mplayer/gtk/menu.c:533: error: 'MSGTR_MENU_AspectRatio' undeclared (first use in this function)
mplayer/gtk/menu.c:534: error: 'MSGTR_MENU_Original' undeclared (first use in this function)
mplayer/gtk/menu.c:549: error: 'MSGTR_MENU_AudioTrack' undeclared (first use in this function)
mplayer/gtk/menu.c:554: error: 'MSGTR_MENU_Track' undeclared (first use in this function)
mplayer/gtk/menu.c:564: error: 'MSGTR_MENU_VideoTrack' undeclared (first use in this function)
mplayer/gtk/menu.c:579: error: 'MSGTR_MENU_Subtitles' undeclared (first use in this function)
mplayer/gtk/menu.c:590: error: 'MSGTR_MENU_Mute' undeclared (first use in this function)
mplayer/gtk/menu.c:592: error: 'MSGTR_MENU_PlayList' undeclared (first use in this function)
mplayer/gtk/menu.c:593: error: 'MSGTR_MENU_SkinBrowser' undeclared (first use in this function)
mplayer/gtk/menu.c:594: error: 'MSGTR_MENU_Preferences' undeclared (first use in this function)
mplayer/gtk/menu.c:595: error: 'MSGTR_Equalizer' undeclared (first use in this function)
mplayer/gtk/menu.c:609: error: 'MSGTR_MENU_HalfSize' undeclared (first use in this function)
mplayer/gtk/menu.c:610: error: 'MSGTR_MENU_NormalSize' undeclared (first use in this function)
mplayer/gtk/menu.c:610: error: syntax error before string constant
mplayer/gtk/menu.c:611: error: 'MSGTR_MENU_DoubleSize' undeclared (first use in this function)
mplayer/gtk/menu.c:612: error: 'MSGTR_MENU_FullScreen' undeclared (first use in this function)
mplayer/gtk/menu.c:623: error: 'MSGTR_MENU_Exit' undeclared (first use in this function)
make[1]: *** [mplayer/gtk/menu.o] Error 1
make[1]: Leaving directory `/home/barts_706/mplayer/Gui'
make: *** [Gui/libgui.a] Error 2

```

Now I haven't yet seen this kind of errors, so if any of you has any idea as to what I can do about it, I would be very grateful for your help.[/QUOTE]


It seems that your problem is on the menu, try this instead:

```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-tv-v4l --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid --disable-divx4linux --enable-x264
```

---

### Post by maagimies on 2006-07-01
Very good guide sapo, but wouldn't it be best to make a debian package out of the compile instead of make install? :eek:
It's easier to manage the installed files that way and everything is more clean ;)

---

### Post by Barts_706 on 2006-07-02
I tried to do as you suggested, sapo,  but it gave me exactly the same error (?).

Maybe I need to remove the effects of previous ./configure ?

I have checked to have newest automake, libncurses, dev packages - so that should not be a problem. Any suggestions?

---

### Post by saax on 2006-07-06
I installed codecs by How to and it works for first day ,but now when i open .wmv file its only play sound and no picture.

Error - Cannot find codec matching selected -vo and video format 0x33564D57.

I re-install codecs,but no succes.

Whats wrong and how can i fix this?

---

### Post by sup on 2006-07-08
You seem to have omitted xvid developement package  libxvidcore4-dev
 - without it, support for xvid will not compile. At least I had it install it manually.

---

### Post by ashrack on 2006-07-09
The latest MPLAYER PRE8 is GTK2 compatible. 
BUt I still dont have the GNOME integration when I OPEN a file. I still get the old GTK1 dialog!!!

I've this installed:
libgtk2.0-dev

and the ./configure give the following GTK output:
Checking for GTK+ version ... 2.8.18

and I've compiled it using this:
###########
./configure --enable-gui --enable-largefiles --enable-menu --enable-runtime-cpudetection --prefix=/usr
###########

What else am I missing??

---

### Post by Don_DiZzLe on 2006-07-09
How do I use the mozilla-mplayer plugin without istalling mplayer from the repos?

---

### Post by sapo on 2006-07-09
> **sup said:**
> You seem to have omitted xvid developement package  libxvidcore4-dev
 - without it, support for xvid will not compile. At least I had it install it manually.
Xvid here works fine without installing anything else besides what is on this howto, thats weird that your xvid didnt work without that lib.

---

### Post by ashrack on 2006-07-09
Here, at the end of the page:
[http://ubuntuforums.org/showthread.php?t=85190](http://ubuntuforums.org/showthread.php?t=85190)

---

### Post by Don_DiZzLe on 2006-07-10
Nevermind I figured it out.

---

### Post by kayrune on 2006-07-11
I followed the guide, but when running make on mplayer it stoppet:

> libavcodec/libavcodec.a(parser.o): In function `cavsvideo_parse':parser.c:(.text+0xaf4): undefined reference to `ff_cavs_find_frame_end'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


---

### Post by blackb1rd on 2006-07-11
Get the same message as kayrune, guess some things are broken in SVN :(

---

### Post by kayrune on 2006-07-11
I updated the SVN and this time it was able to compile, and it seems to work fine. There is one .avi file though, don't know the codec that produse the following error (this file doesn't work with vlc or gstreamer either) is there such a program as Gspot for linux ?

> MPlayer dev-SVN-r19019-4.0.3 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 12, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.


I also tried a 1080P wmv file (demo from nVidia) and although the framerate was much better now, the sound was not good.

Also I have serious problems finding a videorender that works, that might be because of XGL though...?

---

### Post by Flancer on 2006-07-11
Hi there, I wonder if anyone has a ready compiled Mplayer 1.08 (or newer from the SVN repos) with ALSA and xvmc support that they could post? Would love to try it out. I tried compiling on my own but for reasons I cannot understand, it always complains of some syntax errors in the ALSA headers even though I am on a fresh installation of Dapper.

Thanks.

---

### Post by Flancer on 2006-07-12
OK well any new mplayer build on dapper with ALSA support would be appreciated :). Sapo? Anyone?

Thanks.

---

### Post by fubadubrub on 2006-08-04
Hello and thank you for the updated mplayer compile guide for svn.  I am recieving 2 errors and am I doing something wrong or is the source code currently broken and I just have to wait.  If I have to wait how long should I.  I am thinking of redownloading once a day.  Thanks in advance.

First error is: Unknown parameter: --enable-tv-v4l

if I remove this option I get this error:
Unknown parameter: --disable-divx4linux

Then I remove this option too.  I can finally successfully run ./configure

However running make gives this error:
/usr/bin/ld: cannot open output file mplayer: Is a directory
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

My directory structure is: /home/username/sources-and-builds/mplayer

---

### Post by sapo on 2006-08-04
> **fubadubrub said:**
> Hello and thank you for the updated mplayer compile guide for svn.  I am recieving 2 errors and am I doing something wrong or is the source code currently broken and I just have to wait.  If I have to wait how long should I.  I am thinking of redownloading once a day.  Thanks in advance.

First error is: Unknown parameter: --enable-tv-v4l

if I remove this option I get this error:
Unknown parameter: --disable-divx4linux

Then I remove this option too.  I can finally successfully run ./configure

However running make gives this error:
/usr/bin/ld: cannot open output file mplayer: Is a directory
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

My directory structure is: /home/username/sources-and-builds/mplayer
Do you have another directory called mplayer inside the dir you are running make?

if you do, try moving it to somewhere else.

---

### Post by fubadubrub on 2006-08-04
Yes I had source code within source code my bad.  Since I had 2 copies I just deleted the one so now it's just the top level mplayer.  Thank you.

But now I have new problem.  Make gives this now.

In file included from librtsp/rtsp_session.c:48:
librtsp/../rtp.h:37: error: syntax error before '*' token
make[1]: *** [librtsp/rtsp_session.o] Error 1
make[1]: Leaving directory `/home/username/sources-and-builds/mplayer/stream'
make: *** [stream/stream.a] Error 2

---

### Post by sapo on 2006-08-04
> **fubadubrub said:**
> Yes I had source code within source code my bad.  Since I had 2 copies I just deleted the one so now it's just the top level mplayer.  Thank you.

But now I have new problem.  Make gives this now.

In file included from librtsp/rtsp_session.c:48:
librtsp/../rtp.h:37: error: syntax error before '*' token
make[1]: *** [librtsp/rtsp_session.o] Error 1
make[1]: Leaving directory `/home/username/sources-and-builds/mplayer/stream'
make: *** [stream/stream.a] Error 2
It seens that something is broken on the svn sources =x

---

### Post by fubadubrub on 2006-08-05
**The mplayer plugin instructions in the quote box are old and outdated for Dapper.  Read below quote box for updated instructions for Dapper**.

> **helpdeskdan said:**
> I just installed the mplayer plugin.  Combined with my compiled mplayer, it works better than anything I've ever seen on linux. 

Very quick/dirty  instructions (after you have downloaded the source):
1. sudo apt-get firefox-dev (will also install libnss-dev, libnspr-dev)
 
2.  Get gecko-sdk [http://developer.mozilla.org/en/docs/Gecko_SDK#Downloading](http://developer.mozilla.org/en/docs/Gecko_SDK#Downloading)

3.  tar -xzf it in your home dir (for lack of not being sure where to put it)

4.  ./configure --with-gecko-sdk=~/gecko-sdk
(If I were smarter, I could tell you the proper way to do this, but this works)

5.  make

6.  su or sudo:
cp mplayerplug-in*.so /usr/lib/mozilla-firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components
Just to be sure, I also did:
cp mplayerplug-in*.so /usr/lib/firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/firefox/components
(not sure why there are two directories.  Again, if I were smarter...)

7.  Restart firefox and enjoy!

Perhaps somebody may find this information usefull; will be happy to clarify vague details if needed.Here's how to do it properly and get version 3.30 which is totally way more stable, reliable and flat out better.  

Open Synaptic and search for 3 packages, **firefox-dev, libnss-dev, libnspr-dev**.  Install these 3 packages.

**You do not need the Gecko-SDK**.

**Update about Geko SDK!  There is a newly released official Geko SDK version 1.8 for 1.5 and 2.0 Firefox browsers and third party products based on 1.5 or 2.0 platforms.  The Geko SDK is useful only if you do not want to use firefox-dev.  Get the newly released Geko SDK 1.8 here:**

[http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.0.4/sdk/gecko-sdk-i686-pc-linux-gnu-1.8.0.4.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.0.4/sdk/gecko-sdk-i686-pc-linux-gnu-1.8.0.4.tar.bz2)

After you have downloaded it simply extract it.

**I have added to the mplayer-plugin configure instructions information on how to use the new Geko SDK version 1.8**.

Open your terminal and type: 
**cvs -d:pserver:anonymous@mplayerplug-in.cvs.sourceforge.net:/cvsroot/mplayerplug-in login**
(just hit enter for password)

Then type: The below is all one line it may wrap around in the terminal because it's very long.
**cvs -z3 -d:pserver:anonymous@mplayerplug-in.cvs.sourceforge.net:/cvsroot/mplayerplug-in co mplayerplug-in**

Then: **cd mplayerplug-in**

Now type:

**./configure**

If you get this error during configure:  
**"checking for mozilla-plugin... Package mozilla-plugin was not found in the pkg-config search path."**

Please ignore this warning.  It is outdated.  Please continue to install as usual.  Again this warning is completely safe to ignore.


Compiling mplayer-plugin with Geko SDK version 1.8:

**./configure --with-gecko-sdk=/path/to/gecko-sdk**



Then type:
**make**

Then type:
**sudo cp mplayerplug-in*.so /usr/lib/mozilla-firefox/plugins**
**sudo cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components**

Restart Firefox.

These instructions are based off of:
[http://mplayerplug-in.sourceforge.net/install.php#plugin](http://mplayerplug-in.sourceforge.net/install.php#plugin)

Go to 
[http://mplayerplug-in.sourceforge.net](http://mplayerplug-in.sourceforge.net)  Home page for plugin
[http://mplayerplug-in.sourceforge.net/testing.php](http://mplayerplug-in.sourceforge.net/testing.php)  Test your plugin
[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)  Test page same below
[http://www.apple.com/trailers]("http://www.apple.com/trailers/")
[http://www.linspire.com/products_linspire_whatis.php?tab=compatibility](http://www.linspire.com/products_linspire_whatis.php?tab=compatibility) 
[http://developer.mozilla.org/en/docs/Gecko_SDK](http://developer.mozilla.org/en/docs/Gecko_SDK) Geko SDK main page.

Hey what do you know it works.

---

### Post by fubadubrub on 2006-08-05
Never mind about the trailing slash I was just dead that day.  Instead of "Skins" how about "skins".

Maybe you want to leave off trailing slash as that seemed to produce error for me.  By the way Mplayer is working perfectly for me now as well as the plugin.  Thanks to sapo for guide.

sudo cp -R default/ /usr/share/mplayer/Skin/

sudo cp -R default/ /usr/share/mplayer/skins/

---

### Post by starscalling on 2006-08-06
mmmmmmmm
seems mplayer --enable and --disable tags changed since this howto was written
it doesnt know the regular tv4l nor divxforlinux tags anymore

mplayer.c: In function 'main':
mplayer.c:3133: warning: pointer targets in passing argument 2 of 'vobsub_set_from_lang' differ in signedness
mplayer.c:3197: warning: pointer targets in passing argument 2 of 'stream_read' differ in signedness
mplayer.c:3216: warning: pointer targets in passing argument 2 of 'dvd_aid_from_lang' differ in signedness
mplayer.c:3218: warning: pointer targets in passing argument 2 of 'dvd_sid_from_lang' differ in signedness
mplayer.c:3257: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3257: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3257: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3257: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in signedness
mplayer.c:3266: warning: pointer targets in passing argument 1 of 'strrchr' differ in s


lots of that while compiling

subreader.c: In function 'sub_read_line_aqt':
subreader.c:714: warning: pointer targets in passing argument 2 of 'stream_read_line' differ in signedness
subreader.c:729: warning: pointer targets in passing argument 2 of 'stream_read_line' differ in signedness
subreader.c:736: warning: pointer targets in passing argument 2 of 'stream_read_line' differ in signedness
subreader.c: In function 'sub_read_line_subrip09':
subreader.c:772: warning: pointer targets in passing argument 2 of 'stream_read_line' differ in signedness
subreader.c:789: warning: pointer targets in passing argument 2 of 'stream_read_line' differ in signedness
subreader.c: In function 'sub_read_line_jacosub':
subreader.c:828: warning: pointer targets in passing argument 2 of 'stream_read_line' differ in signedness
subreader.c:986: warning: pointer targets in passing argument 2 of 'stream_read_line' differ in signedness




and that 


a few more like this ~_~





well
even with that stuff
guide worked fine
btw
i highly recommend adding checkinstall to the mix:
sudo checkinstall make install
creates a package 
walks you through it
change version to 1.0pre8
let finish
pin the deb // lock it 
install the fonts // skin package
done
lol
btw im now happily enjoying my zetapain[A-Future]_Zegapain_-_01_[H264][AAC][720p][D865E4B4].mkv

---

### Post by starscalling on 2006-08-06
well i really hate to double post....
but this with the last one might be a bit long

[email]nekostar@dapper:~/.xcha[/email]t2/downloads$ mplayer -cache 8192 -ao oss \[A-Future\]_Zegapain_-_01_\[H264\]\[AAC\]\[720p\]\[D865E4B4\].mkv
MPlayer dev-SVN-r19343-4.0.3 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 3000+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

Playing [A-Future]_Zegapain_-_01_[H264][AAC][720p][D865E4B4].mkv.

[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC/MPEG4/LC/SBR), -aid 0, -alang jpn
[mkv] Will play video track 1
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12
A:  76.2 V:  75.7 A-V:  0.492 ct:  0.129 1807/1807 54%  7%  2.7% 97 0 48%

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A: 191.1 V: 191.1 A-V:  0.001 ct:  0.125 4574/4574 49%  6%  2.6% 319 0 48%
  =====  PAUSE  =====



which makes me unhappy ~_______~


nekostar@dapper:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 3000+
stepping        : 0
cpu MHz         : 2162.849
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 4328.43

thats enough to run any h264 even

help!

---

### Post by fubadubrub on 2006-08-06
You should know that even on top of the line desktop computers like AMD 64 cpu and Intel core cpus, h.264 and other codecs running at HD resolutions of 720p or higher still command huge amounts of cpu power.  For example a 1080p quality HD h.264, .mov, .wmv can  in many cases exceed 50% cpu power on top of the line chips.  Also somes scenes may have lower cpu needs like a very dark nighttime scene, while an explosive daytime scene may require more horsepower.  Also the entire system must be taken in account.  Your AMD cpu is close to the bottom end for h.264 HD content, so I'm not suprised to see you having trouble with HD content.  Really at a minmum you need an AMD 64 at a higher frequency and for intel probably an prescott at 3.0Ghz or better.  You can try in the terminal typing man mplayer and reading the documentation.  There are several techniques you can use to get HD content to play on slow systems at the cost of looking ugly.  Hope this helps.

> **starscalling said:**
> ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

which makes me unhappy ~_______~


nekostar@dapper:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 3000+
stepping        : 0
cpu MHz         : 2162.849
cache size      : 512 KB

thats enough to run any h264 even

---

### Post by fubadubrub on 2006-08-06
All those harmless errors can generally be ignored.  Nothing more than what I call the make background noise.
> **starscalling said:**
> mmmmmmmm
seems mplayer --enable and --disable tags changed since this howto was written
it doesnt know the regular tv4l nor divxforlinux tags anymore

mplayer.c: In function 'main':
mplayer.c:3133: warning: pointer targets in passing argument 2 of 'vobsub_set_from_lang' differ in signedness

---

### Post by mlind on 2006-08-07
If anyone wants to build .debs of mplayer and required dependencies, I suggest to get the source packages from Marillat's repository and build those for your box.
I had a thread about this a while ago [http://www.ubuntuforums.org/showpost.php?p=1198299&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1198299&postcount=3)

---

### Post by rlynch on 2006-08-07
Will this allow DVD Discs to play in Mplayer? When I put a disc in now, the video is "splotchy", lol and there is no audio

---

### Post by starscalling on 2006-08-08
> **fubadubrub said:**
> You should know that even on top of the line desktop computers like AMD 64 cpu and Intel core cpus, h.264 and other codecs running at HD resolutions of 720p or higher still command huge amounts of cpu power.  For example a 1080p quality HD h.264, .mov, .wmv can  in many cases exceed 50% cpu power on top of the line chips.  Also somes scenes may have lower cpu needs like a very dark nighttime scene, while an explosive daytime scene may require more horsepower.  Also the entire system must be taken in account.  Your AMD cpu is close to the bottom end for h.264 HD content, so I'm not suprised to see you having trouble with HD content.  Really at a minmum you need an AMD 64 at a higher frequency and for intel probably an prescott at 3.0Ghz or better.  You can try in the terminal typing man mplayer and reading the documentation.  There are several techniques you can use to get HD content to play on slow systems at the cost of looking ugly.  Hope this helps.

yeh i understand what your saying
but in windows my 1.667 ghz system can handle that same video quite well
must be a crappy application of h264 >> x264 in linux then !_!

---

### Post by abu_nawas on 2006-08-08
i'm trying to compile MPlayer-1.0pre8, and when i do make i get this:
```

ve_x264.c: In function 'config':
ve_x264.c:278: error: 'struct <anonymous>' has no member named 'b_cbr'
make[1]: *** [ve_x264.o] Error 1
make[1]: Leaving directory `/home/ubuntu/MPlayer-1.0pre8/libmpcodecs'
make: *** [libmpcodecs/libmpcodecs.a] Error 2

```

need help here [-o<

---

### Post by mlind on 2006-08-09
> **abu_nawas said:**
> i'm trying to compile MPlayer-1.0pre8, and when i do make i get this:
```

ve_x264.c: In function 'config':
ve_x264.c:278: error: 'struct <anonymous>' has no member named 'b_cbr'
make[1]: *** [ve_x264.o] Error 1
make[1]: Leaving directory `/home/ubuntu/MPlayer-1.0pre8/libmpcodecs'
make: *** [libmpcodecs/libmpcodecs.a] Error 2

```

need help here [-o<

Try this patch that's on Marillat's mplayer source package.

```

--- libmpcodecs/ve_x264.c.orig	2006-06-11 20:35:41.000000000 +0200
+++ libmpcodecs/ve_x264.c	2006-07-21 15:49:42.000000000 +0200
@@ -208,7 +208,7 @@
 };
 
 static int parse_cqm(const char *str, uint8_t *cqm, int length,
-                     h264_module_t *mod, char *matrix_name) {
+                     h264_module_t *mod, const char *matrix_name) {
     int i;
     if (!str) return 0;
     for (i = 0; i < length; i++) {
@@ -247,7 +247,10 @@
     mod->param.i_deblocking_filter_beta = deblockbeta;
     mod->param.b_cabac = cabac;
 
+    mod->param.rc.i_rc_method = X264_RC_CQP;
     mod->param.rc.i_qp_constant = qp_constant;
+    if(rf_constant > 0)
+        mod->param.rc.i_rc_method = X264_RC_CRF;
     mod->param.rc.i_rf_constant = rf_constant;
     if(qp_min > qp_constant)
         qp_min = qp_constant;
@@ -275,7 +278,7 @@
                    "VBV requires both vbv_maxrate and vbv_bufsize.\n");
             return 0;
         }
-        mod->param.rc.b_cbr = 1;
+        mod->param.rc.i_rc_method = X264_RC_ABR;
         mod->param.rc.i_bitrate = bitrate;
         mod->param.rc.f_rate_tolerance = ratetol;
         mod->param.rc.i_vbv_max_bitrate = vbv_maxrate;

```

---

### Post by MedievalAnubis on 2006-08-09
This has been one of the most useful guides on anything for Linux. my mplayer wouldn't even start up on Dapper. Now it plays alot of files that were unreadable including WMVs and handles subtitles beautifully for MKVs. Thanks for this guide. It will be forever bookmarked.

P.S I am a fellow Bleach fan!

---

### Post by sapo on 2006-08-09
> **MedievalAnubis said:**
> This has been one of the most useful guides on anything for Linux. my mplayer wouldn't even start up on Dapper. Now it plays alot of files that were unreadable including WMVs and handles subtitles beautifully for MKVs. Thanks for this guide. It will be forever bookmarked.

P.S I am a fellow Bleach fan!
Thanx man, i just feel ashamed of being lazy about updating it, but i think it at least works :)

---

### Post by marinosr on 2006-08-10
Great howto! This was an absolute bear of a task for a noob like me, and I would never have been able to do it without major help. I ran into one big problem and a whole slew of little ones, but I finally have it up and running (sans GUI). One hint I can tell y'all: If config tells you that you need X11 support, install libgtk1.2-dev.

---

### Post by abu_nawas on 2006-08-10
> **mlind said:**
> Try this patch that's on Marillat's mplayer source package.

```

--- libmpcodecs/ve_x264.c.orig	2006-06-11 20:35:41.000000000 +0200
+++ libmpcodecs/ve_x264.c	2006-07-21 15:49:42.000000000 +0200
@@ -208,7 +208,7 @@
 };
 
 static int parse_cqm(const char *str, uint8_t *cqm, int length,
-                     h264_module_t *mod, char *matrix_name) {
+                     h264_module_t *mod, const char *matrix_name) {
     int i;
     if (!str) return 0;
     for (i = 0; i < length; i++) {
@@ -247,7 +247,10 @@
     mod->param.i_deblocking_filter_beta = deblockbeta;
     mod->param.b_cabac = cabac;
 
+    mod->param.rc.i_rc_method = X264_RC_CQP;
     mod->param.rc.i_qp_constant = qp_constant;
+    if(rf_constant > 0)
+        mod->param.rc.i_rc_method = X264_RC_CRF;
     mod->param.rc.i_rf_constant = rf_constant;
     if(qp_min > qp_constant)
         qp_min = qp_constant;
@@ -275,7 +278,7 @@
                    "VBV requires both vbv_maxrate and vbv_bufsize.\n");
             return 0;
         }
-        mod->param.rc.b_cbr = 1;
+        mod->param.rc.i_rc_method = X264_RC_ABR;
         mod->param.rc.i_bitrate = bitrate;
         mod->param.rc.f_rate_tolerance = ratetol;
         mod->param.rc.i_vbv_max_bitrate = vbv_maxrate;

```

i'm having a problem downloading from Marillat's source package (actually it's a apt-get problem with my network). can u upload the patch here?

---

### Post by mlind on 2006-08-10
> **abu_nawas said:**
> i'm having a problem downloading from Marillat's source package (actually it's a apt-get problem with my network). can u upload the patch here?

That was the patch, just make a file out of it and patch the source.
I'll include the debian/patches folder contents as an acrhive

---

### Post by abu_nawas on 2006-08-10
> **mlind said:**
> That was the patch, just make a file out of it and patch the source.
I'll include the debian/patches folder contents as an acrhive
Thanks, it works :D. Now i can play my x264 high profile movie with mplayer. But still no subtitle :(. It was muxed with mp4box.

---

### Post by MedievalAnubis on 2006-08-12
Does anyone know how to compile the mplayer plugin for mozilla firefox? I tried installing it from synaptic but it wants to install another precompiled version of mplayer. Thanks for any help!

---

### Post by fubadubrub on 2006-08-13
See post #73 by fubadubrub for instructions.  It is quite easy to do.  Have fun.> **MedievalAnubis said:**
> Does anyone know how to compile the mplayer plugin for mozilla firefox? I tried installing it from synaptic but it wants to install another precompiled version of mplayer. Thanks for any help!

---

### Post by bitwise on 2006-08-14
> **fubadubrub said:**
> **The mplayer plugin instructions in the quote box are too messy.  Read below for a better way**.

Here's how to do it properly and get version 3.30 which is totally way more stable, reliable and flat out better.  

Open Synaptic and search for 3 packages, **firefox-dev, libnss-dev, libnspr-dev**.  Install these 3 packages.

**You do not need the Gecko-SDK!**.

 Open your terminal and type: 
**cvs -d:pserver:anonymous@mplayerplug-in.cvs.sourceforge.net:/cvsroot/mplayerplug-in login**
(just hit enter for password)

Then type: The below is all one line it may wrap around in the terminal because it's very long.
**cvs -z3 -d:pserver:anonymous@mplayerplug-in.cvs.sourceforge.net:/cvsroot/mplayerplug-in co mplayerplug-in**

Then: **cd mplayerplug-in**

Now type:

**./configure**

If you get this error during configure:  
**"checking for mozilla-plugin... Package mozilla-plugin was not found in the pkg-config search path."**

Please ignore this warning.  It is outdated.  Please continue to install as usual.  Again this warning is completely safe to ignore and is in your best interest to ignore.

Then type:
**make**

Then type:
**sudo cp mplayerplug-in*.so /usr/lib/mozilla-firefox/plugins**
**sudo cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components**

Restart Firefox.

These instructions are based off of:
[http://mplayerplug-in.sourceforge.net/install.php#plugin](http://mplayerplug-in.sourceforge.net/install.php#plugin)

Go to 
[http://mplayerplug-in.sourceforge.net](http://mplayerplug-in.sourceforge.net)  Home page for plugin
[http://mplayerplug-in.sourceforge.net/testing.php](http://mplayerplug-in.sourceforge.net/testing.php)  Test your plugin
[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)  Test page same below
[http://www.apple.com/trailers]("http://www.apple.com/trailers/")
[http://www.linspire.com/products_linspire_whatis.php?tab=compatibility](http://www.linspire.com/products_linspire_whatis.php?tab=compatibility) 

Hey what do you know it works.


FYI - 

I needed the libglib2.0-dev package to install this.

Was getting an error that GTHREAD was required.

Hope it helps someone :)

---

### Post by jbernardo on 2006-08-21
I'm out of luck building x264 support on a amd64 - this is what I get:

```
make[2]: Leaving directory `/usr/src/ffmpeg/mplayer/libmenu'
cc -Wdeclaration-after-statement -O4 -march=k8 -mtune=k8 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include -I/usr/src/DVB/ost/include  -I/usr/include/SDL -D_REENTRANT -I/usr/include/dxr2 -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -I/usr/local/include/cdda -I/usr/include/freetype2 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I.  -I./libavutil -I./libavcodec -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a libmenu/libmenu.a vidix/libvidix.a Gui/libgui.a -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -L/usr/lib -lglib libmpcodecs/libmpcodecs.a  libaf/libaf.a libmpdemux/libmpdemux.a stream/stream.a libswscale/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit  libavformat/libavformat.a  libavcodec/libavcodec.a  libavutil/libavutil.a  libpostproc/libpostproc.a  -lmad -ldv -ltheora -logg   -lmp3lame  -lxvidcore -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread   -lmpcdec   -lfaac -lncurses  -lnsl   -lungif  -lsmbclient    libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a libass/libass.a -lfontconfig -lfreetype -lz  -lGL -ldl -lXxf86dga -lXv -lXvMC -lXvMCW -lXxf86vm -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread        -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm -ljack -lopenal -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic  -lm
libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x38): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x6c): undefined reference to `x264_param_default'
:x264.c:(.text+0x3f7): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x570): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x651): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x754): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x812): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make[1]: ** [mplayer] Erro 1
make[1]: Saindo do diretório `/usr/src/ffmpeg/mplayer'
make: ** [binary-arch] Erro 2
```

If I disable x264 support, mplayer builds without any problem. I did build and install x264 as by this thread.

---

### Post by mlind on 2006-08-21
> **jbernardo said:**
> I'm out of luck building x264 support on a amd64 - this is what I get:

```
make[2]: Leaving directory `/usr/src/ffmpeg/mplayer/libmenu'
cc -Wdeclaration-after-statement -O4 -march=k8 -mtune=k8 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include -I/usr/src/DVB/ost/include  -I/usr/include/SDL -D_REENTRANT -I/usr/include/dxr2 -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -I/usr/local/include/cdda -I/usr/include/freetype2 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I.  -I./libavutil -I./libavcodec -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a libmenu/libmenu.a vidix/libvidix.a Gui/libgui.a -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -L/usr/lib -lglib libmpcodecs/libmpcodecs.a  libaf/libaf.a libmpdemux/libmpdemux.a stream/stream.a libswscale/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit  libavformat/libavformat.a  libavcodec/libavcodec.a  libavutil/libavutil.a  libpostproc/libpostproc.a  -lmad -ldv -ltheora -logg   -lmp3lame  -lxvidcore -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread   -lmpcdec   -lfaac -lncurses  -lnsl   -lungif  -lsmbclient    libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a libass/libass.a -lfontconfig -lfreetype -lz  -lGL -ldl -lXxf86dga -lXv -lXvMC -lXvMCW -lXxf86vm -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread        -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm -ljack -lopenal -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic  -lm
libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x38): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x6c): undefined reference to `x264_param_default'
:x264.c:(.text+0x3f7): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x570): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x651): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x754): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x812): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make[1]: ** [mplayer] Erro 1
make[1]: Saindo do diretório `/usr/src/ffmpeg/mplayer'
make: ** [binary-arch] Erro 2
```

If I disable x264 support, mplayer builds without any problem. I did build and install x264 as by this thread.

Tried the patch attached on post #83 ?

---

### Post by tengil on 2006-08-21
Hi. I can't compile with x264:

libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x38): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x57): undefined reference to `x264_param_default'
:x264.c:(.text+0x39b): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x4eb): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x5d2): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x6a3): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x74d): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

Changing to --disable-x264 and it compiles ok.

.:.

---

### Post by jbernardo on 2006-08-21
Also, I still can't watch the 3gpp movies I made on my phone - 
```
ISO: File Type Major Brand: 3GPP Profile 5
Quicktime/MOV file format detected.
VIDEO:  [mp4v]  320x240  24bpp  3.968 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders


MPlayer interrupted by signal 11 in module: init_audio_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```
I think I'll revert to the "regular" mplayer for now.

---

### Post by jbernardo on 2006-08-21
I tried the patch, but it is already included in mplayer code, and won't apply.

---

### Post by tengil on 2006-08-21
I get the same this with libavcodec:

Playing 04.wma.
ASF file format detected.
Clip info:
 name: Baubles, Bangles and Beads
 author: Deodato
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders


MPlayer interrupted by signal 11 in module: init_audio_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by fubadubrub on 2006-08-22
I have been compiling mplayer for a couple of weeks now and have studied the configure options a whole bunch **(./configure --help)**.  I have questions.


Why the paticular configure options in the guide.  For what reason.  The configure in mplayer seems to have robust auto detection.  For example why: **(-disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora)**.  All these should be auto detected.


Why **(-prefix=/usr)** and not **(--prefix=/usr/local)**.  I believe that generally third party software goes into **(/usr/local)**.


Would not an configure setup like the one below be more appropriate.

**./configure  --prefix=/usr/local --confdir=/etc/mplayer --enable-gui --enable-largefiles --enable-menu**


This allows for proper auto detection of one's computer capability.  If one is missing anything in the configure readout they can simply install the dev package in synaptic.

Your thoughts?

---

### Post by tengil on 2006-08-22
Compiling the 1.0pre8 release instead of from svn worked great. Followed the rest of the how-to. 

All my problems were resolved; wma playback works and video/audio are in sync.

---

### Post by fubadubrub on 2006-08-22
If anyone is having trouble with their audio system it may be caused by replacing **(libsdl1.2debian-alsa)** with **(libsdl1.2debian-all)**.

The mplayer howto list **(libsdl1.2debian-all)** as a dependency and as a result your most likely already installed **(libsdl1.2debian-alsa)** is removed.

I solved my lack of audio by removing **(libsdl1.2debian-all)** and reinstalling **(libsdl1.2debian-alsa)**.

It's probably just me but I just thought you would all would like to know.

---

### Post by Arandomcow5 on 2006-08-22
So i get to the "make" part...and it gives me this:

```
...
cc -Wdeclaration-after-statement -fno-PIC -O4 -march=prescott -mtune=prescott -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include -I/usr/include -I/usr/include/ -I/usr/src/DVB/ost/include  -I/usr/include/SDL -D_REENTRANT -I/usr/include/dxr2  -I/usr/local/include/cdda -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I.  -I./libavutil -I./libavcodec -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a libmenu/libmenu.a Gui/libgui.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0   libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a stream/stream.a libswscale/libswscale.a osdep/libosdep.a -Wl,-z,noexecstack  -Llibmpdvdkit2 -lmpdvdkit  libavformat/libavformat.a  libavcodec/libavcodec.a  libavutil/libavutil.a  libpostproc/libpostproc.a  -lmad  -ltheora -logg     -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread   -lmpcdec   -lncurses  -lnsl          -lpthread -ldl -rdynamic  -lm   libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a libass/libass.a -lfontconfig -lfreetype -lz  -lGL -ldl  -lXv  -lXxf86vm -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread     -L/usr/lib -lcaca -lslang -lX11 -L/usr/X11R6/lib -lncurses -lncurses   vidix/libvidix.a  -L/usr/lib -lesd -laudiofile -lm   -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread
/usr/bin/ld: cannot open output file mplayer: Permission denied
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

Thats the error i get...i have no idea whats going on...any ideas?

---

### Post by Bachstelze on 2006-08-25
During mplayer compiling, I get this :

```

libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x38): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x57): undefined reference to `x264_param_default'
:x264.c:(.text+0x39b): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x4eb): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x5d2): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x6a3): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x74d): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

I've followed all the step for x264 though, any ideas ?

---

### Post by mlind on 2006-08-25
> **HymnToLife said:**
> ```

libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x38): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x57): undefined reference to `x264_param_default'
:x264.c:(.text+0x39b): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x4eb): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x5d2): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x6a3): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x74d): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

I've followed all the step for x264 though, any ideas ?

Tried the patch on post #83 ?

---

### Post by Bachstelze on 2006-08-25
How does it work ? I just have to replace the files in the source tree with those in the archive ?


EDIT : OK, applied the patches but same error...

---

### Post by jbernardo on 2006-08-26
I'm also stuck with exactly the same error as hymntolife. I've tried updating from mplayer's svn today (rev 6101) and still no luck.

---

### Post by tr1plej on 2006-08-26
this is for everyone having problems compiling with x264 (tengil, jbernardo, HymnToLife, and anyone else) i was having the same problem.

the problem is with the configure options. as fubadubrub said in post #99, mplayer's configure has autodetection, so if you hav things like xvid or x264 installed it will enable them. he suggests using: 
**./configure --prefix=/usr/local --confdir=/etc/mplayer --enable-gui --enable-largefiles --enable-menu**

i believe the problem lies in the **--enable-x264** option, the autodetect must not like being told to enable it when it already is, so just taking **--enable-x264** off the **./configure** statment should work. 

i said *should* work because i used my own configure options:
**./configure --enable-gui --enable-x11 --enable-largefiles --enable-menu**
and everything works, i can play and encode x264 files just fine.

note: i tried using **--disable-gui** and got a similar problem to the x264, same when using **./configure** by itself, so i suggest using the **--enable-gui** option

---

### Post by Bachstelze on 2006-08-27
I tried your ./configure lines, both end up with the same error :

```
mencoder.o:(.data+0x1618): undefined reference to `fribidi_charset'
mencoder.o:(.data+0x163c): undefined reference to `flip_hebrew'
mencoder.o:(.data+0x1660): undefined reference to `flip_hebrew'
mencoder.o:(.data+0x1684): undefined reference to `fribidi_flip_commas'
mencoder.o:(.data+0x16a8): undefined reference to `fribidi_flip_commas'
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1

```

Thanks for the help :)

---

### Post by ashrack on 2006-08-30
is there a way to have MPLAYER use the GTK FILE SELECTOR when opening files?
Cos it says that the latest version supports GTK2+ and so IMHO it also supports the GTK FILE SELECTOR!

---

### Post by Bachstelze on 2006-09-01
All right so for some reson I had to reinstall my whole Ubunu an indeed, on a _fresh_ install, it works fine :D 

But I still have a problem, mplayer can't play my MKVs, I get "no tream found". I tried compiling with --enable-mtroska or --enable-mkv but none of them are accepted, any ideas ?

**EDIT :** Fixed, libebml and libmatroska are needed to read MKVs, they're not in the repos but instructions on how to compile them from source are [here](http://www.bunkus.org/videotools/mkvtoolnix/source.html#lib). Maybe someone could add this to the main post ?

---

### Post by hellfire_bg on 2006-09-04
I compiled mplayer with x264 enabled witout problems but it doesn`t appear in the codecs tab. Is this normal? Except this it is not using x264 for decoding  video files encoded with x264. For example this is what happened when i tried to open a sample file, encoded with x264:
> 
 hellfire@debian:~/Movies/Contact$ mplayer Sample.avi
MPlayer dev-SVN-r19666-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2200+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
&#1050;&#1086;&#1084;&#1087;&#1080;&#1083;&#1080;&#1088;&#1072;&#1085; &#1079;&#1072; x86 &#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1086;&#1088;&#1080; &#1089; &#1088;&#1072;&#1079;&#1096;&#1080;&#1088;&#1077;&#1085;&#1080;&#1103;: MMX MMX2 3DNow 3DNowEx SSE
&#1044;&#1086;&#1073;&#1072;&#1074;&#1077;&#1090;&#1077; "echo 1024 > /proc/sys/dev/rtc/max-user-freq" &#1082;&#1098;&#1084; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1085;&#1080;&#1090;&#1077; &#1089;&#1090;&#1072;&#1088;&#1090;&#1086;&#1074;&#1080; &#1089; &#1082;&#1088;&#1080;&#1087;&#1090;&#1086;&#1074;&#1077;.
&#1042;&#1098;&#1079;&#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1077;&#1078;&#1076;&#1072;&#1085;&#1077; &#1085;&#1072; Sample.avi.
[mkv] Will play video track 1
Matroska &#1092;&#1086;&#1088;&#1084;&#1072;&#1090;.
VIDEO:  [avc1]  1280x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1085;&#1077; &#1085;&#1072; &#1074;&#1080;&#1076;&#1077;&#1086; &#1076;&#1077;&#1082;&#1086;&#1076;&#1077;&#1088;: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
&#1054;&#1090;&#1074;&#1072;&#1088;&#1103;&#1085;&#1077; &#1085;&#1072; &#1072;&#1091;&#1076;&#1080;&#1086; &#1076;&#1077;&#1082;&#1086;&#1076;&#1077;&#1088;: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  384.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================

You will notice that it is written in bulgarian (i compiled mplayer with --language=bg). Basically it tells me that it will use [ffh264] vfm: ffmpeg (FFmpeg H.264) as video codec and [liba52] AC3 decoding with liba52 as audio codec. It also tells me that my system is too slow for watching this video file (and my system is Athlon Xp 2200+ (1800Mhz), 512mb ddr, GForce FX 5200).

---

### Post by CaveRat on 2006-09-04
libdvdcss2
To get DVDs working I followed these instructions here
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
under the heading "Playing DVDs" again worked great for me, I can now watch encrypted DVDs no problem.

Hope this helps someone in the future!


WOOT! Oh yes! This was all I needed to watch a DVD. Everything else was already installed and enabled, including the regionset. It took awhile for the movie to start after activating it in MPlayer. Once it did, Terminator 3 ran flawlessly smooth and clear in full screen mode. Thanks all.

---

### Post by abu_nawas on 2006-09-07
i'm having problem to display the subtitle. i use vobsub in windows. it was muxed with mp4box on windows.
can anyone tell me how to display those subtitle with mplayer?

---

### Post by gommle on 2006-09-07
Press "J". Or right click and select sub track.

---

### Post by ashrack on 2006-09-07
> **ashrack said:**
> is there a way to have MPLAYER use the GTK FILE SELECTOR when opening files?
Cos it says that the latest version supports GTK2+ and so IMHO it also supports the GTK FILE SELECTOR!

anyone knows?

---

### Post by abu_nawas on 2006-09-08
> **gommle said:**
> Press "J". Or right click and select sub track.
it doesn't work. it's a mp4 file. i pressed "j" and nothing happens

---

### Post by soonlar on 2006-09-15
Where can I find the lastest HOWTO on this?

---

### Post by rgeddes on 2006-09-16
I followed the instructions to compile the mplayer using gcc 4.0.3.  From the update to the instruction set, I understand mplayer will compile with gcc 4.0.

Executing 'make' in the mplayer directory finished with:

make: *** [mplayer] Error 1

I assumed maybe this was not a bad thing so I proceeded with  'sudo make install' which finished with (you guessed it):

make: *** [mplayer] Error 1

A few questions about the process:

1. It seems that I have a few files and directories that were created on my disk... which ones they are and where they reside is a bit of a mystery.  I'd like to undo the install that produced the error messages to remove the files/dirs.  Is that easily done?  If yes, how so?  If not, what is the usual procedure to clean up the garbage so I can try again?

2. Does the update to the install include gcc 4.0.x or does it mean exactly 4.0?

Thanx
Rich

---

### Post by eternalsword on 2006-09-18
One thing to note that may not be particularly obvious is that if you have compiled and installed the dvdnav libraries ie for building vlc then if you want to use mpdvdkit2 instead (default dvd playback) then you need to give the flag --disable-dvdnav

also, it's typically not a good idea to have --enable flags on codecs when they automatically enable if they are detected.  it makes for less hastle when looking for what's wrong in the configuration.

also for those interested, i'll be compiling mplayer and x264 either weekly or biweekly, so I'll make a tarball of the source.  the first mplayer tarball is at [http://cs.wheaton.edu/~mbucy/files/mplayer1.0svn20060918.tar.bz2](http://cs.wheaton.edu/~mbucy/files/mplayer1.0svn20060918.tar.bz2)  and the first x264 tarball is at [http://cs.wheaton.edu/~mbucy/files/x264svn20060917.tar.bz2](http://cs.wheaton.edu/~mbucy/files/x264svn20060917.tar.bz2)

---

### Post by eternalsword on 2006-09-18
> **rgeddes said:**
> I followed the instructions to compile the mplayer using gcc 4.0.3.  From the update to the instruction set, I understand mplayer will compile with gcc 4.0.

Executing 'make' in the mplayer directory finished with:

make: *** [mplayer] Error 1

I assumed maybe this was not a bad thing so I proceeded with  'sudo make install' which finished with (you guessed it):

make: *** [mplayer] Error 1

A few questions about the process:

1. It seems that I have a few files and directories that were created on my disk... which ones they are and where they reside is a bit of a mystery.  I'd like to undo the install that produced the error messages to remove the files/dirs.  Is that easily done?  If yes, how so?  If not, what is the usual procedure to clean up the garbage so I can try again?

2. Does the update to the install include gcc 4.0.x or does it mean exactly 4.0?

Thanx
Rich

Once it compiles correctly when you make install that version it will overwrite the garbage.

As for why it's not compiling, see what happens if you get rid of all of the --enable flags (other than --enable-gui --enable-largefiles and --enable-menu) in the ./configure line it could be that you're unwittingly asking for it to use a library you don't have.  Then from the configure output, look for the things that you want enabled and make sure it says yes.  if it doesn't then you don't have it.

And as always when compiling, make sure to run "make distclean" when available before trying again.

---

### Post by eternalsword on 2006-09-18
> **soonlar said:**
> Where can I find the lastest HOWTO on this?

this howto works just fine, no need for another one.  although it might be of use that in order to have xvid enabled, you need the libxvidcore libraries installed.

---

### Post by rgeddes on 2006-09-19
> **eternalsword said:**
> Once it compiles correctly when you make install that version it will overwrite the garbage.

As for why it's not compiling, see what happens if you get rid of all of the --enable flags (other than --enable-gui --enable-largefiles and --enable-menu) in the ./configure line it could be that you're unwittingly asking for it to use a library you don't have.  Then from the configure output, look for the things that you want enabled and make sure it says yes.  if it doesn't then you don't have it.

And as always when compiling, make sure to run "make distclean" when available before trying again.

Thank you for the advise.  I configured the compile as you said and the make and make install finished without incident.

Also the command: sudo cp -R default/ /usr/share/mplayer/Skin/  had a problem.  There is no Skin dir, however there is a skin dir... I changed it accrodingly and it went through.

When I run mplayer, I get a message:
New_Face failed.  Maybe the font path is wrong.
Please supply the text font file(~/.mplayer/subfont.ttf).  
I assume it's referring to the subtitle font.  Can I just make the soft link  ~/.mplayer/subfont.ttf and point it to my favorite font?

When I play a movie, it seems to pause about every second roughly... any thoughts on that?

Also, the main reason I undertook this adventure was to use mplayer with jack... could it be to run ./configure with --enable-jack ?

Rich

---

### Post by eternalsword on 2006-09-19
> **rgeddes said:**
> Thank you for the advise.  I configured the compile as you said and the make and make install finished without incident.

Also the command: sudo cp -R default/ /usr/share/mplayer/Skin/  had a problem.  There is no Skin dir, however there is a skin dir... I changed it accrodingly and it went through.

When I run mplayer, I get a message:
New_Face failed.  Maybe the font path is wrong.
Please supply the text font file(~/.mplayer/subfont.ttf).  
I assume it's referring to the subtitle font.  Can I just make the soft link  ~/.mplayer/subfont.ttf and point it to my favorite font?

When I play a movie, it seems to pause about every second roughly... any thoughts on that?

Also, the main reason I undertook this adventure was to use mplayer with jack... could it be to run ./configure with --enable-jack ?

Rich

for the subfont.ttf, yes you can soft link to your favorite font.  As for the other problems, you should probably get in touch with the mplayer folks for that.  Either through their mailing list or they have a channel #mplayer on freenode

---

### Post by hamil on 2006-09-21
Hello!

Running make, gives me an error message.
Any thoughts on how to resolve that?

```
libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x4b): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x75): undefined reference to `x264_param_default'
:x264.c:(.text+0x3d7): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x53c): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x618): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x6ea): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x78b): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

Thanks!

---

### Post by soonlar on 2006-09-22
...but it works in MEPIS just fine.
You know what I gave up on getiting this to work in Ubuntu and installed Mepis 6.0.  It has kmplayer already installed and working.  It is based on Ubuntu 6.06 also which is nice.

---

### Post by MedievalAnubis on 2006-09-23
> **hamil said:**
> Hello!

Running make, gives me an error message.
Any thoughts on how to resolve that?

```
libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x4b): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x75): undefined reference to `x264_param_default'
:x264.c:(.text+0x3d7): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x53c): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x618): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x6ea): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x78b): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

Thanks!

Yea I was experiencing the same problem. The only solution seems to be just to remove --enable-x264 from the configure command line 

new configure command
```
 ./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --with-win32libdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --enable-xvid
```

But if you want to keep x264 support try updating the SVN for it again and recompiling it. They may have updated it by now.

---

### Post by eternalsword on 2006-09-23
the x264 from here [http://cs.wheaton.edu/~mbucy/files/x264svn20060917.tar.bz2](http://cs.wheaton.edu/~mbucy/files/x264svn20060917.tar.bz2) should work.

---

### Post by eternalsword on 2006-09-23
also, I would suggest anything with --enable to leave it out other than --enable-gui --enable-menu and --enable-largefiles  because the rest of the stuff is autodetected.  You can check the configure output to see if everything you want is there.  If something you want has NO beside it then you don't have it installed or don't have it properly set up.

---

### Post by hamil on 2006-09-24
> **eternalsword said:**
> the x264 from here [http://cs.wheaton.edu/~mbucy/files/x264svn20060917.tar.bz2](http://cs.wheaton.edu/~mbucy/files/x264svn20060917.tar.bz2) should work.

Well... This one did not work either, I got the same errormessage from make.
I updated the SVN versions today, so I got Mplayer build 19964 and x264 build 565, and then it actually worked again.

Did build Mplayer with the config options that eternalsword suggested, since everything else got autodetected, as you told me. Thanks.

---

### Post by kerme8503 on 2006-09-24
I cant even edit my "sources.list"!!!  it says i dont have permission even though i am the admin on this compy!!  ahh! how can i change that?

---

### Post by hamil on 2006-09-24
> **kerme8503 said:**
> I cant even edit my "sources.list"!!!  it says i dont have permission even though i am the admin on this compy!!  ahh! how can i change that?

Hmmm... By typing:
sudo gedit /etc/apt/sources.list

---

### Post by kerme8503 on 2006-09-24
your a good man...thank you lol

---

### Post by kerme8503 on 2006-09-24
so i did everything in the guide to a t...but i am confuzed about installing a skin... i downloaded Cyrus and extracted it and renamed it "default"  like it it says.  but after that nothing works...  

and i was like "maybe it will work without the skin" so i ran ```
mplayer /home/erik/azureusdownloads/"Greys Anatomy"/greys.anatomy.s01e01.hdtv-lol.avi
``` and it didnt work...this is what i got  
```
 erik@ubuntu:~$ mplayer /home/erik/azureusdownloads/"Greys Anatomy"/greys.anatomy.s01e01.hdtv-lol.avi
bash: mplayer: command not found

```

---

### Post by keheikev on 2006-09-24
I know this thread is long and old but can someone help me and another poster after we updated firefox mplayer plugin stopped working for us  I originally tried this thread for my install which looks much simpler and doesnt have near the jargon of svn vs svc or what have you and [http://www.ubuntuforums.org/showthread.php?t=135364](http://www.ubuntuforums.org/showthread.php?t=135364)
So basically I can open mplayer but the plugin is not working....
Kiheikev
Aloha!

---

### Post by hamil on 2006-09-25
> **kerme8503 said:**
> so i did everything in the guide to a t...but i am confuzed about installing a skin... i downloaded Cyrus and extracted it and renamed it "default"  like it it says.  but after that nothing works...  

and i was like "maybe it will work without the skin" so i ran ```
mplayer /home/erik/azureusdownloads/"Greys Anatomy"/greys.anatomy.s01e01.hdtv-lol.avi
``` and it didnt work...this is what i got  
```
 erik@ubuntu:~$ mplayer /home/erik/azureusdownloads/"Greys Anatomy"/greys.anatomy.s01e01.hdtv-lol.avi
bash: mplayer: command not found

```
With the skin its directory, try to issue the command:
gmplayer (at least, that is the startcommand I use for the Mplayer in my Gnome enviroment) Why you get that error message with the mplayer command, I do not know..

---

### Post by hamil on 2006-09-25
> **keheikev said:**
> I know this thread is long and old but can someone help me and another poster after we updated firefox mplayer plugin stopped working for us  I originally tried this thread for my install which looks much simpler and doesnt have near the jargon of svn vs svc or what have you and [http://www.ubuntuforums.org/showthread.php?t=135364](http://www.ubuntuforums.org/showthread.php?t=135364)
So basically I can open mplayer but the plugin is not working....
Kiheikev
Aloha!

If you open a new tab in Firefox, and write:
```
about:plugins
```
in the adress field, what is the output?

---

### Post by kerme8503 on 2006-09-25
ok i found the only dir with a "skin" and copied the files there.  i ran gmplayer and it gave me a "command not found" again...

---

### Post by keheikev on 2006-09-25
Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
 It says nothing about the mplayer plugin I will check synaptic to see for sure that it is installed.
What could be up?
TIA
Kiheikev

---

### Post by Josh1 on 2006-09-26
Woot, thanks alot :D.

---

### Post by Wargle on 2006-09-27
Hi, Im a complete noob to unix, but im giving ubuntu a try and ive tried to complie mplayer but i get to the make stage for mplayer and get the following error. Now i cant for the life of me see why I have followed the instructions to the letter but cant see where to look next.

libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x4b): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x75): undefined reference to `x264_param_default'
:x264.c:(.text+0x3d7): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x53c): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x618): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x6ea): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x798): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


Thx for any help you can provide.](*,)  <- this is me right now

---

### Post by Treviño on 2006-09-27
I don't know if anyone has written here, btw to ***enable the amr audio*** support (*needed to play correctly 3gp videos made for/by mobile phones*) you need to untar [this file]("http://www.fastdump.net/16366") to your Mplayer-sources/libavcodec/ directory (recompile the amrwb_float and amr_float directories content, if needed)... Then run ./configure with your favourite settings and you'll see that the _amr_wb_ and _amr_nb_ are now enabled codecs!

After you've compiled try to play a .3gp/.amr file and it will work perfectly! ;)

---

### Post by eternalsword on 2006-09-28
> **Wargle said:**
> Hi, Im a complete noob to unix, but im giving ubuntu a try and ive tried to complie mplayer but i get to the make stage for mplayer and get the following error. Now i cant for the life of me see why I have followed the instructions to the letter but cant see where to look next.

```

libavcodec/libavcodec.a(x264.o): In function `X264_close':x264.c:(.text+0x4b): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':x264.c:(.text+0x75): undefined reference to `x264_param_default'
:x264.c:(.text+0x3d7): undefined reference to `x264_encoder_open'
:x264.c:(.text+0x53c): undefined reference to `x264_encoder_headers'
:x264.c:(.text+0x618): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':x264.c:(.text+0x6ea): undefined reference to `x264_encoder_encode'
:x264.c:(.text+0x798): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

Thx for any help you can provide.](*,)  <- this is me right now

First, did x264 compile and install correctly?  Second, have you tried updating from svn to get the most recent code?

---

### Post by Wargle on 2006-09-29
Thanks eternalsworld, Im pretty sure x264 did complile properly, however since then, I have manually recompiled all codecs and installed them, then did an update through synaptic to install mplayer which has worked fine, with all codecs working, just having trouble installing a new skin now, i did download the quicksilver skin followed the instructions and copied it to the folders specified in the HowTo but its not showing up at, even after using the skin picker in mplayer, not an essential as the main function of the program is working 100%, thanks for the advice though.

---

### Post by eternalsword on 2006-09-30
> **Wargle said:**
> Thanks eternalsworld, Im pretty sure x264 did complile properly, however since then, I have manually recompiled all codecs and installed them, then did an update through synaptic to install mplayer which has worked fine, with all codecs working, just having trouble installing a new skin now, i did download the quicksilver skin followed the instructions and copied it to the folders specified in the HowTo but its not showing up at, even after using the skin picker in mplayer, not an essential as the main function of the program is working 100%, thanks for the advice though.

Installing mplayer from synaptic will not give you x264 capability, but if you're just interested in h264 playback, then you're fine.  x264 is for h264 encoding, so it's for mencoder, not mplayer.

as for the skins, they should be in
/usr/share/mplayer/skins
rather than /usr/share/mplayer/Skin

---

### Post by bobbymcsteels on 2006-10-01
I had exactly the same error msg... is there another way round it or just use apt-get install mplayer??

---

### Post by cor2y on 2006-10-05
yes i just tried following all the steps to recompile mplayer and i got this X264 error.
Is it because they upgraded the codec and now theres problems?

Ok Update
To get x264 to behave you have to emove it from the ./configure argument it will be enabled automatically.

---

### Post by soongwoo on 2006-10-06
You mean just compile mplayer without x264?
Cane the output, mplayer, handle x264?

soongwoo

---

### Post by eternalsword on 2006-10-06
> **soongwoo said:**
> You mean just compile mplayer without x264?
Cane the output, mplayer, handle x264?

soongwoo


What he means is that for some reason manually enabling x264 messes up the build process.  If x264 has been compiled and installed it will be enabled automatically.

---

### Post by Cogito² on 2006-10-07
When going through the guide and I try to install the actual mplayer, it ends with this:

```
mplayer/gtk/fs.c:36: warning: pointer targets in initialization differ in signedness
mplayer/gtk/fs.c: In function 'fs_fsFilterCombo_activate':
mplayer/gtk/fs.c:373: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c: In function 'fs_fsFilterCombo_changed':
mplayer/gtk/fs.c:382: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c: In function 'fs_fsPathCombo_activate':
mplayer/gtk/fs.c:420: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c:421: warning: pointer targets in passing argument 1 of 'chdir' differ in signedness
mplayer/gtk/fs.c: In function 'fs_fsPathCombo_changed':
mplayer/gtk/fs.c:428: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c:430: warning: pointer targets in passing argument 1 of 'chdir' differ in signedness
mplayer/gtk/fs.c: In function 'fs_Up_released':
mplayer/gtk/fs.c:436: warning: pointer targets in assignment differ in signedness
mplayer/gtk/fs.c:438: warning: pointer targets in passing argument 2 of 'gtk_entry_set_text' differ in signedness
mplayer/gtk/fs.c: In function 'fsFileExist':
mplayer/gtk/fs.c:444: warning: pointer targets in passing argument 1 of 'fopen' differ in signedness
mplayer/gtk/fs.c: In function 'fs_Ok_released':
mplayer/gtk/fs.c:461: warning: pointer targets in assignment differ in signedness
mplayer/gtk/fs.c:463: warning: pointer targets in passing argument 2 of 'gtk_entry_set_text' differ in signedness
mplayer/gtk/fs.c:470: warning: pointer targets in assignment differ in signedness
mplayer/gtk/fs.c:473: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c:474: warning: pointer targets in assignment differ in signedness
mplayer/gtk/fs.c:475: warning: pointer targets in passing argument 1 of 'fsFileExist' differ in signedness
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I.. -I../loader -I./wm -I./skin -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -DDEBUG  -o mplayer/gtk/opts.o mplayer/gtk/opts.c
mplayer/gtk/opts.c: In function 'prEntry':
mplayer/gtk/opts.c:481: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/opts.c:489: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/opts.c: In function 'prButton':
mplayer/gtk/opts.c:552: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/opts.c:573: warning: initialization discards qualifiers from pointer target type
mplayer/gtk/opts.c:581: warning: initialization discards qualifiers from pointer target type
mplayer/gtk/opts.c:602: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/opts.c:603: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/opts.c: In function 'getGtkEntryText':
mplayer/gtk/opts.c:1409: warning: initialization discards qualifiers from pointer target type
mplayer/gtk/opts.c: In function 'audioButton':
mplayer/gtk/opts.c:1480: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1482: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1484: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1490: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1492: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1494: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1500: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1506: warning: passing argument 1 of 'gfree' from incompatible pointer type
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I.. -I../loader -I./wm -I./skin -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -DDEBUG  -o mplayer/gtk/url.o mplayer/gtk/url.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I.. -I../loader -I./wm -I./skin -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -DDEBUG  -o mplayer/gtk/eq.o mplayer/gtk/eq.c
mplayer/gtk/eq.c: In function 'ecButtonReleased':
mplayer/gtk/eq.c:542: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/eq.c:543: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/eq.c:544: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/eq.c:545: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/eq.c:546: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
mplayer/gtk/eq.c:547: warning: passing argument 1 of 'gstrdup' discards qualifiers from pointer target type
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I.. -I../loader -I./wm -I./skin -I/usr/include/freetype2 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -DDEBUG  -o mplayer/gtk/common.o mplayer/gtk/common.c
rm -f libgui.a
ar rc libgui.a wm/ws.o wm/wsxdnd.o app.o interface.o cfg.o bitmap.o skin/skin.o skin/font.o skin/cut.o mplayer/widgets.o mplayer/play.o mplayer/mw.o mplayer/sw.o mplayer/menu.o mplayer/pb.o mplayer/common.o mplayer/gtk/menu.o mplayer/gtk/mb.o mplayer/gtk/about.o mplayer/gtk/pl.o mplayer/gtk/sb.o mplayer/gtk/fs.o mplayer/gtk/opts.o mplayer/gtk/url.o mplayer/gtk/eq.o mplayer/gtk/common.o
true libgui.a
make[1]: Leaving directory `/home/thomas/Desktop/MPlayer-1.0pre8/Gui'
make -C libmenu
make[1]: Entering directory `/home/thomas/Desktop/MPlayer-1.0pre8/libmenu'
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu.o menu.c
menu.c: In function 'menu_draw_box':
menu.c:594: warning: pointer targets in passing argument 3 of 'draw_alpha' differ in signedness
menu.c:594: warning: pointer targets in passing argument 4 of 'draw_alpha' differ in signedness
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o vf_menu.o vf_menu.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_cmdlist.o menu_cmdlist.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_pt.o menu_pt.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_list.o menu_list.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_filesel.o menu_filesel.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_txt.o menu_txt.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_console.o menu_console.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_param.o menu_param.c
cc -c -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64   -I. -I.. -I../libmpcodecs   -I/usr/include/freetype2 -o menu_dvbin.o menu_dvbin.c
In file included from ../libmpdemux/dvbin.h:11,
                 from menu_dvbin.c:27:
../libmpdemux/dvb_defaults.h:73:3: warning: #warning No DVB-T country defined in dvb_defaults.h, defaulting to UK. Ignore this if using Satellite or Cable.
ar r libmenu.a menu.o vf_menu.o menu_cmdlist.o menu_pt.o menu_list.o menu_filesel.o menu_txt.o menu_console.o menu_param.o menu_dvbin.o
ar: creating libmenu.a
true libmenu.a
make[1]: Leaving directory `/home/thomas/Desktop/MPlayer-1.0pre8/libmenu'
cc -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT    -I./libavutil -I./libavcodec   -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a libmenu/libmenu.a vidix/libvidix.a Gui/libgui.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit libavcodec/libavcodec.a  libavformat/libavformat.a  libavutil/libavutil.a  libpostproc/libpostproc.a  -lmad  -ltheora -logg   -lmp3lame   -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread  -lx264 -lpthread -lmpcdec   -lfaac -lfreetype -lz -lncurses  -lnsl       -lfontconfig   libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0    -lGL -ldl  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread      -L/usr/lib -lcaca -lslang -lX11 -L/usr/X11R6/lib -lncurses -lncurses    -L/usr/lib -lesd -laudiofile -lm   -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic  -lm
/usr/bin/ld: cannot open output file mplayer: Is a directory
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```

When I search through my folders, usr/share/mplayer doesn't even exist. I've tried going through the installation like 3 times now and it's never worked. I wan't really sure if anyone could help me with the information that I've given. If so, then thanks for any help.

---

### Post by Old Pink on 2006-10-07
> **Cogito² said:**
> When going through the guide and I try to install the actual mplayer, it ends with this:

```
***removed***
```When I search through my folders, usr/share/mplayer doesn't even exist. I've tried going through the installation like 3 times now and it's never worked. I wan't really sure if anyone could help me with the information that I've given. If so, then thanks for any help.

Run ```
sudo aptitude install mplayer
``` in terminal. :)

---

### Post by Cogito² on 2006-10-08
> **Matt.H said:**
> Run ```
sudo aptitude install mplayer
``` in terminal. :)

Awesome that worked. Thanks a lot. What, if I may ask, did that do? Why wasn't the normal installation working for me?

---

### Post by Cogito² on 2006-10-08
> **helpdeskdan said:**
> I just installed the mplayer plugin.  Combined with my compiled mplayer, it works better than anything I've ever seen on linux. 

Very quick/dirty  instructions (after you have downloaded the source):
1. sudo apt-get firefox-dev (will also install libnss-dev, libnspr-dev)
 
2.  Get gecko-sdk [http://developer.mozilla.org/en/docs/Gecko_SDK#Downloading]("http://developer.mozilla.org/en/docs/Gecko_SDK#Downloading")

3.  tar -xzf it in your home dir (for lack of not being sure where to put it)

4.  ./configure --with-gecko-sdk=~/gecko-sdk
(If I were smarter, I could tell you the proper way to do this, but this works)

5.  make

6.  su or sudo:
cp mplayerplug-in*.so /usr/lib/mozilla-firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/mozilla-firefox/components
Just to be sure, I also did:
cp mplayerplug-in*.so /usr/lib/firefox/plugins
cp mplayerplug-in*.xpt /usr/lib/firefox/components
(not sure why there are two directories.  Again, if I were smarter...)

7.  Restart firefox and enjoy!

Perhaps somebody may find this information usefull; will be happy to clarify vague details if needed.

Hi I'm trying to follow these directions, but when typing "sudo apt-get firefox-dev" into the terminal, it says, "E: Invalid operation firefox-dev". What am I doing wrong here? Thanks for any help.

---

### Post by Rob2687 on 2006-10-08
apt-get **install** firefox-dev

---

### Post by Cogito² on 2006-10-08
> **Rob2687 said:**
> apt-get **install** firefox-dev

Hey thanks that worked.

But I just tried:

tar -xzf gecko-sdk-i686-pc-linux-gnu-1.8.0.4.tar.bz2

but it tells me:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

I checked up on a couple websites and I can't figure out why I'm doing the command wrong. If anyone notices anything stupid I'm doing any help would be appreciated. Thanks.

---

### Post by eternalsword on 2006-10-09
> **Cogito² said:**
> Hey thanks that worked.

But I just tried:

tar -xzf gecko-sdk-i686-pc-linux-gnu-1.8.0.4.tar.bz2

but it tells me:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

I checked up on a couple websites and I can't figure out why I'm doing the command wrong. If anyone notices anything stupid I'm doing any help would be appreciated. Thanks.
z is for gzip j is for bunzip
tar -xjf gecko-sdk-i686-pc-linux-gnu-1.8.0.4.tar.bz2

---

### Post by tdlofcc on 2006-10-14
Hi, I'm using this howto to install mplayer with the x264 codec, but I get this error shown below when doing the "make" command.

It's different from the "error 2" I saw described in post #83.
```
x264.c: In function 'X264_init':
x264.c:149: error: 'struct <anonymous>' has no member named 'i_rf_constant'
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/tdl/essential-20060611/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
tdl@Goliath:~/essential-20060611/mplayer$

```

Any help would be greatly apreciated :)

Since after checking out mplayer, I might never have to use Windows again ;)

---

### Post by cyan.ogilvie on 2006-10-14
It looks to me like the attribute 'i_rf_constant' in the x264 struct x264_param_t was renamed to f_rf_constant, and (I guess) changed from an int to a float.  I hacked my mplayer sources on the line that was being complained about to change the name from i_rf_constant to f_rf_constant, and in a fit of paranoia added a '* 1.0' to force the expression to evaluate as a float.

A basic test (using the crf option of x264encopts) seems to work on my system (with mplayer and x264 from svn today)

---

### Post by tdlofcc on 2006-10-16
Hrm. How come movies (divx avi) look alot worse in mplayer than under mediaplayer classic (running under winxp ofcourse)

Because I can count the pixels under mplayer, while Ive seen the movies under  Windows XP looking great ... any ideas ?

---

### Post by eternalsword on 2006-10-17
> **tdlofcc said:**
> Hrm. How come movies (divx avi) look alot worse in mplayer than under mediaplayer classic (running under winxp ofcourse)

Because I can count the pixels under mplayer, while Ive seen the movies under  Windows XP looking great ... any ideas ?

What sort of graphics card do you have?  Does it support hardware scaling?  If not did you compile mplayer with software scaling capability?

---

### Post by eternalsword on 2006-10-18
> **cyan.ogilvie said:**
> It looks to me like the attribute 'i_rf_constant' in the x264 struct x264_param_t was renamed to f_rf_constant, and (I guess) changed from an int to a float.  I hacked my mplayer sources on the line that was being complained about to change the name from i_rf_constant to f_rf_constant, and in a fit of paranoia added a '* 1.0' to force the expression to evaluate as a float.

A basic test (using the crf option of x264encopts) seems to work on my system (with mplayer and x264 from svn today)

this has been fixed in the current revision of ffmpeg

---

### Post by LucasLinard on 2006-10-19
Hi. After i run the make command I get the following error:

> libavcodec/libavcodec.a(x264.o): In function `X264_close':
x264.c:(.text+0x1b): undefined reference to `x264_encoder_close'
libavcodec/libavcodec.a(x264.o): In function `X264_init':
x264.c:(.text+0x45): undefined reference to `x264_param_default'
x264.c:(.text+0x3bb): undefined reference to `x264_encoder_open'
x264.c:(.text+0x4fa): undefined reference to `x264_encoder_headers'
x264.c:(.text+0x5a4): undefined reference to `x264_nal_encode'
libavcodec/libavcodec.a(x264.o): In function `X264_frame':
x264.c:(.text+0x6dc): undefined reference to `x264_encoder_encode'
x264.c:(.text+0x736): undefined reference to `x264_nal_encode'
collect2: ld returned 1 exit status
make: ** [mplayer] Erro 1


CAn you help me?
I'm using Edgy eft, x264 compilled successfuly.

---

### Post by eternalsword on 2006-10-19
> **LucasLinard said:**
> Hi. After i run the make command I get the following error:




CAn you help me?
I'm using Edgy eft, x264 compilled successfuly.

do you have current svn of both?  always update them together.  If something is still wrong, then likely a change to one still needs an update in the other.

---

### Post by LucasLinard on 2006-10-19
I removed the --enagble-x264 at the end of the command.
It went OK!

---

### Post by cvmostert on 2006-10-26
> **Treviño said:**
> I don't know if anyone has written here, btw to ***enable the amr audio*** support (*needed to play correctly 3gp videos made for/by mobile phones*) you need to untar [this file]("http://www.fastdump.net/16366") to your Mplayer-sources/libavcodec/ directory (recompile the amrwb_float and amr_float directories content, if needed)... Then run ./configure with your favourite settings and you'll see that the _amr_wb_ and _amr_nb_ are now enabled codecs!

After you've compiled try to play a .3gp/.amr file and it will work perfectly! ;)

Has anyone by chance made a .deb for this?

---

### Post by sup on 2006-10-29
I had the same problem with x264 so I disabled it (xine can play them for me, I do not have any anyway).

However, I compiled RC1 and now update manager complies that it has an update to pre8 - any ideas how to turn it off? I tried locking version and forcing version through synaptic, but without much succes:-/

---

### Post by Rob2687 on 2006-11-04
Anybody been keeping up with the SVN builds?
I get an error with gmplayer when playing any videos. This started happening since builds from like a week ago.
> [ws] Error in display.
[ws]  Error code: 2 ( BadValue (integer parameter out of range for operation) )
[ws]  Request code: 12
[ws]  Minor code: 0
[ws]  Modules: init_video_codec


Using the command line mplayer seems to work fine though.

---

### Post by janfsd on 2006-11-24
Thanks for the excellent guide...It work for me flawlessly. However the configure scripts have changed and now to compile you should write:

```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --win32codecsdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa 

```
Notice that it's without --enable-xvid --enable-x264, since both options give some errors on compilation, however they are automatically detected so even no need for writing them.
Notice too, that --win32codecsdir has been replaced by --with-win32libdir

---

### Post by sapo on 2006-11-24
> **janfsd said:**
> Thanks for the excellent guide...It work for me flawlessly. However the configure scripts have changed and now to compile you should write:

```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --enable-theora --confdir=/etc/mplayer --win32codecsdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa 

```
Notice that it's without --enable-xvid --enable-x264, since both options give some errors on compilation, however they are automatically detected so even no need for writing them.
Notice too, that --win32codecsdir has been replaced by --with-win32libdir

Thanx, i ll update the first page.

---

### Post by jurgnn on 2006-11-26
<removed old post>

Nevermind, I removed all mplayer files and downloaded new sources from svn, now it works well, was prolly just bug.

---

### Post by Rob2687 on 2006-11-26
Enable theora doesn't compile for me on Edgy.

```
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `decode':
vd_theora.c:(.text+0x6f): undefined reference to `theora_decode_packetin'
vd_theora.c:(.text+0x87): undefined reference to `theora_decode_YUVout'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `uninit':
vd_theora.c:(.text+0x15c): undefined reference to `theora_clear'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `init':
vd_theora.c:(.text+0x1e9): undefined reference to `theora_info_init'
vd_theora.c:(.text+0x1f4): undefined reference to `theora_comment_init'
vd_theora.c:(.text+0x227): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x262): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x29d): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x2b1): undefined reference to `theora_decode_init'
libmpdemux/libmpdemux.a(demux_ogg.o): In function `demux_ogg_open':
demux_ogg.c:(.text+0x2fec): undefined reference to `theora_info_init'
demux_ogg.c:(.text+0x2ffb): undefined reference to `theora_comment_init'
demux_ogg.c:(.text+0x3012): undefined reference to `theora_decode_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

---

### Post by jharris on 2006-11-26
Hi there, thanks for this guide. However, I am getting the same errors as the person above:

```
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `decode':
vd_theora.c:(.text+0x8a): undefined reference to `theora_decode_packetin'
vd_theora.c:(.text+0xa2): undefined reference to `theora_decode_YUVout'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `uninit':
vd_theora.c:(.text+0x176): undefined reference to `theora_clear'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `init':
vd_theora.c:(.text+0x220): undefined reference to `theora_info_init'
vd_theora.c:(.text+0x228): undefined reference to `theora_comment_init'
vd_theora.c:(.text+0x25b): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x296): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x2d1): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x2e5): undefined reference to `theora_decode_init'
libmpdemux/libmpdemux.a(demux_ogg.o): In function `demux_ogg_open':
demux_ogg.c:(.text+0x3020): undefined reference to `theora_info_init'
demux_ogg.c:(.text+0x3028): undefined reference to `theora_comment_init'
demux_ogg.c:(.text+0x303f): undefined reference to `theora_decode_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```
I followed the guide to the letter, so i'm not sure as to what to do next. Any help would greatly be appreciated.

-Jason

*edit* I'm attempting this with Edgy.

---

### Post by Rob2687 on 2006-11-26
Remove the --enable-theora line in the ./configure command. It won't be compiled with Theora support of course but oh well..

---

### Post by lime4x4 on 2006-11-26
Having issues with mplayer so i thought i'd start from scratch with your guide and this is as far as i got when trying to install all the denpenceys

The following packages have unmet dependencies:
  libfaac-dev: Depends: libmp4-dev but it is not installable
E: Broken packages

this is on edgy by the way

---

### Post by sup on 2006-11-27
sudo apt-get libmp4v2-dev
(i guess)

---

### Post by jharris on 2006-11-27
> **Rob2687 said:**
> Remove the --enable-theora line in the ./configure command. It won't be compiled with Theora support of course but oh well..

I'm not familiar with Theora, so I guess I won't miss it. Thanks for your reply.

---

### Post by cor2y on 2006-11-28
well i just tried to compile the latest svn of mplayer and got these errors
> 
make[1]: *** [demux_mov.o] Error 1
make[1]: Leaving directory `/home/cor2y/mplayer/libmpdemux'
make: *** [libmpdemux/libmpdemux.a] Error 2

I'm on Dapper decided to give the latest svn a go and now its not problems with x264 or xvid anyomre but libmpdemux.

Anyone know how to fix?

---

### Post by kaminix on 2006-12-02
```
sor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lglib-2.0   -Wl,-z,noexecstack   -lncurses -lpng -lz -ljpeg -lasound -ldl -lpthread -lfreetype -lz -lfontconfig  -lz -lmad -ldts -lmpcdec  -lpthread -ldl -rdynamic  -lm   
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `decode':
vd_theora.c:(.text+0x96): undefined reference to `theora_decode_packetin'
vd_theora.c:(.text+0xae): undefined reference to `theora_decode_YUVout'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `uninit':
vd_theora.c:(.text+0x186): undefined reference to `theora_clear'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `init':
vd_theora.c:(.text+0x233): undefined reference to `theora_info_init'
vd_theora.c:(.text+0x23b): undefined reference to `theora_comment_init'
vd_theora.c:(.text+0x26f): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x2ab): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x2e7): undefined reference to `theora_decode_header'
vd_theora.c:(.text+0x2fb): undefined reference to `theora_decode_init'
libmpdemux/libmpdemux.a(demux_ogg.o): In function `demux_ogg_open':
demux_ogg.c:(.text+0x31ad): undefined reference to `theora_info_init'
demux_ogg.c:(.text+0x31b5): undefined reference to `theora_comment_init'
demux_ogg.c:(.text+0x31cc): undefined reference to `theora_decode_header'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
```


Any ideas?
EDIT: PReferebly without removing Theora-support.

EDIT: I installed it without theora support, now I have no sound. :(
But video works fine.

---

### Post by th3james on 2006-12-14
Im trying to install on edgy, with AMR codec support
I had the same problem as above, so i disabled theora, however, now make fails with

```
libavformat/libavformat.a(x11grab.o): In function `x11grab_read_close':
x11grab.c:(.text+0x2d): undefined reference to `XCloseDisplay'
x11grab.c:(.text+0x46): undefined reference to `XShmDetach'
libavformat/libavformat.a(x11grab.o): In function `x11grab_read_header':
x11grab.c:(.text+0x9c): undefined reference to `XOpenDisplay'
x11grab.c:(.text+0x195): undefined reference to `XShmQueryExtension'
x11grab.c:(.text+0x1c9): undefined reference to `XDefaultScreen'
x11grab.c:(.text+0x218): undefined reference to `XShmCreateImage'
x11grab.c:(.text+0x282): undefined reference to `XShmAttach'
x11grab.c:(.text+0x341): undefined reference to `XGetImage'
libavformat/libavformat.a(x11grab.o): In function `x11grab_read_packet':
x11grab.c:(.text+0x888): undefined reference to `_XReply'
x11grab.c:(.text+0x941): undefined reference to `XQueryPointer'
x11grab.c:(.text+0xb45): undefined reference to `_XReadPad'
x11grab.c:(.text+0xbee): undefined reference to `XShmGetImage'
x11grab.c:(.text+0xc22): undefined reference to `_XFlush'
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1

```

I thought of removing --enable-X11, but i assume this is needed?
any help appreciated

---

### Post by janfsd on 2006-12-14
> **th3james said:**
> Im trying to install on edgy, with AMR codec support
I had the same problem as above, so i disabled theora, however, now make fails with

```
libavformat/libavformat.a(x11grab.o): In function `x11grab_read_close':
x11grab.c:(.text+0x2d): undefined reference to `XCloseDisplay'
x11grab.c:(.text+0x46): undefined reference to `XShmDetach'
libavformat/libavformat.a(x11grab.o): In function `x11grab_read_header':
x11grab.c:(.text+0x9c): undefined reference to `XOpenDisplay'
x11grab.c:(.text+0x195): undefined reference to `XShmQueryExtension'
x11grab.c:(.text+0x1c9): undefined reference to `XDefaultScreen'
x11grab.c:(.text+0x218): undefined reference to `XShmCreateImage'
x11grab.c:(.text+0x282): undefined reference to `XShmAttach'
x11grab.c:(.text+0x341): undefined reference to `XGetImage'
libavformat/libavformat.a(x11grab.o): In function `x11grab_read_packet':
x11grab.c:(.text+0x888): undefined reference to `_XReply'
x11grab.c:(.text+0x941): undefined reference to `XQueryPointer'
x11grab.c:(.text+0xb45): undefined reference to `_XReadPad'
x11grab.c:(.text+0xbee): undefined reference to `XShmGetImage'
x11grab.c:(.text+0xc22): undefined reference to `_XFlush'
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1

```

I thought of removing --enable-X11, but i assume this is needed?
any help appreciated

Try to add --disable-mencoder , I had the same problem with the latest source, that make it compile.

I think that for the latest svn build you should now make like this:
```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --confdir=/etc/mplayer --win32codecsdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa --disable-mencoder
```
I don't use mencoder, so that doesn't matter for me. Notice too that --enable-theora isn't anymore, and I don't think is needed, because it's automatically detected. ( and you shouldn't write it, because it won't compile)
Maybe you should try to change it in your guide, and don't separate it for dapper, for edgy, as far as I know, it should be the same.

---

### Post by th3james on 2006-12-16
Thanks, it works perfectly now!

---

### Post by janfsd on 2007-01-02
Now it seems that mencoder can be compiled again so the option --disable-mencoder is no needed... so it should be something like this:

```
./configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --confdir=/etc/mplayer --win32codecsdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa
```

I checked the mplayer site, and now it seems that there are some amd64 win codecs, but mplayer doesn't detect them anyway... Has anybody make them work for amd64?? Note that the package just has some codecs, it's actually very small, but at least is something...

---

### Post by dpny on 2007-01-02
I am trying to compile the latest mplayer for PPC Ubuntu. However, I'm getting an error message I don't understand when trying to get the dependencies.:

The first is:

```
$ sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxv-dev is already the newest version.
libpng12-dev is already the newest version.
checkinstall is already the newest version.
E: Couldn't find package libavifile-0.7-dev
```

Removing libavifile-0.7-dev gives me the error:

```
. . .
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxv-dev is already the newest version.
libpng12-dev is already the newest version.
checkinstall is already the newest version.
libgtk2.0-dev is already the newest version.
liblame-dev is already the newest version.
libice-dev is already the newest version.
libxinerama-dev is already the newest version.
libxv-dev is already the newest version.
x-dev is already the newest version.
libx11-dev is already the newest version.
libxv-dev is already the newest version.
libgtk1.2-dev is already the newest version.
subversion is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfaac-dev: Depends: libfaac0 (= 1.24clean-0ubuntu4) but 1.24+cvs20060416-0.3 is to be installed
  libfaad2-dev: Depends: libfaad2-0 (= 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) but 2.0.0+cvs20060416-0.0 is to be installed
E: Broken packages
```

From what I can tell, it appears that their is a problem with the different versions of the libraries installed. Is there a way to solve this?

---

### Post by janfsd on 2007-01-03
> **dpny said:**
> I am trying to compile the latest mplayer for PPC Ubuntu. However, I'm getting an error message I don't understand when trying to get the dependencies.:

The first is:

```
$ sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxv-dev is already the newest version.
libpng12-dev is already the newest version.
checkinstall is already the newest version.
E: Couldn't find package libavifile-0.7-dev
```

Removing libavifile-0.7-dev gives me the error:

```
. . .
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
libx11-dev is already the newest version.
libxv-dev is already the newest version.
libpng12-dev is already the newest version.
checkinstall is already the newest version.
libgtk2.0-dev is already the newest version.
liblame-dev is already the newest version.
libice-dev is already the newest version.
libxinerama-dev is already the newest version.
libxv-dev is already the newest version.
x-dev is already the newest version.
libx11-dev is already the newest version.
libxv-dev is already the newest version.
libgtk1.2-dev is already the newest version.
subversion is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfaac-dev: Depends: libfaac0 (= 1.24clean-0ubuntu4) but 1.24+cvs20060416-0.3 is to be installed
  libfaad2-dev: Depends: libfaad2-0 (= 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) but 2.0.0+cvs20060416-0.0 is to be installed
E: Broken packages
```

From what I can tell, it appears that their is a problem with the different versions of the libraries installed. Is there a way to solve this?

It seems that you have broken packages, probably you have some other apt sources than the official ones. Try to remove that sources and just use the official ones and try again.

---

### Post by fon~Zograf on 2007-01-10
I have a similar problem.
```

zograf@zograf-desktop:~$ sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion
Password:
Reading of lists of packages... It is ready
Construction of a tree of dependences
Reading of the information on a condition... It is ready
The newest version build-essential is already established.
The newest version debhelper is already established.
E: I can not find a package libfaac-dev
zograf@zograf-desktop:~$

```
My console Russian. On it I use the electronic translator promt.ru sorry...

sources.list
```
deb http://ru.archive.ubuntu.com/ubuntu/ edgy main restricted 
deb-src http://ru.archive.ubuntu.com/ubuntu/ edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ru.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 
deb-src http://ru.archive.ubuntu.com/ubuntu/ edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ru.archive.ubuntu.com/ubuntu/ edgy universe 
deb-src http://ru.archive.ubuntu.com/ubuntu/ edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ru.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 
deb-src http://ru.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb http://security.ubuntu.com/ubuntu edgy-security universe 
deb-src http://security.ubuntu.com/ubuntu edgy-security universe 

```

Operational system has established 3 hours back (kubuntu 6.10), has completely updated. From extraneous programs only driver ATI and browser Opera.

p/s
I am sorry for my English, I use the electronic translator.

---

### Post by janfsd on 2007-01-10
Just try to add to your sources universe and multiverse so it will look something like this 
```

deb http://pl.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://pl.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse


## Major bug fix updates produced after the final release of the
## distribution.
deb http://pl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

```

For the security line you could add it too, after that sudo apt-get update, and try again, now it shoud be able to find the missing package.

---

### Post by fon~Zograf on 2007-01-10
2janfsd
Has earned! Loads. The system has warned, what one package will leave, it is normal? (which I do not know)

---

### Post by janfsd on 2007-01-10
> **fon~Zograf said:**
> 2janfsd
Has earned! Loads. The system has warned, what one package will leave, it is normal? (which I do not know)

I didn't understand that, maybe could you post the warning that appears?

---

### Post by fon~Zograf on 2007-01-10
> **janfsd said:**
> I didn't understand that, maybe could you post the warning that appears?
Once again forgive for my English. Mplayer works!!!. Thanks for the help.
p/s
Has gone to learn English language. Now I know only Russian and Japanese  ^_~

---

### Post by janfsd on 2007-01-11
I am glad it worked for you/

---

### Post by tofudrifter on 2007-01-12
```
In file included from wm/ws.c:27:
../loader/../libswscale/swscale.h:30:20: error: avutil.h: No such file or directory
In file included from wm/ws.c:27:
../loader/../libswscale/swscale.h:114: error: syntax error before 'attribute_deprecated'
../loader/../libswscale/swscale.h:114: warning: data definition has no type or storage class
wm/ws.c: In function 'wsXInit':
wm/ws.c:300: warning: assignment from incompatible pointer type
wm/ws.c:304: warning: assignment from incompatible pointer type
wm/ws.c:308: warning: assignment from incompatible pointer type
wm/ws.c:312: warning: assignment from incompatible pointer type
wm/ws.c:316: warning: assignment from incompatible pointer type
wm/ws.c:320: warning: assignment from incompatible pointer type
wm/ws.c:324: warning: assignment from incompatible pointer type
wm/ws.c: In function 'wsCreateWindow':
wm/ws.c:473: warning: pointer targets in assignment differ in signedness
make[1]: *** [wm/ws.o] Error 1
make[1]: Leaving directory `/home/tofudrifter/mplayer/Gui'
make: *** [Gui/libgui.a] Error 2

```

I get this error when trying to compile on breezy. Have gotten same error several times now.

---

### Post by janfsd on 2007-01-12
Are you trying to compile the latest svn? If yes, did you do it from zero or you are updating it?

Edit: Tried to compile the latest svn and I got that error, so maybe it's the svn package that cannot compile, maybe the best will be to wait for an update, or use an older package.

EDIT2: Ok, now I know why it doesn't want to compile, because of the --enable-gui , just remove it and it will work, of course you won't have a gui for the moment, but maybe you can try copying the Gui folder of an older svn source and paste it on the latest. This probably will make it compile, but i don't know if mplayer (the gui) will work properly.

---

### Post by tofudrifter on 2007-01-13
Both your edit's have pretty much answered all my queries, but ye i updated using "svn update" I already got an older compile of mplayer running on my system so i guess i'll wait for an update before i attempt again.

---

### Post by janfsd on 2007-01-13
Just to let you know, the latest svn revision compiles without problem, so just svn update it, and don't forget to do a make clean before compiling.

---

### Post by tofudrifter on 2007-01-15
```
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `init':vd_theora.c:(.text+0xc2): undefined reference to `theora_info_init'
:vd_theora.c:(.text+0xd1): undefined reference to `theora_comment_init'
:vd_theora.c:(.text+0x108): undefined reference to `theora_decode_header'
:vd_theora.c:(.text+0x11f): undefined reference to `theora_decode_init'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `uninit':vd_theora.c:(.text+0x239): undefined reference to `theora_info_clear'
:vd_theora.c:(.text+0x244): undefined reference to `theora_comment_clear'
:vd_theora.c:(.text+0x24c): undefined reference to `theora_clear'
libmpcodecs/libmpcodecs.a(vd_theora.o): In function `decode':vd_theora.c:(.text+0x2ca): undefined reference to `theora_decode_packetin'
:vd_theora.c:(.text+0x2e2): undefined reference to `theora_decode_YUVout'
libmpdemux/libmpdemux.a(demux_ogg.o): In function `demux_ogg_open':demux_ogg.c:(.text+0x3047): undefined reference to `theora_info_init'
:demux_ogg.c:(.text+0x304f): undefined reference to `theora_comment_init'
:demux_ogg.c:(.text+0x3066): undefined reference to `theora_decode_header'
:demux_ogg.c:(.text+0x30a2): undefined reference to `theora_comment_clear'
:demux_ogg.c:(.text+0x30aa): undefined reference to `theora_info_clear'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

It compiles past the gui part now but i'm getting the problem with theora like the people a few posts back.  I know i can just remove the --enable-theora flag in ./configure but i'm curious to know why it works for some but not others...
Could it be because i got mplayer installed from the repositories at the moment?

---

### Post by janfsd on 2007-01-15
Well, that flag is not necessary at all, because it automatically tries to find if you have theora codecs, and if you have them, it enables it.
So, did you get that error without that flag?

---

### Post by tofudrifter on 2007-01-15
```
:ve_x264.c:(.text+0x22e): undefined reference to `x264_param_parse'
:ve_x264.c:(.text+0x24a): undefined reference to `x264_param_parse'
libmpcodecs/libmpencoders.a(ve_x264.o): In function `config':ve_x264.c:(.text+0x374): undefined reference to `x264_param_parse'
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1

```

i get this without the theora flag so fingers crossed for it to compile without mencoder

edit: i get same error oven without --enable-menu

---

### Post by janfsd on 2007-01-16
Are you using the --enable-x264 flag? If not, then try with --disable-x264

Do you type something like this?
```
configure --prefix=/usr --enable-gui --disable-arts --disable-smb --enable-sdl --enable-x11 --confdir=/etc/mplayer --win32codecsdir=/usr/lib/win32 --enable-menu --enable-tv-v4l2 --disable-liblzo --enable-largefiles  --disable-libdv --disable-aa
``` if not, then try just with this

---

### Post by tofudrifter on 2007-01-16
i wasn't using --enable-x264 but i found my problem, i had x264 installed from the repositories, once i removed them and installed x264 from svn again compile worked.

---

### Post by nix4me on 2007-01-21
Hi,

I compiled using svn yesterday and all is well except 1 thing.  Gmplayer does not play mpg files.  mplayer plays them fine.   When gmplayer opens an mpg, it tries to play but skips and hangs and throws up repeated errors.  Here is the output:

```
MPlayer dev-SVN-r21970-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Black.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial_Black.ttf
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/nix4me/Desktop/03_ZX-6_Streets.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  320x240  (aspect 1)  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Trying to force audio codec driver family ffmpeg...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp2 @ 0x894abd8]incorrect frame size
AUDIO: 32000 Hz, 1 ch, s16le, 32.0 kbit/6.25% (ratio: 4000->64000)
Selected audio codec: [ffmp2] afm: ffmpeg (FFmpeg MPEG layer-1 and layer-2 audio decoder)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar YV12 
[mp2 @ 0x894abd8]incorrect frame size000   1/  1 ??% ??% ??,?% 0 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size004   2/  2 ??% ??% ??,?% 1 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size008   3/  3 ??% ??% ??,?% 2 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size012   4/  4 ??% ??% ??,?% 3 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size016   5/  5 ??% ??% ??,?% 4 0                                                   
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size
[mp2 @ 0x894abd8]incorrect frame size

```

any ideas?

nix4me

---

### Post by maranellored on 2007-01-21
this is the error i get when i run the make command
```
libavformat/libavformat.a(allformats.o): In function `av_register_all':
allformats.c:(.text+0xc3): undefined reference to `audio_muxer'
allformats.c:(.text+0xcf): undefined reference to `audio_demuxer'
allformats.c:(.text+0x423): undefined reference to `nut_muxer'
allformats.c:(.text+0x55b): undefined reference to `redir_demuxer'
allformats.c:(.text+0x567): undefined reference to `rtp_muxer'
allformats.c:(.text+0x573): undefined reference to `rtsp_demuxer'
allformats.c:(.text+0x57f): undefined reference to `sdp_demuxer'
allformats.c:(.text+0x61b): undefined reference to `video_grab_device_demuxer'
libavformat/libavformat.a(dc1394.o): In function `dc1394_close':
dc1394.c:(.text+0x1d): undefined reference to `dc1394_stop_iso_transmission'
dc1394.c:(.text+0x2b): undefined reference to `dc1394_dma_unlisten'
dc1394.c:(.text+0x39): undefined reference to `dc1394_dma_release_camera'
dc1394.c:(.text+0x43): undefined reference to `dc1394_destroy_handle'
libavformat/libavformat.a(dc1394.o): In function `dc1394_read_packet':
dc1394.c:(.text+0x77): undefined reference to `dc1394_dma_done_with_buffer'
dc1394.c:(.text+0xa4): undefined reference to `dc1394_dma_single_capture'
libavformat/libavformat.a(dc1394.o): In function `dc1394_read_header':
dc1394.c:(.text+0x308): undefined reference to `dc1394_create_handle'
dc1394.c:(.text+0x330): undefined reference to `dc1394_get_camera_nodes'
dc1394.c:(.text+0x3ac): undefined reference to `dc1394_dma_setup_capture'
dc1394.c:(.text+0x3e9): undefined reference to `dc1394_destroy_handle'
dc1394.c:(.text+0x431): undefined reference to `dc1394_start_iso_transmission'
dc1394.c:(.text+0x46c): undefined reference to `dc1394_dma_unlisten'
dc1394.c:(.text+0x47e): undefined reference to `dc1394_dma_release_camera'
libavcodec/libavcodec.a(allcodecs.o): In function `avcodec_register_all':
allcodecs.c:(.text+0x281): undefined reference to `mpeg_xvmc_decoder'
allcodecs.c:(.text+0x5c9): undefined reference to `xvid_encoder'
allcodecs.c:(.text+0x605): undefined reference to `aac_decoder'
allcodecs.c:(.text+0x611): undefined reference to `mpeg4aac_decoder'
allcodecs.c:(.text+0x61d): undefined reference to `ac3_decoder'
allcodecs.c:(.text+0x641): undefined reference to `amr_nb_encoder'
allcodecs.c:(.text+0x64d): undefined reference to `amr_nb_decoder'
allcodecs.c:(.text+0x659): undefined reference to `amr_wb_encoder'
allcodecs.c:(.text+0x665): undefined reference to `amr_wb_decoder'
allcodecs.c:(.text+0x695): undefined reference to `faac_encoder'
allcodecs.c:(.text+0x6c5): undefined reference to `libgsm_encoder'
allcodecs.c:(.text+0x6d1): undefined reference to `libgsm_decoder'
allcodecs.c:(.text+0x725): undefined reference to `mp3lame_encoder'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```i'm using xubuntu Edgy.
please help !!

---

### Post by janfsd on 2007-01-22
> **maranellored said:**
> this is the error i get when i run the make command
```
libavformat/libavformat.a(allformats.o): In function `av_register_all':
allformats.c:(.text+0xc3): undefined reference to `audio_muxer'
allformats.c:(.text+0xcf): undefined reference to `audio_demuxer'
allformats.c:(.text+0x423): undefined reference to `nut_muxer'
allformats.c:(.text+0x55b): undefined reference to `redir_demuxer'
allformats.c:(.text+0x567): undefined reference to `rtp_muxer'
allformats.c:(.text+0x573): undefined reference to `rtsp_demuxer'
allformats.c:(.text+0x57f): undefined reference to `sdp_demuxer'
allformats.c:(.text+0x61b): undefined reference to `video_grab_device_demuxer'
libavformat/libavformat.a(dc1394.o): In function `dc1394_close':
dc1394.c:(.text+0x1d): undefined reference to `dc1394_stop_iso_transmission'
dc1394.c:(.text+0x2b): undefined reference to `dc1394_dma_unlisten'
dc1394.c:(.text+0x39): undefined reference to `dc1394_dma_release_camera'
dc1394.c:(.text+0x43): undefined reference to `dc1394_destroy_handle'
libavformat/libavformat.a(dc1394.o): In function `dc1394_read_packet':
dc1394.c:(.text+0x77): undefined reference to `dc1394_dma_done_with_buffer'
dc1394.c:(.text+0xa4): undefined reference to `dc1394_dma_single_capture'
libavformat/libavformat.a(dc1394.o): In function `dc1394_read_header':
dc1394.c:(.text+0x308): undefined reference to `dc1394_create_handle'
dc1394.c:(.text+0x330): undefined reference to `dc1394_get_camera_nodes'
dc1394.c:(.text+0x3ac): undefined reference to `dc1394_dma_setup_capture'
dc1394.c:(.text+0x3e9): undefined reference to `dc1394_destroy_handle'
dc1394.c:(.text+0x431): undefined reference to `dc1394_start_iso_transmission'
dc1394.c:(.text+0x46c): undefined reference to `dc1394_dma_unlisten'
dc1394.c:(.text+0x47e): undefined reference to `dc1394_dma_release_camera'
libavcodec/libavcodec.a(allcodecs.o): In function `avcodec_register_all':
allcodecs.c:(.text+0x281): undefined reference to `mpeg_xvmc_decoder'
allcodecs.c:(.text+0x5c9): undefined reference to `xvid_encoder'
allcodecs.c:(.text+0x605): undefined reference to `aac_decoder'
allcodecs.c:(.text+0x611): undefined reference to `mpeg4aac_decoder'
allcodecs.c:(.text+0x61d): undefined reference to `ac3_decoder'
allcodecs.c:(.text+0x641): undefined reference to `amr_nb_encoder'
allcodecs.c:(.text+0x64d): undefined reference to `amr_nb_decoder'
allcodecs.c:(.text+0x659): undefined reference to `amr_wb_encoder'
allcodecs.c:(.text+0x665): undefined reference to `amr_wb_decoder'
allcodecs.c:(.text+0x695): undefined reference to `faac_encoder'
allcodecs.c:(.text+0x6c5): undefined reference to `libgsm_encoder'
allcodecs.c:(.text+0x6d1): undefined reference to `libgsm_decoder'
allcodecs.c:(.text+0x725): undefined reference to `mp3lame_encoder'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```i'm using xubuntu Edgy.
please help !!

I think that is mplayer's fault, probably that svn source is broken, sometimes this happens, I get the same error with the latest svn... Hopefully it will soon be fixed, so just try to do it again tomorrow, after updating it.

---

### Post by xpan on 2007-02-22
Hi, I tried to untar MplayerAMRsupport.tar.gz to Mplayer/libavcodec/ but I can't find this directory anywhere on my hard disk.

I have Mplayer, Xine and VLC players installed.

I used edgy eft. Any ideas?

---

### Post by navy78 on 2007-03-28
Sorry for my dab english,
I followd your guide, but after download the last version of mplayer from svn, 
I launch:

"./configure"
 
and after:

"make" , and the output is:

```

......
......
......

libmpdemux/libmpdemux.a(demux_ogg.o): In function `demux_ogg_open':
demux_ogg.c:(.text+0x309b): undefined reference to `theora_info_init'
demux_ogg.c:(.text+0x30aa): undefined reference to `theora_comment_init'
demux_ogg.c:(.text+0x30c8): undefined reference to `theora_decode_header'
demux_ogg.c:(.text+0x3101): undefined reference to `theora_comment_clear'
demux_ogg.c:(.text+0x3110): undefined reference to `theora_info_clear'
demux_ogg.c:(.text+0x36fb): undefined reference to `theora_comment_clear'
demux_ogg.c:(.text+0x370a): undefined reference to `theora_info_clear'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


```



Please, Can you Help Me??????
Thanks in advance...

---

### Post by LucasLinard on 2007-04-02
remove the --enable-theora of something like it theora from the command you use to compile.

---

### Post by iwan13 on 2007-08-09
hello... there are too many pages to go trought ... i but i havent seen anyone with my problem on pages that iwent trought .... so if there is already a solution to my problem just a link is ok too 
after puting those lines on sources.list and updating (which went smoothly)
i do that loooong command and gget this :(

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

> The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
  gnome-core-devel: Depends: libart-2.0-dev but it is not going to be installed
                    Depends: liborbit2-dev (>= 1:2.12.4) but it is not going to be installed
                    Depends: libatspi-dev (>= 1.6.6) but it is not going to be installed
                    Depends: libatk1.0-dev (>= 1.10.3) but it is not going to be installed
                    Depends: libaudiofile-dev but it is not going to be installed
                    Depends: libeel2-dev (>= 2.12.2) but it is not going to be installed
                    Depends: libglib2.0-dev (>= 2.8.4) but it is not going to be installed
                    Depends: libgnomeprintui2.2-dev (>= 2.12.1) but it is not going to be installed
                    Depends: libgnomeprint2.2-dev (>= 2.12.1) but it is not going to be installed
                    Depends: libgnome-keyring-dev (>= 0.4.6) but it is not going to be installed
                    Depends: libgnome-menu-dev (>= 2.12.0) but it is not going to be installed
                    Depends: libnautilus-extension-dev (>= 2.12.2) but it is not going to be installed
                    Depends: libgail-dev (>= 1.8.8) but it is not going to be installed
                    Depends: gnome-common (>= 2.12.0) but it is not going to be installed
                    Depends: libidl-dev but it is not going to be installed
                    Depends: libgnome2-dev (>= 2.12.0.1) but it is not going to be installed
                    Depends: libgnomevfs2-dev (>= 2.12.2) but it is not going to be installed
                    Depends: libpanel-applet2-dev (>= 2.12.2) but it is not going to be installed
                    Depends: gtk-doc-tools but it is not going to be installed
                    Depends: libpango1.0-dev (>= 1.10.1) but it is not going to be installed
                    Depends: libglade2-dev (>= 1:2.5.1) but it is not going to be installed
                    Depends: libgnomeui-dev (>= 2.12.0) but it is not going to be installed
                    Depends: libxml2-dev (>= 2.6.19) but it is not going to be installed
                    Depends: libxslt1-dev (>= 1.1.15) but it is not going to be installed
                    Depends: librsvg2-dev (>= 2.9.5) but it is not going to be installed
                    Depends: libgtksourceview-dev (>= 1.4.2) but it is not going to be installed
  libaa1-dev: Depends: libslang2-dev but it is not going to be installed
              Depends: libncurses5-dev but it is not going to be installed
  libavcodec-dev: Depends: zlib1g-dev but it is not going to be installed
                  Depends: libdc1394-13-dev but it is not going to be installed
  libavifile-0.7-dev: Depends: libxft-dev but it is not going to be installed
  libcaca-dev: Depends: libncurses5-dev but it is not going to be installed
               Depends: libslang2-dev but it is not going to be installed
  libesd0-dev: Depends: libaudiofile-dev but it is not going to be installed
  libfaac-dev: Depends: libc6-dev but it is not going to be installed or
                        libc-dev
  libfaad2-dev: Depends: libc6-dev but it is not going to be installed or
                         libc-dev
  libgtk1.2-dev: Depends: libglib1.2-dev but it is not going to be installed
  libgtk2.0-dev: Depends: libglib2.0-dev (>= 2.8.5) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.9.0) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
  libjpeg62-dev: Depends: libc-dev
  libmikmod2-dev: Depends: libc6-dev but it is not going to be installed
  libmp4v2-dev: Depends: libc6-dev but it is not going to be installed or
                         libc-dev
  libogg-dev: Depends: libc6-dev but it is not going to be installed
  libpng12-dev: Depends: zlib1g-dev but it is not going to be installed
  libquicktime-dev: Depends: libc6-dev but it is not going to be installed
                    Depends: libdv-dev
                    Depends: libglib-dev
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
                 Depends: libasound2-dev but it is not going to be installed
                 Depends: libartsc0-dev but it is not going to be installed
  xlibs-dev: Depends: zlib1g-dev but it is not going to be installed
E: Broken packages

:( now im a miss i thought i would gett those things with apt-get update but it seemes i missed a spot .. i enabled mp3 on me ubuntu(6.06 dapper drake) and now i wanna do this how-to and i mess up... and being that this is a great community i want to be a part of .... i seem to fail at every try :( ...windows must have put a curse on me or sumthin' :'(

---

### Post by janfsd on 2007-08-25
Just checked your post, it seems that you have broken packages, have you been using 3rd party repositories? can you post your sources.list? (It's in /etc/apt/sources.list)

Try using the -f option with apt-get, sth like this: 
```
sudo apt-get -f install ...
```

---

### Post by zach12 on 2007-08-26
does mplayer play itunes tunes

---

### Post by reyiyo on 2008-10-14
> **Treviño said:**
> I don't know if anyone has written here, btw to enable the amr audio support (needed to play correctly 3gp videos made for/by mobile phones) you need to untar this file to your Mplayer-sources/libavcodec/ directory (recompile the amrwb_float and amr_float directories content, if needed)... Then run ./configure with your favourite settings and you'll see that the amr_wb and amr_nb are now enabled codecs!

After you've compiled try to play a .3gp/.amr file and it will work perfectly! 

The link is broken :'(

---

### Post by andrew.46 on 2008-10-15
Hi:

> **reyiyo said:**
> The link is broken :'(

More current details about adding amr support to mplayer can be found:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

  Andrew

---

