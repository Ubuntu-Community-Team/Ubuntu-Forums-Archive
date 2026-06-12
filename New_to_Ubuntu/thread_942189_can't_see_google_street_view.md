---
title: "can't see google street view"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by scotcella on 2008-10-08
For some reason i can't see houses I would like to look at one google street view. After I click on the Flash icon, the picture comes up black. 

I note that not many people are having issues with it but I'm wondering what I can to do enable myself to see the houses.

THanks in advance!

---

### Post by Ubuntiac on 2008-10-08
Do you have Java installed?

I know you can install it with some other apps that are useful, but not legal in some countries like copy protected DVD playback by typing:
sudo apt-get install ubuntu-restricted-extras

Alternatively just do a search for which package to install Java. I think it's something along the lines of sun-java6-jre.

Also, are you running desktop effects? It's only a slim chance, but DTE's have caused quite a bit of trouble with video playback. Maybe they're an issue here too (although I'd guess at Java first).

---

### Post by crashme on 2008-11-01
I have the same problem. It only occurred after upgrading from Ubuntu 7.10 to 8.04. I'm also in Australia. I have ubuntu-restricted-extras installed for the Flash/Java plugins and Flash and Java are working fine on other sites.

Street view seems to be using Flash, since I have the Flash blocker installed in Firefox and get the button to run the animation. However when pressed it comes up as a black window every time.

EDIT: as for desktop effects, I don't even know what that is.

---

### Post by crashme on 2008-11-08
It's working again after upgrading to Ubuntu 8.10. *shrug*

---

### Post by floydwilde on 2008-12-24
hmm, this forum thread comes the closest to matching my problem.  In google street view when I drag the little guy to the map, instead of the picture of the street i see a black screen. 

It's strange because it was working previously.  I'm using 8.10.  Firefox 3.0.5 is the browser.  

So far I've tried removing some recent plugins.  I tried removing and re-installing flash.  I have a java plugin installed.  

I see this:
 
```
# ls -ll /usr/lib/mozilla/plugins/
total 0
lrwxrwxrwx 1 root root 37 2008-12-25 11:38 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 39 2008-10-31 10:23 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 44 2008-11-08 17:05 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root 42 2008-11-08 17:05 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root 44 2008-11-08 17:05 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root 50 2008-11-08 17:05 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.
```

So I guess I'll go see if there is an alternative to the alternative.  Or something.

---

### Post by floydwilde on 2008-12-24
more notes, I see 

```
# apt-cache search flashplugin
flashplugin-nonfree-extrasound - Adobe Flash Player platform support library for Esound and OSS
flashplugin-nonfree - Adobe Flash Player plugin installer
adobe-flashplugin - Adobe Flash Player plugin version 10

```

I think it's interesting that when I try to remove, with aptitude for instance the adobe-flashplugin, it doesn't seem to remove anything: 

```

# aptitude remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  adobe-flashplugin 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 10.1MB will be freed.
Writing extended state information... Done
(Reading database ... 202929 files and directories currently installed.)
Removing adobe-flashplugin ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

# ls -ll /etc/alternatives/mozilla-
mozilla-flashplugin    mozilla-javaplugin.so  
root@satori:/usr/lib/mozilla/plugins# ls -ll /etc/alternatives/mozilla-flashplugin 
lrwxrwxrwx 1 root root 43 2008-12-25 12:00 /etc/alternatives/mozilla-flashplugin -> /usr/lib/swfdec-mozilla/libswfdecmozilla.so
# cd /usr/lib/swfdec-mozilla/
# ls
libswfdecmozilla.so

```

If I go manually delete those files/symlinks, and reinstall they come back. 

And after I did that, I am able to see pictures in google street view again.  I'm not sure one thing had to do with the other, and the reason i wasn't seeing the pictures was some network problem or something.

---

### Post by macogw on 2009-04-07
It worked because you switched it to use Adobe's Flash from Swfdec.  Swfdec is nice and open source and all, but it doesn't support Street View yet.

---

