---
title: "xhost issue"
date: 2019-03-25
forum: New to Ubuntu
---

### Post by imaclean78 on 2019-03-25
Hi,
I've managed to mess up my Xhost settings and cant figure out how to fix it.

Initially I had remote desktop working on my linux box (18.04) with no issues with my main account.
I decide to create a second user with desktop and ran:

```
xhost +SI:localhost:<SECOND USER>
```

This didnt work so after some fruitless attempts to diagnose/fix it, i flipped back to my main account and discovered that no longer worked either.

In addition, even running just "xhost" I get:
```

$xhost
xhost:  unable to open display ":0"

```
Any help would be greatly appreciated...
Thanks
Iain

---

### Post by imaclean78 on 2019-03-26
Actually it looks like Xorg isn't running...
Odd prior to the change was running at start up

---

