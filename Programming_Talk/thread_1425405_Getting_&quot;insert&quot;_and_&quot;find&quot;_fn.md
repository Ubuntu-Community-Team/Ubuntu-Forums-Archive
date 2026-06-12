---
title: "Getting &quot;insert&quot; and &quot;find&quot; fns to work"
date: 2010-03-09
forum: Programming Talk
---

### Post by trilobite on 2010-03-09
Hi all - 

 I've got the following C code which tries to create a very simple C equivalent of a Python dictionary (with keys and values). 

```
 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h> 

/*  Define the array size  */  
#define arrsize 5  

/*  Our "dictionary" consists of an array of structs */  
typedef struct dict {    
   char *key;
   char *data;    
}arr[arrsize] ;    


/*  Do a function to insert values into the dict. */  
dict insert(char *key, char *data) {            
    arr[x].key = key;
    arr[x].data = data;     
    return dict; 
} 
            

/*  Find data in the dict, given a key */     
char find(char *key) {  
    if arr.key == NULL { 
       printf("Error: key not found"); 
    } 
    else { 
       return arr.data; 
    } 
} 

                              
/*  Main   */  
int main(void)  
{ 
         
/*  Store some data  */  
insert("foo", "123"); 
insert("bar", "456"); 
insert("baz", "789"); 

/*  Find some data  */  
find("bar");   
    
return 0; 

}
  

``` 

What I'm having problems with is understanding how to make the "insert" function insert the data into the next available element in the array (and to give an error if no more are available). That's why I've got arr.[x]'s in the above code.  

I think the code is pretty much on the right track, but if someone can just help to get the above functions working, that would be great! 

Many thanks in advance - 
- trilobite

---

### Post by Some Penguin on 2010-03-09
If you're going to use plain arrays of a hard-coded length, you might as well consider wrapping them in a struct which includes the number of already-used spots.

But you should probably consider using a different structure entirely. like an array of linked lists where the appropriate index is computed by applying a function on the key.

---

### Post by trilobite on 2010-03-09
> **Some Penguin said:**
> If you're going to use plain arrays of a hard-coded length, you might as well consider wrapping them in a struct which includes the number of already-used spots.

But you should probably consider using a different structure entirely. like an array of linked lists where the appropriate index is computed by applying a function on the key.

Hi Some Penguin -  


Thanks very much for that. I'll try that approach and see how it goes.  
Thanks again - bye for now - 
- trilobite

---

### Post by MadCow108 on 2010-03-09
using an array as the underlying structure for a dictionary is simple but has some performance drawbacks.
You have a few choices of how to implementing it.
One would be to do a sorted insert. This means (binary) searching (-> bsearch) the position and moving all elements behind that one further back (->memmove)
This is linear in complexity and thus can be quite slow for big arrays.
Don't forget to resize the array if necessary.
Finding in this is now easy, just do a binary search. This has logarithmic complexity

Another way would be some kind of lazy sorting.
You could maintain a flag "needs_sorting" which is set every time new data is inserted/deleted.
If a find request is made and the flag is set you first sort the array (->qsort) reset the flag and then do the bsearch.
This has horrible performance when searches and inserts requests are mixed, but is quite good when they are separated (e.g. insert only at beginning of program after that only searches).

you should also have a look at (balanced) tree structures.
They have logarithmic complexity in _all_ cases. But you lose locality of reference and have a more complicated base data structure.

(What penguin described is called a hash table btw. They have constant amortized insert and access but bad worst case performance and memory profile)

It is a very good exercise to implement a few variants of these possibilities.
But you should resort to libraries providing advanced data structures when you need to use them.
glib for example provides a bunch of good data structures ready to use.

---

### Post by Some Penguin on 2010-03-09
And more specifically, I was talking about 'separate chaining', a pretty simple method of hashing.  e..g


[http://en.wikipedia.org/wiki/Separate_chaining#Separate_chaining](http://en.wikipedia.org/wiki/Separate_chaining#Separate_chaining)

There are a lot of ways to design hash tables, but that's probably the most straightforward. 

There's also linear probing, but that can be very ugly if you're doing a lot of deletions or if the number of items in your table varies drastically during a run (potentially, lots of reallocation and rehashing).

---

