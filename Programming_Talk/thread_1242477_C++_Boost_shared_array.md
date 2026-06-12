---
title: "C++ Boost shared_array"
date: 2009-08-17
forum: Programming Talk
---

### Post by legends2k on 2009-08-17
Hi,
I'm having a huge Java module with so many *new*s and not a single *delete* call (obviously). I'm trying to port it to C++. I've ported other library dependences I.e. wrote new ones for them. Now for the new-delete problem, I tried using Boost's smart pointer classes. I've a doubt in them. Say if I want something like

```
int **palette = new int* [5];
palette[0] = new int [3];
palette[1] = new int [5];
...
...
```

Will I be able to use boost::shared_array smart pointer class for the same? I.e. will I be able to use smart pointers for double pointers too? If yes, I'm unable to get the syntax right. The main thing is that, once I discard the whole palette, all the pointers, both the double and the single pointers should free memory without leaks.

P.S.:
I tried something like this to no avail.
```
boost::scoped_array<boost::scoped_ptr<int>*> doubleptr_smartptr(new boost::scoped_ptr<int>* [10]);
```

---

### Post by uljanow on 2009-08-17
Why not use STL containers instead of arrays ?

std::vector<int>* vec = new std::vector<int>();

---

### Post by legends2k on 2009-08-17
Thanks for the reply uljanow.

But using vector, or another STL container for that matter, we encounter 2 problems.
1. The code I have to port to C++ is in Java, so using containers, I lose the semantic closeness to using a pointer. Like I cannot do *ptr = 1; I need to use the member functions, which again is recoding the whole Java code.

2. If I use some container, what I get is a single dimensional list of integers, floats, etc. But if you see my question, what I need is muti-dimensional array, that too, variable length for each row. Probably, what you meant is, combining smart pointer and vectors like

boost::shared_array<std::vector> palette(new std::vector<int> 5);
palette[0].push_back(10);

It is feasible, but having double pointers in smart pointers, saves you lot of typing since you can use smart pointers with (almost) the same semantics of an ordinary pointer.

---

### Post by legends2k on 2009-08-17
Found the solution to this problem. It's to use shared_array of shared_arrays. Some good person in Boost mailing list helped me with this. I hope someone will benefit from the answer here, sometime later.

```
shared_array< shared_array<int> > palette (new shared_array<int>[5]);
palette[0].reset(new int[10]);
```

---

### Post by dribeas on 2009-08-17
If you are porting from Java to C++, the closest to references are in fact shared_ptr (and shared_array for arrays) rather than scoped_ptr (scoped_array respectively). The semantics of scoped_* are different from the semantics of Java references (you cannot share an object with scoped_* smart pointers). So the solution provided in the boost user list is better than your approach.

Now, if you did want to write the code with scoped pointers for any reason, the semantics for creation would be a little trickier but possible:

```

int main()
{
   // Just to reduce typing:
   typedef boost::scoped_array<int> int_array;
   typedef boost::scoped_array< int_array > int_array_array;

   // Create the outer array, with default constructed elements
   int_array_array array_of_array( new int_array[ 10 ] );

   // Populate the internal elements using scoped_array.reset (operator= is disabled)
   for ( int i = 0; i < 10; ++i )
   {
      array_of_array[i].reset( new int[ i*10 ] );
   }

   // Usage would be similar to Java:
   for ( int i = 0; i < 10; ++i ) {
      for ( int j = 0; j < i*10; ++j ) {
         array_of_array[i][j] = i+j;
      }
   }
}

```

---

