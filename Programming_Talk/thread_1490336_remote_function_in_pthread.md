---
title: "remote function in pthread"
date: 2010-05-22
forum: Programming Talk
---

### Post by elad2109 on 2010-05-22
Hi all,

I wrote some code in c, using pthread (I configured the linker and compiler in eclipse IDE first).

```

#include <pthread.h>
#include "starter.h"
#include "UI.h"

Page* MM;
Page* Disk;
PCB* all_pcb_array;

void* display_prompt(void *id){

    printf("Hello111\n");

    return NULL;
}


int main(int argc, char** argv) {
    printf("Hello\n");
    pthread_t *thread = (pthread_t*) malloc (sizeof(pthread_t));
    pthread_create(thread, NULL, display_prompt, NULL);
    printf("Hello\n");
    return 1;
}

```

that works fine. However, when I move display_prompt to UI.h
no "Hello111 " output is printed.

anyone know how to solve that?
Elad

---

### Post by MadCow108 on 2010-05-22
you do not wait in the main thread for the other thread to end, so it may get killed before it prints.
It has nothing to do with where the function is defined, its just a so called race condition.

put a pthread_join or some other kind of synchronization into the main

---

