---
title: "firefox 3.0 update?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-06-18
Hey guys,
I want to update to Firefox 3.0 from Firefox 3.0 Beta 5 and I have no idea how to do it.  Anyone have any help?

---

### Post by aysiu on 2008-06-18
> **SalsaShark said:**
> Hey guys,
I want to update to Firefox 3.0 from Firefox 3.0 Beta 5 and I have no idea how to do it.  Anyone have any help?
Are you using Ubuntu 8.04 or Ubuntu 7.10?

---

### Post by SalsaShark on 2008-06-18
Ohh yeah, I'm in 8.04

---

### Post by aysiu on 2008-06-18
> **SalsaShark said:**
> Ohh yeah, I'm in 8.04
Go to System > Administration > Software Sources, enable the Hardy Proposed Updates, click Reload when prompted, then go to System > Administration > Update Manager and install just the Firefox update.

Then go back to Software Sources and disable the Proposed Updates.

---

### Post by drsaamah on 2008-06-18
from my understanding, the final version of ff-3 is in the ubuntu repositories.  So it should update itself.  Open a terminal and type in
```
sudo apt-get update
```
Afterwards, if you haven't gotten the final version yet, update manager will open in X and prompt you to download the update.  If you already got the update, nothing will happen.
To double check what version you currently have, open up firefox and go to the "Help" menu on the toolbar and select "About".  That will tell you what version you are currently using.

---

### Post by SalsaShark on 2008-06-18
> **aysiu said:**
> Go to System > Administration > Software Sources, enable the Hardy Proposed Updates, click Reload when prompted, then go to System > Administration > Update Manager and install just the Firefox update.

Then go back to Software Sources and disable the Proposed Updates.


Ahhh, there it is.  Thank you very much.

---

### Post by Edgewalker_001 on 2008-06-18
This also helped me with not only this but another problem as well, thank you very much aysiu ^_^

---

### Post by niiiick on 2008-06-18
hey guys, i'm in hardy and am still using firefox 2.0.0.14.

firefox 3 doesn't appear to be in the regular or proposed repositories yet.  anything i can do to upgrade now?

---

### Post by aysiu on 2008-06-18
> **niiiick said:**
> hey guys, i'm in hardy and am still using firefox 2.0.0.14.

firefox 3 doesn't appear to be in the regular or proposed repositories yet.  anything i can do to upgrade now?
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
cat /etc/apt/sources.list
sudo apt-get update
apt-cache search firefox
```

---

### Post by niiiick on 2008-06-18
```

