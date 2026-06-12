---
title: "Bash script help"
date: 2010-05-26
forum: Programming Talk
---

### Post by MikeRostermund on 2010-05-26
Hi,

When I create a list of files with ex. `find . -type f` I might get paths with special characters (like whitespaces, single quotation-marks and so),
but you cannot just parse this on to stuff like chmod, because it would[COLOR=#000000] interpret it as
multiple paths.
So. Lets say I get a path named "/home/user/test te'st" from the `find` command.
How would I add the quotation-symbols in each end of the string when I parse it on to chmod,
to make chmod interpret each path as a single string?
Be aware that this needs to be added for each result returned from `find`.

Best regards.
Mike
[/COLOR]

---

### Post by ksa618 on 2010-05-26
This should do the trick:
```
find . -type f | while read LINE ; do chmod 700 "$LINE"; done
```

---

### Post by geirha on 2010-05-26
You can just let find do it.
```
find . -type f -exec chmod 644 {} +
```
That's completely safe, no matter what odd characters may be in the filenames, find will pass them on to chmod correctly.

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by MikeRostermund on 2010-05-28
I got it working. Thanks!

---

### Post by MadCow108 on 2010-05-28
you could also use find's -print0 option in conjunction with xargs -0

---

### Post by MikeRostermund on 2010-05-28
> **MadCow108 said:**
> you could also use find's -print0 option in conjunction with xargs -0
I've tried that, but still.. chmod interpret the input with whitespaces as multiple path's.

But as I mentioned earlier, I got it working.

---

