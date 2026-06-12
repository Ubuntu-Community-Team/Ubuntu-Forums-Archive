---
title: "Errors compiling a simple 3 file C++ project"
date: 2013-07-15
forum: Programming Talk
---

### Post by lgp171188 on 2013-07-15
**linked_list.h**
```

/* linked_list.h */
#ifndef _LINKED_LIST_H
#define _LINKED_LIST_H

#include<iostream>

template <class T>
class LinkedList
{
  struct node {
    T data;
    struct node* next;
  };



public:
  LinkedList();
  void add_node(T data, int position);
  void delete_node(T data);
  void print();
};

#endif

```

**linked_list.cpp**
```

/* linked_list.cpp */
#include<iostream>
#include "linked_list.h"
using namespace std;

template <class T>
LinkedList<T>::LinkedList()
{
  head = NULL;
}

template <class T>
void LinkedList<T>::add_node(T data, int position)
{
  struct node** pp = &head;
  int current_position = 0;
  while(*pp != NULL && position != current_position) {
    ++current_position;
    pp = &(*pp)->next;
  }

  struct node* temp = new node();
  temp->data = data;
  temp->next = *pp;
  *pp = temp;
}

template <class T>
void LinkedList<T>::print()
{
  struct node* temp = head;
  int count = 0;
  while(temp != NULL) {
    std::cout<<temp->data<<endl;
    temp = temp->next;
  }
}

template<class T>
void LinkedList<T>::delete_node(T data)
{
  struct node** pp = &head;
  while(*pp != NULL && (*pp)->data != data)
  {
    pp = &(*pp)->next;
  }
  if (pp != NULL)
  {
    node *temp = *pp;
    *pp = (*pp)->next;
    delete(temp);
  }
  else
    cout<<"Data: "<<data<<" not found in the list"<<endl;
}

```
**m.cpp**
```

/* m.cpp */
#include<iostream>
#include "linked_list.h"
using namespace std;

int main() {
  LinkedList<int> l;
  l.add_node(1,0);
  l.add_node(2,1);
  l.add_node(3,2);
  l.add_node(4,3);
  l.add_node(6,4);
  l.add_node(5,4);
  l.add_node(7,6);
  l.print();
  return 0;
}


```
The command I run to compile, link and create an executable:
```
g++ linked_list.cpp m.cpp
```

Error:
```

linked_list.cpp: In constructor ‘LinkedList<T>::LinkedList()’:
linked_list.cpp:8:3: error: ‘head’ was not declared in this scope
   head = NULL;
   ^
linked_list.cpp: In member function ‘void LinkedList<T>::add_node(T, int)’:
linked_list.cpp:14:23: error: ‘head’ was not declared in this scope
   struct node** pp = &head;
                       ^
linked_list.cpp: In member function ‘void LinkedList<T>::print()’:
linked_list.cpp:30:23: error: ‘head’ was not declared in this scope
   struct node* temp = head;
                       ^
linked_list.cpp: In member function ‘void LinkedList<T>::delete_node(T)’:
linked_list.cpp:41:23: error: ‘head’ was not declared in this scope
   struct node** pp = &head;
                       ^

```

Any idea what I am doing wrong here? Actually this code worked fine as long as it was in a single .cpp file. As soon as I split it, I get errors like this or linker errors saying symbol not found.

---

### Post by mvs1207 on 2013-07-15
You need to declare "head" in your class as type ```
struct node * head;
```.

---

### Post by mvs1207 on 2013-07-15
For templates in different file, I found this [link]("http://stackoverflow.com/questions/495021/why-can-templates-only-be-implemented-in-the-header-file") in stack overflow.

HTH

---

### Post by lgp171188 on 2013-08-08
Thanks for the pointer to the Stackoverflow discussion. It was helpful.

---

