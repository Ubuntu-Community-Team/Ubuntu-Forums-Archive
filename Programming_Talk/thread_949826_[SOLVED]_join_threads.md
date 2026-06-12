---
title: "[SOLVED] join threads"
date: 2008-10-16
forum: Programming Talk
---

### Post by StOoZ on 2008-10-16
any idea , why , when I uncomment the 'pthread_join' , I get segafault?
> #include<pthread.h>
#include<string>
#include<iostream>
#include<ctime>
#define THREADS_N 5

struct threads_args {
    int index_t;
    int  secs_interval;
};


void Wait(double sec) {
    
    clock_t start = clock();
    clock_t end = sec * CLOCKS_PER_SEC;
    while ( clock() - start < end); // waiting...
    
}

void* show_details(void* args) {
    
    struct threads_args* arguments = (struct threads_args*) args;
    std::cout<<"Thread number "<<arguments->index_t<<std::endl;
    std::cout<<"Waiting time "<<arguments->secs_interval<<" now waiting...\n";
    Wait(arguments->secs_interval);
    std::cout<<"Thread "<<arguments->index_t<<" has ended , quitting , goodbye...\n";
    delete arguments;
//    pthread_exit(NULL);
}


int main(int argc , char* argv[]) {
 
    pthread_attr_t attr;
    pthread_attr_init(&attr);
    pthread_attr_setdetachstate(&attr, PTHREAD_CREATE_JOINABLE);
    
    pthread_t thread[THREADS_N];
    for (int i = 0 ; i < THREADS_N ; i++) {
        struct threads_args* argsz = new threads_args;
        argsz->index_t = i + 1;
        argsz->secs_interval = 10 - i;
        pthread_create(&thread[THREADS_N], &attr, show_details, (void*)argsz );
    }
    for (int i = 0 ; i < THREADS_N ; i++) {
//        pthread_join(thread[i] , NULL);
    }

    pthread_exit(NULL);
    return 0;
}


---

### Post by StOoZ on 2008-10-16
im stupid , problem solved. :guitar:

---

### Post by scourge on 2008-10-16
> **StOoZ said:**
> im stupid , problem solved. :guitar:

No, that's an easy mistake to make. Took me a couple of minutes to notice what's wrong.

I would suggest you to pedantically check the return values of the pthread functions though, helps you catch some bugs earlier.

---

