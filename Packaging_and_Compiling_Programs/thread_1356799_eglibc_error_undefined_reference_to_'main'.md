---
title: "eglibc error? undefined reference to 'main'"
date: 2009-12-16
forum: Packaging and Compiling Programs
---

### Post by joxepo84 on 2009-12-16
Dear people!! 

I'm new programin and 

I am trying to compile a program made by me and I get this error:

[I]/usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crt1.o: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status[/I]

Do I have to install something or what do you think?? Could anyone help me please???

---

### Post by lewisforlife on 2009-12-16
Can you paste your program, as well as the command that you used to compile the program?

---

### Post by joxepo84 on 2009-12-16
Hello,

of course I can!

I am using three files in this proyect (ariso.h, ariso.c and principal.c, witch has the main()).

I have the comented error while compiling the file ariso.c:

[I]$ gcc -o ariso ariso.c
/usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crt1.o: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status[/I]

but then I try to compile principal.c and I get another error... and I don't know why is it...

[I]$ gcc -o principal principal.c
/tmp/cc9XScYQ.o: In function `main':
mjargoñ_3.c:(.text+0x62): undefined reference to `ariso_init_threads'
mjargoñ_3.c:(.text+0x80): undefined reference to `ariso_create_thread'
collect2: ld returned 1 exit status[/I]

the files are the next ones.

[ariso.h]
[INDENT][FONT=Arial]#ifndef ARISO_H[/FONT]
[FONT=Arial]#define ARISO_H[/FONT]

[FONT=Arial]#include <ucontext.h>[/FONT]
[FONT=Arial]#include <stdlib.h>[/FONT]
[FONT=Arial]#include <errno.h>[/FONT]
[FONT=Arial]#include <string.h>[/FONT]

[FONT=Arial]#define FATAL(msg)    \[/FONT]
[FONT=Arial]    do {    \[/FONT]
[FONT=Arial]        fprintf(stderr,"%s:%d:%s: %s\n",__FILE__,__LINE__,msg,strerror(errno));    \[/FONT]
[FONT=Arial]        exit(-1);    \[/FONT]
[FONT=Arial]    } while(0)[/FONT]


[FONT=Arial]#define STACK_SIZE    32*1024[/FONT]

[FONT=Arial]#define MAX_THREADS    4[/FONT]

[FONT=Arial]/* Thread library API */[/FONT]
[FONT=Arial]void ariso_init_threads(void);[/FONT]
[FONT=Arial]int ariso_create_thread(void func(), void *);[/FONT]
[FONT=Arial]void ariso_terminate_thread(void);[/FONT]
[FONT=Arial]void ariso_swap_thread(void);[/FONT]
[FONT=Arial]void ariso_scheduler(int, siginfo_t *, void *);[/FONT]

[FONT=Arial]#endif[/FONT]
[/INDENT]

[ariso.c]
[INDENT]#include <stdio.h>
#include <string.h>
#include <stdlib.h> 
#include <ucontext.h> 
#include <errno.h> 
#include <signal.h> 
#include <unistd.h>
#include "ariso.h"

#define FATAL(msg)    \
    do {    \
        fprintf(stderr,"%s:%d:%s: %s\n",__FILE__,__LINE__,msg,strerror(errno));    \
        exit(-1);    \
    } while(0)


/* Types only used inside this file */

typedef enum {
    FREE,
    READY,
    RUNNING,
    WAITING
} state_t;

struct thread_struct {
    int thread_id;
    state_t state;
    ucontext_t context;
    unsigned char stack[STACK_SIZE];
};

/* Data structures only used inside this file */

struct thread_struct thread_table[MAX_THREADS];
ucontext_t kernel_context;
struct thread_struct *current;


/* Functions not used by the main program */
static struct thread_struct *ariso_get_ready_thread(void);
static struct thread_struct *ariso_get_free_thread(void);
static void ariso_do_schedule(void);



/* Functions only used inside this file */

static struct thread_struct *ariso_get_free_thread(void){
    int i;
        for(i=0;i<MAX_THREADS;i++){
                if(thread_table[i].state==FREE) 
            return (&thread_table[i]);
        }
    return (NULL);
}



/* Functions exported to be used by the main programm */
void ariso_init_threads()
{
    int i;

    for(i=0;i<MAX_THREADS;i++)
        thread_table[i].thread_id = i;
    current = NULL;
}

int ariso_create_thread(void func(), void *v){
    struct thread_struct *my_thread, *my_ready_thread;    
    
    if((my_thread=ariso_get_free_thread())==NULL){
        fprintf(stderr, "[ariso_create_thread]my_thread==NULL\n");
        return(-1);
    }else{
        if(getcontext(&(my_thread->context))<0)
                    FATAL("getcontext");
            my_thread->context.uc_stack.ss_sp = my_thread->stack;
            my_thread->context.uc_stack.ss_size = STACK_SIZE;
            my_thread->context.uc_link = &kernel_context;
        makecontext(&my_thread->context, func, 0);        
        my_thread->state=READY;
    }

    func();
    
    return(my_thread->thread_id);
}
[/INDENT]
[principal.c]
[INDENT]#include <stdio.h> 
#include <stdlib.h> 
#include <ucontext.h> 
#include <string.h> 
#include <errno.h>
#include "ariso.h" 
#include <signal.h> 
#include <unistd.h> 
 
#define FATAL(msg)    \ 
    do {    \ 
        fprintf(stderr,"%s:%d:%s: %s\n",__FILE__,__LINE__,msg,strerror(errno));    \ 
        exit(-1);    \ 
    } while(0) 
 
void mi_hilo() 
{ 
        fprintf(stderr,"[mi_hilo] Starting\n"); 
        fprintf(stderr,"[mi_hilo] Finishing\n"); 
} 
 
int main(int argc, char *argv[]) 
{ 
        int i, thread; 
 
    ariso_init_threads();         
    for(i=0;i<7;i++){ 
        thread=ariso_create_thread(mi_hilo, NULL); 
        if(thread!=-1)    
            fprintf(stderr, "[main]Thread %d creado y FREE\n\n", thread); 
        } 
    fprintf(stderr,"[main] Se crearon todos los hilos sin problemas\n"); 
        return(0); 
 
}
[/INDENT]
If you could help me I would be very glad! thank you very much!!!

bye!!

joxepo

---

### Post by MadCow108 on 2009-12-16
ariso.c has no main functions, thus undefined reference while linking
the same when you compile principal.c, it does not have the ariso_* functions defined, thus undefined reference

So first compile:
gcc -c -o ariso.o ariso.c
gcc -c -o principal.o principal.c
(c flag means only compile and don't link)

and the link the objects together
gcc ariso.o principal.o -o outfile

alternatively in one step:
gcc ariso.c principal.c -o outfile

---

### Post by joxepo84 on 2009-12-18
Thank you very much MadCow108!!
That was the problem!! now i can compile and run!
thanks!!
Joxepo

---

