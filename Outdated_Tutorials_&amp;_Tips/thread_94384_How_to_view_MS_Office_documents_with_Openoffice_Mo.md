---
title: "How to view MS Office documents with Openoffice Mozilla plugin"
date: 2005-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by sawjew on 2005-11-23
I spend a lot of time viewing Word, Powerpoint and Excel files online and I don't really want to download each one to view it.  I like to view the file first and then I can save it if I so desire.  I came up with this simple modification to enable me to view MS Office documents using the Openoffice plugin in Firefox.

The first thing is to make sure you have the Mozilla-openoffice.org package installed.


The next step is to open any Openoffice interface (I usually use Writer) and go to Tools > Options > Internet > Mozilla Plug-in and check "enable".

Next go to /home/<your_name>/.mozilla/firefox/
note: you will have to enable "Show Hidden Files" in Nautilus

You will find a file named "pluginreg.dat", open the file with a text editor.

**NOTE that you must have Firefox closed when you modify pluginreg.dat or it will overwrite your modified file with the defaults when you close it.**

You should find a section like this;

```
OpenOffice.org Plug-in handles all its documents:$
OpenOffice.org Plug-in:$
31
0:application/vnd.stardivision.calc:StarCalc 3.0 - 5.0:sdc:$
1:application/vnd.stardivision.chart:StarChart 3.0 - 5.0:sds:$
2:application/vnd.stardivision.draw:StarDraw 3.0 - 5.0:sda:$
3:application/vnd.stardivision.impress:StarImpress 3.0 - 5.0:sdd:$
4:application/vnd.stardivision.impress-packed:StarImpress-packed 3.0 - 5.0:sdp:$
5:application/vnd.stardivision.math:StarMath 3.0 - 5.0:smf:$
6:application/vnd.stardivision.writer:StarWriter Template 3.0 - 5.0:vor:$
7:application/vnd.stardivision.writer-global:StarWriter Global 3.0 - 5.0:sgl:$
8:application/vnd.staroffice.writer:StarWriter 3.0 - 5.0:sdw:$
9:application/vnd.sun.xml.calc:StarOffice 6.0/7 Spreadsheet:sxc:$
10:application/vnd.sun.xml.calc.template:StarOffice 6.0/7 Spreadsheet Template:stc:$
11:application/vnd.sun.xml.draw:StarOffice 6.0/7 Drawing:sxd:$
12:application/vnd.sun.xml.draw.template:StarOffice 6.0/7 Drawing Template:std:$
13:application/vnd.sun.xml.impress:StarOffice 6.0/7 Presentation:sxi:$
14:application/vnd.sun.xml.impress.template:StarOffice 6.0/7 Presentation Template:sti:$
15:application/vnd.sun.xml.math:StarOffice 6.0/7 Formula:sxm:$
16:application/vnd.sun.xml.writer:StarOffice 6.0/7 Text Document:sxw:$
17:application/vnd.sun.xml.writer.global:StarOffice 6.0/7 Master Document:sxg:$
18:application/vnd.sun.xml.writer.template:StarOffice 6.0/7 Text Document Template:stw:$
19:application/vnd.oasis.opendocument.text:OpenDocument Text:odt:$
20:application/vnd.oasis.opendocument.text-template:OpenDocument Text Template:ott:$
21:application/vnd.oasis.opendocument.text-master:OpenDocument Master Document:odm:$
22:application/vnd.oasis.opendocument.text-web:HTML Document Template:oth:$
23:application/vnd.oasis.opendocument.spreadsheet:OpenDocument Spreadsheet:ods:$
24:application/vnd.oasis.opendocument.spreadsheet-template:OpenDocument Spreadsheet Template:ots:$
25:application/vnd.oasis.opendocument.graphics:OpenDocument Drawing:odg:$
26:application/vnd.oasis.opendocument.graphics-template:OpenDocument Drawing Template:otg:$
27:application/vnd.oasis.opendocument.presentation:OpenDocument Presentation:odp:$
28:application/vnd.oasis.opendocument.presentation-template:OpenDocument Presentation Template:otp:$
29:application/vnd.oasis.opendocument.formula:OpenDocument Formula:odf:$
30:application/vnd.sun.xml.base:OpenDocument Database:odb:$
```

Add three lines to the end of this section so that there are now 33 lines and change the number at the top from 31 to 34.  The section should now read like this;

