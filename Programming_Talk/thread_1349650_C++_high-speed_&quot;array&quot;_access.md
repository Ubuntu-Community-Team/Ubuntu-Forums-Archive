---
title: "C++: high-speed &quot;array&quot; access"
date: 2009-12-08
forum: Programming Talk
---

### Post by pianoman on 2009-12-08
Hallo people of the world,

I'm building a physical simulation program in C++ for a university project and one thing is proving rather difficult.

Basically, one of the big objectives is to model the system in real time. I started by simulating regular points on a surface as a perfectly normal C-style 2D array.

Now I've changed this: as i want to determine size at **runtime** (only once per run, no resizing required), I'm currently going with this line in my header:

```
typedef vector< vector<int> >    int_array;
```

(As someone who grew up on c99 which was fine with runtime sizing, this hurt.)

This has seriously slowed down the program unless I add -O3 to my compiler flags (g++ btw, if it helps). So I'm looking for a different storage types:

So far I've come across:
[LIST]
[*]Dynamic arrays - For more than one dimension, this seems to get very complex: pointers of pointers of pointers...
[*]Vectors - where half the people say its as efficient as C-style and the other half say its woeful. It has a lot of features of which i need nearly none.
[*]Valarrays - which no-one seems to talk about anymore. Why? 
[*]External libraries - [Boost]("http://www.boost.org/") is well known but has anybody heard of [Blitz++]("http://www.oonumerics.org/blitz/") before? Googling suggests the performance is impressive and almost FORTRAN-like.
[/LIST]

As I still need to add stuff to the program, slowing it further, are there any very fast-access array-like objects you guys and gals have used?

---

### Post by Can+~ on 2009-12-08
> **pianoman said:**
> Now I've changed this: as i want to determine size at **runtime** **(only once per run, no resizing required)**, I'm currently going with this line in my header:

And what's wrong with? (Or maybe I'm not getting how you're getting the size)

```
int* myarray = new int[size]
```

And you can achieve 2d establishing some access functions, like:

```
myarray[width*i + j]
```

Either as macros or functions.

---

### Post by ve4cib on 2009-12-08
If you don't need to resize anything dynamically and you need random access to every element (i.e. no searching like you would with a linked-list) then a normal array is probably your best bet.

You can either use a normal 2d array (where you deal with an array of pointers, each of those pointing to an array), or you can simulate a 2d array with a single 1-dimensional array:

```

int* myMatrix= (int*)malloc(sizeof(int * MAX_HEIGHT * MAX_WIDTH));
...

// get the element from myMatrix at row i, column j
int getElement(int i, int j) {
    int index = i*MAX_WIDTH + j;
    return myMatrix[index];
}

// get the row value from a 1-d index
int getRow(int index) {
    return index / MAX_WIDTH;
}

// get the column value from a 1-d index
int getCol(int index) {
    return index % MAX_WIDTH;
}

```

Obviously you could improve that by replacing the functions above with similar #define'd macros, but the general concept is the same.  You create a 1-dimensional array with MAX_HEIGHT * MAX_WIDTH elements, and index through it like a normal array.  You can transform from a 1-dimensional index to row/column values (and vice-versa) trivially.

And even if you do need to change the size of the matrix you can re-malloc the single array in one operation, and you just need to change the max height/width values for your transformation calculations.

Ideally I think you'd wrap the 1-d array in a class, along whatever data access/manipulation functions you need.


Another option (and this will be slower, but use less memory): if your data contains a large number of identical values (i.e. 99% of the points are zero, but 1% could be anything) you could create a Sparse Matrix.  Basically it's a 2-D linked list that stores only the non-zero (or non-redundant if the redundant value isn't zero) elements of the matrix.  You have to linearly search through to find an entry, but because you're only storing 1% of the values the search space is relatively small.


EDIT:
Curses!  I typed too slowly!

---

### Post by grayrainbow on 2009-12-08
You do know why source control system git was made, don't you?
With full optimization bare array access want be the problem, but more where it is access, and is it partially access, is all access align, etc.

Also, I guess you don't want GPGPU(multiple operation on floats at once could be lot faster then sequential operation on ints) but eventually you will want something from SSE family for floats, depending on processor you target, or hope on compiler to do it(msse family of flags on gcc for i386).
Also take a look on latest version of g++(4.5) it's supposed to be beta, but quite promising on optimization. Intel compiler is also known as good optimizer.

---

### Post by pianoman on 2009-12-08
Thanks guys, this could work.

The quirk lies in that my system employs periodic boundary conditions i.e. if my system array is 10 by 10 elements wide and a particle is bouncing along a row, it'll step on elements system[8][5], then system[9][5] and then flip to system[0][5]. The function I use to mediate this is called PBC and i call it like
```
system[ PBC((x+1), SIZE_X) ][ y ]
```

