---
title: "Flash not working in firefox 23"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by john_smith2 on 2013-08-18
I have firefox 23 ubuntu studio 12.04 64 bit. Flash is working properly on chrome but not on firefox.

---

### Post by zeljkojagust on 2013-08-18
Flash works in Chrome because it is embedded in browser. To make it work in Firefox, you need to install flashplugin-installer package. Just execute the following in your console:

sudo apt-get install flashplugin-installer

Just press Enter to all questions asked by installer, and you should be good.

---

### Post by jeffroaltiere1 on 2013-08-18
Have you tried getting Ubuntu Restricted Extra's from the Ubuntu Software Center? That comes loaded with Flash in it. It will install it along with java and other useful media codecs that come in handy for playing DVD's.

From the terminal: sudo apt-get install ubuntu-restricted-extras

---

### Post by john_smith2 on 2013-08-19
john@john-Aspire-5742:~$ locate libflashplayer.so
/home/john/Downloads/libflashplayer.so
/home/john/Downloads/install_flash_player_11_linux.x86_64/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

Tried this [http://support.mozilla.org/en-US/questions/964567](http://support.mozilla.org/en-US/questions/964567)

---

### Post by john_smith2 on 2013-08-21
Bump

---

### Post by d2btoo on 2013-08-21
I would check **[COLOR=darkred][noparse]about:plugins[/noparse][/COLOR]** page!

---

