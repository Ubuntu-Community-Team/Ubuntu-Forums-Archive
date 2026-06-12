---
title: "Java Multi-Threading Question"
date: 2011-05-17
forum: Programming Talk
---

### Post by Kentucky88 on 2011-05-17
Here is a very simple example class that I am trying to multi-thread:

[PHP]
import java.util.Random;

public class SingleThreadTest {
    private String[] result;
    private String label;
    private Random rand;
    private String alpha = "abcdefghijklmnopqrst";
    
    public SingleThreadTest()
    {
        rand = new Random();
        result = new String[14];
    }

    public void doSomething()
    {
        while(true)
        {
            generateLabel();
            for(int i = 0; i < 14; i++)
            {
                /* do some work */
                result[i] = label;
            }
            printResultArr();
        }
    }

    private void printResultArr() {
        for(int i = 0; i < result.length; i++) System.out.println("Index: " + i + " Result: " + result[i]);
    }

    private void generateLabel() {
        label = "";
        for(int i = 0; i < 5; i++) label += alpha.charAt(rand.nextInt(alpha.length()));
    }
    
    public static void main(String args[])
    {
        SingleThreadTest test = new SingleThreadTest();
        test.doSomething();
    }
}
[/PHP]

It just randomly generates a label, and then stores the label into a String array.  What I want to do is process each array index of the doSomething() loop in parallel.  I tried to do this by implementing a Thread Pool, but it's been a while since I have done threading and I think my attempt is way too complicated and inefficient:

 [PHP]
import java.util.Random;
import java.util.concurrent.Semaphore;

public class ThreadTest {
    private String[] result;
    private worker[] workerthreads;
    private Object idlethreadlock;
    private Object readylock;
    private Semaphore processinglock;
    private int index;
    private String label;
    private Random rand;
    private boolean ready;
    private String alpha = "abcdefghijklmnopqrst";
    
    public ThreadTest()
    {
        ready = false;
        rand = new Random();
        result = new String[14];
        readylock = new Object();
        idlethreadlock = new Object();
        processinglock = new Semaphore(4);
        index = 0;
        workerthreads = new worker[4];
        for(int i = 0; i < 4; i++)
        {
            workerthreads[i] = new worker(i);
            workerthreads[i].start();
        }
    }

    public synchronized int getNextIndex()
    {
        int retindex = index;
        index++;
        if(index == 13) ready = false;
        return retindex;
    }