Since I use a lot of function calls in the system[x][y] style, is there a way of getting the compiler to accept this as system[width*y + x] without taking too big a speed hit? The speed is the MAJOR consideration here.

Is this what you meant by the #define thing, ve4cib? Or should i book in a 'trawling through code' day? :)

EDIT:
> **grayrainbow said:**
> You do know why source control system git was made, don't you?
Nope. Physicist first, computer geek second, I'm afraid. Would 'git' allow me to modify big chunks of code quicker?

---

### Post by Simian Man on 2009-12-08
> **pianoman said:**
> Since I use a lot of function calls in the system[x][y] style, is there a way of getting the compiler to accept this as system[width*y + x] without taking too big a speed hit? The speed is the MAJOR consideration here.

I'm not quite sure what you're asking here, but if you use 2D arrays, the compiler will automatically insert the multiplication and addition operations for you each time you index it.  Using 2D arrays is almost exactly the same as 1D arrays.  1D arrays are easier to allocate dynamically though.

I think your real speed issues will not involve indexing operations at all, they will involve cache accesses.  You need to make sure that, in the common case, your program exhibits as much spatial locality as you can because otherwise you will thrash the cache with a large enough data set - especially considering what you said about boundary conditions.

---

### Post by pianoman on 2009-12-08
> **Simian Man said:**
> ...if you use 2D arrays, the compiler will automatically insert the multiplication and addition operations for you each time you index it.  

So g++ will interpret system[x][y] as the same as system[size_x*x + y] even when declared in a single dimension? If so, the problem disappears!

> **Simian Man said:**
> I think your real speed issues will not involve indexing operations at all, they will involve cache accesses.  You need to make sure that, in the common case, your program exhibits as much spatial locality as you can because otherwise you will thrash the cache with a large enough data set - especially considering what you said about boundary conditions.

LOL, you may have overestimated my knowledge. I understood the bit about indexing operations, but everything about and after cache accesses is a bit of a blur. How can I optimise properties like locality?

(I should point out that I learned C++ from a physics perspective, something my computer science friends consider a travesty of education, so you can go ahead and make fun.)

---

### Post by Simon17 on 2009-12-08
If you know ahead of time how much memory you are going to need, you can just reserve() the space for the vectors and eliminate the array resizing and copying. This will give you the same benefit of using arrays without having to worry about memory.

---

### Post by grayrainbow on 2009-12-08
> **pianoman said:**
> Thanks guys, this could work.
Nope. Physicist first, computer geek second, I'm afraid. Would 'git' allow me to modify big chunks of code quicker?
We can talk about Schrodinger, or Heisenberg, but computer first :)
According to its creator git was designed becouse he didn't find anything useful, fast enough, etc. So if you want fast wrapper I'm afraid, you probably should write one yourself. But that depends on what "real time" you mean, all physics system I done are for games, where sometimes vectors are enough, and usually formulas on GPU or equivalent of SSE registers are more important + that about access, couse for fast processor memory access is extreamly costly.

---

### Post by Simian Man on 2009-12-08
> **pianoman said:**
> So g++ will interpret system[x][y] as the same as system[size_x*x + y] even when declared in a single dimension? If so, the problem disappears!
Oh no, sorry that wasn't what I meant.  I meant that when you do 2D arrays, the compiler will need to do one multiplication and one addition to index it which is what you will have to if you use a single dimension array in place of a 1D array.  I was just pointing out there's no noticeable spped difference between the two.  As others said, using a function or macro for the indexing is a good idea.

> **pianoman said:**
> LOL, you may have overestimated my knowledge. I understood the bit about indexing operations, but everything about and after cache accesses is a bit of a blur. How can I optimise properties like locality?
Well the most important point is that the way caches work is by assuming that you will often access memory locations that are close to each other.  If your program accesses a large array in order it will be *much* faster than if it accesses the array in random order because the cache will hold the elements you are about to access.

So for your 2D grid, you want to make sure that you are walking across it in order as much as possible.  For example, the following code:

```

#include <iostream>
#define N 10000

#define INDEX(i, j)((i) * N + (j))

int main( ) {
  int* arr = new int[N * N];
  int i, j;

  for(i = 0; i < N; i++)
    for(j = 0; j < N; j++)
      arr[INDEX(i, j)] = i * j;

  unsigned long int n = 0;

  for(i = 0; i < N; i++)
    for(j = 0; j < N; j++)
      n += arr[INDEX(i, j)];

  std::cout << n << "\n";

  return 0;
}
```

Runs in .740 seconds on my machine.  If we change the index macro to go by columns instead of by rows:

```
#define INDEX(i, j)((**j**) * N + (**i**))
```

Then the program runs in 9.694 seconds.  Which is 13 times as slow.  So these kinds of considerations are more important than the speed of std::vector vs. an array or 1D vs 2D arrays.

> **pianoman said:**
> (I should point out that I learned C++ from a physics perspective, something my computer science friends consider a travesty of education, so you can go ahead and make fun.)

