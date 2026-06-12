---
title: "c++ apt library?"
date: 2011-07-02
forum: Programming Talk
---

### Post by yahyai-0 on 2011-07-02
Hello there

 How I can reach APT libraries or how I can update , install , remove and upgrade via C++?? I want another way than system() function ..

2- Is there any simple gtkmm tweaker or updater program for Ubuntu so I can contribute to it?

thanks

---

### Post by nvteighen on 2011-07-02
> **yahyai-0 said:**
> Hello there

 How I can reach APT libraries or how I can update , install , remove and upgrade via C++?? I want another way than system() function ..

2- Is there any simple gtkmm tweaker or updater program for Ubuntu so I can contribute to it?

thanks

1. There's libapt, which is C, but you can use it in C++. In fact, aptitude is written in C++ and uses it :) Install libapt-pkg-dev and libapt-pkg-doc (this installs the API docs).

2. Not sure. IIRC, Ubuntu's GUI updating utility is written in Python.

---

### Post by yahyai-0 on 2011-07-02
> **nvteighen said:**
> 1. There's libapt, which is C, but you can use it in C++. In fact, aptitude is written in C++ and uses it :) Install libapt-pkg-dev and libapt-pkg-doc (this installs the API docs).

2. Not sure. IIRC, Ubuntu's GUI updating utility is written in Python.

Thanks a lot ....

I want to do a bug fixer program for ubuntu , Which will have the updatable list of bug ( info + fix + restore)  the language that I know is C++ only.
What is the best way to do the FIX ?

[LIST=1]
[*]Make script for every BUGS and then call it from the program.
[*]Or packing the script on deb package and the use the programe.?
(( The scripts/package will be on the Internet))
[/LIST]

I hope u understand it ( not good in english)..

---

