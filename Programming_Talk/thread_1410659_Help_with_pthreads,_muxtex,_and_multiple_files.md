---
title: "Help with pthreads, muxtex, and multiple files"
date: 2010-02-19
forum: Programming Talk
---

### Post by slackjack on 2010-02-19
Hey,

I'm new to pthreads.

Here is what I'm trying to do. There are two files consisting of a bunch of single column numbers. I want to do a line by line comparison between the files.

So far I'm trying to open each file in a separate thread and third thread does the comparison. I have [self] discovered that the threads for reading files dont execute in parallel as I thought they would. So it seems mutex would solve this. I can run one thread to read one line, then the second thread to read the one line from the other file (and store the value in a temp variable), then the third does the comparison, and repeat till EOF.

But all this overhead is a little too much for be to grasp. Firstly, how can I read two files from (one) threaded function line by line? I had done it by using a for loop till the end of file was met for both files. If I use mutex lock/unlock on the loop which reads the file, then that loop would have to finish executing then unlock! How can I do this line by line thing?

Thanks.

---

### Post by Simon17 on 2010-02-19
slackjack, Can I ask you how big the files you're reading are?

A mutex doesn't sound like the answer to your problem. If the files are small, it's likely that the OS is letting one thread read the file completely before switching to the other thread.

Feel free to post the parts of your code that you think are problematic as well.

---

### Post by slackjack on 2010-02-19
Hi Simon,

The files can range anywhere from 2000 lines to several hundred thousand lines (may even approach a million). In any case, both files will have the same number of lines.

This is the part of the code that reads the file line by line
```

args1 = (struct thread_args *) ptr;
char *filename = args1->f_name;
FILE *file = fopen ( filename, "r" );
printf("reading file %s\n",filename);
if ( file != NULL )
 {
   char line [8]; /* or other suitable maximum line size */

   while ( fgets ( line, sizeof line, file ) != NULL ) /* read a line */
	{
	    args1->lineVal = atof(line);
	    printf("%f\n", args1->lineVal);
        }
     fclose ( file );
 }

```
If I sandwich the above snippet with mutex lock/unlock, then it makes no difference as the entire file is read, then control is passed to the other thread to read the other file. I need however, one thread to read one line at a time.

---

### Post by Simon17 on 2010-02-19
You need each thread to read one line at a time?

If you mean what I think you mean, then you shouldn't be using threads.

You have no way to determine or control the scheduling of the threads. If you need the threads to wait for each other to read one line at a time, then you might as well read both files in a single thread.

---

### Post by dwhitney67 on 2010-02-19
> **Simon17 said:**
> You need each thread to read one line at a time?

If you mean what I think you mean, then you shouldn't be using threads.

You have no way to determine or control the scheduling of the threads. If you need the threads to wait for each other to read one line at a time, then you might as well read both files in a single thread.

+1

If the OP is merely interested in learning multi-threading, then he should choose to develop a different application.  The file-comparison app should be done in a single-thread.

---

### Post by slackjack on 2010-02-19
Thank you both.

Well I'm trying to do this to cut down on the time needed to read the files. That is, compare them on a line-by-line basis to avoid making arrays to hold the data of both files (remember there may be millions of lines). I'm trying to cut back on this because the target machine is an embedded system. Also, comparing them line-by-line gives a sort of a real-time feel to it, which is what I'm also after.

Please advise guys.

---

### Post by dwhitney67 on 2010-02-19
The most trivial way to compare two files in C, in a single thread:
```

#include <stdio.h>
#include <string.h>

int main(int argc, char** argv)
{
   FILE* file1 = fopen(argv[1], "r");
   FILE* file2 = fopen(argv[2], "r");

   /* do error checking here to ensure both files are open */
   if (!file1 || !file2)
   {
      fprintf(stderr, "Error: Could not open the specified file(s).\n");
      return -1;
   }

   char buf1[1024] = {0};
   char buf2[1024] = {0};
   int  same       = 1;    // assume files are the same until proven otherwise

   while (!feof(file1) || !feof(file2))
   {
      int bytes1 = fread(buf1, 1, sizeof(buf1), file1);
      int bytes2 = fread(buf2, 1, sizeof(buf2), file2);

      if ((bytes1 != bytes2) || (memcmp(buf1, buf2, bytes1) != 0))
      {
         same = 0;
         break;
      }
   }

   if (same)
   {
      fprintf(stdout, "Files are the same.\n");
   }
   else
   {
      fprintf(stderr, "Files are NOT the same.\n");
   }

   return 0;
}

```

