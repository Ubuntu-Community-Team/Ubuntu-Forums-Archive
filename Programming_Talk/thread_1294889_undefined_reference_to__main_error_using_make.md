---
title: "undefined reference to _main error using make"
date: 2009-10-18
forum: Programming Talk
---

### Post by amnishaw on 2009-10-18
/djgpp/lib/crt0.o:crt0.s:(.data+0xc2): undefined reference to `_main'
/djgpp/lib/libc.a(crt1.o):crt1.c:(.text+0x404): undefined reference to `_main'

I get that error when I use my makefile to try to build. 

Here is an excerpt of my code, minus all the logic I've done:

```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <time.h>
#include "PQueue.h"
#include "functions.h"
/*
 * A Queue simulator.
 */
    int main(){

   // Variables for input data.
      float lambda, mu, arrivals, service;
   
   // Various counters
      int i, chansUsed = 0, waitCounter = 0;
   
   // variables needed for calulations for the nodes.
      float f, interval, servDuration, depTime;
.
.
.
.
. 
      return 0;
   }
```This is the makefile, for C. I got the basic template from gnu.org, and have tried different variations of .c's and .o's on the first two lines, without the -o's on the rest. I am at a loss.

main : main.o PQueue.o functions.o
    gcc -o main.o PQueue.o functions.o 

PQueue.o : PQueue.c PQueue.h
    gcc -c PQueue.c -o PQueue.o

functions.o : functions.c functions.h
    gcc -c functions.c -o functions.o

main.o : main.c PQueue.h functions.h
    gcc -c main.c -o main.o

---

### Post by dwhitney67 on 2009-10-18
It appears that you have three .c modules.  Here's a snappy Makefile:
```

APP  = main

SRCS = main.c PQueue.c function.c
OBJS = $(SRCS:.c=.o)

.PHONY: all clean

all: $(APP)

$(APP): $(OBJS)
        $(CC) $^ -o $@

clean:
        $(RM) $(APP) $(OBJS)

```

---

### Post by amnishaw on 2009-10-18
I am still getting the undefined reference to main error. Where would you put the -lm linker in that format of a make file? I've never seen it before.

---

### Post by dwhitney67 on 2009-10-18
> **amnishaw said:**
> I am still getting the undefined reference to main error. Where would you put the -lm linker in that format of a make file? I've never seen it before.
See LIBS below...
```

APP  = main

SRCS = main.c PQueue.c function.c
OBJS = $(SRCS:.c=.o)

LIBS = -lm

.PHONY: all clean

all: $(APP)

$(APP): $(OBJS)
        $(CC) $^ $(LIBS) -o $@

clean:
        $(RM) $(APP) $(OBJS)

```

P.S.  It seems that you are having deeper issues than that of a mere Makefile.  You may need to post your complete code.

---

### Post by amnishaw on 2009-10-18
Here's my code with my main. My other .c's are ONLY functions. They all compile separately. They worked and ran together with xcode from a mac, but now that I'm not on a mac, it won't "make". 

