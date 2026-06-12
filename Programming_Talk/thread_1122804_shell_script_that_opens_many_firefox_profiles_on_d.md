---
title: "shell script that opens many firefox profiles on different desktops?"
date: 2009-04-11
forum: Programming Talk
---

### Post by aaronLund on 2009-04-11
Hi all.
I'm trying to write a shell script that will open all of my firefox profiles and put them on a different desktop.  (I have Compiz set to give me 6).

Anyway, so far I have this and it's not really working.  (i.e. All of my named profiles do not open).

```
#!/bin/sh
firefox -no-remote -P "clean_firefox"
firefox -no-remote -P "devkit"
firefox -no-remote -P "Plug_ins_o_plenty"
firefox -no-remote -P "scanners"
firefox -no-remote -P "Audio
```

I'm not too sure why this isn't working (besides the fact that I'm a noob), but does anybody know how I could get it to work and have every profile open on a different desktop?  

Many thanks.

---

