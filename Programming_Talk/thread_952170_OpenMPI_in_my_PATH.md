---
title: "OpenMPI in my PATH???"
date: 2008-10-18
forum: Programming Talk
---

### Post by Saponsky09 on 2008-10-18
Hi there, I'm trying to run parallel programs in my cluster with open mpi. I'm getting this error:
```

saponsky@Kurosaki-Ichigo:$ mpirun -np 3 -hostfile hostfile ./hello_c
--------------------------------------------------------------------------
Failed to find or execute the following executable:

Host:       kurosaki-server
Executable: ./hello_c

Cannot continue.
--------------------------------------------------------------------------
mpirun noticed that job rank 0 with PID 7358 on node Kurosaki-Ichigo exited on signal 15 (Terminated). 
1 additional process aborted (not shown)

```

I've read in open-mpi site's FAQ that it may be that open-mpi is not in my PATH but I installed the open-mpi-bin, libopenmpi-dev and open-mpi-common packages from Ubuntu's repository and at least mpirun is in my PATH.  
Do you have any idea of what is causing the error? How do I add open-mpi to my PATH?
Tanx in advance!

---

### Post by Saponsky09 on 2008-10-18
I kept reading and I just get more confused, the documentation says that openmpi copies the executable and PATH to each node.
  This confuses me as the error says that the executable wasn't found.  Also, I don't understand if I have to have the same username or the same account for each of the nodes in the cluster, I actually made an account with the same username at the remote node to test if it solves the problem but nothing changed.

---

