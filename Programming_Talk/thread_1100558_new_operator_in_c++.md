---
title: "new operator in c++"
date: 2009-03-19
forum: Programming Talk
---

### Post by abhilashm86 on 2009-03-19
```
#include<iostream>
#include<cstdlib>
using namespace std;

struct NODE
{
        int info;
        struct NODE *link;
};
                struct NODE *first=NULL;
class list
{

        public:

                int insert(int info);
                int deletee();
                int display();
};

```

here is insert function,
```
int list::insert(int val)
{
        NODE *temp,*first,*pass;
        temp=new(struct NODE);
        temp->info=val;
        temp->link=NULL;
        if(first==NULL)
        {
                first=temp;

        }
        else

                pass=first;
            while(pass->link!=NULL)
                {
                        pass=pass->link;
                }
        pass->link=temp;
                              
```

following error is occuring, 
abhilash@abhi:~$ g++ cp24.cpp
abhilash@abhi:~$ ./a.out
1:insert 2:delete 3:display 4:exit
enter the choice
1
enter element to list
12
Segmentation fault

what is error segmentation fault? which part is causing it?

---

### Post by abhilashm86 on 2009-03-19
```
int list::insert(int val)
{
        NODE *temp,*first,*pass;
        temp=(struct NODE *)malloc(sizeof(struct NODE));
        temp->info=val;

```
also i changed new operator to malloc, then also segmentation fault is occuring?

---

### Post by dwhitney67 on 2009-03-19
You should not use malloc() in a C++ program.  Use 'new' instead.

Also, when declaring a variable, try to initialize it too.  So
```

Node* temp = new Node;
temp->info = val;
temp->next = 0;
...

```
In C++, you do not need to use the keyword 'struct' when declaring an object.

---

### Post by dwhitney67 on 2009-03-19
Also, since you are modeling a linked-list within a class (which btw is a good idea), your head node should be defined as a class member, not a local variable within your insert() method.  This variable should be initialized to 0 (NULL) in your List constructor.

Elements that you allocate should be freed in the destructor.

---

### Post by abhilashm86 on 2009-03-19
> **dwhitney67 said:**
> You should not use malloc() in a C++ program.  Use 'new' instead.

Also, when declaring a variable, try to initialize it too.  So
```

Node* temp = new Node;
temp->info = val;
temp->next = 0;
...

```
In C++, you do not need to use the keyword 'struct' when declaring an object.

yea i guessed segmentation occured dude to some new function:) no it was not.
Hey when i want to declare attributes of link list like info field, link?
where do i initialize? can you just tell howto?

so i just used struct in order to define attributes.........

---

### Post by abhilashm86 on 2009-03-19
```
NODE *temp,*first,*pass;

```

mistake lies here, i din't notice to give struct

```
struct NODE *temp,*first,*pass;

```

now there is no segmentation fault:) its working fine.........

---

### Post by dwhitney67 on 2009-03-19
The following may not compile...

```

struct Node
{
  int   value;
  Node* next;
};

class List
{
  public:
    List()
      : m_head(0)
    {
    }

    virtual ~List()
    {
    }

    void insert(int value)
    {
      Node* temp  = new Node;
      temp->value = value;
      temp->next  = 0;

      if (m_head == 0)
      {
        m_head = temp;
      }
      else
      {
         ...
      }
    }

  private:
    Node*  m_head;
};

```

You can also augment struct Node with a constructor:
```

struct Node
{
  Node(int v, Node* n)
    : value(v),
      next(n)
  {
  }

  int   value;
  Node* next;
};

class List
{
  public:
    ...
    void insert(int value)
    {
      Node* temp = new Node(value, 0);

      if (m_head == 0)
      {
        ...
      }
      ...
    }
};

```

---

### Post by abhilashm86 on 2009-03-19
> **dwhitney67 said:**
> Also, since you are modeling a linked-list within a class (which btw is a good idea), your head node should be defined as a class member, not a local variable within your insert() method.  This variable should be initialized to 0 (NULL) in your List constructor.

Elements that you allocate should be freed in the destructor.

yea i get the concept, but my intention was to combine struct and class things and play with random numbers......
hey can you please tell without struct how can i declare list atributes?

---

### Post by abhilashm86 on 2009-03-19
> **dwhitney67 said:**
> The following may not compile...


oh ok, you have used header to take care of link list, but in a single link list header is not much helpfull. So when it comes to doubly link list or other, i guess it'll helpfull.......

---

### Post by dwhitney67 on 2009-03-19
> **abhilashm86 said:**
> yea i get the concept, but my intention was to combine struct and class things and play with random numbers......
hey can you please tell without struct how can i declare list atributes?

This makes no sense.  C++ is about using classes and organizing your code to be modular and self-contained --- it's the entire principle of data encapsulation.

A struct(ure) and a class are identical, with the exception that the methods/data members in a struct are, by default, publicly accessible whereas in a class they are private.

The one thing I would recommend that you do is to encapsulate the struct Node within the class List.

---

