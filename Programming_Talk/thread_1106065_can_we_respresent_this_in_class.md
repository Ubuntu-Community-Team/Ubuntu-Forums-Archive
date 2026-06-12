---
title: "can we respresent this in class?"
date: 2009-03-25
forum: Programming Talk
---

### Post by abhilashm86 on 2009-03-25
if i have to declare member data val and link in a link list, like this
```

struct node
{
     int val,a[max_size];
     struct node *link;
};

```
suppose i rewrite this in c++ using class, then how to convert link part?
```

class list
{
 public:
        int val,a[max_size];
 ...................
}

```
then how to write node part? i want to know whether this is possible? please tell how to.....

---

### Post by CptPicard on 2009-03-25
Several possibilities there, but I guess the most accepted way would be to first define Node as a nested class, and then declare List and Node to be "friends". This way the Node is in the namespace of the class List, and you get direct access to stuff in the list/node from the other class.

Google for it, or let's wait dwhitney67 or someone to write an example ;)

---

### Post by dwhitney67 on 2009-03-25
Sorry for the delay... :-)


If in C, you have
```

struct node
{
   int val;
   int a[max_size];
   struct node *link;
};

```
then in C++, you have 3 options to declare something similar:

1.  Leave it the same as shown above.

2.  Continue to use a struct, but as:
```

struct node
{
   int val;
   int a[max_size];
   node* link;  // the keyword 'struct' is not needed here
};

```
Bear in mind, that in C++, a class and a struct are identical, except for the default permission levels.  For a struct, by default, all members are publicly accessible.

3.  Define node as a class:
```

class node
{
public: // this is to ensure member data is accessible
   int val;
   int a[max_size];
   node* link;
};

```

If you are defining a linked-list, this type of definition is common (I believe Cpt Picard was pointing this out):
```

struct Data
{
   int val;
   int a[max_size];
};

template <typename T>
class LinkedList
{
public:
   ...

   void insert(T data);

private:
   struct node
   {
      T     data;
      node* link;
   };

   node* m_head;
   node* m_tail; 
};

...

int main()
{
   LinkedList<Data*> ll;

   Data* d = new Data;
   ...

   ll.insert(d);
   ...
}

```
Generally there is not a need to make the 'struct node' publicly visible, since the user of the LinkedList only cares about the data that they have inserted into the list.

I recommend that if your node will have more than one item of data, that you define those data items in a separate struct.

---

### Post by abhilashm86 on 2009-03-25
```

#include<iostream>
#include<cstdlib>
using namespace std;


class list
{
        private:
                int val,info;
                list *link;
        public:
                int insert(int);
                int deletee();
                int display();
};

```
yes now i can represent this using a class, but firstly to my and friends knowledge, i thought struct was compulsory in declaring data members, thanks for help.I'll surely try nested classes.

---