P.S.

> **slackjack said:**
> Thank you both.

Well I'm trying to do this to cut down on the time needed to read the files. That is, compare them on a line-by-line basis to avoid making arrays to hold the data of both files (remember there may be millions of lines). I'm trying to cut back on this because the target machine is an embedded system. Also, comparing them line-by-line gives a sort of a real-time feel to it, which is what I'm also after.

Please advise guys.

I don't think you quite understand what it takes to read a file; one must read it, either a byte at a time (very inefficient), or in large chunks.  Accessing the HDD will be the biggest drain on efficiency.  Whether the target is embedded or not, really makes no difference in this case.

---

### Post by slackjack on 2010-02-19
Thanks for the input dwhitney67.

What about reading both files in one thread and after each fread() a second thread could be called for comparison? But the mechanics of threads seems like it won't allow a comparison per fread() in a different thread. I can see that all this can be done without a separate thread, heck, we dont even need threads for this. But I'm curious on using threads to partially solve this problem.

---

### Post by dwhitney67 on 2010-02-19
> **slackjack said:**
> Thanks for the input dwhitney67.

What about reading both files in one thread and after each fread() a second thread could be called for comparison? But the mechanics of threads seems like it won't allow a comparison per fread() in a different thread. I can see that all this can be done without a separate thread, heck, we dont even need threads for this. But I'm curious on using threads to partially solve this problem.

You could launch a thread whose sole purpose is to compare an array of data with another, however as I stated earlier, this will not buy much because the biggest drain of performance will be accessing the HDD where the data lives.  In other words, a separate would be sitting mostly idle while waiting for the fread() to complete.

I have limited knowledge of when to use threads; most of my experience with such has been with socket programming (server/client).

---

### Post by Simon17 on 2010-02-19
Perhaps while reading in the files you could dump all the data into two arrays and then you could split up the arrays and start a couple of threads to do the comparisons?

---

### Post by slackjack on 2010-02-19
But I am unsure of how the sequencing and scheduling would work for this (separate thread for comparison). From what I've seen, if I make two threads in main(). The first one would read the files, and the second (for comparison) won't run until after the first thread is completed, and not in parallel.

---

### Post by MadCow108 on 2010-02-19
you could have the reader thread dump the read lines into the a FIFO queue and have the compare thread read from the other end.

This can even be done without locks for single provider/single consumer queues.
But using locks will not harm the performance as long as you only do simple stuff like comparing.
The io of the reader thread will be your performance bottleneck (resulting in the queue being empty most of the time).

---

### Post by dwhitney67 on 2010-02-19
> **slackjack said:**
> But I am unsure of how the sequencing and scheduling would work for this (separate thread for comparison). From what I've seen, if I make two threads in main(). The first one would read the files, and the second (for comparison) won't run until after the first thread is completed, and not in parallel.

When running "producer" and "consumer" threads, always start the consumer thread first.

In your case, if you decide to pursue a multi-threaded approach, use MadCow108's suggestion for a queue (eg. a message queue is thread-safe), and have the compare-thread (consumer) pop from the queue, and the file-reader (producer) insert to the queue.

Maybe tonight or tomorrow, if I have nothing to do, I will throw together an app using these concepts.

---

### Post by slackjack on 2010-02-19
Hi dwhitney67, I'd appreciate it if you could take the time to put together a quick demo. I'll grab a copy of pthread primer and read up on the concepts that MadCow108 alluded to.

Cheers.

---

### Post by MadCow108 on 2010-02-19
this is a small example of a producer reading lines and pushing them on a locked "stack" and a producer reading from it.

