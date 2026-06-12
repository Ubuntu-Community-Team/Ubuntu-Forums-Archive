---
title: "problem with wget - download a file that changes location....?"
date: 2010-07-31
forum: Programming Talk
---

### Post by hakermania on 2010-07-31
Ok, let's say that I want to download a file every five minutes to my computer.
So, I have
```
a=1; while [ "$a" -eq "1" ]; do wget download_link; sleep 300; done
```The problem is that the hoster seems to change the download location of the file each time. What can i do for this in order to download the same file each time?

P.S.: Don't ask me to change hoster. I have reason.:)

---

### Post by ghostdog74 on 2010-07-31
you have to parse the javascript to get that link, which you might have to use more advanced stuff like ajax, spidermonkey  etc...

---

