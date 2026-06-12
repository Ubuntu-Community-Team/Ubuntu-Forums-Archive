---
title: "Sudo is...broken?..."
date: 2012-08-26
forum: New to Ubuntu
---

### Post by Gigabitten on 2012-08-26
So, I just installed the 12.04 update.  "Just" means today.  I'm not sure if I'm late on that or what, but...anywhat, for awhile, Sudo worked fine, but, as of, as best as I can tell, two hours ago, every time I run into sudo, it throws these two error messages at me:

sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [115, -1, -1]: Operation not permitted

So, this happens everywhere.  If I do **mkdir test** then it works fine.  But, **sudo mkdir test **just doesn't work.  It doesn't matter if I'm in the directory or in a subdirectory of **~** or not...it just seems that sudo won't work for me.

So, any ideas guys?

---

### Post by Gigabitten on 2012-08-26
Hmmmm..........

So, upon logging out and logging back in, my desktop background (the default) looks weird.  Like, that file was corrupted.  Is my system degrading from the gui in?

...so, sudo's working now.  But what's up with the desktop background?

---

### Post by Gigabitten on 2012-08-26
Now, then.  I just updated and restarted...now I feel a bit like an idiot.  All the problems seem to be fixed.  Sudo's working, and so's the background.  I'm happy and sad all at the same time.  Oh, well...
[solved]

---