nick@spider-man:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://www.geexbox.org/debian/ unstable main
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main restricted multiverse
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb-src http://ppa.launchpad.net/do-core/ubuntu gutsy main
# deb http://ftp.de.debian.org/debian sid main
deb http://ppa.launchpad.net/banshee-team/ubuntu gutsy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu gutsy main
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb-src http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb http://moblock-deb.sourceforge.net/debian gutsy main
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://moblock-deb.sourceforge.net/debian gutsy main
nick@spider-man:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign http://www.geexbox.org unstable Release.gpg                                
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-en_US                      
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Get:4 http://moblock-deb.sourceforge.net gutsy Release.gpg [189B]              
Ign http://www.geexbox.org unstable/main Translation-en_US                     
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US               
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US               
Get:5 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]               
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US             
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://ppa.launchpad.net gutsy/main Translation-en_US                      
Hit http://ppa.launchpad.net gutsy Release                                     
Hit http://archive.canonical.com gutsy Release                                 
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US       
Get:6 http://archive.ubuntu.com gutsy-proposed Release.gpg [191B]              
Ign http://archive.ubuntu.com gutsy-proposed/universe Translation-en_US        
Hit http://www.geexbox.org unstable Release                                    
Hit http://ppa.launchpad.net gutsy Release                                     
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://archive.ubuntu.com gutsy-proposed/main Translation-en_US            
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US      
Ign http://archive.ubuntu.com gutsy-proposed/restricted Translation-en_US      
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://archive.ubuntu.com gutsy-updates Release                            
Ign http://ppa.launchpad.net gutsy/main Packages                               
Ign http://ppa.launchpad.net gutsy/main Sources                                
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://www.geexbox.org unstable/main Packages                              
Hit http://archive.ubuntu.com gutsy-proposed Release                           
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Ign http://ppa.launchpad.net gutsy/main Packages                               
Ign http://ppa.launchpad.net gutsy/main Sources                      
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://ppa.launchpad.net gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://ppa.launchpad.net gutsy/main Sources
Hit http://ppa.launchpad.net gutsy/main Packages                     
Hit http://archive.ubuntu.com gutsy-proposed/universe Packages       
Hit http://archive.ubuntu.com gutsy-proposed/main Packages           
Hit http://archive.ubuntu.com gutsy-proposed/multiverse Packages     
Hit http://archive.ubuntu.com gutsy-proposed/restricted Packages     
Hit http://ppa.launchpad.net gutsy/main Sources
Ign http://moblock-deb.sourceforge.net gutsy/main Translation-en_US
Hit http://moblock-deb.sourceforge.net gutsy Release
Hit http://moblock-deb.sourceforge.net gutsy/main Packages
Hit http://moblock-deb.sourceforge.net gutsy/main Sources
Fetched 6B in 2s (2B/s)
Reading package lists... Done
nick@spider-man:~$ apt-cache search firefox
firefox-themes-ubuntu - Firefox themes matching the Ubuntu desktop look
kubuntu-docs - kubuntu documentation
mozilla-firefox-locale-af - Mozilla Firefox Afrikaans language/region package
mozilla-firefox-locale-ar - Mozilla Firefox Arabic language/region package
mozilla-firefox-locale-be - Mozilla Firefox Belarusian language/region package
mozilla-firefox-locale-bg-bg - Mozilla Firefox Bulgarian language/region package
mozilla-firefox-locale-bn-bd - Transitional package for unavailable language
mozilla-firefox-locale-bn-in - Transitional package for unavailable language
mozilla-firefox-locale-ca - Mozilla Firefox Catalan; Valencian language/region package
mozilla-firefox-locale-cs-cz - Mozilla Firefox Czech language/region package
mozilla-firefox-locale-da-dk - Mozilla Firefox Danish language/region package
mozilla-firefox-locale-de-de - Mozilla Firefox German language/region package
mozilla-firefox-locale-el - Mozilla Firefox Greek, Modern (1453-) language/region package
mozilla-firefox-locale-en-gb - Mozilla Firefox English language/region package
mozilla-firefox-locale-es-ar - Mozilla Firefox Spanish; Castilian language/region package
mozilla-firefox-locale-es-es - Mozilla Firefox Spanish; Castilian language/region package
mozilla-firefox-locale-eu - Mozilla Firefox Basque language/region package
mozilla-firefox-locale-fi-fi - Mozilla Firefox Finnish language/region package
mozilla-firefox-locale-fr-fr - Mozilla Firefox French language/region package
mozilla-firefox-locale-fy-nl - Mozilla Firefox Western Frisian language/region package
mozilla-firefox-locale-ga-ie - Mozilla Firefox Irish language/region package
mozilla-firefox-locale-gu-in - Mozilla Firefox Gujarati language/region package
mozilla-firefox-locale-he-il - Mozilla Firefox Hebrew language/region package
mozilla-firefox-locale-hr - Transitional package for unavailable language
mozilla-firefox-locale-hu-hu - Mozilla Firefox Hungarian language/region package
mozilla-firefox-locale-it-it - Mozilla Firefox Italian language/region package
mozilla-firefox-locale-ja-jp - Mozilla Firefox Japanese language/region package
mozilla-firefox-locale-ka-ge - Mozilla Firefox Georgian language/region package
mozilla-firefox-locale-ko - Mozilla Firefox Korean language/region package
mozilla-firefox-locale-ku - Mozilla Firefox Kurdish language/region package
mozilla-firefox-locale-lt - Mozilla Firefox Lithuanian language/region package
mozilla-firefox-locale-mk-mk - Mozilla Firefox Macedonian language/region package
mozilla-firefox-locale-mn - Mozilla Firefox Mongolian language/region package
mozilla-firefox-locale-nb-no - Mozilla Firefox Norwegian Bokm&#65533;l; Bokm&#65533;l, Norwegian language/region package
mozilla-firefox-locale-nl-nl - Mozilla Firefox Dutch; Flemish language/region package
mozilla-firefox-locale-nn-no - Mozilla Firefox Norwegian Nynorsk; Nynorsk, Norwegian language/region package
mozilla-firefox-locale-nso - Mozilla Firefox Northern Sotho language/region package
mozilla-firefox-locale-pa-in - Mozilla Firefox Panjabi; Punjabi language/region package
mozilla-firefox-locale-pl-pl - Mozilla Firefox Polish language/region package
mozilla-firefox-locale-pt-br - Mozilla Firefox Portuguese language/region package
mozilla-firefox-locale-pt-pt - Mozilla Firefox Portuguese language/region package
mozilla-firefox-locale-ro-ro - Mozilla Firefox Romanian language/region package
mozilla-firefox-locale-ru-ru - Mozilla Firefox Russian language/region package
mozilla-firefox-locale-sk - Mozilla Firefox Slovak language/region package
mozilla-firefox-locale-sl-si - Mozilla Firefox Slovenian language/region package
mozilla-firefox-locale-sv-se - Mozilla Firefox Swedish language/region package
mozilla-firefox-locale-tr-tr - Mozilla Firefox Turkish language/region package
mozilla-firefox-locale-zh-cn - Mozilla Firefox Chinese language/region package
mozilla-firefox-locale-zh-tw - Mozilla Firefox Chinese language/region package
mozilla-firefox-locale-zu - Mozilla Firefox Zulu language/region package
totem-mozilla - Totem Mozilla plugin
xubuntu-docs - xubuntu documentation
bookmarkbridge - tool to synchronize bookmarks between browsers
firefox-3.0 - lightweight web browser based on Mozilla (Development Version)
firefox-3.0-dev - Development files for Mozilla Firefox (Development Version)
firefox-3.0-dom-inspector - dummy upgrade package for firefox-3.0-dom-inspector -> xulrunner-1.9-dom-inspector
firefox-3.0-gnome-support - Support for Gnome in Mozilla Firefox (Development Version)
firefox-3.0-venkman - dummy upgrade package for firefox-3.0-venkman -> xulrunner-1.9-venkman
firefox-granparadiso - dummy upgrade package for firefox-granparadiso -> firefox-3.0
firefox-granparadiso-dev - dummy upgrade package for firefox-granparadiso -> firefox-3.0
firefox-granparadiso-dom-inspector - dummy upgrade package for firefox-granparadiso -> firefox-3.0
firefox-granparadiso-gnome-support - dummy upgrade package for firefox-granparadiso -> firefox-3.0
firefox-greasemonkey - firefox extension that enables customization of webpages with user scripts
firefox-launchpad-plugin - Launchpad firefox integration
firefox-sage - lightweight RSS and Atom feed reader for Firefox
firefox-trunk - dummy upgrade package for firefox-trunk -> firefox-3.0
firefox-trunk-dev - dummy upgrade package for firefox-trunk -> firefox-3.0
firefox-trunk-dom-inspector - dummy upgrade package for firefox-trunk -> firefox-3.0
firefox-trunk-gnome-support - dummy upgrade package for firefox-trunk -> firefox-3.0
firefox-trunk-venkman - dummy upgrade package for firefox-trunk -> firefox-3.0
firefox-webdeveloper - web developer extension for the Firefox web browser
gnash - free SWF movie player
gnash-common - free SWF movie player - common files/libraries
gnash-cygnal - free SWF movie player - Media server
gnash-tools - free SWF movie player - Command-line Tools
gnome-launch-box - an application launcher.
gplanarity - simple puzzle game involving untangling planar graphs
gtkcookie - Editor for cookie files
helix-player - the helix audio and video player
junior-internet - Debian Jr. Internet tools
kdocker - minimize all applications to system tray
klash - free SWF movie player - standalone player for KDE
konqueror-plugin-gnash - free SWF movie player - Plugin for Konqueror
latex-xft-fonts - Xft-compatible versions of some LaTeX fonts
libflash-mozplugin - GPL Flash (SWF) Library - Mozilla-compatible plugin
libhtml-widgets-selectlayers-perl - Perl extension for selectable HTML layers
libmozjs-dev - Development files for the Mozilla SpiderMonkey JavaScript library
libmozjs0d - The Mozilla SpiderMonkey JavaScript library
libmozjs0d-dbg - Development files for the Mozilla SpiderMonkey JavaScript library
libxul-common - Gecko engine library - common files
libxul-dev - Development files for the Gecko engine library
libxul0d - Gecko engine library
libxul0d-dbg - Development files for the Gecko engine library
lightning-extension-locale-nb-no - Norwegian Bokmal language package for lightning-extension
lsr - The Linux Screen Reader for GNOME
midbrowser - mobile web browser based on Mozilla
mozilla-beagle - Beagle extension for Firefox
mozilla-bookmarksftp - Iceweasel/Firefox extension to synchronize bookmarks
mozilla-firefox-adblock - AdBlock extension for the Iceweasel and Iceape web browsers
mozilla-firefox-webdeveloper - web developer extension (transitional package)
mozilla-helix-player - the helix audio and video player (browser plugin)
mozilla-imagezoom - Mozilla context menu option to zoom current image
mozilla-livehttpheaders - Adds information about the HTTP headers to Firefox and SeaMonkey
mozilla-plugin-gnash - free SWF movie player - Plugin for Mozilla and derivatives
mozilla-stumbleupon - Mozilla addon for sharing interesting websites
pcmanfm - an extremely fast and lightweight file manager for X
pcmanfm-nohal - an extremely fast and lightweight file manager for X
peercast-handlers - P2P audio and video streaming handlers
squareness - suite of skins for different applications
tinymce - platform independent web based Javascript/HTML WYSIWYG editor
xulrunner - XUL + XPCOM application runner
xulrunner-1.9 - XUL + XPCOM application runner
xulrunner-1.9-dom-inspector - tool for inspecting the DOM of pages in Mozilla Firefox
xulrunner-1.9-venkman - Venkman is Mozilla-based JavaScript debugger
j2re1.4-mozilla-plugin - Java plugin for firefox
firefox-dom-inspector - tool for inspecting the DOM of pages in Mozilla Firefox
iceape - The Iceape Internet Suite
mozilla-plugin-vlc - multimedia plugin for web browsers based on VLC
firefox - lightweight web browser based on Mozilla
firefox-dbg - debugging symbols for firefox
firefox-dev - Development files for Mozilla Firefox
firefox-gnome-support - Support for Gnome in Mozilla Firefox
firefox-libthai - Support for Thai line breaking in Firefox
openoffice.org - OpenOffice.org Office suite
epiphany-browser - Intuitive GNOME web browser
ubufox - modifications for ubuntu firefox (default) install
flashplugin-nonfree - Adobe Flash Player plugin installer
gnome-do - Quickly perform actions on your desktop
gnome-do-plugins - Extra functionality for GNOME-Do launcher
nick@spider-man:~$ 

```

the firefox-3.0 is a dev version...alpha1

---

### Post by aysiu on 2008-06-18
You don't have Ubuntu 8.04 (Hardy Heron). You have Ubuntu 7.10 (Gutsy Gibbon).

There is no Ubuntu version of Firefox 3 for Ubuntu 7.10.

You need [this](http://www.psychocats.net/ubuntu/firefox) instead.

---

### Post by niiiick on 2008-06-18
hm.  no firefox 3 for hardy?  i see.

---

### Post by syxbit on 2008-06-18
there is firefox 3 for hardy. just not gutsy (well, there's an old, old version of it. a late alpha i think)

isn't firefox final just firefox 3rc2?

---

### Post by aysiu on 2008-06-18
> **niiiick said:**
> hm.  no firefox 3 for hardy?  i see.
There is Firefox 3 in Hardy, but you're not running Hardy.

You're running Gutsy. Gutsy has no Firefox 3.

---

