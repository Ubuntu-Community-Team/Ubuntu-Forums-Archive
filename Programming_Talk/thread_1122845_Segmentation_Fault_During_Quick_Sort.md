---
title: "Segmentation Fault During Quick Sort"
date: 2009-04-11
forum: Programming Talk
---

### Post by eerraayyss on 2009-04-11
Hi everyone;

I really need help in my quick sort program. It gives a silly segmentation fault,but only for some special conditions. My program generates random integer,float,double and string arrays with given size then sorts these arrays with my own quick sort function. Later I will use openMP to make my program multi-threaded and give outputs as txt and html files,but i will make these later,you can skip these in my code

My program works great for integers for any size(even for 100 million integers). But it crashes for floats,doubles and strings with sizes 200000 or more and gives segmentation fault. For less sizes these wont give error,too. I really couldnt find anything.

My GDB debug result and stack trace:

[New Thread 0xb7d646e0 (LWP 10297)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7d646e0 (LWP 10297)]
0xb7dd8130 in _IO_file_write () from /lib/libc.so.6
(gdb) bt
#0  0xb7dd8130 in _IO_file_write () from /lib/libc.so.6
#1  0xb7dd7de3 in ?? () from /lib/libc.so.6
#2  0xb7dd80e6 in _IO_do_write () from /lib/libc.so.6
#3  0xb7dd8cb0 in _IO_file_overflow () from /lib/libc.so.6
#4  0xb7dd7f1d in _IO_file_xsputn () from /lib/libc.so.6
#5  0xb7dae671 in vfprintf () from /lib/libc.so.6
#6  0xb7db7e80 in printf () from /lib/libc.so.6
#7  0x08048826 in qzsort_internal ()
#8  0x08048853 in qzsort_internal ()
#9  0x08048853 in qzsort_internal ()
#10 0x08048853 in qzsort_internal ()
#11 0x08048853 in qzsort_internal ()
#12 0x08048853 in qzsort_internal ()
#13 0x08048853 in qzsort_internal ()
#14 0x08048853 in qzsort_internal ()
#15 0x08048853 in qzsort_internal ()
#16 0x08048853 in qzsort_internal ()
#17 0x08048853 in qzsort_internal ()
#18 0x08048853 in qzsort_internal ()
#19 0x08048853 in qzsort_internal ()
#20 0x08048853 in qzsort_internal ()
#21 0x08048853 in qzsort_internal ()
#22 0x08048853 in qzsort_internal ()


My qsort function= qsort.c

```

#include <stdio.h>

#include <string.h>
#include <stdlib.h>

#include <omp.h>
#include "qsort.h"



int zk=0;
int depth=0;

static void swap_internal(char *a, char *b, size_t size)

{

  if (a != b)

  {

    char t;

    while (size--)

    {

      t = *a;

      *a++ = *b;

      *b++ = t;

    }

  }

}

static void qzsort_internal(char *begin, char *end, size_t size, int(*compar)(const void *, const void *))

{

  if (end > begin)
  {
    	

    char *pivot = begin;

    char *l = begin + size, *r = end;

 

    while (l < r)

    {

      if (compar(l, pivot) <= 0)

      {

        l += size;

      }

      else

      {

        r -= size;

        swap_internal(l, r, size);

      }

    }

    l -= size;

    swap_internal(begin, l, size);
	/*printf("recursive %d - begin %d - end %d - l %d - r %d - size %d \n",zk,begin,end,l,r,size);*/
	zk++;
	qzsort_internal(begin, l, size, compar);
	qzsort_internal(r, end, size, compar);

 }

}

 

void omp_qsort(void *base, size_t nmemb, size_t size, int(*compar)(const void *, const void *))

{

  qzsort_internal((char *)base, (char *)base+nmemb*size, size, compar);

  /* to build a multithreaded structure we need begin and end points of array for sorting in function parameters,

       therefore i'm using an internal function which has begin and end points as parameters.*/
  depth=0;	

}


```


My main file: project1.c