I was to lazy to use a proper fifo (or a message queue as dwhitney suggested) so I used this primitive stack structure (lifo) which means the order of read lines will not be preserved  (it is even random as its dependent on thread scheduling) [and max 1000 lines input file]

```
#include <pthread.h>
#define _GNU_SOURCE
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;
static char file[] = "test.txt";

typedef struct stack {
  char * storage[1000];
  int top;
} stack;

static stack s =  {0};

void* producer_thread(void* arg) {
  puts("starting producer");
  FILE * f = fopen(file, "r");
  char * line = NULL;
  size_t len = 0;
  ssize_t read;
  int read_lines=0;
  while ((read = getline(&line, &len, f)) != -1) {
    // lock the stack to modify it
    pthread_mutex_lock(&mutex);
    printf("producer data on stack %d: %s",s.top, line);
    s.storage[s.top] = strdup(line);
    s.top++;
    pthread_mutex_unlock(&mutex);
    read_lines++;
    int i;
    // burn cycles to mix thread ordering a bit
    for (i = 0; i < rand()/2 + 500000; i++);
  }
  if (line)
    free(line);
  printf("producer end, read %d lines\n", read_lines);
}

void* consumer_thread(void* arg) {
  puts("starting consumer");
  char * line;
  int read_lines = 0;
  while (1) {
    if (s.top != 0) {
      // lock the stack to modify it
      pthread_mutex_lock(&mutex);
      line = s.storage[s.top-1];
      s.top--;
      printf("\tconsumer data in stack %d: %s", s.top, line);
      pthread_mutex_unlock(&mutex);
      read_lines++;
      int i;
      // burn cycles to mix thread ordering a bit
      for (i = 0; i < rand(); i++);
      if (line)
        free(line);
    }
    else {
      printf(" read %d. Nothing new there, sleeping\n", read_lines);
      sleep(1);
    }
  }
}

int main() {
  pthread_t producer;
  pthread_t consumer;
  
  pthread_create(&producer, NULL, producer_thread, NULL);
  pthread_create(&consumer, NULL, consumer_thread, NULL);

  pthread_join(producer, NULL);
  pthread_join(consumer, NULL);
  return 0;
}

```

instead of just sleeping you could also use conditionals to wake up the consumer thread when there is new data to read.

note: this is just a quick prototype to illustrate the concept. It may be working incorrectly.
Do not use that code for your project without major overhaul.

---

### Post by dwhitney67 on 2010-02-20
Here's my attempt, but using C++.  Using C is just too archaic for these matters.

