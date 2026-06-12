---
title: "How to make a random number in c++"
date: 2006-12-03
forum: Programming Talk
---

### Post by thenetduck on 2006-12-03
Hi, 
  I am making a program in c++ that requires a lot of random numbers between 0 - 1 so I was using this code to make a random number

```

int random = rand() % 2;

```


This does great when I run my program, however if I re compile the program and run it again, it gives me the same series of random numbers. Is there any way to make it give me a different series of random numbers? 

 thanks, 

 The Net Duck

---

### Post by atoponce on 2006-12-03
You need to set a seed that changes on each pass.  Something like the system timestamp.  Then call sand(time(NULL)), and it should change for you.  I don't recall what it is currently looking at when just calling rand(); natively.

---

### Post by yabbadabbadont on 2006-12-03
[http://www.cplusplus.com/ref/cstdlib/srand.html](http://www.cplusplus.com/ref/cstdlib/srand.html)

---

### Post by emix on 2006-12-03
You have to set the seed for the generator. You can use "srand(time(NULL))" before using the rand function.

"man srand" for info ;)

---

### Post by autoexec on 2006-12-03
[already said]

---

### Post by Verminox on 2006-12-03
although "srand(time(NULL))" is a common method... it is of no use if you want to generate say 10 random numbers instantly. This is because time() returns the UNIX timestamp in seconds.... and due to the processor speed this may actually always be the same.

What I usually do is... make a custom randomizer function... and each time a random number is generated... that number is stored within the function as a static member... and it is used along with time() to seed the next randomization.

eg.

```
int random(){
  static int last = 0;
  srand( time(NULL) + last );
  last = rand();
  return last;
}
```

---

### Post by yabbadabbadont on 2006-12-03
You only need to seed the generator once.  Then you should hit the rand function a couple thousand (yes thousand) times so that the algorithm will settle down.  Most pseudo-random number algorithms produce better results farther in than those returned initially.  (I had a professor whose PHD work was on pseudo-random number generating algorithms...  He loved talking about them.)

---

### Post by thenetduck on 2006-12-03
wow you guys have been a lot of help. Is there a reason why the people who build the main c++ compiler doesn't incoperate somethign simular to Verminox's solution right off of the bat? 

 Once again, thanks.

 The Net Duck

---

### Post by Verminox on 2006-12-03
I'm guessing to save processign time. As yabbadabbadont said, you can probably use the rand function many times after just seeding it once.... So unless anyone wants to generate many many random numbers at once, I think a single seed should do the trick.

Come to think of it... there are probably better solutions to getting many random numbers than my code... too much of srand() might slow down the program by a bit.

If you just want to randomize some really small amount of data, then one seeding at the start of the program should suffice.

---

### Post by shining on 2006-12-03
> **Verminox said:**
> I'm guessing to save processign time. As yabbadabbadont said, you can probably use the rand function many times after just seeding it once.... So unless anyone wants to generate many many random numbers at once, I think a single seed should do the trick.

Come to think of it... there are probably better solutions to getting many random numbers than my code... too much of srand() might slow down the program by a bit.

If you just want to randomize some really small amount of data, then one seeding at the start of the program should suffice.

From the man page:
> 
       The rand() function returns a pseudo-random integer between 0 and RAND_MAX.

       The  srand() function sets its argument as the seed for a new sequence of pseudo-random integers to be returned by rand().  These sequences are repeatable
       by calling srand() with the same seed value.

       If no seed value is provided, the rand() function is automatically seeded with a value of 1.


It doesn't tell anything about the length of the sequence. If there is no cycle, I don't see any reasons for calling srand() more than once, even for generating many random numbers. If there is one, then it depends on the length of the cycle compared to the numbers you need to generate.

The only thing that matters is if you want to have a different output between 2 executions of your program, you'll need to initialize the seed with a different value at each execution, and using the current time seems to be the natural way.
Unless you can only get the current time in seconds, and you launch your program several times by second. But that seems very unlikely.

---

### Post by hod139 on 2006-12-03
For more advanced pseudo random number generators see [boost]("http://www.boost.org/libs/random/random-generators.html").  They are more complicated to use, but provide better/more advanced algorithms.

---

