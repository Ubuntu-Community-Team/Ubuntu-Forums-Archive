---
title: "C++ pointer question"
date: 2007-10-08
forum: Programming Talk
---

### Post by Houman on 2007-10-08
hi there;

can someone please explain to me why would you have somethign like this:

void someFunction (int *(&a))

I read on someone else's code and i dont understand the purpose if it, (what does it do?)

regards

Houman

---

### Post by duff on 2007-10-08
what's the type of "a"?

---

### Post by Yz85Racer on 2007-10-08
> **duff said:**
> what's the type of "a"?
By the looks of it is an int.

---

### Post by rharriso on 2007-10-08
the code seems a little nonsensical. The & operator creates a reference to the object a, meaning that it makes another copy of the object. It seems to me that the * would be unnecessary. 

i would think the same function could be written, 

void function(int a); 

I've used the & operator in a function definition but never the *.

---

### Post by CptPicard on 2007-10-08
The parameter is a reference to a pointer to an int... inside the function, "a" behaves like an int *  -- actually a *is* the same int * that you'd use to call the function with -- check out a references vs. pointers thread that has been active in recent days.

The idea behind using this is that you can set the value of the referred-to pointer inside the function -- the alternative would be to pass a pointer to a pointer -- here's a quick demo:

```

#include <iostream>

using namespace std;


int x = 7;

void myFunction(int *(&a)) {
	a = &x;
}

int main(int argc, char **argv) {
	int a = 5;
	int *p = &a;
	cout << *p << endl;
	myFunction(p);
	cout << *p << endl;
}

```

---

### Post by Wybiral on 2007-10-08
> **CptPicard said:**
> The parameter is a reference to a pointer to an int... inside the function, "a" behaves like an int *  -- actually a *is* the same int * that you'd use to call the function with -- check out a references vs. pointers thread that has been active in recent days.

Indeed. The syntax for it may look wrong, but it is a reference to a pointer. As CptPicard mentioned, it's particularly useful when you want to change the value of the pointer (NOT the value at the address the pointer points to, but the address itself).

Similar to a {int **x;} from C, but you don't have to dereference it (because it's a reference). Less confusing than multiple *'s IMO, but still slightly hairy syntax.

---

### Post by CptPicard on 2007-10-08
Not being much of a C++ guru, I must admit I had to think for a bit of the use case and even test it, although of course the datatype itself is obvious :)

Almost got tripped by thinking that "you can't reassign a reference"... well, perhaps not, but assigning to what you're referring to is perfectly fine ;)

---

### Post by Wybiral on 2007-10-08
> **CptPicard said:**
> Not being much of a C++ guru, I must admit I had to think for a bit of the use case and even test it, although of course the datatype itself is obvious :)

Almost got tripped by thinking that "you can't reassign a reference"... well, perhaps not, but assigning to what you're referring to is perfectly fine ;)

I can't think of a situation in C++, but in C that design is pretty common (but a pointer to a pointer instead of a reference of a pointer).

It's useful if you need to implement a custom ADT. For instance, if the pointer being passed to the function were the top of a stack and you needed to pop it, you would have to alter the address the pointer points to in order to assign it to the next element.

But thats obviously a bad example because in C++ you would write the pop function as a method in the stack class. I actually can't think of any immediate use of it off the top of my head. In C++ you generally want to avoid pointers when you can anyway.

---

### Post by hod139 on 2007-10-08
To follow up Wybrial's post, the most common reason for passing a pointer by reference is when you need to dynamically allocate the pointer.

```

void allocate(int* &array){
  array = new int[10];
}

void allocateBad(int *array){
  array = new int[10];
}

```

In the first function, you allocate as expected.  In the second, you allocate a copy of the pointer, which then goes out of scope when the function returns (leaking memory) and then when you use the array outside the function you will touch unallocated memory most like causing a segfault.

---

### Post by CptPicard on 2007-10-08
> **Wybiral said:**
> I can't think of a situation in C++, but in C that design is pretty common (but a pointer to a pointer instead of a reference of a pointer).

