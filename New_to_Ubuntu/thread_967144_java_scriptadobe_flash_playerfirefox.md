---
title: "java script/adobe flash player/firefox"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by adamogardner on 2008-11-01
so I'm watching some clips on utube of golden eagles taking out wolves and deer and suddenly videos stop playing and I get a message that reads, '
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.
'  I don't know how this works but I find a lot of web pages I visit will declare that I need missing plug-ins to view all of the contents. I have tried to do that but it never works.  I always assumed it was due to linux-incompatability, but now that this has happened with utube it also brings to question these 'missing plugins.'
So I don't know how to turn off/on java script.  I can't seem to install missing plugins to view all contents of certain websites.  and what's with adobe flash; do we use it?

---

### Post by Mazza558 on 2008-11-01
Are you on Hardy or Ibex?

---

### Post by Sealbhach on 2008-11-01
Hi, did you install all the available packages using this guide here?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

This should sort out most of your problems.

I didn't know golden eagles could take out wolves.... wow!


.

---

### Post by adamogardner on 2008-11-02
I'm on hardy.

---

### Post by kansasnoob on 2008-11-02
I'd try starting with this, go to Applications > Accessories > Terminal and run this command (just use copy-n-paste to avoid errors):

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

That'll get you the bare minimum java, gstreamer, etc. Of course if you're running Kubuntu or Xubuntu add the k or x to that command accordingly.

Just in case you have gnash installed, also in terminal:

```
sudo apt-get remove gnash
```

Since Flash 10 is far superior I'd then, still in terminal:

```
sudo apt-get --purge remove flashplugin-nonfree
```

And then install the Flash 10 .deb from here(just copy-n-paste the url in your browser address window):

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Then restart Firefox by going to File > Quit, then restart Firefox and see how it works. Occasionally I've had to restart the desktop (Ctrl > Alt > Backspace) to get changes to stick, I don't know why.

It might also be good to go to Tools > Add-ons > Plugins and make sure that firefox is not still showing both Flash 9 and Flash 10. If so just choose disable in Flash 9 and restart Firefox again.

---

### Post by adamogardner on 2008-11-02
kansasnoob  I tried to start that way, but this is going on.  I don't know about a 'media change'  do I want to proceed?  Will i know what to do after inserting the disk?

---

### Post by kansasnoob on 2008-11-02
> **adamogardner said:**
> kansasnoob  I tried to start that way, but this is going on.  I don't know about a 'media change'  do I want to proceed?  Will i know what to do after inserting the disk?

You're losing me here. What disc? You do have Ubuntu 8.04 installed on your hard drive right?

The commands I gave are to be run in the terminal, no disc needed as the applications are in the repositories.

I'll edit my original post a bit.

---

### Post by adamogardner on 2008-11-02
> **kansasnoob said:**
> You're losing me here. What disc? You do have Ubuntu 8.04 installed on your hard drive right?

The commands I gave are to be run in the terminal, no disc needed as the applications are in the repositories.

I'll edit my original post a bit.

I'm so sorry,  lost traCK OF  things here and here's what I mean:

The following extra packages will be installed:
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse libfaac0 liblame0 libmjpegtools0c2a
  libquicktime1 libx264-57 libxvidcore4 msttcorefonts odbcinst1debian1
  sun-java6-bin sun-java6-jre sun-java6-plugin unixodbc unrar
Suggested packages:
  sun-java6-fonts libct1 libmyodbc odbc-postgresql
Recommended packages:
  w32codecs gsfonts-x11
The following NEW packages will be installed:
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse libfaac0 liblame0 libmjpegtools0c2a
  libquicktime1 libx264-57 libxvidcore4 msttcorefonts odbcinst1debian1
  sun-java6-bin sun-java6-jre sun-java6-plugin ubuntu-restricted-extras
  unixodbc unrar
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.6MB/35.7MB of archives.
After this operation, 103MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)'
in the drive '/cdrom/' and press enter

---

### Post by Sealbhach on 2008-11-04
Have you ticked all the software sources in System/Administration/Software Sources? And also untick the CD rom if it is still ticked?



.

---

