---
title: "no youtube sound"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-01
self-explanatory; i get no sound in youtube(and probably elsewhere, too). i u=se opera 9.5b, perhaps it is a development issue? also, the video is extremely choppy; not used to that.

---

### Post by mmb1 on 2008-05-01
Try to get sound off the internet, and try it on the internet with a different browser.

---

### Post by damis648 on 2008-05-01
Install the package libflashsupport

That fixed it for me :)

---

### Post by Afkpuz on 2008-05-01
I got nothing for your video problem, but might be able to help your sound problem. 


Do you have more than one sound card, or maybe an on-board sound card and a pci sound card?  If so, try this:

Open a terminal and paste in:
```
asoundconf list
```

It should list all the sound cards on your system.  Take note of the name of the sound card you want to use.


Then, paste this into the terminal:
```
asoundconf set-default-card cardname

```
Where "cardname" is replaced with the case-sensitive name you got from the first step.

Press Ctrl+Alt+backspace to log out and then log back in.  See if that helps.


This usually just happens when flash defaults to your other sound card, so the above changes your default system card.  I know it happens to me on fresh installs even when system sounds play.

---

