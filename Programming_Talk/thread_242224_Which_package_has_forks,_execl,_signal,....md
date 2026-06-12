---
title: "Which package has forks, execl, signal,..."
date: 2006-08-23
forum: Programming Talk
---

### Post by ronintiger on 2006-08-23
Hi!

I need to develop some programs that used threads, forks, execl and signals.. 

But I'm relatively new to Ubuntu and I don't know which packages need to be installed under Synaptics... Can anyone help?

Thanx :)

---

### Post by LordHunter317 on 2006-08-23
Install build-essential to get the base toolchain.  They're in libc6, but -dev for that will be installed by build-essential.

---

### Post by kwalo on 2006-08-23
For threads, you should try libpthreads0-dev. If you're using pthreads of course ;)

Forks, signals, etc are system calls, so they are allready there.

---

### Post by ronintiger on 2006-08-26
Ok! 
Worked fine.
Thanks :D!!

---

