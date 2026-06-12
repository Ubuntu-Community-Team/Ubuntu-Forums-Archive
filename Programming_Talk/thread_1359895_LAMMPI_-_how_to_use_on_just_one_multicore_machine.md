---
title: "LAM/MPI - how to use on just one multicore machine?"
date: 2009-12-20
forum: Programming Talk
---

### Post by beepyou on 2009-12-20
If there a way to setup lam/mpi such that it will communicate with other processors on the same machine instead of other machines over tcp/ip?

I have setup the basefile as below:
```
localhost cpu=16
```
and the output of the command: lamnodes shows the correct result:
```
n0        localhost:16:origin,this_node
```
but when I try to run mpirun -np 4 FILE, it's always running with just 1 process. Any reason why?

Also, since all of these cores will have shared memory, I am reading you can use some -ssi addon for optimization. How do u actually run the ssi addon? I tried ```
mpirun -np # -ssi XXXX
``` it said -ssi was not a valid flag.

Thanks!

---

### Post by beepyou on 2009-12-20
no luck?

Have I posted in the wrong forum?

---

### Post by blackrim on 2010-02-23
don't know if you ever got an answer but I have a similar setup and i did lamboot -l hostfile. i think the -l might help.

---

