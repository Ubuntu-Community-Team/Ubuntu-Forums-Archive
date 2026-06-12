---
title: "HOWTO: Flash in breezy(with sound)"
date: 2005-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by comradevik on 2005-10-30
so you upgraded to breezy but you get no sound in flash
here is what I did:

```

cd /usr/lib/mozilla-firefox/plugins
sudo rm libflash*
sudo rm flash*

sudo apt-get install libflash0c2 libflash-dev libflash-mozplugin libflash-swfplayer flashplayer-mozilla flashplugin-nonfree

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

```

restart firefox

this should give you flash sound
to test .. go to [www.badgerbadgerbadger.com](www.badgerbadgerbadger.com)

---

### Post by .Danny on 2005-10-31
Hmm well I have flash sound working, but I see nothing. That is it's just black. And that happens on other pages as well.:(

---

### Post by Nano on 2005-10-31
Didn't work

---

### Post by madjo on 2005-10-31
this worked wonders for me.. thank you

---

### Post by godlike on 2005-10-31
worked great for me too thanx alot

---

### Post by _Zardoz_ on 2005-10-31
No way for me...it doesn't work!

---

### Post by wondering_jew on 2005-10-31
a less messy way to fix this problem is to do

sudo apt-get install libsdl1.2debian-all

then everything that uses sound should play nicely together and you don't need to mess around with the plugins themselves.

---

### Post by comradevik on 2005-11-02
[QUOTE=_Zardoz_]No way for me...it doesn't work![/QUOTE]

Zardoz.. did you follow it step by step.. do you get any errors?
what are the files in your /usr/lib/mozilla-firefox/plugins folder

---

### Post by andycjw on 2005-11-05
[QUOTE=wondering_jew]a less messy way to fix this problem is to do

sudo apt-get install libsdl1.2debian-all

then everything that uses sound should play nicely together and you don't need to mess around with the plugins themselves.[/QUOTE]

This works like charm, thanks!

---

### Post by _Zardoz_ on 2005-11-06
These files are in the directory u told me to look in:

flashplayer.xpt        libjavaplugin.so     libtotem_mozilla.so
libflash-mozplugin.so  libtotem_mozilla.a   libtotem_mozilla.xpt
libflashplayer.so      libtotem_mozilla.la  nppdf.so

I have two soundcards, one integrated and the other one is Audigy on pci. I can hear all sounds but flash because the sound is redirected on the integrated card instead of Audigy. Infact if I plug the jack on the integrated card I can hear flash sound!

---

### Post by joey on 2005-12-24
Howdy...

I had the same problem and all the other posts didn't help. This did.  I followed the instructions. Restarted Firefox. Then I was prompted to reinstall the plug-in via Firefox's plug-in finder.  Then....I got Badgers. :-)

Thanks!

---

### Post by bluevoodoo1 on 2006-01-07
[QUOTE=comradevik]so you upgraded to breezy but you get no sound in flash
here is what I did[/QUOTE]

Thank you! Worked perfectly!

---

