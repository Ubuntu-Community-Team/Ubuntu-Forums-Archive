---
title: "MPI C++ newbie question"
date: 2011-02-09
forum: Programming Talk
---

### Post by Myoxocephalus on 2011-02-09
Hi!
I have a quick question regarding MPI and sending of information to nodes. My code, somewhat simplified, does this:

MPI_reduce(...);
if (myrank == 0){
     do a lot of stuff, and find value for variable x_var;
     if (x_var < limit){
          x_step += dx;
     }
}

Now, this works fine for on node. But, when I use several nodes, the value of x_step is only changed on node with rank 0. I want node 0 to do this job, and then update x_step on ALL nodes. I don't know if that was clear or not. What I'm looking for is probably something av a reveres of MPI_reduce; somthing sends a variable to all nodes so that everyone has the same.

Can anyone help me out? Thanks a lot!

Best regards,
Myoxocephalus

---

### Post by MadCow108 on 2011-02-09
you want the broadcast operation
MPI_Bcast

---

### Post by Myoxocephalus on 2011-02-09
Worked like a charm! Thanks!

Best regards,
Myoxocephalus

---

