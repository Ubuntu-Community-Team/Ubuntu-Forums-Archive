---
title: "I don't get copy constructors..."
date: 2007-08-01
forum: Programming Talk
---

### Post by w1nD on 2007-08-01
Hey everyone,

I've been reading many C++ books, but I still don't really understand what copy constructors do and what they are for. Can someone explain please?

Thanks.

---

### Post by the_unforgiven on 2007-08-01
> **w1nD said:**
> Hey everyone,

I've been reading many C++ books, but I still don't really understand what copy constructors do and what they are for. Can someone explain please?

Thanks.
I think this wikipedia article has nice details:
[http://en.wikipedia.org/wiki/Copy_constructor](http://en.wikipedia.org/wiki/Copy_constructor)

---

### Post by brooksbp on 2007-08-01
Copy constructors allow you to make copies of instances of classes.

Say you have one instance of a class... variables defined.. etc... but you want to have another copy.  Well, instead of creating a new instance of that class and using get/set functions to 'copy' data, you can just use a copy constructor.

By default, all classes have the equals (=) sign overloaded so you can use that as a copy constructor essentially.  BUT this doesn't play well with pointers.  If you copy a pointer, you have two pointers pointing to the same spot--not good.  What you really want is two pointers pointing to different locations in memory with the same data at the spot both pointers are pointing to.

Fairly difficult to explain, but it really is a simple concept; provided you understand pointers.

---

### Post by rjfioravanti on 2007-08-01
An alternative is to have a clone() method on a class

so instead of doing

Class * a = new Class(b)

you could do

Class * a = b.clone();

b.clone() would look like {
  Class * c = new Class();
  c->props = this->getProps();
  return c;
}


Does the same thing just maybe it will help you understand since it gives a different perspective

---

### Post by brooksbp on 2007-08-01
> **rjfioravanti said:**
> An alternative is to have a clone() method on a class

so instead of doing

Class * a = new Class(b)

you could do

Class * a = b.clone();

b.clone() would look like {
  Class * c = new Class();
  c->props = this->getProps();
  return c;
}


Does the same thing just maybe it will help you understand since it gives a different perspective

No.  This does not offer a complete solution.  That clone() does not have support for copying pointer data.

Copy constructors are custom to your class.  The main thing to keep in mind when transferring data within your copy constructor is to watch out for pointers.

If you just copy all the pointers over, you will now have TWO instances of the same class, pointing to the same data.  What you really want is to have TWO instances of the same class, pointing to TWO instances of the same data.  Different locations in memory.  This is a crucial feature of copy constructors, make note of it.

Let me know if you still don't follow and I'll write some code for you.

---

### Post by rjfioravanti on 2007-08-01
> **brooksbp said:**
> No.  This does not offer a complete solution.  That clone() does not have support for copying pointer data.

Copy constructors are custom to your class.  The main thing to keep in mind when transferring data within your copy constructor is to watch out for pointers.

If you just copy all the pointers over, you will now have TWO instances of the same class, pointing to the same data.  What you really want is to have TWO instances of the same class, pointing to TWO instances of the same data.  Different locations in memory.  This is a crucial feature of copy constructors, make note of it.

Let me know if you still don't follow and I'll write some code for you.
I understand..

let me make it more clear

class.h
```

Class * clone();

```

class.cc
```

Class * Class :: clone() {
  Class newPointer* = new Class();
   newPointer->memberVar = this->memberVar;
   . 
   .
   .
   return newPointer;
}

```

I am creating a new pointer and returning it

The purpose of using clone instead of a copy constructor is it more clearly says what you are doing

The thing you want to do is create a copy of something in a different space... so which is more clear?
Class * a = new Class(*b);
Class * a = b->clone();

---

### Post by aks44 on 2007-08-01
> **rjfioravanti said:**
> The purpose of using clone instead of a copy constructor is it more clearly says what you are doing

The thing you want to do is create a copy of something in a different space... so which is more clear?
Class * a = new Class(*b);
Class * a = b->clone();

Java programmer, huh? :p

Definitely, the copy constructor is way more idiomatic to C++, thus much clearer.

A clone() method is useful *only* when you are dealing with a bunch of subclasses through a base class pointer *and* you need to duplicate those (unknown) objects. Which is very seldom.

BTW, in this context clone() is almost useless if it is not declared virtual.

---

### Post by rjfioravanti on 2007-08-01
> **aks44 said:**
> Java programmer, huh? :p

Definitely, the copy constructor is way more idiomatic to C++, thus much clearer.

A clone() method is useful *only* when you are dealing with a bunch of subclasses through a base class pointer *and* you need to duplicate those (unknown) objects. Which is very seldom.

BTW, in this context clone() is almost useless if it is not declared virtual.

Java uses copy constructors as well, I wouldn't say it is a Java thing. I don't buy the argument that people should keep their C++ looking cryptic because thats how  c++ is. Using a clone() method more clearly states the intent of what you are doing. It is good practice to hide the implementation details required to construct an object. Here we are not using any subclassing at all, I just threw out a very primitive example, so I'm not sure what you mean about declaring it to be virtual. You're saying it would be better to use clone when you have lots of subclassing, so you can avoid the prototype problem explained here [http://www.agiledeveloper.com/articles/cloning072002.htm](http://www.agiledeveloper.com/articles/cloning072002.htm). What if you originally don't have subclassing, so you write everything with a copy constructor, but then you need to create subclasses, so you change it everywhere? Why not just use clone() from the start.

---

### Post by aks44 on 2007-08-01
> **rjfioravanti said:**
> What if you originally don't have subclassing, so you write everything with a copy constructor, but then you need to create subclasses, so you change it everywhere?
Then it is a design flaw. Kill your architect. ;)



On a more serious side... the bad news is that clone() forces your class users to create new objects on the heap.

On the contrary, C++ encourages to create objects on the stack in order to benefit from RAII.

Need I explain more on that matter, or shall we give the thread back to the OP? ;)

