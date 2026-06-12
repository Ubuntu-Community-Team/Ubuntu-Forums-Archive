---
title: "No adobe flash after update"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by Ben_222 on 2012-04-13
Hi,I marked an earlier thread as solved about Flash because I have to use Google Chrome to get flash.Isn't there a way to get Flash after the bad update for flash for Firefox?Tried Gnash, but is didn't work. I have tried all the methods,except for reverting back to the previous version.What I can't understand is why are there so few threads about this.Is it the version of Firefox that matters,and many people have an older Firefox that flash works in? Also, in youtube,HTML5 is used in very little of their videos ,as far as I can tell.

---

### Post by NikTh on 2012-04-13
Hi ,
i think its the version of flash combined with graphics card that creates the problem . Is you card nvidia ? 
Did you try flash-aid for Firefox ? Its add-on. Here --> [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) . 
Install it and then install flash - beta.

---

### Post by Ben_222 on 2012-04-13
Ok, I just tried FlashAid again and chose beta,but it did not work.I have this older pc that I play a few online games on and surf the net a bit.It has an Nvidia 6600 card.a fairly fast card for AGP.What's weird is that I have another pc with WinXP about the same age and it has an Nvidia 6200,and flash works on it! The other day I tried installing Mint on an extra hard drive, thinking maybe flash would work on it(came to find out Mint comes with flash),but when I downloaded the video driver, it would not reboot....anyway,thanks for your response...oh,I'm running Ubuntu 10.04,mainly cause of the longer updates,and I dont like Unity

---

### Post by anewguy on 2012-04-13
You're not alone.  I've had problems with flash in Firefox and any of the other browsers I have tried since version 11.04 first came out.  Some times it just plain aborts.  Other times it spins and spins and then tells me the video has expired, only to turn around and have the video play behind that text.

NOTHING has helped it - clean installs of the OS, flash-aid, different versions of flash, clean installs of the OS and never install flash and instead use the open flash player.  NOTHING has helped - 32 or 64 bit.  Somewhere in the forum I believe I still have an open thread about this because I still have such problems with it.  Don't know why.  Don't know how or when whatever is responsible - the player, the browser, linux or even just the website playing the video.  All I know is the dang thing doesn't work and I'm pretty tired of not being able to play flash videos for the most part.  It's one of the reasons I still have Windows around to boot into.

Best of luck!

Dave ;)

---

### Post by NikTh on 2012-04-13
> **Ben_222 said:**
> oh,I'm running Ubuntu 10.04,mainly cause of the longer updates,and I dont like Unity
Hi,
If you don't like Unity you have so many other options. Gnome-shell , gnome-classic-fall back , cinnamon , mate , lxde , etc. 

Did you try to start Firefox without extensions ? . Just write to terminal ```
firefox -safe-mode
``` and look if works.

---

### Post by Ben_222 on 2012-04-14
No luck.Still no flash after starting Firefox with no extensions....

---

### Post by Curtis6767 on 2012-04-14
Open a new tab in Firefox and in the address bar enter about:plugins. That's about plugins. Replace the smiley face with :

look through and see if you have anything under Shockwave Flash or if you have Shockwave Flash at all.

---

### Post by Shadius on 2012-04-14
The problem is with the new Flash version. In order to fix it, I had to downgrade to get it to work. Adobe has stopped support for Flash on Linux so there won't be a fix for it, so I've read. This thread explains how to fix the issue. 

[http://ubuntuforums.org/showthread.php?t=1949107]("http://ubuntuforums.org/showthread.php?t=1949107")

Hope that helps.

---

### Post by NikTh on 2012-04-14
> **Shadius said:**
> so there won't be a fix for it, so I've read. 

Adobe announced that will continue send security updates (maybe bug fixes too?) for 5 years. 

> Adobe will continue to provide security updates to non-Pepper  distributions of Flash Player 11.2 on Linux for five years from its  release.

[http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

---

### Post by Shadius on 2012-04-14
> **NikTh said:**
> Adobe announced that will continue send security updates (maybe bug fixes too?) for 5 years. 



[http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html](http://blogs.adobe.com/flashplayer/2012/02/adobe-and-google-partnering-for-flash-player-on-linux.html)

Thank you for this! Hopefully, they'll fix this bug.

---

### Post by anewguy on 2012-04-14
Just so everyone knows:  As I mentioned in my previous post I have had flash problems since 11.04.  Well, today I was running Windows 7 and Internet Explorer 9, and guess what?  The SAME problem.  So it is definitely flash itself.  I'll have to try downgrading flash to see if I can get it working as well.

Thanks for the info in this thread.

Dave ;)

---

### Post by ajgreeny on 2012-04-14
I have just downloaded the flash tar.gz  11.2.202.233 from adobe and  extracted the libflashplayer.so from it.  I then copied this new version  to replace the 11.1r102 which had been the last that worked on my  machines, and much to my surprise it worked with no problems.

The 11.2.202.228 previously available had not worked at all in my  systems.  This must also be worth a look-see by those who have the  "smurf effect" from version 11.2.202.228.

Were Adobe shamed into doing something to overcome the problem after all?

---

### Post by Shadius on 2012-04-14
> **anewguy said:**
> Just so everyone knows:  As I mentioned in my previous post I have had flash problems since 11.04.  Well, today I was running Windows 7 and Internet Explorer 9, and guess what?  The SAME problem.  So it is definitely flash itself.  I'll have to try downgrading flash to see if I can get it working as well.

Thanks for the info in this thread.

Dave ;)

I was just testing it out to see if my Windows had gotten this bug too, but everything seems to be working fine. However, I tested it out on Chrome & Firefox. Both work.

---

### Post by Shadius on 2012-04-14
> **ajgreeny said:**
> I have just downloaded the flash tar.gz  11.2.202.233 from adobe and  extracted the libflashplayer.so from it.  I then copied this new version  to replace the 11.1r102 which had been the last that worked on my  machines, and much to my surprise it worked with no problems.

The 11.2.202.228 previously available had not worked at all in my  systems.  This must also be worth a look-see by those who have the  "smurf effect" from version 11.2.202.228.

Were Adobe shamed into doing something to overcome the problem after all?

It seems that Adobe has fixed it...?

---

### Post by Ben_222 on 2012-04-14
I typed in about:plugins in the browser, and yes, I do have installed Shockwave Flash 11.2 r202.   Guess I may try the downgrades thing...Better yet, hope adobe will fix this bug soon

---

### Post by Autodave on 2012-04-14
> **Ben_222 said:**
> I typed in about:plugins in the browser, and yes, I do have installed Shockwave Flash 11.2 r202.   Guess I may try the downgrades thing...Better yet, hope adobe will fix this bug soon


I uninstalled Adobe and then went to YOUTUBE and clicked on a video.  It told me that I was missing a plug-in and gave me the option of installing Adobe or Gnash.  I installed Gnash and all is well again.

---

### Post by NikTh on 2012-04-15
> **ajgreeny said:**
> I have just downloaded the flash tar.gz  11.2.202.233 from adobe and  extracted the libflashplayer.so from it.  I then copied this new version  to replace the 11.1r102 which had been the last that worked on my  machines, and much to my surprise it worked with no problems.

The 11.2.202.228 previously available had not worked at all in my  systems.  This must also be worth a look-see by those who have the  "smurf effect" from version 11.2.202.228.



Very Good thinking !! :)

