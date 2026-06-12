---
title: "Installing software"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by *^kyfds( on 2011-12-23
hi.

i'm trying to install java, and i basically got stuck after downloading the installer (a self extracting .bin file)

when i tried to run the file, i got a message saying something like  "the file is of an unknown type"

i read  [this guide]("http://www.java.com/en/download/help/linux_install.xml#selfextracting"), but it didn't really help as i can't understand what to do.

I'm still pretty new to Ubuntu (and linux in general) as a switchover from windows 7,  so don't be surprised if I've made a stupid mistake somewhere.

thanks in advance.

---

### Post by Karlchen on 2011-12-23
Hello, Thehumorouscheese.

I guess that this step-by-step instruction may be a little bit easier to understand and follow, although basically it explains the same procedure as the Oracle instruction: [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU").

HTH,
Karl

---

### Post by hackb0y294 on 2011-12-23
You might read this: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) then post back which version exactly you want to install, and we can go from there.

---

### Post by collisionystm on 2011-12-23
> **Thehumorouscheese said:**
> hi.

i'm trying to install java, and i basically got stuck after downloading the installer (a self extracting .bin file)

when i tried to run the file, i got a message saying something like  "the file is of an unknown type"

i read  [this guide]("http://www.java.com/en/download/help/linux_install.xml#selfextracting"), but it didn't really help as i can't understand what to do.

I'm still pretty new to Ubuntu (and linux in general) as a switchover from windows 7,  so don't be surprised if I've made a stupid mistake somewhere.

thanks in advance.


You need to run the file through the terminal

make it executable, either by right clicking on it and going to permissions, or issue the command

chmod +x FILENAME

then execute it with

./filename

---

### Post by *^kyfds( on 2011-12-24
> **hackb0y294 said:**
> You might read this: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) then post back which version exactly you want to install, and we can go from there.


i went with openJDK method, just because it's available in the ubuntu software centre.

both the iced-tea plugin and the JDK installed sucessfully.

for future reference, is there a simplified method of installing downloaded software packages?

thanks.

---

### Post by Zill on 2011-12-24
> **Thehumorouscheese said:**
> i went with openJDK method, just because it's available in the ubuntu software centre.

both the iced-tea plugin and the JDK installed sucessfully.

for future reference, is there a simplified method of installing downloaded software packages?

thanks.

Simply open a terminal and use apt-get (with the sudo prefix) to install a package.

eg. To install a single package that will pull in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, [COLOR="Red"]Java runtime environment[/COLOR], Flash plugin, LAME (to create compressed audio files), and DVD playback.
```
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Paqman on 2011-12-24
> **Thehumorouscheese said:**
> i went with openJDK method, just because it's available in the ubuntu software centre.


It's actually now the only method. You can't get the old Sun Java 6 for Ubuntu any more, OpenJDK is where it's at now.

---

