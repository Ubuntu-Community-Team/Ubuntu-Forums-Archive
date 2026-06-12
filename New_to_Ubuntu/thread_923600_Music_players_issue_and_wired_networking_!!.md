---
title: "Music players issue and wired networking !!"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Hotzero on 2008-09-18
Hello everybody !!

I have been sick of windows recently. So I changed my OS to Ubuntu 8.04.1. It was great but some times the music players stop working (Including any kind of media players for ubuntu)and to make them work I must restart the wole computer!!!. In addition, I can not connect through the DSL wire. Actually, I can just connect the DSL through the wirelss. 

So I return to windows again Because I am new in Linux.

Also, I fyou can help to know what is that thing that makes Ubuntu do these nice [COLOR="Red"]Compiz Fusion[/COLOR] as in these Video ??? I think they call it [COLOR="Red"]Beryl  [/COLOR] ?? 


[http://www.youtube.com/watch?v=YKEcz_OTTBk]("http://www.youtube.com/watch?v=YKEcz_OTTBk")

---

### Post by jamesrl on 2008-09-19
Ok three issues:
First, no one can really help with non-specific complaints.  E.g., with 'media players stopped working' ... what specific media player (players?), how did it stop working (no sound, poor sound, froze, what kind of file(s) crashed it (mp3, dvd, etc) wouldn't open files, etc.).  There's a comprehensive sound guide to fixing problems in the sound section of these forums.  You can try launching the program from the command line and see if that gives any more info, or describe what happens in more detail.  

Also, there's a high probability that if your sound system crashes, you can get away with not restarting the whole computer, but just [Ctrl]-[Alt]-[Bkspc] to restart X (the graphical login environment of X, which will require you to login again but not wait for a full reboot).

Second, re: wired networking ... what is your ethernet card?  From the command line type in 
```

lspci | grep Ethernet

``` 
(which lists pci cards and then (grep) searches that list for ones beginning with Ethernet) and you should see your wired and wireless ethernet cards.  Should help with debugging wired internet (for debugging purposes it doesn't matter that it is DSL or cable or a T3, just the fact that it is an wired ethernet cable).

Finally, compiz and beryl were two separate development ideas that made eye candy visual effects like wobbly windows, desktop cube, etc.  The two projects merged and are now called 'compiz fusion' (and sometimes just compiz).   With 8.04 you can try enabling compiz fusion by going to System->Preferences->Appearance->Visual Effects and turning on Normal or Extra.  Depending on your hardware compiz fusion may be difficult to set up properly, but if you go to the proper subforum you should see help for your specific video card (assuming your video card can handle compiz).  If it works right away, you can tweak the settings if you go to synaptic package manager (and install the package compizconfig-settings-manager) and then go to System->Preferences->Advanced-Desktop-Effect-Settings.

---

