---
title: "Changing monospace font"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by O-pos on 2008-05-21
Hello,

I would like to install pragmata ttf as a default monospace font on my computer. Is it possible on Ubuntu?

---

### Post by HotShotDJ on 2008-05-21
> **O-pos said:**
> Hello,

I would like to install pragmata ttf as a default monospace font on my computer. Is it possible on Ubuntu?Yes.





Oh.. I suppose you want to know HOW? :lolflag:

Sorry.... punchy today.... anyway, place the TTF file in ~/.fonts.  Now, open a terminal and type:```
sudo fc-cache -fv
```Next, go to System --> Preferences --> Appearance --> Fonts.  Change Fix Width Font to your new choice.

---

