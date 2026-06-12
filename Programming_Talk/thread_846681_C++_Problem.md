---
title: "C++ Problem"
date: 2008-07-01
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-07-01
I am writing a c++ class and i run into problems

the error comes about in the SmartList::clone() i get

> SmartList.h: In member function ‘SmartList* SmartList::clone()’:
SmartList.h:39: error: invalid lvalue in assignment
SmartList.h: In member function ‘SmartList SmartList::operator+(SmartList)’:
SmartList.h:59: error: invalid lvalue in assignment


i guess that i am not supposed to be doing

```
list[5] = &x
```

Heres the code

[PHP]class Node {
	public:
		bool link;
		void * dat;
};

class SmartList {
	private:
		int len;
		Node * n;
		Node* get(int x) {
			if (x>=len) {
				if (n[len-1].link) {
					return (*(SmartList*)n[len-1].dat).get(x-len);
				}
				return 0;
			}
			return &n[x];
		}
	public:
		SmartList() {
			len = 10;
			n = new Node[len];
		}
		SmartList(int l) {
			len = l;
			n = new Node[len];
		}
		int length() {
			if (n[len-1].link) {
				return (*(SmartList*)n[len-1].dat).length();
			}
			return len;
		}
		SmartList* clone() {
			SmartList * tmp = new SmartList(length());
			int z = length();
			for (int i=0;i<z;i++) {
				(*tmp)[i] = (*this)[i];
			}
			return tmp;
		}
		void* operator [] (int x) {
			if (x>=len) {
				if (n[len-1].link) {
					return (*(SmartList*)n[len-1].dat)[x-len];
				}
				return 0;
			}
			return n[x].dat;
		}
		SmartList operator + (SmartList l) {
			SmartList * s = clone();
			if (s->n[length()-1].dat == 0) {
				s->n[length()-1].link = true;
				s->n[length()-1].dat = &l;
			} else {
				SmartList * tmp = new SmartList(2);
				(*tmp)[0] = s->get(length()-1)->dat;
				s->get(length()-1)->link = true;
				s->get(length()-1)->dat = tmp;
				tmp->get(1)->link = true;
				tmp->get(1)->dat = &l;
			}
		}
};[/PHP]

Please, tell me what i am doing wrong or is i have any memory leak (or explain what these are), etc.

Please don't tell me that there is a better idea instead of this class, i am still in the learning stage and making this is practice!

---

### Post by SledgeHammer_999 on 2008-07-01
I didn't look to all of your code only to the "list[5] = &x"---->cannot locate it in your code.

Anywayz I assume that list[] is an array of int. When you do &x you try to assign a pointer to an int(or *int). But as far as I know list[] awaits an int. So the coorrect command should be "list[5] = x".

---

### Post by dwhitney67 on 2008-07-01
Mr. MacDonald -

Please explain what you are attempting to perform with these instructions:
[PHP](*tmp)[i] = (*this)[i];[/PHP]
and
[PHP](*tmp)[0] = s->get(length()-1)->dat;[/PHP]
I do not see anywhere in your code where the 'dat' data member of Node was set equal to an allocated space.

I have also confirmed that your "void * operator[](int x)" method is returning the address of the Node's 'dat' member, which is 0.  So essentially you are implementing code like:
[PHP]0 = 0;[/PHP]
Hence the lvalue error(s).

My "guess" is that your operator[] method should be returning the address of a Node, from which point then the dat member can be set.
For instance:
[PHP]    SmartList* clone()
    {
      SmartList * tmp = new SmartList(length());
      int z = length();
      for (int i=0;i<z;i++)
      {
        *((*tmp)[i]) = *((*this)[i]);
      }
      return tmp;
    }

    Node* operator [] (int x)   // return type modified (was void*)
    {
      if (x>=len)
      {
        if (n[len-1].link)
        {
          return (*(SmartList*)n[len-1].dat)[x-len];    // this will crash if dat not initialized
        }
        return 0;    // this could cause an application to crash too; consider throwing an exception
      }
      return n + x;   // or &n[x]
    }
    ...
    SmartList * operator + (SmartList l)   // return type modified
    {
      SmartList * s = clone();
      if (s->n[length()-1].dat == 0)
      {
        s->n[length()-1].link = true;
        s->n[length()-1].dat = &l;
      }
      else
      {
        SmartList * tmp = new SmartList(2);
        *((*tmp)[0]) = *(s->get(length()-1));
        s->get(length()-1)->link = true;
        s->get(length()-1)->dat = tmp;
        tmp->get(1)->link = true;
        tmp->get(1)->dat = &l;
      }
      return s;   // <--- this has been added; must be deleted elsewhere
    }
