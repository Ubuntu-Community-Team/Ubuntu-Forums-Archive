---
title: "Problem with Flash after latest Firefox update."
date: 2012-04-01
forum: New to Ubuntu
---

### Post by TheMustangZone on 2012-04-01
For some reason, after the recent automatic Firefox update, my Flash is now not working.  I can't see any videos now.  This may be a simple fix, but I'm not sure where to look.  Thanks in advance for any advice.

Rob

---

### Post by Starcruiser322 on 2012-04-01
If you go into your Ubuntu Software Center>Installed section and remove the flash plugin, then search for it and re-install it, that usually helps.

---

### Post by TheMustangZone on 2012-04-01
Thanks, I'll try that.

---

### Post by Starcruiser322 on 2012-04-02
> **TheMustangZone said:**
> Thanks, I'll try that.
Any luck?

---

### Post by lovinglinux on 2012-04-02
Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by celem on 2012-04-02
I had the same problem. I installed Flash-Aid and first did the stable flash install. This was no help. Next I installed the beta install. This worked. I now have flash back in Firefox. Thanks.

---

### Post by lovinglinux on 2012-04-02
> **celem said:**
> I had the same problem. I installed Flash-Aid and first did the stable flash install. This was no help. Next I installed the beta install. This worked. I now have flash back in Firefox. Thanks.

You are welcome. Thanks for reporting.

---

### Post by TheMustangZone on 2012-04-02
> **Starcruiser322 said:**
> Any luck?

No luck with removing and reinstalling.  Any other ideas?

---

### Post by TheMustangZone on 2012-04-02
I just tried the Flash-Aid install and it still does not work.  This is very frustrating. :mad:

---

### Post by flurospar on 2012-04-03
Try getting the DEB from [here]("http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_11_for_Ubuntu_%28apt%29") and see if that works.

---

### Post by lovinglinux on 2012-04-03
> **TheMustangZone said:**
> I just tried the Flash-Aid install and it still does not work.  This is very frustrating. :mad:

Please click Flash-Aid Help menu, generate a report and paste here.

Assuming you are suffering the same problem as everyone that has an nVidia card, then you need to disable hardware acceleration in flash or downgrade.

To disable hardware acceleration, right-click on a video end select Settings.

