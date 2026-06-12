---
title: "pthread_getspecific and pthread_setspecific"
date: 2010-03-14
forum: Programming Talk
---

### Post by cybo on 2010-03-14
i'm still learning about threads. in fact i'm taking an OS class where we use a lot of them. one of the problems involves the use of pthread_getspecific and pthread_setspecific functions (they were not explained in class). i'm having difficulty in understanding of their respective man pages (man page includes the example but i still don't get it). and since i don't understand the man pages i don't know where and why i would use these functions. if there is anyone out there who used those functions before or understands the man pages i'd appreciate any help (if you can provide an example it would be even better).

thank you in advance.

---

### Post by MadCow108 on 2010-03-14
these functions are just means to provide global data on a per thread basis.
you first create a key with pthread_key_create. You mostly make this key global so each thread can read it from anywhere.
Every thread can set and get thread specific global data with help of this global key without interfering with the global data of the other threads.

Example:
It uses thread specific data to save logging information for each thread
each thread may use different log levels and files. 
You don't want to have to pass this information into each function the thread calls, so you use global data.
Normally you would also encapsulate the getspecific call and logging itself into a macro or function for convenience.
```

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
static pthread_key_t msg_key;

#define DEBUG 0
#define NUMTHREADS 4

typedef struct MsgSettings {
  int level;
  FILE * destination;
}MsgSettings;
//destructor
void specific_destroy(void *sp)
{
  free(sp);
}

void do_something()
{
  // get specfic data
  MsgSettings * m = (MsgSettings*)pthread_getspecific(msg_key);
  // output according to data
  if (m->level >= DEBUG)
    fprintf(m->destination, "blub %d", m->level);
}

void *thread_func(void *param)
{
  printf("starting thread\n");
  //set the specfic data
  pthread_setspecific(msg_key, param);
  // do some working, we could just always pass param, but this gets annoying in larger programs
  do_something();
  return NULL;
}

int main(int argc, const char *argv[])
{
  // create key, register destructor
  pthread_key_create(&msg_key, specific_destroy);
  pthread_t             thread[NUMTHREADS];
  int                   i;
  for (i=0; i <NUMTHREADS; ++i) {
    // start threads and give each a own logfile and loglevel
    char file[200];
    MsgSettings * m = malloc(sizeof(MsgSettings));
    snprintf(file, 200, "logfile_thread%d.txt", i);
    m->level = i;
    m->destination = fopen(file, "w");
    pthread_create(&thread[i], NULL, thread_func, m);
  }
  for (i=0; i <NUMTHREADS; ++i) {
    pthread_join(thread[i], NULL);
  }
 
  // delete the key and all data associated with it
  pthread_key_delete(msg_key);
  return 0;
}

```

---

### Post by cybo on 2010-03-15
@MadCow108

thanks. it helped me significantly. this may sound stupid, but why do you declare msg_key as a static variable, won't it work if you delcare it without the static modifier?

---

### Post by MadCow108 on 2010-03-15
I added it out of habit as you should declare file scope global variables static to not allow other files to access them.
In this case this does not make much sense.
We probably want the pthread key to be accessible in other files.
So its better to drop the static.

But if you only have one file/compilation unit it does not matter if its static or not.

---

### Post by cybo on 2010-03-15
@MadCow108

thanks. it really made things much more clear.

---

### Post by cybo on 2010-03-15
i stared writing my own code and was somewhat confused about pthread_key_create. here is what i found in the documentation about it:

> Upon key creation, the value NULL shall be associated with the new key in all active threads. Upon thread creation, the value NULL shall be associated with all defined keys in the new thread.

An optional destructor function may be associated with each key value. At thread exit, if a key value has a non-NULL destructor pointer, and the thread has a non-NULL value associated with that key, the value of the key is set to NULL, and then the function pointed to is called with the previously associated value as its sole argument. The order of destructor calls is unspecified if more than one destructor exists for a thread when it exits.

i understood that upon thread exit a destroy function will be called. i use this function to destroy thread specific data. do i understand it correctly? 

if i do then shouldn't we in the code given above change the specific_destroy from 

```
void specific_destroy(void *sp)
{
  free(sp);
}
```

to

```
void specific_destroy(void *sp)
{
  free((MsgSettings*)sp);
}
```

since if data is void then the compiler won't know how much of memory to free.

however if i understood the meaning of the destructor function incorrectly i would appreciate any insights and corrections.

thank you in advance.

---

### Post by MadCow108 on 2010-03-15
free does not care for the type of data in memoryblock. Its just need to get a pointer to a memoryblock which was allocated with malloc/calloc/realloc.
The allocator places information on how big the block is etc, inside some space near the allocated block (how and where exactly is implementation dependent) so the pointer is all it needs to free it again.

A cast is only needed when you need to read the memory again.
e.g a better destructor (I forgot this last time):
```

void specific_destroy(void *sp)
{
  MsgSettings * m = (MsgSettings*)sp;
  // we want to read the destination pointer, thus we have to know how where in the memoryblock it is located
  // the easiest way of doing it is a cast
  fclose(f->destination);

  // not recommended alternative (this is what the action on the casted pointer does internally):
  // fclose((FILE*)((char*)sp+sizeof(int))); // cast to char* to work on byte sized data then add the 4 byte offset

  free(m); // or free(sp), does not matter
}

```

if you do not need any special action, like the fclose or deep destructor, you could even use free directly:
```

pthread_key_create(&key, free);

```

---

### Post by cybo on 2010-04-07
@MadCow108 thanks. your input really helped.

---

