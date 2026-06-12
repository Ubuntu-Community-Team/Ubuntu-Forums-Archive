---
title: "How do you start applications"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by grc7 on 2008-06-19
New to Linux OS (Ubuntu 8.04LTS).  Have problems:
1. With E-mail I get text only, no pictures or video??
2. Downloaded Google Earth.  How do I use this application?  It downloaded to my desktop as (GoogleEarthLinux.bin) :confused:

This is not my first try with a Linux OS.  I have tried many over the last 10 years with no luck.  Have also posted questions but never received a reply??
Would someone please give some assistance?

---

### Post by cozmicharlie on 2008-06-19
Welcome to Ubuntu. You first need to install the audio and video codecs so you can play all your multimedia.  This is the best tutorial [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).  If you have any problems or need help post back and I can walk you through it.  Don't let the fact that the tutorial involves using the command line worry you - it really is easy.  If you want a GUI (interface) method let me know and I can walk you through it.

Enjoy!

---

### Post by damis648 on 2008-06-19
1. How are you connecting to your mail?

2. Google Earth: Right click the file, and properties. Go to the permissions tab and choose to let the file be executable. Close the dialogue. Now just double click the google earth file and select "run in terminal" and it will install.

---

### Post by atomkarinca on 2008-06-19
> **grc7 said:**
> 2. Downloaded Google Earth.  How do I use this application?  It downloaded to my desktop as (GoogleEarthLinux.bin) :confused:

Open up a terminal (Applications > Accessories > Terminal) and type these in the same order:

```
cd Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by sub2007 on 2008-06-19
Or alternatively, if you are going to follow cozmicharlie's instructions then you'll be adding the Medibuntu repository. This actually contains Google Earth, so after you add that repository then you can search for Google Earth in Synaptic (just type "googleearth" into the search box and when the search has finished mark it for installation) and it will take care of the installation for you without having to touch the Terminal.

---

