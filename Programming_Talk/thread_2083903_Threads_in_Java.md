---
title: "Threads in Java"
date: 2012-11-13
forum: Programming Talk
---

### Post by kevinharper on 2012-11-13
[http://docs.oracle.com/javase/tutorial/essential/concurrency/runthread.html](http://docs.oracle.com/javase/tutorial/essential/concurrency/runthread.html)

Second paragraph below the code... Whaa?

> The first idiom, which employs a Runnable object, is more general, because the Runnable object can subclass a class other than Thread. The second idiom is easier to use in simple applications, but is limited by the fact that your task class must be a descendant of Thread.
What does this say?

---

### Post by mevun on 2012-11-13
In the first idiom, you can have something like:
```

public class Dog extends Animal implements Runnable {
    public void run() {
        System.out.println("Fetching ball");
    }
}

```In the second idiom, you always subclass from Thread.  Really, the second idiom you want to derive a class that naturally has behavior similar to a Thread, which I guess means an object that is more-or-less a computer science/executable object instead of representing something you might see in the real-world.  Not sure this would be a good example, but maybe a SerializableThread class where you can "save the state" of the thread to persistent memory.  Their example is more-or-less if you want to take a non-object oriented approach and just stick some procedural functionality into the run() method so that the program can execute that in its own thread.  I think that is what they mean by 'simple'.

---

### Post by ofnuts on 2012-11-14
To add to Mevun, the "Runnable" class has other uses... for instance in Swing your can use SwingUtilities.invokeLater() to have something run in the event loop.

Usually the constructor of a Runnable takes a bunch of parameters for the run (or the object has setters). Think of Runnable as a little piece of code with its parameters, ready to be launched, on a Thread or elsewhere.

---

### Post by KdotJ on 2012-11-14
Also, if you choose to opt for the second method and extend Thread, then your class cannot extend any other class (as Java does not allow multiple inheritance).

---

### Post by kevinharper on 2012-11-14
Cool. I have a little better understanding of how Threads work.

Thanks guys.

---

