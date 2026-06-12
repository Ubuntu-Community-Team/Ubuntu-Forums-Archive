---
title: "[C++] arrays without bounds?"
date: 2008-10-10
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-10
how would i declare an array in C++ without bounds?

---

### Post by mike_g on 2008-10-10
Maybe use a vector: [http://en.wikipedia.org/wiki/Vector_(STL](http://en.wikipedia.org/wiki/Vector_(STL))

---

### Post by wd5gnr on 2008-10-10
Well that kind of depends. As mike_g points out you can use a class library like STL to give you boundless arrays and other data structures.

A more organic answer is to revert back to old fashioned C programming and make the realization that the name of an array is a pointer. And therefore a pointer can be accessed as an array.

So 

int foo[32];
int *foop;
int x=10;

foop=foo;

foop[8]=x;


So you can do something like:

int *myarray=NULL;
int n;

// we decide we want to make 500 elements
n=500;  // note this could have been computed
myarray= new int[n];
// in theory if new failed it would throw an exception
// unless you use nothrow but I defensively will check
// for NULL. You might prefer ASSERT().
if (myarray==NULL) ; // error!

Unfortunately, I don't know a good way to grow the allocation using new. The usual scheme is to make a new bigger array, copy the old array to the new one, and then delete the old one. In C you have the "realloc" call (which you can use with C++) but even it probably will copy your data to a new location which could be slow.


So maybe:
int *myarray=NULL;
int *temp=NULL;
int n;

// we decide we want to make 500 elements
n=500;  // note this could have been computed
int n0;
myarray= new int[n];
// in theory if new failed it would throw an exception
// unless you use nothrow but I defensively will check
// for NULL. You might prefer ASSERT().
if (myarray==NULL) ; // error
// do some stuff....

// whoops we need 1000
n0=n;
n=1000;
temp=new int[n];
if (temp==NULL) ; // error
for (int i=0;i<n0;i++) temp[i]=myarray[i];
delete [] myarray;
myarray=temp;

---

### Post by jimi_hendrix on 2008-10-10
wow this is way harder then i expected :)

---

### Post by era86 on 2008-10-10
> **jimi_hendrix said:**
> wow this is way harder then i expected :)

Not really once you study a bit :KS

Just declare a pointer and voila!  You can allocate memory for any size of array later using a new or malloc call.  This WILL get messy though.

Use a vector if you can.

Goodluck:guitar:

---

### Post by snova on 2008-10-10
There really is no such thing as a resizeable array in C++, at least nothing built in.

The closest thing I can think of is using realloc(), but that will occasionally move things around to make room, so you have to be careful about copying the pointer.

---

### Post by dwhitney67 on 2008-10-10
> **jimi_hendrix said:**
> wow this is way harder then i expected :)

That is because you failed to read the advice from mike_g.
[php]
#include <vector>
#include <iostream>


// Multipurpose data displayer.
//
template< typename T >
void displayValue( T value )
{
  std::cout << value << std::endl;
}


// Main
//
int main()
{
  // Declare vector (glorified array if you will) to hold int values
  //
  std::vector< int > array;


  // add 5 numbers to the "array"
  //
  for ( size_t i = 0; i < 5; ++i )
  {
    array.push_back( i );
  }


  // heck... let's add two more values
  //
  array.push_back( 10 );
  array.push_back( 20 );


  // display the "array"; note the displayValue function must be
  // specialized; in other words told which type of data it will
  // be displaying.
  //
  std::for_each( array.begin(), array.end(), displayValue<int> );

  return 0;
}
[/php]