```
OpenOffice.org Plug-in handles all its documents:$
OpenOffice.org Plug-in:$
[COLOR="Red"]**34**[/COLOR]
0:application/vnd.stardivision.calc:StarCalc 3.0 - 5.0:sdc:$
1:application/vnd.stardivision.chart:StarChart 3.0 - 5.0:sds:$
2:application/vnd.stardivision.draw:StarDraw 3.0 - 5.0:sda:$
3:application/vnd.stardivision.impress:StarImpress 3.0 - 5.0:sdd:$
4:application/vnd.stardivision.impress-packed:StarImpress-packed 3.0 - 5.0:sdp:$
5:application/vnd.stardivision.math:StarMath 3.0 - 5.0:smf:$
6:application/vnd.stardivision.writer:StarWriter Template 3.0 - 5.0:vor:$
7:application/vnd.stardivision.writer-global:StarWriter Global 3.0 - 5.0:sgl:$
8:application/vnd.staroffice.writer:StarWriter 3.0 - 5.0:sdw:$
9:application/vnd.sun.xml.calc:StarOffice 6.0/7 Spreadsheet:sxc:$
10:application/vnd.sun.xml.calc.template:StarOffice 6.0/7 Spreadsheet Template:stc:$
11:application/vnd.sun.xml.draw:StarOffice 6.0/7 Drawing:sxd:$
12:application/vnd.sun.xml.draw.template:StarOffice 6.0/7 Drawing Template:std:$
13:application/vnd.sun.xml.impress:StarOffice 6.0/7 Presentation:sxi:$
14:application/vnd.sun.xml.impress.template:StarOffice 6.0/7 Presentation Template:sti:$
15:application/vnd.sun.xml.math:StarOffice 6.0/7 Formula:sxm:$
16:application/vnd.sun.xml.writer:StarOffice 6.0/7 Text Document:sxw:$
17:application/vnd.sun.xml.writer.global:StarOffice 6.0/7 Master Document:sxg:$
18:application/vnd.sun.xml.writer.template:StarOffice 6.0/7 Text Document Template:stw:$
19:application/vnd.oasis.opendocument.text:OpenDocument Text:odt:$
20:application/vnd.oasis.opendocument.text-template:OpenDocument Text Template:ott:$
21:application/vnd.oasis.opendocument.text-master:OpenDocument Master Document:odm:$
22:application/vnd.oasis.opendocument.text-web:HTML Document Template:oth:$
23:application/vnd.oasis.opendocument.spreadsheet:OpenDocument Spreadsheet:ods:$
24:application/vnd.oasis.opendocument.spreadsheet-template:OpenDocument Spreadsheet Template:ots:$
25:application/vnd.oasis.opendocument.graphics:OpenDocument Drawing:odg:$
26:application/vnd.oasis.opendocument.graphics-template:OpenDocument Drawing Template:otg:$
27:application/vnd.oasis.opendocument.presentation:OpenDocument Presentation:odp:$
28:application/vnd.oasis.opendocument.presentation-template:OpenDocument Presentation Template:otp:$
29:application/vnd.oasis.opendocument.formula:OpenDocument Formula:odf:$
30:application/vnd.sun.xml.base:OpenDocument Database:odb:$
[COLOR="Red"][B]31:application/msword:Opendocument Text:doc:$
32:application/vnd.ms-excel:Opendocument Spreadsheet:xls:$
33:application/vnd.ms-powerpoint:Opendocument Presentation:ppt:$[/B][/COLOR]
```

Note the modifications highlighted in the text.

Save this file and then go up one level to /home/<user_name>/.mozilla/ where you will find a duplicate copy of "pluginreg.dat".  Replace this pluginreg.dat with your modified pluginreg.dat.

It seems that if you don't replace both of these files the original version will overwrite the modified file next time you open Firefox.

Next time you open Firefox you should be able to view MS Office documents in  a browser window.

To check if this worked open Firefox and open Edit > Preferences > Downloads > Plug-ins and you should see DOC, PPT and XLS listed as supported filetypes.

I have found this to be very successful on Gnome but in KDE I found that the files open correctly, but when you close a tab with an MS Office document in it it crashes Firefox.  I have no idea what causes this.  give it a try and see if it works.

---

