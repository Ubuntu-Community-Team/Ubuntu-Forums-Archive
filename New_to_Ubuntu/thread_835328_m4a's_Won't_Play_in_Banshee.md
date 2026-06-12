---
title: "m4a's Won't Play in Banshee"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2008-06-20
I finally got flash to work with local sound (made everything pulseaudio in sound preferences and reinstalled flashplugin-nonfree) but I can't play m4a's in Banshee. When I try to play an m4a, it kinda freezes Banshee, I can try to play other songs, it won't and I have to restart Banshee to be able to use it again.

I've followed the directions of this post:

[http://ubuntuforums.org/showpost.php?p=3803944&postcount=6](http://ubuntuforums.org/showpost.php?p=3803944&postcount=6)

But I have both multiverse/universe repositories enabled and have "gstreamer0.10-plugins-bad-multiverse" installed. I've reinstalled the gstreamer stuff but still no dice ;(.

Any ideas?

-SMRT

---

### Post by Tom--d on 2008-06-20
You do not need everything to be Pulseaudio.

I only have Music at auto dectec for emesene. and the rest alsa.

Also, install libflash-support in apt-get. It uses pulseaudio for flash.

Banshee not playing m4a's.
Thats an easy one.
Go to Add/Remove, search for gstreamer and install the right codec (in fact, just install them all. Then you will need no more codecs :D)

---

### Post by I[AM]SMRT on 2008-06-25
I've got all the gstreamer plugins installed =/.

EDIT: And I just tried using your sound preferences (auto-detect for music, rest alsa) and now I can't get sound to work with banshee and flash anymore, even when I put it back to what I had =/.

EDIT: Got flash + music working at the same time again, back to square one.

---

