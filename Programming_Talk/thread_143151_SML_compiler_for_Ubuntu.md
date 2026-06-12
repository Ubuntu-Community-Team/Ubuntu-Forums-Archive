---
title: "SML compiler for Ubuntu?"
date: 2006-03-11
forum: Programming Talk
---

### Post by lunarmelody on 2006-03-11
Hello all,
Does anyone know if Ubuntu has a built-in sml compiler I could get using apt-get?  I've tried downloading the tar.Z files from the internet, and installing those, but I keep getting a runtime error when I try to use it.  If there isn't a built-in compiler I could get, does anyone know how I could fix this?  Thanks!

---

### Post by gord on 2006-03-11
> Standard ML of New Jersey interactive compiler
SML/NJ is an implementation of the Standard ML programming language.
Standard ML has many features, including type safety, polymorphism,
algebraic data types with pattern matching, higher-order functions,
and a sophisticated module system. It is especially well-suited for
writing compilers and other language processors.

This package includes the interactive compiler (sml), the compilation
manager (CM), and some essential libraries.  It is a "working"
version, but believed to be stable.

Install this package if you want to program in SML.

is that what you want?
```
sudo apt-get install smlnj
```

and make sure you have [enabled extra repositorys](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) of course :)

---

### Post by lunarmelody on 2006-03-12
Yes thank you!  :-D

---

### Post by bmalavan on 2007-03-14
hey ppl it does nt work for me....!

malavan@malavan-desktop:~$ sudo apt-get install smlnj
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package smlnj
malavan@malavan-desktop:~$

---

### Post by fct on 2007-03-15
[quote="bmalavan"]hey ppl it does nt work for me....![/quote]

Check, as gord suggested [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29)

And make sure you add universe. That's where smlnj is.

---

