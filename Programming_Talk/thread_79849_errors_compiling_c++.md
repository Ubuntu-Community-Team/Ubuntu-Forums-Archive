---
title: "errors compiling c++"
date: 2005-10-21
forum: Programming Talk
---

### Post by jiggyup on 2005-10-21
hi ,

i just installed ubuntu so i can learn more about programming
im currently trying to program in c++, using gedit and ive made sure that ive got both make and g++ installed

however when i try to compile a source file i get A LOT of errors, when i know the program is synatically correct.  here is an example of some errors

/usr/include/c++/4.0.2/fstream:667: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/fstream:669: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’

what exactly is wrong here?  any  help appreciated

thanks

---

### Post by toojays on 2005-10-21
It would help if you posted the command which you are using to compile, as well as a small example of the code which can be used to reproduce this.

---

### Post by jiggyup on 2005-10-21
sure

im using this command to compile

g++ lab3.cpp -o lab3 -lpthread

and in the code just trying to create threads
i didnt include the thread functions or header files

int main(int argc, char* argv[]) {
  	pthread_t server;
  	
	//initialize integer values numInputs, numAlive, max_cpu_queue
	int numInputs = argc - 2;
	numAlive = numInputs;
    int max_cpu_queue = atoi(argv[1]);  
	
	//initialize array of threads, one per input file
    pthread_t threads[numInputs];
	cout << "threads initialized" << endl;

	//initialize servicing thread and error checking
 	pthread_create(&server, NULL, service_function, NULL);
 	pthread_join(server,NULL);
    cout << "servicer ready" << endl;
	
	//create array for the threads using input files
	for (int i=0; i<numInputs; i++) {
	  int st = pthread_create(&threads[i], NULL, thread_function, (void*)argv[i+2]);
	  pthread_join(threads[i],NULL);
	  if (st!=0)
	    printf("pthread_create failed with status: %d\n",st);
	} 
}

---

### Post by LordHunter317 on 2005-10-21
Need to post the entire file.

---

### Post by jiggyup on 2005-10-21
sure, here's what ive got

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

//prototype for thread and service functions
void* thread_function(void *arg);
void* service_function(void *arg);

//prototype for queue functions
void queue_function(void);
void swap(int& x, int& y);

//mutex intializer
pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;

//shared states
int numAlive;		//number currently 'alive' threads
int queue[10];		//scheduling queue

int main(int argc, char* argv[]) {
 	pthread_t server;
  	
	//initialize integer values numInputs, numAlive, max_cpu_queue
	int numInputs = argc - 2;
	numAlive = numInputs;
   	int max_cpu_queue = atoi(argv[1]);  
	
	//initialize array of threads, one per input file
   	 pthread_t threads[numInputs];
	cout << "threads initialized" << endl;

	//initialize servicing thread and error checking
 	pthread_create(&server, NULL, service_function, NULL);
 	pthread_join(server,NULL);
  	  cout << "servicer ready" << endl;
	
	//create array for the threads using input files
	for (int i=0; i<numInputs; i++) {
		int st = pthread_create(&threads[i], NULL, thread_function, (void*)argv[i+2]);
		pthread_join(threads[i],NULL);
	 	if (st!=0)
	   	printf("pthread_create failed with status: %d\n",st);
	} 
}

void* thread_function(void* arg) {
	//using input, open input file
	//while not at the end of file, try to put job in queue by lockgin mutex then inserting number
	//if job in queue, wait
	//after eof, lock mutex decrement numAlive unlock 
	//exit
	return NULL;
}

void* service_function(void* arg) {
	//using minimum item, 'run' the job 
	return NULL;
}

---

### Post by jiggyup on 2005-10-21
my first errors that i get are

g++: o-: No such file or directory
g++: lab3: No such file or directory
lab3.cpp:1:21: error: pthread.h: No such file or directory
lab3.cpp:2:19: error: stdio.h: No such file or directory
lab3.cpp:3:20: error: stdlib.h: No such file or directory

followed up by, probably over 1000 more lines of errors of the form i specified in the first thread, 

i've already tried reinstalling g++ and make, 
what could be going wrong here?

---

### Post by toojays on 2005-10-21
Ah, you are missing the C library headers. Install the build-essential package, that will pull in everything you need.

---

### Post by toojays on 2005-10-21
By the way, the first two errors would only come up if you wrote "o-" instead of "-o" in your command line.

---

### Post by jiggyup on 2005-10-21
ahhi see

i ran the apt-get and now everything is working fine

thanks much

---

