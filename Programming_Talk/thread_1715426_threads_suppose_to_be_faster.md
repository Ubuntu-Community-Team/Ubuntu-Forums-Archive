---
title: "threads suppose to be faster"
date: 2011-03-26
forum: Programming Talk
---

### Post by raac on 2011-03-26
Hello guys, Can someone tell me why the serial version of this program is running faster than the thread version

struct x{
 int s;
 int z;
}

void *someFunction(void *var){
.....
}

//Serial Version

struct x var;

//start timing
for(i = 0; i < 7; i++){
   var.s = 10;
   var.z = 20;
   someFunction(&var)
}
//end timing
-------------------------------------------------------
the following code happens to be slower in a dual core machine
I don't understand why, the following one creates threads
so it's suppose to be faster... Please help.

//Thread version
pthread_t thre;
struct x *var;
var=malloc(sizeof(x));
//start timing
for(i=0; i < 7; i++){
   var->s=10;
   var->z=20;
   lpthread_create(&thre, NULL, someFunction, (void *) var);
   lpthread_join(thre, NULL);
}
//end timing

---

### Post by Some Penguin on 2011-03-27
Call join after you create *all* the threads.

---

### Post by raac on 2011-03-27
Indeed, if I do


   for(i = 0 ; i < n; i++){
      solu->n = n;
      solu->out_flag = FALSE;
      solu->first = i;
      pthread_create(&tid, NULL, queen_thread, (void *) solu);
   }
   pthread_join(tid, NULL);

It will faster, although it is acting weird


somefunction(), prints the value of solu->n, if I do the join inside the loop it will correctly print out n.
Ex.

0
1
2
3
4
5
6

but, if I do the join outside the loop it will print
1
3
2
6
6
6
6

Can someone explain me what is going on?

---

### Post by NovaAesa on 2011-03-27
If you have the "join" inside the loop, you are basically saying:

Start thread 1, wait until it's done.
Start thread 2, wait until it's done.
Start thread 3, wait until it's done.
Start thread 4, wait until it's done.
Start thread 5, wait until it's done.
Start thread 6, wait until it's done.

If you stick the "join" outside the loop, you are saying:

Start thread 1.
Start thread 2.
Start thread 3.
Start thread 4.
Start thread 5.
Start thread 6.
Wait until threads 1, 2, 3, 4, 5, and 6 are done.

Note that if you call join outside the loop, you should call it for all of the threads, so you will need to keep track of all the tids.

And your odd behaviour with getting multiple sixes would be due to modifying shared data within somefunction() without the use of mutexes/semaphores. Basically, it looks like two or more threads are accessing the data at once and are unable to cooperate with it. It's somewhat hard to really tell what's going on without seeing all the code. Also, could you use code tags?

---

### Post by raac on 2011-03-27
Well, my program does not have global variables, so it should not affect the values between the threads right??..I just wanted to understand what I'm doing wrong. My code is messy, somefunction() calls another functions but do not share global variables, so I thought it would be me messy to put everything here

---

### Post by raac on 2011-03-27
> Note that if you call join outside the loop, you should call it for all of the threads, so you will need to keep track of all the tids.

 
Should I put another "for" loop after my current "for" loop to iterate 7 times, and call join inside of it?? How would I keep track of the tids??

---

### Post by NovaAesa on 2011-03-27
It looks like you are passing in a pointer named "solu"/"var" to "queen_thread"/"somefunction". Inside "queen_thread"/"somefunction" does the memory at the end of "solu"/"var" get updated? If so, that is your shared data in question.

Yeah, a for loop would do it. Just stick them in an array or other data structure - the correct data structure would really depend on what else you want to do with the tids, and whether there is a fixed number of threads etc.

---

### Post by t1497f35 on 2011-03-27
When using (posix) threads you have to know (exactly) what you're doing otherwise you'll sooner or later run into (extremely) hard to debug issues which might only show up on the client's system for various reasons.
So I'd suggest you read [Butenhof's book]("http://www.amazon.com/Programming-POSIX-Threads-David-Butenhof/dp/0201633922"), the book is slightly old but the stuff it covers is not.

I know reading a whole book just for the sake of pthreads seems unreasonable, but it actually is, since you'll understand all bells and whistles behind the decisions in other thread wrappers (around posix) and implementations.

---

### Post by raac on 2011-03-27
Ok I messed it up, I don't have two different functions nor two different variables
 
```

Indeed, if I do


for(i = 0 ; i < n; i++){
solu->n = n;
solu->out_flag = FALSE;
solu->first = i;
pthread_create(&tid, NULL, somefunction, (void *) var);
}
pthread_join(tid, NULL);
 

```

 
I just ran it again and it did not even printed out the 7 numbers
 
```

1
2
6
6
6

```

> Inside "queen_thread"/"somefunction" does the memory at the end of "solu"/"var" get updated? 
 
You mean like local variables??

---

### Post by raac on 2011-03-27
Ok ```


-------------------------------------------------
struct x{
   int a;
   int b;
   int c;
   int d;
};
-------------------------------------------------
void *somefunction(void *par){
   struct x var;
   var = *(struct x *) par;
   var->d = otherFunction(var->a,var->b,var->c);
}
-------------------------------------------------
struct x * var;
pthread_t tid;
pthread_t tidArray[7];
for(i = 0 ; i < 7; i++){
   var->a = 7;
   var->b = 1;
   var->first = i;
   pthread_create(&tid, NULL, somefunction, (void *) var);
   tidArray[i] = tid;
}

for(int i = 0; i < 7; i++){
   pthread_join(tidArray[i], NULL);
}

```

Neither var->a, nor var->b, nor var->c get updated in the function 'somefunction'. Only var->d, will may be different after some calculation.

---

### Post by dwhitney67 on 2011-03-27
> **raac said:**
> 
I just ran it again and it did not even printed out the 7 numbers


You seem like a brilliant kid, but you are killing us with your refusal to post the CODE of what is transpiring in some_function(), or queen_thread().

Please post your CODE using CODE tags!  Look for the # icon on the upper right of the reply box.

Unless you know otherwise, usage of printf() (or std::cout) are typically regarded as *not* being thread-safe.  On some systems they might be, but there is no guarantee.

Here's a simple application in which all of the data is outputted:
```

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <unistd.h>

struct Foo
{
   int x, y;
};

void* some_function(void* arg)
{
   struct Foo* foo = (struct Foo*) arg;

   for (int i = 0; i < foo->x; ++i)
   {
      printf("thread %lu: %d\n", pthread_self(), i+1);

      usleep((rand() % 10) * 1000);  /* artificial load */
   }

   return NULL;
}

int main(void)
{
   struct Foo foo = { 6, 0 };
   pthread_t  tids[4];

   srand(time(0));

   for (int i = 0; i < 4; ++i)
   {
      pthread_create(&tids[i], NULL, some_function, &foo);
   }

   for (int i = 0; i < 4; ++i)
   {
      pthread_join(tids[i], NULL);
   }

   return 0;
}

```

---