[/PHP]

P.S.  Do not forget to implement a virtual destructor for SmartList, that takes care of deleting 'n'. Be careful what type of data is stored in Node.  A void pointer cannot be deallocated!

---

### Post by imdano on 2008-07-01
nvm, misread something.

---

### Post by Mr.Macdonald on 2008-07-02
here is a Ascii diagram of the SmartLists idea

[PHP]
- for list members
~ for links
-------~
	    -------~
		        ---
all the dashes could be connected to be thought of as one big list
-----------------

all the ~ (links) do is hold a pointer (Node.dat is the pointer) to the next list (replaced ~ with (Next List)
List 1: -------(List 2)
List 2: 	          -------(List 3)
List 3: 		                    ---
[/PHP]

The Node is supposed to be hidden from the user. if i gave the user a node and they changed the link, then ... their program could crash. all is does is hold either data for a pointer to another SmartList based upon the Node.link value

in my class both data and links are called Nodes, only the Links have Node.link = true
when you provide an index (ie list[23]) my class then if the index is greater than the current list (List 1)
then it trys to go to the last Node in the array to check if it is a link (Node.link == true)
if so then it goes to the list the link points to and tries to get the value at list2[index-list1.len]

after if find the appropriate Node (the one at the right index) it returns node.dat
which is a void* so to accomidate to all data types (generic data)

[PHP]
the goal of

(*tmp)[i] = (*this)[i];

is the way to set values to items in the array just as

int * a = new int[5];
a[2] = 1023;

sets values in an array

i want to be able to do this

SmartList b (23);
int tmp = 50;
b[15] = &tmp;
[/PHP]


[PHP]
This is the same as above just another way
(*tmp)[0] = s->get(length()-1)->dat;
Should be equivalant to
(*tmp)[0] = s->[length()-1];
but i didn't no if s->[] was legal so i played it safe
[/PHP]





> P.S. Do not forget to implement a virtual destructor for SmartList, that takes care of deleting 'n'. Be careful what type of data is stored in Node. A void pointer cannot be deallocated!

what does deallocation mean.

Thank You for responding (technical responses come slow)

---

### Post by jim_24601 on 2008-07-02
I see where you're going with this void pointer thing--the user of the SmartList class is entirely responsible for the data that goes into it, and the class itself doesn't care about the value at all. There are better ways of handling this, but you get into hairy subjects like generics, and we're not critiquing the class. Having said that, your approach is leading you into problems, as you've seen.

Deallocation is simply the opposite of allocation. We use deallocate, delete and free pretty much interchangeably when talking about memory in general. (But don't confuse the delete operator and the free() function.)

You aren't initialising your nodes in SmartList's constructor, so you might get anything in them--this could be a problem if the last node happens to look like a link to another list, but in fact isn't. Your program will then crash. Either initialise them explicitly or give Node a default constructor.

That was an aside. Now on to the meat of your problem. The basic idea of the clone() method is sound--create a new object and copy the existing stuff into it. You've tripped over a detail.

An lvalue, in computer science, means "something that can appear on the left hand of an assignment". It's anything you can assign a value to--naturally we also talk about rvalues, which are things you can get a value from that you use in an assignment. Unless your native language is Hebrew or Arabic, that should be straightforward.

The compiler is complaining that what you're trying to use as an lvalue, i.e. the thing on the left side of the '=', isn't really one. The offending line is

```
(*tmp)[i] = (*this)[i];
```

but that's not how the compiler sees it. You've defined an operator[](), so your code is equivalent to

```
tmp->operator[](i) = this->operator[](i);
```

Your operator[] has return type void*, so it's returning a pointer by value. This is actually quite a subtle point, but the gist of it is that you can't assign to the return value, because it's meaningless. What does it mean to assign to the result of a function? It would be like rewriting history to claim that the function had returned something different.

There's a distinction here between the value of a pointer and the thing it points at, and I'm hammering the point rather because it's something that a lot of people have serious trouble with. If instead you'd had

```
int f(int x) { return x + 1; }
f(1) = 1;
```

it would have been obvious straight away what the problem was. As far as the compiler's concerned, though, that's exactly what you're trying to do here.

This should tell you that you've got something wrong in your definition of operator[], since we expect to be able to assign to the result--we expect it to be an lvalue, in computer science terms. The solution, to which I'm gradually coming round, is for operator[] to return by reference:

```
void*& operator[] (int x) { ... }
```

There is no distinction, as far as the programmer is concerned, between a reference and the thing it refers to, so you can happily assign to it even if it's just popped out of a function.

There's another problem lurking to trip you up, but we'll discuss that in due course.

---

### Post by dwhitney67 on 2008-07-02
McDonald -
I massaged your code; got it to work.  I'm not sure if this meets your needs.

Here it is:
[PHP]#include <iostream>
#include <iomanip>


struct Node
{
  bool  link;
  void *dat;

  Node()
  {
    link = false;
    dat  = 0;
  }

  friend std::ostream & operator<<( std::ostream &os, const Node &node )
  {
    os << "link = " << (node.link ? "true " : "false")
       << "\tdat = " << node.dat;
    return os;
  }
};



class SmartList
{
  public:
    SmartList( size_t length = 10 )
    {
      m_length = length;
      m_node   = new Node[ m_length ];
    }

    virtual ~SmartList()
    {
      while ( (*this)[ m_length - 1 ].link == true )
      {
        reinterpret_cast<SmartList*>((*this)[ m_length - 1 ].dat)->~SmartList();

        (*this)[ m_length - 1 ].link = false;
        (*this)[ m_length - 1 ].dat  = 0;
      }

      delete []m_node;
    }

    size_t getLength() const
    {
      if ( m_node[ m_length - 1 ].link == true )
      {
        return m_length + reinterpret_cast<SmartList*>((*this)[ m_length - 1 ].dat)->getLength();
      }

      return m_length;
    }

    Node & operator[]( size_t index ) const
    {
      if ( index >= m_length )
      {
        SmartList *tmp = reinterpret_cast<SmartList*>((*this)[ m_length - 1 ].dat);

        return (*tmp)[ index - m_length ];
      }

      return m_node[ index ];
    }

    SmartList * clone()
    {
      const size_t len = m_length;

      SmartList *tmp = new SmartList( len );

      for ( size_t i = 0; i < len; ++i )
      {
        tmp->m_node[i] = this->m_node[i];
      }

      if ( (*this)[ len - 1 ].link == true )
      {
        (*tmp)[ len - 1 ].dat = reinterpret_cast<SmartList*>((*this)[ len - 1 ].dat)->clone();
      }

      return tmp;
    }

    SmartList * operator+( SmartList &list )
    {
      SmartList *tmp = this->clone();

      *tmp += list;

      return tmp;
    }

    SmartList & operator+=( SmartList &list )
    {
      if ( (*this)[ m_length - 1 ].link == false )
      {
        // Add a clone of the list to the end
        m_node[ m_length - 1 ].dat  = list.clone();
        m_node[ m_length - 1 ].link = true;
      }
      else
      {
        // search for the last node of the Smart List
        SmartList *next = reinterpret_cast<SmartList*>((*this)[ m_length - 1 ].dat);

        while ( (*next)[ next->m_length - 1 ].link != false )
        {
          next = reinterpret_cast<SmartList*>((*next)[ next->m_length - 1].dat);
        }

        // Add a clone to the last node in the list
        (*next)[ next->m_length - 1 ].dat  = list.clone();
        (*next)[ next->m_length - 1 ].link = true;
      }

      return *this;
    }

    friend std::ostream & operator<<( std::ostream &os, const SmartList &list )
    {
      const size_t len = list.getLength();

      for ( size_t i = 0; i < len; ++i )
      {
        os << "Node[" << std::setw(2) << i << "]   " << list[i] << std::endl;
      }

      return os;
  }

  private:
    size_t  m_length;
    Node *  m_node;

    // Defined, but not implemented
    SmartList( const SmartList & );
    SmartList operator=( const SmartList & );
};


int main()
{
  SmartList list_one;
  SmartList list_two(20);
  SmartList list_three;

  std::cout << "list_one.getLength()   = " << list_one.getLength()   << std::endl;
  std::cout << "list_two.getLength()   = " << list_two.getLength()   << std::endl;
  std::cout << "list_three.getLength() = " << list_three.getLength() << std::endl << std::endl;


  std::cout << "list_one += list_two..." << std::endl;
  list_one += list_two;
  std::cout << "list_one.getLength() = " << list_one.getLength() << std::endl;
  std::cout << "list_two.getLength() = " << list_two.getLength() << std::endl << std::endl;


  std::cout << "list_one += list_three..." << std::endl;
  list_one += list_three;
  std::cout << "list_one.getLength() = " << list_one.getLength() << std::endl;
  std::cout << "list_two.getLength() = " << list_two.getLength() << std::endl << std::endl;


  std::cout << "Node info for list_one:" << std::endl;
  std::cout << list_one << std::endl;

  std::cout << "Creating a clone of list_one..." << std::endl;
  SmartList *clone = list_one.clone();
  std::cout << "clone->getLength() = " << clone->getLength()   << std::endl << std::endl;
  std::cout << "Node info for clone:" << std::endl;
  std::cout << *clone << std::endl;
  delete clone;

  std::cout << "list_four = list_two + list_three..." << std::endl;
  SmartList *list_four = list_two + list_three;
  std::cout << "list_four->getLength() = " << list_four->getLength() << std::endl;
  std::cout << "Node info for list_four:" << std::endl;
  std::cout << *list_four << std::endl;
  delete list_four;

  return 0;
}[/PHP]

---

### Post by jim_24601 on 2008-07-02
> **dwhitney67 said:**
> 
I massaged your code; got it to work.  I'm not sure if this meets your needs.


> **Mr.Macdonald said:**
> 
The Node is supposed to be hidden from the user.


Your version has a memory leak in the destructor. (And the destructor makes the class needlessly polymorphic, imho.)

operator+ should return a temp object by value, not a pointer. (It should also take its parameter by const reference.) Although returning copies by value is problematic with all these clones floating about, and I'd be inclined to disallow operator+ entirely. I suspect the OP intended to implement operator+= and typoed it.

---

### Post by Mr.Macdonald on 2008-07-02
> 
You aren't initializing your nodes in SmartList's constructor, so you might get anything in them--this could be a problem if the last node happens to look like a link to another list, but in fact isn't. Your program will then crash. Either initialize them explicitly or give Node a default constructor.

I believe (not sure) that the Nodes members automatically are set to
[INDENT]
void * dat = 0
bool link = false
[/INDENT]
which is what i want



> 
This should tell you that you've got something wrong in your definition of operator[], since we expect to be able to assign to the result--we expect it to be an lvalue, in computer science terms. The solution, to which I'm gradually coming round, is for operator[] to return by reference:

```

void*& operator[] (int x) { ... }
```

There is no distinction, as far as the programmer is concerned, between a reference and the thing it refers to, so you can happily assign to it even if it's just popped out of a function.

There's another problem lurking to trip you up, but we'll discuss that in due course. 


I think i may have found the problem


SmartList.h
[PHP]class Node {
	public:
		bool link;
		void * dat;
};

class SmartList {
	private:
		int len;
		Node * n;
		Node* get(int x) {
			if (x>=len) {
				if (n[len-1].link) {
					return (*(SmartList*)n[len-1].dat).get(x-len);
				}
				return 0;
			}
			return &n[x];
		}
	public:
		SmartList(int l) {
			len = l;
			n = new Node[len];
		}
		int length() {
			if (n[len-1].link) {
				return (*(SmartList*)n[len-1].dat).length();
			}
			return len;
		}
		SmartList* clone() {
			SmartList * tmp = new SmartList(length());
			int z = length();
			for (int i=0;i<z;i++) {
				(*tmp)[i] = (*this)[i];
			}
			return tmp;
		}
		void*& operator [] (int x) {
			if (x>=len) {
				if (n[len-1].link) {
					return (*(SmartList*)n[len-1].dat)[x-len];
				}
				return 0;
			}
			
			return n[x].dat;
		}
		SmartList operator + (SmartList l) {
			SmartList * s = clone();
			if (s->n[length()-1].dat == 0) {
				s->n[length()-1].link = true;
				s->n[length()-1].dat = &l;
			} else {
				SmartList * tmp = new SmartList(2);
				(*tmp)[0] = s->get(length()-1)->dat;
				s->get(length()-1)->link = true;
				s->get(length()-1)->dat = tmp;
				tmp->get(1)->link = true;
				tmp->get(1)->dat = &l;
			}
		}
};[/PHP]

My tester file
[PHP]#include <iostream>
#include "SmartList.h" 

int main(void) {
	SmartList s (5);
	int * tmp = new int(23);
	s[1] = tmp;
	
	std::cout << s[1] << std::endl;
	
	return s[1];
}[/PHP]

when i compiler the test.cc
```
g++ test.cc -o test
```
i get
```
SmartList.h: In member function ‘void*& SmartList::operator[](int)’:
SmartList.h:44: error: invalid initialization of non-const reference of type ‘void*&’ from a temporary of type ‘int’
test.cc: In function ‘int main()’:
test.cc:11: error: invalid conversion from ‘void*’ to ‘int’

```

I have no idea what this means. So do you think i should just make functions to replace the operator[] idea??

---

### Post by dwhitney67 on 2008-07-02
The memory leak can be corrected by adding a destructor to Node, however the compiler will output a warning that deleting a void pointer may produce unexpected results (perhaps a memory leak?).

There are also other issues:
[PHP]Smartlist smartList;
int value = 5;

smartList[0] = &value;      // this is NOT safe to do
smartList[1] = new int(5);  // safe; pointer will be deleted by Node destructor (or will it??)
[/PHP]

Btw, here's the updated SmartList code, thus ensuring that Node cannot be accessed, and that (hopefully) its contents are properly destroyed:
[PHP]
#include <stdexcept>
#include <iostream>
#include <iomanip>


class SmartList
{
  public:
    SmartList( size_t length = 10 )
    {
      m_length = length;
      m_node   = new Node[ m_length ];
    }

    ~SmartList()
    {
      while ( m_node[ m_length - 1 ].link == true )
      {
        delete reinterpret_cast<SmartList*>((*this)[ m_length - 1 ]);

        m_node[ m_length - 1 ].link = false;
        m_node[ m_length - 1 ].dat  = 0;
      }

      delete []m_node;
    }

    size_t getLength() const
    {
      if ( m_node[ m_length - 1 ].link == true )
      {
        return m_length + reinterpret_cast<SmartList*>((*this)[ m_length - 1 ])->getLength();
      }

      return m_length;
    }

    void *& operator[]( size_t index ) const
    {
      if ( index >= m_length )
      {
        SmartList *tmp = reinterpret_cast<SmartList*>(m_node[ m_length - 1 ].dat);

        if ( tmp == 0 )
        {
          throw std::range_error("index out of range.");
        }

        return (*tmp)[ index - m_length ];
      }

      return m_node[ index ].dat;
    }

    SmartList * clone() const
    {
      const size_t len = m_length;

      SmartList *tmp = new SmartList( len );

      for ( size_t i = 0; i < len; ++i )
      {
        tmp->m_node[i] = this->m_node[i];
      }

      if ( m_node[ len - 1 ].link == true )
      {
        (*tmp)[ len - 1 ] = reinterpret_cast<SmartList*>(m_node[ len - 1 ].dat)->clone();
      }

      return tmp;
    }

    SmartList * operator+( const SmartList &list )
    {
      SmartList *tmp = this->clone();

      *tmp += list;

      return tmp;
    }

    SmartList & operator+=( const SmartList &list )
    {
      if ( m_node[ m_length - 1 ].link == false )
      {
        // Add a clone of the list to the end
        m_node[ m_length - 1 ].dat  = list.clone();
        m_node[ m_length - 1 ].link = true;
      }
      else
      {
        // search for the last node of the Smart List
        SmartList *next = reinterpret_cast<SmartList*>((*this)[ m_length - 1 ]);

        while ( next->m_node[ next->m_length - 1 ].link != false )
        {
          next = reinterpret_cast<SmartList*>(next->m_node[ next->m_length - 1].dat);
        }

        // Add a clone to the last node in the list
        next->m_node[ next->m_length - 1 ].dat  = list.clone();
        next->m_node[ next->m_length - 1 ].link = true;
      }

      return *this;
    }

    friend std::ostream & operator<<( std::ostream &os, const SmartList &list )
    {
      const size_t len = list.getLength();

      for ( size_t i = 0; i < len; ++i )
      {
        os << "Node[" << std::setw(2) << i << "]   " << list[i] << std::endl;
      }

      return os;
  }

  private:
    struct Node
    {
      bool  link;
      void *dat;

      Node()
      {
        link = false;
        dat  = 0;
      }

      ~Node()
      {
        if (dat) delete []dat;
      }

      friend std::ostream & operator<<( std::ostream &os, const Node &node )
      {
        os << "link = " << (node.link ? "true " : "false")
           << "\tdat = " << node.dat;
        return os;
      }
    };

    size_t  m_length;
    Node *  m_node;

    // Defined, but not implemented
    SmartList( const SmartList & );
    SmartList operator=( const SmartList & );
};


int main()
{
  SmartList list_one;
  SmartList list_two(20);
  SmartList list_three;

  std::cout << "list_one.getLength()   = " << list_one.getLength()   << std::endl;
  std::cout << "list_two.getLength()   = " << list_two.getLength()   << std::endl;
  std::cout << "list_three.getLength() = " << list_three.getLength() << std::endl << std::endl;


  std::cout << "list_one += list_two..." << std::endl;
  list_one += list_two;
  std::cout << "list_one.getLength() = " << list_one.getLength() << std::endl;
  std::cout << "list_two.getLength() = " << list_two.getLength() << std::endl << std::endl;


  std::cout << "list_one += list_three..." << std::endl;
  list_one += list_three;
  std::cout << "list_one.getLength()   = " << list_one.getLength()   << std::endl;
  std::cout << "list_three.getLength() = " << list_three.getLength() << std::endl << std::endl;


  std::cout << "Node info for list_one:" << std::endl;
  std::cout << list_one << std::endl;

  std::cout << "Creating a clone of list_one..." << std::endl;
  SmartList *clone = list_one.clone();
  std::cout << "clone->getLength() = " << clone->getLength()   << std::endl << std::endl;
  std::cout << "Node info for clone:" << std::endl;
  std::cout << *clone << std::endl;
  delete clone;

  std::cout << "list_four = list_two + list_three..." << std::endl;
  SmartList *list_four = list_two + list_three;
  std::cout << "list_four->getLength() = " << list_four->getLength() << std::endl;
  std::cout << "Node info for list_four:" << std::endl;
  std::cout << *list_four << std::endl;
  delete list_four;

  return 0;
}[/PHP]

---

### Post by jim_24601 on 2008-07-02
> **Mr.Macdonald said:**
> I believe (not sure) that the Nodes members automatically are set to
[INDENT]
void * dat = 0
bool link = false
[/INDENT]
which is what i want


Unfortunately, not in C++. The programmer (you) is responsible for initialising all variables.

> ```
SmartList.h: In member function ‘void*& SmartList::operator[](int)’:
SmartList.h:44: error: invalid initialization of non-const reference of type ‘void*&’ from a temporary of type ‘int’
test.cc: In function ‘int main()’:
test.cc:11: error: invalid conversion from ‘void*’ to ‘int’

```

I have no idea what this means. So do you think i should just make functions to replace the operator[] idea??

The operator[] bit is fine. Functions won't help you, because you've already got functions. All the various operators do is let users of the class use more convenient syntax for accessing it. If you've got a class that "acts like" an array, it's convenient to use [] notation rather than have to use a function.

The problem that I evilly left for you to find yourself is really the same problem of not distinguishing between a pointer and the thing it points to, or in this case a node and the pointer it contains. Your original code returned a null pointer if it didn't have a node at the index it was given. But you're not returning a pointer to the node, you're returning its contents, and the user of your SmartList can store anything it wants there, including nothing at all. So if operator[] returns a null pointer, does it mean that the user referenced a valid but empty node, or no node at all? There's no way of telling.

But now we're returning a reference to the node's contents, things are even worse. The user expects to be able to write to the reference he gets back, but there's nothing there. How do you make a reference to nothing? Well, you can't, at least not in C++. That's what the compiler is telling you. You can't return a writeable reference to null, because you can't change the value of null. (Well, maybe in FORTRAN.)

The language itself handles this problem by not handling it. If you have

```
int a[10];
```

what is the value of a[11]? The language doesn't define it. It effectively says, if you (the programmer) are foolish enough to try to access past the end of an array, you deserve everything that's coming to you. If you're lucky, your program will crash. If you're unlucky, you'll get a subtle bug that takes weeks to find. (Trust me, I **know** this.)

But as a responsible programmer who doesn't want users of your class to experience random crashes and hard-to-find bugs, what can you do about it? You can't return a null reference, because there's no such thing. You could
[LIST=1]
[*]Instead of a reference to the node contents, return a pointer to it (a void**). Then you could return a null pointer if there was no node. But you'd have to check the result of operator[] wasn't null each time you used it, and then dereference the pointer. It breaks the list-like behaviour you're looking for.
[*]Return a reference to some random point off the end of the array. Believe it or not, the standard vector container does exactly this if you use its operator[] to access a non-existent member. Not recommended, though.
[*]Throw an exception instead.
[/LIST]

Option (3) is my recommendation. Since dwhitney67 has already posted an example of it, I shan't waffle on further about it. You know about exceptions, right?

---

### Post by jim_24601 on 2008-07-02
> **dwhitney67 said:**
> The memory leak can be corrected by adding a destructor to Node, however the compiler will output a warning that deleting a void pointer may produce unexpected results (perhaps a memory leak?).


That would only work if the SmartList took ownership of the data that was put into it--which I assume that it doesn't (it would, as you say, be an extremely bad idea, since the list doesn't know what the data is and can't safely delete it.)

The list does own the sub-list(s) pointed at by the 'link' nodes, and should delete these. Since it knows that they're actually SmartLists, it can safely cast them to SmartList* and use delete. Your previous example only called the destructor and left the memory lying about undeleted.

If you add a destructor to Node, it must **only** delete the 'dat' pointer if it is a link node:

```

Node::~Node()
{
  if (link)
  {
    SmartList* sublist = static_cast<SmartList*>(dat);
    delete sublist;
  }
}

```

And lose the explicit destructor call in the SmartList destructor.

---

### Post by dwhitney67 on 2008-07-02
> **jim_24601 said:**
> That would only work if the SmartList took ownership of the data that was put into it--which I assume that it doesn't (it would, as you say, be an extremely bad idea, since the list doesn't know what the data is and can't safely delete it.)

The list does own the sub-list(s) pointed at by the 'link' nodes, and should delete these. Since it knows that they're actually SmartLists, it can safely cast them to SmartList* and use delete. Your previous example only called the destructor and left the memory lying about undeleted.
[snip]

Basically you're saying that SmartList ought to hold the pointers, and it is up to the application the manage all memory deallocations, not the SmartList.  Seems like an awful mess in the makings.

As for the destructor I wrote, it does deallocate properly.  I uses recursion to ensure that all of the nodes and the sub-lists are deleted, starting from the end (i.e. the last sub-list) and working it's way back to the primary list.   I have ran the destructor through the debugger and noticed that the final statement in the destructor was called for each SmartList (whether primary or sub-list).

P.S.  I disagree with you concerning the Node destructor example you showed.  The Node class should not have any knowledge of what type of data is being held within it.  It is a "servant" class; the SmartList is the "master", and thus holds the context of how the Node class is being used.

---

### Post by Mr.Macdonald on 2008-07-02
(Below is based on my Java experiences)
About throwing an exception (i do know how to), the problem is that the user would have to try-catch all their code. is their a way to throw an exception without the user needing to try-catch the function.


From what i have seen the void* kind of ruins everything. Is their a generic data type ... or do i need to make a template (i REALLY don't want to).

i will make a template if needed but i would rather use a generic data type.

---

### Post by dwhitney67 on 2008-07-03
Throwing an exception is easy; the user can elect to catch a thrown exception or not.  If the latter, and an exception is thrown, the user's program will crash (terminate).  It's probably for the best since the user gave invalid data to the object that threw the exception.

So in the case of the SmartList, if a user creates one (which I believe defaults to 10 nodes during initialization) and then attempts to assign to position 1000, well that should throw an exception.  It's the user's fault for providing an array index way out of bounds.

With respect to the void*, the SmartList has it's load of issues.  For one, it cannot be responsible for memory management of the data stored within it.  It would not know how to properly deallocate memory, or even if it is necessary to deallocate it.  Here are some wild examples:
[PHP]SmartList smart;
int localInteger = 2;

smart[0] = new int(10);        // single int, initialized to 10
smart[1] = &localInteger;      // address of local variable
smart[2] = new int[5];         // array allocation
smart[3] = new ComplexClass;   // some complex class object
...[/PHP]
The only way to ensure proper clean-up of the allocated memory shown above would be for the user's application, which instantiated the SmartList, to deallocate (delete) each of the objects that were allocated.  In the example above, that would be impossible because 'handles' were not assigned to the memory that was allocated.  The proper way would be:
[PHP]
SmartList smart;
int *allocInt = new int(10);
smart[0] = allocInt;
...
delete allocInt;     // this should not occur until the use of SmartList is over
[/PHP]
As for using templates, that would be nice, however bear in mind that it would tie your SmartList into storing only one type of object, as specified by the user.  In such case, the SmartList would be able to manage the objects stored within it, such that eventually they could be deleted.

Anyhow, hopefully by now you understand that the SmartList is far from being "smart".  Sure it's a nice comp-sci exercise, but in the real world, it would be hard to find a need for such a beast.

---

### Post by jim_24601 on 2008-07-03
> **Mr.Macdonald said:**
> (Below is based on my Java experiences)

Well, that explains why you're having trouble with pointers ;)

> About throwing an exception (i do know how to), the problem is that the user would have to try-catch all their code. is their a way to throw an exception without the user needing to try-catch the function.

Yes--just throw the exception and let the user worry about whether to catch it.

Seriously, exceptions are a much better mechanism for error handling than returning a success/fail value, precisely because you *don't* have to wrap every function call in a try/catch block. There's a rule that's usually presented as a joke but has a kernel of truth--"Don't check for an error condition you don't know how to handle." If the user is expecting to attempt to access nonexistent list members, and considers this recoverable, by all means let him catch the exception. (It's a pretty sloppy way to work, though.) If the user isn't expecting to hit any nonexistent members, then the exception reveals a bug in the program, so the *program* can't handle it--let the exception go, and the program terminate, and then find and fix the bug.

Much better than the success/fail case, where the caller is *forced* to check every time, or risk a hard-to-diagnose crash.

> 
From what i have seen the void* kind of ruins everything.


Ah, grasshopper, now you begin to understand.

> Is their a generic data type ... or do i need to make a template (i REALLY don't want to).


There is no generic data type in C++ (well, there sort of is, but it's called a void pointer). Templates aren't really as scarey as all that (well, they can be, but not if you don't want them to be).

---

### Post by jim_24601 on 2008-07-03
> **dwhitney67 said:**
> 
As for the destructor I wrote, it does deallocate properly.  I uses recursion to ensure that all of the nodes and the sub-lists are deleted, starting from the end (i.e. the last sub-list) and working it's way back to the primary list.   I have ran the destructor through the debugger and noticed that the final statement in the destructor was called for each SmartList (whether primary or sub-list).


It does not. It destroys the object, but the memory it previously occupied remains allocated. Calling a destructor does not imply freeing its memory, or how would you destroy auto and temporary objects?

> 
P.S.  I disagree with you concerning the Node destructor example you showed.  The Node class should not have any knowledge of what type of data is being held within it.  It is a "servant" class; the SmartList is the "master", and thus holds the context of how the Node class is being used.

But then you get a sort of hybrid between a class and a struct. (I'm aware these are the same thing modulo default access, but I'm talking as they are usually used.) If it's a class, make it responsible for its members, and have it delete the linked sub-list if it is a link node. If it's a struct, make the SmartList responsible for initialising and destroying it.

---

### Post by jim_24601 on 2008-07-03
> **dwhitney67 said:**
> Throwing an exception is easy; the user can elect to catch a thrown exception or not.  If the latter, and an exception is thrown, the user's program will crash (terminate).  It's probably for the best since the user gave invalid data to the object that threw the exception.

So in the case of the SmartList, if a user creates one (which I believe defaults to 10 nodes during initialization) and then attempts to assign to position 1000, well that should throw an exception.  It's the user's fault for providing an array index way out of bounds.

With respect to the void*, the SmartList has it's load of issues.  For one, it cannot be responsible for memory management of the data stored within it.  It would not know how to properly deallocate memory, or even if it is necessary to deallocate it.  

We seem to be in agreement here.

> The only way to ensure proper clean-up of the allocated memory shown above would be for the user's application, which instantiated the SmartList, to deallocate (delete) each of the objects that were allocated.  In the example above, that would be impossible because 'handles' were not assigned to the memory that was allocated.

The way the SmartList class is presented here, the user is entirely responsible for managing the objects stored in it, including keeping track of what they are and where they came from, if it wants to mix object types and storage classes. But it doesn't have to store the objects separately--it can quite well say

```
smart[0] = new int[10];
...
delete [] smart[0];
smart[0] = NULL;
```

for example.

> Anyhow, hopefully by now you understand that the SmartList is far from being "smart".  Sure it's a nice comp-sci exercise, but in the real world, it would be hard to find a need for such a beast.

It's an excellent excercise. I shouldn't say, though, that such a beast is particularly rare in the "real world". Make it a template and add functions for growing down as well as up, and you've pretty much got a std::deque.

---

