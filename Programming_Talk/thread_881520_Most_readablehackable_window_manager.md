---
title: "Most readable/hackable window manager?"
date: 2008-08-06
forum: Programming Talk
---

### Post by Ademan on 2008-08-06
I'm interested in working on a window manager, however there's alot that goes into one...  I've read a substantial amount of the X11 spec, the ICCCM, and the ewmh spec, however plenty of questions still remain (probably in part because I haven't seen much in practice).

Let me list the questions I have at present, some of them are probably obvious, others not so much, and some I probably *should* have already picked up considering the reading i've done...

[LIST=1]
[*]How does one request a FULL string, or unicode string property from a window?  If you specify too small of a length, the value gets truncated, and specifying an arbitrarily large length doesn't seem right...(but if it is... that's what i'll do)
[*]How does a window manager identify top level windows?  Simply by them being mapped direct children of root? (or reparented to a window-manager-controlled-decoration window?)
[*]How exactly does input filter through windows?  Originally i remember reading that it begins at the highest window and trickles down (or is consumed).  But I remember reading something to the contrary.
[*]How should a well behaved window manager deal with xinerama?
[*]Does the window manager play any part in the handling of 'selection's ?
[/LIST]
And there's definitely more, however I'm blanking at the moment.

Anyways, I figure reading the code of a window manager with a small, and straightforward codebase, would answer most, if not all of my questions, so if anyone can either answer these questions, or point me to relevant code in window managers, or cleanly written window managers, that would be great.

Thanks alot,
Dan

---

### Post by LaRoza on 2008-08-06
This should help: [http://freshmeat.net/projects/tinywm/](http://freshmeat.net/projects/tinywm/)

---

### Post by Ademan on 2008-08-06
Thanks, I've actually looked at tinywm (sorry for not mentioning that).  The problem there, is that tinywm doesn't actually do a whole lot... it's a great example of simple code, however (obviously) it leaves out alot of things that a 'real' window manager would need to do, and consequently doesn't cover the things I'm currently confused about.  (In the meantime I think i'm gonna peak at blackbox)
  
Thanks for the quick reply.

---

### Post by LaRoza on 2008-08-06
I would then suggest dwm, wmii or xmonad.

---

### Post by xelapond on 2008-08-06
If your into Python like me, you could check out PyWm.  Its written to be a base for a new WM, and not actually be used.  It is usable though.  I was going to write my own tiling WM until I found wmii.

[http://www.freenet.org.nz/python/pywm/](http://www.freenet.org.nz/python/pywm/)

---

### Post by Kadrus on 2008-08-06
I'd suggest [pekwm.]("http://pekwm.org/projects/pekwm")
It's very light and i find it to be good for old computers like mine,and i think it can help you out.

---

### Post by Ademan on 2008-08-09
Thanks alot everyone for the replies (sorry for being so late myself...)!  Originally I was thinking I was going to write it in python (and i still may).  But i've found myself butting up against python-xlib enough that I'm seriously considering writing it in c or c++ (which i was raised on, but going back to either after using python is pretty painful).

So again thanks for the replies.  I think I'll be taking a look at dwm, pekwm, pywm and maybe awesomewm (fixes a great deal of the usability problems present in dwm).  Although awesomewm has switched over to xcb, which may or may not make it more useful to me.  (alternatives to xlib are very interesting to me, however, xlib is probably what i'll use, whether it's in python or c/c++)

---

### Post by Sorivenul on 2008-08-11
Just my two cents, but please don't make a fork or rewrite of dwm or its derivatives.  There are too many out there already.  To see what I mean, look [HERE]("http://gilesorr.com/wm/bloodlines.html").  The link is also great for a phenomenal list of window managers.

---

