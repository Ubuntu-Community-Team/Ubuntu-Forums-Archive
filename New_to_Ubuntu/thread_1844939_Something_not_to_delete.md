---
title: "Something not to delete"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by anewguy on 2011-09-16
Well, I would have *thought* that everything in the /tmp folder was just that - temporary, so it could be deleted.  I some iso images that ended up there and I need to clean them up, so I deleted other things as well - some it wouldn't let me delete.

I wouldn't do this again.

I lost all kinds of configuration information, *INCLUDING* my password or at least a pointer or something to it, as it fails for Synaptic so I can't go back in and try to reinstall some things to see if it helps.  It might be all that I have left is to punt!  Hoping I can still keep my /home partition - time will tell.

Just wanted to warn others!

Dave ;)

EDIT:  Well, I got lucky.  I logged out and back in and everything seems fine so far.

---

### Post by 3rdalbum on 2011-09-16
/tmp is deleted on shutdown, but some important temporary stuff is stored there while the computer is on.

---

### Post by anewguy on 2011-09-17
> **3rdalbum said:**
> /tmp is deleted on shutdown, but some important temporary stuff is stored there while the computer is on.

Yep - found that out.  I thought, and thereby the beginning of my mistake, that it would be like the Windows temp folder.  See my big mistake there?  Kind of a dumb thing to do! ;)

Dave ;)

---

### Post by haqking on 2011-09-17
> **anewguy said:**
> Yep - found that out.  I thought, and thereby the beginning of my mistake, that it would be like the Windows temp folder.  See my big mistake there?  Kind of a dumb thing to do! ;)

Dave ;)

/tmp is often accessed alot, if you want to empty it you can drop to runlevel 1 if you really need to do it.

ctrl+alt+f1 to drop to console

```
sudo killall gdm
```
```

sudo telinit 1
```

from the recovery menu select root shell.

```
rm -rf /tmp/*
```

then reboot or type:

```
reboot
```

---

