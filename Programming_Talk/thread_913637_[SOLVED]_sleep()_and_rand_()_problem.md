---
title: "[SOLVED] sleep() and rand () problem"
date: 2008-09-07
forum: Programming Talk
---

### Post by ninjamonkey26 on 2008-09-07
Hi all I'm trying to test this C-program i've written and I cannot get it to compile for the life of me. The two major errors i'm getting are:

tech3.c:43: error: called object 'rand' is not a function.

tech3.c
```

#include "buffer.h"


/*Declare Variables*/
int head, tail=-1; 
int count=0;

/*Begin Main*/
int main(int argc, char *argv[])
{
int sleep_time, producer,consumer;
int sleep=0;
int prod=0;
int con =0;
	
/*1. Get Command Line Arguments */	
	sleep_time = atoi(argv[1]); //take a string and turn it into an int
	producer = atoi(argv[2]);	//Store the int's in variables.
	consumer = atoi(argv[3]);
	
	printf("Sleep Time: %d \n Producer: %d \n Consumer: %d\n",sleep_time,producer, consumer);
/*2. Initialize the Buffer */	
	buffer_item buffer[BUFFER_SIZE];


}//end main

/*3. Create PRODUCER thread(s) */
   void *producerthr(void *param)
	{
		buffer_item rand;
		
		while (prod != producer){
			//Sleep for a random Period of time
			sleep(sleep_time);
			
			//Generate a random number
			rand = rand();
			
			printf("producer produced %d\n", rand);
			if (insert_item (rand))
				fprintf(stderr,"report error condition");
			prod++;
		}
	}//end void *producer
 
buffer_item buffer[BUFFER_SIZE];//the buffer

 int insert_item(buffer_item item)
{
	//insert item into the buffer
	if (count >= BUFFER_SIZE)
	{
		return -1;//indicate error condition
	}//end if
	else
	{	
		head= (head + 1)%BUFFER_SIZE;
		count++;
			if(tail ==-1)
			 tail++;
		buffer[head]<- item;
		return 0; //if successful return 0
	}//end else
}//end of insert_item

/* Buffer Method
 * Inputs: none
 * Outputs: -1 for error, 0 for success
 * Creates a circular queue for manipulating objects.
 */
int remove_item(buffer_item *item)//remove object from the buffer
{
  if (count <= 0)	
	{
		return -1;//indicate error condition
	}
  else
	{
		*item <- buffer[tail];
		tail++;
	
	
 	if ( count == 0)
	{
		head<- -1;
		tail<- -1;
	}
	
		return 0; //if successful return 0
	}
}//end of remove_item 

```

buffer.h
```

#include <stdio.h>
#include <time.h>
#include <stdlib.h>
#include <pthread.h>
#include <string.h>
#include <unistd.h>
#include <signal.h>

typedef int buffer_item;
#define BUFFER_SIZE 6
	
int head, tail;


```
As you can see all the required header files are in there and I'm using -lpthread when compiling so I'm very confused as to why it will not recognize rand and sleep...

---

### Post by ninjamonkey26 on 2008-09-08
Nvm solved, variables were declared with the same name as the functions sleep and rand. Changing those names cleared up the issue

---