Certainly. For me it was more of a "nature of reference" issue -- I still sometimes have to really remind myself that you can assign "through" the reference like that -- that's it's not just a "niftier way to pass values without copy construction" :)

---

### Post by gnusci on 2007-10-09
as hod139 said this is a common way to pass a pointer address as argument so it can be modified inside the function. Here another example:

[PHP]
#include <iostream>

using namespace std;

void someFunction(int* (&a)){
  a = new int[10];
}

int main(void){
    int * pointer;
    someFunction(pointer);

    for(int i=0; i<10; i++)
        pointer[i] = 5;

    for(int i=0; i<10; i++)
        cout<<"["<<i<<"]:"<<pointer[i]<<endl;

    return 0;
}

[/PHP]

---

### Post by Wybiral on 2007-10-09
> **gnusci said:**
> as hod139 said this is a common way to pass a pointer address as argument so it can be modified inside the function. Here another example:

[PHP]
#include <iostream>

using namespace std;

void someFunction(int* (&a)){
  a = new int[10];
}

int main(void){
    int * pointer;
    someFunction(pointer);

    for(int i=0; i<10; i++)
        pointer[i] = 5;

    for(int i=0; i<10; i++)
        cout<<"["<<i<<"]:"<<pointer[i]<<endl;

    return 0;
}

[/PHP]

The problem with this is that the user has to remember to free the array on their own. That's generally a big "no no" in design because it's just asking for leaks. It would work in C (where you can hold the user responsible for manually calling a destructor function) but in C++ the pointer should be wrapped in a class. And if it's in a class, you don't have to pass it around because you will likely use the methods of the class to allocate it (and then the class destructor to free it).

---

### Post by Houman on 2007-10-09
hi everyone;

thank you all so much for you replies, I understand its purpose now, its the same as a double pointer (int** a) but the syntax is still throwing me off;

so instead of  int* (&a) could he have written int*& a? I mean there is something with this syntax that is just odd; 

regards

Houman

---

### Post by hod139 on 2007-10-09
> **Houman said:**
> hi everyone;

so instead of  int* (&a) could he have written int*& a?; 



The parenthesis (or brackets depending on where you are from) are not needed.  And yes, the syntax is kinda ugly.

---

### Post by gnusci on 2007-10-10
> **Wybiral said:**
> The problem with this is that the user has to remember to free the array on their own. That's generally a big "no no" in design because it's just asking for leaks. It would work in C (where you can hold the user responsible for manually calling a destructor function) but in C++ the pointer should be wrapped in a class. And if it's in a class, you don't have to pass it around because you will likely use the methods of the class to allocate it (and then the class destructor to free it).

That's right, you have to care of the memory and release it before to close de program to avoid a leak. Here is the code again:

[PHP]#include <iostream>

using namespace std;

void someFunction(int* (&a)){
  a = new int[10];
}

void free_memory(int* (&a)){
  delete a;
}

int main(void){
    int * pointer;
    someFunction(pointer);

    for(int i=0; i<10; i++)
        pointer[i] = 5;

    for(int i=0; i<10; i++)
        cout<<"["<<i<<"]:"<<pointer[i]<<endl;

    free_memory(pointer); // release de memory before exit.
    return 0;
}

[/PHP]

but:

> I understand its purpose now, its the same as a double pointer (int** a) 

that's not true, **int **** is a double pointer an it is for memory asignament of an array of **int**.

> int* (&a) could he have written int*& a

it is the same...

---

### Post by Wybiral on 2007-10-10
> **gnusci said:**
> That's right, you have to care of the memory and release it before to close de program to avoid a leak. Here is the code again:


Yes, but that's C code. In C++ you want to wrap it into a class and allow the destructor to free it. There's no use in creating custom destructors in a language that already has them. This design will almost guarantee misuse of your code.

Something like this (except it would probably also need a copy constructor in reality):

