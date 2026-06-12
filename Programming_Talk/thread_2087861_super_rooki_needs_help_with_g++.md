---
title: "super rooki needs help with g++"
date: 2012-11-24
forum: Programming Talk
---

### Post by CWZ on 2012-11-24
Ok i to a c++ class a LONGGGGGGGGGGGGGGGG time ago back around the turn of the cent. but i am wanting to get back into it via linux and i got g++ to not return any errors but it wont play it and i skimd the man g++ but i didn't see were it runs the file so... i need help how do i get GNU g++ to run the file???

---

### Post by MadCow108 on 2012-11-24
by default it puts the result into a file named *a.out*, you run it with *./a.out* (./ means current directory)
you can change that with the -o option
```
g++ file.cpp -o result
```

---

### Post by CWZ on 2012-11-24
Ok i am doing something wrong heres my term read out.

[LIST]
[*]cw@cw:~/c++$ cd /
cw@cw:/$ ls
bin    dev   initrd.img      lib32       media  proc  sbin     sys  var
boot   etc   initrd.img.old  lib64       mnt    root  selinux  tmp  vmlinuz
cdrom  home  lib             lost+found  opt    run   srv      usr  vmlinuz.old
cw@cw:/$ cd home
cw@cw:/home$ ls
cw
cw@cw:/home$ cd /
cw@cw:/$ /home/cw/c++/a.out
bash: /home/cw/c++/a.out: No such file or directory
cw@cw:/$ home/cw/c++/a.out
bash: home/cw/c++/a.out: No such file or directory
cw@cw:/$ cd /home/cw/c++
cw@cw:~/c++$ a.out
a.out: command not found
cw@cw:~/c++$ g++ a.out
g++: error: a.out: No such file or directory
g++: fatal error: no input files
compilation terminated.
cw@cw:~/c++$ g++ m1st.cpp
cw@cw:~/c++$ ls
a.out  m1st.cpp  m1st.cpp~
cw@cw:~/c++$
[/LIST]
What did i for get ????

---

### Post by CWZ on 2012-11-24
Ok got it now thx i wasnt in the directory when i tryed running thx thx thx

---

