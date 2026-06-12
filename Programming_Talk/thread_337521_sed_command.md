---
title: "sed command"
date: 2007-01-13
forum: Programming Talk
---

### Post by Waappu on 2007-01-13
Hi

Is there way use sed match parameter as non case sensitive?

```
echo 'Test' | sed 's/TEST/testing/'
``` e.g. if I try to replace word "test" it not mater what case it is and above command works

---

### Post by moma on 2007-01-13
echo 'Test' | sed 's/TEST/testing/I'

Browse to [http://www.gnu.org/software/sed/manual/html_mono/sed.html](http://www.gnu.org/software/sed/manual/html_mono/sed.html)
and search for "case".

---

### Post by Waappu on 2007-01-13
Hi

Thank you =)

---