### Post by sybille on 2008-07-01
The location of pluginreg.dat has changed in Firefox 3, it's now found in the profile folder. For example:
/home/<your_name>/.mozilla/firefox/xxxxxxxx.default (where xxxxxxxx is a series of numbers)

This is now the only file that needs to be changed, in my experience.

---

### Post by Comhra on 2008-08-13
This Plugin for OO would be useful for me as well.  The trouble is when I open pluginreg.dat to edit the file, it doesn't look anything like the file in the first post.
I would like to get this working but I may need a little help here.

---

### Post by Comhra on 2008-08-13
I'm using Hardy and the file I'm talking about looks like this:

[B]Generated File. Do not edit.
[/B]
[HEADER]
Version:0.09:$

[PLUGINS]
/usr/lib/mozilla/plugins/mplayerplug-in.so:$
:$
1210674579000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.50<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
mplayerplug-in 3.50:$
28
0:video/mpeg:MPEG:mpg,mpeg:$
1:audio/mpeg:MPEG:mpg,mpeg:$
2:video/x-mpeg:MPEG:mpg,mpeg:$
3:video/x-mpeg2:MPEG2:mpv2,mp2ve:$
4:audio/mpeg:MPEG:mpg,mpeg:$
5:audio/x-mpeg:MPEG:mpg,mpeg:$
6:audio/mpeg2:MPEG audio:mp2:$
7:audio/x-mpeg2:MPEG audio:mp2:$
8:video/mp4:MPEG 4 Video:mp4:$
9:video/3gpp:MPEG 4 Video:mp4,3gp:$
10:audio/mpeg3:MPEG audio:mp3:$
11:audio/x-mpeg3:MPEG audio:mp3:$
12:audio/x-mpegurl:MPEG url:m3u:$
13:audio/mp3:MPEG audio:mp3:$
14:application/x-ogg:Ogg Vorbis Media:ogg:$
15:audio/ogg:Ogg Vorbis Audio:ogg:$
16:audio/x-ogg:Ogg Vorbis Audio:ogg:$
17:application/ogg:Ogg Vorbis / Ogg Theora:ogg:$
18:audio/flac:FLAC Audio:flac:$
19:audio/x-flac:FLAC Audio:flac:$
20:video/fli:FLI animation:fli,flc:$
21:video/x-fli:FLI animation:fli,flc:$
22:video/x-flv:Flash Video:flv:$
23:video/vnd.vivo:VivoActive:viv,vivo:$
24:application/x-nsv-vp3-mp3:Nullsoft Streaming Video:nsv:$
25:audio/x-mod:Soundtracker:mod:$
26:audio/basic:Basic Audio File:au,snd:$
27:audio/x-basic:Basic Audio File:au,snd:$
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so:$
:$
1210674579000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.50<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
Windows Media Player Plugin:$
18
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:video/x-msvideo:AVI:avi,*:$
3:video/msvideo:AVI:avi,*:$
4:application/x-mplayer2:Media Files:*:$
5:application/x-ms-wmv:Microsoft WMV video:wmv,*:$
6:video/x-ms-asf:Media Files:asf,asx,*:$
7:video/x-ms-wm:Media Files:wm,*:$
8:video/x-ms-wmv:Microsoft WMV video:wmv,*:$
9:audio/x-ms-wmv:Windows Media:wmv,*:$
10:video/x-ms-wmp:Windows Media:wmp,*:$
11:application/x-ms-wmp:Windows Media:wmp,*:$
12:video/x-ms-wvx:Windows Media:wvx,*:$
13:audio/x-ms-wax:Windows Media:wax,*:$
14:audio/x-ms-wma:Windows Media:wma,*:$
15:application/x-drm-v2:Windows Media:asx,*:$
16:audio/wav:Microsoft wave file:wav,*:$
17:audio/x-wav:Microsoft wave file:wav,*:$
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so:$
:$
1210674579000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.50<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
RealPlayer 9:$
7
0:audio/x-pn-realaudio:RealAudio:ram,rm:$
1:application/vnd.rn-realmedia:RealMedia:rm:$
2:application/vnd.rn-realaudio:RealAudio:ra,ram:$
3:video/vnd.rn-realvideo:RealVideo:rv:$
4:audio/x-realaudio:RealAudio:ra:$
5:audio/x-pn-realaudio-plugin:RealAudio:rpm:$
6:application/smil:SMIL:smil:$
/usr/lib/mozilla/plugins/mplayerplug-in-qt.so:$
:$
1210674579000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.50<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
QuickTime Plug-in 6.0 / 7:$
7
0:video/quicktime:Quicktime:mov:$
1:video/x-quicktime:Quicktime:mov:$
2:image/x-quicktime:Quicktime:mov:$
3:video/quicktime:Quicktime:mp4:$
4:video/quicktime:Quicktime - Session Description Protocol:sdp:$
5:application/x-quicktimeplayer:Quicktime:mov:$
6:application/smil:SMIL:smil:$
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so:$
:$
1210674579000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.50<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
DivX Browser Plug-In:$
2
0:video/divx:DivX Media Format:divx:$
1:video/vnd.divx:DivX Media Format:divx:$
/usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so:$
:$
1213088242000:1:5:$
Java(TM) Plug-in 1.6.0_07:$
Java(TM) Plug-in 1.6.0_07-b06:$
33
0:application/x-java-vm:Java::$
1:application/x-java-applet:Java::$
2:application/x-java-applet;version=1.1:Java::$
3:application/x-java-applet;version=1.1.1:Java::$
4:application/x-java-applet;version=1.1.2:Java::$
5:application/x-java-applet;version=1.1.3:Java::$
6:application/x-java-applet;version=1.2:Java::$
7:application/x-java-applet;version=1.2.1:Java::$
8:application/x-java-applet;version=1.2.2:Java::$
9:application/x-java-applet;version=1.3:Java::$
10:application/x-java-applet;version=1.3.1:Java::$
11:application/x-java-applet;version=1.4:Java::$
12:application/x-java-applet;version=1.4.1:Java::$
13:application/x-java-applet;version=1.4.2:Java::$
14:application/x-java-applet;version=1.5:Java::$
15:application/x-java-applet;version=1.6:Java::$
16:application/x-java-applet;jpi-version=1.6.0_07:Java::$
17:application/x-java-bean:Java::$
18:application/x-java-bean;version=1.1:Java::$
19:application/x-java-bean;version=1.1.1:Java::$
20:application/x-java-bean;version=1.1.2:Java::$
21:application/x-java-bean;version=1.1.3:Java::$
22:application/x-java-bean;version=1.2:Java::$
23:application/x-java-bean;version=1.2.1:Java::$
24:application/x-java-bean;version=1.2.2:Java::$
25:application/x-java-bean;version=1.3:Java::$
26:application/x-java-bean;version=1.3.1:Java::$
27:application/x-java-bean;version=1.4:Java::$
28:application/x-java-bean;version=1.4.1:Java::$
29:application/x-java-bean;version=1.4.2:Java::$
30:application/x-java-bean;version=1.5:Java::$
31:application/x-java-bean;version=1.6:Java::$
32:application/x-java-bean;jpi-version=1.6.0_07:Java::$
/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so:$
:$
1217279104000:1:5:$
The demo print plugin for unix.:$
Demo Print Plugin for unix/linux:$
1
0:application/x-print-unix-nsplugin:Demo Print Plugin for Unix/Linux:.pnt:$
/usr/lib/xulrunner-addons/plugins/libnullplugin.so:$
:$
1217279104000:1:5:$
The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.:$
Default Plugin:$
1
0:*:All types:.*:$
/usr/lib/flashplugin-nonfree/libflashplayer.so:$
:$
1218249106000:1:7:$
Shockwave Flash 9.0 r124:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

