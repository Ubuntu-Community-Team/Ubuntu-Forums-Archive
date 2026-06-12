---
title: "Memory Leak?"
date: 2009-03-10
forum: Programming Talk
---

### Post by cs_kid on 2009-03-10
Hey guys, 

I'm workin on a program for my Operating Systems class, and I'm told there's a memory bug in this code but I'm havin trouble figuring out how to resolve it. Any idea how can I fix this? The hint I was given was that I only need to move one line of code in here....

// Make threads to sort string.
// Returns the number of threads created.
int make_enzyme_threads(pthread_t * enzymes, char *string, void *(*fp)(void *)) {
	int i,rv,len;
	thread_info_t *info;
	len = strlen(string);
	info = (thread_info_t *)malloc(sizeof(thread_info_t));

	for(i=0;i<len-1;i++) {
	    info->string = string+i;
	    rv = pthread_create(enzymes+i,NULL,fp,info);
	    if (rv) {
	        fprintf(stderr,"Could not create thread %d : %s\n",
			i,strerror(rv));
		exit(1);
	    }
	}  
	return len-1;
}

---

### Post by dwhitney67 on 2009-03-10
What is this line doing?
```

...
info->string = string+i;
...

```
P.S.  If you are impressed with the code-block above, you should consider doing the same when you post code.

---

### Post by cs_kid on 2009-03-10
Nice code box, I'll tinker with this site and figure out how to do that in a bit (this was my first post to ubuntuforums, just registered tonight). The code line you asked about:  

Code:
...
info->string = string+i;
...

is referring to code in my header file:
This is the complete header file:

#include <pthread.h>
#include <stdio.h>
#include <sys/types.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>

#define MAX 100

typedef struct {
        char *string; // keep testing and swap contents if necessary so that string[0] < string[1]
        int swapcount; // used later
} thread_info_t;

extern int please_quit;

extern int workperformed;

void *run_enzyme(void *data);
int make_enzyme_threads(pthread_t * enzymes_tid, char *string, void *(*fp)(void *));
int join_on_enzymes(pthread_t *threads_tid, int n);

int smp2_main(int, char**);



***************************************************
***************************************************
***************************************************

If you'd like to see the whole picture for the sake of putting things in context, I've attached the original code files, as well as the enzyme.c that I've been modifying (had to zip it because apparently we can't post .c files).

---

### Post by monkeyking on 2009-03-10
consider learning valgrind for  catching mem leaks

compile your code with -g option
then run your code with

valgrind YOURPROGRAM

This should help you find the excact line from where your program leaks

---

### Post by dwhitney67 on 2009-03-11
@ OP

From the code declarations you provided earlier, the following statement is not doing what you think... unless of course all you want is to set 'info->string' equal an offset within 'string'.
```

info->string = string+i;

```
If 'string' is equal to "abcd", then for each iteration of the loop, 'info->string' will have the value "abcd", then "bcd", then "cd", and finally "d".

I could possibly help you with your code, but not until you specify your requirements.  There appears to be more than one line of code that looks suspect as being wrong; thus it is difficult to determine what is it that you are trying to accomplish (other than of course, launch multiple threads).

---

### Post by dwhitney67 on 2009-03-11
I took a closer look at the code you posted; I came up with a working version, however because I am unfamiliar with your project's requirements, I may have assumed some things incorrectly.

(Btw, the one line of code that needed to be readjusted was the malloc() for the thread_info_t object).

```

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>


typedef struct
{
  int   swapcount;
  //char* string;
  char string;
} thread_info_t;


// Function prototypes
void*        dummy_enzyme(void* data);
unsigned int make_enzyme_threads(pthread_t* tids, const char* str, void *(*fp)(void*));


int main(int argc, char** argv)
{
  const char*  str    = "enzymatic";
  pthread_t*   tids   = calloc(strlen(str), sizeof(pthread_t));
  unsigned int n      = make_enzyme_threads(tids, str, dummy_enzyme);
  void*        status = 0;

  for (unsigned int t = 0; t < n; ++t)
  {
    pthread_join(tids[t], &status);

    printf("%d\n", ((thread_info_t*) status)->swapcount);
    free(status);
  }

  free(tids);
}


void* dummy_enzyme(void* data)
{
  thread_info_t* info = (thread_info_t*) data;

  info->swapcount = info->string - 'a';

  return data;
}


unsigned int make_enzyme_threads(pthread_t* tids, const char* str, void *(*fp)(void*))
{
  const size_t len = strlen(str);
  size_t       i   = 0;

  for (; i < len; ++i)
  {
    thread_info_t* info = malloc(sizeof(thread_info_t));

    info->string = *(str + i);   // save a single character???

    if (pthread_create(&(tids[i]), NULL, fp, info) != 0)
    {
      printf("error creating thread.\n");
      break;
    }
  }

  return i;
}

```

---

### Post by cs_kid on 2009-03-12
Thank you so much for your help! 

Your code wasn't exactly what the teacher wanted, but he asked for some pretty weird things. He was trying to teach us about threads, but made up a very obscure situation to demonstrate the concepts. My code is complete now according to his odd...odd requirements, and thanks to you, I was able to fix that memory leak!

PS, my completed function without the mem leak:

```

int make_enzyme_threads(pthread_t * enzymes, char *string, void *(*fp)(void *)) {
	int i,rv,len;
	thread_info_t *info;
	len = strlen(string);
	info = (thread_info_t *)malloc(sizeof(thread_info_t));

	for(i=0;i<len-1;i++) {
	    info->string = string+i;
	    rv = pthread_create(enzymes+i,NULL,fp,info);
		info = (thread_info_t *)malloc(sizeof(thread_info_t));
	    if (rv) {
	        fprintf(stderr,"Could not create thread %d : %s\n",
			i,strerror(rv));
		exit(1);
	    }
	}  
	return len-1;
}

```

---

