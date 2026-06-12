---
title: "devilspie + terminal geometry"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by RavUn on 2008-07-18
I've been searching and trying different things with getting the geometry right.  I set up my terminal to be transparent in the background a while ago and never could get the geometry right and eventually gave up and left it in the top right corner of the screen.  I started messing with it again today and I still cannot figure it out and now it's in the middle of my screen and I don't like it there.

I'm not so worried about it starting up when I login, I just want it to go to the same place when I open the terminal.  My DesktopConsole.ds file is:
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (pin)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
		(geometry "600x300+10+10")
        )
)
```

I've tried all of these variations but it doesn't move at all
```
(geometry "600x300-100+100")
(geometry "600x300+100-100")
(geometry "600x300-100-100")

```

What I did was added (center) to the file hoping I could adjust it from the center using geometry, and now, even after getting rid of (center) it still goes somewhere around the center.  I can adjust the size of the terminal with 800x200, etc... I just can't put it where I want it.  Devilspie works fine with everything else, I don't see why this doesn't work.  I had a similar geometry setting and it was being placed all the way in the top left corner so I guess it just has  mind of its own.  I've done 
```

killall devilspie
killall gnome-terminal

```
and restarted devilspie then the terminal but no luck.

---

### Post by drs305 on 2008-07-18
I had to spend a lot of time with devilspie. I wanted it to open on my 4th workspace but the 'workspace' and 'viewport' listings were problematic and I ended up just using the geometry settings without setting a particular viewport. The '**3950**' setting is 3950 pixels to the right of the first screen's left border. 

With the following setting in my desktop.ds file, it sets up a terminal screen on my 4th screen. 

```

(if
		(contains (window_class) "Gnome-terminal")
)
        (begin
			(geometry "1110x900+3950+75")
			(undecorate)
			(pin)
        )
)

```

---

### Post by glantucan on 2008-08-12
Hi,

Lucky you that it lets you set the position. It lets me set size of the window but not position. This is what I'm using:
```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 4)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "924x668+100+200")
        )
)
```
I'm using it to have a terminal spitting every /var/log/message on the desktop. 

By the way, as you can see you would use ```
set_workspace 4
``` better than giving the position from the top left corner of your first workspace

Any help appreciated

---

