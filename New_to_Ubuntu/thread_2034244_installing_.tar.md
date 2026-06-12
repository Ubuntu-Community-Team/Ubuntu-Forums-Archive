---
title: "installing .tar"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-07-28
I have to install a previous version of VLC, as it won't work with certain streams I watch. Anyway - I downloaded v.1.1.9 that is in .tar.bz2 - I know I have to extract it and install it - but am not too sure how to do so. Would someone be as kind as to explain the process I need to do so. (from terminal of course)

Thank you!

---

### Post by raja.genupula on 2012-07-28
open your terminal and follow these instructions 

```
tar -xvf /path/to/vlc.tar
```

then cd to vlc folder 
then
```
./configure
make
sudo make install
```

if any errors paste here

---

### Post by kabukiM0n0 on 2012-07-28
I get this in response to the first code 

```
tar: /home/km/Downloads: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

```

---

### Post by raja.genupula on 2012-07-28
> **kabukiM0n0 said:**
> I get this in response to the first code 

```
tar: /home/km/Downloads: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

```

could you give me the details of the code what you have entered and what you got and filename also exactly . 

thank you .

---

### Post by kabukiM0n0 on 2012-07-28
No problem.

The extracted file-name is vlc-1.1.9 and the unextracted one is vlc-1.1.9.tar.bz2

---

### Post by kc1di on 2012-07-28
> **kabukiM0n0 said:**
> I get this in response to the first code 

```
tar: /home/km/Downloads: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

```

you need to cd to the directory first 
```
cd /home/km/Downloads
```
then run the commands given.

or you can just navigate to the Download folder in your file manager and right click and select open with archive manager.  
then you can extract the file through the manager. 
after it's extracted you cd to the new directory that is created.
Then run the ```
./configure
make
make install
``` commands
cheers!

---

### Post by kabukiM0n0 on 2012-07-28
I followed you're instructions 
```
cd /home/km/Downloads/vlc-1.1.9
./configure
```

and get this error: 

configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?

---

### Post by raja.genupula on 2012-07-28
hi

open your terminal and type as 
```
sudo aptitude install libdbus-dev
```
then try again .

have you installed build-essential ? If not install it also .

---

### Post by Zill on 2012-07-28
> **kabukiM0n0 said:**
> I have to install a previous version of VLC, as it won't work with certain streams I watch. Anyway - I downloaded v.1.1.9 that is in .tar.bz2 - I know I have to extract it and install it - but am not too sure how to do so. Would someone be as kind as to explain the process I need to do so. (from terminal of course)
Why not just download the deb, install it with gdebi and then lock the version so that it does not update?

[Package: vlc (1.1.9-1ubuntu1.3) [universe]]("http://packages.ubuntu.com/natty-updates/vlc")

Far easier than compiling from source IMHO. ;-)

---

### Post by mc4man on 2012-07-28
> **Zill said:**
> Why not just download the deb, install it with gdebi and then lock the version so that it does not update?

[Package: vlc (1.1.9-1ubuntu1.3) [universe]]("http://packages.ubuntu.com/natty-updates/vlc")

Far easier than compiling from source IMHO. ;-)

Not quite that simple - vlc is a min of 5 packages that need to be installed together.
Add. the 11.04 packages will likely  not work in 12.04

OP - the odds of getting a build of the 1.1.9 source on 12.04 are not good due to changes in libraries that vlc is building against.
You'd be better off trying to resolve your un-described playback issue, possibly going to a newer vlc source rather than older

---

### Post by kabukiM0n0 on 2012-07-29
> **mc4man said:**
> Not quite that simple - vlc is a min of 5 packages that need to be installed together.
Add. the 11.04 packages will likely  not work in 12.04

OP - the odds of getting a build of the 1.1.9 source on 12.04 are not good due to changes in libraries that vlc is building against.
You'd be better off trying to resolve your un-described playback issue, possibly going to a newer vlc source rather than older

The problem is that is only streams for linux on version 1.1.9 or 1.1.6 - So there's my dillema.

---

### Post by Zill on 2012-07-29
> **kabukiM0n0 said:**
> The problem is that is only streams for linux on version 1.1.9 or 1.1.6 - So there's my dillema.
Would you please provide a link to a publicly-available stream that you believe only works on these versions.  This will allow other users to check your findings.

---

### Post by kabukiM0n0 on 2012-07-29
> **Zill said:**
> Why not just download the deb, install it with gdebi and then lock the version so that it does not update?

[Package: vlc (1.1.9-1ubuntu1.3) [universe]]("http://packages.ubuntu.com/natty-updates/vlc")

Far easier than compiling from source IMHO. ;-)
Because I don't know how to do that either :/



