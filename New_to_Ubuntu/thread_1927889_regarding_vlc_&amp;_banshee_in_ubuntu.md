---
title: "regarding vlc &amp; banshee in ubuntu"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by rishiar4 on 2012-02-18
1.how to set vlc as default player??
2.When i play a song in banshee it gives the following error...

[ATTACH]212940[/ATTACH]

---

### Post by maurizzzio on 2012-02-19
You need to download codecs to play mp3 files (just search for Ubuntu Restricted Extras in the Ubuntu Software center) and to set VLC as the default player goto System Settings >  System Info and change the default applications as you wish, if this doesn't work download Ubuntu Tweak and change the default applications (this last method will work for sure) ;)

---

### Post by sadaruwan12 on 2012-02-19
It's not a error banshee doesn't come with the codecs to play file like .mp3 so when you try to play a file like that this message is given and from here select the search button then after ward a list of available codecs will be displayed.

Select them and click to install them that's it after that you want get this message ever.

But is you want set the VLC as your default player then select the file you want to play right click on that then go to open with tab select the VLC palyer and click ok that's it all the other file which are in the same file format will be associated with the VLC player automatically.

---

### Post by fractalman on 2012-02-19
The codecs you need are in a package called ubuntu-restricted-extras, you can find it in the software center or synaptic package manager. it contains loads of codecs for mp3 and similar but ubuntu can't ship with it as a default package due to licensing restrictions.

if you want to set vlc as your default media player then choose system>preferences>preferred applications and select vlc

---

### Post by rishiar4 on 2012-02-20
> **fractalman said:**
> The codecs you need are in a package called ubuntu-restricted-extras, you can find it in the software center or synaptic package manager. it contains loads of codecs for mp3 and similar but ubuntu can't ship with it as a default package due to licensing restrictions.

if you want to set vlc as your default media player then choose system>preferences>preferred applications and select vlc

when i tried to install that i got this
how to fix this????

---

### Post by ubuntu27 on 2012-02-20
Hmm... then try installing it using the [Terminal]("http://www.psychocats.net/ubuntu/terminal") 

Open the terminal, and then type (you can copy and paste)

```
[sudo apt-get install ubuntu-restricted-extras]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")
```

hit ENTER

and then type your password. Don't worry that you don't see anything that you type. That is a security feature.


For additional information see:

[Where is the Terminal?]("http://www.psychocats.net/ubuntu/terminal")

[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")
[URL="http://www.psychocats.net/ubuntu/installingsoftware"]
Installing Software in Ubuntu[/URL]


FOR A FREE UBUNTU GUIDE BOOK:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by rishiar4 on 2012-02-20
[QUOTE=ubuntu27;11703039]Hmm... then try installing it using the [Terminal]("http://www.psychocats.net/ubuntu/terminal") 

Open the terminal, and then type (you can copy and paste)

```
[sudo apt-get install ubuntu-restricted-extras]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")
```hit ENTER

and then type your password. Don't worry that you don't see anything that you type. That is a security feature.


For additional information see:

[Where is the Terminal?]("http://www.psychocats.net/ubuntu/terminal")

[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

[URL="http://www.psychocats.net/ubuntu/installingsoftware"]got this as output!!!!

```
Reading state information... Done
The following extra packages will be installed:
  ca-certificates-java freepats gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icedtea-netx icedtea-plugin icedtea6-plugin java-common libaccess-bridge-java
  libaccess-bridge-java-jni libavcodec-extra-53 libavutil-extra-51 libcdaudio1 libcelt0-0 libdirectfb-1.2-9
  libfaac0 libfftw3-3 libflite1 libgme0 libid3tag0 libmimic0 libmjpegtools-1.9 libmms0 libmp3lame0
  libmusicbrainz4c2a libofa0 liboil0.3 libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libopenspc0
  libquicktime2 libsidplay1 libslv2-9 libsoundtouch0 libts-0.0-0 libvo-aacenc0 libvo-amrwbenc0 libwildmidi1
  libxvidcore4 libzbar0 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib tsconf ttf-dejavu-extra
  ttf-mscorefonts-installer tzdata-java ubuntu-restricted-addons unrar
Suggested packages:
  default-jre equivs libfaad0 libfftw3-dev sidplay-base xsidplay slv2-jack sun-java6-fonts ttf-sazanami-gothic
  ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts
Recommended packages:
  w32codecs
The following packages will be REMOVED:
  libavcodec53 libavutil51
The following NEW packages will be installed:
  ca-certificates-java freepats gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icedtea-netx icedtea-plugin icedtea6-plugin java-common libaccess-bridge-java
  libaccess-bridge-java-jni libavcodec-extra-53 libavutil-extra-51 libcdaudio1 libcelt0-0 libdirectfb-1.2-9
  libfaac0 libfftw3-3 libflite1 libgme0 libid3tag0 libmimic0 libmjpegtools-1.9 libmms0 libmp3lame0
  libmusicbrainz4c2a libofa0 liboil0.3 libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libopenspc0
  libquicktime2 libsidplay1 libslv2-9 libsoundtouch0 libts-0.0-0 libvo-aacenc0 libvo-amrwbenc0 libwildmidi1
  libxvidcore4 libzbar0 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib tsconf ttf-dejavu-extra
  tzdata-java ubuntu-restricted-addons ubuntu-restricted-extras unrar
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 56 newly installed, 2 to remove and 4 not upgraded.
7 not fully installed or removed.
Need to get 0 B/95.2 MB of archives.
After this operation, 181 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

```
Installing Software in Ubuntu[/URL]

---

### Post by ubuntu27 on 2012-02-20
Do you have Synaptic Package Manager installed?

If so, open Synaptoc P.M. and go to Package, and then "Fix Broken Packages", then click on APPLY.


If you dno't have Synaptoc Package Manager...
[This thread]("http://ubuntuforums.org/showthread.php?t=1856256&page=2") might help you:

---

### Post by rishiar4 on 2012-02-21
> **ubuntu27 said:**
> Do you have Synaptic Package Manager installed?

If so, open Synaptoc P.M. and go to Package, and then "Fix Broken Packages", then click on APPLY.


If you dno't have Synaptoc Package Manager...
[This thread]("http://ubuntuforums.org/showthread.php?t=1856256&page=2") might help you:

thanx for the link its working...... :)

---

