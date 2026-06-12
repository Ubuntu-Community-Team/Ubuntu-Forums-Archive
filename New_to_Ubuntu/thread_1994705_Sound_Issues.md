---
title: "Sound Issues"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by aquitania5 on 2012-06-03
Hi everyone, first post here but long time lurker

I have an old Toshiba Satellite M115 S1061 laptop which I use only for web browsing, downloading and minor word processing as I refuse to put my desktop online.

However, as a musician, it would be nice to have someway to listen to music online. But I haven't been able to get the laptop to do this.

I downloaded and installed Ubuntu 10.04 last year August and loved everything about it (had XP on before but it was intolerably slow) except that there was no sound. Went through a lot of trouble browsing the help forums but eventually gave up (desktop became internet bound).

I bought myself a nice pair of headphones later that year and discovered that there actually was audio, it was just really really quiet (everything was maxed out and I could barely hear).

So I tried again, following the advice given to other people but nothing has worked.

Recently I've reinstalled Windows on my desktop, did some upgrades and want to try the no internet thing again so I downloaded Ubuntu 12.04 yesterday and did a fresh HD format and intall hoping that would cure my sound woes but nothing changed.

I would really love if somebody could help me through step by step because I've had no luck with this at all and I'm getting quite frustrated.

Thanks in advance

---

### Post by mapes12 on 2012-06-03
This may have the answer:-

[http://ubuntuforums.org/showthread.php?t=1676720](http://ubuntuforums.org/showthread.php?t=1676720)

---

### Post by aquitania5 on 2012-06-03
He says to add:

options snd-hda-intel model=3stack

to the end of:

/etc/modprobe.d/alsa-base.conf

How do I get into the folder? It tells me permission is denied or the command is not found.

Thanks

---

### Post by mapes12 on 2012-06-03
Others may know of command line instructions but basically you need to access that file as Root. The way I would do this is to launch Nautilus as Root like this in Terminal```
gksu nautilus
```This is the GUI way. Navigate to the file you want to update. Clicking it will launch it in a text editor where you can make the change then save the file. Reboot and hopefully you will be back in business.

It would be a good idea to save a copy of the file before you make the edit. Perhaps to a memory stick or something. Then if it doesn't work you can always bring back the original file.

---

### Post by aquitania5 on 2012-06-03
Nope, nothing changed, Audio is barely audible. Anyone else have any suggestions??

---

