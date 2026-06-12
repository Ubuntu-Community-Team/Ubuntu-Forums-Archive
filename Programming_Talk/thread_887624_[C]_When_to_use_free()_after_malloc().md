---
title: "[C] When to use free() after malloc()"
date: 2008-08-12
forum: Programming Talk
---

### Post by spadewarrior on 2008-08-12
I'm getting enormous memory leaks that almost crash my system as I've got no idea how to implement free() after using malloc().  I'm new to using linked lists.

Here's the program:

[PHP]#include <stdio.h>
#include <math.h>
#include <stdlib.h>
struct node
{
	int num;
	struct node *next;
	
};

typedef struct node Node;
typedef Node  * Link; /* Link is pointer to Node*/

Link int_to_list(int n, Link conductor);
int list_length(Link current);
int is_prime(int n, Link conductor);
int in_list(int n, Link conductor);
Link factors_of_num( int n, Link conductor);
int gcd( int a, int b);
void print_list(Link conductor);


int main(void)
{
	Link rootPrime, conductor, nRoot;
	
	Node prime, coPrimes;
	
	int i = 1;
	int  count = 0;
	int max = 10;
	int n = 3;
	int largest = 0;
	
	double temp = 0.0f;
	double qd = 0.0f;
	
	prime.num = 2;
	prime.next = NULL;
	
	rootPrime = &prime;
	nRoot = &coPrimes;
	
	conductor = rootPrime;
	
	
	
	while ( n <= max )/*Gets primes*/
	{
		if ( is_prime(n, rootPrime) == 0)
		{
			conductor = int_to_list( n, conductor );
		}
		n+=2;
	} 	
	
	
	n = 2;
	
	while ( n < max)
	{
		
		
		conductor = &coPrimes;
		coPrimes.num = 1; 					/* all numbers are coprime with the integer '1'*/
		count = 1;
		coPrimes.next = NULL;
	
		
		
		
		if ( in_list( n, rootPrime ) == 0) 		/* if n  prime  then EVERY positive int below n is co-prime to it */
		{
			count = n - 1;
			
		}
		else /* if n isn't prime */
		{
			
			i = 2;
			while ( i <= n)
			{
					
				if ( gcd( n, i) == 1) /* if '1' is n and i's greatest common divisor */
				{
					conductor = int_to_list( i, conductor );
					count++;
				}
				i++;
			}
		}
		
		temp =  (float)n / (float) count;

		if ( temp > qd )
		{
			qd = temp;
			largest = n;
		}
		
		
		/* display n on the same line each time*/
		printf("\r");
		printf("%d", n);
		fflush(stdout);
		
		
		
		n++;
		
	}
	
	printf("\n");
	
	printf("%d,	%f\n", largest, qd);
	
	
	
	return 0;
}



void print_list(Link conductor)
{
	while ( conductor != NULL)
	{
		printf("%d, ", conductor->num);
		conductor = conductor->next;
	}
}



int gcd(int a, int b) 
{ 
	if ( b == 0 ) return a;
	
	else
	{
		return( gcd ( b, a%b ) );
	}
}



int in_list(int n, Link conductor)
{
	while ( conductor != NULL)
	{
		if ( conductor-> num == n) return 0;
			
		conductor = conductor -> next;
	}
	return -1;
	
}

int list_length(Link current)
{
	int i = 0;
	
	while (current != NULL)
	{
		i++;
		current = current-> next;
	}
		
	return i;
	
}



int is_prime(int n, Link conductor)
{
	if ( n == 3 ) 
	{
		return 0;
	}
	else
	{
		while ( conductor !=NULL && conductor->num < sqrt(n) + (n/2))
		{
			if ( n % conductor -> num == 0) /*if N is divisible by element in list, it's NOT prime*/
			{
				return -1;
			}
			
			conductor = conductor -> next;
			
		}
	}
	return 0;
}

Link int_to_list(int n, Link conductor)
{
	Link current = malloc(sizeof(n));
	
	
	
	conductor->next = current;
	current -> num = n;
	current -> next = NULL;
	
	
	
	return current;
}

[/PHP]

valgrind says:

