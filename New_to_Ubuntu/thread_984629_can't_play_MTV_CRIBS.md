---
title: "can't play MTV CRIBS"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by wenhui100 on 2008-11-16
HI i have already installed the latest flash 10 in ubuntu firefox plugins ..but still can't stream MTV CRIBS .. other sites like metacafe works like charm ... oh by the way I am using ubuntu 8.10 64bit.

I followed the instructions from this site:
[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

Any help is appreciated thanks

---

### Post by wenhui100 on 2008-11-16
oh sorry I forgot the include the URL of MTV CRIBS

[http://www.mtv.com/ontv/dyn/cribs/series.jhtml](http://www.mtv.com/ontv/dyn/cribs/series.jhtml)

---

### Post by Crafty Kisses on 2008-11-16
Works fine for me, did you install this package?
```
sudo apt-get install ubuntu-restricted-extras
```
Try installing that if you haven't already, and go into Firefox and type this in the address bar:
```
about:plugins
```
See what it says for Flash.

---

### Post by wenhui100 on 2008-11-16
Thanks for ur speed reply ... attached below are my plugins


Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.24.3

---

### Post by wenhui100 on 2008-11-17
i have tried the extra command that u have posted .... still nothing ...

---

### Post by fooman on 2008-11-17
i tried yesterday with the flashplugin-nonfree from synaptic and could not view those crib vids (using 64bit intrepid).

today (nov.17),  adobe released a 64bit flash player and now the crib vids play without a problem!  :)

first, uninstall the synaptic version (flashplugin-nonfree) if it is installed.  
download the 64 bit-plugin from here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

extract the file and copy "libflashplayer.so" to the ~/.mozilla/plugins folder.  create the "/plugins" folder if it does not exist already.

enjoy

---

### Post by kernelhaxor on 2008-11-17
> **fooman said:**
> i tried yesterday with the flashplugin-nonfree from synaptic and could not view those crib vids (using 64bit intrepid).

today (nov.17),  adobe released a 64bit flash player and now the crib vids play without a problem!  :)

first, uninstall the synaptic version (flashplugin-nonfree) if it is installed.  
download the 64 bit-plugin from here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

extract the file and copy "libflashplayer.so" to the ~/.mozilla/plugins folder.  create the "/plugins" folder if it does not exist already.

enjoy

Good for you .. Looks like Adobe released just in time for you ..

Many 64-bit Linux users have been waiting for this release for years and years

---

