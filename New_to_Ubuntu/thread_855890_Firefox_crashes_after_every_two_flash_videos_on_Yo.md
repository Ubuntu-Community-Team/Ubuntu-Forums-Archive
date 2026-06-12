---
title: "Firefox crashes after every two flash videos on Youtube"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by alecwh on 2008-07-10
Hello,

For some reason, every second (or rarely third) YouTube video I play, Firefox crashes. This ONLY happens on pages with flash, and it gets annoying very fast.

I've tested this on 3 computers now, and they all do the same thing.

Is this a recognized problem? Why is it doing this? Is there a fix?

---

### Post by iaculallad on 2008-07-10
Try to use GNASH instead of Adobe's proprietary Flash.

```
sudo apt-get install gnash
```

---

### Post by ibuclaw on 2008-07-10
This is to do with flash not mingling with Ubuntu's PulseAudio Sound Server very well.

There are only a few workarounds so far.
One being:
```

wget http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb
sudo dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb
sudo aptitude purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

Or you can upgrade to the latest Flash 10 beta (some reported problems but the crashing has stopped).

Add this to your sources file
```
deb http://ppa.launchpad.net/thielmann/ubuntu hardy main
```
And run and update and install the package **flashplugin-nonfreebeta**

Regards
Iain

---

### Post by Izkata on 2008-10-12
Since this comes up in a Google search (as I've been having the same problem), where's another possible solution:  Disable pulseaudio.  Works perfectly for me, not more firefox crashes at youtube *and* it re-enables sound in youtube without needing libflashsupport:

pkill pulseaudio
sudo chmod -x /usr/bin/pulseaudio

Then restart Firefox.

---

### Post by kansasnoob on 2008-10-12
The Flash 10 RC has worked great for me. Look at my post #15 here:

[http://ubuntuforums.org/showthread.php?t=934600&page=2](http://ubuntuforums.org/showthread.php?t=934600&page=2)

---

