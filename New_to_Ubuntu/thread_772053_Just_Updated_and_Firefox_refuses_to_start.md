---
title: "Just Updated and Firefox refuses to start"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by AmandaKerik on 2008-04-28
The error I get is:
Firefox is already running, but is not responding, please shut down Firefox or restart your computer.
This happens for:
GUI accessed Firefox
Shortcut accessed Firefox (both default and beta on a different partition)
Command line accessed Firefox

I'm in Opera right now, and I need my Greasemonkey (enter dramatic sob here).

Any suggestions?

---

### Post by PartisanEntity on 2008-04-28
The obvious question, did you try restarting?

---

### Post by rockerphil on 2008-04-28
here's what i'd do. open up your terminal and run this code

ps -A

then look for the Firefox processes and then use this

sudo kill <process #s>

---

### Post by skymera on 2008-04-28
or type

```
 killall firefox 
```

If it still doesn't work after, run Firefox from the Terminal and post the output of the errors.

---

### Post by muteXe on 2008-04-28
I went into the repos and installed FF2.  I didn't like how 8.04 came with FF3 beta.  Annoyed me that did.

---

### Post by alienexplorers on 2008-04-28
If after trying to kill firefox it still does not load try entering in terminal:
> firefox -profilemanager
setup a new profile and then try to load firefox.

---

### Post by DezSP on 2008-04-28
> **skymera said:**
> or type

```
 killall firefox 
```

If it still doesn't work after, run Firefox from the Terminal and post the output of the errors.

Actually, you want firefox-bin. :)

---

