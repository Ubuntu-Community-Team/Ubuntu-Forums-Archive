---
title: "Completely uninstall/remove codecs ?"
date: 2008-04-12
forum: Other OS Talk
---

### Post by younity on 2008-04-12
Hi,

I'm having some issues with multimedia codecs, since I tried, but probably failed to install some xine codecs. Basically, no matter the software used, Mplayer, VLC, etc, I got the sound but no video ; 

[http://img391.imageshack.us/my.php?image=screenshotmplayervideouz8.png](http://img391.imageshack.us/my.php?image=screenshotmplayervideouz8.png)

Is there a way to completely remove screwed codecs, or request default configuration ?

PS : I'm using Linux Mint.

Thanks

---

### Post by LaRoza on 2008-04-12
Doesn't Linux Mint have them by default?

You can uninstall them from Synaptic.

---

### Post by Tomatz on 2008-04-12
Doubt it's a codec problem then as VLC has its own codecs independent of the other media players. 

Try this:

Open **vlc**

**Preferences**

Check **"advanced options"** (bottom r/h)

Dropdown **"video"** (l/h pane)

Click **"Output modules"**

Change form "default" to **"X11"**

**OK**

Play a video ;)

It should work now although you wont get as good quality video as using XV (default).

---

### Post by younity on 2008-04-12
Thank you for your replies.

LaRoza : the issue is fixed now, using VLC only, thanks !

But still, I don't wanna use VLC, and it doesn't resolve the whole thing. Mint came up with every codecs installed by default till I messed it up.

Any other idea ?

---

### Post by Tomatz on 2008-04-12
> **younity said:**
> Thank you for your replies.

LaRoza : the issue is fixed now, using VLC only, thanks !

But still, I don't wanna use VLC, and it doesn't resolve the whole thing. Mint came up with every codecs installed by default till I messed it up.

Any other idea ?

If my fix solved the problem, Then it's not a codec issue. The problem is to do with compiz.

The only workaround i have found is using x11 other that xv unfortunately totem (to my knowledge) doesn't allow you to change the video output mode. So you will have to install mplayer as mplayer does.

I have this problem on my eeepc and nothing else seems to work. Even the compiz video playback plugin is next to useless :(

---

