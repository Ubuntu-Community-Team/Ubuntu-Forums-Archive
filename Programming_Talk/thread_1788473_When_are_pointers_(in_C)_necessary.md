---
title: "When are pointers (in C) necessary?"
date: 2011-06-22
forum: Programming Talk
---

### Post by stamatiou on 2011-06-22
Hey guys,
Can you tell me when is it necessary to use pointers in C and not normal variables? Can you also give me an example?
Cheers!

---

### Post by schauerlich on 2011-06-22
Say you have a big struct that you want to pass into a function to modify. You can have this function take in a copy of the struct, modify that copy, then return the copy in the place of the original. Or, you can pass in a pointer to the struct, modify the struct in place, and be done with it. Two (potentially slow) copy operations, or zero. Your choice. :)

---

### Post by stamatiou on 2011-06-22
> **schauerlich said:**
> Say you have a big struct that you want to pass into a function to modify. You can have this function take in a copy of the struct, modify that copy, then return the copy in the place of the original. Or, you can pass in a pointer to the struct, modify the struct in place, and be done with it. Two (potentially slow) copy operations, or zero. Your choice. :)
Sorry but I have a few more questions, you know, I am not very good at C and also my English aren't the best...
    1.Struct = Programm?
    2.Why would I want to pass a "struct" into a function?
    3.What do you mean by modifying?

---

