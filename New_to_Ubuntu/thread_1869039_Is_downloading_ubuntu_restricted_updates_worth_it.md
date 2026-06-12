---
title: "Is downloading ubuntu restricted updates worth it?"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by Radical_Dreamer on 2011-10-25
So this program seems to be useful and highly rated but when I try to install it, it says that the libav codec library and libav utility library need to be removed.  Now, I know how to remove, them (just with the synaptic package manager right?) but should I bother?  Will this programs provide any useful codecs that these two won't or what?

---

### Post by satanselbow on 2011-10-25
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Tells you what is in the repo and how to install. If you do not need any of the functionality is brings don't install it ;)

---

### Post by ajgreeny on 2011-10-25
And don't forget that you can, and obviously have already installed everything the the restricted extras package brings in separately, and if so you may still not need it.  Some of ypur versions may even be newer that those this extras package needs, so if I were you I would not bother.

The properties of the package says
> Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio
files), and DVD playback. and all of that can be installed in packages manually.

I have just checked my system and I do not have that package installed but I can play anything and everything that is possible, having installed all the gstreamer packages, w32codecs from medibuntu, flash with the Flashaid plugin for firefox, and libdvdcss2 etc etc.  Using apt-get in my setup to install the package does not add any dependencies, so I have already got everything it would add.

---

### Post by 3rdalbum on 2011-10-25
> **Radical_Dreamer said:**
> So this program seems to be useful and highly rated but when I try to install it, it says that the libav codec library and libav utility library need to be removed.  Now, I know how to remove, them (just with the synaptic package manager right?) but should I bother?  Will this programs provide any useful codecs that these two won't or what?

There are two versions of the "libav" libraries; the regular ones and the "unstripped" ones.

ubuntu-restricted-extras removes the regular ones and installs the unstripped ones.

The Unstripped ones contain the extra codecs that might step on someone else's patents, or might not be licensed properly open-source.

So yes, it's definitely worth it.

---

### Post by Radical_Dreamer on 2011-10-26
Okay, so basically, after reading one of the links, I'm kind of given the impressions that this would allow me to play bluray, is that true?  Because then I guess there would be some incentive to get it but otherwise the other formats don't seem as neccessary

---

### Post by JRV on 2011-10-26
ubuntu-restricted-extras will not let you play Blu-rays, or DVDs.
To play DVDs you need libdvdcss2 and either w32codecs or w64codecs.
I don't know of a way to play Blu-ray.

ubuntu-restricted-extras includes:
[list]
[*]gstreamer codecs, good, bad, and ugly
[*]Flash
[*]MS core fonts
[*]Java
[*]UNRAR
[/list]

---

### Post by Radical_Dreamer on 2011-10-26
Alright, thanks everyone.  I guess I don't really need this thing then

---

### Post by sammiev on 2011-10-26
Use what works for you. If you decide you need them, then do install. Now you have a better understanding of what the ubuntu-restricted-extras do. GL :)

---

