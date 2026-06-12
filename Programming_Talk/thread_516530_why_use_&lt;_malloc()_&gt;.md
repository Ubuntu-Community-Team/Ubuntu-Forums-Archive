---
title: "why use &lt; malloc() &gt; ??"
date: 2007-08-03
forum: Programming Talk
---

### Post by nss0000 on 2007-08-03
Gents:

Continuing thru various C-tutorials, I've come across the MALLOC() function. Reading thru examples I can't see ( and it's never explained ) why you should ever NEED to use that function. 

Why indeed? I've never "run out" of memory before defining nefarious bunches of pointers and arrays. What's the deal ??

nss
******

---

### Post by tribaal on 2007-08-03
You have to use malloc() to allocate memory dynamically in C.
Say, if you wanted to have an array of arbitrary size like a stack or liked list for example.

- trib'

---

### Post by Wybiral on 2007-08-03
If you haven't ran into a point where you need dynamic memory, then you haven't been programming for too long :)

---

### Post by LaRoza on 2007-08-03
> **nss0000 said:**
> Gents:

Continuing thru various C-tutorials, I've come across the MALLOC() function. Reading thru examples I can't see ( and it's never explained ) why you should ever NEED to use that function. 

Why indeed? I've never "run out" of memory before defining nefarious bunches of pointers and arrays. What's the deal ??

nss
******

"malloc" is similar in function to the C++ "new" keyword. 

One reason to dynamically allocate memory is to effectively use the memory of the computer, another is to prevent the memory from going out of scope before you are done with it.

-EDIT For every malloc, there should be a "free()", for every "new" there should be a "delete".

---

### Post by LaRoza on 2007-08-03
[http://users.actcom.co.il/~choo/lupg/tutorials/unix-memory/unix-memory.html#c_alloc](http://users.actcom.co.il/~choo/lupg/tutorials/unix-memory/unix-memory.html#c_alloc)

---

### Post by slavik on 2007-08-03
because you might not know how much memory you want when writing your program?

simple example: a buffered file reader, where the user specifies the buffer size. :)

---

### Post by LaRoza on 2007-08-03
> **Wybiral said:**
> If you haven't ran into a point where you need dynamic memory, then you haven't been programming for too long :)

That is why the OP asked...

---

### Post by Jessehk on 2007-08-03
Here's an example where you won't know the amount of memory you'll need until you run the program. :)

```

#include <stdio.h>
#include <stdlib.h>

#define INBUFFSIZE 64u


/*
 * Will print a specified error message and exit
 * indicating a failure.
 */
void error( const char *msg ) {
    fprintf( stderr, "%s\n", msg );
    exit( EXIT_FAILURE );
}

void *xmalloc( size_t bytes ) {
    void *mem = malloc( bytes );
    
    /* If the memory could not be allocated... */
    if ( mem == NULL )
        error( "Error: Could not allocate memory." ); /* Or something */
    
    return mem;
}

int readInt( const char *prompt ) {
    char buffer[INBUFFSIZE];
    int result;
    
    printf( "%s", prompt );
    if ( fgets( buffer, INBUFFSIZE, stdin ) == NULL )
        /* Input could not be read for some reason */
        error( "Unknown error reading input" );
  
    if ( sscanf( buffer, "%d", &result ) != 1 )
        error( "Invalid input. Program quitting." );

    
    return result;
}

float average( int *numbs, int size ) {
    int sum = 0;
    int i;
    
    for ( i = 0; i < size; i++ )
        sum += numbs[i];
    
    return (float)sum / size;
}

int main( void ) {
    int n = readInt( "How nany numbers do you want to enter? " );
    int *numbs = xmalloc( n * sizeof( int ) );
    int i;
    
    for ( i = 0; i < n; i++ )
        numbs[i] = readInt( "Enter numb: " );
    
    printf( "The average of the numbers you entered is %.2f\n", average( numbs, n ) );
    
    free( numbs );
    return 0;
}

```

Feel free to ask questions (and others, feel free to criticize and improve my example). :)

---

### Post by winch on 2007-08-03
To calculate the average of a series of numbers you don't need to store the values. Just a running total and the count of numbers.

In ruby
```

total = 0
puts 'How nany numbers do you want to enter?'
count = gets.to_i
count.times do |i|
    puts "Enter number #{i + 1}"
    total += gets.to_i
end
puts "average = #{total / (count + 0.0)}"

```