---

### Post by Comhra on 2008-08-13
Is there something I'm missing here?

---

### Post by Comhra on 2008-08-13
Strange one this.  Proxy,Search & E- Mail are the only items showing up in Open Office, under Tools/Options/Internet.  Mozilla-openoffice.org is not there.

---

### Post by sybille on 2008-08-13
Hi, have you actually installed the mozilla-openoffice.org package? That's the first step, and you won't see an OpenOffice.org section in pluginreg.dat if that package is not installed.

Here's an [apt-url]("http://tombuntu.com/index.php/2007/10/22/the-apturl-protocol-handler-in-ubuntu-710/") so that you can check if the package is installed: [mozilla-openoffice.org]("apt://mozilla-openoffice.org")

Don't worry about this part:
[QUOTE="Comhra"]Proxy,Search & E- Mail are the only items showing up in Open Office, under Tools/Options/Internet. Mozilla-openoffice.org is not there.[/QUOTE]
I don't see an option for the plugin under Tools -> Options -> Internet either, but the plugin works just fine for me.

---

### Post by Comhra on 2008-08-13
mozilla-openoffice.org is installed, I guess that you're right that the plug-in will work when it's called upon to do so.  Thanks for that.

---

### Post by sybille on 2008-08-13
Have you tried opening an ODT (or other OOo native format) file in Firefox? What happens?

