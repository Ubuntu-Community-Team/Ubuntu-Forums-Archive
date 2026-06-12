---
title: "Fire fox is relly messed upp"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Kedster on 2008-09-07
ok so when i got to certain sites(torrent site for sure and lots of others) it will just shut down when i scroll a lil bit it a lot of times doesn't stop scrolling and then shuts down it logs me out of stuff lots, it very leggy and it seems to be getting really slow and like sometimes it wont use flash i think because every once in a while youtube tells me i need to install flash  i dont no whats wrong with it

---

### Post by meborc on 2008-09-07
what version flash are you using?

you might need to reinstall it or firefox... remove firefox from add/remove... remove the .mozilla/firefox folder in your home... reinstall it from add/remove and try again...

or you could try emptying the cache (ctrl+shift+del)

---

### Post by evertsfnic on 2008-09-07
Use The best web browser in the world. "OPERA":popcorn::popcorn:

---

### Post by Kedster on 2008-09-07
from what i can tell i can go to sites i wasn't able to before it doesn't do the scroll thing and flash seems to work a lot better so i think it worked perfectly but if anything else happens ill post

---

### Post by stevoo on 2008-09-07
I had the same problems before my self. 
FF hanging and turning gray with the possibility never to come back and crushing when hitting some sites.

They all come down to Flash.

---

### Post by kansasnoob on 2008-09-07
I've had excellent luck solving Firefox crashes following this guide:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

NOTE: there are specific sections for 64bit and i386!

When you're done just type into the URL box,

> about:PLUGINS

PLUGINS can be all lower case but I don't want to post :p

If it shows anything older than Shockwave Flash 10.0.0 d569 you can remove any older versions by:

```
sudo apt-get remove --purge flashplugin-nonfree
```

and:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

And then get the latest release candidate here:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

It's a deb file so it's easy as falling off a log to install.

---

### Post by Xiong Chiamiov on 2008-09-07
> **evertsfnic said:**
> Use The best web browser in the world. "OPERA":popcorn::popcorn:
If you don't need all of the extensions of firefox, I highly recommend Opera for fast browsing.  There are also some other lightweight gecko-based browsers, such as Epiphany and Kazehakase.

---

