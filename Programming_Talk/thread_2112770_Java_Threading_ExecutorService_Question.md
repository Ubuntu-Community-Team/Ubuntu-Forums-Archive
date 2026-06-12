---
title: "Java Threading ExecutorService Question"
date: 2013-02-05
forum: Programming Talk
---

### Post by Kentucky88 on 2013-02-05
Is the following code below efficient?  Is there an efficient way to remove the Thread.sleep() command in the while loop?  I read another forum about a solution which involved converting the Runnable to Callable and calling get() on the future object, but that seems like a lot of overhead since I don't actually need the result of thread execution (each worker thread prints to file).  But I also don't want to create 500000 worker Runnable objects all at once when I only have 2 execution cores.  I'd ideally like to just create 10 Runnable worker objects or so at a time instead and keep my memory requirements as low as possible. Any suggestions on how to do this?  Also, once the worker object is done running, are there any special tricks I should do to make the garbage collector delete the object sooner rather than later?

[PHP]
    private void run() {
        ExecutorService executor = Executors.newFixedThreadPool(2);        
        for(int idaconfig = 0; idaconfig < 500000; idaconfig++) {
          Runnable worker = new MyTest(idaconfig, this);
          executor.submit(worker);        
        }
        executor.shutdown();
        while (!executor.isTerminated()) {        
            try {
                Thread.sleep(10000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        // Wait until all threads are finish
        System.out.println("Finished all threads");
        try {
            output.close();
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
[/PHP]

---

### Post by PaulM1985 on 2013-02-06
Whenever you submit a task to an ExecutorService it returns a Future object.  You could build a list of these Future objects and check if they have been finished using the isDone() method.

[http://docs.oracle.com/javase/6/docs/api/java/util/concurrent/ExecutorService.html#submit(java.lang.Runnable](http://docs.oracle.com/javase/6/docs/api/java/util/concurrent/ExecutorService.html#submit(java.lang.Runnable))

[http://docs.oracle.com/javase/6/docs/api/java/util/concurrent/Future.html](http://docs.oracle.com/javase/6/docs/api/java/util/concurrent/Future.html)

Paul

---

### Post by Some Penguin on 2013-02-06
> **Kentucky88 said:**
> Is the following code below efficient?  Is there an efficient way to remove the Thread.sleep() command in the while loop?  I read another forum about a solution which involved converting the Runnable to Callable and calling get() on the future object, but that seems like a lot of overhead since I don't actually need the result of thread execution (each worker thread prints to file).


You can use a CountdownLatch.  Initialize it with the total number of tasks, have worker threads call 'countDown' on it (in a finally block -- you probably do NOT want the application to hang if a single task throws an exception and bypasses the countDown so the latch never hits zero!), and then await() when all tasks are submitted.

This only works if you know beforehand how many tasks there will be.  If you don't... perhaps you could use a CyclicBarrier keyed to the number of (worker threads in pool + 1), and after you've finished queuing up all 'real' work you queue one additional task per worker (solely to await() on the barrier) and lastly have the main thread await() on the same barrier.  None of the threads waiting proceed until all have reached that state, which would only be possible when all the worker threads have finished all 'real' work.  That should work.
 
> **Kentucky88 said:**
> 
  But I also don't want to create 500000 worker Runnable objects all at once when I only have 2 execution cores.  I'd ideally like to just create 10 Runnable worker objects or so at a time instead and keep my memory requirements as low as possible. Any suggestions on how to do this?  Also, once the worker object is done running, are there any special tricks I should do to make the garbage collector delete the object sooner rather than later?


Try an ArrayBlockinQueue.  Bound = max number of items you'd like to create.   Worker threads poll from the queue, your main thread uses put() -- which blocks if the queue is full.

> **Kentucky88 said:**
> 
[PHP]
    private void run() {
        ExecutorService executor = Executors.newFixedThreadPool(2);        
        for(int idaconfig = 0; idaconfig < 500000; idaconfig++) {
          Runnable worker = new MyTest(idaconfig, this);
          executor.submit(worker);        
        }
        executor.shutdown();
        while (!executor.isTerminated()) {        
            try {
                Thread.sleep(10000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        // Wait until all threads are finish
        System.out.println("Finished all threads");
        try {
            output.close();
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
[/PHP]

(1) When I create any kind of thread pool like that embedded in an Executor, my code almost always looks like

```

ExecutorService es = null;
try {
  es = Executors.newFixedThreadPoolOrOtherCreatorMethodBlah(...);
  /* work with es */
} finally {
  if (es != null) {
     es.shutdownNow(); 
  }
}

```

The shutdown goes in the finally block so that if /anything/ goes wrong after the ExecutorService is created, I don't leak threads.  With code like

```

      for(int idaconfig = 0; idaconfig < 500000; idaconfig++) {
          Runnable worker = new MyTest(idaconfig, this);
          executor.submit(worker);        
        }
        executor.shutdown();

```

if a runtime exception is thrown when you create or submit the MyTest (say, a RejectedExecutionException, which is unchecked), it'll abort your run() method and leave the executor service's thread pool running.  Maybe that's impossible in your case, but I like to err on the side of caution.

---

### Post by Some Penguin on 2013-02-06
Oh, and if you're concerned about object churn, one thing to check would be whether it's possible to refactor

```

       for(int idaconfig = 0; idaconfig < 500000; idaconfig++) {
          Runnable worker = new MyTest(idaconfig, this);

```

so that MyTest instead takes a range for idaconfigs -- e.g. 

```

       int batchSize = 10000;
       int idaConfigCount = 500000;
       for(int idaconfig = 0; idaconfig < idaConfigCount; idaconfig += batchSize) {
          int maxIdaConfig = idaConfig + batchSize - 1;
          if (maxIdaConfig >= idaConfigCount) {
            maxIdaConfig = idaConfigCount-1;
          }

          Runnable worker = new MyTest(idaconfig, maxIdaConfig, this);

```

and simply have MyTest handle the range in some iterative loop.   It might be less efficient if MyTest takes very different processing time based on the exact idaConfig values (so that some batches are much more expensive than others), but it might work for you.

---