### Post by Barrucadu on 2011-06-22
Not a program, a [struct](http://en.wikipedia.org/wiki/Struct_(C_programming_language)).

---

### Post by Petrolea on 2011-06-22
> **stamatiou said:**
> Sorry but I have a few more questions, you know, I am not very good at C and also my English aren't the best...
    1.Struct = Programm?
    2.Why would I want to pass a "struct" into a function?
    3.What do you mean by modifying?

Struct is a group containing variables (but it can get very complex). Why pass a struct? So you don't have to pass every variable by itself, some pre-defined functions require only one argument, so if you want to pass more variables to it, you would pass a struct containing them (for more info, google is useful).
I think modifying means changing values in a struct.

---

### Post by andrew1992 on 2011-06-22
A struct is just a clump of related data. Don't even worry about the struct example - let's say you have an array of ten integers, and need to pass this array into a function (say, to compute the sum of the elements of the array).  If you passed in the array without declaring the argument to be a pointer, _all_ of the elements of the array would be copied into a new location in memory so that the function gets its own copy. However, if you passed in a reference to the array (a pointer to its first element), it would only have to copy the size of a single pointer to the function. This can speed up execution quite a bit (and use less memory) when you start using large data structures.

---

### Post by stamatiou on 2011-06-22
> **andrew1992 said:**
> A struct is just a clump of related data. Don't even worry about the struct example - let's say you have an array of ten integers, and need to pass this array into a function (say, to compute the sum of the elements of the array).  If you passed in the array without declaring the argument to be a pointer, _all_ of the elements of the array would be copied into a new location in memory so that the function gets its own copy. However, if you passed in a reference to the array (a pointer to its first element), it would only have to copy the size of a single pointer to the function. This can speed up execution quite a bit (and use less memory) when you start using large data structures.
So whenever I see pointers in tutorials and code, I can also use variables? the pointers are used only for speed reasons?

---

### Post by simeon87 on 2011-06-22
Pointers are necessary when you want to refer to a memory location where some data is stored.

For example, when you are building a linked list then you'll want each node to consist of:

- a piece of data
- a pointer to the next node of the linked list

In the second case it can't be a variable because you don't want to store the next node in the previous node, you just want to refer to where the next node is located in memory. That way, you can walk over the linked list easily.

---

### Post by schauerlich on 2011-06-22
A struct (short for structure) is basically a bunch of variables that you stick into one big blob that you can pass around. That means that your struct can consist of 5 integers, an array of 100 characters, etc, and potentially be very large. 

Take the following example:

```
#include <stdio.h>
#include <string.h>

typedef struct person {
  int age;
  char name[80];
} person_t;

person_t rename_person(person_t p, char *name) {
  strcpy(p.name, name);

  return p;
}

void rename_person_fast(person_t *p, char *name) {
  strcpy(p->name, name);
}

int main(int argc, char **argv) {
  person_t joe;
  person_t alberto;

  joe.age = 30;
  alberto.age = 40;

  joe = rename_person(joe, "Joe");
  rename_person_fast(&alberto, "Alberto");

  printf("%s is %d years old\n", joe.name, joe.age);
  printf("%s is %d years old\n", alberto.name, alberto.age);

  return 0;
}

```

When we use rename_person, we copy the entire struct person called "joe" into the function, change the value of the "name" field, then copy this new version back into the old variable. With rename_person_fast, all we do is pass in a pointer to the struct person named "alberto". Then, *the original* alberto is modified, without copying anything anywhere.

---

### Post by cgroza on 2011-06-22
I am surprised no one mentioned polymorphism...

---

### Post by schauerlich on 2011-06-22
> **cgroza said:**
> I am surprised no one mentioned polymorphism...

I'm not sure what you mean.

---

### Post by cgroza on 2011-06-22
> **schauerlich said:**
> I'm not sure what you mean.
Ouch, I was thinking C++ then. My bad, sorry.

---

### Post by unknownPoster on 2011-06-22
> **cgroza said:**
> I am surprised no one mentioned polymorphism...

Only applies to object oriented programming. Which you can kind of implement in C with structs with function pointers, but that's a bit out of scope for this question.

---

### Post by BkkBonanza on 2011-06-23
You shouldn't think of pointers as not being "normal" variables. They are. A pointer is just a variable that contains an address of some other piece of data. You use pointers all the time without even realizing it. When you use a string (in C an array of char),

char szBob[] = "BobBob";

szBob is actually a pointer and can be used like one in various ways. It is the address of the memory location where those char are stored.

As long as you think of pointers as addresses of specific data types you won't go wrong in working with them.

---

### Post by zobayer1 on 2011-06-23
How about an **[COLOR=Red]Array of Functions[/COLOR]** ?
Say, you want to call some consecutive similar type of functions in a loop? All you need to do is to store their pointers...
Here is a short example [http://zobayer.blogspot.com/2010/02/cc-array-of-functions.html](http://zobayer.blogspot.com/2010/02/cc-array-of-functions.html)

---

### Post by stamatiou on 2011-06-23
> **zobayer1 said:**
> How about an **[COLOR=Red]Array of Functions[/COLOR]** ?
Say, you want to call some consecutive similar type of functions in a loop? All you need to do is to store their pointers...
Here is a short example [http://zobayer.blogspot.com/2010/02/cc-array-of-functions.html](http://zobayer.blogspot.com/2010/02/cc-array-of-functions.html)
And when do we use pointers as functions?
For Example:
```
main()    {
int *function(int a, int b)    {

}
}
```

---

### Post by zobayer1 on 2011-06-23
> **stamatiou said:**
> And when do we use pointers as functions?
For Example:
```
main()    {
int *function(int a, int b)    {

}
}
```
This is not a pointer to function, this is a function returning an integer pointer.

One practical example is the qsort() library function:

```

void qsort(void *base, size_t nmemb, size_t size, int(*compar)(const void *, const void *));

```Here, you have to give a pointer to a function of this form:
```

int comp(const void *, const void *);

```Here is an example:
```

int comp(const void *a, const void *b) {
    return *(int *)a - *(int *)b;
}

int main() {
    int i, a[10] = {2, 5, 1, 3, 54, 6, 2, 4, 5, 1};
    qsort(a, 10, sizeof(int), comp);
    for(i = 0; i < 10; i++) printf("%d\n", a[i]);
    return 0;
}

```There are also many applications, like when you try to handle a signal, or create some posix thread.

---

### Post by schauerlich on 2011-06-23
> **zobayer1 said:**
> One practical example is the qsort() library function:

Let's not confuse the poor fellow, this is more than he needs to deal with if he doesn't know when to use normal pointers.

---

### Post by zobayer1 on 2011-06-23
> **schauerlich said:**
> Let's not confuse the poor fellow, this is more than he needs to deal with if he doesn't know when to use normal pointers.

Ow, I though qsort might be a useful one...

---

### Post by Arndt on 2011-06-23
One can write a lot about pointers in C, but off the top of my head, I find these uses:

1) Passing arguments to a function by reference for modification. If we want a function to modify a variable v we send to it, we send the address &v of the variable, and the function then does *v = value. (This is not the same as pass by reference in C++ - that doesn't exist in C - but you can use the C way in C++.)

2) Referring to elements in arrays. If you know the base of the array, all you need is an index and no pointer, but if you operate with several arrays, or use auxiliary functions which do something with an element, it is much easier to use a single pointer than a base address and an index.

3) Allocated blocks of memory. A static array is declared as int a1[10], for example, but if you want a dynamically allocated block, you do a2 = malloc(SIZE*sizeof(int)), and what you have then is a pointer. This case includes all dynamic data structures.

4) Passing arguments to a function by reference because of speed. There may be a choice between copying a piece of data (a struct, for example), and passing just the address to it. Then the latter way is faster.

