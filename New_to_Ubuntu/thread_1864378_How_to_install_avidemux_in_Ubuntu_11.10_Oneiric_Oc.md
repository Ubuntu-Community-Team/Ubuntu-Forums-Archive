---
title: "How to install avidemux in Ubuntu 11.10 Oneiric Ocelot?"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-10-18
Dear All,
After several hours of frustration, I am asking for your help.

(BACKGROUND: Avidemux is no longer in oneiric [http://ubuntuforums.org/showthread.php?t=1850942](http://ubuntuforums.org/showthread.php?t=1850942))

Avidemux was in my machine in Ubuntu 11.04. After I upgraded to 11.10, it was still there from previous install. However, recently, I had to go for a fresh installation after I added a hard disk to my machine and the directories were fully rearranged. 

Now, when I try to install avidemux,
[LIST]
[*]The .deb's (2.6 for natty) in [http://www.avidemux.org/nightly/](http://www.avidemux.org/nightly/) can be downloaded and installed. But many of the functionalities do not work. 
[*] deb's can also be compiled from .tar.gz source ([http://www.avidemux.org/nightly/source/](http://www.avidemux.org/nightly/source/)), can be installed, but again lacks many necessary functionalities.
[*]The 2.5 .deb's from [http://packages.ubuntu.com/natty/](http://packages.ubuntu.com/natty/) produces dependency problems. I tried to solve one by one which finally came to the point of libx264-106.
[*] [http://www.getdeb.net/updates/ubuntu/11.10/](http://www.getdeb.net/updates/ubuntu/11.10/) does not have anything in avidemux.
[/LIST]

I really need avidemux and will appreciate any help or suggestion.

---

### Post by mc4man on 2011-10-18
The 2.5.5 source needs a x264 patch to compile correctly - then is fine
(other then that the cmake install can only be removed manually if need be.

Currently there is a fix in place for builds in 12.04 & then 11.10 though I'd say possibly a week for 11.10

If you don't want to wait or want 2.5.5 then it's pretty straightforward to build thru cmake or the incluced bootStrap.sh
(though i'd definitely edit the bootStrap.sn to install in /usr/local

If 2.5.4 is ok & again you don't want to wait the source that's in place for 12.04 will build fine to deb's for 11.10, the x264 patch is included

Have done both ways here for i386 & amd64
Let me know if you want to build & which way

Bug report here - I attached the x264 patch in comment 3
[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096)

---

### Post by mmasroorali on 2011-10-18
> **mc4man said:**
> The 2.5.5 source needs a x264 patch to compile correctly - then is fine
(other then that the cmake install can only be removed manually if need be.

Currently there is a fix in place for builds in 12.04 & then 11.10 though I'd say possibly a week for 11.10

If you don't want to wait or want 2.5.5 then it's pretty straightforward to build thru cmake or the incluced bootStrap.sh
(though i'd definitely edit the bootStrap.sn to install in /usr/local

If 2.5.4 is ok & again you don't want to wait the source that's in place for 12.04 will build fine to deb's for 11.10, the x264 patch is included

Have done both ways here for i386 & amd64
Let me know if you want to build & which way

Bug report here - I attached the x264 patch in comment 3
[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096)


I can not wait for a week, I need avidemux immediately.

I would like to build 2.5.5 for i386 in 11.10. This seems to be the stable one.

Could you please let me know how I can do it.

Thanks.

---

### Post by mc4man on 2011-10-18
simple - 
1st. double ck. on your build -deps, run this
```
sudo apt-get install libgtk2.0-dev libmp3lame-dev \
libmad0-dev liba52-dev libvorbis-dev libmjpegtools-dev libxvidcore-dev \
libfreetype6-dev libxml2-dev libasound2-dev libsdl-dev libxv-dev \
libxmu-dev libfaac-dev  libfaad-dev libx264-dev cmake libqt4-dev \
libopencore-amrnb-dev imagemagick libsamplerate0-dev \
libdca-dev quilt libjack-jackd2-dev libopencore-amrwb-dev libpulse-dev \
yasm  xsltproc libvpx-dev libaften-dev libqt4-opengl-dev patch
```

Then start with a **Fresh** extracted 2.5.5 source, I got it here
[http://avidemux.sourceforge.net/download.html](http://avidemux.sourceforge.net/download.html)

Am attaching the patch below, right click save as

Extract your 2.5.5 source, extract the patch & drop it into the source folder - screen 1
then cd to the source and run this
```
patch -p1 < 03_x264-115.diff
```
you should see this
> ~/Downloads/avid2/avidemux_2.5.5$ patch -p1 < 03_x264-115.diff
patching file plugins/ADM_videoEncoder/ADM_vidEnc_x264/encoder.cpp
patching file plugins/ADM_videoEncoder/ADM_vidEnc_x264/x264Options.cpp
doug@doug-XPS-M1330:~/Downloads/avid2/avidemux_2.5.5$

After that open the source folder > bootStrap.sh
On line 9 add /local screen 2
then at the previous avidemux_2.5.5$ prompt
```
chmod u+x bootStrap.sh; ./bootStrap.sh
```
When the build completes run this
```
sudo ldconfig
```
That's it unless you want to use the .desktop in the source folder - let me know, it's a good idea otherwise you'll be starting avidemux up from the command line or alt+F2

---

### Post by alphacrucis2 on 2011-10-19
I tested out mc4man's instructions and it worked. At the end of the process, I find three executables in /usr/local/bin

Namely avidemux2_cli, avidemux2_gtk, avidemux2_qt.

I notice when I double click avidemux2_gtk to start it and then click keep in launcher it works. I guess it must have become associated with an existing .desktop file?


EDit. Although the launcher stays there it doesn't actually work. I suspect it is because the associated desktop file is pointing at the old 2.5.4 binary which doesn't exist on my machine any more

---

### Post by mc4man on 2011-10-19
Probably what you should so (I currently have the .debs I built installed to test so ..
Create one or 2 .desktops 


```
gedit ~/.local/share/applications/avidemux2_gtk.desktop
```

```
[Desktop Entry]
Name=Avidemux (GTK+)
GenericName=GTK+ Video Editor
Comment=Edit your Videos
Comment[de]=Videos bearbeiten
TryExec=avidemux2_gtk
Exec=avidemux2_gtk
Icon=
Terminal=false
Type=Application
Categories=GTK;AudioVideo
MimeType=video/mpeg;video/x-mpeg;video/x-avi;application/x-flash-video;application/x-shockwave-flash;video/flv
```
```

gedit ~/.local/share/applications/avidemux2_qt.desktop
```

```
[Desktop Entry]
Name=Avidemux (Qt)
GenericName=Qt Video Editor
Comment=Edit your Videos
Comment[de]=Videos bearbeiten
TryExec=avidemux2_qt4
Exec=avidemux2_qt4
Icon=
Terminal=false
Type=Application
Categories=Qt;AudioVideo
MimeType=video/mpeg;video/x-mpeg;video/x-avi;application/x-flash-video;application/x-shockwave-flash;video/flv
```
For the Icon= line do a **full path **to the location of avidemux_icon.png

Ex. 
Icon=/home/doug/Pictures/avidemux_icon.png

Then drag either or both to launcher **from **~/.local/share/applications

or you you wanted both available from 1 icon then create 1 & use a quicklist


```
[Desktop Entry]
Name=Avidemux (GTK+)
GenericName=GTK+ Video Editor
Comment=Edit your Videos
Comment[de]=Videos bearbeiten
TryExec=avidemux2_gtk
Exec=avidemux2_gtk
Icon=
Terminal=false
Type=Application
Categories=GTK;AudioVideo
MimeType=video/mpeg;video/x-mpeg;video/x-avi;application/x-flash-video;application/x-shockwave-flash;video/flv
X-Ayatana-Desktop-Shortcuts=AviDemuxqt;

[AviDemuxqt Shortcut Group]
Name=Avidemux (Qt)
Exec=avidemux2_qt4
TargetEnvironment=Unity
```

If you want the menu in avidemux instead of the global use these instead on the Exec= line
```
Exec=env UBUNTU_MENUPROXY=0 avidemux2_gtk
```
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 avidemux2_qt4
```

---

### Post by alphacrucis2 on 2011-10-19
Thanks. I already created some .desktops by copying an existing one and editing using gvim. However you have clarified some of this stuff for me. :guitar:

---

### Post by mmasroorali on 2011-10-19
Thanks, it worked, perfectly.

---

### Post by vivek25 on 2011-10-19
> **mc4man said:**
> The 2.5.5 source needs a x264 patch to compile correctly - then is fine
(other then that the cmake install can only be removed manually if need be.

Currently there is a fix in place for builds in 12.04 & then 11.10 though I'd say possibly a week for 11.10

If you don't want to wait or want 2.5.5 then it's pretty straightforward to build thru cmake or the incluced bootStrap.sh
(though i'd definitely edit the bootStrap.sn to install in /usr/local

If 2.5.4 is ok & again you don't want to wait the source that's in place for 12.04 will build fine to deb's for 11.10, the x264 patch is included

Have done both ways here for i386 & amd64
Let me know if you want to build & which way

Bug report here - I attached the x264 patch in comment 3
[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096)
hey pal i have a serious i have to install unbuntu for my Uni work and every time i try to install UBUNTU 11.10 ist shows following error
An error occured 
unsubsrciptable object
for more information please see the logfile
c:\users\vivekv~1\appdata\local\temp\wubi-11.10-rev245.log
please help i dont have much time

---

### Post by caish5 on 2011-10-19
While this compiles a working avidemux it seems to have issues with audio codecs and is therefore mostly unusable.

Any more ideas?

---

### Post by mc4man on 2011-10-19
> **caish5 said:**
> While this compiles a working avidemux it seems to have issues with audio codecs and is therefore mostly unusable.

Any more ideas?
You could wait for ubuntu packages, check here 

[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/831096)

or a ppa now for 2.5.4
[https://launchpad.net/~n-muench/+archive/programs-ppa](https://launchpad.net/~n-muench/+archive/programs-ppa)

---

### Post by alexthunder on 2011-10-25
@mc4man
Thanks a lot! Works like a charm!

---

### Post by jcw.atticus on 2012-01-23
> **mc4man said:**
> 

Extract your 2.5.5 source, extract the patch & drop it into the source folder - screen 1
then cd to the source and run this
```
patch -p1 < 03_x264-115.diff
```



Could you clarify this step for me? I've extracted both and put the patch into the source folder, but I don't know what you mean by "cd to the source." What do I do with the code?

Sorry if this is an obvious question, but I have very limited knowledge in these matters. Thanks for you help!

---

