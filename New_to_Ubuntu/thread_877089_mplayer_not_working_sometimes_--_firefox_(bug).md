---
title: "mplayer not working sometimes -- firefox (bug)?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by koba101 on 2008-08-01
Hi,

I'm not sure if this is a bug or not....

Sometime if i sign in to gmail and stay signed on mplayer won't play at all (it just stays stopped)

The moment I sign out of gmail it works again.

Can i report this ?

---

### Post by alienexplorers on 2008-08-17
Sounds like you have a genuine problem there.  Report it to launchpad.

---

### Post by Yuki_Nagato on 2008-08-17
Could be PulseAudio.

You cannot run two "sound channels" in Ubuntu at one time with PulseAudio installed.  So playing something on Veoh.com and then starting up MPlayer will not work.  The first application monopolizes the channel until you shut it down.

I have no fix for it beyond uninstalling PulseAudio.  I have learned to live with it.

---

