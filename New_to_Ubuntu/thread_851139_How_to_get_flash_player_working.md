---
title: "How to get flash player working?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-06
I can not seem to be able to get flash player working in firefox...

---

### Post by nothingspecial on 2008-07-06
In terminal

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by rraj.be on 2008-07-06
```
[http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")
```

Just follow what is given above.

It should solve your problem.

---

### Post by pikabuntu on 2008-07-06
i got this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  blt tcl8.4 tk8.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by nothingspecial on 2008-07-06
Try following this guide, especially "part 1/5 Essential Packages"

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by pikabuntu on 2008-07-06
Whenever i go to a page with flash content, firefox does not have the addons popup.  It used to, and i tried to install flash player that way, but it always said that it could not be installed.  I just tried downloading the .tar.gz of flash player, extracting it, and running flash-player installer in the terminal.  It seems to work fine until:

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

*******i entered: /usr/lib/mozilla

WARNING: Please enter a valid installation path.

---

### Post by rraj.be on 2008-07-06
what happened when you tried what's in the link given by me?

---

### Post by pikabuntu on 2008-07-06
> **rraj.be said:**
> what happened when you tried what's in the link given by me?

read post above :)

---

### Post by BLTicklemonster on 2008-07-07
[http://www.readatwork.com/](http://www.readatwork.com/)

Can't view this site.

Nothing I've tried here or anywhere else works. I see no yellow bar at the top of the screen, either.

Ubuntu 64.

---

### Post by aktiwers on 2008-07-07
That site works great here.

Virtual XP OS :)

I have flash 9 installed from adobes website. But I have seen some real good reactions to Flash 10 Beta, so I would go for that.

---

### Post by BLTicklemonster on 2008-07-07
After not getting anything working, I went to youtube and it showed the yellow bar, so I installed flash, and bam, youtube works and the above site work.

Freking strange.

---

### Post by BLTicklemonster on 2008-07-07
Lmao. I had clicked on a youtube video to make sure I was telling the truth when I posted that. Haven't rebooted or anything since, and now when I go to youtube the video area is just a blank gray box. No "no script" warning, no "install flash", no nothing. It just stopped working since I posted that.


Argh.

---

### Post by aktiwers on 2008-07-07
Have you tried this?
[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

I installed flash on my friends 64bit Ubuntu, and cant remember exactly what I did. But after reading that link, I am pretty sure this is the way to go :) Though I installed flash 9 on his PC. But I read a lot good about flash 10

---

### Post by BLTicklemonster on 2008-07-07
Closed Firefox, went shopping, came back and it works again.

Huh.

---

### Post by brel on 2008-07-07
I've been having problems on windows as well with firefox 3 and flash. If I restart firefox it works for a while but then I start getting grey boxes instead of youtube videos. I'm going to check the firefox forums to see if there is anything there.

Flash works fine in konquerer so it's more than likely a firefox issue. My current workaround is to cut and paste into konquerer whenever I want to see some flash.

---

### Post by Footer on 2008-07-07
> **aktiwers said:**
> Have you tried this?
[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

I installed flash on my friends 64bit Ubuntu, and cant remember exactly what I did. But after reading that link, I am pretty sure this is the way to go :) Though I installed flash 9 on his PC. But I read a lot good about flash 10

I just tried installing Flash 10 beta and it didn't work because of my 64bit architecture (Kubuntu 8.10 64bit).  Does anyone know if there is a Flash 10 beta for 64bit Linux?

This is getting annoying!  Also would be nice to be able to just restart npviewer.bin instead of the whole browser (I have three windows and dozens of tabs in each) to get Flash working again.  Seems to work for awhile and then craps out, only fix I know is to restart the browser.

Thanks!

Edit:  DUH!  Just went to that link, will try install when I get a chance.

Edit 2:  OK, call me old fashioned but I took a closer look at that link and it's using nspluginwrapper.  I believe this is more or less a 32bit workaround which I'm not really interested in.  I guess if it's stable and works, I'd be willing to give it a try but I'd rather stay with a 64bit version if available.  Appreciate any opinions!

---

