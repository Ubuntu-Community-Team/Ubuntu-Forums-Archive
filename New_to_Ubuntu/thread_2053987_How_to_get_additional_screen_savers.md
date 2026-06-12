---
title: "How to get additional screen savers?"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by sremick on 2012-09-06
First experience with Xubuntu... liking the UI much better than the direction Ubuntu has gone. Am setting this up for another user, not myself... transitioning her away from Vista. I expect she's going to be very happy. This is also giving me an opportunity to learn Xubuntu.

I've solved numerous issues, finding my own solutions via Google and searching these forums. This one stumps me, though: How do you get additional screen savers installed? I understand why Xubuntu only includes a couple and I'm not criticizing this... but almost all of the ones listed are grayed-out and say "not installed" when you click on them (and the ones included aren't even some of the better ones). So I'd like to install the rest of the list. I've searched the Software Center, these forums, and on Google to no avail. Help?

---

### Post by critin on 2012-09-06
In the Software Center I searched for "screensavers" and found "GL(Mesa) screen hacks for xscreensaver".  I'm on ubuntu ATM, but it should be the same in Xubuntu, perhaps not.  I don't use them in my xubuntu so haven't searched from there.

The owners website is available from there if you want to check it out.
[http://www.jwz.org/xscreensaver/](http://www.jwz.org/xscreensaver/)

---

### Post by pqwoerituytrueiwoq on 2012-09-06
```
sudo apt-get install xscreensaver-gl xscreensaver-gl-extra xscreensaver-data xscreensaver-data-extra rss-glx;killall xscreensaver;rss-glx_install;xscreensaver -nosplash &; exit
```
that will get you all but a couple screensavers

---

