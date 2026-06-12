---
title: "Pointer, weird error!!"
date: 2007-05-08
forum: Programming Talk
---

### Post by Adntu on 2007-05-08
Hi
I am learning c++ pointers, I tried the following fragment:
```

int p1*;
*p1=1;
int p22=4;
cout<<p22;
```

and it gives: 

```
Segmentaiton fault (core dumped)
```

but when I added new int:
```

int p1*;
int y;
*p1=1;
int p22=4;
cout<<p22;
```

it works fine!!! is there anything I did not get about pointers causes this behavior???

---

### Post by hod139 on 2007-05-08
> **Adntu said:**
> Hi
I am learning c++ pointers, I tried the following fragment:
```

int p1*;
*p1=1;
int p22=4;
cout<<p22;
```and it gives: 

This code shouldn't even compile.  The first line should be changed to:
```

int *p1;

```

---

### Post by Adntu on 2007-05-09
I am sorry, I wrote it incorrect here, but in my file it is:
```
#include <iostream>
using namespace std;
main ()
{
int *pa;
float *ps;
char *pd;


*pa=1;
*ps=2;
*pd=3;
cout << *pa<<*ps<<*pd;
return 0;
}

```

as I said I am just trying it out.
so what might be the cause???
thanks

---

### Post by Wybiral on 2007-05-09
Pointers are generally used to point to addresses, you're using them to store values... If that's all you need, just use a normal variable,

---

### Post by Adntu on 2007-05-09
no, this is not a functional code, just I am trying to use the pointers, would you please tell me what is wrong with my code? I just wrote it similar to some website and to one book I have????

---

### Post by seamless on 2007-05-09
This is your problem:
```
int *pa;
*pa=1;
```
You create a pointer to a memory address then write to it. However, you have never allocated memory at that address to store the value.

You need to do something like:
```
int *pa = new int;
*pa=1;
delete pa;
```
Be sure to use a corresponding delete with every new otherwise the memory will not be freed and you will have created a nice memory leak in your program.

---

### Post by siiib on 2007-05-09
try this

#include <iostream>
using namespace std;

int main ()
{

// initialise values
int a = 3;
float s = 3.14;
char d = 'c';

// create pointers
int *pa;
float *ps;
char *pd;

//give pointers addresses of values
pa=&a;
ps=&s;
pd=&d;


cout << "actual value of pa: " << *pa << endl;
cout << "actual value of ps: " << *ps << endl;
cout << "actual value of pd: " << *pd << endl;

cout << "address value of pa: " << pa << endl;
cout << "address value of ps: " << ps << endl;
cout << "address value of pd: " << pd << endl;

return 0;


}

make any sense??  note pedants: i've left the new and delete stuff out to make it a bit clearer.. see previous post.. this would be considered poor practice in real life but for teaching purposes makes a point

---

### Post by seamless on 2007-05-09
I'm going to briefly explain what siiib has done a bit.

int a = 3; // this will create an int on the stack and allocate memory for it.
int *pa; // this will create a pointer of type int.
pa=&a; // this will set pa to point to the memory address of a.

Now any manipulation of *pa will change a because pa points to the address of a. So:
*pa=14; // now a == 14.

A pointer simply points to a memory address. You need allocated memory at that address to manipulate the value. You can either do this by creating an object on the stack like in siiib's example or you can create it on the heap using new. If the object is created on the stack the memory will be freed once the object is out of scope. For example if you have it in a function call x() then once the program leaves x() then the memory will be freed. If you create it on the heap using new then it will remain until you explicitly free it using delete.

Simply put a pointer poitns to something you either have to set it to point to something already created or create something for it to point to.

---

### Post by siiib on 2007-05-09
heh thanks for the explanation.. i was eating my dinner at the time..

 i think what has you confused is that you are trying to 'allocate' a value using the dereference operator.. the dereference operator * is special in that it gives you the value at an address not the address.. by logical extension and thinking ahead (like i think you have) you'd think that it would work the other way wouldn't you?? but it doesn't really  work like that.. *pa ==4; is not something that you'd normally see..thats just how it is i'm afraid.