main.c
```
/* 
 * File:   main.c
 * Author: Amber
 *
 * Created on October 12, 2009, 4:10 PM
 */

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <time.h>
#include "PQueue.h"
#include "functions.h"
/*
 * A Queue simulator.
 */
int main()
{
    
    // Variables for input data.
    float lambda, mu, arrivals, service;
    
    // Various counters
    int i, chansUsed = 0, waitCounter = 0;
    
    // variables needed for calulations for the nodes.
    float f, interval, servDuration, depTime;
    
    // My variables needed for statistical analysis
    float totWait = 0.0, totServ = 0.0, lastDep, myAvgTinQ, 
        myRho, myAvgTimeSys, myPNot, myAvgPinQ, myAvgPinSys;
    
    float startServ, stopServ = 0.0;
    
    // The variables for the given forumlas.
    float pNot, avgSys, avgTSys, avgQ, avgTQ, rho;
    
    //Prompting the user for data.
    do 
     {
         printf("Please enter a value for lambda: ");
          scanf("%f", &lambda);
    
        printf("Please enter a value for mu (larger than lambda): ");
        scanf("%f",&mu);
     }while(lambda >= mu);
  
    printf("Please enter a value for the number of arrivals to simulate: ");
    scanf("%f", &arrivals);
    
    printf("Please enter the number of service channels: ");
    scanf("%f", &service);
    
     PNode myNode;
    PQueue myPQueue = newPQueue(arrivals);
     FifoQ fifo = newFifo();
    
    srand(time(NULL));
    
    // Generating arrival and service times and inserting them intothe priority queue.
    for(i = 0; i<arrivals; i++){
        f = (float)(rand() / (((float)RAND_MAX + 1.0)));
        interval = (float)(-1.0 * (float)(1.0/lambda) * log(f));
        servDuration = (float)(-1.0 * (float)(1.0/mu) * log(f));
        myNode = newPNode('A', interval, servDuration);
        insert(myPQueue, myNode);
    }

/*
    The simulation logic. Checks to see if the item on top is an arrival
    or departure, and handles them accordingly.
 */
    do
     {
        
         if(myPQueue->heap[1].tType == 'A'){
             if(chansUsed != service){
                 depTime = myPQueue->heap[1].eventTime +myPQueue->heap[1].serviceTime;
                myNode = newPNode('D', depTime, 0.0);
                insert(myPQueue, myNode);
                chansUsed++;
                if(chansUsed == 1) // Gets the start of service time
                    startServ =myPQueue->heap[1].eventTime; 
                deleteMin(myPQueue);
            }
            else {
                insertFItem(fifo, myPQueue->heap[1]);
                waitCounter++;
                deleteMin(myPQueue);
            }
         }
        else if(myPQueue->heap[1].tType == 'D'){
            if(emptyFifo(fifo) == 0){
                PNode temp = getFItem(fifo);
                totWait = totWait + (myPQueue->heap[1].eventTime - temp.eventTime);
                printf("Did I wait? %f\n",totWait);
                printf("Fifo count %i\n", fifo->count);
                removeFItem(fifo);
                depTime = myPQueue->heap[1].eventTime + temp.serviceTime;
                myNode = newPNode('D', depTime, 0.0);
                insert(myPQueue, myNode);
                deleteMin(myPQueue);
            }
            else{
                chansUsed--;
                if(chansUsed == 0){ // Gets the end of service time -- Time in between is the idle time.
                    stopServ = myPQueue->heap[1].eventTime;
                    totServ = totServ + (stopServ - startServ); // The total time being serviced.
                }
                lastDep = myPQueue->heap[1].eventTime;
                deleteMin(myPQueue);
            }
        }
     }while(isEmpty(myPQueue) == 0);
    
    // Average time spent in the system
    myAvgTimeSys = (totWait + totServ)/arrivals;
    
    // The average people in the wait Queue
    myAvgPinQ = waitCounter/arrivals;
    
    // The average time spent in the wait queue
    myAvgTinQ = totWait/waitCounter;
    
    // The percent Idle time
    myPNot = (lastDep - (totServ))/lastDep;
    
    // The utlization factor
    myRho = (totServ)/lastDep;
    
    // The average people in the System
    myAvgPinSys = (totServ + (totWait/arrivals))/lastDep;

    printf("**********************************************************\n\n");
    printf("My Sim's Percent Idle Time: \t\t\t  %f\n", myPNot);
    printf("My Sim's Average people in the System: %f\n", myAvgPinSys);
    printf("My Sim's Avg Time in System: \t\t\t  %f\n", myAvgTimeSys);
    printf("My Sim's Average people in the Queue:  %f\n", myAvgPinQ);
    printf("My Sim's Average Time in the Queue:       %f\n", myAvgTinQ);
    printf("My Sim's Utilization Factor: \t\t\t  %f\n", myRho);
    printf("\n");
    printf("**********************************************************\n");
    pNot = percentIdle(lambda, mu, service);
    avgSys = avgPplSys(lambda, mu, service, pNot);
    avgTSys = avgTimeSys(lambda, avgSys);
    avgQ = avgPplQ(lambda, mu, avgSys);
    avgTQ = avgTimeQ(avgQ, lambda);
    rho = utiRho(lambda, mu, service);
    printf("\n");
    printf("Percent Idle Time: %f\n", pNot);
    printf("Average People in System: %f\n", avgSys);
    printf("Average Time in the System: %f\n", avgTSys);
    printf("Average people in the Queue: %f\n", avgQ);
    printf("Average Time in the queue: %f\n", avgTQ);
    printf("Utilization factor: %f\n", rho);
    printf("\n");
    printf("**********************************************************\n");
    
    free(myPQueue->heap);
    free(myPQueue);
    freeFifo(fifo);
   
    return 0;
}

```

---

