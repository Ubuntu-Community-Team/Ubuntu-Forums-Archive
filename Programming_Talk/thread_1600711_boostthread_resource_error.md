---
title: "boost::thread_resource_error"
date: 2010-10-19
forum: Programming Talk
---

### Post by balteo on 2010-10-19
Hello,

I am encountering the following error:

**********************************
terminate called after throwing an instance of 'boost::thread_resource_error'
  what():  boost::thread_resource_error
Abandon
**********************************

trying to run a threadgroup of 500 threads as follows:

thread_group * thgrp = new thread_group();
    for (int i = 0; i < NUMTHREADS; i++) {
        thgrp->create_thread(bind(&simulate, i, 100, 0.05, 0.2, 1.0, 100, 100, endPrices));
    }
    thgrp->join_all();


Can anyone please help. I don't understand why I get this error as I have no resource problems with my machine.

Julien.

---

### Post by dwhitney67 on 2010-10-19
I thought you might find the information [here]("http://support.math.cmu.edu/Parallel_Cluster/smp/Lthreadsfaq.htm#Q81") to be interesting, and related to your question.

As for your program, you should consider placing the call to boost::thread_group::create_thread() within try/catch blocks.

```

try {
   for (int i = 0; i < NUMTHREADS; i++) {
      thgrp->create_thread(bind(&simulate, i, 100, 0.05, 0.2, 1.0, 100, 100, endPrices));
   }
}
catch (std::exception& e) {
   std::cerr << "Caught exception: " << e.what() << std::endl;
}
thgrp->join_all();

```

P.S.  There's no need to allocate the boost::thread_group object.  IIRC, it maintains an STL list of allocated boost::thread objects.

---

### Post by balteo on 2010-10-20
thanks a lot for this reply,
I have too many threads anyway. As suggested by someone, I am going to alter the design of my app.
Julien.

---

