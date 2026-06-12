---
title: "Why do we have to use assert() with mutexes?"
date: 2009-11-23
forum: Programming Talk
---

### Post by Koalano on 2009-11-23
Hi! I'm new to thead programming and I have a question. 

I'm reading an example. This example illustrates condition variables in the context of producers and consumers. You create a producer thread that creates work and then N consumer threads that operate on the (simulated) work.

Here is a code snippet of one of the consumers:

```
    while( 1 ) {
      assert( pthread_mutex_lock( &cond_mutex ) == 0);
      assert( pthread_cond_wait( &condition, &cond_mutex )
      == 0 );

   if (workCount) {
     workCount—;
     printf( “Consumer %x: Performed work (%d)\n”,
               pthread_self(), workCount );
   }
   assert( pthread_mutex_unlock( &cond_mutex ) == 0);

 }
```My question is why do we have to use assert() in this snippet? In this case, the consumer will abort if the mutex is not available. 

If we don't use assert(), the consumer just waits for the mutex to be available and then do the work. Wouldn't this be the behavior we expect from a consumer?

Thanks for reading my question.

Regards,

Koalano

---

### Post by JBAlaska on 2009-11-23
The assert() statement; unless the code is compiled with NDEBUG defined, assert() does nothing when its argument evaluates to true (that is, nonzero), but causes the program to abort if the argument evaluates to false (zero). Such assertions are especially useful in multithreaded programs--they immediately point out runtime problems if they fail, and they have the additional effect of being useful comments. 

Using invariants is an extremely useful technique. Even if they are not stated in the program text, think in terms of invariants when you analyze a program.

The invariant in the producer code that is expressed as a comment is always true whenever a thread is in the part of the code where the comment appears. If you move this comment to just after the mutex_unlock(), this does not necessarily remain true. If you move this comment to just after the assert(), this is still true. 

Like So:
```
char consumer(buffer_t *b)
{
    char item;
    pthread_mutex_lock(&b->mutex);
    while(b->occupied <= 0)
        pthread_cond_wait(&b->more, &b->mutex);

    assert(b->occupied > 0);

    item = b->buf[b->nextout++];
    b->nextout %= BSIZE;
    b->occupied--;

    /* now: either b->occupied > 0 and b->nextout is the index
       of the next occupied slot in the buffer, or
       b->occupied == 0 and b->nextout is the index of the next
       (empty) slot that will be filled by a producer (such as
       b->nextout == b->nextin) */

    pthread_cond_signal(&b->less);
    pthread_mutex_unlock(&b->mutex);

    return(item);

```

See?..Easy!

---

### Post by Koalano on 2009-11-23
Thanks for your answer.

I just misunderstand the meaning of the way pthread_mutex_lock() works. Initially I thought that if the mutex is not available, the function will return a non-zero value, causing assert() to terminate the program. However, the truth is that, even when the mutex is not available, pthread_mutex_lock() still does not return a non-zero value, it just waits for the mutex, and when it becomes available, my program continues normally.

Regards,

Koalano.

---