### Post by dwhitney67 on 2009-10-18
I cannot see anything wrong with the code you posted.  I also did not see anything that would require you to link with the math library (-lm).

Just out of curiosity, have to installed the build-essential package on your system?
```

sudo apt-get install build-essential

```

Also, did you try the Makefile that I posted?  What were the results?

---

### Post by amnishaw on 2009-10-18
The first time I tried yours, it still said there was an undefined reference to main. But I also had some of the math references undefined in my functions.c. I wasn't sure if I would need the math.h for my personal calculations, that's why it was there. I am having difficulties, atm, because I have to access the linux boxes on campus, so they had a hiccup and kicked me off for a few minutes. I can only assume they have the build essentials.

Could it have something to do with the fact that I started it on a mac? Some essential portion I am missing? It wouldn't seem so, but that is the only thing I can guess.

---

### Post by dwhitney67 on 2009-10-18
If you were to provide the PQueue.h and .c, along with the function.h and .c, then I could attempt to recreate the issue (if any) on my system.

I have a Mac at my office with xcode, and so far I have found xcode to work just like GCC, at least for the basic Standard C stuff.  Your code does not look like it is that complex, but then on the other hand, I have not seen all of it.

---

### Post by amnishaw on 2009-10-18
It is not complex at all, really. Which is why I am so flustered at it saying I don't have a main.

But when I used the makefile with the LIBS in it, it gave me this:
makefile:13: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

If we can fix that, and I still get the error, I'll post the rest of my files.

EDIT: I fixed the tab error
Only to get this

make.exe: *** Warning: File `makefile' has modification time in the future (2009-10-18 21:28:06 > 2009-10-18 21:28:00)
gcc    -c -o main.o main.c
make.exe: *** No rule to make target `function.o', needed by `main'.  Stop.

---

### Post by dwhitney67 on 2009-10-18
EDIT:

Do you have a function.c???  Regardless of how trivial your code may be, I cannot "chat" with you in trying to solve the issue you are having.  _Please_ provide all of the information you have, including the code, in your next post.

------------------------------

```

APP  = main

SRCS = main.c PQueue.c function.c
OBJS = $(SRCS:.c=.o)

LIBS = -lm

.PHONY: all clean

all: $(APP)

$(APP): $(OBJS)
<tab>$(CC) $^ $(LIBS) -o $@

clean:
<tab>$(RM) $(APP) $(OBJS)

```
Replace the <tab> with, you guessed it, a tab-space.

---