```

#include <stdio.h>

#include <string.h>
#include <stdlib.h>

#include <omp.h>
#include "qsort.h"


extern depth;


void rand_str(char *dst, int size)

{

   static const char text[] = "abcdefghijklmnopqrstuvwxyz"

                              "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

   int i, len = rand() % (size - 1);

   for ( i = 0; i < len; ++i )

   {

      dst[i] = text[rand() % (sizeof text - 1)];

   }

   dst[i] = '\0';

   //return dst;

}





int compare_int (const void * a, const void * b)

{

    /* integer comparison */

    const int *ia = (const int *)a; 

    const int *ib = (const int *)b;

    return *ia  - *ib; 

}

int compare_float (const void * a, const void * b)

{

    /* float comparison */

    if( ( *(float*)a - *(float*)b ) < 0) return -1;

}

int compare_double (const void * a, const void * b)

{

    /* double comparison */

    if( ( *(double*)a - *(double*)b ) < 0) return -1; 

}



int cstring_cmp(const void *a, const void *b)

{

    const char **ia = (const char **)a;

    const char **ib = (const char **)b;

    return strcmp(*ia, *ib);

	/* strcmp functions works exactly as expected from

	comparison function */

}




int main ()

{

   	

	double time1,time2;
	double *time;

	int i;

	int *a;

	int stringsize=3;

	int arraysize;
	int counter=0;

	

	char **b;
	float *c;
	double *d;
	int counter2=0;
        arraysize=500000;
	d=(double*)malloc(sizeof(double)*arraysize);

	for(i=0;i<arraysize;i++){

		d[i]=arraysize * (rand() / ((double) RAND_MAX));

	}
	fprintf(op,"\n**** Double ****\n");
	for(i=0;i<arraysize;i++){
	    fprintf(op,"%lf ",d[i]);	
	}	


	printf("Start * double Array Size = %d Thread Say&#305;s&#305; = %d \n",arraysize,omp_get_max_threads());	
	omp_qsort(d,arraysize,sizeof(double),compare_double);
	printf("Finish * double Array Size = %d \n\n",arraysize);


	fprintf(op,"\n**** Double - Sorted ****\n");
	for(i=0;i<arraysize;i++){
	    fprintf(op,"%lf ",d[i]);	
	}
	free(d);

return 0;

}


```


There may be some unused variables you can skip these. My program works great for integers therefore I think there must be something wrong with my qzsort_internal in qsort.c where I use pointers a lot,but they all seem to be correct. I'm really in a very difficult situation. Thanks for any help

---

### Post by eerraayyss on 2009-04-11
any idea?

it would be great,if someone at least tell me more about GDB error message and stack trace.


My GDB debug result and stack trace:

[New Thread 0xb7d646e0 (LWP 10297)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7d646e0 (LWP 10297)]
0xb7dd8130 in _IO_file_write () from /lib/libc.so.6
(gdb) bt
#0 0xb7dd8130 in _IO_file_write () from /lib/libc.so.6
#1 0xb7dd7de3 in ?? () from /lib/libc.so.6
#2 0xb7dd80e6 in _IO_do_write () from /lib/libc.so.6
#3 0xb7dd8cb0 in _IO_file_overflow () from /lib/libc.so.6
#4 0xb7dd7f1d in _IO_file_xsputn () from /lib/libc.so.6
#5 0xb7dae671 in vfprintf () from /lib/libc.so.6
#6 0xb7db7e80 in printf () from /lib/libc.so.6

---

### Post by Arndt on 2009-04-11
> **eerraayyss said:**
> 




There may be some unused variables you can skip these. My program works great for integers therefore I think there must be something wrong with my qzsort_internal in qsort.c where I use pointers a lot,but they all seem to be correct. I'm really in a very difficult situation. Thanks for any help

What does this function return when it doesn't return -1?

```

int compare_double (const void * a, const void * b)

{

    /* double comparison */

    if( ( *(double*)a - *(double*)b ) < 0) return -1; 

}

```

---

### Post by eerraayyss on 2009-04-11
doesn't that automatically return something positive when ( *(double*)a - *(double*)b ) is bigger than zero?

Because my program works great for integers which has a different type compare function,you may be right,however I think that would cause a false sorting, not a segmentation fault which is probably about a pointer error? But thanks for your idea,I am trying it right now and will post the result later.

---

### Post by eerraayyss on 2009-04-11
thanks Arndt,it fixed my problem with floats and doubles. But what about strings? For string sorting I get segmentation fault,too? Do you have any idea about it? It may be my string compare function or my calling of double pointer to char in my qsort or string allocation with double char pointer, because I'm not sure about these. When I debug string example through GDB,I get:


Program received signal SIGSEGV, Segmentation fault.
0xb7f76da6 in ?? () from /lib/libc.so.6
(gdb) bt
#0  0xb7f76da6 in ?? () from /lib/libc.so.6
#1  0xb7f770e6 in _IO_do_write () from /lib/libc.so.6
#2  0xb7f77cb0 in _IO_file_overflow () from /lib/libc.so.6
#3  0xb7f76f1d in _IO_file_xsputn () from /lib/libc.so.6
#4  0xb7f4d671 in vfprintf () from /lib/libc.so.6
#5  0xb7f56e80 in printf () from /lib/libc.so.6
#6  0x0804872e in qzsort_internal (
    begin=0xb7d87008 "&#65533;\237\025\bX\210c\bH\210c\b8&#65533;\004\bH&#65533;\004\b\030\210c\bh&#65533;\004\b\b\210c\b&#65533;\207c\b\230&#65533;\004\b&#65533;&#65533;\004\b&#65533;&#65533;\004\b&#560;\004\b&#1584;\004\b&#65533;\207c\b&#65533;\210c\b\b&#65533;\004\b\030&#65533;\004\b(&#65533;\004\b\210\207c\bx\207c\bX&#65533;\004\bh&#65533;\004\bx&#65533;\004\bX\207c\bH\207c\b8\207c\b\030\207c\b&#65533;\206c\b&#1585;\004\b&#65533;\206c\b&#65533;&#65533;\004\b\230\206c\bx\206c\b8\206c\b8&#65533;\004\b&#65533;\205c\bX&#65533;\004\bh&#65533;\004\b&#65533;\205c\b&#65533;\205c\b&#65533;\205c\b\210\205c\bh\205c\bX\205c\bH\205c\b(\205c\b&#65533;\204c\b\b&#65533;\004\b&#65533;\204c\b"..., 
    end=0xb7dcac04 "&#552;S\b\030&#65533;\025\b(&#65533;\025\b&#65533;&#65533;S\bH&#65533;\025\b&#65533;&#65533;S\b\230&#65533;S\b\210&#65533;S\bx&#65533;S\b\230&#65533;\025\bh&#65533;S\bX&#65533;S\bH&#65533;S\b&#1568;\025\b8&#65533;S\b\030&#65533;S\b&#65533;&#65533;S\b\030&#65533;\025\b&#1575;S\b8&#65533;\025\b\230&#65533;S\bX&#65533;S\bh&#65533;\025\bx&#65533;\025\bH&#65533;S\b\230&#65533;\025\b&#65533;&#65533;\025\b&#65533;&#65533;\025\b8&#65533;S\b&#1569;\025\b&#65533;&#65533;\025\b&#65533;&#65533;\025\b\b&#65533;\025\b(&#65533;S\b\030&#65533;S\b8&#65533;\025\bH&#65533;\025\b&#65533;&#65533;S\b&#65533;&#65533;S\bx&#65533;\025\b\210&#65533;\025\b\210&#65533;e\b&#65533;&#65533;\025\b&#1574;S\b&#550;S\b&#65533;&#65533;S\b\230&#65533;S\b&#65533;&#65533;\025\b\210&#65533;S\bX&#65533;S\b"..., size=4, 
    compar=0x80485f2 <cstring_cmp>) at program.c:89
#7  0x0804875b in qzsort_internal (
    begin=0xb7d87008 "&#65533;\237\025\bX\210c\bH\210c\b8&#65533;\004\bH&#65533;\004\b\030\210c\bh&#65533;\004\b\b\210c\b&#65533;\207c\b\230&#65533;\004\b&#65533;&#65533;\004\b&#65533;&#65533;\004\b&#560;\004\b&#1584;\004\b&#65533;\207c\b&#65533;\210c\b\b&#65533;\004\b\030&#65533;\004\b(&#65533;\004\b\210\207c\bx\207c\bX&#65533;\004\bh&#65533;\004\bx&#65533;\004\bX\207c\bH---Type <return> to continue, or q <return> to quit---
