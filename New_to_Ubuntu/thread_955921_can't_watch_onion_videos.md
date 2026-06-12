---
title: "can't watch onion videos"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by cowznofsky on 2008-10-22
I'm not sure what format they use at The Onion, but the videos don't play.  I just see a mostly blank panel with an embed block on it.

---

### Post by Pconfig on 2008-10-22
Are you sure you have flash installed? Seems to me those videos play with a flash movieplayer ;)

---

### Post by Nxion on 2008-10-22
You need the flash :)

```
sudo aptitude install flashplugin-nonfree
```

---

### Post by cowznofsky on 2008-10-22
but I can watch youtube.  isn't that flash?

---

### Post by Nxion on 2008-10-23
Well then I guess you don't need flash :) Maybe Java; Can you give a screen shot of what you see if you try to watch the videos on the onion? Also, aside from Youtube, does other videos play on other sites? Try [www.southparkstudios.com.]("http://ubuntuforums.org/www.southparkstudios.com/")

What happens when you try to play them?

---

### Post by kansasnoob on 2008-10-23
Hmmmmmmmmm, oddly I couldn't either - and that was with the new Flash 10 Final Release! So after quite a bit of playing I found that the somewhat older Flash 10 RC does work.

**Assuming this is Hardy (8.04)** go to terminal:

```
 sudo apt-get install --reinstall ubuntu-restricted-extras
```

NOTE: I'm assuming this is Ubuntu, if it's Kubuntu or Xubuntu add the k or x accordingly!

(Just doing that to be certain you have the neccessary java, etc)

Now to remove any and all other versions of flash:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
sudo apt-get remove --purge adobe-flashplugin
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

(I would expect two of those commands to say something to the effect of "can't do - not found", that's OK. We just want to be sure that we removed all previous flash plugins)

Then install the Flash 10 RC from this .deb:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

Once you're all done you'll need to restart Firefox: File > Quit, pause a minute and start Firefox again. Click on Tools > Addons > Plugins. You should see only one Shockwave Flash - hopefully 10.0.0 d569 and you should also see Java listed. (Occasionally I've had to restart the desktop to get changes to take a hold)

Something I've also found beneficial to flash performance is flashblock which should replace the flash "screen" with a button, although in Hardy and Mint Elyssa I've recently seen just a blank screen where there should be a button, but it's purely cosmetic - clicking on the blank screen still produces the flash screen. Anyway flashblock is in the repos so you can install from synaptic if you desire.

As to what's going on I've read that it's growing pains as far as websites needing to upgrade to use the newest flash, I don't know, I just do what works at the time. It can be reversed or changed easily later on.

---

