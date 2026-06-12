---
title: "how to install Firefox 3 RC1?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by djarcadian on 2008-05-17
How do I upgrade to FF 3 RC1?

---

### Post by macaholic on 2008-05-17
By replacing the /usr/lib/firefox-3.0b5 contents with the contents of the downloaded and extracted tar file. However, the ubuntu team might update it in the next couple of days anyhow, so I would suggest waiting until then.

---

### Post by djarcadian on 2008-05-17
I downgraded to FF2 because I was having problems with the beta. Will that change how I upgrade at all?

---

### Post by bodhi.zazen on 2008-05-17
> **djarcadian said:**
> I downgraded to FF2 because I was having problems with the beta. Will that change how I upgrade at all?

If you must have it :

[http://www.mozilla.com/en-US/firefox/all-rc.html](http://www.mozilla.com/en-US/firefox/all-rc.html)

Please note : Almost no extensions are working out of the box (extensions have not been ported yet). Same with themes.

Otherwise looks good (posting from ff3 rc1 now).

---

### Post by djarcadian on 2008-05-18
> **macaholic said:**
> By replacing the /usr/lib/firefox-3.0b5 contents with the contents of the downloaded and extracted tar file. However, the ubuntu team might update it in the next couple of days anyhow, so I would suggest waiting until then.

It won't let me delete the contents of that folder. How do I delete the contents of that folder?

---

### Post by shifty_powers on 2008-05-18
```
gksudo nautilus
```

in a terminal

---

### Post by war59312 on 2008-05-18
> **djarcadian said:**
> It won't let me delete the contents of that folder. How do I delete the contents of that folder?

ALT+F2 then enter in gksudo nautilus and click enter and then type in root pw

then browse to /usr/lib/firefox-3.0b5/ and now you can delete everything :)

---

### Post by bilbo.san on 2008-05-18
I am looking forward for this update too, but I would suggest to wait until the Ubuntu team releases it, hopefully they will, otherwise, it might get uncomfortable to make the FireFox and Thunderbird upgrades manually on every release.

---

