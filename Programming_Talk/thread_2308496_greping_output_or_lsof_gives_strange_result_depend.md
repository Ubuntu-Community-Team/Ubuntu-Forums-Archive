---
title: "greping output or lsof gives strange result depending on what is greped for"
date: 2016-01-03
forum: Programming Talk
---

### Post by Dreamer Fithp Apprentice on 2016-01-03
In bash, why does this show me an open epub but not an open fb2?

```
echo "greping for .fb2:"
lsof | grep "\.fb2"

echo "greping for .epub:"
lsof | grep "\.epub"

```

---

### Post by Dreamer Fithp Apprentice on 2016-01-04
Hyde at stackoverflow gave me the hint I needed to find the answer on this.  It isn't the file extension or type that makes the difference. It just so happens the fb2 file I was testing with is smaller. Small enough for fbreader to read the whole thing into memory and not need to keep the file open. File isn't open, so lsof doesn't see it. Duh.

---