---

### Post by rjfioravanti on 2007-08-01
> **aks44 said:**
> 
On a more serious side... the bad news is that clone() forces your class users to create new objects on the heap.

On the contrary, C++ encourages to create objects on the stack in order to benefit from RAII.

Need I explain more on that matter?

Not sure what RAII is. 

But copy constructor would use the new operator as well, unless you do

Class a(*b);  or Class a(b); whichever

But that really only takes off the stack entirely if your class contains only primitive types doesn't it? What if your class contains pointers to objects that need to be copied?

---

### Post by raijinsetsu on 2007-08-01
> **rjfioravanti said:**
> ... Why not just use clone() from the start.

The reason is: you have to have either a copy constructor or assignment operator(in C++) whenever you have a class with at least 1 member that is a pointer.
Any function that returns an object (not a reference or a pointer) will cause memory exceptions. This is because each copy (created through C++ implicit copy constructor) will have members that all point to the same address.
The implicit C++ copy constructor is actually just a memcpy call, so the data referenced by pointers is not copied.

As for the clone() function, just have it call the copy constructor for that class. Clone should ONLY be a wrapper for the copy constructor because most C++ classes NEED a copy constructor.

> **rjfioravanti said:**
> Not sure what RAII is. 

But copy constructor would use the new operator as well, unless you do

Class a(*b);  or Class a(b); whichever

But that really only takes off the stack entirely if your class contains only primitive types doesn't it? What if your class contains pointers to objects that need to be copied?

