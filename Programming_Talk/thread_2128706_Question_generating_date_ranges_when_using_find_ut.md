---
title: "Question: generating date ranges when using find utility"
date: 2013-03-24
forum: Programming Talk
---

### Post by mreich on 2013-03-24
Hello,

Using the -atime -mtime or -ctime tests in the find utility returns information about files that were accessed, modified or changed N 24 hour periods ago.  Does anyone know how to use time utilities to generate arguments to these tests that specify particular dates?   One could use a calender and a calculator to compute the number of days between the desired date and the current time.  But, section 6.6 'Relative Times in Date Strings' in the find info pages explain a scheme of expressions for specifying relative times.  The problem is that the expressions are valid arguments to the date utility, which returns date strings, not numbers of 24 hour periods between times.

Thanks,
M.Reich

---

### Post by ofnuts on 2013-03-24
Use the "-newerXY" specification. For instance: 
```

# finds all file modified since March 20
find . -newermt 20130320 -ls

```

Variants allow you to compare the timestamps of the file to the timestamp of a reference file (find -neweram foo.bar) will find all files accessed ('a') since the modification ('m') of foo.bar .

 If you need older files, then use "not newer", you can even combine several tests:
```

# find all files changed between March 10 and March 20. 
find . -newermt 20130310 -a -not -newermt 20130320 -ls

```

---

### Post by mreich on 2013-03-24
Hello,

Thanks for the response.  I thought all -newer variations compared timestamps, missed -newerXt.  
Incidentally, your location looks water logged.

---

### Post by ofnuts on 2013-03-24
> **mreich said:**
> 
Incidentally, your location looks water logged.
No it's not, you are looking at inaccurate maps :)

---

