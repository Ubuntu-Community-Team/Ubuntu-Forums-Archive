---
title: "CSS &amp; position:fixed;"
date: 2009-08-14
forum: Programming Talk
---

### Post by Tux.Ice on 2009-08-14
I have a small problem, with using CSS and position:fixed; on a login bar. What I am trying to do, is have this login bar be well, fixed. However, when I scroll down over any text that is being written with javascript, or has javascript attached to it in some way (via jQuery, the example in the screenshot is a news feed that scrolls through 3 feeds)

Does anyone have a solution?

[http://imgur.com/kg0py.png](http://imgur.com/kg0py.png)

---

### Post by gjoellee on 2009-08-14
I am quite tired, so I am a little confused about your post. You can try to use this.
```

position:absolute;
left:100px;
top:150px;
```

---

### Post by jeffathehutt on 2009-08-14
Check out the z-index property of the login bar.  A higher z-index will make sure it is always on top of the other text.

---

### Post by Tux.Ice on 2009-08-14
Thank you very much, that fixed it.

---

