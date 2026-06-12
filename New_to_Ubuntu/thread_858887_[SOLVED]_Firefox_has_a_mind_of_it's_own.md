---
title: "[SOLVED] Firefox has a mind of it's own"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by BLTicklemonster on 2008-07-14
Whenever I open Firefox, it opens to this page

[http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)

Even though I have already changed preferences to make my home page a different one.

Checking open a blank page doesn't help either.

---

### Post by aysiu on 2008-07-14
Maybe ```
sudo chown -R *username*:*username* ~/.mozilla
``` might fix it?

---

### Post by BLTicklemonster on 2008-07-14
lmao nope. I even closed firefox before I ran that.

---

### Post by aysiu on 2008-07-14
After you run that command and restart Firefox, you have to try to change the home page preference yet again.

---

### Post by BLTicklemonster on 2008-07-14
Wait a minute.

I'm in icewm, and I edited my toolbar to this

```
prog    "Firefox" /usr/share/pixmaps/firefox-3.0.png firefox firefox
```

and when I click on it, I get that page.

BUT

when I right click on the desktop and bring up my menu, which is edited like this:

```
prog "Mozilla Firefox" /usr/share/pixmaps/firefox.png firefox
```

I don't get that page.


*Edit:

Edited out the second firefox in my toolbar, and it's gone.

```
prog    "Firefox" /usr/share/pixmaps/firefox-3.0.png firefox
```

Dangedest thing I ever seen.

---

### Post by aysiu on 2008-07-14
It actually makes sense. You have an extra *firefox*, which probably asks it to launch Firefox with the webpage *firefox*, so maybe it does a search for Firefox and gets the Firefox homepage?

---

### Post by BLTicklemonster on 2008-07-14
That sounds reasonable.

Thanks for hopping on this right away :)


(is it appropriate to hit the thanks icon in situations like this?)

---

