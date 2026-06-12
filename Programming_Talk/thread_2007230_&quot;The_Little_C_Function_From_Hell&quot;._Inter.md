---
title: "&quot;The Little C Function From Hell&quot;. Interesting read.."
date: 2012-06-20
forum: Programming Talk
---

### Post by muteXe on 2012-06-20
[http://blog.regehr.org/archives/482](http://blog.regehr.org/archives/482)

---

### Post by satsujinka on 2012-06-20
It's interesting that despite the behavior being clearly specified, it's apparently so difficult to get right. Of course, it could just be that this is of marginal interest so not too many people even bothered to look into it.

---

### Post by Bachstelze on 2012-06-20
It's not difficult at all to get right, as demonstrated by the fact that it was promptly fixed in clang. The only thing that it proves is that the GCC devs are good at ignoring bug reports, but that's not exactly news...

---

### Post by trent.josephsen on 2012-06-20
I wish the author wouldn't say "implicit cast" when "implicit conversion" is meant. Casts are always explicit. (He's right that the conversion in question is supposed to follow the same rules as a cast.)

---

