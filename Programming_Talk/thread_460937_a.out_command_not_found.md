---
title: "a.out command not found"
date: 2007-06-01
forum: Programming Talk
---

### Post by w4llsb4lls on 2007-06-01
Hi guys, 

Thanks in advance for any light shed on this....

Had some problems compiling with gcc, completed some essential builds and now my programs compile without any problems.

When I a.out in a terminal I get the following error.

> 
walls@Linux:~/C Programming/ICA Test$ a.out
bash: a.out: command not found

Any help out there? I think it may be a path or something simple - hopefully.

Cheers.

---

### Post by YoG%*@ on 2007-06-01
hi

have you tried prefixing a.out with ./ ?
```

./a.out

```

---

### Post by w4llsb4lls on 2007-06-01
Bingo!

Appreciate it, many thanks.

---

### Post by hillbilly on 2007-06-01
you could edit your PATH variable to 
> export PATH=.:$PATH
so that you don't get such errors.

---

### Post by FuturePast on 2007-06-01
> **hillbilly said:**
> you could edit your PATH variable to 

so that you don't get such errors.
For security reasons, that's not such a great idea.

---

