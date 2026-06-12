---
title: "Help compiling EMC2 under Feisty Fawn"
date: 2007-05-31
forum: Programming Talk
---

### Post by wjhildreth on 2007-05-31
Hello all.

I am trying to compile EMC2 (Linux CNC) under Ubuntu v7.04 and I get the following error:

> none -k_ -o po/rs274_err.pot emc/task/emctaskmain.cc emc/rs274ngc/rs274ngc_errors.cc && touch po/rs274_err.pot
/bin/sh: none: not found
make: *** [po/rs274_err.pot] Error 127
joeh@joeh-ubuntu:~/downloads/emc2/src$ 


I have no clue what the 'none' command is or what library it could be found in, can someone please point me in the right direction?

Many thanks for your time and energy.

Warm Regards,

Joe Hildreth

---

### Post by wjhildreth on 2007-05-31
I done a make clean and started over from scratch.

I got the simulation stuff to run.

Now, can anyone explain how to get rtlinux or rtai working?

Regards,

Joe Hildreth

---

