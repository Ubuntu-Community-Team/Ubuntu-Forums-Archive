---
title: "[SOLVED] USB won't unmount"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by tqprvn on 2008-05-30
hi all

Put in a USB drive yesterday, deleted some stuff off it, unmounted, unplugged....and it is still on my desktop.

I can still open it in my file viewer too - even when it is unplugged.

Tried restarting, it is still there. 

Tried plugging it in again, it mounts as a different drive (with the same name) and unmounts correctly.

How do I get rid of it?

Matt

---

### Post by abhiroopb on 2008-05-30
So if I understand correctly you basically have a "phantom" drive that refuses to dissappear but isn't actually doing anything?

If so do the following in a terminal:

```

cd /media
sudo ls -a

```

This should give you a list of everything that is mounted in the media folder. If you find you're "phatom" drive, and are SURE that it isn't connected to anything then do the following in a terminal:

```

sudo rm -rf <name of drive>

```

---

### Post by bumanie on 2008-05-30
If you are not comfortable with command line, go to terminal and enter > gksudo nautilus You should then be able to go to computer, open filesystem and navigate to your desktop and remove the 'errant' drive to the garbage bin.

---

### Post by tqprvn on 2008-05-30
thanks, killed it in nautilus.

---