\207c\b8\207c\b\030\207c\b&#65533;\206c\b&#1585;\004\b&#65533;\206c\b&#65533;&#65533;\004\b\230\206c\bx\206c\b8\206c\b8&#65533;\004\b&#65533;\205c\bX&#65533;\004\bh&#65533;\004\b&#65533;\205c\b&#65533;\205c\b&#65533;\205c\b\210\205c\bh\205c\bX\205c\bH\205c\b(\205c\b&#65533;\204c\b\b&#65533;\004\b&#65533;\204c\b"..., 
    end=0xb7dcac08 "\030&#65533;\025\b(&#65533;\025\b&#65533;&#65533;S\bH&#65533;\025\b&#65533;&#65533;S\b\230&#65533;S\b\210&#65533;S\bx&#65533;S\b\230&#65533;\025\bh&#65533;S\bX&#65533;S\bH&#65533;S\b&#1568;\025\b8&#65533;S\b\030&#65533;S\b&#65533;&#65533;S\b\030&#65533;\025\b&#1575;S\b8&#65533;\025\b\230&#65533;S\bX&#65533;S\bh&#65533;\025\bx&#65533;\025\bH&#65533;S\b\230&#65533;\025\b&#65533;&#65533;\025\b&#65533;&#65533;\025\b8&#65533;S\b&#1569;\025\b&#65533;&#65533;\025\b&#65533;&#65533;\025\b\b&#65533;\025\b(&#65533;S\b\030&#65533;S\b8&#65533;\025\bH&#65533;\025\b&#65533;&#65533;S\b&#65533;&#65533;S\bx&#65533;\025\b\210&#65533;\025\b\210&#65533;e\b&#65533;&#65533;\025\b&#1574;S\b&#550;S\b&#65533;&#65533;S\b\230&#65533;S\b&#65533;&#65533;\025\b\210&#65533;S\bX&#65533;S\b8&#65533;S\b"..., size=4, 
    compar=0x80485f2 <cstring_cmp>) at program.c:91
#8  0x0804875b in qzsort_internal (
    begin=0xb7d87008 "&#65533;\237\025\bX\210c\bH\210c\b8&#65533;\004\bH&#65533;\004\b\030\210c\bh&#65533;\004\b\b\210c\b&#65533;\207c\b\230&#65533;\004\b&#65533;&#65533;\004\b&#65533;&#65533;\004\b&#560;\004\b&#1584;\004\b&#65533;\207c\b&#65533;\210c\b\b&#65533;\004\b\030&#65533;\004\b(&#65533;\004\b\210\207c\bx\207c\bX&#65533;\004\bh&#65533;\004\bx&#65533;\004\bX\207c\bH\207c\b8\207c\b\030\207c\b&#65533;\206c\b&#1585;\004\b&#65533;\206c\b&#65533;&#65533;\004\b\230\206c\bx\206c\b8\206c\b8&#65533;\004\b&#65533;\205c\bX&#65533;\004\bh&#65533;\004\b&#65533;\205c\b&#65533;\205c\b&#65533;\205c\b\210\205c\bh\205c\bX\205c\bH\205c\b(\205c\b&#65533;\204c\b\b&#65533;\004\b&#65533;\204c\b"..., 
    end=0xb7dcac0c "(&#65533;\025\b&#65533;&#65533;S\bH&#65533;\025\b&#65533;&#65533;S\b\230&#65533;S\b\210&#65533;S\bx&#65533;S\b\230&#65533;\025\bh&#65533;S\bX&#65533;S\bH&#65533;S\b&#1568;\025\b8&#65533;S\b\030&#65533;S\b&#65533;&#65533;S\b\030&#65533;\025\b&#1575;S\b8&#65533;\025\b\230&#65533;S\bX&#65533;S\bh&#65533;\025\bx&#65533;\025\bH&#65533;S\b\230&#65533;\025\b&#65533;&#65533;\025\b&#65533;&#65533;\025\b8&#65533;S\b&#1569;\025\b&#65533;&#65533;\025\b&#65533;&#65533;\025\b\b&#65533;\025\b(&#65533;S\b\030&#65533;S\b8&#65533;\025\bH&#65533;\025\b&#65533;&#65533;S\b&#65533;&#65533;S\bx&#65533;\025\b\210&#65533;\025\b\210&#65533;e\b&#65533;&#65533;\025\b&#1574;S\b&#550;S\b&#65533;&#65533;S\b\230&#65533;S\b&#65533;&#65533;\025\b\210&#65533;S\bX&#65533;S\b8&#65533;S\b8&#65533;\025\b"..., size=4, 
    compar=0x80485f2 <cstring_cmp>) at program.c:91


