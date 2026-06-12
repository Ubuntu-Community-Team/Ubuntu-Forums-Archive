---
title: "Bit of a starter with C++ Programming"
date: 2009-05-29
forum: Programming Talk
---

### Post by PaulM1985 on 2009-05-29
Hi

I have been trying to convert some Java code I have written into C++ but I have been having trouble.

The book I have bought has turned out to be pretty useless as it doesn't mention headers, no info on how to create classes that link together unless I want to write my whole program as one massive file and virtually nothing of any use on arrays.

I have posted my code below, which won't compile.  Some of the things in there are just basic concepts that I probably don't know about.

Code is supposed to have:
A constructor called Face that takes in an array of ints (which are 3d points), and an int which is the number of points in the array called no_of_corners.  It populates an array belonging to the class with the points and sets the class variable number_of_corners to no_of_corners.

A function get_number_of_corners, which takes no arguments and returns the number of corners.

A function get_corners, which returns the array of corners.

I have copied my code below:
Face.h:
```

#ifndef FACE_H
#define FACE_H

class Face
{
 public:
  const static int X = 0;
  const static int Y = 1;
  const static int Z = 2;

  Face(int a_corners[][3], int no_of_corners);

  int get_corners(void)[][3];

  int get_number_of_corners(void);

 private:
  int corners[][3];
  int number_of_corners;
};

#endif

```

Face.cpp
```

#include "Face.h"

Face::Face(int a_corners[no_of_corners][3], int no_of_corners)
{
  number_of_corners = no_of_corners;

  corners = new int[number_of_corners][3];

  for (int i = 0; i < number_of_corners; i++)
    {
      corners[i][X] = a_corners[i][X];
      corners[i][Y] = a_corners[i][Y];
      corners[i][Z] = a_corners[i][Z];
    }
}

int Face::get_corners(void)[][3]
{
  return corners;
}

int Face::get_number_of_corners(void)
{
  return number_of_corners;
}

```

Any help on where I am going wrong, or general points in the right direction would be a great help.

Paul

---

### Post by NielsBhor on 2009-05-29
Where's your main.cpp?

---

### Post by matja on 2009-05-29
Hi Paul,

Is there any reason why you can't use a std::vector instead of an array? I think this would solve most, if not all, of the compilation errors, be easier and a more "C++ way of doing it".

If there is a reason for using arrays, it can of course be solved that way too and we can get back to that.

Regards,
Mattias

---

### Post by MadCow108 on 2009-05-29
Although it is important to understand the concept of array's you should also familiaries yourself with vectors and the other STL features.
[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)
The make the work alot easier and less error prone.

In your code are numerous errors:
int get_corners(void)[][3];
should probably be:
int ** get_corners(void);

a two dimensional array in simple c is nothing else as a pointer to another pointer, hence int **

similary this won't work:
corners = new int[number_of_corners][3];
you need to do this:
// create array of pointers to integers
corners = new int*[number_of_corners];
// allocate space for three ints and set the pointer to point to the other pointer
for (int i=0;i<3;i++) corners[i] = new int[3];

I'm not too familiar with the [][] syntax so i only got it to work if you replace the int var[][] with int ** var everywhere. It probably also works with [][] somehow but I don't know how.

Generally you should avoid pointers whenever possible in c++
you can still pass by reference with the & character:
function(type & variable)

---

### Post by PaulM1985 on 2009-05-29
Hi

NielsBhor: This is quite a small cog in a fairly large wheel, it is just that the basic concepts of 2d arrays are the basis of what I am working with.  

It looks like I need to use a pointer to a pointer?  (Please confirm... anyone.) when it comes to passing two dimensional arrays into a function.

And the same for returning from a function? .....

matja:  I will look at vectors.  Each point is a vector and I need an adaptable collection of them.  In the same way that I would use ArrayList in Java.  Each point is a corner, so sometimes I may want a square, others I may want a hexagon, for example. eg array of 4 or 5.

If anyone could confirm the above, or add addtional comments, it would be appreciated.

Thanks again

Paul

---

### Post by MadCow108 on 2009-05-29
yes a multidimensional vector can be implemented as an array of pointer to an array of values (which in c are again pointers to the first element)
e.g.
int ** array would be a pointer to a pointer pointing to an int.
you allocate the memory for this array with:
int ** array = new int*[size];
now you have an array of pointers pointing to a pointing to an integer
array.
now you have to make room for the second dimension. For this you have to loop over the array of pointers and let the pointers point to an array if integers:
for (int i=0;i<size2;i++) test[i] = new int[size2];
access to the values goes with: array[i][j];

To pass this around youll have to pass the base pointer array of type int**