For more information on the STL vector and other STL containers, bookmark and reference this page:
[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

---

### Post by glok_twen on 2008-10-10
+1 on vectors, the stl is great that way. all kinds of built in support for algorithms like sorting, finding, etc, once the data is in a vector.

the maddening part for me in using them over the years has been that gdb does not at all easily let you examine their contents. (whether used through command line, kdgb, eclipse, emacs, etc). if anyone's solved this please share.

---

### Post by Sinkingships7 on 2008-10-10
> **snova said:**
> There really is no such thing as a resizeable array in C++, at least nothing built in.

The std::vector is fully re-sizable, as that's its purpose. Not only is it re-sizable, but I'm pretty sure it's dynamic as well, so it re-sizes automatically if its full when you use the append() method.

---

### Post by era86 on 2008-10-11
> **Sinkingships7 said:**
> The std::vector is fully re-sizable, as that's its purpose. Not only is it re-sizable, but I'm pretty sure it's dynamic as well, so it re-sizes automatically if its full when you use the append() method.

No built in arrays though that are re-sizeable...  The vector uses an array in its implementation, then reallocates as necessary.

---

### Post by NovaAesa on 2008-10-11
> **era86 said:**
> The vector uses an array in its implementation, then reallocates as necessary.

Are you sure? I'm fairly certain that it's implemented as a linked list.

EDIT: Nope, I was wrong. I guess I should have done my research first.
> Vector containers are implemented as dynamic arrays; Just as regular arrays, vector containers have their elements stored in contiguous storage locations, which means that their elements can be accessed not only using iterators but also using offsets on regular pointers to elements.

---

### Post by hod139 on 2008-10-11
I know vector's get all the love, but there are also double ended queues in the STL, [deque]("http://www.cplusplus.com/reference/stl/deque/"). There have a very similar interface to vectors, but some major differences.  With deques, you can insert into the front in constant time.  However, the elements are not guranteed to be contiguous, so reference (pointer) arithemetic access is not going to work.  But, as per the OP's question, it is a dynamic array.

---

### Post by cl333r on 2008-10-11
If you wanna go wild you could use linked lists :)

---

### Post by era86 on 2008-10-11
> **cl333r said:**
> If you wanna go wild you could use linked lists :)

:)
I believe there is a list data structure in C++, is there not?

---

### Post by jimi_hendrix on 2008-10-11
well i know in C# you can just say int i[] = new int[] and get a boundless array but i will try vectors

---

### Post by gomputor on 2008-10-11
*C++ Data Structures:*  [[COLOR="Red"]http://www.cppreference.com/wiki/stl/start[/COLOR]]("http://www.cppreference.com/wiki/stl/start")

---

### Post by dribeas on 2008-10-11
> **glok_twen said:**
> +1 on vectors, the stl is great that way. all kinds of built in support for algorithms like sorting, finding, etc, once the data is in a vector.

First thing: do use vectors, do use STL containers.
Now, just a side note. I have seen this kind of comment many times, and it is not really true you don't need your data to be in a vector to use the algorithms, not even in any STL container.

STL algorithms work on iterators, there are different 'types' of iterator (iterator concepts in C++0x terminology). Basically InputIterator, OutputIterator, ForwardIterator, Bidirectional and RandomAccessIterator (read your favorite book/online docs - I like [SGI STL]("http://www.sgi.com/tech/stl/Iterators.html")).

Each of the algorithm defines what type of iterator it requires for operation ([std::copy]("http://www.sgi.com/tech/stl/copy.html") requires two InputIterators and one OutputIterator, [std::sort]("http://www.sgi.com/tech/stl/sort.html") requires two RandomAccessIterator, ... again go to the docs).

What most people overlook is that pointers are iterators (RandomAccessIterators, which are the most flexible kind) so you can use algorithms from STL with raw pointers:

```

int array[100];
int sorted[100];
// Fill in array
std::copy( array, array+100, sorted );
std::sort( sorted, sorted+100 );
// Now sorted contains the same elements as array, in order

```

---

### Post by jimi_hendrix on 2008-10-11
ill just try the vectors...sounds simpliest (and having a bunch of pointers = headache because i dont fully understand their full potential yet :))

---

### Post by samjh on 2008-10-11
> **jimi_hendrix said:**
> ill just try the vectors...sounds simpliest (and having a bunch of pointers = headache because i dont fully understand their full potential yet :))

General rule of thumb: use what the language provides (vectors, in this case).  Only go beyond it if what is provided doesn't meet your requirements.

---

### Post by jimi_hendrix on 2008-10-11
ya...i would use another language that would be easier to code this in like python or lua but i want to learn C++ for game dev so why not practice?

also i like C++ string parsing...it just works for me

---

