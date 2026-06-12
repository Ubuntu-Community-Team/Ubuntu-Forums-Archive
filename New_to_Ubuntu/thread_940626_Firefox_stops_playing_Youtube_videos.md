---
title: "Firefox stops playing Youtube videos"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Vorlander on 2008-10-07
Thats occurs frequently.

Youtube videos plays Ok, but when FIrefox took some time opened, then YOutube does not play at all.
I just see a grey screen ehere the video must be and nothing happens.

The only solutions is Close/Open firefox again. to fix the situation, until next time

What can it be ??

---

### Post by philinux on 2008-10-07
It's a bug in flash. Hopefully the new version 10 will fix it.

---

### Post by bwang on 2008-10-07
You can get version 10:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
tar -zxvf flashplayer10_install_linux_091508.tar.gz
cd install_flash_player_10_linux/
./flashplayer-installer
```

If you don't like to use the Terminal, or if the first command doesn't work, then go to [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and follow the instructions to download the tar.gz installer file. Extract the archive, and double click flashplayer-installer. Select Run in Terminal from the dialog box that pops up.

---

### Post by Vorlander on 2008-10-07
> **bwang said:**
> You can get version 10:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
tar -zxvf flashplayer10_install_linux_091508.tar.gz
cd install_flash_player_10_linux/
./flashplayer-installer
```

If you don't like to use the Terminal, or if the first command doesn't work, then go to [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and follow the instructions to download the tar.gz installer file. Extract the archive, and double click flashplayer-installer. Select Run in Terminal from the dialog box that pops up.

Holy ****.
I forgot to mention I'm Hardy 64bits (AMD64x2)

When I try ./flashplayer-installer it gives me worng arch :(

---

### Post by philinux on 2008-10-07
2 ways.

[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html) Scroll to the bottom for a script.

Or.

Big discussion here.
[http://ubuntuforums.org/showthread.php?t=890760&highlight=flash+10](http://ubuntuforums.org/showthread.php?t=890760&highlight=flash+10)

---

### Post by Vorlander on 2008-10-07
> **philinux said:**
> 2 ways.

[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html) Scroll to the bottom for a script.

Or.

Big discussion here.
[http://ubuntuforums.org/showthread.php?t=890760&highlight=flash+10](http://ubuntuforums.org/showthread.php?t=890760&highlight=flash+10)


I tried the script and does not work.

This the output fo Terminal :

> 
Installing Flash Player 10
--18:40:17--  [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz)
           => `flashplayer10_install_linux_081108.tar.gz.2'
Resolviendo download.macromedia.com... 88.221.163.191
Conectando a download.macromedia.com|88.221.163.191|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 4,035,433 (3.8M) [application/x-gzip]

100%[====================================>] 4,035,433    897.69K/s    ETA 00:00

18:40:22 (854.95 KB/s) - `flashplayer10_install_linux_081108.tar.gz.2' guardado [4035433/4035433]

install_flash_player_10_linux/
install_flash_player_10_linux/libflashplayer.so
install_flash_player_10_linux/flashplayer-installer
*** NSPlugin Viewer  *** ERROR: libcurl.so.3: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so
Linking the libraries so Firefox can find it.
Done :-)


Seems to finish ok, but when I go to youtube they say I don't have any flashPlayer or Java installed.

Before this script I had flash-plugin-nonfree, and it works (with the mentioned error, but I could see the clips)

---

### Post by philinux on 2008-10-07
Yep same here.

Download and install getlibs first.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Then run the script again.
I used this script and it works.
[http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/](http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/)
Full screen flash is much smoother.

---

### Post by Vorlander on 2008-10-08
> **philinux said:**
> Yep same here.

Download and install getlibs first.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Then run the script again.
I used this script and it works.
[http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/](http://meandubuntu.wordpress.com/2008/08/20/flash-10-rc-on-ubuntu-amd64/)
Full screen flash is much smoother.

Thanks.

It's working now

---

