---
title: "I've never seen this Java construct before...."
date: 2011-07-06
forum: Programming Talk
---

### Post by skytreader on 2011-07-06
I saw this code snippet from Head First Design Patterns:

```

public static Singleton getInstance(){
  if(uniqueInstance == null){
    synchronized(Singleton.class){         //This thing is new to me
      if(uniqueInstance == null){
        uniqueInstance = new Singleton();
      }
  }
  return uniqueInstance;
}

```

Uhhmmm...so what does the line I marked do? I know that it has been written as such so that only the block of code enclosed by synchronized's curly braces are actually synchronized. But why does it have that argument for? And what does Classname.class do? The closest I've found on the net as explanation for it is java.lang.Class but it doesn't quite hit the spot.

Sorry if I can't be very clear on my question. Again, I've never seen this construct before. Thanks.

---

### Post by PaulM1985 on 2011-07-06
This is related to threading.

Lets imagine the code was simpler:
```

public static Singleton getInstance(){
  if(uniqueInstance == null){               //line1
        uniqueInstance = new Singleton();   //line2
      }
  return uniqueInstance;
}

```

Lets say that there are two threads running at the same time.  ThreadA calls getInstance() and evaluates line1 to true.  ThreadA then has to give some processing time to ThreadB which has also called getInstance().  ThreadB evaluates line1 to true (since we still haven't set uniqueInstance) and then creates a new singleton and returns.  ThreadA is allowed to start running again.  It evaluated line1 to true when it was processing earlier and so goes on to create a second instance of the Singleton, which is wrong since there should only ever be one.

The code you supplied, with the synchronized part, prevents this.  Only one thread can be running in the synchronized part of any object.  Since this is in a static function, you need to pass (Singleton.class) in so that it synchronizes for the entire class, not just objects of that class.

So taking the example on to the synchronized code:

```

public static Singleton getInstance(){
  if(uniqueInstance == null){          // line1
    synchronized(Singleton.class){     //line2
      if(uniqueInstance == null){      //line3
        uniqueInstance = new Singleton(); //line4
      }
  }
  return uniqueInstance;
}

```

ThreadA executes, evaluates line1 and finds it is true, and executes line2.  ThreadB starts evaluates line1 to true, gets to line2 and can not progress further, because the class has been locked by ThreadA.  ThreadB's processing time finishes and ThreadA can continue.  It evaluates line3 to be true and sets the uniqueInstance and returns.  ThreadB can start and is now allowed to execute line2 and move into the synchronized region.  In this case, line3 will evaluate to false, since ThreadA set uniqueInstance.  So ThreadB doesn't set uniqueInstance a second time and returns the singleton that ThreadA created.

Paul

---

### Post by 1clue on 2011-07-06
As well, "synchronized" can synchronize on any object even though it normally synchronizes on the current class instance.  (as opposed to the static class shown)

---

### Post by Some Penguin on 2011-07-06
'synchronized' also imposes certain constraints regarding different threads' views of the same data.  See "Java Concurrency in Practice".

---

