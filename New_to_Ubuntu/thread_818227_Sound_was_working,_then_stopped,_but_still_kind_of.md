---
title: "Sound was working, then stopped, but still kind of works"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by HawkST on 2008-06-04
Basically my sound worked fine straight from install (compared with Fiesty, when it wouldn't work at all), but when Songbird told me I needed to install GStreamer or something for song playback, I tried to, and from what I could tell nothing went disastrously wrong, but since then (I assume it is from this, I can't think of any other triggers) my sound has been messing up.

The welcome sounds play about, but the volume control is stuck on mute (aka the lowest level) and any attempts to edit it give the error "No volume control GStreamer plugins and/or devices found."

Whats wrong? And how can I resolve this - maybe reset my sound settings?

---

### Post by ph1 on 2008-06-04
First, go into synaptic, and uninstall gstreamer, and reinstall it.  Synaptic will let you know what other dependencies are necessary.  While you're in synaptic you might want to look at some of the plugins associated with gstreamer, too, to see if any might be useful to you.  If that doesn't work, you can try reinstalling alsa, which is a bit more of a pain.  Post back with more information if you can't get it to work.

---

