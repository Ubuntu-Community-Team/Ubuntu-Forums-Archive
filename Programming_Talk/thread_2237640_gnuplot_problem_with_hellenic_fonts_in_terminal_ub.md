---
title: "gnuplot problem with hellenic fonts in terminal ubuntu 14.04"
date: 2014-08-03
forum: Programming Talk
---

### Post by Claus7 on 2014-08-03
Hello,

I had faced this problem again, back in maverick, using gnuplot 4.4 and on. The problem persisted with 4.6 version (also in ubuntu trusty). 

I was not able to type hellenic fonts, while using gnuplot. For example I wanted to type:
```
set xlabel "&#954;&#940;&#964;&#953;"
```
and I could not type the word *&#954;&#940;&#964;&#953;*.

In maverick, I was able to downgrade gnuplot to versions 4.2.x without any problem and the issue was fixed. In trusty, this was not the case because there were unmet dependencies (libraries that their versions in trusty were much newer than the ones required).

So I went to gnuplot website and installed the rc1 5.0 version by typing:
./configure
make
sudo make install

and the problem disappeared.

Regards!

---