To downgrade get the flash player version 11.1.102.63 from [Adobe](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip). Extract the archive, find the tar.gz file corresponding to your architecture and copy it (don't extract it). Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the one from the tar.gz file in the proper location.

---

### Post by Benchrest on 2012-04-03
Thankyou, this worked for me to downgrade. My machine that did not work has a ATI Radeon 9600 XT graphics card. I found the downgrade worked a bit different for me than your write up. Going to "here" in your post downloaded a file.  I opened Flash-aid custom and pointed it to that file. it determined directories for me and one was 32 bit. I selected that and then it list a bunch of tar.gz files of which the first one matched my machine. I then went to the Script tab as you said and wala it worked! Thankyou.

---

### Post by lovinglinux on 2012-04-03
> **Benchrest said:**
> Thankyou, this worked for me to downgrade. My machine that did not work has a ATI Radeon 9600 XT graphics card. I found the downgrade worked a bit different for me than your write up. Going to "here" in your post downloaded a file.  I opened Flash-aid custom and pointed it to that file. it determined directories for me and one was 32 bit. I selected that and then it list a bunch of tar.gz files of which the first one matched my machine. I then went to the Script tab as you said and wala it worked! Thankyou.

You are welcome.

---

### Post by marcellux on 2012-04-03
Thank you very much!!!!!! Just installed the flash-aid add-on, upgraded to the beta version of flash, reboot was needed and now everything works fine again!!!

---

### Post by lovinglinux on 2012-04-03
> **marcellux said:**
> Thank you very much!!!!!! Just installed the flash-aid add-on, upgraded to the beta version of flash, reboot was needed and now everything works fine again!!!

You are welcome.

---

### Post by TheMustangZone on 2012-04-03
> **lovinglinux said:**
> Please click Flash-Aid Help menu, generate a report and paste here.

Assuming you are suffering the same problem as everyone that has an nVidia card, then you need to disable hardware acceleration in flash or downgrade.

To disable hardware acceleration, right-click on a video end select Settings.

To downgrade get the flash player version 11.1.102.63 from [Adobe]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip"). Extract the archive, find the tar.gz file corresponding to your architecture and copy it (don't extract it). Open Flash-Aid Advanced mode, select "Custom" in the installation option, paste the tar.gz path in the field. Click the Script tab, then Execute. Flash-Aid will remove all installed flash versions and install the one from the tar.gz file in the proper location.

Here is the info from Flash-Aid help:
```

Ubuntu Architecture  Linux RobsPC 2.6.32-40-generic #87-Ubuntu SMP Mon Mar 5 20:26:31 UTC 2012 i686 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=10.04 DISTRIB_CODENAME=lucid DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"  Firefox Packages  firefox                        install firefox-branding                install firefox-gnome-support                install firefox-locale-en                install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources  lucid-partner.list  Flash packages  adobe-flash-properties-gtk            install adobe-flashplugin                install flashplugin-installer                deinstall Plugin locations   /usr/lib/firefox/plugins/flashplugin-alternative.so /usr/lib/iceape/plugins/flashplugin-alternative.so /usr/lib/iceweasel/plugins/flashplugin-alternative.so /usr/lib/midbrowser/plugins/flashplugin-alternative.so /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/xulrunner/plugins/flashplugin-alternative.so /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so  Flash symlinks   /usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory) /usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' /etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' /usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) /usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) /usr/lib/adobe-flashplugin/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped /usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) /usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) /usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86-gcc3:$  [PLUGINS] libflashplayer.so:$ /usr/lib/adobe-flashplugin/libflashplayer.so:$ :$ 1331854066000:1:1:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1329507418000:1:4:$ The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)) executes Java applets.:$ IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_20:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_20:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ librhythmbox-itms-detection-plugin.so:$ /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$ :$ 1277463660000:1:5:$ This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$ iTunes Application Detector:$ 1 0:application/itunes-plugin:::$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 2.30.2):$ 19 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file:ogg:$ 4:application/ogg:Ogg multimedia file:ogg:$ 5:audio/ogg:Ogg Audio:oga:$ 6:audio/x-ogg:Ogg Audio:ogg:$ 7:video/ogg:Ogg Video:ogv:$ 8:video/x-ogg:Ogg Video:ogg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:application/x-totem-plugin:Totem Multimedia plugin::$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image:pntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1274279893000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ npPicasa3.so:$ /opt/google/picasa/3.0/lib/npPicasa3.so:$ :$ 1226106226000:1:5:$ Picasa plugin:$ Picasa:$ 1 0:application/x-picasa-detect:3.0:pinstall:$  [INVALID] 
```I tried right clicking on a video, but nothing happens because the video doesn't show up.  I'll try the downgrade link next.  Thanks.

Rob

---

### Post by lovinglinux on 2012-04-03
> **TheMustangZone said:**
> Here is the info from Flash-Aid help:
```

Ubuntu Architecture  Linux RobsPC 2.6.32-40-generic #87-Ubuntu SMP Mon Mar 5 20:26:31 UTC 2012 i686 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=10.04 DISTRIB_CODENAME=lucid DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"  Firefox Packages  firefox                        install firefox-branding                install firefox-gnome-support                install firefox-locale-en                install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources  lucid-partner.list  Flash packages  adobe-flash-properties-gtk            install adobe-flashplugin                install flashplugin-installer                deinstall Plugin locations   /usr/lib/firefox/plugins/flashplugin-alternative.so /usr/lib/iceape/plugins/flashplugin-alternative.so /usr/lib/iceweasel/plugins/flashplugin-alternative.so /usr/lib/midbrowser/plugins/flashplugin-alternative.so /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/xulrunner/plugins/flashplugin-alternative.so /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so  Flash symlinks   /usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory) /usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' /etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' /usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) /usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) /usr/lib/adobe-flashplugin/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped /usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) /usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) /usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86-gcc3:$  [PLUGINS] libflashplayer.so:$ /usr/lib/adobe-flashplugin/libflashplayer.so:$ :$ 1331854066000:1:1:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1329507418000:1:4:$ The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)) executes Java applets.:$ IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_20:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_20:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ librhythmbox-itms-detection-plugin.so:$ /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$ :$ 1277463660000:1:5:$ This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$ iTunes Application Detector:$ 1 0:application/itunes-plugin:::$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 2.30.2):$ 19 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file:ogg:$ 4:application/ogg:Ogg multimedia file:ogg:$ 5:audio/ogg:Ogg Audio:oga:$ 6:audio/x-ogg:Ogg Audio:ogg:$ 7:video/ogg:Ogg Video:ogv:$ 8:video/x-ogg:Ogg Video:ogg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:application/x-totem-plugin:Totem Multimedia plugin::$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image:pntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1274279893000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ npPicasa3.so:$ /opt/google/picasa/3.0/lib/npPicasa3.so:$ :$ 1226106226000:1:5:$ Picasa plugin:$ Picasa:$ 1 0:application/x-picasa-detect:3.0:pinstall:$  [INVALID] 
```I tried right clicking on a video, but nothing happens because the video doesn't show up.  I'll try the downgrade link next.  Thanks.

Rob

I see nothing wrong in your report. Let me know if the downgrade works.

---

### Post by TheMustangZone on 2012-04-04
> **lovinglinux said:**
> I see nothing wrong in your report. Let me know if the downgrade works.

I used the file from the downgrade link and that fixed it.  Thanks so much for all of the help.  I would have never figured it out on my own.:)

