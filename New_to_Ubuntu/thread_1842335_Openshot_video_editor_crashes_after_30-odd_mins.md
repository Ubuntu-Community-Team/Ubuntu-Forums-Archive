---
title: "Openshot video editor crashes after 30-odd mins"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by CaronMargarete on 2011-09-11
Any idea why openshot crashes on some but not all pc/ laptops? I've read through some forums and can't seem to find a consistent reason.

I get anywhere from 30-60mins of use before it crashes and I have to restart my acer aspire 4535 to get it working again. 

Is there a crash report I can run in the terminal? Steps to check processes? 

Note: Please keep replies in basic layman terms/ instructions as I'm not familiar with a lot of linux-lingo.
Ta.
Caron.

---

### Post by hakermania on 2011-09-11
Hello Caron, can you please run the program in a terminal? You can open the terminal through Ctrl+Alt+T
After opening the terminal type in
```

openshot

```and press enter
Use the program normally and when it crash notice any error message outputed (printed) in the terminal.
Post back for the results.

Also, please remember what you were doing in the program while the crash happened.

---

### Post by CaronMargarete on 2011-09-13
Hi Hakerman, thanks for your help.

```
caronmargarete@caronmargarete-laptop:~$ openshot
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
A new frmMain has been created
state saved
Not the primary instance of OpenShot. Not starting queue watcher thread.
on_mnuOpenProject_activate called with self.mnuOpenProject
A new frmOpenProject has been created
st:1 removing common factor 384 from timebase
project modified:  Opened project
state saved
on_tlbPlay_clicked called with self.tlbPlay
    Last message repeated 275 times
[mp3 @ 0x7fd8e016f550]mdb:94, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 92 times
[mp3 @ 0x15cc1100]mdb:15, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 92 times
[mp3 @ 0x29d4000]mdb:46, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x29d4000]mdb:88, lastbuf:2 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 95 times
[mp3 @ 0x7fd8c93cc200]mdb:88, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x7fd8c93cc200]mdb:88, lastbuf:41 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 98 times
[mp3 @ 0x7fd8c93bba00]mdb:3, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 98 times
[mp3 @ 0x7fd8c80141f0]mdb:38, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x7fd8c80141f0]mdb:23, lastbuf:3 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
project saved! - Dauda Sanni Football Portfolio 2011 video
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 101 times
[mp3 @ 0x7fd8c80df550]mdb:23, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x7fd8c80df550]mdb:26, lastbuf:5 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Changed visibility of clip
state saved
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 104 times
[mp3 @ 0x7fd8c812aa40]mdb:35, lastbuf:0 skipping granule 0
[mp3 @ 0x7fd8c812aa40]mdb:26, lastbuf:10 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
project modified:  Changed visibility of clip
state saved
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 104 times
[mp3 @ 0x2d07990]mdb:26, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
project modified:  Moved clip
state saved
st:1 removing common factor 384 from timebase
on_tlbPlay_clicked called with self.tlbPlay
    Last message repeated 104 times
[mp3 @ 0x188bbdb0]mdb:20, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Changed visibility of clip
state saved
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
project modified:  Changed visibility of clip
state saved
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 104 times
[mp3 @ 0x7fd8c94801f0]mdb:46, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 107 times
[mp3 @ 0x7fd8c94c2d40]mdb:46, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
project saved! - Dauda Sanni Football Portfolio 2011 video
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 107 times
[mp3 @ 0x7fd8e03ace40]mdb:9, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_tlbResize_toggled called with self.tlbResize
on_tlbRazor_clicked called with self.tlbRazor
on_tlbResize_toggled called with self.tlbResize
on_tlbArrow_clicked called with self.tlbArrow
on_tlbResize_toggled called with self.tlbResize
on_tlbArrow_clicked called with self.tlbArrow
on_tlbRazor_clicked called with self.tlbRazor
on_tlbResize_toggled called with self.tlbResize
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x7fd8e03ace40]mdb:45, lastbuf:7 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbSnap_toggled called with self.tlbSnap
on_tlbSnap_toggled called with self.tlbSnap
on_mnuSaveProject_activate called with self.mnuSaveProject
project saved! - Dauda Sanni Football Portfolio 2011 video
on_frmMain_destroy
caronmargarete@caronmargarete-laptop:~$ openshot
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
A new frmMain has been created
state saved
Not the primary instance of OpenShot. Not starting queue watcher thread.
on_mnuOpenProject_activate called with self.mnuOpenProject
A new frmOpenProject has been created
st:1 removing common factor 384 from timebase
project modified:  Opened project
state saved
project modified:  Moved clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Changed audio of clip
state saved
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
    Last message repeated 530 times
[mp3 @ 0x7f41443bf880]mdb:72, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Changed visibility of clip
state saved
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
project modified:  Changed visibility of clip
state saved
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 107 times
[mp3 @ 0x7f4138145710]mdb:45, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x7f4138145710]mdb:26, lastbuf:19 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 110 times
[mp3 @ 0x1543e070]mdb:38, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Changed audio of clip
state saved
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 110 times
[mp3 @ 0x7f4138148740]mdb:36, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 113 times
[mp3 @ 0x7f4138278ef0]mdb:30, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 113 times
[mp3 @ 0x337d2f0]mdb:29, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x337d2f0]overread, skip -7 enddists: -6 -6
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 116 times
[mp3 @ 0x7f41394893b0]mdb:17, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Changed audio of clip
state saved
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_frmMain_key_press_event
on_frmMain_key_press_event
st:1 removing common factor 384 from timebase
on_tlbPlay_clicked called with self.tlbPlay
    Last message repeated 116 times
[mp3 @ 0x7f41380bca20]mdb:8, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Changed audio of clip
state saved
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 116 times
[mp3 @ 0x7f4138277c70]mdb:8, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 119 times
[mp3 @ 0x7f41388436f0]mdb:13, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
project modified:  Sliced clip
state saved
on_tlbRazor_clicked called with self.tlbRazor
on_tlbArrow_clicked called with self.tlbArrow
on_mnuRemoveClip_activate clicked
project modified:  Removed clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
st:1 removing common factor 384 from timebase
    Last message repeated 119 times
[mp3 @ 0x7f413809bc40]mdb:27, lastbuf:0 skipping granule 0
on_tlbPlay_clicked called with self.tlbPlay
on_tlbPlay_clicked called with self.tlbPlay
[mp3 @ 0x7f413809bc40]mdb:27, lastbuf:5 skipping granule 0
The program 'openshot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 175 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault
caronmargarete@caronmargarete-laptop:~$ openshot
--------------------------------
   OpenShot (version 1.1.3)
--------------------------------
A new frmMain has been created
state saved
Not the primary instance of OpenShot. Not starting queue watcher thread.
on_mnuOpenProject_activate called with self.mnuOpenProject
A new frmOpenProject has been created
st:1 removing common factor 384 from timebase
project modified:  Opened project
state saved
project modified:  Moved clip
state saved
on_tlbPlay_clicked called with self.tlbPlay
    Last message repeated 422 times
[mp3 @ 0x7f00d81c28d0]mdb:9, lastbuf:0 skipping granule 0
The program 'openshot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 47 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault
caronmargarete@caronmargarete-laptop:~$ 

```I opened Openshot through the terminal and then opened the file I'm working on. It worked for about half an hour when it stopped cutting (razor tool), which is the first time this has happened.

