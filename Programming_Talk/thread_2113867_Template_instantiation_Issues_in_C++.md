---
title: "Template instantiation Issues in C++"
date: 2013-02-08
forum: Programming Talk
---

### Post by dany2704 on 2013-02-08
I am using library file Slist.h which has template declaration and definition.The library file is instantiated in the construtor 
of mypgm.c(cpp file).The compiler throws an error which is mentioned at the bottom.

**Slist.h**
template <class Object> 
class SList;     // fwd declaration. 
template <class Object> 
class SListItr;  // fwd declaration. 
template <class Object> 
class SListNode 
{ 
    SListNode( const Object &theElement = Object( ), 
               SListNode *n = NULL ) 
      : element( theElement ), next( n ) { } 
 
    Object     element; 
    SListNode *next; 
    friend class SList<Object>; 
    friend class SListItr<Object>; 
}; 
 
template <class Object> 
class SList 
{ 
  public: 
    SList( ); 
    SList( const SList &rhs ); 
    ~SList( ); 
    int isEmpty( ) const; 
    void makeEmpty( ); 
    SListItr<Object> zeroth( ) const; 
    SListItr<Object> first( ) const; 
    const SList & operator=(  SList &rhs ); 
    int  IsType() {return LinkedListType;}; 
  private: 
    SListNode<Object> *header; 
    Object *ptr_Object; 
};

//SList definition 
template <class Object> 
SList<Object>::SList( ) 
{ 
     ptr_Object = new Object(); 
     header = new  SListNode<Object>;  
} 
 
// Copy constructor. 
template <class Object> 
SList<Object>::SList( const SList<Object> &rhs ) 
{ 
    header = new SListNode<Object>;  
    *this = rhs; 
} 
 
// Destructor. 
template <class Object> 
SList<Object>::~SList( ) 
{ 
    makeEmpty( ); 
    delete ptr_Object; 
    delete header; 
} 

**mypgm.c**
class mypgm
{
public:
    mypgm::mypgm()
    {
    ptr_dead_acc_list= new SList<String>; // ptr_dead_acc_list is of type SList<String>
    }
 };

**String class details for your reference**
class String 
{ 
        private: 
                char *_text; 
                friend class String_Iterator; 
        public: 
                // ctors and dtor 
                explicit String ();                      
                explicit String (char *); 
                explicit String (int ); 
                String (String& );               
                ~String(); 
 
                ///////////////// 
                // conversions: 
                ///////////////// 
                //  to C-like type char * 
                operator char *() {return _text;} 
 
                ///////////////// 
                // overloads: 
                ///////////////// 
                // assignment String = String 
                String &operator=(String &); 
}

**Error**:

SList.h: In constructor 'SList<Object>::SList() [with Object = String]': 
mypgm.c:131:   instantiated from here 
SList.h:85: error: no matching function for call to 'String::String(String)' 
String.h:27: note: candidates are: String::String(String&) 
SList.h:41: error: in passing argument 1 of 'SListNode<Object>::SListNode(const Object&, SListNode<Object>*) [with Object = String]' 
SList.h: In constructor 'SListNode<Object>::SListNode(const Object&, SListNode<Object>*) [with Object = String]': 
SList.h:85:   instantiated from 'SList<Object>::SList() [with Object = String]' 
mypgm.c:131:   instantiated from here 
SList.h:42: error: passing 'const String' as 'this' argument of 'String::operator char*()' discards qualifiers 
make: *** [all]

I feel that the arguments are not passed correctly during instantion,i have tried to resolve this ,but my steps are in vain
i am new to template concept.could you please help me to resolve this issue.
Thanks for looking into this

---

### Post by Zugzwang on 2013-02-08
> **dany2704 said:**
> 
I feel that the arguments are not passed correctly during instantion,i have tried to resolve this ,but my steps are in vain
i am new to template concept.could you please help me to resolve this issue.
Thanks for looking into this

I am not sure if that is already the complete solution to your problem, but the copy constructor of your String class does not have the correct interface: a "const" is missing:

So instead of
```

String (String& ); 

```
use
```

String (const String& ); 

```

This might resolve the issue, as in the line
```

SListNode( const Object &theElement = Object( ), 
SListNode *n = NULL ) 
: element( theElement ), next( n ) { } 

```
you are trying to use it with a const element.

Oh, and please use the CODE-tags in your posts. The line above is pretty much unreadable in this formatting.

---

