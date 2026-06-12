---
title: "Using libgtkmm"
date: 2006-07-16
forum: Programming Talk
---

### Post by NSIMPSON on 2006-07-16
SO, I read one of the threads that referenced 

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)

I used the package manager to install libgtkmm-2.4-12ca along with it's dependencies and figured that I should be good to go, so took the first example file in chapter 3 from the website and proceded to execute the compile string specified on that page

g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`

The result was a string of errors of which I beleive the following are important:

Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable

So several questions, first, is the compile string correct for Ubuntu. If it is correct then:

1. What should I set PKG_CONFIG_PATH to?
2. Why doesn't the install do it automatically?

---

### Post by mostwanted on 2006-07-16
You also need to install the development package for gtkmm, before you can compile anything. Look for something that looks like the package you installed but with a "-dev" suffix as well.

---

### Post by ralphmerridew on 2006-08-05
$ dpkg -l "*gtkmm*" | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name              Version        Description
+++-=================-==============-============================================
un  libgtkmm-2.4-1    <none>         (no description available)
un  libgtkmm-2.4-1c2  <none>         (no description available)
ii  libgtkmm-2.4-1c2a 2.8.8-0ubuntu1 C++ wrappers for GTK+ 2.4 (shared libraries)


Don't see any gtkmm-dev.

---

### Post by JoshHendo on 2006-08-27
I have had this problem too.

I have tried to install the development files, but it doesn't seem to want to install (dependency problems).

Is there a way to make it so the one that I currently have installed will work?

Thanks
- Josh

---

