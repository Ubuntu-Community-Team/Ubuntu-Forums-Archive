---
title: "multiprocessor and critical sections."
date: 2010-02-14
forum: Programming Talk
---

### Post by lostinxlation on 2010-02-14
Questions for those who have experience on the system programming with multiprocessor system.
 
When the multiple processes access, so called the critical section of the memory, they use a spin lock to allow only one of the processes to access the critical section with Test & Set instruction or similar types at a time. But my understanding is that those processes running on the different processors are independent(the processes are made to be independent to run in parallel), which makes me think why they have to access the same memory locations. I would guess it should be to synchronize the processes or something, but cannot think of an actual example.  What is the typical use of critical sections shared by multiple processes ?

---

### Post by MadCow108 on 2010-02-14
Shared memory is a way of providing communication/synchronization between threads.
If you don't need communication you don't need shared memory and you don't need locks and critical sections.

e.g. you want to calculate a single value which is just the sum of several independent calculation steps which can be parallelized.
The independent steps run happily on each processor with its private memory and no critical sections but when their finished they have to combine all part results to the final result.
This final result is saved in a single memory spot and is dependent on all threads.
So you need a way of synchronizing the access of each thread to this memory location (as long as the operations on it are not atomic).

pseudocode:
```

void calculate(int * result)
{
  int tempresult=0;
  // calculate temp result this is can be done in parallel
  for (1.. 100000)
   tempresult += 1;

  // here's the critical section, this needs some kind of lock
  *result += tempresult;
}

int main() {
  int result;
  make_tons_of_threads(calculate(&result));
}

```

the final step is called a reduce operation. Most frameworks (like openmp or MPI) provide some clever way of doing this very fast.

The classic educational example of this kind of problem is calculating pi. If you wish I can provide some implementations in openMP and MPI which must be lying around on my computer somewhere.

---

### Post by lostinxlation on 2010-02-14
Thanks,
 
The pseudocode solved my question.

---

