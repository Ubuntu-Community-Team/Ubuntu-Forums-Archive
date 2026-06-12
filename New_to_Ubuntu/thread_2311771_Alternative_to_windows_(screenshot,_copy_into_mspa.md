---
title: "Alternative to windows: (screenshot, copy into mspaint, minor editing (arrows etc))"
date: 2016-01-29
forum: New to Ubuntu
---

### Post by BluTiger on 2016-01-29
I'm desperately trying to find a good logical replacement to this simple process I used to do all the time in windows to help my friends and others with their website/windows needs.

I used to simply hit PrtSc (name of the button on my keyboard) and open up mspaint from the taskbar and paste it to the new image file (cropping out the extra stuff also) then start to mark it up with arrows and text boxes.

I've tried a few different of the default programs on Xubuntu and nothing at all seems to really let me do this...fast or efficiently. Am I looking at this little project the wrong way on linux or is there a similar alternative?

Thanks very much,
BluTiger, "Cam"

---

### Post by vasa1 on 2016-01-29
So what's needed is a screenshot program that stores the image in the clipboard to allow you to paste it somewhere else?

See post #9 in this thread: [https://forums.bunsenlabs.org/viewtopic.php?id=276](https://forums.bunsenlabs.org/viewtopic.php?id=276)

I didn't try it because I don't mind taking two steps instead of one ;)

---

### Post by Dennis N on 2016-01-30
Did you know Xubuntu's xfce4-screenshooter already allows you to open a screenshot in an image-editing application, such as gimp ready to edit? You can also copy it to the clipboard, if you wish.

To make it easier, there is a screenshot panel plugin that takes a screenshot of the entire screen with one click (no active-window-only option). Again, it's possible to open the screenshot in an application or paste to clipboard.

Other possibilities: You can run it from the command line, with a given set of options. You can create an alias to make that easier. Maybe even set up a hot key to run the alias.

---

### Post by Bucky Ball on 2016-01-30
Only ever used xfce4-screenshooter. Flexible, fast, lightweight and efficient. :D

You can install it from Synaptics or terminal with 

> sudo apt-get install xfce4-screenshooter

Actually, if you're using Xubuntu you should have it already under 'Accessories> Screenshot'.

---

### Post by Dennis N on 2016-01-30
> I used to simply hit PrtSc (name of the button on my keyboard) and open up mspaint from the taskbar and paste it to the new image file

Hey BluTiger, If you prefer a simple editor like mspaint I suggest you look at **pinta**, which is modeled after mspaint. You can select the screenshots to open in pinta (basic editing options) as well as gimp (with many advanced options).

---

### Post by vasa1 on 2016-01-30
> **Dennis N said:**
> Hey BluTiger, If you prefer a simple editor like mspaint I suggest you look at **pinta**, which is modeled after mspaint. You can select the screenshots to open in pinta (basic editing options) as well as gimp (with many advanced options).
Wouldn't *pinta* pull in mono dependencies? A very simple editor is *gpaint*. Lubuntu comes with *mtpaint*.

---

### Post by BluTiger on 2016-01-30
*Yawn, scratches, heads to coffee pot.*

Ok, I'll look into it. ;)

---

### Post by vasa1 on 2016-01-30
> **BluTiger said:**
> [I]*Yawn, scratches, heads to coffee pot.*

Ok, I'll look into it. ;)
[/I]
Thanks for letting people help you. Yawn, scratch, whatever ...

---

### Post by CantankRus on 2016-01-30
You can also look at the screenshot tool "shutter" which is capable 
of simple editing.

---

### Post by Dennis N on 2016-01-30
> **vasa1 said:**
> Wouldn't *pinta* pull in mono dependencies? A very simple editor is *gpaint*. Lubuntu comes with *mtpaint*.

Depends on mono? I checked, and yes it does. Pinta was one I had used in the past other than gimp - which is my personal choice, so I suggested it as much closer to paint (as I remember paint from XP!). I'm not familiar with either of the other two you mention.

