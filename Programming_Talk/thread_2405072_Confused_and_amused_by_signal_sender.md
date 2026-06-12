---
title: "Confused and amused by signal sender"
date: 2018-10-31
forum: Programming Talk
---

### Post by luca31 on 2018-10-31
Hi all, I'm reading the glibc documetation about the signal handling, I'm not sure about how the raise call affects the program iteration in the following code:
[https://www.gnu.org/software/libc/manual/html_node/Termination-in-Handler.html#Termination-in-Handler](https://www.gnu.org/software/libc/manual/html_node/Termination-in-Handler.html#Termination-in-Handler)
 I'm wondering if the raise call makes the signal being handled before proceeding the normal iteration or if it is handled asynchronously and unpredictably stacking the signal and continuing the normal execution.
Moreover I'm not sure about what happens in the example code if a different signal handled by the same handler is catched during the handler execution... For the signal interrupting the handler, being true the volatile variable it should raise the signal again but I'm not sure what implies... because that signal should be blocked inside his handler... will it be stacked so that the previous signal will be handled? Will it be handled as soon as the interrupted signal's handler finish?



Regards

A C noob

---

### Post by luca31 on 2018-11-01
Solved with the following proof of code:

```


fusillator@catorcio@1:~/Code/unixprogramming$ cat raise.c
#include <signal.h>
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>

volatile sig_atomic_t fatal_error_in_progress = 0;

void myhandler(int sig){
    printf("Receiving %u\n", sig);
    if (fatal_error_in_progress)
        raise (sig);
    fatal_error_in_progress=1;
    printf("Fatal error in progress\n");
    sleep(60);
    printf("Handled sig %u\n", sig);
}

int main(void){
    printf ("process id %u\n",(int) getpid());
    struct sigaction sa;
    sa.sa_handler = myhandler;
    sigemptyset(&sa.sa_mask);
    sa.sa_flags = 0;

    sigaction(SIGUSR1, &sa, NULL);
    sigaction(SIGUSR2, &sa, NULL);
    printf("send a SIGUSR1\n");
    raise(SIGUSR1);
    printf("raised SIGUSR1\n");
}
fusillator@catorcio@1:~/Code/unixprogramming$./raise
process id 2943
send a SIGUSR1
Receiving 10
Fatal error in progress
fusillator@catorcio@2:~/Code/unixprogramming$kill -USR2 2943
fusillator@catorcio@1:~/Code/unixprogramming$./raise
process id 2943
send a SIGUSR1
Receiving 10
Fatal error in progress
Receiving 12
Fatal error in progress
Handled sig 12
Receiving 12
Fatal error in progress

```

So the signal USR2 interrupts the USR1 handler execution and cause the same handler to be called again for USR2. 
Since USR2 signal is locked in this context the call to raise returns immediately putting the signal pending on the process. 
The iteration proceeds and when the handler finishes, USR2 is unlocked and the same handler runs again in loop.
The example code of the glibc manual, on which this code is based, handles termination signals and on the last istruction of the handler 
terminates the process setting up the signal's handler to the default action
Luca ~&#55357;&#56846;

---

### Post by luca31 on 2018-11-04
I found a good explanation further into the glibc manual at [Blocking-for-Handler]("https://www.gnu.org/software/libc/manual/html_node/Blocking-for-Handler.html#Blocking-for-Handler")

---

