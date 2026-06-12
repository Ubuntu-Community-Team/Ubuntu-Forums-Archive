---
title: "[SOLVED] [bash] Problem with $PWD"
date: 2008-06-24
forum: Programming Talk
---

### Post by TreeFinger on 2008-06-24
I have a very simple script that is going to assign the current working dir to a variable.

I have tried everything..

MYDIR=$PWD
MYDIR=`pwd`
MYDIR=$(pwd)


nothing works.. why? I'm copying this out of a book for god's sake.

---

### Post by Alasdair on 2008-06-24
Works for me.

> MYDIR=$PWD
> echo $MYDIR
/home/alasdair

---

