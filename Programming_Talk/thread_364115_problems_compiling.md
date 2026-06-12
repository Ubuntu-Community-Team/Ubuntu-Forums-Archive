---
title: "problems compiling"
date: 2007-02-17
forum: Programming Talk
---

### Post by yvinogradov on 2007-02-17
Hi, I just installed Ubuntu today and tried compiling a test program today and it wouldn't :

'gcc test.cpp' yeilds:

'gcc: error trying to exec 'cclplus'" execcvp: No such file or directory

I am guessing it's missing a linker, but here are my questions:

why g++ doesn't exist, I am not a Unix/Linux pro, but I thought that gcc was a C compiler and g++ was a C++ compiler.

why is gvim missing? vim works fine but I would prefer to work with gvim but it's not there.

am i missing something from the installation?

thanks a lot for your help.

i don't thing it matters, but my test.cpp file is simple, so I don't think it's the problem:

-----------
int main() { return 0; }
-----------

---

### Post by lnostdal on 2007-02-17
have you done:
```
sudo aptitude install build-essential
```
..?

edit: 
also see [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) .. first writing mentions some other packages with some handy man-pages etc. in them

i think a sticky with a FAQ is needed :}

---

### Post by yabbadabbadont on 2007-02-17
The various compiling tools are not included in the default installation.  "sudo apt-get install build-essential" to install the most common ones.  Likewise, gvim is not included by default.  "sudo apt-get install gvim" to install it.  If you are using the Gnome desktop, the easiest way to search for and install/remove software would be to run Synaptic from the System->Administration menu.  Using it you can search both the package names and descriptions.

Edit: Too slow!  :lol:  (but my post was more complete :p:D)

---

### Post by yvinogradov on 2007-02-17
Thanks!

---