Note: Steam also depends on mono, so in my case, it was already installed.

---

### Post by CantankRus on 2016-01-31
> **Dennis N said:**
> 

Note: Steam also depends on mono, so in my case, it was already installed.
Steam depends on mono???

---

### Post by vasa1 on 2016-01-31
> **Dennis N said:**
> Depends on mono? I checked, and yes it does. ....
I think at one time, mono was included by default in Ubuntu because *Tomboy*, IIRC, needed it. This package and mono was later dropped from Ubuntu.

---

### Post by Dennis N on 2016-01-31
> **CantankRus said:**
> Steam depends on mono???

See below. I have Steam installed in Manjaro. That is also where I installed Pinta.

```
[dmn@Zotac ~]$ pacman -Qi steam-manjaro
Name           : steam-manjaro
Version        : 1.0.0.51-4
Description    : Digital distribution client bootstrap package. Includes common
                 game depends. See
                 https://forum.manjaro.org/index.php?topic=16054
Architecture   : x86_64
URL            : http://steampowered.com/
Licenses       : custom
Groups         : None
Provides       : steam
Depends On     : bash  desktop-file-utils  hicolor-icon-theme  curl  dbus
                 freetype2  gdk-pixbuf2  ttf-font  zenity  libindicator-gtk2
                 libindicator-gtk3  dhcp-client  networkmanager  wpa_supplicant
                 [COLOR="#FF0000"]mono  mono-addins[/COLOR]  wqy-microhei  sdl  sdl_image  sdl_mixer
                 sdl2  sdl2_image  tcp_wrappers  speex  gperftools
                 libcurl-gnutls  rtmpdump  gnutls28  nettle4  lib32-libgl
                 lib32-gcc-libs  lib32-libx11  lib32-sdl  lib32-sdl_image
                 lib32-sdl_mixer  lib32-sdl2  lib32-sdl2_image
                 lib32-tcp_wrappers  lib32-speex  lib32-gperftools
                 lib32-libcurl-gnutls  lib32-rtmpdump  lib32-libgnutls28
                 lib32-nettle4

```

---

### Post by Dennis N on 2016-01-31
> **vasa1 said:**
> I think at one time, mono was included by default in Ubuntu because *Tomboy*, IIRC, needed it. This package and mono was later dropped from Ubuntu.

I don't have mono installed in Ubuntu, it is installed in Manjaro (as a dependency of steam-manjaro). That is where I installed Pinta, so I get a free ride.

I was unaware mono is no longer in Ubuntu's repositories. That makes it a bit harder to install Pinta. Too bad.

No response yet on what the OP actually did.

---

