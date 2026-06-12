---
title: "openMPI message"
date: 2009-01-22
forum: Programming Talk
---

### Post by LasherHN on 2009-01-22
I compiled openMPI because the one from the repos were acting funny.
Everything works now, sorta but everytime I use mpirun to run something it asks for my sudo password and gives this message:

```
hellop: Symbol `ompi_mpi_comm_world' has different size in shared object, consider re-linking
```

And I'm not sure what it means or what's it about. (I'm just starting a parallel computing class)

---

### Post by monkeyking on 2009-01-22
I had problems in the past with the mpi in the repos.

But you need to elaborate on your setup,
did you compile mpi on all your machines,
is it a homogeneous system.

---

### Post by LasherHN on 2009-01-22
It's actually in my laptop (Dell Inspiron 6000 under Intrepid, Pentium M, I don't really remember the specifications anymore ), I installed it here because I've been told you can simulate more than one process so I can code and compile here to see if it works then take my work to school's lab.

Edit: The strange message went away...
Still it asks me for my sudo password every time I use mpirun tho. I'm thinking that it may have to do with a configuration with ssh (I had to install a ssh server for it to work out).

---

### Post by monkeyking on 2009-01-23
You just need to install your dsa key.
If you don't thinking about it,
you can use ssh install keys

[http://www.catb.org/~esr/ssh-installkeys/](http://www.catb.org/~esr/ssh-installkeys/)

---

