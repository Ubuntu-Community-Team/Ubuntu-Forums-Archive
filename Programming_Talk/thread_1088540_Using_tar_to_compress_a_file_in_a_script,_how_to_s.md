---
title: "Using tar to compress a file in a script, how to specify the directory tree?"
date: 2009-03-06
forum: Programming Talk
---

### Post by jucas_lo on 2009-03-06
Hi! I need to do make a bash script, and i have to create a tar file of a directory. Now I have two small problems that if I manage to resolve, would make my life a lot easier:

1) I need to tar the directory test/conf. So i do:

```
tar -uf conf.tar test/conf/ 
```

In the tar created i get a directory test and under this I get the folder conf (test/conf). So is there a way to tell tar to create only a conf folder in the tarfile (i.e. instead of test/conf just conf) without manually changing dirs?. I tried: ```
tar -uf conf.tar testrel/conf/ -C testrel/conf/
``` but it didn't work

2) Can I change the name of the output folder when extracting ? for instance if I am extracting a tar in which there is only one folder called conf, can i tell tar to extract it with the name conf2???

I would really appreciate any suggestion!!!

thanks guys!

:popcorn:

---

### Post by dwhitney67 on 2009-03-06
```

tar -C test -cvf conf.tar conf

```

---

### Post by jucas_lo on 2009-03-06
thanx

---

### Post by the_unforgiven on 2009-03-06
Check out the **--transform** option from the tar manual:
[http://www.gnu.org/software/tar/manual/tar.html#SEC108](http://www.gnu.org/software/tar/manual/tar.html#SEC108)

This allows you to replace the names/paths of the files as they go in and out of the tarfile.
Pretty neat if you want to make the path to which it should be extracted different from which it was built.

---

