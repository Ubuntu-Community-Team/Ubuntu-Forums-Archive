---
title: "RuneScape HD on Ubuntu 64-bit HOW-TO"
date: 2009-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Frogging101 on 2009-11-24
Many people have been trying to run RuneScape HD on Ubuntu 64-bit properly. This tutorial has been tested on Ubuntu 8.10. It also corrects an issue where java 'takes over' the sound card, and you can't hear anything but RuneScape. 
[B]
You must have pulseaudio installed to complete this tutorial. Also, make sure you have the latest drivers for your video card.
[/B]
Anyway, here it is:

1. UNINSTALL any existing java packages, 64-bit or otherwise.

2. Follow these instructions to install 32-bit Firefox (**Installing 32-bit edition of Firefox**), do ***NOT*** install java yet: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Installing%2032-bit%20Edition%20of%20Firefox]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins#Installing%2032-bit%20Edition%20of%20Firefox")

You will now be able to start 32-bit firefox with ```
firefox32
```

2. Install IcedTea java

```
sudo apt-get install icedtea6-plugin
```

3. Install **getlibs** (Credit goes to Cappy for creating this program)

Go to thread [http://ubuntuforums.org/showthread.php?t=474790]("http://ubuntuforums.org/showthread.php?t=474790")

4. Run these commands in order:

```
sudo getlibs -p icedtea6-plugin
sudo getlibs -p icedtea-6-jre-cacao
sudo getlibs -p openjdk-6-jre
sudo getlibs -p openjdk-6-jre-lib
sudo getlibs -p openjdk-6-jre-headless
```

5. Now, we will set up the plugin. Run these commands in order:
```

sudo ln -s /usr/lib32/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so /usr/local/firefox32/plugins/
sudo rm /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjsoundalsa.so
sudo rm /usr/lib32/jvm/java-6-openjdk/jre/lib/i386/libjsoundalsa.so
sudo rm /usr/lib32/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libjsoundalsa.so
```

6. Run firefox32 in a terminal, and you should be ready to play!

---

