---
title: "Flash problems - newbie"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by someguy3 on 2012-05-17
Total beginner here.  I cannot get Adobe Flash Player or any substitutes (including Ubuntu Restricted Extras) to properly install.  I keep getting messages that I need to check my internet connection and that the package cannot download. Here is the specific message:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libo/liboil/liboil0.3_0.3.17-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libo/liboil/liboil0.3_0.3.17-2ubuntu2_i386.deb) 404  Not Found [IP: 91.189.92.182 80]

I'm new here obviously, but I just installed Ubuntu and downloaded the firmware for my wifi card, as it was not initially recognized by Ubuntu.  I'm using it now, so I'm confused as to why it will not install.  Any help would be appreciated.

---

### Post by sreeakshay on 2012-05-17
Sorry to post this here. I am unable to find the means to post a new post at ubuntu forums. Can someone give me the instructions for that?

Thanks,

Akshay

---

### Post by Vereinfachen on 2012-05-17
someguy3,
are you able to update your system? Your internet connection works? You install by installing ubuntu-restricted-extras like this
```
sudo apt-get install ubuntu-restricted-extras
```
Could you upload your /etc/apt/sources.list somewhere so I can take a look? Like pastebin or poste them here in [ code] tags.

sreeakshay,
you go back into the specific forum category. There is a button on the top left called "New Thread" that you have to click to create a new topic.

---

### Post by sreeakshay on 2012-05-17
thanks Vereinfachen

---

### Post by Marcappuccino on 2012-05-17
[FONT="Georgia"]@Someguy3
Hi, try entering ```
sudo apt-get install ubuntu-restricted-extras
``` from the terminal, if that doesnt work, try installing Chromium ```
sudo apt-get install chromium-browser
```or Chrome (Through [http://www.google.co.uk/chrome](http://www.google.co.uk/chrome)) - They are both bundled with Adobe Flash and don't require you to install them manually.
If those don't work, try installing a different flavour, such as Kubuntu, Xubuntu, or even Lubuntu, *or* try a reinstall of Ubuntu.

@Sreeakshay
Go to homepage, select category, and cick on 'New Thread'[/FONT]

---

### Post by someguy3 on 2012-05-17
Thanks for the quick reply.


Here is the message I got after trying from the terminal

chris@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract freepats gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly liba52-0.7.4 libass4 libavcodec-extra-53
  libavformat53 libavutil-extra-51 libcdaudio1 libcelt0-0 libdc1394-22 libdca0
  libdirac-encoder0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libfaac0
  libfaad2 libfftw3-3 libflite1 libgme0 libgsm1 libgstreamer-plugins-bad0.10-0
  libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug1 libmp3lame0
  libmpcdec6 libmpeg2-4 libofa0 liboil0.3 libopenal-data libopenal1
  libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libopenspc0 libpostproc52
  libquicktime2 libschroedinger-1.0-0 libsidplay1 libslv2-9 libsoundtouch0
  libspandsp2 libswscale2 libts-0.0-0 libtwolame0 libva1 libvo-aacenc0
  libvo-amrwbenc0 libvpx1 libwildmidi-config libwildmidi1 libx264-120
  libxvidcore4 libzbar0 libzvbi-common libzvbi0 tsconf
  ttf-mscorefonts-installer ubuntu-restricted-addons unrar
Suggested packages:
  frei0r-plugins libfaad0 libdvdcss2 debhelper fakeroot build-essential
  libfftw3-dev sidplay-base xsidplay slv2-jack
The following NEW packages will be installed:
  cabextract freepats gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly liba52-0.7.4 libass4 libavcodec-extra-53
  libavformat53 libavutil-extra-51 libcdaudio1 libcelt0-0 libdc1394-22 libdca0
  libdirac-encoder0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libfaac0
  libfaad2 libfftw3-3 libflite1 libgme0 libgsm1 libgstreamer-plugins-bad0.10-0
  libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug1 libmp3lame0
  libmpcdec6 libmpeg2-4 libofa0 liboil0.3 libopenal-data libopenal1
  libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libopenspc0 libpostproc52
  libquicktime2 libschroedinger-1.0-0 libsidplay1 libslv2-9 libsoundtouch0
  libspandsp2 libswscale2 libts-0.0-0 libtwolame0 libva1 libvo-aacenc0
  libvo-amrwbenc0 libvpx1 libwildmidi-config libwildmidi1 libx264-120
  libxvidcore4 libzbar0 libzvbi-common libzvbi0 tsconf
  ttf-mscorefonts-installer ubuntu-restricted-addons ubuntu-restricted-extras
  unrar
0 upgraded, 71 newly installed, 0 to remove and 0 not upgraded.
Need to get 143 kB/61.3 MB of archives.
After this operation, 103 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe liboil0.3 i386 0.3.17-2ubuntu2
  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libo/liboil/liboil0.3_0.3.17-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libo/liboil/liboil0.3_0.3.17-2ubuntu2_i386.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Also, I know nothing of programming stuff, so if you have the patience to walk me through how to do some of these things you're suggesting, that would be amazing.


EDIT: my internet works fine as far as I can tell.  I'm using it now.

---

### Post by Vereinfachen on 2012-05-17
can you post your /etc/apt/sources.list?

Edit: open a terminal (dash->enter terminal) and run 
```
gedit /etc/apt/sources.list
```

copy and paste the text

---

### Post by someguy3 on 2012-05-17
> **Vereinfachen said:**
> can you post your /etc/apt/sources.list?
I'm new enough to this that I'm not positive that this is what you want, but here is what I found:

# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

---

### Post by Vereinfachen on 2012-05-18
What do you get when you run
```
sudo apt-get update
```
? :)

---

### Post by westie457 on 2012-05-18
> **someguy3 said:**
> I'm new enough to this that I'm not positive that this is what you want, but here is what I found:

# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

@ someguy3

No-one else has said this yet. Welcome to UF.

If that is all of your sources list it is not long enough. To get the restricted extras you need to enable some more repositories. Unfortunately I do not know how to add repos using the command line.
So we will do it through Update Manager.

Start Update Manager click 'Settings' - bottom left corner- a small window opens.

In the 'Ubuntu Software' tab put a check mark in all of the boxes except for the one called source.

In the 'Updates' tab check the first 2 boxes and the fourth box, leave the third empty. Click on 'Close' and again to exit Update Manager.

Try those terminal commands again starting with ```
sudo apt-get update
```

---

