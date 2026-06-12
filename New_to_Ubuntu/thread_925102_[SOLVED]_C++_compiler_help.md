---
title: "[SOLVED] C++ compiler help"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ktuluscout on 2008-09-20
I recently converted a thinkpad T30 laptop over to ubuntu and I need some help using the compiler in terminal. I am taking a intro to computer programing class and we using C++. I used vi to create a small program that I named sample.cc and I tried to use gcc to compile it but I get the following error:

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

I created this same program on our school unix computer and I used the G++ compiler and it worked fine. I would appreciate any help you guys can give me. If you need any more info just ask.

---

### Post by lswest on 2008-09-20
install g++ with ```
sudo apt-get install g++
``` and try to compile it using g++ instead, since it's a c++ program.

---

### Post by acidsolution on 2008-09-20
```

sudo apt-get install g++

```

---

### Post by jemate18 on 2008-09-20
have you installed g++ using the above posts?

Where you able to compile your source using g++

---

### Post by anubhavrocks on 2008-09-20
File name suffix is used by gcc to determine the compilation.So a file with .cpp extension will invoke C++ compiler.

---

### Post by ktuluscout on 2008-09-24
sorry to take so long to respond. I got the g++ compiler working. I did not know that all had to do was type the sudo apt-get into terminal to get the compiler. Thanks everbody

---

### Post by StOoZ on 2008-09-24
and also install the essential stuff for developing :
> sudo apt-get install build-essential

you'll need it sooner or later.

---

