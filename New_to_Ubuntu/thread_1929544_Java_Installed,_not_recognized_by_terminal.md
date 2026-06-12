---
title: "Java Installed, not recognized by terminal"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Eniliad on 2012-02-22
Hi guys, I'm running the most recent installation of Xubuntu (installed today!). I've been getting some help with getting things set up elsewhere, but there's a few things I'm really stuck at. The biggest one for me right now is Java. I was disappointed to learn that Sun Java isn't supported on Xubuntu, but I was able to use the Software Center to download the OpenJDK without much trouble. I appear to have both 6 and 7 installed at the moment (not sure why or if that's a bad thing) but when I go to use it in the Terminal, I get the usual message that comes up if I don't have Java installed. I'd like to get the command-line working because I'd like to open a specific .jar file with extra parameters. If you're familiar with Minecraft, you'll know what I'm talking about. The game will load initially but crashes upon trying to get to the main menu. I'd like to try it with the extra parameters, but without the Terminal working, I don't think I can.

Thanks for the help! If you need any specs on my computer, please, let me know and I'll provide.

---

### Post by Cheesemill on 2012-02-22
You can install the official version of Java from Oracle. Before doing so I would recomend uninstalling any other versions that you have installed (OpenJDK).

Just use the following steps:
```
sudo add-apt-repository ppa:flexiondotorg/java 
sudo apt-get update
sudo apt-get install --reinstall sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
```

Also you only need the JDK (Java Development Kit) packages if you wish to develop Java applications. If you only need to run Java apps you can skip installing the sun-java6-jdk package.

---

### Post by Eniliad on 2012-02-22
Hey, thanks a ton! I was able to install Sun Java without a hitch. Seems to be working just great. :)

---

