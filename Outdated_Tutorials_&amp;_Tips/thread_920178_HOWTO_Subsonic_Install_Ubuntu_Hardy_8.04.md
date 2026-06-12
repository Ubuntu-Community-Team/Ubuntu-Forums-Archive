---
title: "HOWTO: Subsonic Install Ubuntu Hardy 8.04"
date: 2008-09-15
forum: Outdated Tutorials &amp; Tips
---

### Post by sherl0ck on 2008-09-15
Subsonic is a great web-based media streamer.
URL:[ [http://subsonic.sourceforge.net](http://subsonic.sourceforge.net)]("http://subsonic.sourceforge.net")

Step1: Dependencies
```
sudo apt-get install tomcat5.5
```
```
cd; wget http://prdownloads.sourceforge.net/subsonic/subsonic-3.4.zip
```

Step2: Modify Init For Tomcat & Start
```
sudo nano /etc/init.d/tomcat5.5
```
Change TOMCAT_SECURITY=yes to TOMCAT_SECURITY=no
[SIZE="2"]*If anyone has a better solution for this please post.[/SIZE]
```
sudo /etc/init.d/tomcat5.5 start
```

Step3: Unzip/Install Subsonic
```
unzip subsonic-3.4.zip
```
```
mv subsonic.war /var/lib/tomcat5.5/webapps/
```
```
mkdir /var/subsonic
```
```
chown tomcat55:nogroup /var/subsonic
```

Step4: Test 
```
firefox http://127.0.0.1:8180/subsonic
```

Enjoy! -Sherl0ck

---

### Post by GeirS73 on 2008-10-11
I run a 8.04 server edition and Subsonic works like a charm, except that thumbnails weren't shown. I got the following exception in /var/subsonic/subsonic.log

> ...
java.lang.NoClassDefFoundError
at com.sun.imageio.plugins.jpeg.JPEGImageReaderSpi.createReaderInstance(JPEGImageReaderSpi.java:89)
...

I googled for it and found an [article]("http://forums.sun.com/thread.jspa?messageID=1783454") suggesting that the reason for the exception was probably that java didn't find the proper libX*.so libraries. 

It seems that the java libraries are referencing /usr/X11R6/lib when looking for some low level image libraries, but on a server edition that directory doesn't exist (until you install X i guess). The solution is to do the following:

```

cd /usr/X11R6/
ln -s ../lib 

```

---

### Post by TwiceOver on 2008-10-11
Hrm.

Tomcat keeps crashing for me, I have to keep restarting the service.  Also the site is really laggy for me.  Other pages are just fine from my home server.

My dad was looking for something similar and I see it has a Windows installer, so I'll have him try it out.  I use Jinzora2 for my streaming and that seems to work fine.

---

### Post by TwiceOver on 2008-10-13
OK Got mine working... So far anyway.  Just for reference.  Subsonic requires both Java JRE and JDK in order to run and not crash I guess.

Nice program, the detachable web player is excellent.  Finally my own music at work!

---

