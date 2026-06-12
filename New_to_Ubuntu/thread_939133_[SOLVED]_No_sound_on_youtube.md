---
title: "[SOLVED] No sound on youtube?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Axis on 2008-10-05
So I noticed when I'm on youtube none of the videos will make any noise!?

I am completely updated and I installed the non-free flash version. (You know the first option when you go to a flash based site without flash) Any suggestions?

I have also downloaded the flash installer from the website, and then tried again only to yet again not prevail.

Any help would be appreciated!

---

### Post by billgoldberg on 2008-10-05
> **Axis said:**
> So I noticed when I'm on youtube none of the videos will make any noise!?

I am completely updated and I installed the non-free flash version. (You know the first option when you go to a flash based site without flash) Any suggestions?

I have also downloaded the flash installer from the website, and then tried again only to yet again not prevail.

Any help would be appreciated!

[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)

---

### Post by cecure on 2008-10-05
Sorry my suggestion was incorrect

---

### Post by christianvaldes on 2008-10-05
Did you resolve your problem?
Can you get sound out of another program?
Try closing all your applications and then running youtube.com
Another device might not have released the Soundcard.
Also the soundcard may be configured improperly.

---

### Post by kansasnoob on 2008-10-05
The following tutorial solved my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Note: there are specific steps for i386 and 64bit!

Afterwards I'd still get an occasional Flash/Firefox crash so I removed any possible older versions of flash by:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

(Don't worry if it says "not found" or something of the sort, we're just making sure any and all older versions of flash are removed)

Then install the Flash 10 RC:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

---

### Post by christianvaldes on 2008-10-05
> **kansasnoob said:**
> The following tutorial solved my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Note: there are specific steps for i386 and 64bit!

Afterwards I'd still get an occasional Flash/Firefox crash so I removed any possible older versions of flash by:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

(Don't worry if it says "not found" or something of the sort, we're just making sure any and all older versions of flash are removed)

Then install the Flash 10 RC:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

I had a problem with Flash on Youtube.
I installed the latest version of Flash from Adobe.
This solved my flash freezing in my browser.
I was curious is this the same problem you were having.

---

### Post by Axis on 2008-10-05
> **kansasnoob said:**
> The following tutorial solved my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Note: there are specific steps for i386 and 64bit!

Afterwards I'd still get an occasional Flash/Firefox crash so I removed any possible older versions of flash by:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

(Don't worry if it says "not found" or something of the sort, we're just making sure any and all older versions of flash are removed)

Then install the Flash 10 RC:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

This solved my problem :)

Thank you guys very much. Best community ever still to this day.

---

### Post by christianvaldes on 2008-10-05
Let me know if you have problems with youtube.com freezing.

---

### Post by kansasnoob on 2008-10-05
> **christianvaldes said:**
> I had a problem with Flash on Youtube.
I installed the latest version of Flash from Adobe.
This solved my flash freezing in my browser.
I was curious is this the same problem you were having.

I had a variety of problems: sound not working part of the time, flash not working after watching video w/vlc, flash actually "crashing" firefox frequently.

I tried a few other work arounds, one of which really improved things, but the "fix" I just posted has been the most reliable.

Although I have used that .deb for other Hardy based releases like Mint Elyssa and it works just fine with no other changes, in fact I just tried it on a fresh install of Hardy - fully updated - without the pulse audio fix and it appeared to work just fine.

---

