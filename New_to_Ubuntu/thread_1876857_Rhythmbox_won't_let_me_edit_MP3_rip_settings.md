---
title: "Rhythmbox won't let me edit MP3 rip settings"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by John Peschken on 2011-11-06
I decided to fire up Rhythmbox today and see if I like it better than I did before.  It is giving me a bit of trouble.

I select Edit-Preferences-Music tab, and I can set the "Preferred Format" to "MPEG Layer 3", "Ogg Vorbis", or "MPEG4 Audio".  There is a mysterious fourth option on the list with no title.  The "Settings" button is grayed out no matter what I select.

I would expect to see at least FLAC on this list, but it's not there.  I have tried un-installing and re-installing the Ubuntu Restricted Extras and Rhythmbox but that has not helped.  I'm thinking that maybe I have a bad configuration file somewhere that persists, but I do not know where to look for that.  Maybe it is something else entirely.  I am out of ideas, so I need help from one of you experts.

By the way, Banshee works fine, so the trouble would seem to be RB specific.

Thanks,

John

---

### Post by John Peschken on 2011-11-26
It turns out this is a known bug (879535) I found on Launchpad.  The priority is low, so apparently they feel ripping is not important.  I suppose that's true since there are so many other programs you can use THAT ACTUALLY WORK!

As I understand it, the problem is going to be solved with Pangolin.

---

### Post by muffinresearch on 2012-01-03
> **John Peschken said:**
> It turns out this is a known bug (879535) I found on Launchpad.  The priority is low, so apparently they feel ripping is not important.  I suppose that's true since there are so many other programs you can use THAT ACTUALLY WORK!

As I understand it, the problem is going to be solved with Pangolin.


Fwiw the bug is 879525 [1] 

[1] [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/879525](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/879525)

---