```

#include <iostream>

class object
{
    protected:
    int m_size;
    int *m_data;

    public:
    object(const int size);
    ~object();
    void print();
};

object::object(const int size)
{
    m_size = size;
    m_data = new int[size];
    for(int i = 0; i < m_size; i++)
    {
        m_data[i] = i * 2;
    }
}

object::~object()
{
    delete m_data;
}

void object::print()
{
    for(int i = 0; i < m_size; i++)
    {
        std::cout << "[" << i << "]:" << m_data[i] << std::endl;
    }
}

int main()
{
    object obj(10);
    obj.print();
    return 0;
}


```

> **gnusci said:**
> that's not true, int ** is a double pointer an it is for memory asignament of an array of int.
It's not just for arrays. I think what the OP meant was that it's used the same as double pointers from C when you needed to alter a pointer (since C didn't have references as parameters).

---

### Post by hod139 on 2007-10-10
> **gnusci said:**
> 
that's not true, **int **** is a double pointer an it is for memory asignament of an array of **int**.

I think you missed the point of Wybrial's comparison.

C++ way:
```

[COLOR=#000000][COLOR=Black]void someFunction[/COLOR][COLOR=Black]([/COLOR][COLOR=Black]int[/COLOR][COLOR=Black]* &[/COLOR][COLOR=Black]a[/COLOR][COLOR=Black]){ 
  [/COLOR][COLOR=Black]a [/COLOR][COLOR=Black]= new [/COLOR][COLOR=Black]int[/COLOR][COLOR=Black][[/COLOR][COLOR=Black]10[/COLOR][COLOR=#007700][COLOR=Black]]; [/COLOR]
} [/COLOR][/COLOR]

```C way:
```

[COLOR=#000000][COLOR=Black]void someFunction(int** a){
  *a = (int*)malloc(10*sizeof(int));
}[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=Black]

Also this code:
[/COLOR][/COLOR]```
 void free_memory(int* (&a)){
  delete a;
}

```leaks memory.  I think you mean delete[] a;

> **Wybiral said:**
> In C++ you want to wrap it into a class and allow the destructor to free it. There's no use in creating custom destructors in a language that already has them. This design will almost guarantee misuse of your code.


This isn't always true.  Many times you do want to write your own constructor and destructor guarenteeing better use of your code.  For example:
```

template <class T> 
class MyClass {

public:   
  // CONSTRUCTORS, ASSIGNMENT OPERATOR, & DESTRUCTOR
  MyClass(size_type s) { this->create(s); }
  MyClass(const MyClass& v) { copy(v); }
  MyClass& operator=(const MyClass& v); 
  ~MyClass() { destroy(); } 

  // MEMBER FUNCTIONS
  //go here

private:  
  void create(size_type n);
  void destroy();
  void copy(const MyClass<T>& v); 

  // REPRESENTATION
  T** values;
};

// Create an empty MyClass (null pointers everywhere).
template <class T>  void MyClass<T>::create(size_type s) {
  values = new T*[s];
  for (unsigned int i = 0; i < size; i++) {
    values[i] = NULL;
  }
}

template <class T> void MyClass<T>::destroy() {
  for (int i = 0; i < size; i++) {
      delete [] values[i];
  }
  delete [] values; 
}

// Assign one MyClass<T>& to another, avoiding duplicate copying
template <class T> MyClass<T>& MyClass<T>::operator=(const MyClass<T>& v) {
  if (this != &v) {
    destroy();
    this->copy(v);
  }
  return *this;
}

// Create the MyClass as a copy of the given MyClass
template <class T> void MyClass<T>::copy(const MyClass<T>& v) {
  this->create(v.size);
  // copy private data, be careful not to dereference null
}

```

---

### Post by Wybiral on 2007-10-10
> **hod139 said:**
> This isn't always true.  Many times you do want to write your own constructor and destructor guarenteeing better use of your code.  For example:

What I mean is that you don't want the users of your code to have to explicitly call "new" and "free" constructor functions (external to a class that can destruct them). You want to use C++'s syntax for constructors and not manually implement "myObject_init" and "myObject_free" type functions that used to be common practice in C.

IMO it's a bad idea for a function to allocate memory to a pointer unless the pointer is wrapped in a class that can guarantee it's release. Otherwise, as I said, it's almost begging for misuse because it forces your users to understand the inner workings of that function.

Any time your code requires the user to call some kind of "free" function because it isn't designed to take advantage of constructors/destructors, you're basically reverting back to C-style design. I'm sure there are exceptions, but generally it's not a good idea.

---

### Post by hod139 on 2007-10-10
> **Wybiral said:**
> What I mean is that you don't want the users of your code to have to explicitly call "new" and "free" constructor functions (external to a class that can destruct them). You want to use C++'s syntax for constructors and not manually implement "myObject_init" and "myObject_free" type functions that used to be common practice in C.
<snip>
I now see what you were trying to say, and I agree completely.

---

### Post by aks44 on 2007-10-10
> **hod139 said:**
> This isn't always true.  Many times you do want to write your own constructor and destructor guarenteeing better use of your code.  For example:

<<snipped example>>
I agree about the point you're making, ie. factorizing common code no matter if it is used in constructors or destructors.

However I feel like I have to point out that the above code is flawed (it's not exception safe, not even the basic guarantee).

I'm perfectly aware you threw it together just to demonstrate your point, but I couldn't help... ;)

---

### Post by hod139 on 2007-10-10
> **aks44 said:**
> 
However I feel like I have to point out that the above code is flawed (it's not exception safe, not even the basic guarantee).

I'm perfectly aware you threw it together just to demonstrate your point, but I couldn't help... ;)

Yeah yeah...  feel free to fix it if you want!

---

### Post by aks44 on 2007-10-11
> **hod139 said:**
> Yeah yeah...  feel free to fix it if you want!

Here it is...

```
template <class T> 
class MyClass
{
  MyClass(); // we don't provide a default constructor, and we
             // don't want the compiler to auto-generate one
public:   
  inline MyClass(size_t s) : values(0), size(0) { create(s); };
  inline MyClass(const MyClass& v) : values(0), size(0) { copy(v); };
  inline MyClass& operator =(const MyClass& v) { copy(v); return *this; };
  inline ~MyClass() { destroy(); };

  // MEMBER FUNCTIONS
  // go here

private:  
  void create(size_t n);
  void destroy();
  void copy(const MyClass<T>& v);

  // REPRESENTATION
  T** values;
  size_t size;
};

// Create an empty MyClass (null pointers everywhere).
template <class T>
void MyClass<T>::create(size_t s)
{
  destroy();
  if (s)
  {
    values = new T*[s];
    size = s;
    for (unsigned int i = 0; i < size; ++i)
      values[i] = NULL;
  };
}

template <class T>
void MyClass<T>::destroy()
{
  if (values)
  {
    for (int i = 0; i < size; ++i)
      delete values[i];
    delete[] values;
    values = 0;
    size = 0;
  };
}

// Create the MyClass as a copy of the given MyClass
template <class T>
void MyClass<T>::copy(const MyClass<T>& v)
{
  if (this != &v)
  {
    MyClass<T> tmp(v.size);
    for (int i = 0; i < size; ++i)
    {
      // copy private data from v to tmp, be careful not to dereference null
      // ...
    };
    std::swap(values,tmp.values);
    std::swap(size,tmp.size);
  };
}
```


FWIW copy() provides a strong guarantee but create() only provides a basic guarantee. destroy() should provide a nothrow guarantee if T is implemented sanely (ie. if T's destructor does not throw).


To anyone wondering what this "exception safety" thing is about, I suggest reading [a few]("http://www.gotw.ca/gotw/008.htm") [introductory articles]("http://www.gotw.ca/gotw/059.htm") about that, from Herb Sutter's GOTW (he has other articles on this matter too, just dig his site).


@hod: My precedent remark was not against you, but rather to warn unsuspecting newbies that there was something wrong with the code. ;)

---

### Post by hod139 on 2007-10-11
> **aks44 said:**
> 
@hod: My precedent remark was not against you, but rather to warn unsuspecting newbies that there was something wrong with the code. ;)

No problems, I don't mind any critiques of code I post, especially when the person follows up with code of their own and a good explanation.  That was a good catch with my destroy function (the seg fault would have found it for me :) ). 


As for the copy and assignment operator, I still don't fully understand exception safety differences.  What makes my version not exception safe?  Nothing will leak if the allocation fails, so I don't think I understand these exception rules good enough.

---

### Post by aks44 on 2007-10-12
> **hod139 said:**
> As for the copy and assignment operator, I still don't fully understand exception safety differences.  What makes my version not exception safe?  Nothing will leak if the allocation fails, so I don't think I understand these exception rules good enough.

I'll first quote your original code for convenience, to avoid switching between posts:

> **hod139 said:**
> ```

template <class T> 
class MyClass {

public:   
  // CONSTRUCTORS, ASSIGNMENT OPERATOR, & DESTRUCTOR
  MyClass(size_type s) { this->create(s); }
  MyClass(const MyClass& v) { copy(v); }
  MyClass& operator=(const MyClass& v); 
  ~MyClass() { destroy(); } 

  // MEMBER FUNCTIONS
  //go here

private:  
  void create(size_type n);
  void destroy();
  void copy(const MyClass<T>& v); 

  // REPRESENTATION
  T** values;
};

// Create an empty MyClass (null pointers everywhere).
template <class T>  void MyClass<T>::create(size_type s) {
  values = new T*[s];
  for (unsigned int i = 0; i < size; i++) {
    values[i] = NULL;
  }
}

template <class T> void MyClass<T>::destroy() {
  for (int i = 0; i < size; i++) {
      delete [] values[i];
  }
  delete [] values; 
}

// Assign one MyClass<T>& to another, avoiding duplicate copying
template <class T> MyClass<T>& MyClass<T>::operator=(const MyClass<T>& v) {
  if (this != &v) {
    destroy();
    this->copy(v);
  }
  return *this;
}

// Create the MyClass as a copy of the given MyClass
template <class T> void MyClass<T>::copy(const MyClass<T>& v) {
  this->create(v.size);
  // (#)
  // copy private data, be careful not to dereference null
}

```

Your copy constructor doesn't have problems *if* copy() does not throw past the call to create() (ie. after what I labeled (#)). However if copy() throws after (#) you'll have a memleak, but I bet you already knew that.

Now let's focus on the operator=().
First it calls destroy(), which leaves a dangling pointer even though the memory is deleted. Then copy() is called, which in turn calls create(). If new fails, an exception is thrown and the object is no more in a useable nor destroyable state.
From now on, 3 problems:
- if you try to access the data, you'll end up accessing freed memory. Lucky you if you get a segfault, but that's quite improbable so the problem would be hard to spot.
- if you try to assign another object to the one which is in a buggy state, copy() will call destroy() and free the memory *again*.
- *when* (not *if*, it can't be avoided) you destroy the object, double-free *again*.

I'm not sure how Linux behaves with regard to multiple deletes of the same memory area, but again you'd be very lucky if you got a segfault+coredump.


FWIW resetting the pointer in destroy() gives operetor=() the basic guarantee (object remains in a useable and destroyable state, although unpredictable) *if* copy() does not throw past (#). The main thing that annoys me is that condition that copy() must not throw after (#) to maintain the basic guarantee.

Now in the version I provided, copy() can throw anywhere before the final swaps, and if this happens the original object has not been changed, which is the strong guarantee.



Back to the reason why you posted that code, even though I agree that factorizing common code is a must, I'd have to disagree on how you did it, especially regarding copy/assignment.

It's quite common (and the safest thing to do BTW) to implement assignment in terms of copy + swap. Something like:
```
class C
{
  C& operator =(const C& c)
  {
    C c2(c);
    // swap data members between *this and c2
    // swaps cannot throw so the only point of failure is the copy constructor
    return *this;
  };
};
```


In your example, I'd even go as far as implementing the copy constructor in terms of the "size" constructor:

```
class C
{
  C(const C& c)
    : values(0),
      size(0)
  {
    C c2(c.size); // allocate the array
    // copy the contents of the array from c to c2
    // swap data members between *this and c2
  };
};
```

C::C(size_t) would allocate it's memory (no need for a create() function anymore), and C::~C() would destroy the memory (no need for a destroy() function anymore).
Which leaves us with a single thing to factorize out: the **static C::swap(C&, C&)** function. :)

EDIT: in fact, better make swap() a non-static member, so you can write C().swap(myobj) to clear an object ; to do that you can't use the static version, writing C::swap(myobj, C()) is illegal because C++ only allows const references to be taken from temporary objects. I guess MSVC's non-standard implementation gave me bad habits (it allows taking non-const references from a temporary object, which is not correct C++, now I'm used to take advantage of this misfeature :oops:).


I hope I've been clear enough, not sure if this fully answered your question but I'm hungry now... ;)

---

### Post by hod139 on 2007-10-12
Wow, thanks for the detailed explanation.  I learned something new today.  I have always had my assignment operator call destroy, then copy.  In practice, I always NULL pointers after calling delete (which you noted adds some guarantees), but I never thought about the possibility of a double free occurring.

Thanks again for the explanation.

---

### Post by pmasiar on 2007-10-12
reading this... excellent explanation, but... there are people suggesting for beginners to start programming by learning C... I wonder if those people do know C as deeply as aks44 does, aks44 never suggests that :-)

---

### Post by aks44 on 2007-10-12
> **pmasiar said:**
> there are people suggesting for beginners to start programming by learning C... I wonder if those people do know C as deeply as aks44 does, aks44 never suggests that

Thanks, but the fact is that I don't know C quite well... indeed I'm pretty lousy at C because I miss too many C++ features. Unless of course you made a typo and meant C++. :)


But anyway you're right, either C or C++ are hardly a beginners language IMHO. Both require many knowledge of what happens "under the hood" to be used correctly. And C++ adds exceptions to the game (OO is just some pretty advanced "syntactic sugar" IMO), which breaks control flows and adds complexity to individual class designs (but it greatly simplifies the overall design IMHO, most of the time you don't have to bother with "exceptional" cases in the normal flow, you just handle them separately).


And no, I WON'T name any good beginners language. You do that job quite correctly on your own... :p

---

### Post by mjwood0 on 2007-10-12
Wow Aks44!  That's really a helpful explanation.

I'm the complete opposite.  I live my life in C and really have a hard time with all the C++ concepts.  Then again, I usually spend a good deal of time embedding assembly into C as I do tend to write things on a direct hardware interface level.

This whole syntax thing is very similar to the confusion many people have regarding void pointers.  

```
(void)function_call(void * a)
```

Or even pointers in general for that matter.  I can't tell you how many people I've worked with over the years who don't understand stuff like this:

```
unsigned int * foo = (unsigned int *)(0xFF000000);

```

---

### Post by aks44 on 2007-10-13
> **mjwood0 said:**
> I can't tell you how many people I've worked with over the years who don't understand stuff like this:

```
unsigned int * foo = (unsigned int *)(0xFF000000);

```


Strange, I am under the impression that way too many people understand that kind of unchecked casts, and that most of them are happily misusing it (at the application level, mind you, I reckon it's necessary when dealing with low level code). ;)

---

### Post by mjwood0 on 2007-10-13
> **aks44 said:**
> Strange, I am under the impression that way too many people understand that kind of unchecked casts, and that most of them are happily misusing it (at the application level, mind you, I reckon it's necessary when dealing with low level code). ;)

I don't think I could live without it.

Granted, I'd never put an actual address there except for debug.  Usually, it's a #define from a memory map.  Not that it's *that* much safer, but there are only so many ways to access hardware directly.

Thanks again for the C++ tutorial.

---

