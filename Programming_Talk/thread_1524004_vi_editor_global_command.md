---
title: "vi editor global command"
date: 2010-07-04
forum: Programming Talk
---

### Post by yc2 on 2010-07-04
I am reading this tutorial on vi by Walter Alan Zintz
[http://www.networkcomputing.com/unixworld/tutorial/009/009.part3.html#section1](http://www.networkcomputing.com/unixworld/tutorial/009/009.part3.html#section1)

It says that this command may overflow your disk

```
[COLOR="Red"]WARNING THIS COMMAND MAY OVERFLOW YOUR DISK![/COLOR]
global /^Chapter [1-9]/ write >> t.of.contents
[COLOR="Red"]WARNING THIS COMMAND MAY OVERFLOW YOUR DISK![/COLOR]
```
I cannot understand why?

---

### Post by yc2 on 2010-07-04
Starting this thread maybe finally made me think clearly about the problem. I guess a dot is missing? (otherwise w will write the entire file, I never dared try it)

```
global /^Chapter [1-9]/ . write >> t.of.contents
```

---

