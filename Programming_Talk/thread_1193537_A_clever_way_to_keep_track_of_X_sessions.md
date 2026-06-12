---
title: "A clever way to keep track of X sessions"
date: 2009-06-21
forum: Programming Talk
---

### Post by mikeym on 2009-06-21
Hi,

Does anyone have any clever ideas about how to keep track of X sessions? I've been working on a script to start games on a new session so that they don't interfere with compiz. I launches games with something like:

```
startx -- :1
```

and then a .xinitrc script to open a openbox session which it then opens a selected game in the virtual terminal screen :1.


However I'd like to be able to keep track of these sessions to see which X sessions are open so I can launch a game into an existing session or offer to open a new one. Unfortunately I've no idea how to tell which sessions are open. (I'd thought about trying to keep track of them with a daemon but I can't even determine the pid of X session to match the virtual terminal / screen.) 

I'd also like to watch the X session and close it if all the child processes have finished running. 

Any thoughts?

---

