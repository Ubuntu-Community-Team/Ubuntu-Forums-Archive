---
title: "Python 3.1:  Security Hole or Bug or Ignorance?"
date: 2010-07-11
forum: Programming Talk
---

### Post by McRat on 2010-07-11
In the IDLE Python IDE, on the immediate mode side, I was showing the kids about infinite loops and CNTRL-C.

Something really weird happened.


```
>>> while 1:
	print ("test")

test
test
test
...
test
test
[COLOR="SeaGreen"]smb://qinsp1-linux32/public/2010/Reports/PPE/DexModel1.prt[/COLOR]test
test
test
...
```

That green line popped up out of nowhere.  It's the path to a file on the server that I had used for a CAD application earlier, has nothing to do with Python.

Not sure how that happened.  Any thoughts?

---

### Post by ov3rcl0ck on 2010-07-11
My theory... you have some kind of process running in the background, it output, and it came up in IDLE's prompt, which is basically just a shell running in the background with python running in it.

I might be wrong, however. I've never used python3.X because I personally don't really like it, i used python2.x for the time being.

---

### Post by raf-kig on 2010-07-11
> **ov3rcl0ck said:**
> I might be wrong, however. I've never used python3.X because I personally don't really like it, i used python2.x for the time being.
How long is the *time being*? Until Python drops support for 2.x and forces 3.x on us? Sadly, it looks as if Guido had a few too many Heinekens one night and conjured up this mess for Python. Until we get some kind of resolution on how this will finally play out I'm staying clear of Python.

---

### Post by soltanis on 2010-07-11
Luckily we're about to get Perl 6.

---

### Post by McRat on 2010-07-11
> **ov3rcl0ck said:**
> My theory... you have some kind of process running in the background, it output, and it came up in IDLE's prompt, which is basically just a shell running in the background with python running in it.

I might be wrong, however. I've never used python3.X because I personally don't really like it, i used python2.x for the time being.

No, no other apps active.  I'm not much a multi-tasker.  

Gotta say, that's bizarre.  Could it be an environment variable for USER that equals the last SAMBA file access?

Kinda of worrisome in case it's not a bug.

---

### Post by trent.josephsen on 2010-07-11
My initial thought would be that you or someone else inadvertently middle-clicked on the window, pasting the primary selection (most recently highlighted text) into it.  (When I was new to Linux, I did this quite a few times without figuring out exactly what was going on, and a lot of other people seem still to be ignorant of this feature.) Barring that, who knows?  But as it only happened once I would tend to blame it on something I did by accident rather than a bug in Python.

---

### Post by nvteighen on 2010-07-12
It's quite obvious:

You hit Ctrl-V (paste). In a QWERTY keyboard, C is to the left of V...

---

