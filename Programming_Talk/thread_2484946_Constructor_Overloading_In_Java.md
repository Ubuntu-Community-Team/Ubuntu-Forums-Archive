---
title: "Constructor Overloading In Java"
date: 2023-03-15
forum: Programming Talk
---

### Post by ronakmehta on 2023-03-15
So I had began learning Java and am currently utilising it as my language of choice in my university's Concurrent Programming class.

First of all here is the code:

```
[COLOR=var(--highlight-keyword)][FONT=inherit]import[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] java.util.concurrent.CountDownLatch;[/FONT][/COLOR]

[COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]Lab1[/FONT][/COLOR]{

[COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]static[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]main[/FONT][/COLOR][FONT=inherit](String[] args)[/FONT]{

    [COLOR=var(--highlight-namespace)][FONT=inherit]CountDownLatch[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]leftLatch[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]CountDownLatch[/FONT][/COLOR]([COLOR=var(--highlight-namespace)][FONT=inherit]3[/FONT][/COLOR]);
    [COLOR=var(--highlight-namespace)][FONT=inherit]CountDownLatch[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]midLatch[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]CountDownLatch[/FONT][/COLOR]([COLOR=var(--highlight-namespace)][FONT=inherit]1[/FONT][/COLOR]);

    [COLOR=var(--highlight-namespace)][FONT=inherit]LabThread[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]t1[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]LabThread[/FONT][/COLOR]();
    [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]Thread[/FONT][/COLOR](t1).start();

    [COLOR=var(--highlight-comment)][FONT=inherit]// (new Thread(new LabThread(new CountDownLatch(1),leftLatch,1))).start();[/FONT][/COLOR]
    [COLOR=var(--highlight-comment)][FONT=inherit]// (new Thread(new LabThread(new CountDownLatch(0),leftLatch,2))).start();[/FONT][/COLOR]
    [COLOR=var(--highlight-comment)][FONT=inherit]// (new Thread(new LabThread(new CountDownLatch(0),leftLatch,3))).start();[/FONT][/COLOR]
    [COLOR=var(--highlight-comment)][FONT=inherit]// (new Thread(new LabThread(leftLatch,midLatch,4))).start();[/FONT][/COLOR]
 [COLOR=var(--highlight-comment)][FONT=inherit]//     (new Thread(new LabThread(midLatch,new CountDownLatch(0),5))).start();[/FONT][/COLOR]
    [COLOR=var(--highlight-comment)][FONT=inherit]// (new Thread(new LabThread(midLatch,new CountDownLatch(0),6))).start();[/FONT][/COLOR]
    [COLOR=var(--highlight-comment)][FONT=inherit]// (new Thread(new LabThread(midLatch,new CountDownLatch(0),7))).start();[/FONT][/COLOR]
}
}

[COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]LabThread[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]implements[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]Runnable[/FONT][/COLOR]{

[COLOR=var(--highlight-namespace)][FONT=inherit]CountDownLatch[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]waitLatch[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-literal)][FONT=inherit]null[/FONT][/COLOR];
[COLOR=var(--highlight-namespace)][FONT=inherit]CountDownLatch[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]decLatch[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-literal)][FONT=inherit]null[/FONT][/COLOR];
[COLOR=var(--highlight-namespace)][FONT=inherit]int[/FONT][/COLOR] threadNr;

[COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]LabThread[/FONT][/COLOR][FONT=inherit](CountDownLatch waitLatch, CountDownLatch decLatch,[COLOR=var(--highlight-namespace)][FONT=inherit]int[/FONT][/COLOR] threadNr)[/FONT]{
    [COLOR=var(--highlight-literal)][FONT=inherit]this[/FONT][/COLOR].waitLatch = waitLatch;
    [COLOR=var(--highlight-literal)][FONT=inherit]this[/FONT][/COLOR].decLatch = decLatch;
    [COLOR=var(--highlight-literal)][FONT=inherit]this[/FONT][/COLOR].threadNr = threadNr;
}

[COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]run[/FONT][/COLOR][FONT=inherit]()[/FONT]{
    [COLOR=var(--highlight-keyword)][FONT=inherit]try[/FONT][/COLOR]{
        [COLOR=var(--highlight-literal)][FONT=inherit]this[/FONT][/COLOR].waitLatch.await();
        [COLOR=var(--highlight-literal)][FONT=inherit]this[/FONT][/COLOR].decLatch.countDown();
    }[COLOR=var(--highlight-keyword)][FONT=inherit]catch[/FONT][/COLOR] (InterruptedException e) {
        e.printStackTrace();
    }
    System.out.println(threadNr);
} [COLOR=var(--highlight-color)][FONT=inherit]}[/FONT][/COLOR]
```

I've been working on a lab project that requires me to start and execute a few threads in a precise order.

When I try to compile, I receive the following error:

```
[COLOR=var(--highlight-color)][FONT=inherit]Lab1.java:[/FONT][/COLOR][COLOR=var(--highlight-namespace)][FONT=inherit]12[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit]: error: constructor Thread in [/FONT][/COLOR][COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] [/FONT][/COLOR][COLOR=var(--highlight-literal)][FONT=inherit]Thread[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] cannot be applied to given types;[/FONT][/COLOR]    [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]Thread[/FONT][/COLOR](t1).start();
    ^
required: CountDownLatch,CountDownLatch,[COLOR=var(--highlight-namespace)][FONT=inherit]int[/FONT][/COLOR]
found: LabThread
reason: actual and formal argument lists differ in length [COLOR=var(--highlight-namespace)][FONT=inherit]1[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] error[/FONT][/COLOR]
```

I realise it's quite obvious, but I haven't been able to discover a fix. I tried everything: removing the overloaded constructor, extending Thread instead of implementing Runnable as suggested in the [source]("https://www.scaler.com/topics/constructor-overloading-in-java/"), everything I thought could help, but it just continues pestering me with this same problem, and it's becoming ridiculous. If you have a solution, please share your knowledge with me!

---

