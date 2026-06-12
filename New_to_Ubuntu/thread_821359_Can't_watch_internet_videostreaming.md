---
title: "Can't watch internet videostreaming"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by furoido on 2008-06-07
Can get radio and also sound on internet videostreaming, webcam, etc, but can't get any picture/image...always get a "transfering data from 'x' site", but nothing happens...anyone got any suggestions?

---

### Post by furoido on 2008-06-07
based on suggestions on another similar post, i tried to remove gnash and make sure flashplugin was installed...seems ok...any ideas what else it might be?


andrew@andrew-desktop:~$ sudo apt-get remove gnash swfdec
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
E: Couldn't find package swfdec
andrew@andrew-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Bubba64 on 2008-06-07
> **furoido said:**
> Can get radio and also sound on internet videostreaming, webcam, etc, but can't get any picture/image...always get a "transfering data from 'x' site", but nothing happens...anyone got any suggestions?

Go to add remove and install Ubuntu restricted extras, all the gstreamer stuff, and vlc. The restricted extras has the flash stuff in it and the gstreamer extras have a bunch of stuff that will read pretty much anything you come across. Also check out smplyer in add remove as an additional player beyond totem, vlc, and Mplayer. First though before you install any of these get medibuntu repository, this will give you some extras as well.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Good Luck

---

### Post by sailor2001 on 2008-06-07
if you are using firefox, look for the add-on "agent switcher"

---

### Post by billgoldberg on 2008-06-07
Could be a lot of things.

What internet streaming?

Flash?

Try install libflashsupport

For other kinds of video, install the mozilla totem plugin.

But first click on the link in my sig called "media and ubuntu" and install the medibuntu repo.

Then install

"non-free-codecs" and "ubuntu-restricted-extras".

Then you should be able to watch video streams.

You could also try the vlc mozilla plugin, if you have vlc installed.

---

