---
title: "Creating pipelines between programs"
date: 2009-02-27
forum: Programming Talk
---

### Post by nebu on 2009-02-27
I am writing a C++ program which needs to read the input of some system call i make inside the program......


how do i make a pipe between my c++ program and the system call of my output so that i can use the output of the system call in my c++ program??

---

### Post by geirha on 2009-02-27
You'll want to look at [popen](http://manpages.ubuntu.com/manpages/intrepid/en/man3/popen.3.html)
```
man 3 popen
```

---

