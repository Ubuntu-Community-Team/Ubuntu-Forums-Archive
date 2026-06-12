---
title: "Java: Timer and Thread"
date: 2009-08-26
forum: Programming Talk
---

### Post by pfdevil on 2009-08-26
Hello,

I create a new Timer object and give it a Task that must be executed every second. The only operation the Task does is to create a new thread.

1. Will the Timer terminate while the thread is still executing?
2. If the Timer terminates will the thread still continue executing?
3. Will the Task still be executed each second, while the other previous threads are still executing?

Here is a bit of sample code I wrote that explains it.

```
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // This is the timer object I created
        Timer t = new Timer();

        //This is the task that must be executed each second
        TimerTask task = new TimerTask()
        {
            public void run() {
                /**
                 * When the task is executed a new thread is created.
                 * For the sake of this test, the thread will never
                 * terminate.
                 */
                InfinityThread infinite = new InfinityThread();
                infinite.start();
            }
        };

        /**
         * A fixed-delay timer places the emphasis on ensuring that the indicated
         * delay always elapses between invocations. This example will schedule a
         * task to recur with at least a second delay between invocations, starting immediately.
         */
        t.schedule(task,0,1000);
    }
```

---

### Post by kpkeerthi on 2009-08-27
> **pfdevil said:**
> 
1. Will the Timer terminate while the thread is still executing?
No. The process will keep running until it is manually killed. Think of it (the timer) as a daemon.
> **pfdevil said:**
> 
2. If the Timer terminates will the thread still continue executing?

This situation will not arise. However, if you kill the timer (i.e. the process) manually all threads that were spawed from it also die.
> **pfdevil said:**
> 
3. Will the Task still be executed each second, while the other previous threads are still executing?

Yes. The timer doesn't care if the previously spawned threads complete or not (the threads could even be running for days depending on what they were programmed do). The Timer keeps scheduling new tasks/threads.

---

### Post by pfdevil on 2009-08-27
Thanks, this clears up a few things.

Basically my program needs to execute a task every second. If a certain condition is true a new thread is created within the task. I just needed to be sure that the task will still be executed each second.

---