---

### Post by bcschmerker on 2012-04-16
The discontinuance on LinUX of Adobe® Flash™ after 11.2.202.233 could be problematic to some Users.  A number of user-music and -video Websites (e.g., [UStream® Television]("http://www.ustream.tv/"), [SingSnap® Karaoke]("http://www.singsnap.com/")) still need an Adobe® shockwave/flash technology, as W3C Hypertext Markup Language 5 is not a one-for-one replacement for the proprietary Macromedia® software architecture still supported by Adobe Systems for Microsoft® Windows® 6-up and Apple® MacOS X® 10.4-up.

I found that Gnash™ does not support upstream commands supported in Flash™, and have yet to test Pepper™.

---

### Post by Curtis6767 on 2012-04-16
This article says that Flash or Pepper will be available with Chrome but does not mention Chromium. No more support from FireFox, which I find interesting.

[http://www.h-online.com/open/news/item/Chrome-only-future-for-Flash-on-Linux-1440104.html](http://www.h-online.com/open/news/item/Chrome-only-future-for-Flash-on-Linux-1440104.html)

---

### Post by nico23 on 2012-04-18
this is fzuckign annying, my flash updated Kubuntu 12.04 now its stopped working, i keep the error that it could not download one sources list. then a windows appears wich is like 6000 pixels wide and contains text in all languages.

bad decision to go beta, i taught its pretty stable because it will be releases soon. 

and now i read this crap that adobe is planning to release flash only inside crome WTF?

******* google spyware, and now they baught off adobe and made a crap deal to get more people to use googles **** browser? i hate google and adobe.

```
Achtung: „gksudo“ kann nicht gefunden werden, stattdessen wird „/bin/bash“ gestartet. Prüfen Sie bitte die Einstellungen des Profils.

/usr/lib/update-notifier/package-data-downloader: Zeile 3: Process new requests to download per-package data: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 19: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 20: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 21: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 22: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 23: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 24: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 25: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 26: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 27: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 28: import: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 29: import: Kommando nicht gefunden.
from: can't read /var/mail/datetime
/usr/lib/update-notifier/package-data-downloader: Zeile 32: DATADIR: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 33: STAMPDIR: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 34: NOTIFIER_SOURCE_FILE: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 35: NOTIFIER_FILE: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 36: NOTIFIER_PERMANENT_SOURCE_FILE: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 37: NOTIFIER_PERMANENT_FILE: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 39: failures: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 40: permanent_failures: Kommando nicht gefunden.
/usr/lib/update-notifier/package-data-downloader: Zeile 42: Syntaxfehler beim unerwarteten Wort `('
/usr/lib/update-notifier/package-data-downloader: Zeile 42: `def create_or_update_stampfile(file):'
```

---

### Post by bpb101 on 2012-04-19
unfortually i think the time has come , as support for flash is gone we have to downgrade to google chrome as they are supporting it now

everything works fine for me now

---

### Post by bcschmerker on 2012-06-11
Adobe Systems has patched some earlier versions of Flash&#8482; Player for systems unable to run Version 11.3 r300 (which is RTM for Microsoft® Windows® and Apple® Mac OS® X&#8482;, as of 10 June 2012).  When using Mozilla® Firefox®, one extension that will be needed is [Flash-Aid&#8482;](https://addons.mozilla.org/en-US/addon/flash-aid/), which has a Custom install option satisfactory for Flash&#8482; Player LinUX GZip TAr's available from Adobe®.  Due to known issues with Flash&#8482; Player 11.2 r202 that are WONTFIXes for LinUX in general (Adobe® having discontinued Flash&#8482; Player for LinUX at 11.2), I recommend using Flash-Aid's&#8482; "Custom (http url or local path)" option to install [LibFlashPlayer.so Version 10.3 r183](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz) from the Macromedia® Flash Player Download site to your User Program library subdirectory /usr/lib/mozilla-addons/plugins:
```
http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_10_linux.tar.gz
```
Be advised that this only works with 32-bit, or i386, installations; as of June 2012, Ubuntu® AMD64 Editions have an unresolved problem with the 32-bit plugin wrapper.

---

