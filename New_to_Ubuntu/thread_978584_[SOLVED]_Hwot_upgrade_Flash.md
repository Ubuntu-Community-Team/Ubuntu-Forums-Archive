---
title: "[SOLVED] Hwot upgrade Flash"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-11-11
**[about: plugins]("about:plugins")** in Firefox says I'm running Shockwave Flash 9.0 r124. Currently sound in flash has stopped working. How can I upgrade to the latest flash and have sound?

All links I find who's similar to this one seems very outdated.

---

### Post by fooman on 2008-11-11
i assume you are using hardy as in your sig? ..if so:

open synaptic and search for flashplugin-nonfree,  right click on it and choose "mark for complete removal".

do the same for libflashsupport and gnash.

after those are uninstalled,  search for "adobe-flashplugin"

install it and you should be set.

---

### Post by neurostu on 2008-11-11
"adobe-flashplugin"  doesn't show up on my install, are you sure you haven't included an extra repository in your install?

---

### Post by michaeljohn225 on 2008-11-11
about: plugins in Firefox says I'm running Shockwave Flash 9.0 r124. Currently sound in flash has stopped working. How can I upgrade to the latest flash and have sound?

All links I find who's similar to this one seems very outdated.
__________________

---

### Post by philinux on 2008-11-11
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Or enable the partner repo it only contains flash from adobe and opera.
There's even a .deb file for linux. Make sure you uninstall flashplugin-nonfree.

---

### Post by peakshysteria on 2008-11-11
Thanks a million guys. Sound working with Shockwave Flash 10.0 r12. Installed the .deb

---

### Post by neurostu on 2008-11-11
> **philinux said:**
> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Or enable the partner repo it only contains flash from adobe and opera.
There's even a .deb file for linux. Make sure you uninstall flashplugin-nonfree.

Does this plugin have the same issues that libflashsupport has? (Crashing firefox all the time)

---

### Post by peakshysteria on 2008-11-11
Have been running stable all day. No issues at all. Current setup:

My Firefox Information

Last updated: Tue, 11 Nov 2008 23:13:29 GMT
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3

**Extensions** (enabled: 17, disabled: 0; total: 17)
[list]
[*][Dictionary Switcher](http://en.design-noir.de/mozilla/dictionary-switcher/) 1.0 
[*][Dictionary Tooltip](http://www.rjonna.com/ext/dictionarytip.php) 1.3 
[*][DownloadHelper](http://www.downloadhelper.net) 3.4 
[*][Flashblock](http://flashblock.mozdev.org/) 1.5.6 
[*][Forecastfox](http://forecastfox.mozdev.org/) 0.9.7.7 
[*][Greasemonkey](http://www.greasespot.net/) 0.8.20080609.0 
[*][InfoLister](http://mozilla.doslash.org/infolister) 0.10 
[*][last.fmCode](http://mll2.free.fr/?p=42) 0.7a 
[*][Linkification](http://yellow5.us/firefox/linkification/) 1.3.5 
[*][Locationbar²](http://en.design-noir.de/mozilla/locationbar2/) 1.0.3 
[*][Nightly Tester Tools](http://www.oxymoronical.com/web/firefox/nightly) 2.0.2 
[*][Norsk Bokmål og Nynorsk ordliste]() 2.0.10.0 
[*][Tab Mix Plus](http://tmp.garyr.net) 0.3.7.3 
[*][Text Link](http://piro.sakura.ne.jp/xul/_textlink.html.en) 2.0.2008052801 
[*][Tiny Menu](http://trac.arantius.com/wiki/Extensions/TinyMenu) 1.4.9 
[*][Ubuntu Firefox Modifications]() 0.5 
[*][Update Channel Selector](http://www.oxymoronical.com/web/firefox/updatechannel) 1.0.3 
[/list]

**Themes** (4)
[list]
[*]Camifox [selected]
[*]Default 
[*]Gradient iCool 
[*]Qute 3++ (custom mod) 
[/list]

**Plugins**
[list]
[*]Default Plugin
[*]Demo Print Plugin for unix/linux
[*]DivX® Web Player
[*]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
[*]iTunes Application Detector
[*]Java(TM) Plug-in 1.6.0_07-b06
[*]QuickTime Plug-in 7.2.0
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.22.1
[*]VLC Multimedia Plugin (compatible Totem 2.22.1)
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[/list]

---

### Post by neurostu on 2008-11-12
Whats up with the iTunes Application detector plugin?

---

### Post by peakshysteria on 2008-11-12
Not sure actually. I haven't installed it myself. Looks like it came with the clean install. Strange.

Anyways, even stranger is that no today after rebooting my machine sound is missing once again. Ima is very good and CPU is much better than in flash 9. But how can I get my sound back again?

---

### Post by peakshysteria on 2008-11-14
Solved thanks to this thread: [http://ubuntuforums.org/showthread.php?p=6175945#post6175945](http://ubuntuforums.org/showthread.php?p=6175945#post6175945)

---

### Post by peakshysteria on 2008-11-18
Got a prompt for an update for Mozilla Firefox today. After upgrading from 3.0.3 to 3.0.4 once again flash plays without sound. Why is this happening? And how do I solve it. Every time I seem to find a solution there seems to be something new causing the same problem to appear.

---

### Post by jaysoun on 2008-11-18
i need to wirte  all my appilcation on a usb  to put it in my laptop how to do this?

---

### Post by peakshysteria on 2008-11-18
jaysoun: Really far away from your own thread one should think.

Solved my recurring Flash problem with an upgrade from Hardy to Intrepid. Had some trouble with getting my ATI driver up and running. But after following: [Installing the restricted drivers "the Ubuntu way"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22") Everything boothed fine and dandy. With working flash, java, ATI ccc, Compiz, SAMBA, NTFS, Google Earth etc.

Seems like I once again (for the third time) mark this thread as solved.
:)

---

