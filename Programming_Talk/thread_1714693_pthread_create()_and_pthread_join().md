---
title: "pthread_create() and pthread_join()"
date: 2011-03-25
forum: Programming Talk
---

### Post by raac on 2011-03-25
Ok guys I'm doing this program in C and I don't know why i'm getting segmentation fault.
I think all you need is this to get the idea... (I'm giving meaningless code, I just need help on the pointer manipulation which i think is the reason of the seg fault)


typedef struct ti{
   int value1;
   int value2;
}info;


//Main
       info *solu;
      pthread_t tid;   
      solu->value1 = 3;
      solu->value2 =1;
      if(error = pthread_create(&tid, NULL, queen_thread, (void *) solu))
         fprintf(stderr, "Failed to create thread: %s\n", strerror(error));
      if (error = pthread_join(tid, NULL)) {
         fprintf(stderr, "Failed to join thread: %s\n", strerror(error));
         exit(-1);
      }

//queen_thread function
void *queen_thread(void *infopointer){
   info solutions;
   solutions = *(info *) infopointer;
   solutions->value1 = 4;
  return NULL;
}
/

---

### Post by raac on 2011-03-25
Ok, I narrowed down the problem, for some reason

//header
typedef struct ti{
   int value1;
   int value2;
}info;

//Main 
info * x;

x->value1 = 4;    <----This gives me a segmentation fault

---

### Post by t1497f35 on 2011-03-25
**If** the info structure is created on the stack of the main() function - that's likely your problem, because the stack might be gone by the time the thread function tries to do something with the info struct from the stack of the main func.
Make sure you're creating the struct on the heap, if that's not your problem - post a compilable piece of code so that we can reproduce your seg fault.

---

### Post by raac on 2011-03-25
Well, it does not even get to the pthread_create, like I said 

Ok, I narrowed down the problem, for some reason

//header (header.h)
typedef struct ti{
int value1;
int value2;
}info;

//Main 

#include "header.h"
int main(){
info *x;

x->value1 = 4; <----This gives me a segmentation fault
}

//---------------------------------------------------------
However if I do this

#include "header.h"
int main(){
info x;

x.value1 = 4; <----This works just fine
}

---

### Post by t1497f35 on 2011-03-25
This one compiles and runs fine with gcc

[PHP]
#include <stdlib.h>
#include <stdio.h>
#include <pthread.h>
#include <errno.h>

typedef struct {
    int value1;
    int value2;
} info_t;

void *queen_thread(void *arg) {
    pthread_detach(pthread_self());
    
    info_t *info = (info_t*) arg;
    info->value1 = 4;
    printf("value1 is: %d\n", info->value1);
    return NULL;
}


int main(int argc, char *argv[]) {
    info_t *info = malloc(sizeof(info_t));
    if(info == NULL) {
        perror("malloc");
        return 1;
    }
    
    info->value1 = 3;
    info->value2 =1;
    int error;
    pthread_t thread;
    if(error = pthread_create(&thread, NULL, queen_thread, (void *) info)) {
        printf("can't create thread\n");
        return 1;
    }
    
    pthread_exit(NULL);
}

[/PHP]

---

### Post by raac on 2011-03-25
Yeah thanks!!!!, you were right malloc fixes the problem, i had to allocate memory on the heap. Thanks again

---

