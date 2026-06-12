---
title: "[SOLVED] C++ Variable Help"
date: 2008-12-01
forum: Programming Talk
---

### Post by djbushido on 2008-12-01
Ok, this is going to be hard to explain. I am trying to use a variable without knowing its exact name, like Variable1, where the "1" is a seperate piece of data, and the program knows to use "variable" like:
```
for(i,i<10,i++)
{[INDENT]int variable(i);[/INDENT]
}
```
My for loop is probably off, but i think that it is enough to get the idea. I understand that this is hard to explain, so will be more than happy to try and refine this, and any help would be greatly appreciated. Thank you!

---

### Post by Nemooo on 2008-12-01
Don't you think an array would suit your purpose?

```
int variable[10]

for(i = 0; i < 10; i++)
    variable[i] = something
```

---

### Post by Nemooo on 2008-12-01
Am I stupid or is there no way to delete a post?

---

### Post by hessiess on 2008-12-01
Using an array or a linked list is a much beater option. If you have to create vairiables like that then you are probabily going about it in the wrong way.

---

### Post by djbushido on 2008-12-01
an array is probably a good idea, but the problem is that i won't always know how big to make the array. Is using int i[]; legal? So that the array is automatically sized to the last value?

---

### Post by namegame on 2008-12-01
> **hessiess said:**
> Using an array or a linked list is a much beater option. If you have to create vairiables like that then you are probabily going about it in the wrong way.

A linked list may be a bit too complicated given the needs of the OP. I think an array would be a better investment of time/effort. Although, if the OP doesn't know about linked lists, I highly suggest learning about them. They are extremely useful in some applications.

---

### Post by namegame on 2008-12-01
> **djbushido said:**
> an array is probably a good idea, but the problem is that i won't always know how big to make the array. Is using int i[]; legal? So that the array is automatically sized to the last value?

Dynamically allocate the memory for the array. Although if it is getting this complicated a linked list may be better.

---

### Post by dwhitney67 on 2008-12-01
Use the STL vector.

[php]
#include <vector>
#include <iostream>
#include <algorithm>

template <typename T>
void doSomething(const T& value)
{
  std::cout << "value = " << value << std::endl;
}

int main()
{
  // declare a vector that will hold int values
  std::vector<int> values;

  // add values to the vector
  values.push_back(10);
  values.push_back(20);
  values.push_back(30);

  // print size of the vector
  std::cout << "size of values = " << values.size() << std::endl;

  // do something with values
  std::for_each(values.begin(), values.end(), doSomething<int>);

  return 0;
}
[/php]

---

### Post by dribeas on 2008-12-01
> **dwhitney67 said:**
> Use the STL vector.


+1, it takes care of automated memory allocation and dellocation and has the same advantages as a handmade array on the other side: memory is allocated contiguously and it provides access to elements throught operator[]. Remember that you must resize the vector to the required size before accessing the elements.

---

### Post by jimi_hendrix on 2008-12-01
<GEEK_OCD>
can we quit it with the no {} around the for loops...just bad practice
</GEEK_OCD>

yes i know thats not standard xhtml...

+1 for vecots
+1 for arrays
-1 for linked lists....probably too complex for this use

---

### Post by djbushido on 2008-12-01
Ok, so i'm kind of getting confused with this, so i'll ask the previous question simply:

will ```
int i[];
``` dynamically allocate memory such that i can ignore the size of the array, and just do like ```
i[5689]=7
```
Understanding that this is probably horrible style, just intended to work.

---

### Post by jimi_hendrix on 2008-12-01
no...you need vectors or to learn new/delete...i advise vectors

---

### Post by dribeas on 2008-12-02
> **jimi_hendrix said:**
> no...you need vectors or to learn new/delete...i advise vectors