---

### Post by nss0000 on 2007-08-03
Gents:

With all humility ... as the least/last/lowest C-coder on this N.G. ... I must protest discomfort at the various responses. They all seem to assume that I will NOT know the size of "datastructures" occurring in a program. 
I have a hard time imagining this in the context of scientific programming ( if you don't know relevant matrix and matrix sizes, then you wouldn't have the job! ),  and can just barely imagine it ( datamining a library for literal_strings of obscure length ??! ) when processing text.

More rudely I think, with pocket_change RAM prices you might as  well buy another 2/4-GIG instead of worrying about efficient memory use ( how Calvinist... )  or undersized arrays.

---

### Post by Mathiasdm on 2007-08-03
> **nss0000 said:**
> Gents:

With all humility ... as the least/last/lowest C-coder on this N.G. ... I must protest discomfort at the various responses. They all seem to assume that I will NOT know the size of "datastructures" occurring in a program. 
I have a hard time imagining this in the context of scientific programming ( if you don't know relevant matrix and matrix sizes, then you wouldn't have the job! ),  and can just barely imagine it ( datamining a library for literal_strings of obscure length ??! ) when processing text.

More rudely I think, with pocket_change RAM prices you might as  well buy another 2/4-GIG instead of worrying about efficient memory use ( how Calvinist... )  or undersized arrays.

Well, allow me to introduce you to the 'linked list', a datastructure that (in some cases) is better than the array, but will require dynamic memory allocation.

An element of a linked list contains:
-data
-a link to the next element in the linked list

Example:
struct linked_list_element {
DATA data;
linked_list_element* next_element;
}

A major benefit of a linked list is that the size can change: you can attach a new element to the back. You just do:

```
linked_list_element new_element = malloc(sizeof(linked_list_element));
last_element.next_element = &new_element;

```
(Sorry if I make some silly mistake ;-) The basic idea should make it clear)

If you're working with lots of programs on your computer, or have a program that stores a variable amount of data in memory, you DON'T want to work with a huge array. Example: if you start out with 16 integers, but know that (in the future) there's a small change you'll need 1 billion integers, do you really want to allocate a huge array?
It's very important to be able to program efficiently, and not waste memory/CPU time if you can do otherwise. Why waste money on more RAM, when you can just do a better programming job?

---

### Post by fct on 2007-08-03
Dynamic memory allocation is necessary when you some steps further from "Hello World"-like programs. That's not only C, languages like Java or C# use lots of dynamic memory, only it is transparent to the programmer so he doesn't manually allocate memory the way it's done in C.

And yes, that includes scientific computing, which makes use of a lot of it for dynamic data structures in memory that save a lot of time. You don't want to go field by field in a static array when you can use a binary tree for searching.

If you want an example of a worthy programmer not knowing how much memory he will need, consider developing a database engine that scales from hundreds to millions of registers.

---

### Post by hod139 on 2007-08-03
> **nss0000 said:**
> Gents:

With all humility ... as the least/last/lowest C-coder on this N.G. ... I must protest discomfort at the various responses. They all seem to assume that I will NOT know the size of "datastructures" occurring in a program. 
I have a hard time imagining this in the context of scientific programming ( if you don't know relevant matrix and matrix sizes, then you wouldn't have the job! ),  and can just barely imagine it ( datamining a library for literal_strings of obscure length ??! ) when processing text.

More rudely I think, with pocket_change RAM prices you might as  well buy another 2/4-GIG instead of worrying about efficient memory use ( how Calvinist... )  or undersized arrays.

What happens if the dataset is too large to fit on the stack?  You do realize that statically allocated memory resides in a different memory location than dynamic memory, and is of a much more limited space.  No matter how much RAM you buy, you will have a limitation to what can reside on the stack.

Also, it's funny you brought up scientific computing. 
As another poster pointed out, many data structure require dynamic memory to be efficient.  You should learn some of the basic data structures, linked list, binary tree, priority queue, etc, and then you might appreciate the power of dynamic memory.

---

### Post by aks44 on 2007-08-03
> **nss0000 said:**
> I must protest discomfort at the various responses. They all seem to assume that I will NOT know the size of "datastructures" occurring in a program.