```
==8141== Invalid write of size 4
==8141==    at 0x8048820: int_to_list (leaky.c:205)
==8141==    by 0x804854B: main (leaky.c:52)
==8141==  Address 0x41b502c is 0 bytes after a block of size 4 alloc'd
==8141==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==8141==    by 0x8048808: int_to_list (leaky.c:199)
==8141==    by 0x804854B: main (leaky.c:52)
==8141== 
==8141== Invalid read of size 4
==8141==    at 0x804877E: is_prime (leaky.c:190)
==8141==    by 0x8048535: main (leaky.c:50)
==8141==  Address 0x41b502c is 0 bytes after a block of size 4 alloc'd
==8141==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==8141==    by 0x8048808: int_to_list (leaky.c:199)
==8141==    by 0x804854B: main (leaky.c:52)
==8141== 
==8141== Invalid write of size 4
==8141==    at 0x8048812: int_to_list (leaky.c:203)
==8141==    by 0x804854B: main (leaky.c:52)
==8141==  Address 0x41b502c is 0 bytes after a block of size 4 alloc'd
==8141==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==8141==    by 0x8048808: int_to_list (leaky.c:199)
==8141==    by 0x804854B: main (leaky.c:52)
3==8141== 
==8141== Invalid read of size 4
==8141==    at 0x8048704: in_list (leaky.c:153)
==8141==    by 0x8048593: main (leaky.c:72)
==8141==  Address 0x41b502c is 0 bytes after a block of size 4 alloc'd
==8141==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==8141==    by 0x8048808: int_to_list (leaky.c:199)
==8141==    by 0x804854B: main (leaky.c:52)
==8141== 
==8141== Invalid write of size 4
==8141==    at 0x8048820: int_to_list (leaky.c:205)
==8141==    by 0x80485D4: main (leaky.c:86)
==8141==  Address 0x41b50d4 is 0 bytes after a block of size 4 alloc'd
==8141==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==8141==    by 0x8048808: int_to_list (leaky.c:199)
==8141==    by 0x80485D4: main (leaky.c:86)
7==8141== 
==8141== Invalid write of size 4
==8141==    at 0x8048812: int_to_list (leaky.c:203)
==8141==    by 0x80485D4: main (leaky.c:86)
==8141==  Address 0x41b5144 is 0 bytes after a block of size 4 alloc'd
==8141==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==8141==    by 0x8048808: int_to_list (leaky.c:199)
==8141==    by 0x80485D4: main (leaky.c:86)
9
6,	3.000000
==8141== 
==8141== ERROR SUMMARY: 39 errors from 6 contexts (suppressed: 13 from 1)
==8141== malloc/free: in use at exit: 52 bytes in 13 blocks.
==8141== malloc/free: 13 allocs, 0 frees, 52 bytes allocated.
==8141== For counts of detected errors, rerun with: -v
==8141== searching for pointers to 13 not-freed blocks.
==8141== checked 68,188 bytes.
==8141== 
==8141== LEAK SUMMARY:
==8141==    definitely lost: 52 bytes in 13 blocks.
==8141==      possibly lost: 0 bytes in 0 blocks.
==8141==    still reachable: 0 bytes in 0 blocks.
==8141==         suppressed: 0 bytes in 0 blocks.

```

This isn't a problem when variable 'max' is 10, but when I increase to what I actually need ( 1,000,000 ) my system becomes unusable. 

Any suggestions?

Thanks.

---

### Post by theyranos on 2008-08-12
I think you probably have a two-part problem here. First, I strongly suspect all those "Invalid Write" messages that Valgrind is giving you have to do with this line:

```
Link current = malloc(sizeof(n)); 
```

You're assigning a malloc just large enough for a single number to a structure that expects to have enough memory for both a number and a link. Try ```
Link current = malloc(sizeof(Node));
``` and see if those valgrind messages go away.

The rules for free()ing stuff are:
[LIST]
[*]Only pass "free()" something that came from malloc(), unaltered.
[*]You need one free() per malloc()
[/LIST]

Here's some code that'll free an entire List. I'm being lazy by using recursion here, and at 1,000,000 items, there might be a stack overflow. If that happens, just unroll the recursion and it'll work.

```

void free_list(List list_to_be_freed) {
  if (list_to_be_freed->next)
    free_list(list_to_be_freed->next);
  free(list_to_be_freed);
}

