---
title: "Java Threading Q"
date: 2010-07-27
forum: Programming Talk
---

### Post by vik_2010 on 2010-07-27
Just wondering the difference between the following two examples is. In the first, "synchronized" is wrapped about both "System.out.print(c)" and lock.notify(); in the second, it is just wrapped about lock.notify()

The first program usually prints "ab" then just stalls without ending... just a blinking cursor. Rarely, it prints "acb". The second prints "acb" always. 

Why the difference?
[PHP]
public class ThreadTest {
    public static void main(String[] args) {
            final Object lock = new Object();
            Thread t1 = new Thread() {
                public void run() {
                    try {
                    System.out.print("a");
                    synchronized(lock) {lock.wait();}
                    System.out.print("b");
                    } catch (InterruptedException e) {
                        System.err.print("INTERRUPTION");
                    }
                }
            };
            Thread t2 = new Thread() {
                public void run() {
                    synchronized(lock) {
                        System.out.print("c");
                        lock.notify();
                   }
                }
            };
            t1.start();
            t2.start();
    }
}
                    
[/PHP][PHP]
public class ThreadTest {
    public static void main(String[] args) {
            final Object lock = new Object();
            Thread t1 = new Thread() {
                public void run() {
                    try {
                    System.out.print("a");
                    synchronized(lock) {lock.wait();}
                    System.out.print("b");
                    } catch (InterruptedException e) {
                        System.err.print("INTERRUPTION");
                    }
                }
            };
            Thread t2 = new Thread() {
                public void run() {
                    System.out.print("c");
                    synchronized(lock) {lock.notify();}
                }
            };
            t1.start();
            t2.start();
    }
}
                    
[/PHP]Thanks.

---

### Post by Some Penguin on 2010-07-27
Code looks fine.  Code runs fine for me w/ the Sun JDK (1.6.0_20-b02).  Are you stepping through the code using an IDE like Eclipse?  That can definitely mess with the scheduling.

---

### Post by vik_2010 on 2010-07-27
nah, I know it works - insofar as a program that just prints 'a', 'b', and 'c' can "work." I was just wondering about the mechanics.

For example, Sometimes, "c" prints before "a." I thought that was very unusual, because "c" is in t2, and "a" is in t1, and t1.start() is called before t2. It has to have something to do with the way the JVM starts threads, but I don't know the code, so I can't be sure.

Most importantly, I was wondering about the notify() and wait() calls:

My understanding is that wait() causes the thread to go to bed (;)) until a thread calls notify() on its monitor. Thus, if the program works as I expected and t1 runs before t2, then "a" should print, then the synchronized block with lock.wait() should be entered, then t1 should sleep() [or wait()? what's the diff?], then t2 should print "c", then it should enter it's own synchronized state and call "lock.notify()", which would wake up t1 again and cause it to print "b". (THIS IS IN EXAMPLE 2). Thus, the output should be "acb." However, if t2 starts _before _t1(the unexpected occurrence - which happens, like, once in a couple dozen runs), then "c" will print, then (CONJECTURE) the synchronized lock.notify() call will be made (but this time, there won't be any thread to awaken because t1 hasn't yet run, and it can't yet because t2 has the lock), then t2 will end. THEN t1 will run, and it will wait indefinitely because now there is nothing else to wake it up.

For the first example, I think the same problem lies at bottom:

How is t2 (rarely) executing before t1?

---

### Post by Some Penguin on 2010-07-27
The scheduler is not obligated to have threads receive cycles in the order you start() them.  It could, but it doesn't have to.   'start' simply sets things in motion so that the scheduler can start giving it cycles. 

It is true, however, that the notify()-ing thread will not wait for a thread to wait for it.  In that case, the waiting() thread will not terminate.  The main thread will, but because you haven't marked the spawned threads as daemon threads, the JVM shouldn't end.  I should have noticed this but didn't.

Re:  wait vs sleep, wait() is condition-based (until it receives a notification) while a Thread.sleep() call is given a specific time to wait.  Both can be interrupted, but sleep() isn't tied to any particular condition object and doesn't require any synchronization.  wait() involves the waiter being added to a queue dealing w/ that specific object... and releasing the lock in the meantime.  notify() results in one waiting thread being woken up, while the notifyAll() variant does the obvious thing.

---