Actually, I don't think it will work if there is no listing for OOo in pluginreg.dat....

If the plugin isn't working for ODT files, you could try closing Firefox completely, renaming pluginreg.dat (to pluginreg.bak, for example), and then starting Firefox again. This will force Firefox to regenerate a new pluginreg.dat file, and you'll be able to see if the new version contains any mention of OpenOffice.org.

---

### Post by atownley on 2009-01-21
You, sir, are the man!  Thanks for posting this hack.  I figured it was there somewhere, but it took a while to actually figure out how to do it.

This has saved me no end of trouble, and makes a project I wanted to do that much easier.

Kudos.

ast :D

---

### Post by mfraser on 2009-03-26
I've got the mozilla-openoffice.org package installed and the plugin works in Konqueror, but I can't get it to work in Firefox 3.0.7. The plugin isn't listed under Tools -> Add-ons, I've tried editing pluginreg.dat, but that doesn't help.

This is with Kubuntu 8.04.

---

### Post by you_must_conform on 2009-09-16
sawjew what a brilliant hack! i was searching for a way to open documents with firefox, and only found pdf viewers. then i discovered the OOo plugin. awesome! i knew OOo should be able to view MS docs, and then I found this thread. brilliant!

slight tweak is necessary if you ever want to do this in Windows (lol). I am on windows right now, and firefox encodes its data differently than what you have posted, sawjew. (or it could be a change in a later version, although i don't see a reason.)

anyway if you're in windows, append this:
```

30|application/msword|Opendocument Text|doc|$
31|application/vnd.ms-excel|Opendocument Spreadsheet|xls|$
32|application/vnd.ms-powerpoint|Opendocument Presentation|ppt|$

```
instead of this:
```

31:application/msword:Opendocument Text:doc:$
32:application/vnd.ms-excel:Opendocument Spreadsheet:xls:$
33:application/vnd.ms-powerpoint:Opendocument Presentation:ppt:$

```
don't limit yourself there! keep adding any mime type you want haha. open a gif with oo:
```

34:image/gif:Graphics Interchange Format:gif:$

```
colons to pipes, people, that's all! first and probably last post here. i don't know why i made this account, lol, but i made it a helluva long time ago (didn't even remember the name - still use the email though haha).

---

### Post by AsoSako on 2009-09-21
This doesn't seem to work with Firefox version 3.0 or later since there appears to be no pluginreg.dat at /home/<user_name>/.mozilla/

I can find and edit the first pluginreg.dat within the firefox directory however as you mentioned it would be reset to its previous settings if I don't edit the second file and I can't seem to find said file.  Can anyone please tell me the new location of the second pluginreg.dat
Or perhaps if it is some other file now that resets the original, and needs to be edited.

The only pluginreg.dat I currently find is within /home/MYUSERNAME/.mozilla/firefox/7rxcxj8v.default

---

### Post by Ms_Angel_D on 2009-09-21
I just got this running on Kubuntu 9.04 KDE 4.3 by installing the plugin as well as mozplugger.

I closed firefox installed the mozilla-openoffice.org & Mozplugger 

```
sudo apt-get install mozilla-openoffice.org mozplugger
```

than deleted

```
/home/MY_USERNAME/.mozilla/firefox/ix2cdkrb.default/pluginreg.dat
```

Firefox will regenerate the file.

Then when I launched firefox I was able to  open word documents & office spreadsheets. I didn't have any presentations to test with but I'm assuming they will work as well.

---

### Post by AsoSako on 2009-09-22
I seem to have fixed it.  Now if anyone knows a way to do this with Office '07 documents that would be great.  Personally I tried doing it with similar lines using the '07 MIME types and extensions, but it didn't seem to work at all.

---

### Post by TWO on 2010-01-20
Could anyone explain how they got this to work because as it stands I can only get .ppt files embedded with mozplugger. Both .doc and .xls open openoffice writer embedded but all I am presented with is a blank template.

---

