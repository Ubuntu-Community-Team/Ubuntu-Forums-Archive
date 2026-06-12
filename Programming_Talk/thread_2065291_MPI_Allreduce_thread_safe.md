---
title: "MPI_Allreduce thread safe?"
date: 2012-10-01
forum: Programming Talk
---

### Post by azzamite on 2012-10-01
Hello there

[Here]("http://www.mcs.anl.gov/research/projects/mpi/www/www3/MPI_Allreduce.html") it says that this operation is thread safe, however I'm not quite sure about how to  [interpret]("http://www.cs.uiuc.edu/homes/wgropp/projects/parallel/MPI/mpi-errata/discuss/thread-safety/thread-safety-1-clean.txt") that.

Since this particular call doesn't accept a "tag" parameter, I think it is NOT thread safe; for instance, if we have 10 process with 3 threads each and each thread calls MPI_Allreduce...

Can we be sure that the calls will not get mixed?

Anyone knows an alternative for this collective operation that is truly thread safe?

---

### Post by azzamite on 2012-10-02
Seems like we're expected to have a private communicator for each group of threads.
[http://www.mcs.anl.gov/research/projects/mpi/www/www3/MPI_Comm_dup.html](http://www.mcs.anl.gov/research/projects/mpi/www/www3/MPI_Comm_dup.html)

This should work for now.

---

