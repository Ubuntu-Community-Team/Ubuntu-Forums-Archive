---
title: "whats wrong with this command??"
date: 2006-08-25
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2006-08-25
I executed this command on a HPUX machine , not on ubuntu.

This is in csh:
```

otis 21: find / -name "tnsnames.ora" 2> /dev/null
find: missing conjunction
otis 22:

```

But when I use the same commnad on diferent teminal using sh (default shell) I get the output??

```

otis 23: sh
$ find / -name "tnsnames.ora" 2> /dev/null
/arbor/FXENVP/scripts/tnsnames.ora
/u09/data/BED/BED/tnsnames.ora
/u01fxenvp/app/oracle/product/9i/network/admin/samples/tnsnames.ora
/u01fxenvp/app/oracle/product/9i/network/admin/tnsnames.ora

```

---

### Post by LordHunter317 on 2006-08-25
See the beginning of [http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/](http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/).  csh sucks is your answer.

---

### Post by peabody on 2006-08-27
I believe the problem is that csh doesn't share the same output redirection operators.

---

