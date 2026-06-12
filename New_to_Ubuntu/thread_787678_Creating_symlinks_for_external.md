---
title: "Creating symlinks for external?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by El Lance-O on 2008-05-09
I just bought a 160GB external specifically for storing my music and movies on because my 80GB HD just doesn't cut it.

How might I about creating a symlink (or something of the sort) so that when I plug in my external, my Movies and Music folders show up in my home directory?

Is this possible?

---

### Post by Nepherte on 2008-05-09
You can create a symlink to it indeed. If your external disk is not plugged in, it will give you an error if you click on it. If it is plugged in and you've mounted it to the same location as the symlink directs to, it will work.
```
ln -s <targetdirectory> <symlinkname>
```
See the man page for more information.

---

### Post by El Lance-O on 2008-05-09
That's the thing, I don't want to have to deal with errors. I'd rather just have the symlinks show up when it's plugged in, and disappear when I disconnect it.

Is this realistic? It would just be awesome if it could work like that.

---

### Post by El Lance-O on 2008-05-09
bump Bump BUMP!

---

### Post by El Lance-O on 2008-05-09
:(

---

