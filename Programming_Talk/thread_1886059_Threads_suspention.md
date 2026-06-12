---
title: "Threads suspention"
date: 2011-11-24
forum: Programming Talk
---

### Post by jmwalloh on 2011-11-24
Hi, How do you suspend one thread for the other to do it's work if two threads (**T1 & T2**)T1 is a lower priority thread and T2 is a higher priority thread in java. T1 prints "hello" inside a loop 5 time after sleeping for 3 secs while T2 prints "world" once after 7 secs.
E.g

```
[B]for(int i=0; i<4; i++){
     Thread t1 = new Thread();
     t1.sleep(3000);
     System.out.print("Hello");
}[/B]
```
T2 is supposed to interrupt T1 after 7 sec to print "world"

---

### Post by ofnuts on 2011-11-24
> **jmwalloh said:**
> Hi, How do you suspend one thread for the other to do it's work if two threads (**T1 & T2**)T1 is a lower priority thread and T2 is a higher priority thread in java. T1 prints "hello" inside a loop 5 time after sleeping for 3 secs while T2 prints "world" once after 7 secs.
E.g

```
[B]for(int i=0; i<4; i++){
     Thread t1 = new Thread();
     t1.sleep(3000);
     System.out.print("Hello");
}[/B]
```

T2 is supposed to interrupt T1 after 7 sec to print "world"Your code has no meaning. Thread t1 is never started... Thread.sleep()  is a static method, ie, if some code in a thread calls it, that very  thread goes to sleep. If you ever implement that correctly, ie, start  two threads, and the code for one thread sleeps 3 secs and prints  "Hello" 5 times, while the code of the other sleeps for 7s before  printing "word", the first thread will be ended before the second wakes  up, whatever the priorities you assign to them.

---

