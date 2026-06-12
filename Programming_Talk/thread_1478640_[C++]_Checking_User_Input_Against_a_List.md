---
title: "[C++] Checking User Input Against a List"
date: 2010-05-09
forum: Programming Talk
---

### Post by dodle on 2010-05-09
In Python the keyword "[color=red]in[/color]" could be used to check if a string (or other type) was in a list:
[php]if mystring in mylist:
  print "It is in the list"
else:
  print "Not found in the list"[/php]

Is there a similar keyword in C++, or do I need to create a function to iterate through a list?

---

### Post by soltanis on 2010-05-10
Uh, maybe? There is no "in" keyword in C++ although with the joys of operator overloading there's a good chance some C++ library lets you do that. I'll let someone who actually knows C++ (or uh, more of it than I do) answer, and for my part I can tell you that in C, you will have to use a compound conditional statement (if, else if, else) (and C doesn't have a concept of lists).

---

### Post by MadCow108 on 2010-05-10
there are the STL containers and algorithms
[http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)
[http://www.cplusplus.com/reference/algorithm/](http://www.cplusplus.com/reference/algorithm/)

what you are looking for is:
find, bsearch, upper_bound, lower_bound or equal_range

also have a look at the map, which is a kind of dictionary (based on a btree and not a hashtable like in python)

your python code would translate to:
```

list<string> l;
..
list<string>::iterator res = find(l.begin(), l.end(), mystring);
if (res != l.end())
  cout << "found" << endl;
else
  cout << "not found" << endl;

```

the algorithm's work on all containers with an STL interface

---

### Post by dodle on 2010-05-10
Thanks madcow, that does just what I need it to.  Thanks for the example as well.

[php]#include <iostream>
#include <list>
#include <algorithm>
using namespace std;

int main()
{
  string mystring;
  list<string> mylist;
  mylist.push_back("Hello");
  mylist.push_back("World");
  
  cout << "Type Something: ";
  getline(cin, mystring);
  
  list<string>::iterator get = find(mylist.begin(), mylist.end(), mystring);
  if (get != mylist.end())
    cout << mystring << " found in list." << endl;
  else
    cout << mystring << " not found." << endl;
  
  return 0;
}
[/php]

---