The real problem IMNSHO is not that you don't know the size of A data structure... but rather that you CAN'T know the final NUMBER of items you'll have to handle.


A real world example:
At work the server we wrote has no practical limit on the number of clients (max. 2^64 clients which is way more than we'll ever have).

How would you handle this? Pre-allocate an array of 2^64 structures (which themselves are quite big, giving something like 2^65536+ pre-allocated bytes) or allocate each and every new client structure "on the fly"? (and I over-simplified the problem, each and every real world structure can have a variable amout of "children" structures which in turn... etc)

---

### Post by Wybiral on 2007-08-03
A good example that comes to mind (and has popped up a few times recently on these boards) is a particle system.

Most games use a universal particle system that manages projectiles, rain, explosions, smoke... etc...

You have NO possible way of know how much you will need at the time of writing the engine. Furthermore... The number changes rapidly throughout the program.

You might say "use a memory pool and keep count of how much is in it...

That's possible... But what happens when you have to remove an element from the middle? Ooops... Now you lose efficiency because you would have to copy the last element into it's place and decrease the count.

A better solution is for each particle to keep a pointer to it's next and previous particles... Append one by allocating it to the next pointer, and delete one by patching up the pointers in it's next/prev and freeing it.

This is a linked list.

As others have mentioned... You can't get too far in a low level language like C without a good understanding of ATD's (and I wouldn't recommend getting too far in higher level languages without having some understanding).

You make a dynamically changeable binary tree with static arrays and report back to me on that. :)

---

### Post by aJayRoo on 2007-08-03
Like all the other replies have suggested, it is very common (even in scientific computing) to need to use dynamically allocated memory. For example I have written code (in fortran 90) to numerically model the interactions between two or more hurricanes. The model reads a text file which sets all the parameters including the time-step and length of the model run. This means that the number of iterations in the model (and hence the amount of output produced) can vary and so dynamic allocation of memory is essential in order to be able to store all the output data efficiently.

---

### Post by Jessehk on 2007-08-03
> **winch said:**
> To calculate the average of a series of numbers you don't need to store the values. Just a running total and the count of numbers.


I'm aware of that. the example of finding the average was arbitrary. What was important was dynamically creating an array based on user input. :)

---

### Post by aks44 on 2007-08-03
> **aJayRoo said:**
> Like all the other replies have suggested, it is very common (even in scientific computing) to need to use dynamically allocated memory.

I'll even add that not only it is very common, but it is also a REQUIREMENT.

---

### Post by Modred on 2007-08-03
> **hod139 said:**
> You should learn some of the basic data structures, linked list, binary tree, priority queue, etc, and then you might appreciate the power of dynamic memory.

Just thought I'd point out that trees and heaps can be implemented just as easily, if not easier, with static arrays as with dynamic allocation.  Some simple arithmetic versus pointer manipulation.  Of course, I won't contest that you'll need dynamic memory allocation if your tree or heap ever runs out of space and you want to provide more.

[quote=nss0000]I have a hard time imagining this in the context of scientific programming ( if you don't know relevant matrix and matrix sizes, then you wouldn't have the job! )[/quote]

What if you have one program to work with multiple problems?  Might be nice if it can adapt to different size matrices. I'd hate to rewrite a program each time I need to solve a new problem!

---

### Post by hod139 on 2007-08-03
> **Modred said:**
> Just thought I'd point out that trees and heaps can be implemented just as easily, if not easier, with static arrays as with dynamic allocation.  Some simple arithmetic versus pointer manipulation.  Of course, I won't contest that you'll need dynamic memory allocation if your tree or heap ever runs out of space and you want to provide more.

Well, if we are going to get technical, a heap is an array representation of a tree, and a binary heap is a priority queue.  

Now, how in the world can you use a static array to implement a heap?  Say you allocate the array to hold N items.  What happens when you insert N+1 items.  You have to resize the array.  This is dynamic memory management.  There is no way around it.  Even if you allocate an array the max size of the stack, I can insert more than that many elements.

---

### Post by Modred on 2007-08-04
> **hod139 said:**
> What happens when you insert N+1 items.  You have to resize the array.  This is dynamic memory management.  There is no way around it.

Oh wow, you can read what I said, quote it, rephrase it, and think you're telling me something new.

[quote=Modred]Of course, I won't contest that you'll need dynamic memory allocation if your tree or heap ever runs out of space and you want to provide more.[/quote]

Sounds awfully familiar.  My point is that you don't need dynamic memory allocation to perform heap operations on an array, but from your original post I got the idea that just learning how a heap works would magically teach the need for dynamic memory.  If you limit your heap to holding X items at maximum, then you can use an array of size X and you're done.  For a heap that can dynamically grow, as you're describing, then yes, you would need to dynamically allocate a new array at a larger size.

Now that we've said the same thing at least three times to make sure each other understand, why don't we move on?

Also, if we're going to be technical, then a heap is not an "array representation of a tree".  It's a tree that satisfies a heap property, such as each root in a subtree has a value greater than any value in its subtrees (max-heap).  The actual implementation doesn't affect its definition as a heap.

---

### Post by hod139 on 2007-08-04
> **Modred said:**
> Oh wow, you can read what I said, quote it, rephrase it, and think you're telling me something new.

Sorry about that.  I must be getting tired, not sure how I missed it.

> Also, if we're going to be technical, then a heap is not an "array representation of a tree". It's a tree that satisfies a heap property, such as each root in a subtree has a value greater than any value in its subtrees (max-heap). The actual implementation doesn't affect its definition as a heap.Again, you are right.  I must be really tired.  An array is commonly used, and is how I often think of the underlying structure, but yes, a heap simply must satisfy the heap property.

I think it's time I stop posting tonight, and go to bed :)

---

### Post by slavik on 2007-08-04
memory is not cheap, memory is cheaper than the programmer.

here's a reason why node based storage is not great: it causes the CPU to jump around in memory, thus producing more L2 misses (since the CPU can't grab a bunch of relevant stuff around what you are requesting).

