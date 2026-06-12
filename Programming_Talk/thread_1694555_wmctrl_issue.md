---
title: "wmctrl issue?"
date: 2011-02-24
forum: Programming Talk
---

### Post by Zachf on 2011-02-24
I have noticed an odd issue with wmctrl I just can't explain.
I run:

wmctrl -r WinName -e 0,x,y,w,h

which is supposed to set the window called WinName to location x,y with width w and height h.
Strangely, when I run:

wmctrl -Gl

to get the managed windows and respective geometries, often the values are not those that I set.

The windows in question are embedded terminals and as such have no borders or title bar. I though that that might be the issue, so I've run the same commands but with terminals that have both borders and a title bar and the issue persists.

I've ignored this slight annoyance for a long time and am finally appealing to the masses for insight :p

Thanks in advance!

---