Uhm... Copy constructors do not need NEW. The C++ compiler would determine how the class (and it's members) would be allocated. new would definately be called if calling
```

int funcA(Object &B)
{
Object *A=new Object(B);
...

```
The above would only be used if funcA needed many copies of B to do something, or if the function were returning a new instance of an object.

New probably wouldn't be called for
```

int funcB(Object &B)
{
Object A(B);
...

```
as Object A would be allocated on the stack, and the copy constructor(which is just another function) would be called on it with B as it's argument.

---

### Post by aks44 on 2007-08-01
> **rjfioravanti said:**
> Not sure what RAII is.

"Resource Acquisition Is Initialization" (which should be more adequately dubbed "Resource Release Is Destruction" but I'm not the one who coined that term...).
IOW the fact that any object on the stack will have its destructor called whenever it goes out of scope, no matter which exit path is taken.

> **rjfioravanti said:**
> But copy constructor would use the new operator as well, unless you do

Class a(*b);  or Class a(b); whichever
No: operator new() uses a constructor (in this very case, the copy constructor), not the other way around.


> **rjfioravanti said:**
> But that really only takes off the stack entirely if your class contains only primitive types doesn't it? What if your class contains pointers to objects that need to be copied?

The very role of copy constructors is to take care of shallow / deep copies...

```
class Example
{
private:
  Whatever* m_ptr;
public:
  Example()
    : m_ptr(new Whatever())
  {};
  Example(const Example& rhs)
    : m_ptr(new Whatever(*rhs.m_ptr))
  {};
  Example& operator=(const Example& rhs)
  {
    Whatever* new_ptr = new Whatever(*rhs.m_ptr);
    delete m_ptr;
    m_ptr = new_ptr;
  };
  ~Example()
  {
    delete m_ptr;
  };
  void doWhatever() { m_ptr->whatever(); };
};
```

Does it answer your question?

---

### Post by aks44 on 2007-08-01
> **raijinsetsu said:**
> The implicit C++ copy constructor is actually just a memcpy call, so the data referenced by pointers is not copied.

I'm gonna be picky on this one (as usual :p)...

The implicit copy constructor (or assignment operator, they work the same) *actually* calls each class member's copy constructor. Only if not a single member has a custom copy constructor (ie. every single member and all its base classes have implicit copy ctor) then the compiler is able to optimize it as a memcpy call.

---

### Post by rjfioravanti on 2007-08-01
> **aks44 said:**
> 
No: operator new() uses a constructor (in this very case, the copy constructor), not the other way around.

You said you did not want to use the heap. If you have a copy constructor, then you would do

Class * a = new Class(*b) , which uses the heap

unless you do 

Class a(*b); 
Thats all I was saying

I read up on RAII now so I know what youre talking about.

---

### Post by raijinsetsu on 2007-08-01
> **w1nD said:**
> Hey everyone,

I've been reading many C++ books, but I still don't really understand what copy constructors do and what they are for. Can someone explain please?

Thanks.

Here's an example of a copy constructor
```


class A
{
private:
[INDENT]A *next;[/INDENT]
public:
[INDENT]~A() //deconstructor
{
[INDENT]if(next)
[INDENT]delete next[/INDENT][/INDENT]
};

A(const A &obj)
{
[INDENT]if(obj.next)
[INDENT]next=new A(*obj.next);[/INDENT][/INDENT]
};[/INDENT]
};


```
Explanation:
If you didn't have that copy constructor, and you called the following code:
```

A GetNext(A &obj)
{
[INDENT]return *obj.next;[/INDENT]
};

...

A *obj1=new A,*obj2;
*obj2=GetNext(*obj1);

...

```
the obj1.next member would by some memory address, and obj2.next would be the same memory address, which is only ok if you want this. If you were to delete obj1, obj1.next would be deleted, and obj2.next would now point to something that doesn't exist anymore. This can cause memory exception errors.

So, in short, copy constructors allow you to copy the complex members of a class.

---

### Post by aks44 on 2007-08-01
> **rjfioravanti said:**
> You said you did not want to use the heap. If you have a copy constructor, then you would do

Class * a = new Class(*b) , which uses the heap

unless you do 

Class a(*b); 
Thats all I was saying
So I guess we agree that the copy constructor by itself is independant from the stack / heap.

Back to the (off) topic: the fact is that clone() can trivially be implemented in terms of the copy constructor, while the contrary is plain false.


> **rjfioravanti said:**
> I read up on RAII now so I know what youre talking about.

Good. RAII really is the foundation for all automatic resource management in C++ as well as exception-safe code.
Use it & abuse it until you can't even remember how you managed to write anything without it. ;)

---

### Post by Dancingwllamas on 2007-08-01
Another problem with the clone() function as posted above is that it returns a pointer by value instead of by reference. The function must return by reference. Otherwise, the pointer created within the function goes away when the function returns, if this makes sense.

Best way is to use it as a wrapper for the copy constructor (as some have said above).

---

### Post by rjfioravanti on 2007-08-01
> **Dancingwllamas said:**
> Another problem with the clone() function as posted above is that it returns a pointer by value instead of by reference. The function must return by reference. Otherwise, the pointer created within the function goes away when the function returns, if this makes sense.

Best way is to use it as a wrapper for the copy constructor (as some have said above).

Pointers are just numbers that represent addresses, you always pass them by value

---

### Post by Dancingwllamas on 2007-08-01
Wow, I completely misread the post. For some reason I thought he was returning it differently.

My mistake.

---

