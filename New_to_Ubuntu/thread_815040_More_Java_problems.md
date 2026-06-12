---
title: "More Java problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by jmtjet on 2008-06-01
I'm trying to install jre to play some online games. I'm using Ubuntu 8.04 hardy and Firefox 2.0(uninstalled 3). 
I've installed jre using this command: 
Sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
As far as I can tell java is installed. I checked this using this command: java -version.
 The output to that command is:
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

But still no Java? If I try to play a games I get the "missing plugin" message. 

Also, If I check Firefox plugins via "about:plugins" it's not there. Would someone help me get this thing install properly. Thanks.

---

### Post by dstin1 on 2008-06-01
you need to link the following file to your plugin folder.

/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so

I think when I did it I used Nautilus.
```
gksudo nautilus
```

then go to the java folder right click on the file create link the cut and paste it to your plugin folder.

you can also use the ln command but I am not sure of the exact syntax.

---

### Post by jmtjet on 2008-06-09
I can't copy/paste the needed plugin into the Firefox plugins folder due to not having permission. How do I change the permissions so I can move the needed java plugin? Thanks.

---

### Post by SunnyRabbiera on 2008-06-09
you have to enter superuser mode by typing in sudo before the desired command.

---

### Post by Nepherte on 2008-06-09
```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so
```
Assuming Firefox 2 uses /usr/lib/firefox/plugins

---

### Post by jmtjet on 2008-06-09
Thanks, that got it. :)

---

