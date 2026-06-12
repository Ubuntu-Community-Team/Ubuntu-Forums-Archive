---
title: "Impossible to execute one program"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by davili on 2012-11-27
Hello,

I'm a begginer with ubuntu (I use 12.04, in a Compaq Mini Cq10, Processor Intel® Atom™ N270, 1,6 GHz, level cache 2, 512 KB, Hard disk: SATA160 GB (5400 rpm), grafic card Intel® Graphics Media Accelerator 950, until 128 MB  graphic memory available). And after a long time using Ubuntu without problems, I can not open one program (Mnemosyne) and I cant understand why.
This is the url of the screen (and the explanation of the problem): [http://www.freeimagehosting.net/u31lp](http://www.freeimagehosting.net/u31lp)

Do you know guys what could happend or what should I do in order to fix it?

Thank you very much in advance.

---

### Post by LuciferRex on 2012-11-27
Does it do that after a restart on first run?

---

### Post by squakie on 2012-11-27
If one run appeared to abort and you tried again, the process may actually still be running in the background.  Try:  ps -e in a terminal window and see if the app shows.  If so, try:  kill -kill <the proc id> to kill it.

I also noticed you say you are using 12.04 and have 512kb (I assume you meant 512mb) of memory.  This could be a problem as well, as that is really short on memory, and if your graphics adapter is using shared memory then it eats into that as well.

---

