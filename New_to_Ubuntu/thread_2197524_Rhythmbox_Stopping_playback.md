---
title: "Rhythmbox: Stopping playback"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by pat4 on 2014-01-04
Hi, Perhaps this is going to sound a little odd but I need some help with stopping playback in Rhythmbox..   I'm using Ubuntu 12.04 - Precise Pangolin - and have a problem after I have lanched an MP3 file in Rhythmbox. The program launches OK and plays fine. I am able to pause playback, fast forward and reverse, change tracks etc.. but cannot for the life of me find any way of stopping playback completely. Right-clicking the icon in launcher  I am oferred various options in cluding "quit".  Clicking this has no effect whatsoever.   I am left with music playback and seemingly the only way of stopping this is to remove the entire playlist. I suspect I am missing something obvious but having tried to find a solution I am needing a bit of help here!  I am sorry if this "problem" is a result of "newbie error" but any and all help would be appreciated.  Many thanks.. Pat.

---

### Post by tea for one on 2014-01-04
No, I do not think that you are missing anything obvious.

Rhythmbox does not have a "stop" button now. I think that it did have one in earlier iterations.

I simply use "pause" and "quit"

Having said that, I do not use Unity, so I am not familiar with all the options in the launcher.

---

### Post by pat4 on 2014-01-06
Thank you for that... At least I know I am not missing something.  Kind regards...  Pat.

---

### Post by efflandt on 2014-01-06
Note that if you close out Rhythmbox (hit X) while it is playing, you can still control it by right clicking the speaker icon at top of screen. You can also open Rhythmbox from there.

---

### Post by kostkon on 2014-01-06
> **pat4 said:**
> Hi, Perhaps this is going to sound a little odd but I need some help with stopping playback in Rhythmbox..   I'm using Ubuntu 12.04 - Precise Pangolin - and have a problem after I have lanched an MP3 file in Rhythmbox. The program launches OK and plays fine. I am able to pause playback, fast forward and reverse, change tracks etc.. but cannot for the life of me find any way of stopping playback completely. Right-clicking the icon in launcher  I am oferred various options in cluding "quit".  Clicking this has no effect whatsoever.   I am left with music playback and seemingly the only way of stopping this is to remove the entire playlist. I suspect I am missing something obvious but having tried to find a solution I am needing a bit of help here!  I am sorry if this "problem" is a result of "newbie error" but any and all help would be appreciated.  Many thanks.. Pat.
When Rhythmbox is playing or is paused but the play queue has at least one song in it, then if you close its window it actually minimises/closes in the sound indicator (speaker icon), it doesn't quit. You can then bring it up again by selecting its entry in the sound indicator. So you don't really need to have its icon in the launcher at all, you can control it that way, like any other player that supports MPRIS (in Gnome-Shell as well).

On the other hand, if the play queue is empty and you aren't currently playing any song and you close its window then Rhythmbox quits.

Hope that helps.

---

