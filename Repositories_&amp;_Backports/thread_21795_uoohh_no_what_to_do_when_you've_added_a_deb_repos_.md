---
title: "uoohh no: what to do when you've added a deb repos on bad advice"
date: 2005-03-23
forum: Repositories &amp; Backports
---

### Post by und3rdog on 2005-03-23
ok, So I added
deb [http://lyre.mit.edu/debian/](http://lyre.mit.edu/debian/) testing main
to my repos file based on a comment from a friend who said I could get "mad speed" over internet 2 to MIT (I'm a student at a New England School)
...
then i go and do a update/dist-upgrade
...
now my desktop consists of the normal 4 icons with a big fat debian swirl in the background with no panels in sight!

Is there any way to reverse this?  Can I once again have my lovely ubuntu desktop back?

---

### Post by TravisNewman on 2005-03-24
try removing that repo and update/dist-upgrade again.
It's bad to add debian repos that have major system packages like that. What you've done is basically upgraded to Debian Sarge, it would seem. Removing that source, the newest release should be seen as the ones in your Ubuntu sources.

---

### Post by und3rdog on 2005-03-24
Very Well! I will try that..

I bet if I do a "sudo apt-get dist-upgrade -f --reinstall"  I'll have good results.

Anyways thanks.

---

### Post by az on 2005-03-24
Have you installed another window manager?

---

### Post by und3rdog on 2005-03-24
Window Manger, alas no (as it would have helped since gnome freaked out).  But I did solve my problems.  Apparently, gnome-panel doesn't install on the repos hoary upgrade method?  I don't know what the deal is with that, but a quick synaptic (which also didn't install by default) click fixed that.  Now I have lovely panels back,  it turns out the "stary" hoary backgrounds did install so no more debian swirl.  As a matter of fact, I'd say my inadvertent MIT adventure caused no real problems that the hoary repos couldn't undo. It just didn't install some common sense stuff automatically.  I would like my cursors back if anyone knows the package.  Thanks.

---

