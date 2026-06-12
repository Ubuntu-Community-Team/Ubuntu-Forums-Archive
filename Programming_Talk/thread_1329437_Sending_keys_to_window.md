---
title: "Sending keys to window"
date: 2009-11-17
forum: Programming Talk
---

### Post by Raizor on 2009-11-17
I have an app that I need to pass keystrokes to.  I'm looking for the easiest way, preferrably a shell script, to make this happen.

Here's what I'm trying to do:

Send the following, timed keys, to an active window using a script.

I want to send a / key once every 10 seconds to an active window in ubuntu desktop.

I've seen xsendkeys, etc. but am still at a loss for how to make this happen.

---

### Post by pokerbirch on 2009-11-17
[xdotool]("http://www.semicomplete.com/projects/xdotool/xdotool") any good?

---

### Post by Raizor on 2009-11-24
I think this is going to work for me.  I've been playing with it and haven't been able to sort out the sytnax for it.  Any pointers?

Basically I need a counter (for about 10 seconds) then send the input to a specific window on desktop #1.

Any help is appreciated.

---

### Post by Raizor on 2009-11-27
bump

---