and if you are the type that says "memory|CPU|etc is cheap", you most likely have never programmed a microwave or a rover sent to another planet ...

hey memory is cheap, let's stick in 2GB of RAM into a microwave. so what the upgraded system makes the rover 2KG more massive, the stuff was cheap!!!

as for processing strings of arbitrary length, try data mining the human genome project ;)

@modred: how about an unbalanced tree/heap? the reason why an array is used for heapsort is because the tree has to be "almost complete" and thus it also becomes easy to allocate just enough space for it as an array.

---

### Post by nss0000 on 2007-08-04
Gents:

Thank you for the examples and discussion of MALLOC(). I see that my ignorance of C-language tools is nearly without bound and some 'dynamic' allocation of study time is required. 
I have not yet taken up STRUCTURES or LINKED-LISTS( K&R seems not to discuss them ) ... and have got a bit tied-up in various input/output issues. However, I will stay-awake for situations where some simple pre-defined variable size gets me into trouble.

Thanks again for your thoughts:

nss
******

---

### Post by Modred on 2007-08-04
> **slavik said:**
> @modred: how about an unbalanced tree/heap? the reason why an array is used for heapsort is because the tree has to be "almost complete" and thus it also becomes easy to allocate just enough space for it as an array.

I fail to see why these posts keep coming up with "but what about this?"  I never said that you wouldn't need dynamic memory allocation for certain uses, merely that understanding how a data type works doesn't guarantee you'll be using dynamic memory.  Knowing how to add and remove values from a heap doesn't teach you dynamic memory, unless you're implementing it and realize something along the lines of "oh, my array is wasting lots of unused space and then not having indices large enough for this new element."  But just knowing how the data structure works?  You can do all of that with a pencil and piece of paper.  Hence no appreciation for dynamic memory allocation is guaranteed by just studying the data structures.

---

### Post by slavik on 2007-08-04
> **Modred said:**
> I fail to see why these posts keep coming up with "but what about this?"  I never said that you wouldn't need dynamic memory allocation for certain uses, merely that understanding how a data type works doesn't guarantee you'll be using dynamic memory.  Knowing how to add and remove values from a heap doesn't teach you dynamic memory, unless you're implementing it and realize something along the lines of "oh, my array is wasting lots of unused space and then not having indices large enough for this new element."  But just knowing how the data structure works?  You can do all of that with a pencil and piece of paper.  Hence no appreciation for dynamic memory allocation is guaranteed by just studying the data structures.
my post was to simply point out that sometimes, it is more efficient to represent something that is thought of to be node based in terms of an array. :)

