---
title: "vector.size() of a custom class."
date: 2010-09-29
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-09-29
I'm trying to initialize this function in cpp:

```
class coord {
    int x;
    int y;
public:
    coord(int a, int b);
};
coord::coord(int a, int b) {
    x = a;
    y = b;
}

void move(std::vector<coord> *vertex, int *map[21][12], char dir) {
    if (dir = 'D'){
            for (int i = vertex.size() ; i > 0; i--) {

            }
    }
}


```

get a compiler error

In function ‘void move(std::vector<coord, std::allocator<coord> >*, int* (*)[12], char)’:
error: request for member ‘size’ in ‘vertex’, which is of non-class type ‘std::vector<coord, std::allocator<coord> >*’|
||=== Build finished: 1 errors, 0 warnings ===|

---

### Post by NovaAesa on 2010-09-29
Think about what type of variable "vertex" is. Why would using *any* instance function on vertex be a bad idea?

---

### Post by YourMomsASmurph on 2010-09-29
> **NovaAesa said:**
> Think about what type of variable "vertex" is. Why would using *any* instance function on vertex be a bad idea?

Just thought of something -- could be wrong let me know.

vertex is a pointer to a piece of memory that holds a vector, thus it's not a vector itself.

So change *vertex to &vertex, which should work.

---

### Post by NovaAesa on 2010-09-29
Yes, you could do that and it would work fine. Another option would be to change vertex.size() to vertex->size(). This is shorthand for (*vertex).size().

EDIT: Which option is best really depends on what calling semantics you are after.

---

### Post by dwhitney67 on 2010-09-29
> **YourMomsASmurph said:**
> I'm trying to initialize this function in cpp:

```
class coord {
    int x;
    int y;
public:
    coord(int a, int b);
};
coord::coord(int a, int b) {
    x = a;
    y = b;
}

void move(std::vector<coord> *vertex, int *map[21][12], char dir) {
    if (dir = 'D'){
            for (int i = vertex.size() ; i > 0; i--) {

            }
    }
}


```

get a compiler error

In function &#8216;void move(std::vector<coord, std::allocator<coord> >*, int* (*)[12], char)&#8217;:
error: request for member &#8216;size&#8217; in &#8216;vertex&#8217;, which is of non-class type &#8216;std::vector<coord, std::allocator<coord> >*&#8217;|
||=== Build finished: 1 errors, 0 warnings ===|

Is that the real code, or something that you conjured up from memory?

Error here:
```

if (dir = 'D'){    // assignment?

```

Error here:
```

for (int i = vertex.size()   // vertex is a pointer

```

Warning here:
```

for (int i = vertex.size()...   // size() returns type of size_t

```

Now the following begs to be asked... why are you passing pointers around?  Just pass by reference.

And why is 'move(...)' not part of a class?

---

### Post by YourMomsASmurph on 2010-09-29
> **dwhitney67 said:**
> Is that the real code, or something that you conjured up from memory?



Came up with it from memory, the code is... huge right now, so just tried to remember the parts that were important.

> **dwhitney67 said:**
> Is that the real code, or something that you conjured up from memory?
Error here:
```

if (dir = 'D'){    // assignment?

```Error here:
```

for (int i = vertex.size()   // vertex is a pointer

```Warning here:
```

for (int i = vertex.size()...   // size() returns type of size_t

```Now the following begs to be asked... why are you passing pointers around?  Just pass by reference.

And why is 'move(...)' not part of a class?

Brain wasn't working -- Thought I was passing by reference for what ever reason.
It wasn't until NovaAesa made me look at the code that I realized what I was doing was completely wrong.

//Making a "Falling block game" brains slightly lost as to how to organize it properly (Which is why move is not part of a class yet). 
I'm just creating all the functions I am going to need. Write each one separately, then put together and edit at the end.
(Only really have 1 semester of programming courses[trying to self teach], BUT need to have a few games programmed by this summer to get a chance at a specific internship.)

---

### Post by nvteighen on 2010-09-30
By the way, I'm pretty sure you also don't need your **map** parameter to be an array of 2D arrays (int *map[12][12])... Pass the 2D array, unless you want to modify the 2D array's memory address (which I really doubt: I guess you want to modify its contents). But maybe, your map should be a class or maybe there is a STL container for that (I'm not a C++ programmer)... C-like arrays are impractical in C++ because C++ has better higher-level constructs for you (C has to cope with that kind of arrays because of what tasks the language is meant to be used for... but you're *not* programming in C!).

---