I can use any help.Thanks.

---

### Post by dwhitney67 on 2009-04-11
I recently had a prelim job "interview" with a company that wanted me to write a boat-load of code to fulfill the requirements of a make-believe project.  They allotted me 6 hours to complete the exercise, and even though I did complete the problem, apparently the requirements I was given were insufficient to fully satisfy their testing program's requirements and the algorithm I chose to sort objects was also poorly chosen (ie. took too long).  Since I did not get the job, I guess _I_ was at fault on both counts.  Btw, one of the requirements was that I was unable to use the C++ STL.

Anyhow, in an effort to prove that I could solve the problem more efficiently, I researched the quick sort algorithm (which I was familiar with from my days at the university), but for the most part is always discussed with arrays, never linked lists, which involve pointers.

I was lucky to finally find a worthy resource by Googling that help me along the way, and I finally came up with something that I will probably never have a need to use again (fingers crossed, and for good measure, I knocked on wood).

Here's the stuff, that hopefully can be adopted (downgraded) to C...
```

#ifndef NONSTD_LIST_H
#define NONSTD_LIST_H

#include <unistd.h>
#include <cassert>


namespace nonstd
{

template <class T>
class List
{
  private:
    class ListIterator;

  public:
    typedef ListIterator       iterator;
    typedef const ListIterator const_iterator;
    typedef T                  value_type;

    // constructor
    List()
      : m_head(0),
        m_tail(0),
        m_size(0)
    {
    }

    List(const List<T>& other)
      : m_head(0),
        m_tail(0),
        m_size(0)
    {
      for (iterator it = other.begin(); it != other.end(); ++it)
      {
        push_back(*it);
      }
    }

    // destructor
    ~List()
    {
      clear();
      m_head = m_tail = 0;
    }

    // push_front()
    void push_front(T elem)   // inserts at the beginning
    {
      if (m_head == 0)
      {
        m_head = new Node(elem, 0, 0);
        m_tail = m_head;
      }
      else
      {
        m_head = new Node(elem, 0, m_head);
      }
      ++m_size;
    }

    // pop_front()
    void pop_front()         // deletes the first element
    {
      Node* tmp = m_head->m_next;
      delete m_head;
      m_head = tmp;
      m_head->m_prev = 0;
      --m_size;
    }

    void push_back(T elem)   // inserts at the end
    {
      if (m_head == 0)
      {
        m_head = new Node(elem, 0, 0);
        m_tail = m_head;
      }
      else
      {
        m_tail->m_next = new Node(elem, m_tail, 0);
        m_tail = m_tail->m_next;
      }
      ++m_size;
    }

    void pop_back()         // deletes the last element
    {
      Node* tmp = m_tail;
      m_tail = tmp->m_prev;
      delete tmp;
      --m_size;
    }

    iterator insert(iterator& position, const T& elem)
    {
      iterator it = begin();

      for (; it != position; ++it);

      it.m_node->m_prev->m_next = new Node(elem, it.m_node->m_prev, it.m_node);
      ++m_size;

      return it.m_node->m_prev->m_next;
    }

    iterator erase(iterator position)
    {
      iterator it = begin();

      for (; it != position; ++it);

      it.m_node->m_prev->m_next = it.m_node->m_next;
      it.m_node->m_next->m_prev = it.m_node->m_prev;

      iterator next = it.m_node->m_next;

      delete it.m_node;

      --m_size;

      return next;
    }

    void clear()
    {
      iterator it = begin();

      while (it != 0)
      {
        Node* node = it.m_node;
        ++it;
        delete node;
      }
      m_size = 0;
    }

    size_t size() const
    {
      return m_size;
    }

    iterator begin()
    {
      return m_head;
    }

    const_iterator begin() const
    {
      return m_head;
    }

    iterator end()
    {
      return 0;
    }

    const_iterator end() const
    {
      return 0;
    }

    iterator last()
    {
      return m_tail;
    }

    const_iterator last() const
    {
      return m_tail;
    }

    void sort()
    {
      // we always number elements in linked list as 1, 2, ..., n
      // instead of 0, 1, ..., n-1; hence start index is 1.
      m_head = quicksort(m_head, 1, m_size);

      // restore previous-element pointers
      Node* node  = m_head;
      Node* pnode = 0;

      while (node != 0)
      {
        node->m_prev = pnode;
        pnode = node;
        node  = node->m_next;
      }
      m_tail = pnode;
    }

    typedef bool (*Sorter)(const T& first, const T& second);

    void sort(Sorter s)
    {
    }

  private:
    struct Node
    {
      Node(T elem, Node* prev, Node* next) : m_elem(elem), m_prev(prev), m_next(next) {}
      bool operator>(const Node& other)  { return m_elem > other.m_elem;  }
      bool operator<(const Node& other)  { return m_elem < other.m_elem;  }
      bool operator==(const Node& other) { return m_elem == other.m_elem; }

      T     m_elem;
      Node* m_prev;
      Node* m_next;
    };

    class ListIterator
    {
      public:
        typedef T iterator_category;

        ListIterator(Node* head) : m_node(head) {}

        ListIterator(const ListIterator& it) : m_node(it.m_node) {}

        bool operator==(const ListIterator& other) const { return m_node == other.m_node; }
        bool operator!=(const ListIterator& other) const { return m_node != other.m_node; }

        void operator++()   // goto the next element
        {
          assert(m_node != 0);
          m_node = m_node->m_next;
        }

        void operator--()   // goto the previous element
        {
          assert(m_node != 0);
          m_node = m_node->m_prev;
        }

        T& operator*()      // access the current element
        {
          assert(m_node != 0);
          return m_node->m_elem;
        }

    private:
        friend class List<T>;
        Node* m_node;
    };


    // quicksort()
    //
    Node* quicksort(Node* list, unsigned int listStart, unsigned int listEnd)
    {
      if (listStart >= listEnd)
        return list;

      unsigned int i = listStart;
      unsigned int j = listEnd - 1;

      Node* right = getNthNode(list, listEnd);
      Node* left  = getNthNode(list, listStart);
      Node* pivot = selectPivot(left, right);
      right       = findPrev(left, pivot);

      for (;;)
      {
        // now start partitioning the list
        for (; left->m_elem < pivot->m_elem; ++i)
        {
          left = left->m_next;
        }

        for (; (right->m_elem > pivot->m_elem) && (j > 1); --j)
        {
          right = findPrev(list, right);
        }

        if (i < j)
        {
          list = swapNodes(list, left, right);

          // left, right ptrs got swapped, to continue traversing we need them
          // back at the same positions.
          Node* tmp = left;
          left  = right;
          right = tmp;
        }
        else
        {
          break;
        }
      }

      // restore pivot
      list = swapNodes(list, left, pivot);

      // now sort on smaller linked lists
      list = quicksort(list, listStart, i-1);
      list = quicksort(list, i+1, listEnd);

      return list;
    }

    // getNthNode()
    //
    Node* getNthNode(Node* list, unsigned int n)
    {
      for (unsigned int i = 1; list != 0 && i < n; ++i)
      {
        list = list->m_next;
      }

      return list;
    }

    // selectPivot()
    //
    Node* selectPivot(Node* list, Node* end)
    {
      unsigned int n = numNodes(list, end);
      Node* noden = getNthNode(list, (unsigned int)((float)n/2 + 0.5));
      Node* right = findPrev(list, end);

      if (noden != right)
      {
        // swap the pivot and right most element in the list
        // later pivot will be restored.
        swapNodes(list, noden, right->m_next);
        return noden;
      }
      else
      {
        return noden->m_next;
      }
    }

    // numNodes()
    //
    unsigned int numNodes(Node* list, Node* end)
    {
      unsigned int i = 1;

      for (; list && (list != end); ++i, list = list->m_next);

      return (list == end ? i : 0);
    }

    // findPrev()
    //
    Node* findPrev(Node* list, Node* curr)
    {
      for (; list && list->m_next; list = list->m_next)
      {
        if (list->m_next == curr)
          break;
      }

      if (list->m_next != curr)
      {
        // we did not find any element; probably indicates what
        // we are searching for is the beginning node.
        return curr;
      }

      return list;
    }

    // swapNodes()
    //
    // A complete swap algorithm which cares of several scenarios while swapping
    // two nodes in a linked list which doesn't have any special nodes.
    // Scenarios considered while swapping:
    // 1) two nodes which are far away
    // 2) two nodes which are far away, one is node at the beginning of the list
    // 3) two nodes which are neighbors
    // 4) two nodes which are neighbors, one node is at the beginning of the list
    Node* swapNodes(Node* list, Node* node1, Node* node2)
    {
      Node* node1prev = findPrev(list, node1);
      Node* node2prev = findPrev(list, node2);
      Node* tmp       = node2->m_next;

      // check whether node to be swapped is in beginning (i.e. header node)
      if (node1 != list)
      {
        node1prev->m_next = node2;
      }
      else
      {
        // as we do not have special header node, if the first node and some
        // other node, need to be swapped, then update the list (makes new min
        // node as logical header)
        list = node2;
      }

      // are nodes to be swapped neighboring nodes?
      if (node1->m_next == node2)
      {
        node2->m_next = node1;
        node1->m_next = tmp;
      }
      else
      {
        // nodes to be swapped are not neighbor nodes, they are apart;
        // so condiser all scenarios
        node2->m_next = node1->m_next;
        node1->m_next = tmp;
        node2prev->m_next = node1;
      }

      return list;
    }

    // Data Members
    Node*  m_head;
    Node*  m_tail;
    size_t m_size;
};

} // end namespace nonstd

#endif

```

