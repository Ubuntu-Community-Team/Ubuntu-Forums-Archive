---
title: "Running mpi compiled programs"
date: 2006-03-09
forum: Programming Talk
---

### Post by maitreya on 2006-03-09
Compiled a source program with mpicc with no errors. Executing it ```
mpirun -np 4 *program*
``` gives this error ```
ssh: connect to host localhost port 22: Connection refused
p0_11534:  p4_error: Child process exited while making connection to remote process on localhost: 0
```

All the processes run on the same cpu.

Solved by opening port 22 to localhost and apt-get the openssh server.

---

### Post by hondacodonbk on 2009-05-12
I think you try begin with : lamboot ( to start lam/mpi )

---

### Post by gcordoba on 2009-08-27
Probably that is the solution, but how exactly to tell the firewall to open port 22 to the localhost?. I tried several choices without success:
 
Assuming that 127.xxx.yyy.xyy is the host IP:

gcordoba@urcunina:~/tmp$ sudo ufw allow from 127.xxx.yyy.xyy to any port 22
Rule added
gcordoba@urcunina:~/tmp$ mpiexec -n 1 ./a.out 
ssh: connect to host urcunina port 22: Connection refused
--------------------------------------------------------------------------
A daemon (pid 6662) died unexpectedly with status 255 while attempting
to launch so we are aborting.

There may be more information reported by the environment (see above).

This may be because the daemon was unable to find all the needed shared
libraries on the remote node. You may set your LD_LIBRARY_PATH to have the
location of the shared libraries on the remote nodes and this will
automatically be forwarded to the remote nodes.
--------------------------------------------------------------------------
--------------------------------------------------------------------------
mpiexec noticed that the job aborted, but has no info as to the process
that caused that situation.
--------------------------------------------------------------------------
mpiexec: clean termination accomplished
---------------------------------------------------------------------

Even following [http://www.funnestra.org/ubuntu/intrepid/#texlive](http://www.funnestra.org/ubuntu/intrepid/#texlive) on
gcordoba@urcunina:~/tmp$ sudo pico /etc/ssh/sshd_config
 It gives the same result, either for "urcunina" or for 127.xxx.yyy.xyy

Any idea?
Thanks
Gus

---

