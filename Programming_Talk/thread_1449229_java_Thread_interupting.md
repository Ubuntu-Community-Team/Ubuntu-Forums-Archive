---
title: "java Thread interupting"
date: 2010-04-07
forum: Programming Talk
---

### Post by Xender1 on 2010-04-07
My java application has two classes (Main.java which implements the main method, and ThreadTester.java which is my thread and implements Runnable).

From my main.java main method, i create two new ThreadTester threads. Here is what my ThreadTester currently looks like: (dumbed down a bit)
```

public class ThreadTester implements Runnable  {
    int speed; int dist;
    private volatile boolean keeprunning = true;
    //CONSTRUCTOR
    ThreadTester(int s) {
        speed = s; dist = 0;
    }

    public void run() {
        //a while loop while the distance each has gone is < 1000
        while (keeprunning) {
        while (this.dist <= 50) {

                this.dist += this.speed;

            try {
                Thread.sleep(1000); //tries to sleep for a sec
            } catch (InterruptedException ex) { //if interupted
              
                return;
            }
        } //end while loop
        keeprunning = false;
        }//end keeprunning
        System.out.format("I am done with the race!");
    }

}

```
in my main method of the main class 
```

public class Main {
    public static void main(String[] args) {
        // TODO code application logic here
        ThreadTester a = new ThreadTester(1);
        ThreadTester b = new ThreadTester(2);

        System.out.println("Start");


        new Thread(a).start();
        new Thread(b).start();

      //call finished by the winner
        }

    public void finished(ThreadRunner firstplace) {

        System.exit(1);
    }
}

```
So i did some searching and read that i should use a volatile bool variable as the way to interupt it, and in my case here i have it so when one of the ThreadTesters distance > 10 it stops the while loop in run, and then sets the bool to false. This is not causing my other thread to stop running though and its  distance is continued to be updated. What am i missing? (the whole finished this is for later use when i call it based off which thread finished first).
Thanks!

---

### Post by PaulM1985 on 2010-04-07
I'm not sure what exactly you wanted to achieve.  I have run the code posted and it is working as I expected it.  Both threads are running to dist == 52 then exiting the while loop.  They then set keepRunning to false and exit the outer while loop.  In effect, the outer while loop is unused.  

Did you want them both of the threads to stop when one of the threads got to greater than 50?

If this is the case I would change it so that instead of:
```

 while (keeprunning) {
        while (this.dist <= 50) {

                this.dist += this.speed;
System.out.println("Thread " + speed + " at " + dist);

            try {
                Thread.sleep(1000); //tries to sleep for a sec
            } catch (InterruptedException ex) { //if interupted
              
                return;
            }
        } //end while loop
        keeprunning = false;
        }//end keeprunning

```

You would have:
```

        while (this.dist <= 50 && keeprunning) {

                this.dist += this.speed;
System.out.println("Thread " + speed + " at " + dist);

            try {
                Thread.sleep(1000); //tries to sleep for a sec
            } catch (InterruptedException ex) { //if interupted
              
                return;
            }
        } //end while loop
        keeprunning = false;

```

and set keeprunning to be static in the class.

Is this what you wanted?

Paul

---

### Post by Xender1 on 2010-04-07
ah yes, that is what I wanted! I changed keeprunning to a volatile to static and now once one thread finishes it sets it to false and the other thread that is running stops too because keeprunning is no longer true. Thank you very much! If I were to look at both of the threads (the one that ran and finished and the one that got interupted) is there a property of the one that got interupted so I would know which one did not finish? like b.interupted() or would both a and b have interupted return true

---

### Post by PaulM1985 on 2010-04-07
I don;t think there will be because the thread wasn't interrupted in a Thread interupt sense, it just stopped processing because a variable was set.  You could include another variable in the class called finished (this would have to be non-static because you want one instance for each class) that would be set if it has exited the loop and keeprunning was true.

Remember that when you are testing that they have finished, you want to have a join function or something similar in the Main thread to wait for both of the two threads to finish.

Paul

---

### Post by Xender1 on 2010-04-07
Ok, my finished ThreadTester is 
```

public class ThreadTester implements Runnable  {
    int speed; int dist; boolean finished;
    static boolean keeprunning = true;

    //CONSTRUCTOR
    ThreadTester(int s) {
        speed = s; dist = 0; finished = false;
    }

    public void run() {
        //a while loop while the distance each has gone is < 1000
        while (this.dist <= 50 && keeprunning) {
            if(keeprunning) {
               this.dist += this.speed;
               System.out.println("Thread " + speed + " at " + dist);
            }
            try {
                Thread.sleep(1000); //tries to sleep for a sec
            } catch (InterruptedException ex) { //if interupted
              
                return;
            }
        } //end while loop
        if (keeprunning) {
            this.finished = true;
            System.out.println("A thread finished!");
        }
        keeprunning = false;
    }
}

```  
I never introduced the join in my main, when I do join do i create a third thread and have that join? or do i simply implement it by having new Thread(b).join() right after calling new Thread(a).start()? because im having a hard time calling finished because if i just have in main after both start.

Here is an idea but join is not a method....which im pretty sure it should be and its saying i need to implement and i have no idea how i would do that, i feel like maybe im just missing an import.
in main
```

        new Thread(t).start();
        t.join();
        new Thread(h).start();
        h.join()

        if (t.finished) {finished(t.name, h.name);}
        if (h.finished) {finished(h.name, t.name);}

```
without the joins it tries to run these two ifs right after calling start instead of waiting for the threads to finish. with the .join() it says i need to implement that method...

---

### Post by Xender1 on 2010-04-07
Wow.....so just finished it...feel pretty dumb about what the problem was (it was the way i made it a thread). So before I had this:
```

ThreadTester a = new ThreadTester(1);
new Thread(a).start();

```
this would make it so if i did a.join() it would have no idea what method join is.
If i implement it in main like this:
```

ThreadTester a = new ThreadTester(1);
Thread mythread = new Thread(a);

```
then i can call a.start() and after a.start i do a.join() and it knows what join is! yaayy! problem solved thanks very much PaulM really helped give me an understanding of some simple thread stuff.

---

### Post by PaulM1985 on 2010-04-08
Hi

From looking at what you have put for the join() stuff, you may want to make the change so that you do both of the start()'s first followed by both of the join()'s.

If you do:
Thread a = new Thread();
Thread b = new Thread();
a.start();
a.join();
b.start();
b.join();

I think this will start a, wait until a joins, then start b and wait until b joins.  So neither of these threads will be running at the same time.

I think what you want is:
a.start();
b.start();
a.join();
b.join();

This way both threads start at the same time and then you wait for them both to finish.  Have a look at the java API: [http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/) and have a look at the thread methods for a bit more info.

Good luck.

Paul

---

