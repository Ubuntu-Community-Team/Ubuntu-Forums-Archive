---
title: "Where'd my music go?  Did RB eat it?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by w.g.hanna on 2008-11-30
I'm still running hardy, my first distro.  My primary music program is rhythmbox, but I also play around with banshee.  I have a large music collection.  I use both to listen to music and to manage my sansa fuze. my first indication i was having a problem was when i couldn't find my temple of the dog in either player.  I shrugged it off.  Maybe i never ripped it - but that wouldn't make sense.  But whatever.  But then I tried to look up a Rancid album I know I've listened to on my Fuze.  Couldn't find it on RB, and i got kind of panicked.  Is my music getting eaten?  Totally unacceptable.  

So I check on Banshee - and there it is.  

They're both directed at the same folder.  So what could be the deal?

---

### Post by Diabolis on 2008-12-01
Maybe those files appear under "Missing files", this happens when Rhythmbox doesn't recognize the type of files. That's because it needs extra libraries.

I had to install this ones:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad

```

I don't use Rhythmbox anymore tho, now Amarok is my choice number one.

---

