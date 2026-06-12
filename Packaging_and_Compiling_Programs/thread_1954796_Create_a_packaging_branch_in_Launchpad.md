---
title: "Create a packaging branch in Launchpad"
date: 2012-04-08
forum: Packaging and Compiling Programs
---

### Post by r-senior on 2012-04-08
I'm trying to create a packaging branch in Launchpad to hold the 'debian' directory separately from the source branch. I see lots of examples of these packaging branches referred to with URLs like:

```
lp:<project>/<series>/debian
```

I've taken my 'debian' directory and initialized it with bzr, added the files and committed it, e.g.

```
$ cd debian
$ bzr init
$ bzr add
$ bzr commit -m 'Initial revision of packaging branch'

```

But when I try and push this using a "nested" URL like the one above, it doesn't work:

```
$ bzr push lp:<project>/<series>/debian
bzr: ERROR: Permission denied: "Cannot create 'debian'. Only Bazaar branches are allowed."
```

If I push as 'lp:<project>/<series>-debian' it works. But that's not the way I see a lot of examples doing it.

Any ideas?

---