### Post by amnishaw on 2009-10-18
PQueue.h
```

/* 
 * File:   PQueue.h
 * Author: Amber
 *
 * Created on October 12, 2009, 4:38 PM
 */

#ifndef _PQUEUE_H
#define    _PQUEUE_H

#include<stdio.h>
#include<stdlib.h>

/*
 * Definition of a node
 */
typedef struct NodeT
{
   char tType;
   float eventTime;
   float serviceTime;
} PNode;

/*
 * Definition of a PQueue
 * Implemented in a heap
 */
typedef struct PQueueT
{
   PNode * heap;// array of pointers to nodes
   int heapSize;
} *PQueue;

typedef struct NodeFifo 
{
    PNode nodeItem;
    struct NodeFifo *next;
} *nodeF;

typedef struct FifoT
{
    nodeF top;
    nodeF current;
    int count;
} *FifoQ;

PQueue newPQueue(int size);

PNode newPNode(char type, float time, float service);

int isEmpty(PQueue myQueue);

PNode findMin(PQueue myQueue);

void insert(PQueue myQueue, PNode myNode);

void deleteMin(PQueue myQueue);

void makeEmpty(PQueue myQueue);

void percolateDown(PQueue myQueue, int slot);

FifoQ newFifo();

void removeFItem(FifoQ myFifo);

void insertFItem(FifoQ myFifo, PNode myNode);

PNode getFItem(FifoQ myFifo);

int emptyFifo(FifoQ myFifo);

void freeFifo(FifoQ myFifo);


#endif    /* _PQUEUE_H */

```PQueue.c
```
#include<stdio.h>
#include<stdlib.h>
#include "functions.h"
#include "PQueue.h"

/*
    Creates space for the pointer to a priority queue
    as well as creates the space for the array of nodes
    that the queue consists of.
*/
PQueue newPQueue(int size){
    PQueue myPQueue = malloc(sizeof(struct PQueueT));
    myPQueue->heap = malloc(((2*size)+1)*sizeof(struct NodeT));
    if(myPQueue == NULL)
        return NULL;
    myPQueue->heapSize = 0;
    return myPQueue;
}

/*
    Creates a node that is used to insert into the
    prioity queue.
*/
PNode newPNode(char type, float time, float service){
    PNode temp;
    temp.tType = type;
    temp.eventTime = time;
    temp.serviceTime = service;
    return temp;
}

/*
    Checks to see if the priority queue is empty.
    0 = false (queue not empty), 1 = true (queue is empty)
*/
int isEmpty(PQueue myQueue){
    if(myQueue->heapSize == 0)
        return 1;
    else
        return 0;
}

/*
    Gets the item from the top of the queue.
*/
PNode findMin(PQueue myQueue){
    PNode tmp;
    tmp = myQueue->heap[1];
    return tmp;
}

/*
    Inserts a node into the priority queue in
    the correct priority.
*/
void insert(PQueue myQueue, PNode myNode){
    myQueue->heap[0] = myNode;
    int hole = ++(myQueue->heapSize);
    while(myNode.eventTime < myQueue->heap[hole/2].eventTime){
        myQueue->heap[hole] = myQueue->heap[hole/2];
        hole /=2;
    }
    myQueue->heap[hole] = myNode;
}

/*
    Removes the first node (the highest priority) from
    the top of the queue and replaces it with the last,
    rearranging to maintain min heap order.
*/
void deleteMin(PQueue myQueue){
    myQueue->heap[1] = myQueue->heap[myQueue->heapSize--];
    percolateDown(myQueue, 1);
}

/*
    Logically makes the priority queue empty
*/
void makeEmpty(PQueue myQueue){
    myQueue->heapSize = 0;
}

/*
    Used to rearrange to maintain min-heap conditions.
*/
void percolateDown(PQueue myQueue, int slot){
    int child;
    PNode tmp = myQueue->heap[slot];
    while(slot*2 <= myQueue->heapSize){
        child = slot *2;
        if(child != myQueue->heapSize && 
           myQueue->heap[child +1].eventTime < myQueue->heap[child].eventTime)
            child++;
        if(myQueue->heap[child].eventTime < tmp.eventTime)
            myQueue->heap[slot] = myQueue->heap[child];
        else
            break;
        slot = child;
    }
    myQueue->heap[slot] = tmp;
}

/*
    Creates a new queue implemented as a linked list.
*/
FifoQ newFifo()
{
    FifoQ newFifo = malloc(sizeof(FifoQ));
    newFifo->count = 0;
    return newFifo;
}

/*
    removes the first item in the queue (top)
*/
void removeFItem(FifoQ myFifo)
{
    if(myFifo->count == 1)
    {
        myFifo->current = NULL;
    }
    else
    {
        nodeF temp = myFifo->top->next;
        myFifo->top = temp;
    }
    (myFifo->count)--;
}

/*
    Inserts an item at the end of the queue (current)
*/
void insertFItem(FifoQ myFifo, PNode myNode)
{
    nodeF temp = malloc(sizeof(nodeF));
    temp->nodeItem = myNode;
    if(myFifo->count == 0)
    {
        myFifo->top = temp;
        myFifo->current = myFifo->top;
    }
    else
    {
        myFifo->current->next = temp;
        myFifo->current = myFifo->current->next;
    }
    free(temp);
    (myFifo->count)++;
}

/*
    Returns the information portion of the struct
    for a node from the queue.
*/
PNode getFItem(FifoQ myFifo)
{
    return myFifo->top->nodeItem;
}

/*
    Checks to see if the FIFO queue is empty.
    0 = false (not empty), 1 = true (is empty)
*/
int emptyFifo(FifoQ myFifo){
    if(myFifo->count == 0)
        return 1;
    else
        return 0;
}

/*
    Frees the allocated memory created for the fifo queue.
*/
void freeFifo(FifoQ myFifo)
{
    int i;
    for(i = myFifo->count; i> 0; i--)
        removeFItem(myFifo);
    free(myFifo);
}
```functions.h
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "PQueue.h"

#ifndef _functions_h
#define    _functions_h

int factorial(int i);

float percentIdle(float lambda, float mu, float channels);

float avgPplSys(float lambda, float mu, float channels, float percent);

float avgTimeSys(float lambda, float avgPpl);

float avgPplQ(float lambda, float mu, float avgPpl);

float avgTimeQ(float avgPq, float lambda);

float utiRho(float lambda, float mu, float channels);

