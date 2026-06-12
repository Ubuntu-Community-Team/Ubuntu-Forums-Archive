---
title: "[SOLVED] Install/Remove LimeWire"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-28
I was reading a LimeWire forum for Ubuntu users & found there are a lot of people having the same issues. I was not able to exit the program without shutting down the computer. I removed LimeWire using the following commands. (For anyone interested).
-------------------------------------------------------------------------
Re: remove limewire 

Quote:
[COLOR="Blue"]sudo aptitude remove limewire[/COLOR] 
should work. Alternatively you can go to s[COLOR="Blue"]ynaptic and type limewire[/COLOR] into the search function. There you should be able to choose 'remove' or 'completely remove'

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
see: [COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=810049[/COLOR]
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
To get rid of a file owned by root, you'll need to use sudo.

Navigate to the directory that runLime.sh_limewire is in - from what you've posted it looks like 
Code:
[COLOR="Blue"]cd /usr/share/ubuntu-docs/ubuntu/sample[/COLOR]
and then use 
Code:
[COLOR="Blue"]sudo rm -fv runLime.sh_limewire
[/COLOR]

This worked great for me. (Thanks to All who contributed). 

I was hoping that once I removed the program that perhaps by re-installing it might get rid of closing/exiting issue. However, now I'm not able to re-install LimeWire. 
Any Ideas ?... Or perhaps someone knows of a more (Ubuntu) user friendly product?

---

### Post by forestpixie on 2008-05-28
I use ktorrent , there is bittorrent, deluge, transmission and probably more. There is also frostwire which is like limewire apparently. Utorretnt works well with wine, there is also azureus.

Quite alot to choose from

---

### Post by CoCoKnots on 2008-05-28
Great, Thanks... How do I know which ones are 'wine' oriented & those which are Ubuntu/Linux?

---

### Post by forestpixie on 2008-05-28
If it runs with an .exe you'll need wine - the first 4 are gnome except ktorrent which is kde  - it runs in gnome but adds a bunch of libraries - I use it and am happy.

Frostwire you can get as a .deb - that's for debian based like Ubuntu. Azureus just runs I think - so on my list it's utorrent.

You have asked one of those questions here - there have been loads of 'which torrent' threads here :)

---