hth

---

### Post by jamescox84 on 2007-05-09
They're what we call dangling pointers, they point to some unknown location. Pointers point to a memory address, that's what they store, the address. If you just declare a pointer without initializing it with a default value, it points to a unknown area in memory. When you try to dereference it and assign it a value like this ```
*p = 10;
``` chances are your writing to memory you don't have permission to write to, hence the Segmentation Fault. If you want to give it something to point to other than another variable, then you can allocate a new data with new like this, but don't forget to release the allocated memory with delete before the program end's or you will have a memory leak.

```

#include <iostream>

int main()
{
    int *p = new int; // Allocates memory for a new int
    
    *p = 42; // Now we can access that memory
    
    std::cout << *p << std::endl;

    delete p; // Never, ever forget to free memory!!!

    return 0;
}

```

Hope that helped explain things, pointers are very useful for somethings but it's recommended that where ever possible you should use references.

---

### Post by siiib on 2007-05-10
int *p = new int; // Allocates memory for a new int

<groan> only if you're using the heap.. whats a heap??.. anyone?

p.s.thx you just won me a coffee:popcorn:

---

### Post by jamescox84 on 2007-05-10
Sorry, I realize most of what I wrote had already been explained, so sorry about that.

The heap is a large area of memory that applications can allocate parts of, when needed.

---

### Post by Adntu on 2007-05-10
Oooh! a lot of explanation and examples as well, thank you very much guys, it is clear enough for me now, but still I have two questions:
-what is the proper way to manage memory when dealing with pointers? I  mean should I use the "new/delete" approach or the stack one?
-in case there is a "memory leak" does this mean memory will not freed until the program ends, or will not for ever?
again thanks a lot, I appreciate your help! better than some books!!!

---

### Post by amo-ej1 on 2007-05-10
when you have memory leak the memory will not be freed until your program terminates. But a large memory leak will have your system go out of memory and end up unwanted results (typically you application will be killed by the kernel, but it's also possible that other applications get killed in order to free the memory). This is something you don't want to see on e.g. a webserver

Edit:

this can be easily tested, create an application which looks like:

int main(){ while(1){ int * a = new int(); }


Concerning your stack approach, the stack approach is the safest, however it can't be applied. If you have an application which reads a number and then reads that amount of integers. You could allocated the first number on the stack but after this you would need to allocate the space for the next values to read. So in the most typical case you won't know at compile time how much data there is to process (e.g. reading from a network or from a file or user input)

---

### Post by seamless on 2007-05-10
> **Adntu said:**
> -what is the proper way to manage memory when dealing with pointers?
When dealing with pointers only worry about memory management when you use new yourself. Only memory that is allocated with new needs to be freed with delete.

> **Adntu said:**
> I  mean should I use the "new/delete" approach or the stack one?
You need to use both depending on the situation and your implementation. They are both there and both have their place. A good rule of advice is use the stack when you can.

Some examples of when you have to use the heap with new and delete are:
 * Objects on the stack are deleted when their scope ends so if you need an object to be persistent.
 * You are using lots of memory, either lots of objects or data. The stack has a size limit usually much smaller than the heap. This is defendant on the system and I believe the compiler as well.
 * Any case where you don't know the exact amount of memory you are going to use. For instance using a linked list to store a variable list of data.

---

### Post by siiib on 2007-05-13
>The heap is a large area of memory that applications can allocate parts of, when needed.
heh sorry i was being ironic..:)  what i was trying to say is can we not get ahead of ourselves confusing the cr8p out of someone when they just need a simple stack based example to get them started for now..thx for all contributions.. good thread.:popcorn:

---

### Post by thelinuxguy on 2007-05-13
> **jamescox84 said:**
> They're what we call dangling pointers

Adntu: It is very obvious but Wikipedia has a good article on dangling pointers in case you are interested. [http://en.wikipedia.org/wiki/Dangling_pointer](http://en.wikipedia.org/wiki/Dangling_pointer)

---