---

### Post by lovinglinux on 2012-04-05
> **TheMustangZone said:**
> I used the file from the downgrade link and that fixed it.  Thanks so much for all of the help.  I would have never figured it out on my own.:)

You are welcome.

---

### Post by Benchrest on 2012-04-17
Just noticed today there is another flash upgrade available.  Is there a way to permanently disable the flash upgrade, or at least make me do something extra to get it installed?  I saved the retro flash 11.1 so it's not a real big deal to reinstall it.  But now every time the update manager runs it will show I have this new flash to install. And if I'm not thinking (happens to often) I will install the new incompatible version. Maybe this should be a new thread as it would apply to any fix a person would want to permanently keep from installing.

---

### Post by lovinglinux on 2012-04-17
> **Benchrest said:**
> Just noticed today there is another flash upgrade available.  Is there a way to permanently disable the flash upgrade, or at least make me do something extra to get it installed?  I saved the retro flash 11.1 so it's not a real big deal to reinstall it.  But now every time the update manager runs it will show I have this new flash to install. And if I'm not thinking (happens to often) I will install the new incompatible version. Maybe this should be a new thread as it would apply to any fix a person would want to permanently keep from installing.

The tutorial you followed probably instructed to place the flash plugin in the flashplugin-installer folder, that's why new updates reverts to the problematic version.

Follow this [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) and you won't need to bother with each update.

---

### Post by daviddixit on 2012-04-17
> **lovinglinux said:**
> Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
Hello!
I had the same problem. I installed Flash-Aid and still it will not play videos anywhere.
What should I do ?
aaagh. I am out of my depth!

---

### Post by lovinglinux on 2012-04-19
> **daviddixit said:**
> Hello!
I had the same problem. I installed Flash-Aid and still it will not play videos anywhere.
What should I do ?
aaagh. I am out of my depth!

Click Flash-Aid menu, select "Help > Generate Report" then paste the report here, so I can take a look.

---

### Post by daviddixit on 2012-04-21
Where is the Flash aid menu ?!

---

### Post by lovinglinux on 2012-04-22
> **daviddixit said:**
> Where is the Flash aid menu ?!

If you don't know where it is, then you actually didn't use it yet. It is in the Tools menu. Run the Wizard before generating the report. It might fix your problem.

---