#endif
```functions.c
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "PQueue.h"
#include "functions.h"


/*
    Percentage of time no one is in the system
*/
float percentIdle(float lambda, float mu, float channels)
{
    int k;
    float sum, percent;
    for(k = 0; k <= (int)channels-1; k++){ // Sumation loop
        sum = sum + (1.0/(factorial(k)) * pow((lambda/mu), (float)k));
    }
    float bottom = (1.0/factorial((int)channels)) * pow(lambda/mu, channels) * ((channels * mu)/((channels*mu) - lambda));
    percent = 1.0/(sum + bottom);
    
    return percent;
}

int factorial(int i)
{
    int temp = 1;
    int k;
    for(k = 1; k<=i; k++)
        temp = temp * k;
    return temp;
}

/*
    The average number of people in the whole system
*/
float avgPplSys(float lambda, float mu, float channels, float percent)
{
    float avg;
    float top, bottom;
    top = lambda * mu * pow(lambda/mu, channels);
    bottom = factorial(channels-1) * pow((channels*mu)-lambda, 2);
    avg = (top/bottom)*percent + (lambda/mu);
    return avg;
}

/*
    Average time the customer spends in the system.
    Uses the average number of people in the system.
*/
float avgTimeSys(float lambda, float avgPpl)
{
    float avg;
    avg = (float)(avgPpl/lambda);
    return avg;
}

/*
    Average numver of customers in the wait queue.
    Uses the average numver of people in the system.
*/
float avgPplQ(float lambda, float mu, float avgPpl)
{
    float L;
    L = (avgPpl- (lambda/mu));
    return L;
}

/*
    Average time a customer spends waiting in the wait queue.
    Uses the average number of people in the queue.
*/
float avgTimeQ(float avgPq, float lambda)
{
    float avg;
    avg = (float)(avgPq/lambda);
    return avg;
}

/*
    Percent of time that the service lanes are being used.
*/
float utiRho(float lambda, float mu, float channels)
{
    float rho;
    rho = ((float)lambda/(float)(channels*mu));
    return rho;
}
```Error with my makefile:
gcc -o main.o PQueue.o functions.o
q:/jgrasp_186_10.v03/djgpp/lib/crt0.o:crt0.s:(.data+0xc2): undefined reference to `_main'
q:/jgrasp_186_10.v03/djgpp/lib/libc.a(crt1.o):crt1.c:(.text+0x404): undefined reference to `_main'
collect2: ld returned 1 exit status
make.exe: *** [main] Error 1

Error with the other makefile: 
make.exe: *** No rule to make target `function.o', needed by `main'.  Stop.

---

### Post by dwhitney67 on 2009-10-18
I compiled your code on my system; everything works fine.  The only issue was that I erred in one of the source code entries of the Makefile I provided earlier.  In lieu of 'function.c', I should have used 'functions.c' (note the plurality).

Anyhow, do you have GCC installed on your system?  Try running this command to verify:
```

gcc --version

```

---

### Post by dwhitney67 on 2009-10-18
> **amnishaw said:**
> ...
Error with my makefile:
gcc -o main.o PQueue.o functions.o
...
Also, this statement is wrong!  Did you not copy the Makefile I provided???  My Makefile does not have the error that you have above.  The correct statement can/should be one of the following:
```

gcc -o main main.o PQueue.o functions.o

OR

gcc -o $@ main.o PQueue.o functions.o

OR

gcc main.o PQueue.o functions.o -o $@

```

---

### Post by amnishaw on 2009-10-18
The error I am getting now is one I've never seen before.

make.exe: Nothing to be done for `all'

I feel as if I'll never get rid of errors.

---

### Post by Arndt on 2009-10-19
> **amnishaw said:**
> The error I am getting now is one I've never seen before.

make.exe: Nothing to be done for `all'

I feel as if I'll never get rid of errors.

What happens if you remove all the .o files and start again?

What you see above is not an error; it's 'make' telling you that there is nothing to do, as far as it can see. Here, it probably means that you have a "main" file which is younger than all .o files. But it doesn't mean that it is correct - if there were errors while producing it, it won't be runnable.

---

### Post by dwhitney67 on 2009-10-19
> **amnishaw said:**
> ...

Error with my makefile:
gcc -o main.o PQueue.o functions.o

...

Just in case the error with the statement above was not clear, the link error was the result of GCC outputting the beginning of the executable image into the main.o object file.  This trashed the main.o object file, thus preventing the linker from finding main().

---

