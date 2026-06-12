---
title: "Video Doesn't Play, Shows Garbled Afterimage of Desktop Instead"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by tsunamikitsune on 2008-05-16
Earlier, my video files seemed to work fine in Totem, but now they seem to be giving me trouble. I've tried playing the same video that worked originally (in Totem) on Mplayer, VLC, and Totem again, along with a few other video files. Each one gave me the same garbled mess:

[IMG]http://i47.photobucket.com/albums/f173/kitsune37/Screenshot-1.png[/IMG]

What could be the cause for this? I'm pretty sure I have the codecs I need, as Totem downloaded them for me when I first tried to play the video in it.

---

### Post by pytheas22 on 2008-05-16
If you're running desktop effects, turn them off and try watching the video again.  It's probably their fault.

---

### Post by tsunamikitsune on 2008-05-16
Nope, still looks messed up with Desktops Effects off. Also, when I first played a video, I had them on and it worked fine.

---

### Post by pytheas22 on 2008-05-16
Alright, then try creating a new user account, logging in under it and trying to play video there.  This will narrow the problem down to your local user configuration or a system-wide problem.

---

### Post by dca on 2008-05-16
Verify you're not running both gstreamer and xine engine...
 
...wait a minute, that's running in VLC...  It happens in Totem as well, I'm confused...

---

### Post by tsunamikitsune on 2008-05-16
> **pytheas22 said:**
> Alright, then try creating a new user account, logging in under it and trying to play video there.  This will narrow the problem down to your local user configuration or a system-wide problem.

Works fine under a new user. :(

---

### Post by pytheas22 on 2008-05-16
> Works fine under a new user.

At least we know where to look.  Try refreshing your xine configuration:
```

mv ~/.xine ~/.xine.backup
```

then try to play the movie again in mplayer or totem.  Any luck?

I'm not sure if xine is the right directory to move--it's probably not if the problem also exists in vlc--but if it's not that, I would suspect it's something related to either X or gnome, or maybe the .gstreamer-x.x directory.  If moving .xine doesn't work, you could try moving these other ones.

---

### Post by tsunamikitsune on 2008-05-16
Cool, it works now. Thanks a ton. :)

---

### Post by pytheas22 on 2008-05-17
I'm glad to hear it works.  For the benefit of anyone else who finds this thread, which folder did you end up renaming to solve the problem?

---

### Post by tsunamikitsune on 2008-05-18
I just used the exact line you gave me in the terminal and everything worked fine.

Unfortunately, it's broken again and that doesn't seem to be working anymore...

---

### Post by pytheas22 on 2008-05-18
That's strange.  What about:
```

rm -r ~/.xine*
```

If that still doesn't work, try to open a video in mplayer:
```

mplayer -v /path/to/video
```

and see if it dumps any information to the terminal about what's wrong.

---

