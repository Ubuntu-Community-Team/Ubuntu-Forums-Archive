---
title: "[SOLVED] opera and flash player has anyone got it to work yet"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-05-30
hi i have spent hundreds of hours trying to get the flash player to work with opera browser < have not tried for about a month < wondered if anyone had actualy managed it yet i am using opera 9.27 ,i dont want to use 9.5 AS IT CAUSED ALL SORTS OF PROBLEMS LAST TIME I TRIED IT .
PLEASE ONLY REPLY IF YOU HAVE MANAGED TO ACTUALY GET IT TO WORK OR REALY DO KNOW WHAT YOU ARE TALKING ABOUT AS I AM NOT PREPARED TO SPEND STUPID AMOUNTS OF TIME ON THIS ANYMORE. 
I WOULD REALY LIKE TO GET IT WORKING ANY HELP FROM SOMEONE WHO HAS DONE IT WOULD BE VERY MUCH APPRECIATED. tHANKS ANDREW:confused:

---

### Post by sayakb on 2008-05-30
Install the ubuntu-restricted-modules ; all gstreamer plugins and the Gnash swf viewer/player.

---

### Post by Mentem on 2008-05-30
I'd stay away from gnash. I had trouble with running flash until I removed it. It doesn't seem to support flash too well, yet.

---

### Post by workshop1702 on 2008-06-10
still no flash player with opera , surley someone out there must have don this please please will somoene help

---

### Post by fbnaia on 2008-06-10
I am using flash with opera 9.50 Beta 2, i wasnt able to get it to work with the non-beta version...

you can download that one here [http://www.opera.com/download/?ver=9.50b2]("http://www.opera.com/download/?ver=9.50b2")

---

### Post by elgalloloco on 2008-06-10
Make sure u have Flash installed.

Open Synaptic, search for "flashplugin-nonfree", and install it.

Then open Opera -> Tools -> Preferences -> Advanced (TAB) -> Content (Left Panel) -> Plug-in Options (Button on the Right) and make sure your paths are pointing to the correct path. 

Heres how I got it configured on mine.

Hope it helps!

---

### Post by workshop1702 on 2008-06-10
have tried all this still no luck also tried the beta version but this caused so many problems i had to remove it . andrew

---

### Post by markbuntu on 2008-06-10
Flash 9 in the repos does not work with Opera 9.27 period. It will work with Opera9.5beta, at least the newer versions. 

You need an older version of flash to work with 9.27 that you can get from the flash website where older versions are kept. You can download it to your desktop or wherever and unpack it but do not run the installer. Instead copy the libflash.so to your /usr/lib/opera/plugins file and then go to /usr/share/opera/ini and edit the pluginpath.ini to change the path for Flash. You may also have to change the path in the plugin search in the preferences in the browser.

That's what I did when firefox3b5 was driving me crazy and it worked for me. Opera9.27 would play flash but was almost as bad as firefox so I gave up and went to firefox3rc1 and that is much more stable.

This way when you upgrade to Opera9.5 all you have to do is delete the libflash.so and the upgrade will do the rest. And it isolates the older flash from being found by any other browser you might be using.

I did this a few months ago so my memory about it is kinda sketchy but that is basically what you need to do.

---

### Post by i_love_AMY_MACDONALD on 2008-06-11
> **workshop1702 said:**
> have tried all this still no luck also tried the beta version but this caused so many problems i had to remove it . andrew
i usually download all flash videos, since i can watch them again and also share them with my friends!! i use _keepvid.com_

---

### Post by Daveth on 2008-06-11
I find 9.5 beta2 build 1933 works with flash, with /usr/lib/mozilla/plugins/flashplugin-alternative.so.

Beta is still a bit of a pain as it still fails to render some graphics on some pages, but i love Opera so much I can put up with it. 9.26 was rubbish, and i found 9.27 a bit better, but the newer beta builds are getting there. I just wish opera wouild speed up to the final version.

---

### Post by workshop1702 on 2008-06-12
have tried opera 9.5 again works great with flash player but have new problem now the opera fit to width function isnt working.anyone any ideas please how to fix this.:)

---

### Post by workshop1702 on 2008-06-12
hi is the beta 2 the newest version , i have beta 1 . cannot find a download of beta 2 ,the flash player is working ok but have other problems with it main one bieng the fit to width does not work with a lot of pages especialy ebay which i use a lot.thanks for the help . Andrew

---

### Post by Daveth on 2008-06-13
if you fancy the bleeding edge of Opera.....

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

