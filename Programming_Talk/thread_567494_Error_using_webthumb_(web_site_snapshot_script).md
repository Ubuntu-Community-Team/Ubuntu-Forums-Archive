---
title: "Error using webthumb (web site snapshot script)"
date: 2007-10-04
forum: Programming Talk
---

### Post by AJL on 2007-10-04
I need to find a way to programmatically take a snapshot of a website and generate a thumbnail image.  What I found was a script called "webthumb" created by [http://www.boutell.com/webthumb/](http://www.boutell.com/webthumb/)

I installed the necessary packages, Xvfb and netbpm but the issue I am encountering is the inability for my script to connect to X.  I have never tried anything like this before so I feel a little clueless on where to go next. 
```
webthumb http://www.instantspot.com/ | pnmscale -xysize 100 100 | pnmtojpeg > instantspot.jpg
```

And the result:
```

Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
AUDIT: Thu Oct  4 15:39:02 2007: 21264 Xvfb: client 1 rejected from local host (uid 1000)
Xlib: connection to ":2.0" refused by server
Xlib: No protocol specified

xsetroot:  unable to open display ':2.0'
AUDIT: Thu Oct  4 15:39:02 2007: 21264 Xvfb: client 1 rejected from local host (uid 1000)
Xlib: connection to ":2.0" refused by server
Xlib: No protocol specified


(firefox-bin:21270): Gtk-WARNING **: cannot open display:  
Unable to start mozilla -width 1024 -height 768 at Desktop/webthumb-1.01/webthumb line 162.

```

I guess my question would be...How can I grant this script access to X?  And then second question, Is that the right question to ask?  :)

---

### Post by AJL on 2007-10-09
Anbody?

---

### Post by qwerion on 2007-10-18
Me haz same problem. Seems like we should be using xvfb-run script instead of Xvfb. Me no good with Perl.

So...

Anybody??

---

### Post by zebx on 2008-03-06
Same problem :(

---

### Post by mssever on 2008-03-07
I've never used webthumb, but from glancing at their website, it appears that you could get the same result from gnome-screenshot(1).

---

