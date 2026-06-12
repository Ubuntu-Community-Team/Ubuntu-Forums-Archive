---
title: "Understanding basic concepts in C++"
date: 2007-10-15
forum: Programming Talk
---

### Post by keifer on 2007-10-15
I'm working on teaching myself C++ in my spare time, and most of what I learned with Ruby/Python is translating really well. The two items that I'm having problems understanding are pointers and the rational about how header files are handled. 

If I'm understanding pointers correctly, they allow multiple variables to reference the same chunk of data in memory? What is the advantage over just using a single variable? Could someone *please* point me to a good resource on getting a handle on pointers? Pleeeeaaaase? ;)

As for headers, I'm just wondering why C++ encourages separating the declaration from the implementation. I'm sure there must be an advantage to it, but all I'm see is the increase in files to manage.

Please forgive the novice questions, but my high school only offers visual-basic classes ( yuck ).

---

### Post by sixblades on 2007-10-15
One example of how pointers can be useful:
Linked lists. These are essentially arrays that can be resized quite easily and have several advantages that typical arrays don't. Now I'm a little rusty on my C++, but here's essentially how a linked list works:

You create a custom class that includes three different variables. We'll call this a "node" class, and let's just say that it's used to store integers (for simplicity). This "node" class includes a pointer to the previous node's memory address and the next node's memory address, as well as the actual data stored. I'd like to provide some example code for you, but I'm worried that my current heavy Java usage would result in bad C++ code.

Also:
[http://en.wikipedia.org/wiki/Linked_list]("http://en.wikipedia.org/wiki/Linked_list")
[http://en.wikipedia.org/wiki/Binary_tree]("http://en.wikipedia.org/wiki/Binary_tree")

Hope that helps a bit. :)

---

### Post by ryno519 on 2007-10-15
Questions are good. No need to ask for forgiveness. :)

Pointers can be tricky to grasp at first, but they're a very powerful tool. Yes, a pointer *points* to a location in memory. Consider this example to get an idea of how a pointer could be useful.

```

#include <iostream>
#include <list>

using namespace std;

list<int> PopulateList()
{
    list<int> integers;
    for(int i = 0; i < 1000; ++i)
        integers.push_back(i);
        
    return integers;
}

void ShowList(list<int> integers)
{
    list<int>::iterator iter = integers.begin();
    for(; iter != integers.end(); ++iter)
        cout << *iter << endl;
}

int main()
{
    list<int> integers = PopulateList();
    ShowList(integers);

    return 0;
}

```

PopulateList will return a list of 1000 ints which we'll say is 4000 bytes of memory. Now when you pass this object to ShowList by value what it will do is make a copy of that list, so you are creating an identical list which will also be 4000 bytes. This is a waste of memory and a waste of clock cycles. Lets try doing this with pointers.

```

#include <iostream>
#include <list>

using namespace std;

list<int>* PopulateList()
{
    list<int>* integers = new list<int>();
    for(int i = 0; i < 1000; ++i)
        integers->push_back(i);
        
    return integers;
}

void ShowList(list<int>* integers)
{
    list<int>::iterator iter = integers->begin();
    for(; iter != integers->end(); ++iter)
        cout << *iter << endl;
}

int main()
{
    list<int>* integers = PopulateList();
    ShowList(integers);

    delete integers;

    return 0;
}

```

Notice that PopulateList now returns a pointer. We're now simply passing the location in memory of the list back and forth. Now when we pass the value to ShowList instead of copying those 4000 bytes, all that will be sent is the 4 byte memory location.

Disclaimer: This is NOT the best way to implement the above example.

The declarations and implementations are seperated mainly due to readability. If you want to use somebodies opensource library or adding to a piece of opensource code you didn't write this comes in handy. Typically you will ONLY want to see the prototype and a summary of what it does if you want to use that method. You don't really care how the original programmer implemented that method, all you care about is how to use it. If the definitions and implementations were in the same file it would be all that much harder to read.

---

### Post by dwhitney67 on 2007-10-16
Pointers are a feature of C and C++ (and possibly other languages).  As previously mentioned, if used imaginatively, they can be used to create link lists of data that are easily traversable, or in which data can easily be added or subtracted.  Passing objects as pointers between functions (as ryno519 demonstrated) can help with performance.  In other cases it is used to access data within hardware registers which otherwise might not be possible.

Concerning your other question about the separation of header files and implementation, that is mainly to divide the declarations of data types and functions from the implementation.  Also it lends itself for ease in s/w maintenance and also to speed up the compilation process.  There are cases when the implementation is placed in header files:  inline functions and when dealing with templates.  In other cases, a developer may simply be lazy.  What irks me is when some non-inline implementation is in the header file and other in the regular .cpp file.

Anyhow, everybody has an opinion, and mine is that it is hard to examine the public interface of a class whose header file is "polluted" with implementation code. It's probably one of the reasons I dislike Java (even though I use it on occasion!); but that is another topic.

Btw, what might also confuse you is the subtle difference between pointers and references.  Taking ryno519's example and putting a little twist on it to use references:

```
#include <iostream>
#include <list>
#include <iterator>

using namespace std;

typedef list< int >            MyList;
typedef MyList::iterator       MyListIterator;
typedef MyList::const_iterator MyListConstIterator;


void PopulateList( MyList& intList, const int maxNums = 10 )
{
  for( int i = 0; i < maxNums; ++i )
  {
    intList.push_back( i );
  }
}

void ShowList( const MyList& intList )
{
  for( MyListConstIterator iter = intList.begin(); iter != intList.end(); ++iter )
  {
    cout << *iter << " ";
  }
  cout << endl;
}

void AlternateShowList( const MyList& intList )
{
  copy( intList.begin(), intList.end(), ostream_iterator< int >( cout, " " ) );
  cout << endl;
}

int main( int argc, char** argv )
{
  MyList integers;

  PopulateList( integers );
  ShowList( integers );
  AlternateShowList( integers );
}
```

P.S.  ryno519 - your code has a memory leak; you really should show the "delete" for the list allocated in PopulateList().

---

### Post by ryno519 on 2007-10-16
> **dwhitney67 said:**
> P.S.  ryno519 - your code has a memory leak; you really should show the "delete" for the list allocated in PopulateList().

Yes, I should have. This just goes to show you that a ubuntu forums quick reply box is not the ideal development environment.

---

### Post by dwhitney67 on 2007-10-16
I agree.  Perhaps that's something that could be added in the future... a "preview/compile" feature that only looks at the text within the CODE section.

I for one try to compile/test my code before submitting it.  There is nothing worse than having buggy code shot down by a peer.

In your example, showing the delete is not a necessity, but merely for completeness.  The memory would have been returned to the heap after the program terminated.

---

### Post by ryno519 on 2007-10-16
> **dwhitney67 said:**
> I agree.  Perhaps that's something that could be added in the future... a "preview/compile" feature that only looks at the text within the CODE section.

I for one try to compile/test my code before submitting it.  There is nothing worse than having buggy code shot down by a peer.

In your example, showing the delete is not a necessity, but merely for completeness.  The memory would have been returned to the heap after the program terminated.

That would be an interesting feature, but wouldn't do much to find bugs, just syntax errors. I usually compile and test my code, and I did for the first example. For the second example I just changed the first one around a bit and assumed it would work.

Just goes to show, never assume anything will work and when possible have a peer review your code.

---

### Post by aks44 on 2007-10-16
Others already replied about pointers, I'll just add that ryno's example is *not* exception safe (but this is a more advanced topic, let's not confuse the OP for now ;)), PopulateList() should return a RAII wrapper class, or use dwhitney67's method (which I tend to use a lot).


> **keifer said:**
> IAs for headers, I'm just wondering why C++ encourages separating the declaration from the implementation. I'm sure there must be an advantage to it, but all I'm see is the increase in files to manage.

It may look like it at first glance, but now imagine you rely on a library that is millions of lines of code (eg. Linux's kernel, X Windows / GTK / QT libraries, ...).
Separating declarations from definitions allows you to use only the relevant headers (which usually contain way less stuff than the implementation), and link your code with pre-compiled binaries of the library. Imagine if you had to download and let the compiler parse the whole kernel sources just to write a small "hello world" program...

Plus, as long as the interface in the headers (signature of functions, ...) doesn't change, a library's developper is free to change the underlying implementation (eg. to correct bugs) and to benefit of the changes you only have to download the new pre-compiled binaries, instead of the whole new code.


For all programming languages, doing more work upfront is the best way to make your life easier in the near future. Doing less work now only increases exponentially the amount of work you'll have to do soon.
So a truly lazy programmer (as anyone sane should be ;)) does the hard work *now* to be able to avoid much more work in the future...

---

### Post by vambo on 2007-10-16
The best explanation of pointers I've ever come across is in "The C Programming Language"  by Kernighan and Ritchie. You might find it in a library - not aware of any of it being online.

---

### Post by keifer on 2007-10-16
Thanks for the explanations, now I just need to find some free time to  tinker and explore. :)

---

### Post by mjwood0 on 2007-10-16
> **aks44 said:**
> So a truly lazy programmer (as anyone sane should be ;)) does the hard work *now* to be able to avoid much more work in the future...

Man -- I want to become a programmer in another 20 years... :)

---

### Post by spookware on 2007-10-17
I would just add that the separation of header and source files is more to do with the c/c++ compilation model than it does with some sort of software engineering ideology. Unlike many modern languages C/C++ utilizes separate compile and link phases. 

So if I have two distinct source files that use a shared definition each source file needs to know the definition of that item. In many modern languages this is accomplished by giving the compiler all source files at once so that the compiler has complete global knowledge of all definitions and can choose the right one. However since C/C++ compile each source file individually and then link them together each individual file must be provided with the definition, thus the definition is placed in a header so that multiple source files can share the same definition.

So I would argue that the separation of definition from implementation is actually an artifact of the C/C++ compilation model and not some sort of engineering discipline.

---

### Post by slavik on 2007-10-17
it also allows you to compile the source and still have the definition available.

---