```

Hope this is useful.
-Theyranos

---

### Post by Lster on 2008-08-12
You need to free memory when you remove an element from the linked list. However, I can't see when you do remove elements. I must ask: what are you trying to achieve with the code?

Linked lists have the benefit, over arrays, of deleting/ inserting elements in O(1) complexity but indexing takes O(n)...

---

### Post by sameerds on 2008-08-12
I think the code provided here has too much noise to actually discuss things about memory allocation. Before even trying to wade through that code to look for a segment fault, I would suggest that the code itself should be rewritten. Create a struct called "List", along with functions like "append", "delete", etc and just play with those. Put all the relevant stuff in a file called list.c and another called list.h ... Once you have a working list implementation, you can use that with whatever code you like, not just lists of prime numbers.

---

### Post by spadewarrior on 2008-08-12
Lster: Firstly I must admit that I don't know what O(1) and O(n) mean and that I'm completely new to linked lists... As for the program itself, I'm not deleting from the lists at all, but I am trying to reuse list coPrimes each time in the bigger while loop.

I'm doing one of the project Euler problems; I won't say which one as I'm pretty sure this code works aside from the memory leaks and don't want to help anyone googling for answers ;).



theyranos: Thanks for that. malloc(sizeof( Node )) greatly reduces the memory problems. I'm not sure I understand your free_list() function.

I get these errors from gcc:
```

error: invalid type argument of ‘->’
: error: invalid type argument of ‘->’
: error: incompatible type for argument 1 of ‘free’
```

Should I be passing the list (i.e. Node) or a pointer to the start of the list? Neither seem to work for me.

Thanks for all your help!

---

### Post by theyranos on 2008-08-12
Whoops! Typo. Should've said Link instead of List.

```

void free_list(Link list_to_be_freed) {
  if (list_to_be_freed->next)
    free_list(list_to_be_freed->next);
  free(list_to_be_freed);
}

