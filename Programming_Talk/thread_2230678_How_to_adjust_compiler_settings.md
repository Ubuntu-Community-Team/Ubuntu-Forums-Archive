---
title: "How to adjust compiler settings"
date: 2014-06-20
forum: Programming Talk
---

### Post by spacerocket on 2014-06-20
Hello,

My current compiler (g++) doesn`t allow to compile C++11....

Any idea about how could I change the settings for it to follow the C++11 standard?

---

### Post by ofnuts on 2014-06-20
If you compiler doesn't allow it, then a setting won't change that, unless you didn't even try "man g++".

Otherwise, see [http://gcc.gnu.org/projects/cxx0x.html](http://gcc.gnu.org/projects/cxx0x.html) and compaere with the relase of GCC on your system. Maybe you need to upgrade.

---

### Post by QIII on 2014-06-20
I *think, *but I don't remember, that I looked for C++11 in synaptic, added it and just added a flag to the path -- but I did that in my IDE setup.  Not at home right now to look.

I think from the terminal the basic syntax would be

```
g++ -std=c++11 your_file.cpp -o your_program
```

plus whatever other flags you'd normally use.

---

