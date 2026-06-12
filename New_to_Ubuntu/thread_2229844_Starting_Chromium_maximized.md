---
title: "Starting Chromium maximized"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by ViliX64 on 2014-06-15
Every time I start chromium, it's streched over the whole screen, but it's not maximized. I've already changed my menu shortcut to:
```
chromium-browser %U --start-maximized
```

but it still launches only streched and not maximized.

---

### Post by texpat on 2014-06-15
Well, according to this: [http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/) you get:

```
--start-maximized
--start-fullscreen
```

---

### Post by ViliX64 on 2014-06-15
Even --start-fullscreen doesn't work. It's still the size of the screen, but it's now maximized so there is a bit more space at the borders.

---

### Post by texpat on 2014-06-15
Hmm... bummer. I tried it an also had issues, but I thought it may have to do with my flaky dual screen setup. You running more than one screen?

There's always

```
--window-position: Specify the initial window position: --window-position=x,y

and

--window-size: 	Specify the initial window size: --window-size=w,h
```

I suppose that could do as a work-around (*if* it works).

---

### Post by ViliX64 on 2014-06-15
I don't think so, the window is already streched to it's full limits, but it's not maximized.

[ATTACH=CONFIG]253968[/ATTACH]
I find difference between those two. The first one is not maximized and the second one is. The first one is the default one.

---

### Post by texpat on 2014-06-15
Yes, you're right, of course. I misread your previous post.

So using maximum x and y is not the same as maximize. But only by about 2 pixels... But I suppose you wouldn't be asking if it weren't important ;-)

To me it looks like there's a bug, then. There may be a possiblity to emulate a mouse click on the maximize icon? Sounds like overkill to me though.

---

### Post by ViliX64 on 2014-06-16
That might be too hard to implement to solve this small issue. But it's at leat an idea. Thanks.

---