```

Hopefully that works (been a while since I've used typedefs). Pass it the first address in a list that was created with malloc. Like, for example 

```
if (coPrimes.next) free_list(coPrimes.next);
```

---

### Post by spadewarrior on 2008-08-12
I've tried putting free_list(nRoot) at the end of the while loop but I get:

```
double free or corruption
```

and a long memory map. I'm guessing I should be putting it somewhere else...?

---

### Post by theyranos on 2008-08-12
The double free message is because nRoot is set to &coPrimes and the memory used by coPrimes wasn't malloc'd, but instead was created automatically by the compiler because you declared coPrimes as a Node. So, what's happening is, my code frees coPrimes, then the compiler frees coPrimes when the function completes.

```
if (nRoot->next) free_list(nRoot->next);
```

ought to do it.

---

### Post by Lster on 2008-08-12
[QUOTE=spadewarrior]Lster: Firstly I must admit that I don't know what O(1) and O(n) mean and that I'm completely new to linked lists... As for the program itself, I'm not deleting from the lists at all, but I am trying to reuse list coPrimes each time in the bigger while loop.

I'm doing one of the project Euler problems; I won't say which one as I'm pretty sure this code works aside from the memory leaks and don't want to help anyone googling for answers .[/QUOTE]

If you are only going to insert elements to the end of the list and never going to delete an element, you would do better using an array. The O(1) and O(n) describe how fast code should run (ignoring coefficient and constant factors).

O(n) means that if there were n elements in the list, the time it would take to complete that operation is rough proportional to n. O(1) means the same but, of course, the time it takes for the operation to complete is not proportional to n!

In essence what I was saying was: to insert/ delete an element in a linked list is faster than in an array; but in an array, it is faster to find the nth index.

If you're learning linked lists then it's probably best to try and make a library with them as a simple C file first. You can then include that file in any program that requires linked lists!

---

### Post by nvteighen on 2008-08-12
I'm currently working on a (double) linked list implementation for a project of mine and can assure you the best is what sameerds has told you: create a file list.c where you implement a list data type with associated functions, and a proper list.h file to #include in the main module (and, for safety, also in list.c).

Then, you'll be able to reuse that module for whenever you need a linked list.

Or you can use GLib's lists. I don't know whether Project Euler allows using external libraries or not, but using it could help you to focus on the actual problem and, also, learn what functions are expected in a linked list implementation.

---

### Post by spadewarrior on 2008-08-12
Yeah, I was thinking of doing that. I guess I will now!

---

### Post by Reiger on 2008-08-12
A doubly linked list has AFAIK only one benefit over an array; namely you don't need to worry [as much] about the size of your collection.

But deletion still takes O(n) time in the worst case (namely the middle of the list) whereas with arrays deletion/insertion takes O(1) time.

---

### Post by Lster on 2008-08-12
Deletion of an entire linked list takes O(n). Deletion, depending on what you know, takes O(1) or O(n) time. If we are talking about double linked lists and we know the element we want to delete, that can be done in O(1) time. If we have to find the element first, then it will take O(n) time. The same goes for insertion...

[http://en.wikipedia.org/wiki/Linked_list#Linked_lists_vs._arrays](http://en.wikipedia.org/wiki/Linked_list#Linked_lists_vs._arrays)

To quote Wikipedia:

[QUOTE=Wikipedia]Linked lists permit insertion and removal of nodes at any point in the list in constant time, but do not allow random access.[/QUOTE]

---

### Post by nvteighen on 2008-08-12
> **Reiger said:**
> A doubly linked list has AFAIK only one benefit over an array; namely you don't need to worry [as much] about the size of your collection.

There's another one, and very important: inserting something in the middle of an array can be a nightmere in C...; in a linked list, it's pretty much easier.

---

### Post by nvteighen on 2008-08-12
> **Lster said:**
> Deletion of an entire linked list takes O(n). Deletion, depending on what you know, takes O(1) or O(n) time. If we are talking about double linked lists and we know the element we want to delete, that can be done in O(1) time. If we have to find the element first, then it will take O(n) time. The same goes for insertion...

[http://en.wikipedia.org/wiki/Linked_list#Linked_lists_vs._arrays](http://en.wikipedia.org/wiki/Linked_list#Linked_lists_vs._arrays)

To quote Wikipedia:
> 
(Wikipedia)
Linked lists permit insertion and removal of nodes at any point in the list in constant time, but do not allow random access.

I'm working on random access for linked lists. I need that functionality for my project. The way I plan to do it is to emulate what C arrays do: an offest from the first node.

---

### Post by Lster on 2008-08-12
[QUOTE=nvteighen]There's another one, and very important: inserting something in the middle of an array can be a nightmere in C...; in a linked list, it's pretty much easier.[/QUOTE]

[PHP]
def delete(x, i):
	l = len(x)
	
	while i < l-1:
		x[i] = x[i+1]
		i += 1
	
	return x[:l-1]

def newdel(x, i):
	return x[:i]+x[i+1:]


a = range(1, 10+1)
print newdel(a, 2)
print delete(a, 2)
[/PHP]

---

### Post by Lster on 2008-08-12
[QUOTE=nvteighen]I'm working on random access for linked lists. I need that functionality for my project. The way I plan to do it is to emulate what C arrays do: an offest from the first node.[/QUOTE]

That won't work, I don't think. You'll soon get irregularities in spacing and it will fail. I doubt that O(1) access is possible with linked lists.

---

### Post by nvteighen on 2008-08-12
> **Lster said:**
> [PHP]
def delete(x, i):
	l = len(x)
	
	while i < l-1:
		x[i] = x[i+1]
		i += 1
	
	return x[:l-1]

def newdel(x, i):
	return x[:i]+x[i+1:]


a = range(1, 10+1)
print newdel(a, 2)
print delete(a, 2)
[/PHP]

That's overkill :)

[PHP]
a = range(1, 10 + 1)
a.insert(2, 0) #insert a 0 after a[2]
a.remove(0) # remove 0 from list
[/PHP]

> **Lster said:**
> That won't work, I don't think. You'll soon get irregularities in spacing and it will fail. I doubt that O(1) access is possible with linked lists.

It will have to work :)

Actually, it won't be truly "random", but it will resemble an array or, better a Python list. Each node has an index in the list and I traverse the list using the index as parameter to know where to stop (yes, O(n)). For the client code, it will be as accessing an array and will ease the list usage. All access will be performed through a **list** data type, not node-by-node as usual in C.

This dynamic lists will serve as base for dynamic matrices. The end goal: create a little library for graphs in C that supports adjacency matrices to store edges. The list data type should afterwards also give adjacency lists support.

But you will have to wait a bit. I'm still on the nodes-level and have found some flaws in the current design. And have to run some tests before climbing one step up in the abstraction "ladder" (node->list->matrix).

A nice project, don't you think? :)

---

### Post by spadewarrior on 2008-08-12
OK I've started a list header file. After some research, I've created this function:

[PHP]void free_list(Link current) {
	Link tmp;
	
	while (current != NULL) {
		tmp = current;
		current = current->next;
		free(tmp);
	}

}
[/PHP]

I've made a very small program that to test this which mallocs() a list of two nodes, prints them out then passes the head node to free_list() to free the memory.

Valgrind is saying:

```
 malloc/free: 1 allocs, 0 frees, 8 bytes allocated.