---

### Post by nss0000 on 2007-08-04
Hummm ... oh I think I see. STRUCTURES & LLists are just workarounds, cause C doesn't allow multi-dim arrays with different data_types.

---

### Post by jpkotta on 2007-08-04
> **nss0000 said:**
> Hummm ... oh I think I see. STRUCTURES & LLists are just workarounds, cause C doesn't allow multi-dim arrays with different data_types.

While using a linked list would be the prefered method (to the point that you would almost certainly never do what I'm doing here), it isn't necessary.  

```

#include <stdio.h>
#include <string.h>

#define ARRAY_SIZE 5

int main(void) 
{
    void *array[ARRAY_SIZE];
    int the_int;
    long the_long;
    char the_string[80];

    array[0] = &the_int;
    array[1] = &the_long;
    array[2] = the_string;

    *(int *)array[0] = 1024;
    *(long *)array[1] = 1<<20;
    strncpy((char *)array[2], "this is a string", 80);

    printf("the_int = %d\nthe_long = %ld\nthe_string = %s\n", 
           *(int *)array[0], *(long *)array[1], (char *)array[2]);

    return 0;
}

```

A linked list is more than a workaround.  It is a different type of data structure than an array.  It has slower access time but faster insertion/deletion time.

---

### Post by Wybiral on 2007-08-04
> **jpkotta said:**
> A linked list is more than a workaround.  It is a different type of data structure than an array.  It has slower access time but faster insertion/deletion time.

Linked lists make it possible to insert and delete info from the front AND the middle.

With an array you have to move all of the elements back.

It's not a work around, and it's not inefficient... It's a standard practice as well as the other common ADT's.

EDIT:

Also... It only has slower access time when you need to arbitrarily access an element... Iterating or accessing the front/back elements generally is not slower.

---

### Post by the_unforgiven on 2007-08-05
> **jpkotta said:**
> A linked list is more than a workaround.  It is a different type of data structure than an array.  It has slower access time but faster insertion/deletion time.
That is because the arbitrary element's address cannot be computed at compile time - the way it can be done for an array. 

Mostly, the address calculation for an arbitrary element in an array gets compiled as a single instruction (in x86 asm) as LEA wrt some indexing register. This is possible because arrays are by definition contiguously allocated in the memory.

This is not possible for any linked data structure because the nodes are not adjacent in the memory - in fact, most of the times, they're scattered all over the place. So, we lose heavily on the locality of reference, cache misses and hence slower access.

BUT, the linked data structures provide us following advantages:
o. ANY data structure can be represented - which I doubt is possible with arrays - except for possibly tabular data structures. I know, a simple tree can also be implemented as an array, but what about more complex indexing structures like B-Trees?
o. Though, access to arbitrary element is slower (as compared to indexed/array method), it does allow us to insert/delete arbitrary element in O(1).
o. Array size needs to be known at compile time. Even if you can relocate the array to increment/decrement the size, it involves allocating new contiguous memory area and moving all the required elements from the current memory area which is a very time consuming operation.
o. Dynamic growth/shrinking as per the available memory and program requirements. This also helps in reducing the waste of memory - an array still consumes memory whether all the cells are populated or not.

Also, just throwing more memory because it is cheaper is not a solution because then the OS has to manage the additional memory. Moreover, it might not be even possible on the platform that you're using. For example, IA-32 (aka x86) has a theoretical limit of 4G virtual memory addressability (this is, not taking into consideration PAE). So, adding more memory is not always an option.

The reason why linked data structures were invented is because arrays have inherent limitations.

My 2 cents ;)

---

### Post by nss0000 on 2007-08-05
Reading about the WWW, I gather that static arrays can be sized right-up-to the total available (hardware) RAM.  But I do see the practical issue:

On my x64 kit, a static 3-dimx10^3 array of DOUBLES will send me running to NEGG, and anyrate with only 8-GIG total available I'm quickly SOL. No room for more than a couple of these_guys, so you better write-off data to storage, toss the array, free its' memory  and reuse the array "name". Or suchlike ... 

Am I even close to the MALLOC() rational? I really need to code & test-out  my blablabla fearing the NOT-EVEN-WRONG syndrome.

nss
*******

---

