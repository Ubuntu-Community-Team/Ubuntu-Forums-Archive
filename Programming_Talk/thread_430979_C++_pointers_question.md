---
title: "C++ pointers question"
date: 2007-05-02
forum: Programming Talk
---

### Post by DrPppr242 on 2007-05-02
I'm trying to learn more about C++ and I was told that pointers are very important but I'm not sure if I unserstand what they are used for or why they're useful.  I think the syntax would be like...
> 
int var1 = 2;
int *pntr;

*pntr = & var1;
which would associate *pntr with var1's memory location so any changes to either *pntr or var1 would affect the other
> 
var1 = 12;
cout << *pntr << endl;
*pntr = 15;
cout << var1;
would then display:
12
15
right?  But if thats how pointers work I don't understand the need or usefulness of having a *pntr variable when using var1 in every instance does the same thing.  Sorry for the long post but could someone please explain to me how this works.

---

### Post by siiib on 2007-05-02
ok one is called call by value .. the other call by reference.. look it up in your book..ok heath robinson explanation.. techie types bear with me
basically when you pass values to a function they are copied across to a work area called the stack.. for simple built in data types like float or int the performance overhead is minimal as they will fit into a cpu register.. however if you copy a more complex (and bigger) data type like a struct, class whatever then the heap has trouble as it only has so much space.. it has to keep loading and reloading bits and this takes time.. so it is easier to pass the pointer to the memory location of the class or struct and use the actual information that resides in memory on the heap.. you manipulate the 'actual' values and not copies which are copied.. worked on and then passed back to replace the original if necessary..
so mainly its a  performance thing.. you can pass a large data structure by value if you want but it will make your program run like a dog and is considered bad programming practice.. if youare using c++ you may wish to check out references which are a bit like pointers but tend to be used if your function is 'read only'.. they are much easier to follow..
hth

---

### Post by DrPppr242 on 2007-05-02
thanks a ton for the reply, do you know of a place that would have simple source code example I could look at? cause I'm still a little confused I know when I use a function and pass by reference I use the &, but I've never needed to initialize a pointer with the *, is a pass by reference function the same as a pointer?

---

### Post by skeeterbug on 2007-05-02
> **DrPppr242 said:**
> thanks a ton for the reply, do you know of a place that would have simple source code example I could look at? cause I'm still a little confused I know when I use a function and pass by reference I use the &, but I've never needed to initialize a pointer with the *, is a pass by reference function the same as a pointer?

[http://www.codersource.net/c++_pointers.html](http://www.codersource.net/c++_pointers.html)

---

### Post by steve.horsley on 2007-05-02
The value of pointers becomes apparent when you start using pointers to point to an element in an array or other structure. This is all then dealing with un-named variables or structures - it's difficult to show the value with a simple example like the one above. But in complex structures like linked lists, you can snap a new element into the list just by changing the pointers of the neighbours to point to the new element. This site gives a good intro to the idea:
[http://en.wikipedia.org/wiki/Linked_list](http://en.wikipedia.org/wiki/Linked_list)

And the principle of having complex structures, classes, objects with pointers to other objects, linking them together in a mesh that somehow represents the problem being solved is very powerful and widespread. It can be used for almost any problem that models relationships between objects, and of course you can follow the relationships between objects by following a trail of pointers from object to object.

---

### Post by DrPppr242 on 2007-05-02
thanks again I'm starting to get an idea of what they're for now but I think I'll need a bit more experience to get the full picture, but your saying that they're generally used for things like accessing a member of an object without using a method, or and element of an array.

---

### Post by Dancingwllamas on 2007-05-03
The main use for pointers is dynamic memory (ie: linked lists as some one already mentioned). Instead of creating enough space to store anything your program will ever need to store, you can allocate memory during runtime.

For example, lets say that you want a user to type in a set of numbers and to store them in an array. You don't know exactly how many they want to input, so you could either create a very big array or you can rely on dynamic memory. Assuming you are storing an array of integers:

```

int *i_ptr; //pointer you are going to use for dynamic memory
int number_of_numbers //how many values the user inputs

cout << "How many values do you want to input?" << endl;
cin >> number_of_numbers;

i_ptr = new int[number_of_numbers] //creates an array of values with number_of_numbers places to store data
for(int i=0; i<number_of_numbers; ++i)
     cin >> iptr[i];   //you do not need to dereference iptr with * with arrays because of the way C++ works

```

When done with the memory, be sure to use "delete [] i_ptr;" to return the memory to the system, preventing a memory leak. I would also recommend reading [http://www.cplusplus.com/doc/tutorial/dynamic.html]("http://www.cplusplus.com/doc/tutorial/dynamic.html") to get a better understanding of how to work with dynamic memory and pointers.

Hope this helps.

---

### Post by WSayin on 2007-05-03
I faced the same problem when I first started C/C++, what the heck are pointers for? It doesn't really make sense when you are looking at individual variables. For me, their use finally clicked when I started looking at linked lists. The way I think of pointers is "They allow you to allocate memory to a variable without actually giving it a name." Hopefully that doesn't confuse the !%#% out of you.

---

### Post by hollowhead on 2007-05-03
I use pointers for some of the points made in the post above and also returning more than one value from a function.

---

### Post by baltimark on 2007-05-03
> **DrPppr242 said:**
> thanks again I'm starting to get an idea of what they're for now but I think I'll need a bit more experience to get the full picture, but your saying that they're generally used for things like accessing a member of an object without using a method, or and element of an array.

I don't think that's what anyone is saying. You're mixing up concepts a little. When you say "accessing a member of an object" you make it sound like accessing a member of a class in C++. That's not what pointers are for. 

First of all, the syntax in your original example is wrong. It should be

```

int var1;
int *p;
p = &var1

```

p is an address of a pointer. &var1 is an address. *p is what the pointer points to.  

*p is an int and you can't assign an address to an int.

Other than that, your code seems all right and its output is what you say. 

Pointers are useful for many things, but a main thing is that you can create something large (a file, an array, whatever) and pass its address around your program instead of the whole thing. 

For instance, when you get into passing variables into functions, you'll be able to just pass a pointer to the variable (e.g. xp) instead of passing all of the information in xp.

It's hard to really explain them without examples, but I'll give an analogy. Think of a street of houses. You have:

1) an address  (&var1 or p)

2) how many people live at that address (var1 = 12, or *p = 12)

p is an address.  (&var1 is an address)

*p is what's at the address. (var1 is what's at the address)