    public void doSomething()
    {
        try {
            while(true)
            {
                index = 0;
                generateLabel();
                ready = true;
                synchronized(readylock) { readylock.notifyAll(); }
                while(index < 13) synchronized(idlethreadlock) { idlethreadlock.wait(); }
                //wait for all worker threads to finish
                for(int i = 0; i < 4; i++) processinglock.acquire(); 
                printResultArr();
                for(int i = 0; i < 4; i++) processinglock.release(); 
                //all worker threads have released lock and should now be finished
            }
        }
        catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    private void printResultArr() {
        for(int i = 0; i < result.length; i++) System.out.println("Index: " + i + " Result: " + result[i]);
    }

    private void generateLabel() {
        label = "";
        for(int i = 0; i < 5; i++) label += alpha.charAt(rand.nextInt(alpha.length()));
    }

    public class worker extends Thread {
        private String lab;
        private int threadid;
        
        public worker(int threadid)
        {
            this.threadid = threadid;
        }

        @Override
        public void run()
        {
            try {
                while(true)
                {
                    while(!ready) synchronized(readylock) { readylock.wait(); }
                    synchronized(processinglock) { processinglock.acquire(); }
                    lab = label;
                    int index = getNextIndex();
                    Thread.sleep(rand.nextInt(20));
                    result[index] = lab + " Thread: " + threadid;
                    synchronized(idlethreadlock) { idlethreadlock.notify(); }
                    processinglock.release();
                }
            } catch (InterruptedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }
        }
    }
    
    public static void main(String args[])
    {
        ThreadTest test = new ThreadTest();
        test.doSomething();
    }
}
[/PHP]

Can someone show or tell me a better way to multi-thread the first example problem above?

---

### Post by dwhitney67 on 2011-05-17
> **Kentucky88 said:**
> 
Can someone show or tell me a better way to multi-thread the first example problem above?

What is it that you want the first example to do that requires it to do it as a multi-thread application?

If your intent is to remove the for-loop from doSomething(), and create 14 separate threads, then do it.

IMHO, your examples are too complicated if you are merely looking to learn the basics of multi-threading.  Take a look at this *simple* example:
```

import java.lang.Thread;


class MyThread extends Thread
{
   public MyThread()
   {
   }

   public void run()
   {
      System.out.println("MyThread is running.");
   }

   public static void main(String[] args)
   {
      MyThread mt = new MyThread();
      mt.start();
   }
}

```
If you want to create more than one thread, and have each of these share a common object, then you better make sure that each thread accesses this object in a *synchronized* manner.  You can declare functions (that access this shared data object) to be synchronized.
```

class MyThread extends Thread
{
   private SomeObject myObject;

   MyThread(SomeObject obj)
   {
      myObject = obj;
   }

   ...

   public synchronized void doSomething()
   {
      System.out.println("doSomething is not doing any special at the moment.");

      myObject.someMethod();
   }

   public static void main(String[] args)
   {
      SomeObject obj = new SomeObject();

      MyThread mt1 = new MyThread(obj);
      MyThread mt2 = new MyThread(obj);

      mt1.start();
      mt2.start();
   }
}

```

---

### Post by Kentucky88 on 2011-05-17
Dwhitney, the part of my application that requires threading is the for-loop inside the doSomething() function:

[PHP]
    public void doSomething()
    {
        while(true)
        {
            generateLabel();
            for(int i = 0; i < 14; i++)
            {
                /* do some work */
                result[i] = label;
            }
            printResultArr();
        }
    }
[/PHP]I want to multithread the "result[i] = label; " part.  Instead of copying a label, the program that I am really interested in optimizing is doing something more complicated on each iteration of the for-loop.  Both both programs are similar in that they iterate through an array, do some processing on each index of the array, and then place the result into the result[].  I have 4 cores on my computer and I want each core to process an index in parallel for efficiency.  That would mean I want 4 threads to process 14 results through each iteration of the while loop (in my other program, the while loop runs for thousands of loops so I only want to create the 4 worker threads once and then reuse for life of program).  Note that I only have 14 results at a time that I can process.  I need to call printResultArr() to get the next 14 results...printResultArr() depends on the 14 results. I thought thread pools would be the best approach to solve this problem and that's what I tried to implement above.

---

### Post by stchman on 2011-05-17
The way I do threads is to make a class that implements Runnable.

Here is some sample code:

Main class:
[PHP]

public class ThreadTest {
    public static void main(String[] args) {
        // get out of static main
        ThreadTest m = new ThreadTest();

        m.arraySort();
        
    }
    
     public void arraySort() {
        double arraySizeMax = 20000.0;
        
        Thread[] t = new Thread[ 100 ];
        
        
        for( int i = 0; i < t.length; i++ ) {
            t[ i ] = new Thread( new ThreadTwo( (int)( arraySizeMax * Math.random() ) ) );
        }
        
        for( int i = 0; i < t.length; i++ ) {
            t[ i ].start();
        }
    }
}
[/PHP]Class that implements Runnable:
[PHP]
public class ThreadTwo implements Runnable {
    int numElements = 0; 
    
    public ThreadTwo( int elements ) {
        numElements = elements;
    }
    
    @Override
    public void run() {
        createAndSort( numElements );
    }
    