---

### Post by lisati on 2009-04-11
Looking at the debugger's output I might suspect a rogue pointer or something of that nature.

---

### Post by dwhitney67 on 2009-04-11
> **lisati said:**
> Looking at the debugger's output I might suspect a rogue pointer or something of that nature.

Yep, that would cause a problem.  =D>

---

### Post by soltanis on 2009-04-11
The problem is finding where the rogue pointer is and why.

#1 frustration of debugging C programs.

---

### Post by dwhitney67 on 2009-04-12
The cstring_cmp() function piqued my interest; I don't quite understand why there is a need to cast the const void* to a const char**.

I wrote this little program (see below) to test the differences; the cstring_cmp2() function, which mimics the OP's, causes the application to crash.

```

#include <string.h>
#include <stdio.h>

int cstring_cmp1(const void* a, const void* b)
{
  const char* sa = (const char*) a;
  const char* sb = (const char*) b;

  return strcmp(sa, sb);
}

int cstring_cmp2(const void* a, const void* b)
{
  const char** sa = (const char**) a;
  const char** sb = (const char**) b;

  return strcmp(*sa, *sb);
}


int main(int argc, char** argv)
{
  printf("cstring_cmp1 = %d\n", cstring_cmp1(argv[0], argv[0]));

  printf("cstring_cmp2 = %d\n", cstring_cmp2(argv[0], argv[0]));

  return 0;
}

```

