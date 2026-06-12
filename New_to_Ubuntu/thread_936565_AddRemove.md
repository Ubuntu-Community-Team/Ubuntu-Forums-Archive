---
title: "Add/Remove"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by metsfan47 on 2008-10-02
Dumb question, sorry! If I add a game via add/remove, how do I run the game? Its not listed under games. Thanks in advance. 

-A

---

### Post by Bucky Ball on 2008-10-02
Is it listed under 'other' in the Applications menu?

---

### Post by metsfan47 on 2008-10-02
Nope, not anywhere under applications.

---

### Post by Bucky Ball on 2008-10-02
This happens to me sometimes also and I am figuring you are maybe missing some dependencies for the app you installed, therefore it is not showing. Maybe check what is needed to run it, may not have loaded with it automatically (not necessarily the case).

---

### Post by cardinals_fan on 2008-10-02
Try running the game from a terminal window (Accessories -> Terminal).

---

### Post by metsfan47 on 2008-10-02
I'm not sure how to use the terminal that well yet. Sorry.

---

### Post by cariboo on 2008-10-02
Game executables usually end up in /usr/games if you can't find it there, in a terminal type:

```
locate <gamename>
```

Where <gamename> = the name of the game. Once you locate it, you can manually add it to the menu, by right clicking on applications.

Jim

---

### Post by LowSky on 2008-10-02
sometimes a quick log-off will renew your applications menu, just type Ctrl+Alt+Backspace

---

### Post by 3rdalbum on 2008-10-03
My signature has the information you need - "Where did my installed program go".

---