    // non static method create and sort method
    void createAndSort( int elements ) {
        // create counters
        int i = 0, j = 0;

        // create temp variable
        double temp = 0.0;
        
        // create variables for timer
        long initTime = 0, finalTime = 0;
        double totalTime = 0.0;
        
        // create data array
        double[] data = new double[ elements ];
            
        // create a random numbers from 1 - 100 and fill array
        for( i = 0; i < elements; i++ ) {
            data[ i ] = 100 * Math.random();
        }
        
        // set initial time
        initTime = System.currentTimeMillis();
            
        for( j = 0; j < elements; j++ ) {
            for( i = 0; i < elements - 1; i++ ) {
                if( i == elements )
                    break;
                        
                // test to see if an element is greater than the element after it
                if( data[ i ] > data[ i + 1 ] ) {
                    // if element is greater then swap them
                    temp = data[ i ];
                    data[ i ] = data[ i + 1 ];
                    data[ i + 1 ] = temp;
                }
            }
        }

        // set final time
        finalTime = System.currentTimeMillis();
    
        // calculate total time, the clock parameter is in milliseconds
        totalTime = (double)( finalTime - initTime ) / 1000.0;
            
        System.out.println( "Total time to sort " + elements + " numbers is " + totalTime + " seconds" );
    } // end createAndSort method
}
[/PHP]What this does is it spawns 100 threads that sort random amounts of random numbers using the ever inefficient bubble sort.

---

### Post by Reiger on 2011-05-17
You want to look at [the various static methods to create an Executor]("http://download.oracle.com/javase/1.5.0/docs/api/java/util/concurrent/Executors.html"). An executor is basically a scheduler that manages a thread pool, and there are various types. Using one you can take advantage of the methods defined for [ExecutorService]("http://download.oracle.com/javase/1.5.0/docs/api/java/util/concurrent/ExecutorService.html") and the scheduled variant depending on your needs.

---

### Post by Kentucky88 on 2011-05-17
> **Reiger said:**
> You want to look at [the various static methods to create an Executor]("http://download.oracle.com/javase/1.5.0/docs/api/java/util/concurrent/Executors.html"). An executor is basically a scheduler that manages a thread pool, and there are various types. Using one you can take advantage of the methods defined for [ExecutorService]("http://download.oracle.com/javase/1.5.0/docs/api/java/util/concurrent/ExecutorService.html") and the scheduled variant depending on your needs.

The executor does look like a good approach.  However, in my case, each task needs a separate instance of a fairly bulky class which I only want to instantiate once.  For that reason, I need 4 instances of a class which extends thread similar to what I had in my posted example.  The trick is that I need to reuse the worker instances.  I can't just create them as needed and then throw away after each task is complete.

---

### Post by Reiger on 2011-05-18
You could use the ThreadFactory (some static methods allow you to pass in your custom ThreadFactory) to tie the number of bulky objects to the thread.

Quick hack (just separate bits of code, assumes you want one bulky object per thread which is used inside the threadpool):
```

abstract class MyTask implements Runnable {
  @Override
  public void run() {
    ThreadWithObject two = (ThreadWithObject) Thread.currentThread(); 
    performTask(two.getContext());
  }
  
  abstract void performTask(MyBulkyObject context);
}

class ThreadWithObject extends Thread {
  public ThreadWithObject(Runnable task) {
    super(task);
  }
  private MyBulkyObject context;
  public MyBulkyObject getContext() {
    // lazily create context object.
    // should also ensure the object is instantiated on the thread
    // which will access it in MyTask.run()
    if(context==null) {
      context = new MyBulkyObject();
    }
    return context
  }
}

// make sure that all tasks submitted to the Executor
// are MyTask instances
ThreadFactory factory = new ThreadFactory() {
  @Override
  public Thread newThread(Runnable r) {
    return new ThreadWithObject(r);
  }
}

```

---

### Post by Kentucky88 on 2011-05-18
Thanks Reiger, you're right.  I think ThreadPools with custom ThreadFactory is the best approach.  Below is the final example code.  It might be about the same length as my earlier example or perhaps a bit longer, but I think it's easier to follow and definitely more efficient.  Only part that I don't like is that after submitting the threads, ExecutorService should provide a convenience function isAllDone() which returns true if all submitted tasks have completed executing.  Instead, I have to save the Future of each task into a List and then periodically poll all tasks to check if they have finished executing.

[PHP]
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.ThreadFactory;


public class ThreadPoolExample {
    private String[] result;
    private Random rand;
    private String label;
    private String alpha = "abcdefghijklmnopqrst";
    private ExecutorService threadpool;
    
