---
title: "Launch several instances of a python scripts in parallel in different windows..."
date: 2009-04-20
forum: Programming Talk
---

### Post by Valistar on 2009-04-20
Hi everyone,

I wrote a python script which work if you launch one instance of it. 
So far, if I launch several instances of my script, all of them are launched in the same shell window, forcing me to quit the last instance to access the one before and so on...

What I would like to do is to run one instance of my script in one different shell window (and if possible one instance per gnome-terminal tab). 

Is it possible? If so, must I use subprocess and if yes, how does it work cause I don't understand it well. If not, how can I do that?

Thanks

Valistar

---

### Post by albandy on 2009-04-20
xterm -e program_to_lauch

---

### Post by Valistar on 2009-04-20
Thanks a lot for the tip! However it seems that the different instances are not working in parallel..anyway, I'll take a look to it. Thanks again!

---

### Post by 1001how2 on 2009-04-20
I’d been using Python’s cPickle module for my serializing data structures to disk. As my data size got larger I started to care about performance, and after a few searches ended up at the marshal module. It comes with a few caveats, but is working great, much faster for me than cPickle. So if you’re looking for performance and can live with the caveats, give marshal a try.

---

