---
title: "Releasing lock in Java"
date: 2013-03-16
forum: Programming Talk
---

### Post by 3v3rgr33n on 2013-03-16
Hi

I have a somewhat simple problem. I have a synchronized method, I want to release the lock when a specific condition is met. How do I do that?

```

public synchronized void someMethod(){
           if (empty>0){
                   --empty;
            }
            else{
                  //releaseLock here
                  doSomeOtherCrazyThing();
                  }
}

```

Regards,

A

---

### Post by r-senior on 2013-03-16
Could you use a synchronized block rather than making the whole method synchronized?

```

public void someMethod() {

    synchronized(self) {
        if (empty > 0) {
            --empty;
            return;
        }
    }

    doSomeOtherCrazyThing();

}

```

Alternatively hand-code something with an explicit lock rather than using the synchronized keyword:

[http://docs.oracle.com/javase/7/docs/api/java/util/concurrent/locks/Lock.html](http://docs.oracle.com/javase/7/docs/api/java/util/concurrent/locks/Lock.html)

---

### Post by 3v3rgr33n on 2013-03-16
Thnx!

---

### Post by ofnuts on 2013-03-16
> **3v3rgr33n said:**
> Hi

I have a somewhat simple problem. I have a synchronized method, I want to release the lock when a specific condition is met. How do I do that?

```

public synchronized void someMethod(){
           if (empty>0){
                   --empty;
            }
            else{
                  //releaseLock here
                  doSomeOtherCrazyThing();
                  }
}

```

Regards,

A
It looks like you need a synchronized method to update the value of 'empty', and call that method from other unsynchronized methods..

---

### Post by 3v3rgr33n on 2013-03-16
I don't understand what you're trying to say.

---

### Post by r-senior on 2013-03-17
I presume something like this?

```
/**
 * Decrement empty
 * @returns true if empty could be decremented, i.e. was > 0
 */
public synchronized boolean decrementEmpty() {
    if (empty > 0) {
        --empty;
        return true;
    }
    return false;
}

public void crazyUnsynchronizedMethod() {
    if (!decrementEmpty()) {
        doSomeOtherCrazyThing();
    }
}

```

The advantage would be that it doesn't conflate the manipulation of empty with doing some other crazy thing -- you might want to decrement empty from somewhere else and not tie that to doing some other crazy thing. With a contrived example like this, it's difficult to say which approach makes most sense.  (Or, indeed, whether the return value from the first method should indicate whether empty ends up as zero rather than whether empty could be decremented).

---

### Post by ofnuts on 2013-03-17
> **r-senior said:**
> I presume something like this?
With a contrived example like this, it's difficult to say which approach makes most sense..

IMHO the other method never makes sense, and leads to the original question. Synchronized methods should be short and focused. If your design doesn't let you write such methods, reconsider the design...

---

### Post by 3v3rgr33n on 2013-03-17
> **ofnuts said:**
> IMHO the other method never makes sense, and leads to the original question. Synchronized methods should be short and focused. If your design doesn't let you write such methods, reconsider the design...

Best advice ever!

I changed the structure. Now works. Thanx guys :-)

---