    public ThreadPoolExample()
    {
        result = new String[14];
        rand = new Random();
        threadpool = Executors.newFixedThreadPool(4, factory);
    }

    public void doSomething()
    {
        List<Future> futures = new ArrayList<Future>();
        while(true)
        {
            generateLabel();
            for(int i = 0; i < 14; i++)
            {
                futures.add(threadpool.submit(new MyTask(label, result, i)));
            }
            while(!futures.isEmpty())
            {
                try {
                    futures.get(0).get();
                    for(int i = 0; i < futures.size(); i++)
                    {
                        if(futures.get(0).isDone()) 
                        {
                            futures.remove(i); 
                            i--;
                        }
                    }
                } catch (InterruptedException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                } catch (ExecutionException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
            printResultArr();
        }
    }

    private void printResultArr() {
        for(int i = 0; i < result.length; i++) System.out.println("Index: " + i + " Result: " + result[i]);
    }

    private String generateLabel() {
        label = "";
        for(int i = 0; i < 5; i++) label += alpha.charAt(rand.nextInt(alpha.length()));
        return label;
    }
    
    public class MyTask implements Runnable {
        private String label;
        private String[] result;
        private int index;

        public MyTask(String label, String[] result, int index)
        {
            this.label = label;
            this.result = result;
            this.index = index;
        }
    
        @Override
        public void run() {
            ThreadWithObject thisthread = (ThreadWithObject)(Thread.currentThread());
            try {
                Thread.sleep(1);
                result[index] = label + " Thread: " + thisthread.getContext().getClassname();
            } catch (InterruptedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }        
        }        
    }
        
    class ThreadWithObject extends Thread {
        public ThreadWithObject(Runnable task) {
            super(task);
        }

        private RandomClass context;
        public RandomClass getContext() {
            // lazily create context object.
            // should also ensure the object is instantiated on the thread
            // which will access it in MyTask.run()
            if(context==null) {
                context = new RandomClass();
            }
            return context;
        }
    }

    // make sure that all tasks submitted to the Executor
    // are MyTask instances
    ThreadFactory factory = new ThreadFactory() {
        @Override
        public Thread newThread(Runnable r) {
            return new ThreadWithObject(r);
        }
    };

    public class RandomClass
    {
        private Random rand;
        private String classname;

        public RandomClass()
        {
            rand = new Random();
            classname = new String(generateLabel());
        }

        public String getClassname() {
            return classname;
        }
        public int getNum() { return rand.nextInt(10); } 
    }
    
    public static void main(String args[])
    {
        ThreadPoolExample test = new ThreadPoolExample();
        test.doSomething();
    }
}
[/PHP]

---

### Post by Reiger on 2011-05-19
Again, depending on what you are trying to do the ExecutorService API might have just what you need:

1) Submit all tasks
2) call shutdown() on the ExecutorService
3) call awaitTermination() in a loop on the ExecutorService with parameters amounting to a suitably large timeout:
```

long timeout = 60L
TimeUnit unit= TimeUnit.SECONDS;
service.shutdown();
// give it 60 seconds, if not completed
// method will return before the timeout once the service is done
// or the thread is interrupted
// repeat, until done.

boolean done = false
while(!done) {
  done =awaitTermination(timeout, unit);
  // you might want to handle the interrupt case, i.e.: if(!done)
}

if(service.isTerminated()) { 
  System.out.println("Should alway be true"); 
}

```

---

