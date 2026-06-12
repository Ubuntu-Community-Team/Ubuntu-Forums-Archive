---
title: "Which version of gcc..."
date: 2005-10-02
forum: Programming Talk
---

### Post by kudu on 2005-10-02
...should I be using ? Why so many versions in synaptic ? I'm using v3.3 now, which I believe is the default hoary setup. Should I be using v4 instead ? And if so, why ? Thanks for any answers.

kudu

---

### Post by toojays on 2005-10-02
Whatever you're using, you're best to use the default compiler, unless you have a good reason. So for hoary, stick with gcc 3.3.
Some of the other gcc versions in Synaptic (e.g. gcc-avr) are for cross-compiling to embedded processors. Sometimes older and newer versions of gcc (e.g. gcc-4 with hoary) are included for developers who specifically need them.
Breezy uses GCC 4, which has some features which are not present in GCC 3.3, most notably auto-vectorisation and precompiled headers. It's up to you to decide whether it's worth it to you to use a non-default compiler. Since you can have both installed at the same time, it's not a big deal if you want to try out GCC 4.

---

### Post by kudu on 2005-10-03
Thanks for that. :)

kudu

---

