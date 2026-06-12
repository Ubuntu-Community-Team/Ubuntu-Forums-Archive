---
title: "Best way to migrate from mint 10 to 12.04?"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by memyselfnie on 2013-01-17
I am about to update my wife's computer from mint 10 to ubuntu 12.04. Basically, just wanna be sure there are no problems before I actually try anything, but she really only uses Thunderbird.  Going to back her home directory up first, but my question is, is there a way to just upgrade, or should I just wipe it all out, and do a clean install.  Also, what is the best way to handle ownership (and file permissions)?

---

### Post by ajgreeny on 2013-01-17
Mint 10 was based on Ubuntu 10.10, so you could not do a simple, single process update to Ubuntu 12.04, even if the cross-distro problem allowed that to happen; you would need to go from 10.10 to 11.04, then 11.04 to 11.10, then finally 11.10 to 12.04.

You will need to do a clean installation.  The base code for those two distro versions is so very different (gnome 2 to gnome 3, and gtk2 to gtk3) that it is what I would have suggested anyway, even if going from 10.04 to 12.04.

---

### Post by sidzen on 2013-01-17
@ajgreeny -- OP cannot leave /home intact and not format on install?  Seems to me the FS would have more impact than the version of Gnome.  Just wondering.

---

### Post by ajgreeny on 2013-01-17
> **sidzen said:**
> @ajgreeny -- OP cannot leave /home intact and not format on install?  Seems to me the FS would have more impact than the version of Gnome.  Just wondering.
Not sure what you're asking or saying here.

---

### Post by snowpine on 2013-01-17
Curious if you have read this page yet? (first google hit for "mint upgrade")

[http://community.linuxmint.com/tutorial/view/2](http://community.linuxmint.com/tutorial/view/2)

It will walk you step-by-step through the various upgrade methods, explaining the pros and cons of each. :)

---

### Post by tlhIngan on 2013-01-17
I always recommend a fresh reinstall.
Backup your files somewhere and reformat.

---

### Post by sidzen on 2013-01-17
That's one cool backup utility Mint has and snowpine points out!
Forget my previous post -- it's not relevant.

---

### Post by ajgreeny on 2013-01-18
No I did not read that article on updating Linux Mint to a newer version.  I did not even consider doing that as the OP wanted to update from Mint 10 to Ubuntu 12.04, so not even to a newer version of Mint.

In any case, I have always preferred to clean install rather than carry out a distro upgrade, and a jump from the 10.10 equivalent to 12.04 would surely not be worth the risk.

You may, of course feel differently.

---

### Post by memyselfnie on 2013-01-20
Thank you all, did wind up doing a clean install.  Used the backup software included with 12.04, which turned out excellent, with no problems.:guitar:

---

