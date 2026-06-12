---
title: "[SOLVED] tar &amp;amp; make"
date: 2008-08-07
forum: Programming Talk
---

### Post by kmads on 2008-08-07
Hi, I need a little help with tar and make.

I have an directory which I would like to put in an tarball from a Makefile. My directory looks like this:
```
$ ls -R1
.:
Makefile
build/
my_programs.tar.gz

./build:
a_program1
a_program2
$ 
```

I would like to put all files (and folders) from the build-directory in the tarball via the Makefile:
```
$ cat Makefile 
tarit:
        tar cfzv my_programs.tar.gz build/
```
The tarball now contains:
```
$ tar tzf my_programs.tar.gz 
build/
build/a_program1
build/a_program2
```

How can I tar it so it doesn't contain the build-directory? E.g. so it looks like:
```
$ tar tzf my_programs.tar.gz 
./
./a_program1
./a_program2
```

Thanks,
Kmads

---

### Post by dwhitney67 on 2008-08-07
Write your Makefile like:
```
tarit:
        cd build; tar czvf ../my_programs.tar.gz *
```

---

### Post by kmads on 2008-08-07
> **dwhitney67 said:**
> Write your Makefile like:
```
tarit:
        cd build; tar czvf ../my_programs.tar.gz *
```

Thanks!

Best regards,
Kmads

---

