---
title: "Question about the nextInt() method"
date: 2010-05-26
forum: Programming Talk
---

### Post by s3a on 2010-05-26
Edit: This is a question about Java.

Here is some code I copied (with a few added comments) from a video I'm watching (My question is about what's bolded):

```
import java.util.Random;

public class learningThreads implements Runnable
{
    String name;
    int time;
**    Random r = new Random();**
    
    public learningThreads(String x)
    {
        name = x;
**        time = r.nextInt(999);**
    }
    
    public void run()
    {
        try
        {
            System.out.printf("%s is sleeping for %d\n", name, time);
            Thread.sleep(time);
            System.out.printf("%s is done\n", name);
        }
        catch(Exception e){}
    }
    
    public static void main(String[] args)
    {
        // The following creates threads but are not yet started to be used
        Thread t1 = new Thread(new learningThreads("one"));
        Thread t2 = new Thread(new learningThreads("two"));
        Thread t3 = new Thread(new learningThreads("three"));
        Thread t4 = new Thread(new learningThreads("four"));
        
        // The following starts each thread above
        t1.start();
        t2.start();
        t3.start();
        t4.start();
    }

}
```

At first, I thought the purpose of the nextInt() method is to give an integer to the object that calls it but then I noticed that instead of giving it a specific integer, the integer being set is an interval with that specific integer being the end of the interval. I was just hoping someone could explain that part to me in a little more detail.

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by simeon87 on 2010-05-27
Yes, nextInt(n) gives a random integer in the interval 0 till and including n - 1. Full details can be found [here]("http://java.sun.com/javase/6/docs/api/java/util/Random.html#nextInt%28int%29").

---

### Post by s3a on 2010-05-27
That answered my question :) Also, I didn't know the integer it sends is [0,n) or [0,n-1]. Thanks a lot!

---

### Post by LKjell on 2010-05-27
> **s3a said:**
> That answered my question :) Also, I didn't know the integer it sends is [0,n) or [0,n-1]. Thanks a lot!

[0,n) or [0,n-1] is the same when you are talking about integers.

---

### Post by s3a on 2010-05-28
I know; I was just trying to say it in my own words but thanks.

---

