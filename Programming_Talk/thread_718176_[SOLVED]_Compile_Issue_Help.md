---
title: "[SOLVED] Compile Issue Help"
date: 2008-03-07
forum: Programming Talk
---

### Post by JupiterV2 on 2008-03-07
I wrote a custom header that inherits a class that uses templates from a separate header, which I also wrote. The GUI for my program has been written with gtkmm. With the following compile command to g++:

g++ -c -Wall main.cpp -o main.o `pkg-config --cflags gtkmm-2.4`

I get a bunch of errors that boil down to an issue with the class which inherits the templated class. When I remove the 'pkg-config...` line, the code compiles happily and works as intended (all calls to GUI commented out). I then commented out all the code related to the custom headers and gtkmm compiles happily. However, they won't work together.

I wrote a test suite for the custom headers and ran the code through a battery of tests. I also ran the test suite with valgrind to check for memory leaks. Code worked perfectly.

I am only having an issue with the custom headers when gtkmm is involved.

Do I need to rewrite my custom library and compile it into a dynamic library to resolve the issue? Is g++ automatically pre-compiling the templated header and causing an issue? (I know that only 1 pre-compiled header can be used per program)

Anyone able to point me in the right direction?

---

### Post by PaulFr on 2008-03-08
Could you post some of the actual error lines ?

---

### Post by JupiterV2 on 2008-03-08
Here is a sample of the errors (with a heck of a lot of stuff commented out to produce the origin of the problem):

```
main.cpp: In function ‘int main(int, char**)’:
main.cpp:8: error: ‘List’ was not declared in this scope
main.cpp:8: error: expected primary-expression before ‘int’
main.cpp:8: error: expected `;' before ‘int’
```

List is a class template:

[php]template <class T>
class List {
  protected:
    unsigned int index;
    std::vector<T> list;

  public:
    /* constructors */
    explicit List();
    virtual ~List();

    /* Helpers */
    const bool empty() const;
    const bool full() const;
    const unsigned int size() const;

    /* Modifiers */
    void free();
    virtual void insert(T t);
    T remove();
    T remove(int i);

    T operator[] (int i) const { return list.at(i); }
};
[/php]

The main.cpp looks as follows (bare bones version):

[php]#include <gtkmm/main.h>
#include "list.h"

int main(int argc, char* argv[]) {
    Gtk::Main kit(argc, argv);
    
    // for testing purposes...
    List<int> l;
    
    return 0;
}
[/php]


Through extra testing, I did manage to narrow things down a bit further. The code compiles fine with:

g++ -c main.cpp -o main.o `pkg-config --cflags gtkmm-2.4`

...when #include <gtk/main.h> has been commented out. Uncommenting it produces the errors mentioned above.

---

### Post by PaulFr on 2008-03-08
Have you checked template instantiation ? I did not get your error with gtkmm/main.h included. Here is what I did to get your sample code to compile to an executable: ```
#include <gtkmm/main.h>
#include "list.h"

[B]template <> class List<int> {
    public:
        List() { }
};[/B]

int main(int argc, char* argv[])
{
    Gtk::Main kit(argc, argv);

    // for testing purposes...
    List<int> l;

    return 0;
}
```

---

### Post by JupiterV2 on 2008-03-08
> 
```

#include <gtkmm/main.h>
#include "list.h"

template <> class List<int> {
    public:
        List() { }
};

int main(int argc, char* argv[])
{
    Gtk::Main kit(argc, argv);

    // for testing purposes...
    List<int> l;

    return 0;
}

```


Compiling your code I get the error:

main.cpp:5: error: ‘List’ is not a template
main.cpp:5: error: explicit specialization of non-template ‘List’
main.cpp: In function ‘int main(int, char**)’:
main.cpp:13: error: ‘List’ is not a template

Perhaps I should give you the full version of some of my code:

```

/******************************************************************************
    Copyright Rob Thornton (2008)
    All rights reserved.
******************************************************************************/

#ifndef _LIST_H
#define _LIST_H

#include <vector>

template <class T>
class List {
  protected:
    unsigned int index;
    std::vector<T> list;
    
  public:
    /* constructors */
    explicit List();
    virtual ~List();

    /* Helpers */
    const bool empty() const;
    const bool full() const;
    const unsigned int size() const;

    /* Modifiers */
    void free();
    virtual void insert(T t);
    T remove();
    T remove(int i);
    
    T operator[] (int i) const { return list.at(i); }
};


/******************************************************************************
    Constructors
******************************************************************************/
template <class T>
List<T>::List()
:
    index(0)
{
    list.resize(10);
}

template <class T>
List<T>::~List() {}

/******************************************************************************
    Helpers
******************************************************************************/
template <class T>
const bool List<T>::empty() const { return index == 0; }

template <class T>
const bool List<T>::full() const { return index == list.size(); }

template <class T>
const unsigned int List<T>::size() const { return index; }


/******************************************************************************
    Modifiers
******************************************************************************/
template <class T>
void List<T>::free() {
	list.clear();
	list.resize(10);
	index = 0;
}

template <class T>
void List<T>::insert(T t) {
    if( full() ) list.resize( list.size() + 10);

    list[index++] = t;
}

