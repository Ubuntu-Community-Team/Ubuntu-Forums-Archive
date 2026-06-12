---
title: "Updates"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by bigal1932flying on 2012-12-18
Most times when I start Ubuntu 12.10 I receive advice that there are Updates to be installed.
Every time there seems to be VLC updates included in the list.
Is this normal or do I have a problem with my VLC Software?

---

### Post by snowpine on 2012-12-18
Ubuntu is "open source" so you never need to guess about updates; you can see for yourself (and even read the source code if you know how!) exactly when each update was released and what it changed/fixed:

[http://changelogs.ubuntu.com/changelogs/pool/universe/v/vlc/vlc_2.0.4-0ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/v/vlc/vlc_2.0.4-0ubuntu1/changelog)

(Disregard if you have any 3rd-party software sources like the VLC PPA. :))

Another helpful command is:

```
apt-cache policy vlc
```

This will compare your installed version with the version(s) available in your software sources.

---

### Post by Sef on 2012-12-18
It could be normal if updates VLC are provided from the VLC community. Updates are usually for improved security or features.

---

