---
title: "Flash not working in 8.04"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by handyguy33 on 2008-05-05
Hi all.

I recently installed Hardy Heron on a friend's computer. Everything seems fine except that I cannot get flash to work properly. I tried re-installing the flash plugin, taking firefox back to version 2, and using alternate plugins (swfdec, and Gnash) but it still plays flash poorly. The video is clunky and there's no sound. Nothing that I've tried has changed this. I then tried installing Opera and installed the flash plugin for that, but it gives me no video or sound at all. Is there something in 8.04 that doesn't deal well with flash? Any help is appreciated.

---

### Post by forumache on 2008-05-05
Yeah, it might be the pulseaudio thing. Try this:

Close Firefox. Type in a terminal: pulseaudio -k
This will kill pulseaudio. Restart firefox and go to a site with flash. Do you hear sound?

Please note that other applications which were using sound device before the command to kill pulseaudio need to be closed and reopened.

Good luck,
Dan.

---

### Post by corevette on 2008-05-05
> **forumache said:**
> Yeah, it might be the pulseaudio thing. Try this:

Close Firefox. Type in a terminal: pulseaudio -k
This will kill pulseaudio. Restart firefox and go to a site with flash. Do you hear sound?

Please note that other applications which were using sound device before the command to kill pulseaudio need to be closed and reopened.

Good luck,
Dan.

they talk about pulseaudio+flash on the ubuntu wiki
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
scroll down to the bottom where it says 'known issues'

---

### Post by pro003 on 2008-05-05
open your terminal and type this:

```
 sudo apt-get install ubuntu-restricted-extras
```

that worked for me :popcorn:

---

### Post by handyguy33 on 2008-05-05
Well, we've got sound now, thanks for the info. The video is a little choppy yet, but that may be a seperate issue (Geforce 400 mx and restricted drivers). Yea Ubuntu!

---

### Post by roderick on 2008-05-05
Is your video card doing any acceleration? Post the output of glxinfo  and look for Direct Rendering: Yes.

I have seen cases where an unaccelerated desktop can cause sluggish behaviour all around.

---

### Post by pro003 on 2008-05-05
I'm glad it worked... You're welcome.:popcorn:

---

### Post by handyguy33 on 2008-05-05
I'm not in front of the machine in question at the moment, but it sounds like that's exactly what's happening. I'll try what you suggested tonight and give an update in the morning.

---

