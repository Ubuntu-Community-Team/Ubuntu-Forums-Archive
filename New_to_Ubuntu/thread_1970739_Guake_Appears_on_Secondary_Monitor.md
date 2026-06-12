---
title: "Guake Appears on Secondary Monitor"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Darkness Des on 2012-05-01
I recently switched over from Windows back to Ubuntu, as multi-monitor support had finally been perfected (fantastic job on that, by the way. Never going back to Windows again) and was getting all of my usual applications set up when I got to Guake.

Whenever I hit the key to open it, it appears on the left (secondary) monitor. I wish for it to appear on my right (primary) laptop monitor. Screenshot of issue included.

Thanks in advance!

---

### Post by vedmar on 2012-10-25
Hi, did you resolve this issue?

I found possible solution on this link 
[http://charliedavi.tumblr.com/post/21263884848/how-to-get-guake-terminal-running-on-dual-monitors]("http://charliedavi.tumblr.com/post/21263884848/how-to-get-guake-terminal-running-on-dual-monitors")

but it doesn't work for me...maybe it will for you.

It seems that Guake will appear on second monitor only if second monitor is positioned up, which causes some other issues for me.
So I would like it to appear on the right positioned monitor but no success for now.

---

### Post by vedmar on 2012-10-25
Solution is to change inside guake.py

window_rect = screen.get_monitor_geometry(0)

to

window_rect = screen.get_monitor_geometry(1)

---