---

### Post by Arndt on 2009-04-12
> **dwhitney67 said:**
> 

Anyhow, in an effort to prove that I could solve the problem more efficiently, I researched the quick sort algorithm (which I was familiar with from my days at the university), but for the most part is always discussed with arrays, never linked lists, which involve pointers.



I'd like to recommend to everybody that they choose a stable sorting algorithm, if possible. Quicksort isn't stable, mergesort is (among others). And mergesort is much easier to use with linked lists. (The 'qsort' algorithm in Linux isn't necessarily quicksort - I don't know which algorithm it is.)

A stable sorting algorithm has the property that elements which compare equal (but may have extra information connected to them which doesn't take part in the comparison) remain in the same order after the sorting as they were before.

When sorting a table with several columns, this means that no special sorting function has to be written, which sorts multi-column; you just sort first according to the less important column, then the more important one, and the sorting of the less important column will not have been destroyed.

Sadly, almost every column presentation with sorting ability that one sees nowadays uses a nonstable sort, and usually with no way to even specify multi-column sorting. A stable sorting algorithm gives substantial added value, for no additional work at all in the interface.

Anther reason for avoiding quicksort is that it may become O(n^2) in certain cases, if you don't add extra logic. Mergesort is O(n*ln n).

If the OP has been told to implement quicksort specifically, this is of course no help for solving his problem.

---

