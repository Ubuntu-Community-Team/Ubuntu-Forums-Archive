---
title: "pyserial not getting any data"
date: 2010-04-05
forum: Programming Talk
---

### Post by apocalypznow on 2010-04-05
Hi there,
I have my programs using pyserial which have always worked on Debian, but on Ubuntu (karmic) they don't at all.
I connect using 9600,n,8,1. RCSCTS=0.  I've tried combinations of setting DTR=True/False and CTS=True/False, but nothing works on Ubuntu. On Debian, all the default settings work.

What fails on Ubuntu is that after a serial port is successfully opened, a read() never returns.  Minicom shows that data is indeed coming through, however.

Please help!

---

