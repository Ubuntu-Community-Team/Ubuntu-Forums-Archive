---
title: "PHP convert split into preg_split"
date: 2011-02-13
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-13
this works but is deprecated
$results = split(chr(29), $rlines);

the new funtion is preg_split
$results = preg_split(chr(29), $rlines);

but of course, that does not work.

So what would it be to work with preg_split?

I found explode works the same as split.
[http://php.net/manual/en/function.split.php](http://php.net/manual/en/function.split.php)

---

