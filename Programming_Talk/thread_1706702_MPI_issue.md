---
title: "MPI issue"
date: 2011-03-14
forum: Programming Talk
---

### Post by translucid on 2011-03-14
Hi!
I'm using lam4-dev for the mpi environment on ubuntu 10.10 x64(it is running on a VM on a sony vaio laptop, if that matters).
My problem is rather odd. For example, I compile a simple .cpp program and it works lije a charm, and after running it in various ways (different no of processes etc) it just doesn't work anymore.

I get something like this for each process:

It seems that some error has occurred during MPI_INIT.  This will
cause your process to abort.  These kinds of errors are usually
system-related, such as running out of disk space, running out of
memory, or something more serious such as data not being passed
between processes properly.  That is, you should not be seeing this
error message; if you are, something is likely Very Wrong with your
system.  :-(

Perhaps this Unix error message will help:

        Unix errno: 14
        Bad address

I have uninstalled, reinstalled and changed lam4-dev several times (to other apps that contain the mpi environment), but the problem remains the same.
I don't know how to fix this, I'm rather a newbie on ubuntu, not to mention mpi.
I don't know what other details I should give, I will provide any additional information if requested.
Thank you.

---

### Post by talonmies on 2011-03-14
Is there any good reason why you are using lam? Nothing in that codebase has been changed in a long time and it possible that there are underlying conflicts with more modern libc and other user space stuff that has evolved since the lam code base was frozen.

I would strongly recommend switching to either OpenMPI or mpich2. Apart from getting MPI V2.0 support, you will be using an actively tested and developed codebase which might work better the much more modern userspace you are running with.

---

### Post by deceaseddolphin on 2011-04-13
I faced similar problems with lam4-dev.

Install OpenMPI. It should work smoothly.

---