> **Zill said:**
> Would you please provide a link to a publicly-available stream that you believe only works on these versions.  This will allow other users to check your findings.


It's not a publicly available stream ... It's a closed website. [http://aznv.tv]("http://aznv.tv")
But I'll quote you. 
> 2. Linux: VLC player is native to this operating system. There are much less problems with VLC on Linux than there are on Windows. VLC does not support seek due to the way VLC has implemented the HTTP content-range header. Linux also has several other programs with capabilities in streaming, however, they require the user to find special codecs to make the stream work.  
There is also a little bit on winamp through WINE but seeing that doesn't run on my system .. I took it out as it was irrelevant. 

SMPlayer doesn't work - nothing happens. MPlayer says it doesn't recognize the input.

I made a mistake though . it was version 1.1.5 not 1.1.6

---

### Post by Zill on 2012-07-29
> **kabukiM0n0 said:**
> Because I don't know how to do that either :/
[LIST=1]
[*]Uninstall any existing versions of VLC
[*]Open the link I gave you and click on the appropriate "Download vlc" link at the bottom
[*]Click on the resulting downloaded file to open gdebi
[*]Install the vlc package with gdebi (*unless* you receive warnings about missing dependencies!)
[*]Open Synaptic and lock the version to prevent further updates
[/LIST]
Note that there *may* be dependency problems as highlighted by mc4man.  In which case do *not* proceed or you will end up in "dependency hell". :-(
> **kabukiM0n0 said:**
> It's not a publicly available stream ... It's a closed website. [http://aznv.tv]("http://aznv.tv")
But I'll quote you...
The quotation you provided says nothing about why a particular version of VLC is required!
Why do you think one version works and a later one doesn't?

---

### Post by kabukiM0n0 on 2012-07-29
Do I download from the link on the right? that says 'download source package' ?
> **Zill said:**
> 
The quotation you provided says nothing about why a particular version of VLC is required!
Why do you think one version works and a later one doesn't?

It's in the forums, I just couldn't find it - but from what I remember (apart from the fact v.2.0 didn't work) was that it had something done to it, which disabled what this particular stream needed. Let me find the discussion..

---

### Post by Zill on 2012-07-29
> **kabukiM0n0 said:**
> Do I download from the link on the right? that says 'download source package' ?
No.

At the bottom left of the screen you will see "Download vlc".  Click on "amd64" if you have a 64-bit system or "i386" if you have a 32-bit system.

See attached screenshot...

---

### Post by mc4man on 2012-07-29
You best bet if this is important will be to build the vlc-1.9 source, though it isn't exactily straightfoward.

In addtion to the vlc source you'll need to locally build an older ffmpeg & x264 sources just for the vlc build.
(the natty sources for them will work fine

Also a couple of options would likely need to be disabled though they're not that important or useful.

If you seriously want to pursue then let me know - not as difficult as it may appear

screen shows vlc-1.9 playing your site, this was done on 12.10
(- the issue is not the vcodec - VP6 or the container - .nsv, it's just streaming them in a player which current vlc & most other players can't do.

As an aside or low rent alternative -  ffplay or avplay will play those stream url's just fine, just no 'real' players will

---

### Post by kabukiM0n0 on 2012-07-30
> **mc4man said:**
> You best bet if this is important will be to build the vlc-1.9 source, though it isn't exactily straightfoward.

In addtion to the vlc source you'll need to locally build an older ffmpeg & x264 sources just for the vlc build.
(the natty sources for them will work fine

Also a couple of options would likely need to be disabled though they're not that important or useful.

If you seriously want to pursue then let me know - not as difficult as it may appear

screen shows vlc-1.9 playing your site, this was done on 12.10
(- the issue is not the vcodec - VP6 or the container - .nsv, it's just streaming them in a player which current vlc & most other players can't do.

As an aside or low rent alternative -  ffplay or avplay will play those stream url's just fine, just no 'real' players will

I seriously want to pursue this, yes.

---

### Post by mc4man on 2012-07-30
Ok - will do this in 2 parts
We're going to use the method as worked out by andrew.46 for the current git vlc as seen here with a few changes
[https://help.ubuntu.com/community/CompileVLC](https://help.ubuntu.com/community/CompileVLC)

So first to prepare your install & get the build deps

I'd advise updating & getting your install up to date - 
```
sudo apt-get update
```
Then if desired open update-manager, get updated & if need be restart

All commands in a code box are meant to be run as 1 command, copy & paste completely in to a terminal, press enter

Make sure _each command completes fully without error_ before moving on, if any issue copy the error from terminal & post in a quote box

Remove vlc & some packages if installed, if they aren't installed you'll be told so.

```
sudo apt-get purge vlc-data libvpx-dev libavcodec-dev libavformat-dev

```

Get the build-deps, we'll do in 3 seperate commands
```
sudo apt-get -y install build-essential git-core checkinstall automake yasm

```
When done, make sure you get the whole command here
```
sudo apt-get -y install liba52-0.7.4-dev libaa1-dev libasound2-dev libass-dev \
libavahi-client-dev libcaca-dev libcairo2-dev libcddb2-dev libcdio-dev libdca-dev \
libdirac-dev libdvbpsi-dev libdvdnav-dev libdvdread-dev libebml-dev libfaad-dev \
libflac-dev libfluidsynth-dev libfreetype6-dev libfribidi-dev libgcrypt11-dev \
libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnomevfs2-dev libgnutls-dev libhal-dev \
libid3tag0-dev libjack-jackd2-dev libkate-dev liblircclient-dev liblua5.1-0-dev \
libmad0-dev libmatroska-dev libmodplug-dev libmpcdec-dev libmpeg2-4-dev libmtp-dev \
libncursesw5-dev libnotify-dev libogg-dev liboggkate-dev libpango1.0-dev libpng12-dev \
libproxy-dev libpulse-dev libqt4-dev libraw1394-dev \
librsvg2-dev libschroedinger-dev  libshout3-dev \
libsmbclient-dev libspeex-dev libsqlite3-dev libsvga1-dev libsysfs-dev libtag1-dev \
libtar-dev libgme-dev libtheora-dev libtool libtwolame-dev libudev-dev libupnp3-dev \
libv4l-dev libva-dev libvcdinfo-dev libvorbis-dev libvpx-dev libx11-dev libx11-xcb-dev \
libxcb-composite0-dev libxcb-keysyms1-dev libxcb-randr0-dev libxcb-shm0-dev \
libxcb-xv0-dev libxcb-xvmc0-dev libxcb1-dev libxext-dev libxml2-dev libxpm-dev \
libxt-dev libxv-dev libzvbi-dev lua5.1 qt4-qtconfig libspeexdsp-dev 
```

Finally - 
```
sudo apt-get -y install libfaac-dev libmp3lame-dev \
libopencore-amrnb-dev libopencore-amrwb-dev zlib1g-dev 
```

I'd also advise removing the previous vlc config files - to do so open home folder & look for .config folder. If you don't see any hidden files/folders, (they all start with . ), then  go ctrl+h on keyboard
Open .config inside will be a vlc folder, delete it.

Once all this is done see next post to do the builds

---

### Post by mc4man on 2012-07-30
As before all code boxes are _1 single command_, **copy & paste carefully & completely in to a terminal, then press enter**.
**Do not proceed to the next command if the previous one errors**. If any issue copy about 15 lines or so from bottom of terminal output & post in a quote box.

So open a terminal, you may wish to make it a bit wider, if so grab the bottom right corner & slightly resize

Getting the 3 sources, we'll require vlc source so I know it's the same as used here.
Note that after 5 days I can't edit this post, the source urls should be good for some time.

```
mkdir -pv $HOME/vlc_build1 && cd $HOME/vlc_build1
```
(get the whole command here & all code boxes to follow - 
```
wget https://launchpad.net/ubuntu/+archive/primary/+files/ffmpeg_0.6.1.orig.tar.gz && \
wget https://launchpad.net/ubuntu/+archive/primary/+files/x264_0.106.1741.orig.tar.gz && \
wget https://launchpad.net/ubuntu/+archive/primary/+files/vlc_1.1.9.orig.tar.bz2
```

Unpacking & we'll rename 2 just because it's easier for me typing wise
```
tar xzvf  ./ffmpeg_0.6.1.orig.tar.gz &&  mv ./ffmpeg-0.6.1 ./ffmpeg && \
tar xzvf  ./x264_0.106.1741.orig.tar.gz && mv ./x264-0.106.1741 ./x264 && \
tar xvjf ./vlc_1.1.9.orig.tar.bz2
```

At this point your vlc_build1 folder in your home should look like shown in screen 1

If all went well then build ffmpeg - Just to note - by default the cursor in your terminal will stop blinking after 10 sec's of no output, if that happens don't do anything, all is ok, just let the build & install finish..
```
cd  $HOME/vlc_build1/ffmpeg && \
if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
  ARCHOPTS=""
fi && \
./configure --prefix=$HOME/vlc_build1/vlcdeps/usr \
              $ARCHOPTS \
              --enable-gpl \
              --enable-version3 \
              --enable-nonfree \
              --enable-postproc \
              --enable-pthreads \
              --enable-libfaac \
              --enable-libmp3lame \
              --enable-libopencore-amrnb \
              --enable-libopencore-amrwb \
              --disable-ffmpeg \
              --disable-ffplay \
              --disable-ffserver \
              --disable-doc && \
make && make install-libs install-headers && make distclean
```

When that completes correctly then build x264

```

if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
  ARCHOPTS=""
fi && \
cd $HOME/vlc_build1/x264 && \
./configure --prefix=$HOME/vlc_build1/vlcdeps/usr  $ARCHOPTS && \
make && make install && make distclean
```

Finally vlc - 
```
cd $HOME/vlc_build1/vlc-1.1.9 && \
if [ ! "$(uname -m)" = "x86_64" ]; then
 ARCHOPTS="--enable-loader"
else
  ARCHOPTS=""
fi && \
CPPFLAGS="-I$HOME/vlc_build1/vlcdeps/usr/include " \
CFLAGS="-I$HOME/vlc_build1/vlcdeps/usr/include"  \
CXXFLAGS="-I$HOME/vlc_build1/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build1/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build1/vlcdeps/usr/lib/pkgconfig" \
./configure \
            --prefix=/usr/local \
            --enable-realrtsp \
            --enable-aa \
            --enable-vcdx \
            --enable-ncurses \
            --enable-merge-ffmpeg \
            --disable-v4l2 \
            --disable-live555 \
            --disable-skins2 && \
make && \
sudo checkinstall --pakdir "$HOME/vlc_build1" --backup=no --deldoc=yes --fstrans=no \
--deldesc=yes --delspec=yes --default && \
sudo ldconfig && make distclean
```

Vlc will take some time to build & then install - you will need to enter your password after the build completes so checkinstall can do it's thing.

After install a log out in may be needed so vlc will show in the Dash if using unity.

You may notice the the bottom half of the window deco is black instead of graduated, such is..

If you happen to run vlc from a terminal you may see a qt4 error line, that's expected with this source & doesn't matter - 
[http://forum.videolan.org/viewtopic.php?f=13&t=93486](http://forum.videolan.org/viewtopic.php?f=13&t=93486)

Myself return the menu items to vlc window where that won't occur, that's something for later if desired

---

### Post by kabukiM0n0 on 2012-07-30
Thank you very much! Like really .. thank you ever so much!! :popcorn:

---

### Post by mc4man on 2012-07-30
Hopefully works out - forgot to mention

Make sure that you don't inadvertently upgrade vlc back to the repo version as the repo vlc will be seen as an upgrade.
, 
If it happens then remove vlc completely, 
(sudo apt-get purge vlc vlc-data 

You'll notice in your build folder the vlc_1.1.9  .deb, just re-install, no need to rebuild, ect. 
Keep in mind that if re-installing the deb you need to run this after install
sudo ldconfig

---

### Post by kabukiM0n0 on 2012-07-31
> **mc4man said:**
> Hopefully works out - forgot to mention

Make sure that you don't inadvertently upgrade vlc back to the repo version as the repo vlc will be seen as an upgrade.
, 
If it happens then remove vlc completely, 
(sudo apt-get purge vlc vlc-data 

You'll notice in your build folder the vlc_1.1.9  .deb, just re-install, no need to rebuild, ect. 
Keep in mind that if re-installing the deb you need to run this after install
sudo ldconfig

I think it accidentally updated, it's back to not being able to stream. 
how would i re-install?  (after I purged it of course)
sudo apt-get install vlc_1.1.9 followed by the sudo idconfig?

---

### Post by mc4man on 2012-07-31
> **kabukiM0n0 said:**
> I think it accidentally updated, it's back to not being able to stream. 
how would i re-install?  (after I purged it of course)
sudo apt-get install vlc_1.1.9 followed by the sudo idconfig?

No, apt-get will not work - 
2 ways
If gdebi is installed & you've purged the repo vlc packages then use that as in 
right click on the .deb > open with "Gdebi Package Installer"
After it install do the ldconfig command

Or assuming you haven't moved the .deb we created do this in a terminal
(again make sure all repo vlc packages have been purged..
```
sudo dpkg -i ~/vlc_build1/vlc*.deb && sudo ldconfig
```


(i'd give you exact command but don't know if you are 32 or 64 bit

After installing you can lock vlc in synaptic but that won't prevent update-manager or a sudo apt-get upgrade command from upgrading, ask about apt pinning or we could re-run the build with a new checkinstall command & re-version your package higher than 12.04 will ever see..

(myself only use synaptic for updating..

---

### Post by kabukiM0n0 on 2012-07-31
There's no need, With them two commands, if it does upgrade - i'll just purge it and re-install. 
again, thanks man!

---

