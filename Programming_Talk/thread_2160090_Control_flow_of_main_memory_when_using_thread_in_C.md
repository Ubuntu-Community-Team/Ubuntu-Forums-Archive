---
title: "Control flow of main memory when using thread in C programming assumingPagedSegmented"
date: 2013-07-05
forum: Programming Talk
---

### Post by Rahul04789 on 2013-07-05
Hi all,

I executed the following threaded C programme and got different results:


#include<pthread.h>
#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
void *threadout(void * args)
{
    char buffer[1024];
    char *c;
    struct timespec s;
    s.tv_sec=0;
    s.tv_nsec=10000000L;
    snprintf(buffer,1024,"\nThis is a thread from process %ld\n",(long)getpid());
    c=buffer;
    while(*c!='\0')
    {
        fputc(*c,stderr);
        c++;
        nanosleep(&s,NULL);
    }
    return NULL;
}

int main()
{
    int error;
    int i;
    pthread_t *tids;
    tids=(pthread_t*) calloc(4,sizeof(pthread_t));
    for(i=0;i<4;i++)
    {    pthread_create(tids+i,NULL,threadout,NULL);}
    for(i=0;i<4;i++)
    {
        pthread_join(tids[i],NULL);
    }
    return 0;
}


Output:

rahul@rahul-VPCEG28FN:~/CProgram/Untitled Folder$ ./maincritical 




TTTThhhhiiiissss     iiiissss    aaaa    tttthhhhrrrreeeeaaaadddd    ffffrrrroooommmm     pppprrrroooocccceeeessssssss    2222777788886666



Please look the attachments for my questions.
I have assumed** paged segmentes memory management.**

[ATTACH=CONFIG]244430[/ATTACH][ATTACH=CONFIG]244431[/ATTACH]

---

### Post by ofnuts on 2013-07-05
1) looks like homework....

2) I'd assume that as a minimum, you type it out for us in good ol' ASCII in the post body.

---

### Post by Rahul04789 on 2013-07-06
Please look on the two questions that I have written in the pic (leave rest);

---

### Post by ofnuts on 2013-07-06
Please retype them here....

---

### Post by Rahul04789 on 2013-07-11
Q1)   Let us assume that the page corresponding to the thread creation is loaded in the main memory(let us assume a segmented paged memory management).  So tell me that when one thread is created then that thread will make CPU to load the "void *threadout(void * args)" function into the memory and execute the corresponging codes in that function or after the creation of all the threads, each thread will load the "void *threadout(void * args)" function into memory and execute it.

---

### Post by ofnuts on 2013-07-11
When a thread is created then it become eligible for dispatch. Your main thread is still running, so unless creating a thread implies a wait, it keeps its timeslice and continues creating the other threads... However, if it were to create very many threads, it would yield the CPU to the first created threads when its timeslice ends.

Your code isn't very correct to test this because the sleeps in each thread make it return the CPU to the main thread... If you make the main thread sleep between each thread creation you get a very different result, and it you don't put any sleep you get something different.

```

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <time.h>

#define THREADS 9
#define MAX_OUTPUT 40

void *threadout(void * args) {
    char sig = * (char *)args;
    struct timespec s;
    s.tv_sec=0;
    s.tv_nsec=10000000L;
    for (int i=0;i<MAX_OUTPUT;i++){
        fputc(sig,stderr);
//        nanosleep(&s,NULL);
    }
    return NULL;
}

int main(){
    char threadsigs[THREADS]="123456789";
    pthread_t threads[THREADS];
    int i;
    struct timespec s;
    s.tv_sec=0;
    s.tv_nsec=10000000L;
    for(i=0;i<THREADS;i++) { 
        fputc('M',stderr);
        pthread_create(&threads[i],NULL,threadout,&threadsigs[i]);
        fputc('m',stderr);
//        nanosleep(&s,NULL);
    }
    for(i=0;i<THREADS;i++) {
        pthread_join(threads[i],NULL);
    }
    return 0;
}

```
For instance, without sleeps:

```

MmM1111111111111111111111111111111111111111mM23333333333333333333333333333333333333333mM2222222222222222222222222222222222222224444444444444444444444444444444444444444mMmM55555555555555555555555555555555555555556mMmM78888888888888888888888888888888888888888666666666666666666666666666666666666666777777777777777777777777777777777777777mMm9999999999999999999999999999999999999999

```
where you notice that the first threads starts while main is creating the second, while the 3rd and 8th start as soon as created... .

---

