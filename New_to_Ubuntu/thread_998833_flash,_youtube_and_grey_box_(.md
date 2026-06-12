---
title: "flash, youtube and grey box :("
date: 2008-12-01
forum: New to Ubuntu
---

### Post by tomcheng76 on 2008-12-01
While playing of the video from youtube, i pressed hyperlink from the sidebar. Grey box is shown in the youtube where the video should be played from there. Problem exists until reopening firefox3.

Using Ubuntu 8.10 AMD64
latest Firefox3 and flashplugin-nonfree
tried this already:
```

sudo update-alternatives --auto xulrunner-addons-flashplugin

```

Please help me.

---

### Post by hellion0 on 2008-12-01
There's an alpha for Linux 64-bit Flash on Adobe's site. Although it's an alpha, it's been known to work well so far, from the people here who've tried it. It could fix the problem.

I think you can grab the new alpha by going [here](http://get.adobe.com/flashplayer/).

Other than that, someone who knows 64-bit better may be of more help (I'm a 32-bit girl.)

---

### Post by fr.theo on 2008-12-01
what Ubuntu environment do you have 8.04 Hardy 32/64 bit or 8.10 intrepid?

what version of fire fox do you have?

do you have flash player 10 installed, if not try this thread.

[http://ubuntuforums.org/showthread.php?t=954349](http://ubuntuforums.org/showthread.php?t=954349) 


be sure that you download it from adobe first in order to install it, don't worry it is a deb file so it should automatically install itself once you double click on it.

here is the download location: [http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

I use it and it works very well.

---

### Post by tomcheng76 on 2008-12-01
@hellion0: there is no deb for x86_64

@fr.theo: i already posted on the #1, it is a Ubuntu 8.10 Intrepid x86_64 with latest firefox3 (3.0.4+nobinonly-0ubuntu0.8.10.1)
flashplugin-nonfree (10.0.12.36ubuntu1)

Thanks in advance

---

### Post by fr.theo on 2008-12-01
sorry about that, however there is a 64 deb of flash player go to the link I posted on my earlier post and you will go to adobe from there you can select your OS " .deb for 8.04 ubuntu" it is 64 should work with intrepid as it is a 64 bit architecture.

---

### Post by Moop on 2008-12-01
I use the 64bit version of flash and it works much better. You can download it from here. [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

You will want to uninstall the old version of flash first. You can find installation instructions here. [http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

---

### Post by tomcheng76 on 2008-12-01
There really isn't any deb for 64bit...
It show ' Error: Wrong architecture '1386' ' in Package installer.
I affraid i can only install the .sh version and do the library linking myself for firefox...

---

### Post by tomcheng76 on 2008-12-01
@Moop: thanks for the link :)

---

### Post by fr.theo on 2008-12-01
I downloaded it my self and I have Ubutnu 8.04 64 LTS, it works for me, all I did is go to adobe site and download flash player 10, but make sure you select the OS.

---

### Post by tomcheng76 on 2008-12-01
@fr.theo: I really tried ".deb for 8.04 ubuntu", but it is 1386 :(

Anyway, i solved using "Download 64-bit Plugin for Linux (TAR.GZ, 3.54 MB)" from [here]("http://labs.adobe.com/downloads/flashplayer10.html") 
The lab 10.0.20.7 library work flawlessly on youtube :)
It works by doing this. Hope it helps others.
```

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

```

btw, how to register the libflashplayer.so using nspluginwrapper?

---

### Post by gandaran on 2008-12-01
> btw, how to register the libflashplayer.so using nspluginwrapper?
you don't have to, it' works just by installing the 64-bits flash, you have to uninstall/remove nspluginwrapper!

---

### Post by tomcheng76 on 2008-12-01
> **gandaran said:**
> you don't have to, it' works just by installing the 64-bits flash, you have to uninstall/remove nspluginwrapper!

okay, i uninstalled.
Thanks everyone who posted a reply here :)

---

