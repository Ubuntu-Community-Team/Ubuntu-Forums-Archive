---
title: "Thread Garbage Collection"
date: 2012-03-07
forum: Programming Talk
---

### Post by shashanksingh on 2012-03-07
I have a question in java.

Suppose a thread is in exucution and suppose it still ahs a long time before it finishes it job. However its reference is lost in the 'main' thread.

Will the thread be available for garbage collection once its reference is lost or only after it has finished executing?

---

### Post by Some Penguin on 2012-03-07
Running threads are valid roots from the perspective of garbage collection, and thus are the contents are considered 'live'.

---

### Post by shashanksingh on 2012-03-14
So suppose my program made a thread somewhere and say it forgot to stop it before teminating.
So after my application has terminated, how long would the other thread be running around in the system ? Will it continue to exist untill the JVM is shut down?

I know its bad programming practice to do so, but just in case I lost its reference somewhere?

---

### Post by Some Penguin on 2012-03-14
The JVM will shut down when all non-daemon threads have terminated, or when you explicitly kill it (e.g. System.exit(someintegerstatuscode)).  At that point, any daemon thread will be terminated.

If you start a thread but do NOT mark it as a daemon thread, and don't explicitly shut down the JVM, then it won't shut down until that thread exits.

---

