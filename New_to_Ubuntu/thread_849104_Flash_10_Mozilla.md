---
title: "Flash 10 Mozilla"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mevets on 2008-07-04
Adobe recently release version 10 of their Flash player. I was wondering if anyone knew the path it should be installed to because the default one (/usr/lib/mozilla) does not work. Does anyone know what it should be?

---

### Post by TenPlus1 on 2008-07-04
Uninstall flashplayer-nonfree from the repo's then run the installer provided in the flash10 package, it'll work... (dont chose a directory, just press enter and let it install itself)...

btw: it works well but still has bugs on some flash movies...

---

### Post by silkstone on 2008-07-04
I followed the guide by reassuringlyoffensive which is posted here...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

-------------

UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY

Note: You can safely install the Ubuntu package (flashplugin-nonfree) over the top of this manual installation method at a later date, I've tested it several times. The method used below will install the plugin into the same directory the Ubuntu package does, with the same symlinks and can be overwritten cleanly.

Install the Flash plugin manually by downloading the tar archive of Adobe Flash v10 beta. Simply open the tar archive, then find the file named "libflashplayer.so" and place it on your desktop. Next, execute this command in the terminal:

32-Bit Ubuntu Family Users Only:

sudo apt-get purge flashplugin-nonfree && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart Firefox and use the plugin.

-------------

I also deleted libflashsupport from Synaptic, and also deleted pluginreg.dat which is in .mozilla/firefox/xxxxx/ (this is recreated automatically when Firefox restarts).

---

### Post by mevets on 2008-07-04
I found out the problem was that I was running the script with sudo. I did this because it told me it would install system wide.

If you run the script w/ sudo and just press enter at the point it prompts for a path it will NOT correctly guess the path to install it to. But, if you install it w/o sudo it will install it to /home/[username]/.mozilla

---

