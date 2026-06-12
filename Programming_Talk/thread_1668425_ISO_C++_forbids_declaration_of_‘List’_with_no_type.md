---
title: "ISO C++ forbids declaration of ‘List’ with no type"
date: 2011-01-16
forum: Programming Talk
---

### Post by abel abadi on 2011-01-16
**I use g++ compiler for my c++ programming**! And i keep getting this error

hashtbl.h:21: error: ISO C++ forbids declaration of ‘List’ with no type
hashtbl.h:21: error: expected ‘;’ before ‘<’ token
hashtbl.cpp: In constructor ‘HashTbl<DT, KF>::HashTbl(int)’:
hashtbl.cpp:11: error: ‘dataTable’ was not declared in this scope


here is some part of my program:
------------------------------------hashtbl.h
template < class DT, class KF >
class HashTbl
{
    public:
        HashTbl ( int initTableSize );
        ~HashTbl ();
-------------------hashtbl.cpp
#include<iostream>
#include <new>

#include "hashtbl.h"
#include "listlnk.cpp"
using namespace std;


template < class DT, class KF >

HashTbl<DT,KF>:: HashTbl ( int initTableSize )

{
	tableSize=initTableSize;
	dataTable = new List<DT>[tableSize];

}
-------------------------linklis.h
template < class DT >         // Forward declaration of the List class

class List;



template < class DT >

class ListNode                // Facilitator class for the List class

{

  private:



    // Constructor
-----------------------------linklis.cpp
#include <iostream>

#include "listlnk.h"

#include <new>

using namespace std;



//--------------------------------------------------------------------



template < class DT >

ListNode<DT>:: ListNode ( const DT &nodeDataItem, ListNode<DT> *nextPtr )



// Creates a list node containing item elem and next pointer

// nextPtr.


please anybody help me out!
with regards!

---

### Post by MadCow108 on 2011-01-16
yipee another thread about this:
you can't declare templates in the cpp file. they need to be completely defined in the header.
[http://www.parashift.com/c++-faq-lite/templates.html#faq-35.12](http://www.parashift.com/c++-faq-lite/templates.html#faq-35.12)

also I think you need to add a typename to the template parameter:
dataTable = new List<typename DT>[tableSize];

---

### Post by worksofcraft on 2011-01-16
noh oops I hadn't read it properly... never mind

---

