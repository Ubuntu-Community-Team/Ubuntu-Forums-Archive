---
title: "libjpeg-turbo installation"
date: 2012-01-02
forum: Programming Talk
---

### Post by Clive McCarthy on 2012-01-02
I'm about to start a new project which will read many jpeg images and I started the exploratory work to read the EXIF data. One thing lead to another and I stumbled upon libjpeg-turbo.

Wow, I thought, it has the _same_ API as libjpeg62 which I'm already using on an earlier project, and it promises a 2X to 4X speed improvement. This could be like free money, quantitative easing, etc. you get my drift... The fact that the guys at Chrome are using it was a clincher.

First I tried the obvious:
**[COLOR="Blue"]sudo apt-get install libjpeg-turbo[/COLOR]**
but that didn't work. And then a few obvious variants to equally no effect.

Then I downloaded the Debian package from Sourceforge and installed that using the Ubuntu installer and all seemed well, except I can't find where the installer put the lib and neither can gcc.

I'm using 10.10 -- forgot to mention.

I've searched in /usr/lib for anything with jpeg in the name, so where is it and what is it called?

This is probably a very simple issue but it has the promise of instant gratification. :)

Maybe the lib is lurking in /opt/libjpeg-turbo/lib

---

### Post by Clive McCarthy on 2012-01-04
This guy seems to have figured how to do it:
[http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html]("http://foss-boss.blogspot.com/2010/11/show-off-ubuntu-desktop-on-cloud.html")

# wget 'http://sourceforge.net/projects/libjpeg-turbo/files/1.0.1/libjpeg-turbo_1.0.1_i386.deb/download' -O libjpeg-turbo_1.0.1_i386.deb
# dpkg -i libjpeg-turbo_1.0.1_i386.deb
Selecting previously deselected package libjpeg-turbo.
(Reading database ... 25967 files and directories currently installed.)
Unpacking libjpeg-turbo (from libjpeg-turbo_1.0.1_i386.deb) ...
Setting up libjpeg-turbo (1.0.1-20100909) ...

# ls -l /usr/lib/libjpeg.so.62
lrwxrwxrwx 1 root root 17 2010-11-12 12:35 /usr/lib/libjpeg.so.62 -> libjpeg.so.62.0.0
# rm -rf /usr/lib/libjpeg.so.62
# ln -s /opt/libjpeg-turbo/lib/libjpeg.so.62.0.0 /usr/lib/libjpeg.so.62

---

