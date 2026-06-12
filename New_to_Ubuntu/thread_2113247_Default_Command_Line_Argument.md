---
title: "Default Command Line Argument"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by toad3000 on 2013-02-06
If one of my command requires a command line argument and the the person forget to type the argument when running, how do I specify the default argument in my script? Thanks

---

### Post by steeldriver on 2013-02-06
you can do use the ${var:-default} syntax I think

```
$ echo "${var:-default}"
default
$ var="abcd"
$ echo "${var:-default}"
abcd

```see [http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)

---

### Post by Impavidus on 2013-02-07
```

$ cat script
#!/bin/bash
echo ${1-foo}
$ ./script bar
bar
$ ./script 
foo
$ ./script ""

#Empty line as an empty argument was given.
$ cat script2
#!/bin/bash
echo ${1:-foo}
$ ./script ""
foo
#Using :- instead of - changes treatment of empty arguments

```

---

