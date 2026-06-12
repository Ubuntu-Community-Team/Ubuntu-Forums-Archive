---
title: "Removing text from a file by expression matching"
date: 2010-07-09
forum: Programming Talk
---

### Post by vinayg18 on 2010-07-09
Hi,

I have a file with several lines such as
```
<page=100>
<page=120>
.
.
.
```

I want to delete all such lines. How do I do it?
The expression would be <page=*> is all I know.
Thanks in advance.

---

### Post by geirha on 2010-07-09
If you want to script editing of a file, I recommend ed. See:

[http://bash-hackers.org/wiki/doku.php?id=howto:edit-ed](http://bash-hackers.org/wiki/doku.php?id=howto:edit-ed) 
[http://sdf.lonestar.org/index.cgi?tutorials/ed](http://sdf.lonestar.org/index.cgi?tutorials/ed)
[http://wolfram.schneider.org/bsd/7thEdManVol2/edtut/edtut.pdf](http://wolfram.schneider.org/bsd/7thEdManVol2/edtut/edtut.pdf)

In short, this should remove all lines containing only <page=something> from *file*.
```

printf '%s\n' '/^<page=.*>$/d' w | ed -s *file*

```

---

