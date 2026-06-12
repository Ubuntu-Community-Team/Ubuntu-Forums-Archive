---
title: "Java and Flash"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by bloodandsoil on 2008-11-01
Hi, what is the "official" way to install java and flash support on Ubuntu 8.10?

When I go to a website that uses flash or java, I am not getting the ubuntu dialog that pops up and asks me to install it.

Thanks! :)

---

### Post by Nepherte on 2008-11-01
Flash:
```
sudo apt-get install flashplugin-nonfree
```

Java:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by bloodandsoil on 2008-11-01
I looked on the wiki help and do not see anything about this.

Looks like there are many different versions of java and flash able to be installed.  Kinda confusing.

Why doesn't 8.10 pop up an installation box when I visit java or flash site?  Isn't it supposed to prompt me to automatically install the supporting software?

---

### Post by Nepherte on 2008-11-01
You simply didn't search all to well: 
[https://help.ubuntu.com/7.04/internet/C/web-plugins.html](https://help.ubuntu.com/7.04/internet/C/web-plugins.html)
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Anyways, with the two commands I gave you in my earlier post, you should get the wanted effect (unless you are using 64bit, then you will have to do something else to install the java web plugin).

---

### Post by bloodandsoil on 2008-11-01
Yea I did actually see all of those pages, but they are not for version 8.10.

I was looking for instructions for the version of Ubuntu that I am using--8.10.

---

### Post by jespdj on 2008-11-01
The instructions to install Flash and Java for 8.10 are the same as for 8.04 and earlier versions.

---

### Post by bloodandsoil on 2008-11-01
> **jespdj said:**
> The instructions to install Flash and Java for 8.10 are the same as for 8.04 and earlier versions.

Should I just install the Ubuntu restricted extras package? Is that a recommended method to get java, flash, and the other things?

When I go to installed ubuntu-restricted-extras, it wants to remove libavcodec51.  Is that normal?  What is libavcodec51?

---

### Post by Nepherte on 2008-11-01
libavcodec51 is the codec library from the ffmpeg project. It supports most existing encoding formats (MPEG, DivX, MPEG4, AC3, DV...).

It probably conflicts with ubuntu-restricted-extras because the latter one also contains codecs (namely gstreamer). You can safely continue the installation.

The installation of flash and java is the same for all versions of ubuntu. The "recommended" method to install it, is to install the packages from the repositories. ubuntu-restricted-extras is just a meta package containing other packages, so it will just do the same thing as my commands with the difference that it will install music and video codecs + unrar.

---

