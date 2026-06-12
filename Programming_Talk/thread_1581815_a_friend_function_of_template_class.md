---
title: "a friend function of template class"
date: 2010-09-25
forum: Programming Talk
---

### Post by kingkong22 on 2010-09-25
I have a question about a friend function of template class. Since Code
has worked well through g++3.3.4 to g++4.2.4 in ubuntu. But Code chokes
in g++4.3.3 in ubuntu. snippet code as follows:

template<class T, class A, class P>  class List {
 //...
 friend class List<T,A,P>::iterator;  // Line 410 <<<<<<
 //...
};

I used g++4.3.3, it generated errors in Line 410

>error: use typedef name 'List<T,A,P>::iterator. 
>error: friend declaration has no name of class or function

since Code run through g++3.3.4 ~g++4.2.4, I don't know why it
breaks in g++4.3.3 ?  What is the correct syntax for g++4.3.3 ?
Does an expert have any idea to fix it ? thanks in advance.

---

### Post by GeneralZod on 2010-09-25
Can you post more code, specifically any and all instantiations of List? As given, the snippet compiles fine under my copy of 4.3.3.

Edit:

A reduced but fully compilable snippet that demonstrates the error would be best.

---

### Post by kingkong22 on 2010-09-25
Hi GeneralZod, 
Below is the snippet code that generates the error message:
```


#include <iterator>
struct pallocator {};

template<class C, class T> struct pstl_serialize_traits {};

template <class A>
struct __plist_node {
};

template <class T, class A=pallocator, class Tr=pstl_serialize_traits<T,A> >
class plist;

template <class C, class CPtr, class Ref> struct __plist_iterator {
  typedef __plist_iterator<C, CPtr, Ref> self;

  typedef C container_type;
  typedef typename container_type::value_type value_type;
  typedef typename container_type::allocator_type allocator_type;
  typedef typename container_type::serializer_type serializer_type;

  typedef typename container_type::iterator iterator;
  typedef typename container_type::const_iterator const_iterator;

  typedef typename container_type::size_type size_type;
  typedef typename container_type::difference_type difference_type;
  typedef typename container_type::offset_type offset_type;

  typedef Ref reference;
  typedef value_type *pointer;

  typedef __plist_node<allocator_type> link_type;
};

template <class T, class A, class Tr> class plist {
public:

  typedef plist<T, A, Tr> self;

  typedef T value_type;
  typedef A allocator_type;
  typedef Tr serializer_type;

  typedef typename A::size_type size_type;
  typedef typename A::difference_type difference_type;

  typedef typename serializer_type::reference reference;
  typedef typename serializer_type::const_reference const_reference;

  typedef __plist_iterator<self, self*, reference> iterator;    //<<<<<<< Line 49
  typedef __plist_iterator<self, const self*, const_reference> const_iterator;

  typedef __plist_node<A> link_type;

protected:
                                                                         
  allocator_type alloc;
  serializer_type serialize;

  typedef typename A::offset_type offset_type;

public:
  /**Ctors**/

  friend class plist<T,A,Tr>::iterator;  //<<<<<<<< Line 63

  //friend class plist<T,A,Tr>::const_iterator;   // same as above !
};

int main() {}

```

---

### Post by kingkong22 on 2010-09-25
#include <iterator>
struct pallocator {};

template<class C, class T> struct pstl_serialize_traits {};

template <class A>
struct __plist_node {
};

template <class T, class A=pallocator, class Tr=pstl_serialize_traits<T,A> >
class plist;

template <class C, class CPtr, class Ref> struct __plist_iterator {
  typedef __plist_iterator<C, CPtr, Ref> self;

  typedef C container_type;
  typedef typename container_type::value_type value_type;
  typedef typename container_type::allocator_type allocator_type;
  typedef typename container_type::serializer_type serializer_type;

  typedef typename container_type::iterator iterator;
  typedef typename container_type::const_iterator const_iterator;

  typedef typename container_type::size_type size_type;
  typedef typename container_type::difference_type difference_type;
  typedef typename container_type::offset_type offset_type;

  typedef Ref reference;
  typedef value_type *pointer;

  typedef __plist_node<allocator_type> link_type;
};

template <class T, class A, class Tr> class plist {
public:
  typedef plist<T, A, Tr> self;

  typedef T value_type;
  typedef A allocator_type;
  typedef Tr serializer_type;

  typedef typename A::size_type size_type;
  typedef typename A::difference_type difference_type;

  typedef typename serializer_type::reference reference;
  typedef typename serializer_type::const_reference const_reference;
  typedef __plist_iterator<self, self*, reference> iterator;    //<<<<<<< Line 49
  typedef __plist_iterator<self, const self*, const_reference> const_iterator;

  typedef __plist_node<A> link_type;

protected:
  allocator_type alloc;
  serializer_type serialize;

  typedef typename A::offset_type offset_type;

public:
  /**Ctors**/

  friend class plist<T,A,Tr>::iterator;  //<<<<<<<< Line 63

  //friend class plist<T,A,Tr>::const_iterator;   // same as above !
};

int main() {}


Sorry for the previous post ! This time seems ok ! Thank you so much !!

---

### Post by lisati on 2010-09-25
> **kingkong22 said:**
> 
Sorry for the previous post ! This time seems ok ! Thank you so much !!

I've done what I can..... and don't be scare of the [noparse]```
 and 
```[/noparse] tags - it can help make code snippets easier to manage.

---

### Post by kingkong22 on 2010-09-25
Thank you, lisati !

---

### Post by GeneralZod on 2010-09-25
This might shed some light on the matter:

[http://stackoverflow.com/questions/392120/why-cant-i-declare-a-friend-through-a-typedef](http://stackoverflow.com/questions/392120/why-cant-i-declare-a-friend-through-a-typedef)

---

### Post by kingkong22 on 2010-09-25
Back to my question, I have tried many combinations, but still not work.
How about you ? Dear GeneralZod ?

---

### Post by dwhitney67 on 2010-09-25
I suspect that you have not provided all the necessary code, which would be helpful to troubleshoot this issue.  In other words, it would be helpful to see how the __plist_iterator is accessing the protected/private data of plist, and to assess whether it is really necessary.

I tried changing the "friend" declarations you have to the following, and the code compiles.  But I'm not sure whether this is what you require or not.
```

template <class T, class A, class Tr> class plist {
   ...
public:
  friend class __plist_iterator<self, self*, reference>;
  friend class __plist_iterator<self, const self*, reference>;
};

```

---

### Post by kingkong22 on 2010-09-27
Thank you ! dwhitney67. 
It is a very good solution ! thanks again.

---

