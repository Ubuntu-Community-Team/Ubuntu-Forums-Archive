---
title: "problems viewing online videos"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-12-01
Thanks for reading

I have recently updated to 8.10 and since then i have been able to view very little online media. I can view the very popular site videos such as youtube, but not much else - at all!

For example before i upgraded i could watch programs on the following website (channel 5 gadget show)

[http://fwd.five.tv/videos/top-5-video-games]("http://fwd.five.tv/videos/top-5-video-games")

And now the screen just says 'player loading' for ever. 

The same thing happens on other sites, and on some the content plays, but the controls are not visible (volume, play/pause etc)

Has anyone else had this problem? is it as simple as downloading a package? 

Cheers

Mckenzie

---

### Post by phantomjoker on 2008-12-01
This is what i have tried so far -

[LIST]
[*]vlc media player - firefox pluggin
[*]gnash - firefox pluggin
[*]windows media pluggin - couldn't install it - didn't think i could
[/LIST]

What else could i try?

---

### Post by fooman on 2008-12-01
those are flash videos.

open synaptic (system > administration > synaptic package manager) and uninstall any gnash items you have installed.

then search for and install both "flashplugin-nonfree" and "ubuntu-restricted-extras".

see if that helps.

---

### Post by slinkey1981 on 2008-12-01
It sounds like you need the mplayer plugins for mozilla. I'm not sure what the correct package names are, but I'll look into it and edit this post.

Edit: wow, who would have thought the mozilla mplayer plugin is called 'mozilla-mplayer'

---

### Post by phantomjoker on 2008-12-01
> **fooman said:**
> 

 "flashplugin-nonfree" and "ubuntu-restricted-extras".



neither worked... sorry

---

### Post by phantomjoker on 2008-12-01
and the mozilla-mplayer didnt either :|

---