...
 LEAK SUMMARY:
==8019==    definitely lost: 8 bytes in 1 blocks.
```

How come it's not being freed properly?

---

### Post by hod139 on 2008-08-12
> **spadewarrior said:**
> How come it's not being freed properly?
Because you are passing the parameter 'current' by value.

---

### Post by hod139 on 2008-08-12
> **nvteighen said:**
> 

This dynamic lists will serve as base for dynamic matrices. The end goal: create a little library for graphs in C that supports adjacency matrices to store edges. The list data type should afterwards also give adjacency lists support.

You should look into STL maps (I think Python calls them dictionaries.)

---

### Post by spadewarrior on 2008-08-12
I don't understand what you mean I'm afraid.

---

### Post by theyranos on 2008-08-12
Your free_list looks fine (and considerably better than my lazy recursive thing from before :)). I wrote a small test program myself that creates a two-node list, then passes it to your function, and Valgrind detected no leaks for me.

To find out why it's not working for you, we may need to see your very small test program.

---

### Post by theyranos on 2008-08-12
> **hod139 said:**
> Because you are passing the parameter 'current' by value.

This doesn't matter. If you look at the original post, "Link" typedef'd as a pointer.

---

### Post by nvteighen on 2008-08-12
> **hod139 said:**
> You should look into STL maps (I think Python calls them dictionaries.)
If I were in C++... I'm in C. The problem is that I want it to be as smallest as possible.

---

### Post by spadewarrior on 2008-08-12
OK that's good.

Here's the (possibly very wrong) test code:

[PHP]#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "list.h"

int main(void)
{
	Node thing;
	Link head = &thing;
	Lpntr pHead = &head;
	
	thing.num = 1;
	thing.next = NULL;
	
	Push( pHead, 34);
	
	while( head != NULL) {
		printf("%d, ", head->num);
		head = head->next;
	}
	
	free_list( head );
	
	return 0;
}

[/PHP]

And in case it's useful, here's list.h so far:

[PHP]#include <stdio.h>
#include <stdlib.h>

struct linked_list {
	int num;
	struct linked_list * next;
};


typedef struct linked_list Node;
typedef Node * Link;
typedef Link * Lpntr;

int list_count(Link headPointer);

void Push(Lpntr head, int n); 

int list_count(Link headPointer)
{
	int count = 0;
	Link current = headPointer;
	
	while ( current != NULL) {
		count++;
		current = current->next;
	}
	return count;
}

void Push(Lpntr head, int n) {
	Link newNode = malloc(sizeof(Node));
	
	newNode->num = n;
	newNode-> next = *head;
	*head = newNode;
}

void free_list(Link current) {
	Link tmp;
	
	while (current != NULL) {
		tmp = current;
		current = current->next;
		free(tmp);
	}

}
[/PHP]

---

### Post by theyranos on 2008-08-12
There are actually two problems in main.

First, you use the "head" pointer as a cursor to print all the values before calling free_list. When you do call free_list, head must already be set to NULL, otherwise the while loop above that call never would have exited.

Second, assuming you fixed the first thing, you'd either segfault or get the valgrind "double free" error, because the initial node "thing" is one that's being created (and automatically freed) by the compiler.

Here's an (untested; I don't have the internet and a compiler on the same computer :() rewrite of your main function that just fixes those two little things. Lemmie know if it doesn't work or you have more questions.

[PHP]
#include <stdio.h> 
#include <stdlib.h> 
#include <math.h> 
#include "list.h" 

int main(void) 
{ 
    Link head = malloc(sizeof(Node));
    Lpntr pHead = &head; 
     
    head->num = 1; 
    head->next = NULL; 
     
    Push( pHead, 34); 
    
    Link cursor = head;
    while( cursor != NULL) { 
        printf("%d, ", cursor->num); 
        cursor = cursor->next; 
    } 
     
    free_list( head ); 
     
    return 0; 
}  
[/PHP]

---

### Post by dwhitney67 on 2008-08-12
You should not be freeing the Node that you declared on the stack; that is, do not free 'thing'.

Either malloc() 'thing' from the heap, or start by free()-ing 'thing->next'.

---

### Post by spadewarrior on 2008-08-12
theyranos: Thanks a lot! That's fixed it. I'm going to read more about malloc() on the net now.

---

### Post by dwhitney67 on 2008-08-12
> **theyranos said:**
> There are actually two problems in main.

First, you use the "head" pointer as a cursor to print all the values before calling free_list. When you do call free_list, head must already be set to NULL, otherwise the while loop above that call never would have exited.

Second, assuming you fixed the first thing, you'd either segfault or get the valgrind "double free" error, because the initial node "thing" is one that's being created (and automatically freed) by the compiler.

Here's an (untested; I don't have the internet and a compiler on the same computer :() rewrite of your main function that just fixes those two little things. Lemmie know if it doesn't work or you have more questions.

[PHP]
#include <stdio.h> 
#include <stdlib.h> 
#include <math.h> 
#include "list.h" 

int main(void) 
{ 
    Link head = malloc(sizeof(Node));
    Lpntr pHead = &head; 
     
    head->num = 1; 
    head->next = NULL; 
     
    Push( pHead, 34); 
    
    Link cursor = head;
    while( cursor != NULL) { 
        printf("%d, ", cursor->num); 
        cursor = cursor->next; 
    } 
     
    free_list( head ); 
     
    return 0; 
}  
[/PHP]

What's the point of having/declaring 'pHead'?  Just use 'head'.

I think that what is really confusing is the typedefs.  There really should only be one:  Node.

Here's my take:
[PHP]#include <stdlib.h>
#include <stdio.h>


typedef struct Node
{
  int          num;
  struct Node *next;
} Node;


Node *insert( Node *node, int value )
{
  Node *newNode = malloc( sizeof(Node) );

  newNode->num  = value;
  newNode->next = node;

  return newNode;
}

void freeNodes( Node *node )
{
  while ( node != 0 )
  {
    Node *nextNode = node->next;
    free( node );
    node = nextNode;
  }
}

void displayNodes( Node *node )
{
  while ( node != 0 )
  {
    Node *nextNode = node->next;
    printf( "%d ", node->num );
    node = nextNode;
  }
  printf( "\n" );
}

int main()
{
  Node *head = 0;

  head = insert( 0,    10 );    // or just use insert( head, 10 ) because head = 0
  head = insert( head, 20 );
  head = insert( head, 30 );

  displayNodes( head );

  freeNodes( head );

  return 0;
}[/PHP]

---

### Post by theyranos on 2008-08-12
@dwhitney67: I concur. Having to actually remember which typedefs are pointers and which arent is one of the more annoying aspects of programming stuff for windows.

@The OP: You should really consider keeping the *s in your API.

---

### Post by spadewarrior on 2008-08-12
Duly noted.

---

### Post by Reiger on 2008-08-12
> **Lster said:**
> If we have to find the element first, then it will take O(n) time. The same goes for insertion...

Which is what I meant with "worst case", but meh: I'm talking from the purely API-style theory POV. In fact, on the basis of what I remember from the Datastructures courses which used Java for guinea pig language. And actually in Java an array is pretty much a collection of allocated 'cells' of which the position is known inside the heap. (That's fairly easy because the VM maintains the heap...) Hence the worst case of O(1) for an array; even though in truth it ought to be multiplied by lg(n). :D

---

