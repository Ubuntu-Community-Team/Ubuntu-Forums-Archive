---
title: "Problem in understanding the output of a threaded C programme"
date: 2013-07-02
forum: Programming Talk
---

### Post by Rahul04789 on 2013-07-02
Hi All,

I executed this programme and got different output while executing it. PFB one of the outputs.


#include<stdio.h>
#include<fcntl.h>
#include<sys/stat.h>
#include<unistd.h>
void * print_(void *arg)
{
fprintf(stderr,"Thread received %d\n", *(int *)arg);
return NULL;
}
int main(void)
{
int i,j;
pthread_t tid[10];
for (i=0;i<4;i++)
{
if(pthread_create(tid+i,NULL,print_,(void *) &i)){tid[i]=pthread_self();}
}

for(j=0;j<4;j++)
{
if(pthread_equal(pthread_self(),tid[j]))
    continue;
pthread_join(tid[j],NULL);
}
printf("All threads done.");
return 0;
}


Output:

rahul@rahul-VPCEG28FN:~/CProgram/Untitled Folder$ ./qwe 
Thread received 4
Thread received 3
Thread received 3
Thread received 3
All threads done.

I just want to know why thread 3 has printed three times and why thread 1 or thread 2 has not printed anything?
If its so, then there might be a situation that some threads will never be executed.?
Please someone explain me its do confusing...

---

### Post by Rahul04789 on 2013-07-02
#include<pthread.h> is included in this programme

---

### Post by spjackson on 2013-07-02
Each of the 4 threads has printed precisely once, but what each one has printed is not what you expect.

Each instance of print_ gets passed the same address. The content of this address is volatile because it is being changed by the main thread. The value contained at the point each thread reads the address is not deterministic. If you want each thread to read a deterministic different value, then pass a different address to each call of pthread_create.

---

### Post by dwhitney67 on 2013-07-02
It appears that spjackson beat me...

@ the OP:  You are passing the address of a variable that is on the stack, not the value it refers to.  Thus by the time the thread is able to print the value, your main thread has already set the value of that stack variable to 3.

Consider the following solution:
```

#include <pthread.h>
#include <stdio.h>

struct ThreadData
{
    int value;
};

void* myThread(void* arg)
{
    struct ThreadData* data = (struct ThreadData*) arg;

    fprintf(stderr, "Thread %lu has arg %d\n", pthread_self(), data->value);

    return NULL;
}

int main()
{
    const int NUM_THREADS = 4;

    struct ThreadData data[ NUM_THREADS ];
    pthread_t tid[ NUM_THREADS ];

    for (int i = 0; i < 4; ++i)
    {
        data[i].value = i;

        pthread_create(&tid[i], NULL, myThread, &data[i]);
    }

    for (int i = 0; i < 4; ++i)
    {
        pthread_join(tid[i], NULL);
    }

    return 0;
}

```

---

### Post by Rahul04789 on 2013-07-02
@ spjackson: 
hey I didn't understand "The content of this address is volatile because it is being changed by the main thread. The value contained at the point each thread reads the address is not deterministic."
Plz explain further.

---

### Post by spjackson on 2013-07-02
> **Rahul04789 said:**
> @ spjackson: 
hey I didn't understand "The content of this address is volatile because it is being changed by the main thread. The value contained at the point each thread reads the address is not deterministic."
Plz explain further.
You pass the address of main's variable i. At some point each thread will read the value stored in i, but in a multi-threaded environment you cannot predict when that read will happen. Meanwhile, the main function is incrementing the value of i in its for loop.

When the first thread reads the value of i, it could be 0, 1, 2, 3, 4 and you don't know which. You know what the value is at the time you call pthread_create, but you don't know what it will be by the time the thread reads it. The same applies to the other 3 threads.

Compare this with [COLOR=#000000]dwhitney67's solution where a different element of the data array is passed to each of the threads.[/COLOR]

---

### Post by Rahul04789 on 2013-07-02
@spjackson: ok got it .. Thanks

---