And even using vectors, you must reserve() enough capacity for the size you have (unless you go adding one element at a time at the end with push_back().

---

### Post by djbushido on 2008-12-03
so is there a way to dynamically allocate memory for an array, such that just writing a position in an array and a value to set it to is legal? or if not, how would i go about creating something like described in my first post? Sorry I'm probably not of much help, but feel like I'm not really getting anywhere other than confused...

---

### Post by dwhitney67 on 2008-12-03
Here are two equivalent ways to access an array.  Most people prefer to use the square-brackets [] because it makes code easier to read.
[php]
#include <cassert>

int main()
{
  const int someSize = 5;

  int* array1 = new int[someSize];
  int* array2 = new int[someSize];

  for (int i = 0; i < 5; ++i)
  {
    array1[i] = (i+1);
  }

  // or

  for (int i = 0; i < 5; ++i)
  {
    *(array2+i) = (i+1);
  }

  for (int i = 0; i < 5; ++i)
  {
    assert(array1[i] == *(array2+i));
  }

  delete [] array1;
  delete [] array2;

  return 0;
}

[/php]

---

### Post by scourge on 2008-12-03
> **namegame said:**
> A linked list may be a bit too complicated given the needs of the OP. I think an array would be a better investment of time/effort. Although, if the OP doesn't know about linked lists, I highly suggest learning about them. They are extremely useful in some applications.

Using std::list (a doubly-linked list) is just as easy as using a vector. Linked lists in C can be a chore though.

---

### Post by djbushido on 2008-12-03
So apparently the conversation seems to be leaning toward linked lists. Where can i learn about this, or other helpful info?

---

### Post by Zugzwang on 2008-12-03
> **djbushido said:**
> so is there a way to dynamically allocate memory for an array, such that just writing a position in an array and a value to set it to is legal? or if not, how would i go about creating something like described in my first post? Sorry I'm probably not of much help, but feel like I'm not really getting anywhere other than confused...

Arrays have a fixed size, that's part of the definition. If you want PHP-style auto-sizing arrays, you might want to use maps. So dwhitney's example (shortened) would be:
[PHP]
#include <map>
#include <iostream>
#include <algorithm>

int main()
{
  // declare a vector that will hold int values
  std::map<int,int> values;

  // add values to the vector
  values.insert(1,10);
  values.insert(55,20);
  values.insert(1234567,30);

  // print size of the map
  std::cout << "size of values = " << values.size() << std::endl;

  // do something with values
  std::cout << "Content of values(55):" << values[55] << "\n";

  return 0;
}  
[/PHP]

---

### Post by namegame on 2008-12-03
> **scourge said:**
> Using std::list (a doubly-linked list) is just as easy as using a vector. Linked lists in C can be a chore though.

Forgive me, I have recently been enlightened to the fact that I'm a bit of a blub-programmer. Currently, I'm only capable of thinking in C, as it's the only language I "know" extensively.

I didn't even know about std::list, although I'm currently trying to work in C++. I'll have to look into it.

---

### Post by dwhitney67 on 2008-12-03
The Standard Template Library (STL) vector is the container that most closely models an array.  In fact, I like to think of it as a "glorified" array.

The vector provides the means to insert (push_back) values, retrieve them using the square-brackets as is done with regular arrays, and provides the interface to iterate over the entire data set.

An STL map, although useful in many applications, is overkill when all that is needed is an array.

For more information on vectors, maps, and the rest of the STL, click on this [link]("http://www.cplusplus.com/reference/stl/").

---

### Post by Kazade on 2008-12-03
> **dribeas said:**
> And even using vectors, you must reserve() enough capacity for the size you have (unless you go adding one element at a time at the end with push_back().


Wrong. With vectors you must "resize()". reserve() is solely for efficiency (it allocates memory so that it doesn't have to repeatedly reallocated when pushing back a large number of items). reserve() doesn't change the size of the vector, resize() does.

Basically, if you did this:

vector<int> myvec(1); //Initialize to 1
myvec.reserve(10);
myvec[8] = 1; //<< THIS IS BROKEN
myvec.size(); //<< reports 1

instead this is what you should do:

vector<int> myvec(1); //Initialize to 1
myvec.resize(10);
myvec[8] = 1; //<< This is now correct
myvec.size(); //<< reports 10

You either need to use (reserve() AND push_back()) or resize().

---

### Post by dribeas on 2008-12-03
> **scourge said:**
> Using std::list (a doubly-linked list) is just as easy as using a vector. Linked lists in C can be a chore though.

The question asks explicitly about using square brackets to access information. In std::list operator[] is not implemented, and as it is a sequential access container, it would be inefficient if random access is required.

If you want to store data in a container you should first of all decide what your usage pattern looks like. Unless you need a lot of insertions or deletions at the start or in the middle of the container std::vector is a safe bet.

The ease of use is exactly the same in both containers for the shared operations.

---

### Post by djbushido on 2008-12-03
Okay, I think I'm going to use vectors for now. So a basic example would be:
```

vector<int> vector1(1); //Initializes vector of size 1 (2 holding spots-0 and 1) and can hold "int" types
vector1.resize(10); //Resizes vector to size 10 (11 values) and can hold "int"
vector1[8]=19; //Puts the value "19" in the 8th position of vector1
vector1.size(); //Returns the size, which is 10

```
Is this correct?

---

### Post by dwhitney67 on 2008-12-03
A resize() will set the number of locations that are accessible.  Using a size of 10 will permit you to access locations 0 thru 9.

Your example code is pretty much spot on for basic examples.  If you have not already done so, please book-mark the following link to obtain more information and examples of the various STL containers:
[http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)

---

### Post by djbushido on 2008-12-04
Thank you for that, i was about to be really confused...I took VB as a class and that was legal. Also thank you for the link, now marking this solved.

---