Of course not, everyone starts out a beginner at programming.  Plus I know little about physics :).

---

### Post by ve4cib on 2009-12-08
> **pianoman said:**
> Since I use a lot of function calls in the system[x][y] style, is there a way of getting the compiler to accept this as system[width*y + x] without taking too big a speed hit? The speed is the MAJOR consideration here.

Is this what you meant by the #define thing, ve4cib? Or should i book in a 'trawling through code' day? :)

Yeah, pretty much.  In my earlier example I had

```

int getIndex(int i, int j) {
    return i * MAX_WIDTH + j;
}

```

Function calls are generally expensive.  You need to push things onto the memory stack, set jump return registers, etc, etc...  It can add up to a lot of clock-cycles.

A faster way of doing the same thing would be:

```

#define GET_INDEX(i,j) ((i) * (MAX_WIDTH) + (j))

```

*(All the extra parentheses are to force the expressions to evaluate properly -- this is a common, and very good practice when defining macro functions.)*

Now every time in your code when you would have called getIndex(i,j) you would instead call GET_INDEX(i,j).  The preprocessor will replace GET_INDEX(i,j) with the maths, eliminating any and all function calls, potentially speeding things up significantly.

To maximize the speed your best bet is probably to avoid using any C++ style classes and focus on a fairly primitive, old-school style of C programming.  Classes, with all their implicit pointer dereferencing, tend to be marginally slower than raw procedural code.  Classes are easier to maintain, and tend to be easier to write, but they tend to be slightly slower than the same program written without classes.  Or at least this was the case historically -- I don't know how true it is anymore.

---

### Post by TheStatsMan on 2009-12-08
> **pianoman said:**
> Hallo people of the world,

I'm building a physical simulation program in C++ for a university project and one thing is proving rather difficult.

Basically, one of the big objectives is to model the system in real time. I started by simulating regular points on a surface as a perfectly normal C-style 2D array.

Now I've changed this: as i want to determine size at **runtime** (only once per run, no resizing required), I'm currently going with this line in my header:

```
typedef vector< vector<int> >    int_array;
```(As someone who grew up on c99 which was fine with runtime sizing, this hurt.)

This has seriously slowed down the program unless I add -O3 to my compiler flags (g++ btw, if it helps). So I'm looking for a different storage types:

So far I've come across:
[LIST]
[*]Dynamic arrays - For more than one dimension, this seems to get very complex: pointers of pointers of pointers...
[*]Vectors - where half the people say its as efficient as C-style and the other half say its woeful. It has a lot of features of which i need nearly none.
[*]Valarrays - which no-one seems to talk about anymore. Why?
[*]External libraries - [Boost]("http://www.boost.org/") is well known but has anybody heard of [Blitz++]("http://www.oonumerics.org/blitz/") before? Googling suggests the performance is impressive and almost FORTRAN-like.
[/LIST]

As I still need to add stuff to the program, slowing it further, are there any very fast-access array-like objects you guys and gals have used?

When using template libraries, especially STL from what I understand you do have to optimise for speed. What is so bad about using -03 flag anyway.

Boost ublas prides itself on being good C++ code rather than being performance oriented.

Blitz++ uses expression templates to obtain speed. What that means is if you have vectors or matrices A,B, C and D, then you can write A=B+C+D and essentially get the same performance as hand coded C. Old school C++ you could also obtain the same level of abstraction, however for each addition a temporary matrix was required and as such the performance was poor.  I think that Blitz++ was the first C++ linear algebra library to use expression templates. There are other libraries now (eigen2.x) for example that also make use of expression templates to achieve very good performance. 

If you are just using the array to store data and do not need linear algebra operations then you do not need these libraries.

---

### Post by Habbit on 2009-12-08
If you just want a lean-mean 2D array wrapped into a class you can use with a simple syntax, look at [The C++ FAQ Lite 13.10-12]("http://www.parashift.com/c++-faq-lite/operator-overloading.html#faq-13.10"). It's not the main point of the page itself, but it gives good cues on creating a very simple and efficient Matrix class with compact storage (unlike your vector of vectors).

---

### Post by MadCow108 on 2009-12-09
> **pianoman said:**
> LOL, you may have overestimated my knowledge. I understood the bit about indexing operations, but everything about and after cache accesses is a bit of a blur. How can I optimise properties like locality?

this paper is a nice introduction on how the computer memory works and how one can optimize its use:
[http://people.redhat.com/drepper/cpumemory.pdf](http://people.redhat.com/drepper/cpumemory.pdf)
its partly probably a bit too detailed for practical application, but very informative.

just to make sure:
I hope you aren't copying these 2d vectors around but instead passing them by reference.
a function like:
func(int_array ar) will copy the whole thing when passed your matrix (very very slow)
whereas func(int_array & ar) will just pass a kind of pointer to the vector (fast)

---

