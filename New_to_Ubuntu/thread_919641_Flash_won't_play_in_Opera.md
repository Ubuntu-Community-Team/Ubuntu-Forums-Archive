---
title: "Flash won't play in Opera"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by lolwhites on 2008-09-14
I upgraded Opera to version 9.52, now Flash content won't play. I'm running the latest version of flash, and the plugin path is correct (/usr/lib/flashplugin-nonfree, so I have no idea what the problem is.

It works OK in Firefox and Seamonkey, it's just Opera that poses the problem.

Edit: I've just discovered that when I switch tabs, the spot where the flash should be is instead a "hole" showing what's under it in the next tab!

---

### Post by gandaran on 2008-09-14
> I upgraded Opera to version 9.52, now Flash content won't play. I'm running the latest version of flash, and the plugin path is correct (/usr/lib/flashplugin-nonfree, so I have no idea what the problem is.
it should work with flash installed in this folder!
you can copy the plugin, **libflashplayer.so** file t o /usr/lib/opera/plugins then.

---

### Post by lolwhites on 2008-09-14
I checked /usr/lib/opera/plugins and it was already there.

I sometimes get sound but still no picture.

---

### Post by ronniet on 2008-09-21
> **lolwhites said:**
> I checked /usr/lib/opera/plugins and it was already there.

I sometimes get sound but still no picture.

**Same here!**  :(
Using *Opera 9.52*

I've tried the alternative flash plugin, the mozilla plugin and copying the .so file to the opera/plugin, but still no working Flash. All Flash movies are reeeeeeaallly slooowww IF they play at all, most are just a white square, to get any further with them you have to keep reloading the page. Weird...  :confused:

**Any help would be much appreciated folks!**  :)

---

### Post by MasterNetra on 2008-09-21
Then stick with mozilla! :mrgreen:

---

### Post by ronniet on 2008-09-21
> **MasterNetra said:**
> Then stick with mozilla! :mrgreen:

***buzzer***- wrong answer!

---

### Post by MasterNetra on 2008-09-21
It can't be wrong because i'm always right! :cool: :p

---

### Post by TenPlus1 on 2008-09-21
I have Opera 9.60 installed with Flash 10 beta in ~/.opera/plugins for good measure and all works well...

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by ronniet on 2008-09-21
> **TenPlus1 said:**
> I have Opera 9.60 installed with Flash 10 beta in ~/.opera/plugins for good measure and all works well...

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Tried that, just there, and while the browser doesn't freeze as much, it just doesn't display ANY Flash with v10  :(

---

### Post by linkmaster03 on 2008-09-21
This is what happens to me in Firefox, so I have to use Opera for Flash lol.

---

### Post by Stratok on 2009-07-14
Found an answer:
so this is what I did:
go to: tools>preferences>advanced>content>plug-in options>change path> check /usr/lib/opera/plugins, uncheck /usr/lib/mozilla/plugins...

Now go to /usr/lib/mozilla/plugins and copy the plugins to /usr/lib/opera/plugins... you may need admin permisions...
in ubuntu is: gksu nautilus
in xubuntu is: gksu thunar
in kubuntu, well i dont know

Now here is the trick:
in the opera plug in folder delete the flash plugin, sonething like flashplugin-alternative.so
download a prior version of flashplayer:
for example(from adobe page)...

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp10_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp10_archive.zip)

unzip... use the 10r12_36 version for example (that one worked for me...)
decompress the flashplayer_10r12_36_linux.tar.gz file, and copy:
libflashplayer.so
to /usr/lib/opera/plugins
now it works!.

---

### Post by westeh on 2010-01-20
Worked for me to  - thank you wery much.

Harald:D

---

