---
title: "lxde11.10 chromium missing plug-in? how to solve this?"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by vandrf on 2012-04-02
some file on you tube, many files cant wach missing plug-in error. 
I tried sudo apt-get install ubuntu-restricted-extras, but the same thing. Then install flash aid for firefox but the same thing in firefox. What to do next?

---

### Post by dniMretsaM on 2012-04-02
Did you actually run FlashAid after you installed it?

---

### Post by Rodney9 on 2012-04-02
Flash Install on Lubuntu - [http://ubuntuforums.org/showthread.php?t=1493672](http://ubuntuforums.org/showthread.php?t=1493672)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by vandrf on 2012-04-02
Yes i run FlashAid, but again the same thing.

---

### Post by dniMretsaM on 2012-04-02
Try installing the lubuntu-restricted-extras package. Also, FlashAid is for Firefox only, how are you running it in Chromium?

---

### Post by lovinglinux on 2012-04-02
> **vandrf said:**
> Yes i run FlashAid, but again the same thing.

Please click Flash-Aid Help menu, generate a report and post here.

---

### Post by vandrf on 2012-04-04
```
PART 1.
Ubuntu Architecture

Linux djordje-desktop 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-kde-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources


Flash packages

flashplugin-installer				install
Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86-gcc3:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1333405614000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1320721957000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
gecko-mediaplayer-rm.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so:$
:$
1313849555000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
RealPlayer 9:$
7
0:audio/x-pn-realaudio:RealAudio:ram,rm:$
1:application/vnd.rn-realmedia:RealMedia:rm:$
2:application/vnd.rn-realaudio:RealAudio:ra,ram:$
3:video/vnd.rn-realvideo:RealVideo:rv:$
4:audio/x-realaudio:RealAudio:ra:$
5:audio/x-pn-realaudio-plugin:RealAudio:rpm:$
6:application/smil:SMIL:smil:$
gecko-mediaplayer-dvx.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-dvx.so:$
:$
1313849555000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
DivX Browser Plug-In:$

2
0:video/divx:DivX Media Format:divx:$
1:video/vnd.divx:DivX Media Format:divx:$
gecko-mediaplayer-wmp.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so:$
:$
1313849555000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
Windows Media Player Plug-in:$
20
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:video/x-msvideo:AVI:avi,*:$
3:video/msvideo:AVI:avi,*:$
4:application/x-mplayer2:Media Files:*:$
5:video/x-mplayer2:Media Files:*:$
6:application/x-ms-wmv:Microsoft WMV video:wmv,*:$
7:video/x-ms-asf:Media Files:asf,asx,*:$
8:video/x-ms-asx:Media Files:asx,*:$
9:video/x-ms-wm:Media Files:wm,*:$
10:video/x-ms-wmv:Microsoft WMV video:wmv,*:$
11:audio/x-ms-wmv:Windows Media:wmv,*:$
12:video/x-ms-wmp:Windows Media:wmp,*:$
13:application/x-ms-wmp:Windows Media:wmp,*:$
14:video/x-ms-wvx:Windows Media:wvx,*:$
15:audio/x-ms-wax:Windows Media:wax,*:$
16:audio/x-ms-wma:Windows Media:wma,*:$
17:application/x-drm-v2:Windows Media:asx,*:$
18:audio/wav:Microsoft wave file:wav,*:$
19:audio/x-wav:Microsoft wave file:wav,*:$
gecko-mediaplayer-qt.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer-qt.so:$
:$
1313849555000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
QuickTime Plug-in 7.6.9:$
6
0:video/quicktime:Quicktime:mov:$
1:video/x-quicktime:Quicktime:mov:$
2:image/x-quicktime:Quicktime:mov:$
3:video/quicktime:Quicktime:mp4:$
4:video/quicktime:Quicktime - Session Description Protocol:sdp:$
5:application/x-quicktimeplayer:Quicktime:mov:$
gecko-mediaplayer.so:$
/usr/lib/mozilla/plugins/gecko-mediaplayer.so:$
:$
1313849555000:1:5:$
<a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$
mplayerplug-in is now gecko-mediaplayer 1.0.4:$

46
0:audio/x-mpegurl:MPEG Playlist:m3u:$
1:video/mpeg:MPEG:mpg,mpeg:$
2:audio/mpeg:MPEG:mpg,mpeg:$
3:video/x-mpeg:MPEG:mpg,mpeg:$
4:video/x-mpeg2:MPEG2:mpv2,mp2ve:$
5:audio/mpeg:MPEG:mpg,mpeg:$
6:audio/x-mpeg:MPEG:mpg,mpeg:$
7:audio/mpeg2:MPEG audio:mp2:$
8:audio/x-mpeg2:MPEG audio:mp2:$
9:audio/mp4:MPEG 4 audio:mp4:$
10:audio/x-mp4:MPEG 4 audio:mp4:$
11:video/mp4:MPEG 4 Video:mp4:$
12:video/x-m4v:MPEG 4 Video:m4v:$
13:video/3gpp:MPEG 4 Video:mp4,3gp:$
14:audio/mpeg3:MPEG audio:mp3:$
15:audio/x-mpeg3:MPEG audio:mp3:$
16:audio/x-mpegurl:MPEG url:m3u:$
17:audio/mp3:MPEG audio:mp3:$
18:application/x-ogg:Ogg Vorbis Media:ogg,oga,ogm:$
19:application/ogg:Ogg Vorbis Media:ogg,oga,ogm:$
20:audio/x-ogg:Ogg Vorbis Audio:ogg,oga:$
21:audio/ogg:Ogg Vorbis Audio:ogg,oga:$
22:video/x-ogg:Ogg Vorbis Video:ogg,ogm:$
23:video/ogg:Ogg Vorbis Video:ogg,ogm:$
24:application/x-vlc-plugin:VLC plug-in:vlc:$
25:application/x-google-vlc-plugin:Google VLC plug-in::$
26:audio/flac:FLAC Audio:flac:$
27:audio/x-flac:FLAC Audio:flac:$
28:video/fli:FLI animation:fli,flc:$
29:video/x-fli:FLI animation:fli,flc:$
30:video/x-flv:Flash Video:flv:$
31:video/flv:Flash Video:flv:$
32:video/vnd.vivo:VivoActive:viv,vivo:$
33:audio/x-matroska:Matroska Audio:mka:$
34:video/x-matroska:Matroska Video:mkv:$
35:application/x-nsv-vp3-mp3:Nullsoft Streaming Video:nsv:$
36:audio/x-mod:Soundtracker:mod:$
37:audio/x-aiff:AIFF Audio:aif:$
38:audio/basic:Basic Audio File:au,snd:$
39:audio/x-basic:Basic Audio File:au,snd:$
40:audio/x-scpls:Shoutcast Playlist:pls:$
41:video/x-mng:Multiple-Image Network Graphics:mng:$
42:audio/webm:WEBM audio File:webm:$
43:audio/x-webm:WEBM audio File:webm:$
44:video/webm:WEBM video File:webm:$
45:video/x-webm:WEBM video File:webm:$

[INVALID]
```

---

### Post by lovinglinux on 2012-04-05
First, click "Check Update" in the extension menu and wait to receive a message. Make sure the message is that a new version of flash is available. If not, let me know. This is because Adobe just purged the last beta flash from their servers and Flash-Aid needs to get the latest version url.

Once you update the version information, launch Flash-Aid Wizard and select the beta version in the installation options. Don't worry, that is not actually a beta, but the same version from the repositories, since Adobe will no longer provide betas. Proceed with the Wizard to install flash. Restart any browser to take effect.

---

### Post by vandrf on 2012-04-07
I tried 2-3 times and the same again. missing plug-in, when watching youtube video? What to try now?

---

### Post by lovinglinux on 2012-04-07
> **vandrf said:**
> I tried 2-3 times and the same again. missing plug-in, when watching youtube video? What to try now?

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by vandrf on 2012-04-08
Solved. Tnx. I downgrade flash and now works.:p

---

### Post by pyutaros on 2012-11-19
I didn't read the entire thread, so I apologize if someone already posted something like this.  I got tired of manually downgrading flash on every computer I use, so i wrote this script.  Save it to a your computer and remove the ".txt".  Make sure it's sent to run as an executable and then you can run it from a terminal by typing ./Adobe_fix.  Here is the code below:

```
wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip
unzip fp_11.1.102.63_archive.zip
tar -xzvf fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz -C fp_11.1.102.63_archive/
sudo cp -f fp_11.1.102.63_archive/libflashplayer.so /usr/lib/flashplugin-installer
```

---