### Post by oldos2er on 2016-01-31
Seems pinta would install just fine on 15.10: ```
sudo apt-get install -s pinta
[sudo] password for ann:        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cli-common libgdiplus libglib2.0-cil libgtk2.0-cil libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo4.0-cil
  libmono-corlib2.0-cil libmono-corlib4.0-cil libmono-corlib4.5-cil libmono-i18n-west2.0-cil libmono-i18n-west4.0-cil
  libmono-i18n4.0-cil libmono-posix2.0-cil libmono-posix4.0-cil libmono-security2.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system2.0-cil libmono-system4.0-cil mono-4.0-gac mono-gac
  mono-runtime mono-runtime-common mono-runtime-sgen
Suggested packages:
  monodoc-gtk2.0-manual libmono-i18n2.0-cil libmono-i18n4.0-all libgamin0 libmono-winforms2.0-cil
The following NEW packages will be installed:
  cli-common libgdiplus libglib2.0-cil libgtk2.0-cil libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo4.0-cil
  libmono-corlib2.0-cil libmono-corlib4.0-cil libmono-corlib4.5-cil libmono-i18n-west2.0-cil libmono-i18n-west4.0-cil
  libmono-i18n4.0-cil libmono-posix2.0-cil libmono-posix4.0-cil libmono-security2.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system2.0-cil libmono-system4.0-cil mono-4.0-gac mono-gac
  mono-runtime mono-runtime-common mono-runtime-sgen pinta
0 upgraded, 31 newly installed, 0 to remove and 0 not upgraded.
Inst cli-common (0.9+nmu1 Ubuntu:15.10/wily [all])
Inst libgdiplus (3.6-1 Ubuntu:15.10/wily [amd64])
Inst libmono-system-xml4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst libmono-system-security4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst libmono-system-configuration4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst libmono-system4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst libmono-security4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst mono-4.0-gac (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst mono-gac (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst mono-runtime-common (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [amd64]) []
Inst mono-runtime-sgen (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [amd64]) []
Inst mono-runtime (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [amd64]) []
Inst libmono-corlib4.5-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libglib2.0-cil (2.12.10-5.1 Ubuntu:15.10/wily [amd64])
Inst libmono-cairo4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-system-drawing4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libgtk2.0-cil (2.12.10-5.1 Ubuntu:15.10/wily [amd64])
Inst libmono-corlib4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-sharpzip4.84-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-posix4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-system-core4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-addins0.2-cil (1.0+git20130406.adcd75b-3 Ubuntu:15.10/wily [all])
Inst libmono-addins-gui0.2-cil (1.0+git20130406.adcd75b-3 Ubuntu:15.10/wily [all])
Inst libmono-corlib2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-i18n-west2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-i18n4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-i18n-west4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst libmono-security2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst libmono-system2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all]) []
Inst libmono-posix2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Inst pinta (1.6-1 Ubuntu:15.10/wily [all])
Conf cli-common (0.9+nmu1 Ubuntu:15.10/wily [all])
Conf libgdiplus (3.6-1 Ubuntu:15.10/wily [amd64])
Conf libmono-system-xml4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-system-configuration4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-system4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-security4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf mono-4.0-gac (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf mono-gac (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf mono-runtime-common (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [amd64])
Conf mono-runtime-sgen (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [amd64])
Conf mono-runtime (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [amd64])
Conf libmono-corlib4.5-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-system-security4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libglib2.0-cil (2.12.10-5.1 Ubuntu:15.10/wily [amd64])
Conf libmono-cairo4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-system-drawing4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libgtk2.0-cil (2.12.10-5.1 Ubuntu:15.10/wily [amd64])
Conf libmono-corlib4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-sharpzip4.84-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-posix4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-system-core4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-addins0.2-cil (1.0+git20130406.adcd75b-3 Ubuntu:15.10/wily [all])
Conf libmono-addins-gui0.2-cil (1.0+git20130406.adcd75b-3 Ubuntu:15.10/wily [all])
Conf libmono-corlib2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-i18n-west2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-i18n4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-i18n-west4.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-security2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-system2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf libmono-posix2.0-cil (3.2.8+dfsg-4ubuntu4 Ubuntu:15.10/wily [all])
Conf pinta (1.6-1 Ubuntu:15.10/wily [all])
```

---

### Post by BluTiger on 2016-01-31
> **vasa1 said:**
> Thanks for letting people help you. Yawn, scratch, whatever ...


I hope that came across as a joke! I really only yawned and went to make a pot of coffee.:| lol.

> **Dennis N said:**
> I don't have mono installed in Ubuntu, it is installed in Manjaro (as a dependency of steam-manjaro). That is where I installed Pinta, so I get a free ride.

I was unaware mono is no longer in Ubuntu's repositories. That makes it a bit harder to install Pinta. Too bad.

No response yet on what the OP actually did.

I'm still researching...I don't want to be installing all sorts of repositories via command line until I got a good handle on what I'm doing and feel comfortable doing it. ;)

---

### Post by Dennis N on 2016-01-31
> **BluTiger said:**
> I'm still researching...I don't want to be installing all sorts of repositories via command line until I got a good handle on what I'm doing and feel comfortable doing it. ;)

A wise course of action. 

(F.W.I.W., My personal choice on Xubuntu is the screenshot panel plugin set to open in a graphics editor.)

---

