---
title: "xmodmap to remove Caps Lock"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by jeremymiles on 2008-05-18
Hi All,

I've been trying to run xmodmap to disable my caps lock key.  There are quite a few web pages which describe how to do this ([here's one]("http://www.ubuntugeek.com/disable-and-enable-caps-lock-in-ubuntu.html")), and they all say to open a terminal and write:
[FONT="Courier New"]
xmodmap -e “clear Lock”[/FONT]

But when I do that (including if I sudo it), it says:
[FONT="Courier New"]
xmodmap:  unknown command on line commandline:1
xmodmap:  unable to open file 'Lock”' for reading
xmodmap:  2 errors encountered, aborting.

[/FONT]

I can't seem to find anyone else who has had that problem.  Any hints or advice?

Thanks,

Jeremy

---

### Post by jeremymiles on 2008-05-18
Geez, I'm so stupid I scare myself.

I looked at that post, and realized that the quotes were changed from " to &#8220;&#8221; in the formatting of the web page, which I copied and pasted from.  

Oh well, if anyone makes the same mistake, they'll see the solution.

Jeremy

---