Note, the following code will not compile; it is merely for demonstration purposes only.
```

#include "liteboost/thread/thread.hpp"
#include "liteboost/thread/mutex.hpp"
#include <fstream>
#include <queue>
#include <algorithm>
#include <iostream>
#include <stdexcept>

template <typename T>
class Queue
{
public:
   Queue() {}

   void insert(T* data)
   {
      liteboost::mutex::scoped_lock lock(mutex);

      dataQueue.push(data);
   }

   T* pop()
   {
      liteboost::mutex::scoped_lock lock(mutex);

      T* data = 0;

      if (dataQueue.size() > 0)
      {
         data = dataQueue.front();
         dataQueue.pop();
      }

      return data;
   }

private:
   std::queue<T*>   dataQueue;
   liteboost::mutex mutex;
};

struct Data
{
   char   data1[1024];
   char   data2[1024];
   size_t data1_size;
   size_t data2_size;
};


class Reader
{
public:
   Reader(const char* filename1, const char* filename2, Queue<Data>& q)
      : file1(filename1, std::ios::in),
        file2(filename2, std::ios::in),
        queue(q)
   {
      if (!file1 || !file2)
      {
         throw std::runtime_error("Error: Cannot open the specified file(s).");
      }
   }

   void operator()()
   {
      while (file1 && file2)
      {
         Data* d = new Data;

         file1.read(d->data1, sizeof(d->data1));
         d->data1_size = file1.gcount();

         file2.read(d->data2, sizeof(d->data2));
         d->data2_size = file2.gcount();

         queue.insert(d);
      }

      // send packet indicating no more data; this will terminate the comparer thread
      Data* d = new Data;
      d->data1_size = 0;
      d->data2_size = 0;
      queue.insert(d);
   }

private:
   std::fstream file1;
   std::fstream file2;
   Queue<Data>& queue;
};

class Comparer
{
public:
   Comparer(Queue<Data>& q) : same(true), queue(q) {}

   void operator()()
   {
      bool done = false;

      while (!done)
      {
         Data* d = queue.pop();

         if (d)
         {
            if (d->data1_size == 0 && d->data2_size == 0)
            {
               done = true;
            }
            else if ((d->data1_size != d->data2_size) ||
                     !std::equal(d->data1, d->data1 + d->data1_size, d->data2))
            {
               same = false;
            }

            delete d;
         }
         else
         {
            usleep(5000);
         }
      }
   }

   bool isSame() const
   {
      return same;
   }

private:
   bool         same;
   Queue<Data>& queue;
};


int main(int argc, char** argv)
{
   using namespace std;
   using namespace liteboost;

   if (argc != 3)
   {
      cerr << "Usage: " << argv[0] << " <file1> <file2>" << endl;
      return -1;
   }

   try
   {
      Queue<Data> queue;
      Reader      reader(argv[1], argv[2], queue);
      Comparer    comparer(queue);

      thread_group threads;
      threads.add_thread(new thread(reader));
      threads.add_thread(new thread(comparer));

      threads.join_all();

      if (comparer.isSame())
      {
         cout << "The files are the same." << endl;
      }
      else
      {
         cerr << "The files are NOT the same." << endl;
      }
   }
   catch (exception& e)
   {
      cerr << e.what() << endl;
      return -1;
   }

   return 0;
}

```

P.S.  "liteboost" is home-made code that derives upon pthreads, and is modeled after the Boost thread library.  One could easily substitute the real Boost library in its place.

---

### Post by slackjack on 2010-02-20
Thanks for the code guys! :)

MadCow108, the for() loops gives both threads a chance to execute without one thread having to fully complete its execution, which was my initial problem. But a lot of time is wasted in waiting for the loops to finish. Either it compares the same lines several times, or doesnt get enough time to do compare all lines. I'll try to put together some conditional variables and see if I can pull it off. 

dwhitney67, its gonna take me some time to go through your code and understand it. My C++ is a bit weak :p

Thanks again.

---

### Post by slackjack on 2010-02-21
I'm using conditional variables to achieve a great deal of synchronization (pthread_cond_signal() and pthread_cond_wait() ). The calling thread calls nanosleep() to give other threads (the comparator thread) a chance to execute. But what I've noticed is that, not all lines are compared. Anywhere from 97%-100% is compared. I would like to always have a 100% hit. I tried playing with the delay in nanosleep() but it gets worse with smaller delay, or if its sufficiently large, the program is too slow!

[http://www.pastebin.com/d51cc3b10](http://www.pastebin.com/d51cc3b10)

---

### Post by dwhitney67 on 2010-02-21
slackjack

Why are you pursuing this exercise as a multi-threaded solution?  Comparing two files is NOT necessary!

Madcow108 and I... well, I speak for myself... were merely pulling your chain.

Synchronization will come easy, whether using a mere mutex, or a conditional mutex, but please, pick a task that is more complicated than comparing two freakin' files.

You saw my first, comprehensive example.  Do you believe that my second example, which uses two threads, plus a main-thread, is better???  Get real... you are wasting your time pursuing the "end of the rainbow".

I haven't a clue where you possibly may have screwed up in your "program", because frankly, you haven't posted squat.

Why did you choose nanosleep()... why not just use sleep(), or usleep().... or use some other stupid thing like select() for your purposes.

Anyhow... I'm going to sleep... wait... another beer beckons my appetite.


P.S.  Pardon me... apparently you posted some code.  Are you reading two files, each consisting of simple lines containing a floating point number?  Jeez.

From your comparison thread, this is wrong... once you have the mutex, it is locked.  There is no need to explicitly lock it.
```

pthread_mutex_lock(&mutex);     // WRONG!
pthread_cond_wait(&token, &mutex)

```

---

