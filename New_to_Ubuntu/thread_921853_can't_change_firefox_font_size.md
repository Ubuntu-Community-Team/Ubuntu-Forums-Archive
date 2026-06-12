---
title: "can't change firefox font size"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by kukeluk on 2008-09-16
halloo all..
i've already fresh install my ubuntu..but i can't change my firefox font size..
thanks before!! :KS

---

### Post by beesthorpe on 2008-09-16
Edit > Preferences  opens the Firefox configuration options gui. Then the font settings are about half way down the "content"  window.  There is also an "advanced" button that allows you to set absolute minimums for font sizes that cannot be overridden by the website.  I use this set to 13px, but be aware that it can slightly mess up page layout.

---

### Post by OffAxis on 2008-09-16
In Firefox 3 (at least on Windows) it's:
**Tools-->Options-->Content-->Fonts and Colors** (in the middle of the page). There's also an 'Advanced' button if you want more specific control.

---

### Post by kukeluk on 2008-09-16
is not work i try to set the size until reach minimum size

---

### Post by beesthorpe on 2008-09-16
Hmm - I wonder if there's a rogue user style sheet setting.

This would be a file called userContent.css stored at  ~/.mozilla/firefox/xxxxxxxx.default/chrome/

(where "~" represents your user's home directory and "xxxxxxxx" represents a random string of 8 characters. The dot means the file is usually hidden - View > Show Hidden Files will make Nautilus display them.)

If this file exists you could try renaming it to  userContent.css.copy or something and restarting Firefox.

---