When you have arrays. . .

p is the address

p[0] is what's at the address  (12)
p[1] is what is "next door"       (maybe 7)
p[2] is "next door" to that     (maybe 6)
etc.

This is much easier than trying to write code where you make a separate variable for each house. p0, p1, p2, etc.

In your example, using addresses is just as easy as using values. When you have a whole "street", it becomes easier to just handle the first address and then start from there.

So, you have a pointer to houses (think "int" pointer). 

To carry the analogy further, if you wanted a pointer to "hotels" (think "double" pointer), you need a different kind of pointer (double *dp). When you try to dereference a pointer that's supposed to be a house, but there's a hotel there, you're going to get gobbledygook.

---

### Post by ghandi69_ on 2007-05-03
> **DrPppr242 said:**
> thanks again I'm starting to get an idea of what they're for now but I think I'll need a bit more experience to get the full picture, but your saying that they're generally used for things like accessing a member of an object without using a method, or and element of an array.

I just remember my professor, for understanding purposes.. told us to read it backwards.

For example..

int *x.

You would read... 'x is a pointer to an integer'

Also remember that '*x' used together from here on can be treated like any int variable.

Another thing way to think of it is that '&*x' is the same as 'x' at this point. 

Others have already provided good information, just trying to add something different that might help.

Another thing of note, is lets say you have int *x = 5

if you do cout << *x + 5; you should get 10
if you do cout << x+5 ; you would get some crazy memory address where something is stored.

---

### Post by DrPppr242 on 2007-05-03
baltimark, thanks for the great explanation, I think I get what they're used for now.

---

### Post by ios_base on 2007-05-04
Are these memory addresses located in the stack or what?  Some place in the RAM I'm fairly sure.

---

### Post by baltimark on 2007-05-04
> **ios_base said:**
> Are these memory addresses located in the stack or what?  Some place in the RAM I'm fairly sure.
This stuff isn't really my area of knowledge, but when you create a variable (y = 5), it is pushed onto the stack. 

The address is "located" in the ram. . .you can ask the computer to return an address 

```

cout << &y

```
or the value stored at that address. 
```
cout << y
```

But, an address can refer to a place on the heap, on the stack, or in registers.

---

### Post by slavik on 2007-05-04
in C, when you allocate stuff with malloc (C++ uses new which has extra features and is an operator, not a function), it goes to the operating system to ask for memory, since you can't simply 'give' memory, you are given an address of where you may write and that is what malloc gives back (so does new, but new can sometimes do something extra).

---

### Post by psusi on 2007-05-04
> **baltimark said:**
> 
But, an address can refer to a place on the heap, on the stack, or in registers.

Registers aren't memory and don't have addresses, so pointers can't point to those.  Local variables are allocated on the stack, globals and statics are allocated on the code ( for const data ), data or bss segments, and malloc/new allocate from the heap.  Pointers can point to any of them.

---

