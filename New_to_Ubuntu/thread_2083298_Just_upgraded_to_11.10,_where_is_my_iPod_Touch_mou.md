---
title: "Just upgraded to 11.10, where is my iPod Touch mounted?"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by pmooney78 on 2012-11-12
I just upgraded to 11.10 because I got a notification that I'll no longer get security updates for 11.04 if I don't upgrade. I won't mention all the things I hate about 11.10 here, but one thing I haven't been able to work out that is really bothering me: where is my iPod Touch being mounted?

Under 11.04 (and several earlier releases), it was mounted at "~/.gvfs/Patrick Mooney's iPod" -- there was also another virtual mount at "~/.gvfs/Documents on Patrick Mooney's iPod". Now I just see a mount at "~/.gvfs/Documents on Patrick Mooney's iPod".

I really need to know a real mount point to plug in to preferences for gtkPod and gPodder. Any suggestions?

---

### Post by pmooney78 on 2012-11-12
Never mind. Installing ifuse solved the problem. Why ifuse was removed when I upgraded to 11.10, I have no ******* clue. Thanks, Canonical.

---