5) Passing arrays to functions as parameters. For example, passing a string, what you send to the function is the address of the first character of the string. Many functions return a pointer to a place within a string, for example 'strchr'.

6) Complicated data structures. Some data structures can be implemented by having one object include another, but often it's the case that they are potentially circular, and then they have to refer to each other indirectly. One way is by using an index into a common array, the Fortran way. Another way is by using pointers.

7) Function pointers have been mentioned, and they are indeed a case of pointers, but in that case there is no alternative - functions are always accessed by pointers. It may not look that way when you call f(a), but you can write (*f)(a) if you like, whether f is an actual function name, or a variable with a function pointer in it. The * is mostly used for clarity when a pointer variable is involved.

---

### Post by CptPicard on 2011-06-23
Conceptually the most important thing about a pointer is that it  is an "indirection variable"; it is a way to refer to something without actually "being" something. This important point is taken care of in many other languages by variables containing references to objects; therefore, pointers are not really as fundamental as some people would make them be; it is the underlying idea that they implement that is.

The ability to achieve recursion is the core of Turing-complete languages. You can do it in many ways, but code-data-dualism is an interesting point here; considering that you'll want to be computing in terms of either... but in the end you'll want to physicalise the recusion, which will require you to implement something (data) that does not require always repeating in whole everything that was one recursive step before, which would explode your memory requirement.

Of course, "on an infinite tape", in the theory sense this is not important so this is not a strictly theoretical explanation of why pointers are important... but I guess it gets close.

---

### Post by stchman on 2011-06-23
If you want to do any type of dynamic memory allocation (dynamic array sizing), then pointers are necessary.

If you wish to return more than one piece of data from a function, pointers are necessary.

I am sure there are others, but I am a Java guy (thank God for the garbage collector).

---

### Post by zobayer1 on 2011-06-23
> **stchman said:**
> If you want to do any type of dynamic memory allocation (dynamic array sizing), then pointers are necessary.

If you wish to return more than one piece of data from a function, pointers are necessary.

I am sure there are others, but I am a Java guy (thank God for the garbage collector).

Yeah, it would be nice if C/C++ had same thing... So that, we wouldn't need to write destructor explicitly .

---

### Post by _niai on 2011-06-25
> **stamatiou said:**
> And when do we use pointers as functions?
A pointer cannot be a function, it's just a pointer: a memory address. In C, the function's name is a pointer to the function itself, you use this pointer every time you call the function. If you mean to ask when you need to define/declare a pointer to a function, the answer would be, when you need to choose the function to be called depending on, say, the data value or type. For example, you have the following structure:
```
struct Student {
int number;
char* name;
int mark;
};
```And you have data for many many students. In one case you may need all the data sorted by name, in another - by mark, and yet another - by number. You can write the sorting function just once, if it takes as an argument a pointer to a comparing function.

If it still seems confusing, maybe it's because you don't need this yet. It's not complicated, but I remember I couldn't understand any of this before actually having to use a couple of these fellows (pointers to functions). It's easy to understand, when you actually see the use of it, not to worry.

---

### Post by slooksterpsv on 2011-06-25
```

#include <iostream>

using namespace std;

void changeIntVal(int& x, int newVal)
{
 x = newVal;
}

int main()
{
        int y = 10;
        cout << y << endl;
        changeIntVal(y, 5);
        cout << y << endl;
        return 0;
}

```

The only reason I post this is to illustrate a basic example of it's importance. The output is the following:

10
5

So we set y to 10, then used it in a function which changed its value due to it having the address of the variable.
I know the above example is C++, but still illustrates an example.

I would think, and I could be wrong on this, in things like game development, if you have large models you're loading into structures or that it'd be easier to use a pointer instead of copying the model (especially if it's huge) and modifying the data that way.

---