I closed and opened it again. As I was trying to save the file (out of frequent habit to ensure I saved some of my work) it crashed. I opened it again to commence work and crashed again, which it will now do continuously until I restart my laptop.

Thoughts?

---

### Post by hakermania on 2011-09-16
Sorry for the late response but loads of homework prevents me from being here.

Well, as the output indicates the problem is a bug of the program, every Segmentation Fault must be handled and output what caused the error and by no means to crash the application. You can fill a bug here for it: [https://bugs.launchpad.net/openshot](https://bugs.launchpad.net/openshot)
Be sure that the bug is not already reported and that you specify how to reproduce the bug plus Openshot's Version, your Ubuntu version and system information generally.

---

### Post by CaronMargarete on 2011-09-18
> **hakermania said:**
> Sorry for the late response but loads of homework prevents me from being here.

Well, as the output indicates the problem is a bug of the program, every Segmentation Fault must be handled and output what caused the error and by no means to crash the application. You can fill a bug here for it: [https://bugs.launchpad.net/openshot](https://bugs.launchpad.net/openshot)
Be sure that the bug is not already reported and that you specify how to reproduce the bug plus Openshot's Version, your Ubuntu version and system information generally.

Bug reported: [https://bugs.launchpad.net/openshot/+bug/853601](https://bugs.launchpad.net/openshot/+bug/853601)

---

### Post by hakermania on 2011-09-19
> **CaronMargarete said:**
> Bug reported: [https://bugs.launchpad.net/openshot/+bug/853601](https://bugs.launchpad.net/openshot/+bug/853601)

Good to know :)

---

### Post by Eolinwen on 2011-09-20
Hi,

You are using an old version of Openshot. We are at the Dawn to realize our last version (i.e. 1.4.0). And I don' t remember when it has been implanted (in the 1.2.2 or in the 1.3.0) but there is a automatic save mode implanted. :rolleyes:

Anyway, you must update your version of Openshot and our video  framework : MLT.
Here the steps to do for reach this purpose.
 
Let's began. You must have :


                       * the ffmpeg Medibuntu 's version;

I re-call about the installation of the repository of Medibuntu is necessarie for having the utiilsation of formats H264 and 3gp (no disponible with the official package for legal licences) .You must open with text editor (gedit for Gnome, kate for KDE, LXeditor for LXDE,....) your sources lists and et add the folowing lines and save :

```
##Depot Medibuntu
deb http://packages.medibuntu.org/ lucid free non-free 
```                      * you must after import the key, so you must open an terminal :

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```                     * You close all and you update your sources lists either in console either using your package manager (i.e. synaptic)

```
sudo update && sudo install ffmpeg
``` Don't worry, it will remove someones and re-install some others, That's normal and trust in your package manager. :confused:

                    * You check that you have all the dependencies needed, only one can not run Openshot. If it missed you one, install the missing.
Voici la liste :
[*]x264
    ffmpeg (libavformat52 or/ou libavformat-extra-52 or/ou libavformat-unstripped-52)
    python (+2.5 at least)
    python-xdg
    python-gtk2
    python-mlt2
    python-pygoocanvas
    python-imaging
    libgoocanvas3
    libgoocanvas-common    
    sox
    frei0r-plugins
    libsdl1.2debian or/ou libsdl1.2-pulseaudio
    librsvg2-common
    python-httplib2
    fontconfig
[/*] 

NB : I removed voluntary all about MLT because it is the subject of my last point. 

                               * A recent version of MLT i.e.the 0.7.4 that you could find with the following commands :

```
sudo add-apt-repository ppa:sunab/sunab2
```Recharge ta liste et met à jour MLT comme sur la screenshot suivante 
[[IMG]http://pix.toile-libre.org/upload/img/1316373570.png[/IMG]]("http://pix.toile-libre.org/?img=1316373570.png")

                              

```
sudo add-apt-repository ppa:openshot.developers/daily
```Run Openshot and normally all should works. :lolflag:
[The original answer in the French Ubuntu Forum]("http://forum.ubuntu-fr.org/viewtopic.php?pid=6225391#p6225391")
[The dependency list on the OpenshotUsers Forum]("http://openshotusers.com/forum/viewtopic.php?f=12&t=758")

NB: sorry for my bad English

---

### Post by CaronMargarete on 2011-09-20
> **Eolinwen said:**
> Hi,

You are using an old version of Openshot. We are at the Dawn to realize our last version (i.e. 1.4.0). And I don' t remember when it has been implanted (in the 1.2.2 or in the 1.3.0) but there is a automatic save mode implanted. :rolleyes:

Anyway, you must update your version of Openshot and our video  framework : MLT.
Here the steps to do for reach this purpose.
 
Let's began. You must have :


                       * the ffmpeg Medibuntu 's version;

I re-call about the installation of the repository of Medibuntu is necessarie for having the utiilsation of formats H264 and 3gp (no disponible with the official package for legal licences) .You must open with text editor (gedit for Gnome, kate for KDE, LXeditor for LXDE,....) your sources lists and et add the folowing lines and save :

```
##Depot Medibuntu
deb http://packages.medibuntu.org/ lucid free non-free 
```

Hi Eolinwen,

Thanks for replying. I've attempted the first part and got this result:

```
caronmargarete@caronmargarete-laptop:~$ ##Depot Medibuntu
caronmargarete@caronmargarete-laptop:~$ deb http://packages.medibuntu.org/ lucid free non-free
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
caronmargarete@caronmargarete-laptop:~$ 
```Please excuse me if the answer is obvious but why would I take from Medibuntu depot when I'm using ubuntu? Is there an easier way to update my version to 1.4.0?

Thanks in advance,
Caron.

---

### Post by Eolinwen on 2011-10-02
Hi Margarete,

Good idea to contact me in MP. THis forum is so huge and there are no possibility to follow the threads which I answered it. :D

Before, one word about licence's problems.  H264 and MP3 are proprietaries codecs and only the framework Gstreamer (installed by default) can do that without any actions of the user at the installation (well only said I want to use them). The reason is because Fluendo (the cie behind GStreamer paid a right for using them). It is not the case for all software which use this codecs like FFmpeg.  So the version installed in the multiverse repository is without those. But they are available thanks to the community (i.e by Medibuntu repository).

Like you are beginner and that's right that console is not funny but so powerful and like I am a Geek, I have given you the faster way to do that.

I will explain you know another method let's say more ...............graphical.

On the top right side, call the Update sources following this screenshots in the order. Push on the Configuration button. 

 [[IMG]http://pix.toile-libre.org/upload/img/1317580317.png[/IMG]]("http://pix.toile-libre.org/?img=1317580317.png")

[[IMG]http://pix.toile-libre.org/upload/img/1317580354.png[/IMG]]("http://pix.toile-libre.org/?img=1317580354.png")

[[IMG]http://pix.toile-libre.org/upload/img/1317580370.png[/IMG]]("http://pix.toile-libre.org/?img=1317580370.png")

At this step, you must click on below at the left side on the button Add. It will open the Software Sources.

[[IMG]http://pix.toile-libre.org/upload/thumb/1317580391.png[/IMG]]("http://pix.toile-libre.org/?img=1317580391.png")

The next screen will display and you copy paste this line in 

```
deb http://packages.medibuntu.org/ lucid free non-free
```[[IMG]http://pix.toile-libre.org/upload/img/1317580396.png[/IMG]]("http://pix.toile-libre.org/?img=1317580396.png")

You click on the right button called Add an updated source. Your manager will ask you to update the software list, you not do it now. You must add the key before and only after add this key you update it. It will said you the new update software. You update those and you could check in the Ubuntu Software Center the version of FFmpeg (I believe it but I am not sure. Because I am not using the Ubuntu Software Manager but more Synaptic or the console) .

For having the last version you must add the Openshot repository.  And it will be better to have the last version of MLT by the Sunab repository. I gave you the good command line in my previous post.

For having the Openshot repository, you must open an console and copy paste the following line 
```
sudo add-apt-repository ppa:jonoomph/openshot-edge
```And update after you Update manager (first and second screenshot).

If my explanations are not clear take a look here :
[http://www.openshot.org/ppa/](http://www.openshot.org/ppa/)

Good luck. Take so much pleasure to use Openshot that we have had to create it. :lolflag:
IF you have yet some problems don't hesitate to contact me in Private.

Olivier/Cenwen

---

### Post by CaronMargarete on 2011-10-08
After trying this, and it still being seemingly technical- I'm sure it's easy for some. I decided to visit the openshot website to download the new version direct. 

It's much easier and there's a great forum at hand to help.

---

