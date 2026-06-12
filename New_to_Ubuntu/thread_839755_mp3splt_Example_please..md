---
title: "mp3splt Example please."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by hossiam on 2008-06-24
OK I am not too sure how to use terminal apps.   But I would like to try to use mp3splt for my podcasts.   Can someone write me a sample based on my example.

home/*username*/music/funpodcast.mp3

I would like to split into 5 minute intervals.

Also how/can I add to my Scripts menu when I right click the podcast I would like to split.

I am using 8.04.

Thanks.

---

### Post by milosz.galazka on 2008-06-24
Maybe something like this:
```
mp3splt -t 5.00 file.mp3
```
You probably want do this in separate directory..

[More examples]("http://mp3splt.sourceforge.net/mp3splt_page/documentation/man.html#lbAF")

---

### Post by hossiam on 2008-06-25
Thank you.  This is perfect.  It took under a minute to split a 4 hour show.  It seems like it's in the original condition.  Perfect thanks again.

---

