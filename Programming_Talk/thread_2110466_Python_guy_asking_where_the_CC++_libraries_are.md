---
title: "Python guy asking where the C/C++ libraries are?"
date: 2013-01-30
forum: Programming Talk
---

### Post by slimjimmrtim on 2013-01-30
When programming in Python, or many other languages like Java, there are many libraries to import/include. Where are these in C/C++? Do people developing C/C++ use a framework or something? Where is all the documentation? Where does one find libraries?

Thank you in advance for replies!

---

### Post by 3246251196 on 2013-01-30
> **slimjimmrtim said:**
> When programming in Python, or many other languages like Java, there are many libraries to import/include. Where are these in C/C++? Do people developing C/C++ use a framework or something? Where is all the documentation? Where does one find libraries?

Thank you in advance for replies!

```
apt-file show libc6-dev
```

this library includes all the include-files, and, of course, the static/dynamic library object files.

---

### Post by SledgeHammer_999 on 2013-01-30
It depends on what you want to do. Almost always there is a library for every task you want to accomplish (and for some the are several libs)

For C++ you could use the Standard Template Library(STL) which is available under any good compiler. A sample reference with examples is here ->[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

You can try different libs from the Boost libraries(a collection of very helpful libs)-> [http://www.boost.org/doc/libs/](http://www.boost.org/doc/libs/)

And of course helpful functions exist in the helper libs of Gtk and Qt. Eg for Gtk take a look at Glibmm->[http://developer.gnome.org/glibmm/unstable/namespaceGlib.html](http://developer.gnome.org/glibmm/unstable/namespaceGlib.html)

However you are not limited to those. You search the net for what you want to accomplish and you will find some relevant lib. Then you install it through the packagemanager (unless it is an obscure one). Usually it comes with a -doc package which has documentation or you find the docs online.

---

### Post by micahpage on 2013-01-30
the c++ reference from the post above is what i have used. There is no python interpreter help() function for c++ like there is for python.

---

### Post by slimjimmrtim on 2013-01-31
Thank you everyone. The Boost library looks pretty neat. In my poking around I have also come across [http://pocoproject.org/](http://pocoproject.org/) which is neat too. What brought be there was the ability to grab a web page, since, a lot of the work I do involves interacting with the web. I of course did see the curl library, and successfully used, but it was infinitely more complicated than in Python. As I look around the C++ ecosystem I am, to a degree, learning that it is not as archaic as it previously seemed.

---

