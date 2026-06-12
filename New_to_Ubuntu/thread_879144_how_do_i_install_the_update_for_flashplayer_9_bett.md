---
title: "how do i install the update for flashplayer 9 betta 2?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by oneouncebrick on 2008-08-03
i have installed flashplayer for my computer (xubuntu hardy heron) and now youtube sound will not work. but goole video does, i know they are both flash based tho O.o i searched this problem on the forums and i was not the only one, however, i then found that many people fixed the problem by installing the update for flash player (heres the link to the thread i found this out on(page 2) [http://ubuntuforums.org/showthread.php?t=296590&page=2](http://ubuntuforums.org/showthread.php?t=296590&page=2) <-- this will show you the link to the update page for flashplayer.. please give step by step instructions on how i can install this update! :confused:

---

### Post by Liolikas on 2008-08-03
I think you can do it in same way as on windows just:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveflash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveflash)
Download ant install.

---

### Post by billgoldberg on 2008-08-03
Start by removing flash 9.

I just removed the file in /home/.mozilla/plugin

```
cd /tmp
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

*from my blog*

---

