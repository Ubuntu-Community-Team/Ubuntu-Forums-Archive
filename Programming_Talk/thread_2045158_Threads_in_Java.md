---
title: "Threads in Java"
date: 2012-08-20
forum: Programming Talk
---

### Post by Hetepeperfan on 2012-08-20
Hi folks,

I'm not to familiar with threads in java. But I was thinkering with it to improve my understanding of it.

I know that for threading one shouldn't make assumptions about wich thread starts first.

I used three classes: Hello.java, Bye.java and HelloThreads.java. The program starts with the latter. In the main method it runs one of the former two classes concurrently. At least I hoped.
But I'm not joining any threads but somehow it seems that the threads are not running concurrently at all, because the main thread, the Bye thread do not finish before the Hello thread. Since I'm waiting for 1000 ms before printing my hello message I would really expect that Bye and the main thread finish long before Hello. So the behavior I'm getting is not concurrent at all. I would even suspect that the process finishes long before the Hello message is printed.
Thus my question is why does my "program" behaves unconcurently?

the output i'm getting is:
```
$ java HelloThreads
Class Hello says hello.
Class bye says bye.

```Hello.java
```

public class Hello extends Thread {

    public void run ( ) {
        try{
            sleep(1000);
        }
        catch ( Exception e ){

            e.printStackTrace();

        }
        System.out.println( "Class Hello says hello." );
    }
}

```Bye.java

```
public class Bye implements Runnable {

    public void run ( ) {
        System.out.println( "Class bye says bye." );
    }
}

```and finally



```
public class HelloThreads {
    
    public static void main ( String args[] ){

        Hello hellos = new Hello();
        Bye bye = new Bye();

        Thread goodbye = new Thread( bye );

        hellos.run();
        goodbye.run();

    }
}

```So the behavior I'm getting is like I joined the Hello.run() thread. then the Bye.run gets joined. and then my program finishes. So it acts like I synchronized the threads, but I didn't. Would anyone please explain

kind regards,

Maarten

---

### Post by myrtle1908 on 2012-08-20
You should be calling start() not run().

Common mistake is to call the run() method of the Thread instead of start().

This is because the run() method is executed by the thread that created the thread.

```

hellos.start();
goodbye.start();

```

---

### Post by Hetepeperfan on 2012-08-21
> **myrtle1908 said:**
> You should be calling start() not run().

Common mistake is to call the run() method of the Thread instead of start().

This is because the run() method is executed by the thread that created the thread.

```

hellos.start();
goodbye.start();

```

But of course, thank you for pointing that out, make perfect sense!

---

### Post by Hetepeperfan on 2012-08-21
Still I've got one more question on this java threading issue.

I've changed the .run() to the start() as was mentioned and now .

And the output is:
```
$ java HelloThreads
Class bye says bye.
Class Hello says hello.
```However the main class seems to wait kindly until the Hello class has finished sleeping and printing it's hello message. Is this normal in java? Being used to C++ and C with pthreads my process should finish before the Hello instance finishes sleeping ending the process and thereby "killing" the Hello instance. I would expect I should join the Hello instance - which I didn't -, but it still behaves like it's being joined.

Any suggestions?

---

### Post by spjackson on 2012-08-21
> **Hetepeperfan said:**
> However the main class seems to wait kindly until the Hello class has finished sleeping and printing it's hello message. Is this normal in java? Being used to C++ and C with pthreads my process should finish before the Hello instance finishes sleeping ending the process and thereby "killing" the Hello instance. I would expect I should join the Hello instance - which I didn't -, but it still behaves like it's being joined.
The JVM waits for all threads to end before exiting. You only need to join in Java if you want to do something in the main thread after the other threads complete. Yes, this is different from Posix threads in C/C++.

---

### Post by Hetepeperfan on 2012-08-21
> **spjackson said:**
> The JVM waits for all threads to end before exiting. You only need to join in Java if you want to do something in the main thread after the other threads complete. Yes, this is different from Posix threads in C/C++.


Thanks a lot!!

---

