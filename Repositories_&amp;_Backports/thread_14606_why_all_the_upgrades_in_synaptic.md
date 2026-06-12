---
title: "why all the upgrades in synaptic"
date: 2005-02-08
forum: Repositories &amp; Backports
---

### Post by sharkzf6 on 2005-02-08
OK, next dumb question (still a newb). Why are there so many upgrades in synaptic? Should I perform them? I hesitate cause I don't want to bork my system since it's all working properly (exept for that damn Totem...Ugghhh...).

---

### Post by landotter on 2005-02-08
[QUOTE=sharkzf6]OK, next dumb question (still a newb). Why are there so many upgrades in synaptic? Should I perform them? I hesitate cause I don't want to bork my system since it's all working properly (exept for that damn Totem...Ugghhh...).[/QUOTE]

I'd go ahead and do them all, unless you're on dial up and don't want to waste the time.

Do install totem-xine which will replace the Totem back-end. Then go to the mplayer site and get the package of basic codecs. Unpack them with file-roller and point Totem to the codecs in the preferences. You should now be able to play nearly everything.

---

### Post by sharkzf6 on 2005-02-08
[QUOTE=landotter]I'd go ahead and do them all, unless you're on dial up and don't want to waste the time.

Do install totem-xine which will replace the Totem back-end. Then go to the mplayer site and get the package of basic codecs. Unpack them with file-roller and point Totem to the codecs in the preferences. You should now be able to play nearly everything.[/QUOTE] Nah....I got plenty of bandwidth...like I said, just didn't want to do anything that would bork the system after getting such a warm fuzzy feeling from everything working (including the 66.29 drivers with my 6800). Thanks again.

---

### Post by mendicant on 2005-02-08
For warty, definitely install upgrades, since they're security updates.  For hoary, you have to be a little more comfortable with something that isn't a stable release.

---

### Post by Jad on 2005-02-08
I'm not sure if its weird, but 
installing totem-xine will require to remove totem-gstreamer and ubuntu-deskop 
 is it safe to remove ubuntu-desktop?

---

### Post by landotter on 2005-02-08
[QUOTE=Jad]I'm not sure if its weird, but 
 installing totem-xine will require to remove totem-gstreamer and ubuntu-deskop 
  is it safe to remove ubuntu-desktop?[/QUOTE]
 
 strangely enough, yes. Ubuntu desktop just points to a bunch of other packages, it's in a sense a "metapackage". Once all the packages are installed, it's not really needed any more.
 
 Totem-xine replaces totem-gstreamer.

---