template <class T>
T List<T>::remove() {
    T t;

    if( empty() ) return t;
    else return list[--index];
}

template <class T>
T List<T>::remove(int i) {
    T t;

    if( !empty() ) {
        t = list[i];
        list[i] = list[--index];
    }
    return t;
}

#endif /* _LIST_H */

```

This is an example of one of the inheriting classes:

```

/******************************************************************************
    Copyright Rob Thornton (2008)
    All rights reserved.
******************************************************************************/

#ifndef _GROUP_H
#define _GROUP_H

#include "list.h"
#include "node.h"

class Group : public List<Node> {
    bool enabled;
    std::string header;

  public:
    /* constructors */
    explicit Group();
    explicit Group(std::string, bool);
    virtual ~Group();

    /* Helpers */
    bool getenabled();
    std::string getheader();

    /* Modifiers */
    void copy(Group &g);
    void setenabled(bool);
    void setheader(std::string);
};


/******************************************************************************
    Constructors
******************************************************************************/
Group::Group()
:
    enabled(true),
    header("Unknown")
{}

Group::Group(std::string h, bool e)
:
    enabled(e),
    header(h)
{}

Group::~Group() {}


/******************************************************************************
    Helpers
******************************************************************************/
bool Group::getenabled() { return enabled; }

std::string Group::getheader() { return header; }


/******************************************************************************
    Modifiers
******************************************************************************/
void Group::copy(Group &g) {
	unsigned int s = g.size();
	
	for(unsigned int i = 0; i < s; i++) insert(g[i]);
}

void Group::setenabled(bool e) { enabled = e; }

void Group::setheader(std::string h) { header = h; }

/******************************************************************************
    Non-Member
******************************************************************************/
template<class _CharT, class _Traits>
std::basic_ostream<_CharT, _Traits>& 
operator<< (std::basic_ostream<_CharT, _Traits>& out, Group& g) {
	 out << "[" << g.getheader() << "]";
	return out;
}


#endif /* _GROUP_H */


```

I wrote the following test program which compiles and runs without issue:

```

#include <iostream>
#include "catagory.h"
#include "group.h"

int main(int argc, char* argv[])
{
    Group g1("header1", true);
    Group g2("header2", false);

    Node n1("lhs1", "rhs1", "sp11", "sp21");
    Node n2("lhs2", "rhs2", "sp12", "sp22");
    Node n3("lhs3", "rhs3", "sp13", "sp23");
    Node n4("lhs4", "rhs4", "sp14", "sp24");

    g1.insert(n1);
    g1.insert(n2);
    g1.insert(n3);
    g1.insert(n4);
    
    g2.copy(g1);
    
    Catagory c;
    c.insert(g1);
    c.insert(g2);
    
    Group g3("header3", true);
    
    Catagory c2;
    c2.read("test.dat");

    std::cout << "c2.empty=" << (c2.empty() ? "true" : "false") << std::endl;
    c.write("test.dat");
    copy(c2, g3);
    
    Group g4 = c2.remove();

    std::cout << "g4.empty=" << (g4.empty() ? "true" : "false") << std::endl;
    std::cout << g1.getheader() << ":" << (g1.getenabled() ? "true" : "false") 
        << std::endl;
    std::cout << g2.getheader() << ":" << (g2.getenabled() ? "true" : "false") 
        << std::endl;
    std::cout << g3.getheader() << std::endl;
    std::cout << g4.getheader() << ":" << (g4.getenabled() ? "true" : "false") 
        << std::endl;

    int x = 0;

    while( !g3.empty() ) {
        Node n = g3.remove(x++);
        std::cout << n << std::endl;
    }
 
    return 0;
}

```

I hope this helps to diagnose the problem. Like I said, the above code compiles and runs perfectly. I would think that were I not instantiating the template correctly the test code would fail too.

I assumed that including the above headers into my program (the non-test program) would go flawlessly when the conflict arose. I'm willing to bet its something silly like a missed semi-colon but buggered if I can find it.

---

### Post by PaulFr on 2008-03-08
Interesting.

Okay, I was able to reproduce your problem once I added your guard lines **_LIST_H** to list.h.

So, **_LIST_H** at the top of your list.h is already defined somewhere in gtkmm or headers included from it, and so you are not having your list.h expanded at all. 

I changed this to **#ifndef _MYLIST_H**, and it worked.  Please try.

Update: FYI, I searched for the header file where _LIST_H was defined, and I found it in **/usr/include/c++/4.2/bits/stl_list.h**.

---

### Post by JupiterV2 on 2008-03-09
This solved the issue. Thanks so much!

---

### Post by aks44 on 2008-03-09
> **PaulFr said:**
> So, **_LIST_H** at the top of your list.h is already defined somewhere in gtkmm or headers included from it, and so you are not having your list.h expanded at all. 

I changed this to **#ifndef _MYLIST_H**, and it worked.  Please try.

Update: FYI, I searched for the header file where _LIST_H was defined, and I found it in **/usr/include/c++/4.2/bits/stl_list.h**.


More on that topic: names beginning with an underscore are **implementation-reserved**. Which means that, unless one is writing a C++ compiler or an STL implementation, one should never ever declare such names.

---

