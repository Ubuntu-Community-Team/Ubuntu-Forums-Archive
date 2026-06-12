---
title: "Opera &amp; Quicktime"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Sinkingships7 on 2008-06-14
I would like to switch over to Opera. The only thing stopping me from making a full switch is not being able to play embedded video (not flash), such as Quicktime.

How do I get this working?

I'm running Opera 9.5

---

### Post by Sinkingships7 on 2008-06-15
bump

---

### Post by FreewheelinFrank on 2008-06-15
Opera seems to use the Mozilla Mplayer plug-in.

Try installing Mplayer and the Mozilla plug-in from Synaptic.

---

### Post by gandaran on 2008-06-15
> **Sinkingships7 said:**
> I would like to switch over to Opera. The only thing stopping me from making a full switch is not being able to play embedded video (not flash), such as Quicktime.

How do I get this working?

I'm running Opera 9.5

probably the easiest way is to just copy the player plugin to a plugin folder where opera looks for it, that will be /usr/lib/mozilla/plugins or better, /usr/lib/opera/plugins, this way it won't be shared with firefox.
now about the plugin, opera does not work with the totem plugin, but works with others, works fully with the xine plugin (only disappointment is that xine doesn't have a control bar), works with mplayer plugin, only problem is it will play in a very small window, but there are many others I haven't tried yet.
so just install the plugin of your choice, find where it's installed, copy all the plugins files to the opera plugins folder and uninstall/remove completely the the plugin again, so it won't mess up with your other installed firefox plugin.
I have three browsers installed, firefox , opera and flock, firefox uses the totem/gstreamer plugin, opera the xine plugin, and flock mplayer plugin!

edit:
if you just  remove the totem plugin and install mplayer or other plugins I think opera  will work, you don't have to  copy the plugins, the same plugin will be shared for all browsers.

---

### Post by Sinkingships7 on 2008-06-15
> **FreewheelinFrank said:**
> Opera seems to use the Mozilla Mplayer plug-in.

Try installing Mplayer and the Mozilla plug-in from Synaptic.

This seemed to work out fine, for the most part. However, is there any way I could view a video like this one? [http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html](http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html)
It asks me to download Quicktime, although streaming videos play fine, like the movie trailers.

---

### Post by FreewheelinFrank on 2008-06-15
If I'm not mistaken, that page will only pass on the movie if it detects the presence of Quicktime.

---

### Post by Sinkingships7 on 2008-06-15
> **FreewheelinFrank said:**
> If I'm not mistaken, that page will only pass on the movie if it detects the presence of Quicktime.

That's what I noticed. The Totem plug-in for Firefox handles it well...

---

### Post by FreewheelinFrank on 2008-06-15
Nothing with the MPlayer plug-in. :confused:

---

