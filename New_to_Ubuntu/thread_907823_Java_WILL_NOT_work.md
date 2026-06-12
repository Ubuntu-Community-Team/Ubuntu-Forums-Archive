---
title: "Java WILL NOT work"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by k1ngb0b0 on 2008-09-01
Hello everyone.

I can't seem to figure this out.  I have java installed correctly but firefox does not detect that I have it installed.

I go to the address bar and type about:plugins and java is not displayed.  Help would be greatly appreciated.

---

### Post by jemate18 on 2008-09-01
> **k1ngb0b0 said:**
> Hello everyone.

I can't seem to figure this out.  I have java installed correctly but firefox does not detect that I have it installed.

I go to the address bar and type about:plugins and java is not displayed.  Help would be greatly appreciated.

On firefox Click
Edit -> Preferences

On the Content tab
Check enable java

Can you give the process on how you installed java?

---

### Post by aloshbennett on 2008-09-02
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

see if the applets load

---

### Post by alienexplorers on 2008-09-02
Did you make a symbolic link to the /usr/lib/firefox-addons/plugins?

---

### Post by Crafty Kisses on 2008-09-02
Post the results of this command:
```
java --version
```

---

### Post by Nepherte on 2008-09-02
Did you also download the java browser plugin package? The browser plugin is not included in the normal java5/6 package.

If you are running 32bit:
```
sudo apt-get install sun-java6-plugin
```
If you are running 64, you will need openjdk instead of the regular sun java:
```
sudo apt-get install icedtea-gcjwebplugin
```

---

### Post by k1ngb0b0 on 2008-09-02
> On firefox Click
Edit -> Preferences

On the Content tab
Check enable java

Can you give the process on how you installed java?

Java is already enabled in the browser.  To install, I went to add/remove programs and clicked OpenjDK Java

> [http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

see if the applets load

The clocks did not load.

> Did you make a symbolic link to the /usr/lib/firefox-addons/plugins?

I did not do this, I'm not sure how to do it.  Can you explain the process?

> Post the results of this command: java -version

java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)


The java browser plugin says it's the most current (I use 64 bit unbuntu so I use openjdk.)

Thank you all for the great responses :)  Hopefully I'll get this figured out soon.

---

### Post by k1ngb0b0 on 2008-09-03
Still haven't figured this out..

---

### Post by philinux on 2008-09-03
In firefox click

Tools>Addons>Plugins

screen print it and post back. You might need to maximise the pane.

---

### Post by k1ngb0b0 on 2008-09-03
Java isn't listed as one of the plugins.

It also does not show up when I type about:plugins in the firefox address bar.

---

### Post by k1ngb0b0 on 2008-09-04
Haven't found a solution yet dispite looking at various forums and other places for help...

---

### Post by lordadi on 2008-09-08
This link maight solve it:[http://www.psychocats.net/ubuntu/java]("http://www.psychocats.net/ubuntu/java"), but this assumes that firefox does not already believe itself to have java. If it still believes that java is installed, you have (as I see it) 2 options:[LIST=1]
[*]Delete your .mozilla directory to **lose ALL your settings, bookmarks and most importantly conf files**
[*]install a 32 bit firefox with 32 bit goodies and set it as your default browser. see [http://ubuntuforums.org/showthread.php?t=202537]("http://ubuntuforums.org/showthread.php?t=202537") or [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins"). The first link is prefered because it IS known to work for AMD64. However, please read the 101 pages of the thread before trying anything :lolflag:
[/LIST]

By The Way, BACKUP before you try this as it *may* break your system.


Lordadi.

---

