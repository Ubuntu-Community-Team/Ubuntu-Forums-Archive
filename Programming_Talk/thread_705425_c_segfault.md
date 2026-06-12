---
title: "c segfault?"
date: 2008-02-23
forum: Programming Talk
---

### Post by rye_ on 2008-02-23
can anyone please tell me why I get a segfault error with the c source code below.

thanks

```

#include <stdio.h>
#include <stdlib.h>
#include <limits.h>

#define NUMBER 1000000000LL
//------------------------------------------
//integer struct and functions
//------------------------------------------
struct list_int { 
	//instance variable list
	int * list;
	//instance variable holding array size
	int size;
	int entries;
};

struct list_int * create_list_int(){
	
	//initialize the list structure
	struct list_int * the_list = malloc(sizeof(struct list_int));
	
	//create the list and initialize content to zero
	the_list->list = malloc(sizeof(int)*1);
	the_list->list[0] = 0;
	
	//marker holder array size information
	the_list->size = 1;
	
	//number of entries utilized
	the_list->entries = 0;
	
	return &the_list;
}
	
void add_num_int(const long long int addition, struct list_int * container){

	container->list = realloc(container->list, sizeof(int)*((container->size)+1));
	
	container->list[container->size] = (int) addition;
	
	container->size++;
	
	container->entries++;
}

//------------------------------------------
//Long integer struct and functions
//------------------------------------------

struct list_long { 
	//instance variable list
	long int * list;
	//instance variable holding array size
	int size;
	int entries;
};

struct list_long * create_list_long(){
	
	//initialize the list structure
	struct list_long * the_list = malloc(sizeof(struct list_long));
	
	//create the list and initialize content to zero
	the_list->list = malloc(sizeof(long int)*1);
	the_list->list[0] = 0;
	
	//marker holder array size information
	the_list->size = 1;
	
	//number of entries utilized
	the_list->entries = 0;
	
	return &the_list;
}
	
void add_num_long(const long long int addition, struct list_long * container){

	container->list = realloc(container->list, sizeof(long int)*((container->size)+1));
	
	container->list[container->size] = (long int) addition;
	
	container->size++;
	
	container->entries++;
}

//------------------------------------------
//Long Long integer struct and functions
//------------------------------------------

struct list_long_long { 
	//instance variable list
	long long int * list;
	//instance variable holding array size
	int size;
	int entries;
};

struct list_long_long * create_list_long_long(){
	
	//initialize the list structure
	struct list_long_long * the_list = malloc(sizeof(struct list_long_long));
	
	//create the list and initialize content to zero
	the_list->list = malloc(sizeof(long long int)*1);
	the_list->list[0] = 0;
	
	//marker holder array size information
	the_list->size = 1;
	
	//number of entries utilized
	the_list->entries = 0;
	
	return &the_list;
}
	
void add_num_long_long(const long long int addition, struct list_long_long * container){

	container->list = realloc(container->list, sizeof(long long int)*((container->size)+1));
	
	container->list[container->size] = addition;
	
	container->size++;
	
	container->entries++;
}

int main(int argc, char * argv[]){

	/* 
		create the containers that will store the number 1:NUMBER
		depending on size
		unused arrays will be of length 1
	*/

	struct list_int * integerList = create_list_int();
	struct list_long * longList = create_list_long();
	struct list_long_long * longLongList = create_list_long_long();

	
	/*
		populate the arrays, starting from number 2
	*/
	
	long long int counter = 0;
	for(counter = 2; counter < NUMBER; counter++){
		if (counter <= INT_MAX){
			add_num_int(counter, integerList);
		}
		else if (counter > INT_MAX && counter <= LONG_MAX){
			add_num_long(counter, longList);
		}
		else {
			add_num_long_long(counter, longLongList);
		}
	}
	
	//printf("%d", integerList->list[343435]);
//			
	return 0;
	
	
}

```

---

### Post by volanin on 2008-02-23
Just to start, replace all of yours **return &the_list;** to **return the_list;**
Pay more attention to your compiler warnings!
:)

---

### Post by cb951303 on 2008-02-23
you are trying to return the adress of a pointer in your 3 allocation functions

just delete "&" in front of return

---

### Post by rye_ on 2008-02-23
whoops.

thanks guys.

---