Very important: to delete you have to loop over the lowest dimesions and call delete [] array[i] to delete everything and not just the pointer.
If the pointer goes out of scope or gets deleted you lose the possiblity of deleting the data the pointer was pointing to, a so called memory leak.
Also you have to be very careful not to access past the array boundaries.


Another maybe simpler way would be this:
int * array = new int[size1*size2];
access with: array[i+size1*j];


It is strongly recommended to use vectors instead of arrays.
Vectors are containers that handle all the tedious tasks involved with arrays, e.g. allocating memory, resizing, copying and most important boundary checking and deleting.
The are handled exactly like arrays just easier.

There are loads of tutorials for this found by google.
Just see that you find a C++ tutorial and not a C one if you want to learn C++.

---

### Post by PaulM1985 on 2009-05-30
Ok, I think I am almost there.  I am just getting one compiler error:

Face.cpp: In constructor &#8216;Face::Face(int**, int)&#8217;:
Face.cpp:7: error: invalid conversion from &#8216;int**&#8217; to &#8216;int&#8217;

Code now is..

Face.h
```

#ifndef FACE_H
#define FACE_H

class Face
{
 public:
  const static int X = 0;
  const static int Y = 1;
  const static int Z = 2;

  Face(int **a_corners, int no_of_corners);

  int** get_corners(void);

  int get_number_of_corners(void);

 private:
  int **corners;
  int number_of_corners;
};

#endif
```

Face.cpp
```

#include "Face.h"

Face::Face(int **a_corners, int no_of_corners)
{
  number_of_corners = no_of_corners;

  **corners = new int*[3];

  for (int i = 0; i < 3; i++)
    corners[i] = new int[number_of_corners];

  for (int i = 0; i < number_of_corners; i++)
    {
      corners[X][i] = a_corners[X][i];
      corners[Y][i] = a_corners[Y][i];
      corners[Z][i] = a_corners[Z][i];
    }
}

int** Face::get_corners(void)
{
  return corners;
}

int Face::get_number_of_corners(void)
{
  return number_of_corners;
}

```

I can't see what is wrong.  The declaration in the header looks the same as in the c++ file... ??

Paul

---

### Post by Linteg on 2009-05-30
Well, line 7 is a bit weird isn't it?
```
**corners = new int*[3];
```
corners is an int**, but **corners is an int (in fact, the value of corners[0][0])
Try:
```
corners = new int*[3];
```

---

### Post by PaulM1985 on 2009-05-30
Yay, thats worked.

Thanks everyone for all your input and help.

Paul

---

### Post by Linteg on 2009-05-30
Just don't forget to write a destructor for your class, else it will happily be leaking memory.

---

### Post by matja on 2009-05-30
Hi again,

I noted some other things that you may or may not want to take a look at. First of, you flipped the order of the array so you have an array of three arrays containing the x, y, and z-coordinates, respectively, instead of an array of corners. You could get your old representation back with
```

corners = new int*[number_of_corners];
for(int i = 0; i < number_of_corners; ++i) {
   corners[i] = new int[3];
   corners[i][X] = a_corners[i][X];
   corners[i][Y] = a_corners[i][Y];
   corners[i][Z] = a_corners[i][Z];
}

```

Secondly, you most likely need a destructor to free the memory allocated for corners once an instance of your class is destroyed. A quick Google search gave
[http://www.cprogramming.com/tutorial/constructor_destructor_ordering.html]("http://www.cprogramming.com/tutorial/constructor_destructor_ordering.html").
An explicit constructor is needed when you use new to allocate memory for a class' members. This would by the way be avoided with a std::vector.

Thirdly, the get_corners() function returns a pointer to the actual member corners, which means that outside code are free to modify it as they please, even delete it if they so wish. If this is intentional, corners could just be declared public and the get_corners() method removed. You could also return a copy of corners, but then the function would have to return a pointer to a newly allocated array that eventually has to be deleted by the caller. Another option is to have the caller pass an array to the function that corners is copied to.

Finally, the get_number_of_corners() function should be declared const so it can be used on const Face objects.
[http://en.wikipedia.org/wiki/Const_correctness#Methods]("http://en.wikipedia.org/wiki/Const_correctness#Methods")
If the get_corners() is changed to return a copy of the corners member, it should be declared const too.

I hope this helps!

/Mattias

---

### Post by PaulM1985 on 2009-05-30
Hi matja

I have never written a destructor before so I will have a look at what is involved with one.

I had intended in returning a copy rather than the actual collection of corners, but at the time I got carried away with getting it to compile. I will make a note to remember to do that.

Thanks for the suggestion with declaring them const.  I have heard of this with functions in c++ but I don't know what it is, so I will have a look and try and sort it out.

Thanks for the help.

Paul

---

