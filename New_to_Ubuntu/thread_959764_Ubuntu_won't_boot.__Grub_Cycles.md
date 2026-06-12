---
title: "Ubuntu won't boot.  Grub Cycles"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by rayboston on 2008-10-26
Hi,

My computer got shut down improperly and now Ubuntu won't boot.  The grub chooser comes up, but if I pick Ubuntu or Ubuntu safe mode, the screen goes blank and then grub comes back.

Any thoughts?  Do I need to reinstall?

Thanks!

Ray

---

### Post by Crafty Kisses on 2008-10-26
Have you tried using SuperGrub to repair Grub?

[http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)

---

### Post by caljohnsmith on 2008-10-26
Have you run an fsck on your Ubuntu partition yet? That might help. You can do it from your Live CD with:
```
sudo fsck -y /dev/sdaX
```
And replace sdaX with your Ubuntu partition. If it returns any errors, please post them.

---

