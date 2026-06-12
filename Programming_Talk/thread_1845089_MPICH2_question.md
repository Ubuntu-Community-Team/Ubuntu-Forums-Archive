---
title: "MPICH2 question"
date: 2011-09-16
forum: Programming Talk
---

### Post by IPMU_Yan on 2011-09-16
Hi all I have a question on how to use mpich2. It seems that no matter what values I pass to mpirun -np xx, mpich2 just runs xx copies of the program without parallelization. I specify the number of cores in used and it always show 1 -- xx such lines will appear.

But when I use openmpi, everything works as predicted. Would someone point me how to solve this problem?


I have the following simple program

  int dum;
  char **dummy;
  int myid,NCore;
  MPI::Init(dum,dummy);
  myid = MPI::COMM_WORLD.Get_rank();
  NCore = MPI::COMM_WORLD.Get_size(); 
  cout << myid << " " << NCore << endl;
  double sum(0.);
  for (int i=myid; i < 10; i+=NCore){
    sum += i;
  }
  cout << myid << " " << sum << endl;

  MPI::Finalize();

Notice I have not included the reduce command.

---

