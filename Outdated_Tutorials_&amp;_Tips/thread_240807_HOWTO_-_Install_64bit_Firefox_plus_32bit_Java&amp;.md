---
title: "HOWTO - Install 64bit Firefox plus 32bit Java&amp;Flash plugins"
date: 2006-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Alexander_Corvinus on 2006-08-21
Why should i download 32bit Firefox to install Java and Flash when i can succesfully use 64bit firefox?
So:

1. Download Firefox:
[http://www.mozilla.com/products/download.html?product=firefox-1.5.0.6&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-1.5.0.6&os=linux&lang=en-US)

2. Untar it (i.e.: /home/firefox/ )

3. Download Flash player for linux:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz)

4. Untar it and copy from that folder the files: "flashplayer.xpt" and "libflashplayer.so" and paste them to the /firefox/plugins folder (make sure it's the firefox that you have downloaded and NOT the one installed on Ubuntu... it won't work!)

5. Check the following link to make sure it's working:
[http://www.joecartoon.com](http://www.joecartoon.com)

6. Go to:
[http://jdl.sun.com/webapps/download/AutoDL?BundleId=10635](http://jdl.sun.com/webapps/download/AutoDL?BundleId=10635) and download the JRE for Linux on 32bit

For the java part I can't take any credit since it's all Kilz's fault :mrgreen: 
Just kidding!
The following part it's taken from this tutorial:[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537) (Kilz has all the credit!)
I just modified the version of jre and firefox folder (PS: I LOVE YOU KILZ for that beautiful tutorial!)
Well here it is:

> Java
```
cd ~/Desktop
sudo bash
chmod 777 ./jre-1_5_0_08-linux-i586.bin ./jre-1_5_0_08-linux-i586.bin
```

You will have to agree to the EULA, then it will extract to your desktop.
We will now install it

```
mkdir /usr/local/java32
cp -r -p ./jre1.5.0_08/* /usr/local/java32 
cd /home/firefox/plugins/ 
ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./
```

Restart Firefox and go [http://www.wildsnake.com/webgame/sso/](http://www.wildsnake.com/webgame/sso/) to test Java. 
The whole point of this mini-mini howto is to install (well... unpack) Firefox 64bit and use it peacefully with flash and java!
Hope it helped

---

### Post by mdr on 2006-11-06
well this worked for me on Firefox 2 and using flash 9 beta

very easy and simple ....

---

### Post by nardis_Miles1 on 2006-11-15
I'm wondering if this 64-bit firefox is stable. I have been running the debian firefox version on an amd64 box and it frequently dies. The way to kill it is to click on a hyperlink, or to click on the back arrow. Have you had that sort of failure with your fresh installation?

Art Edwards

---

### Post by teppic on 2006-11-22
This is using 32bit Firefox, not 64bit.

---

