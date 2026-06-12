---
title: "[SOLVED] Lost Main Menubar while in Firefox"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-10-31
I'm in intrepid Ubuntu: I lose the main menubar (i.e. Applications Places System) when in Firefox. How can I restore it? I want it there all the time.

---

### Post by ethoxyethaan on 2008-10-31
You might be in fullscreen, try pressing F11 in firefox to restore it,

also try to be more specific with your problem, perhaps a screenshot can help.

---

### Post by Ludwig9 on 2008-10-31
> **ethoxyethaan said:**
> You might be in fullscreen, try pressing F11 in firefox to restore it,

also try to be more specific with your problem, perhaps a screenshot can help.
I was not in full screen, but by pressing F11 I went into fullscreen and then by pressing it again I came out of fullscreen and had the main menubar, just like I wanted. Thanks.

---

### Post by raedq on 2008-12-02
> **Ludwig9 said:**
> I was not in full screen, but by pressing F11 I went into fullscreen and then by pressing it again I came out of fullscreen and had the main menubar, just like I wanted. Thanks.

Here is a fix I found... Worked well for me... Good luck :)

- Close FF
- Open a terminal and write: metacity --replace &
- Reopen FF
- in terminal: compiz --replace &
- close terminal
 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220443](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220443)

---

### Post by raedq on 2008-12-02
> **raedq said:**
> Here is a fix I found... Worked well for me... Good luck :)

- Close FF
- Open a terminal and write: metacity --replace &
- Reopen FF
- in terminal: compiz --replace &
- close terminal
 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220443](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220443)

Apparently here it is:

On CompizConfig>Utility>Workarounds
Disable the first option(Legacy Fullscreen support)

---

### Post by Ludwig9 on 2008-12-02
> **raedq said:**
> Here is a fix I found... Worked well for me... Good luck :)

- Close FF
- Open a terminal and write: metacity --replace &
- Reopen FF
- in terminal: compiz --replace &
- close terminal
 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220443](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/220443)
I did this and it is a lot better, but it still goes out sometimes. By clicking F11 I can bring it back.

---

### Post by LowSky on 2008-12-02
> **raedq said:**
> Apparently here it is:

On CompizConfig>Utility>Workarounds
Disable the first option(Legacy Fullscreen support)

This works wonders, I did it a while back and it saved me a lot of frustration

---

### Post by Ludwig9 on 2008-12-02
> **LowSky said:**
> This works wonders, I did it a while back and it saved me a lot of frustration
Would you please explain how to get to CompizConfig? I like watching wonders work.;)

---

