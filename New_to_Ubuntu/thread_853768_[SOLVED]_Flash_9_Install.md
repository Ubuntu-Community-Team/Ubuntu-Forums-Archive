---
title: "[SOLVED] Flash 9 Install"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by llloyd on 2008-07-08
I'm a little stuck here... I downloaded the install tar.gz for Flash 9, ungzipped it, untarred it, and running into an impass. Help? O.o Ok... Let me see...

llloyd@Kenya:~/install_flash_player_9_linux$ sudo sh flashplayer-installer

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
or Opera browser (i.e., /usr/lib/mozilla): /usr/bin/firefox

WARNING: /usr/bin/firefox is not a directory.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/bin        

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/share/

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

All aquired from a "whereis firefox' and 'whereis mozilla' ... I have *no* idea what directory it wants. :P Help? Thanks!

L. Lloyd

Firefox was installed with Xubuntu 8.04 so I never downloaded or ran anything to get it.

---

### Post by ibuclaw on 2008-07-08
```
whereis firefox
```
Should give you the answer **/usr/lib/firefox**

And besides, flash is in the repositories, no need to manually install it ;)

```
sudo apt-get install flashplugin-nonfree
```

Regards
Iain

---

### Post by uniquegeek on 2008-09-13
I had the same problem.  At one point, I had installed several flash players via Symantic or Adept, until learning I should only install *flashplayer-nonfree*.  I removed the other ones, but still no go.  I tried downloading the package from Adobe manually, and installing via the command line, but got the error as above.

Here are the tricks:
- it seems the Adobe installer wants the actual numbered version of the directory.  "*whereis firefox*" didn't help me in this respect.  I ended up using */usr/lib/firefox-3.0.1*  Yours might be slightly different.
- when testing out whether flash works on something like YouTube, make sure you don't have something like the "NoScript" add-on preventing anything you may need.  (D'oh!)  I had to allow both *youtube.com* and *ytimg.com* in NoScript.

... that brings up the question whether flash was actually working all along and my NoScript was thwarting all my efforts.  Oh, probably.

---

