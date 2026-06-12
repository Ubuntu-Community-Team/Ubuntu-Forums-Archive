---
title: "C++ objects with private stringstreams in vectors"
date: 2008-02-14
forum: Programming Talk
---

### Post by zenkaon on 2008-02-14
Hello all,

I have a problem I was hoping someone could shed some light on. 

I have many objects of the same type, so I usually put them all in a stl vector and then iterate on that vector when I want to do a common thing to all of the objects.

Except if my objects have a stringstream private member variable I am unable to do so. This is bloody annoying as it is bloody handy if an object knows its own name.

Below is a simplified example of my problem:

```

#include <iostream>
#include <string>
#include <sstream>
#include <vector>

using std::vector;
using std::stringstream;
using std::cout;
using std::endl;

class foo{
	public:
	explicit foo(stringstream* t);
	~foo();
	void sayhello();
	private:
	stringstream text_;         // (1)
};

foo::foo(stringstream* t){
	text_<<t->str();          // (2)
}

foo::~foo(){}

void foo::sayhello(){
	cout<<text_.str()<<endl;   // (3)
}

int main(){
	stringstream* hello=new stringstream;
	*hello<<"Hello World !";

	foo* bar = new foo(hello);
	delete hello;
	bar->sayhello();

	vector<foo>* v_foo = new vector<foo>;
	//v_foo->push_back(*bar);        // (4)

	delete bar;
	delete v_foo;
	return EXIT_SUCCESS;
}


```

At present, this code will compile and runs fine.

However, uncomment (4) and I get the compiler error message:

I am aware that I am using a red-hat system and posting on an ubuntu forum. I've moved to ubuntu, the sys-admins at work love ubuntu, but work remains steadfastly RHEL. I'm not going to be able to change my system or compiler. 

```

/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h: In copy constructor `std::basic_ios<char, std::char_traits<char> >::basic_ios(const std::basic_ios<char, std::char_traits<char> >&)':
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h:81:   instantiated from `void std::_Construct(_T1*, const _T2&) [with _T1 = foo, _T2 = foo]'
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_vector.h:560:   instantiated from `void std::vector<_Tp, _Alloc>::push_back(const _Tp&) [with _Tp = foo, _Alloc = std::allocator<foo>]'
foo.cpp:39:   instantiated from here
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/ios_base.h:781: error: `std::ios_base::ios_base(const std::ios_base&)' is private
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h:81: error: within this context
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h: In copy constructor `std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >::basic_stringbuf(const std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >&)':
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h:81:   instantiated from `void std::_Construct(_T1*, const _T2&) [with _T1 = foo, _T2 = foo]'
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_vector.h:560:   instantiated from `void std::vector<_Tp, _Alloc>::push_back(const _Tp&) [with _Tp = foo, _Alloc = std::allocator<foo>]'
foo.cpp:39:   instantiated from here
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/streambuf:769: error: `std::basic_streambuf<_CharT, _Traits>::basic_streambuf(const std::basic_streambuf<_CharT, _Traits>&) [with _CharT = char, _Traits = std::char_traits<char>]' is private
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h:81: error: within this context
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/vector.tcc: In member function `std::basic_ios<char, std::char_traits<char> >& std::basic_ios<char, std::char_traits<char> >::operator=(const std::basic_ios<char, std::char_traits<char> >&)':
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/vector.tcc:238:   instantiated from `void std::vector<_Tp, _Alloc>::_M_insert_aux(__gnu_cxx::__normal_iterator<typename _Alloc::pointer, std::vector<_Tp, _Alloc> >, const _Tp&) [with _Tp = foo, _Alloc = std::allocator<foo>]'
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_vector.h:564:   instantiated from `void std::vector<_Tp, _Alloc>::push_back(const _Tp&) [with _Tp = foo, _Alloc = std::allocator<foo>]'
foo.cpp:39:   instantiated from here
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/ios_base.h:784: error: `std::ios_base& std::ios_base::operator=(const std::ios_base&)' is private
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/vector.tcc:238: error: within this context
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/vector.tcc: In member function `std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >& std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >::operator=(const std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >&)':
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/streambuf:776: error: `std::basic_streambuf<_CharT, _Traits>& std::basic_streambuf<_CharT, _Traits>::operator=(const std::basic_streambuf<_CharT, _Traits>&) [with _CharT = char, _Traits = std::char_traits<char>]' is private
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/vector.tcc:238: error: within this context


```

Now if (1), (2) & (3) are commented out, with (4) uncommented, the code will compile and run once more.

I have tried this using references as well as pointers to the stringstreams.

All other types of data member seem to work, it seems specific to stringstreams.

Any ideas as to what's going on?

---

### Post by aks44 on 2008-02-14
stringstreams don't have copy / assignment semantics (which vectors require).

Using std::list may solve your problems, as lists don't need copy semantics.

---

### Post by zenkaon on 2008-02-14
Nice idea, but sorry, doesn't work. 

I think that you may be on to something about the copy assignment semantics.

If I replace vector with list throughout I get the slightly shorter error message:

```

/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h: In copy constructor `std::basic_ios<char, std::char_traits<char> >::basic_ios(const std::basic_ios<char, std::char_traits<char> >&)':
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h:81:   instantiated from `void std::_Construct(_T1*, const _T2&) [with _T1 = foo, _T2 = foo]'
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_list.h:438:   instantiated from `std::_List_node<_Tp>* std::list<_Tp, _Alloc>::_M_create_node(const _Tp&) [with _Tp = foo, _Alloc = std::allocator<foo>]'
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_list.h:1163:   instantiated from `void std::list<_Tp, _Alloc>::_M_insert(std::_List_iterator<_Tp>, const _Tp&) [with _Tp = foo, _Alloc = std::allocator<foo>]'
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_list.h:785:   instantiated from `void std::list<_Tp, _Alloc>::push_back(const _Tp&) [with _Tp = foo, _Alloc = std::allocator<foo>]'
foo.cpp:39:   instantiated from here
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/ios_base.h:781: error: `std::ios_base::ios_base(const std::ios_base&)' is private
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h:81: error: within this context
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h: In copy constructor `std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >::basic_stringbuf(const std::basic_stringbuf<char, std::char_traits<char>, std::allocator<char> >&)':
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/streambuf:769: error: `std::basic_streambuf<_CharT, _Traits>::basic_streambuf(const std::basic_streambuf<_CharT, _Traits>&) [with _CharT = char, _Traits = std::char_traits<char>]' is private
/usr/lib/gcc/i386-redhat-linux/3.4.6/../../../../include/c++/3.4.6/bits/stl_construct.h:81: error: within this context


```

---

### Post by aks44 on 2008-02-14
Dang, I should have thought about that (std::list::push_back et al. use copy constructors).


What about writing your own copy / assignment for your foo class?

They should just copy all fields, but use

**text_ << rhs.text_.str();**

for copying the stringstream (assuming **rhs** is the name of the source object).



EDIT: for the sake of completeness: your problem lies in the fact that your foo class doesn't explicitly define copy / assignment, so the compiler auto-generates them. But in the process it tries to use std::stringstream copy / assignment which is forbidden (the parent class std::ios_base declares them private and doesn't define them).

---

### Post by zenkaon on 2008-02-15
OK, the moral of the story is don't use stringstreams as private data members in classes - unless your prepared to write your own copy / assignment operators.

I have fudged my way around this problem in a manor that it probably unsuitable to most people. I develop particle physics software and we use the ROOT framework (really bad name, I know) [http://root.cern.ch](http://root.cern.ch) 

ROOT contains histogram objects, I use them a lot, the title of the histogram is a string. I can store the name of my object in the histogram title and retrieve it with a simple histo->GetTitle() member function. The histograms CAN be used as data members in an object that is going to be placed into a stl vector.

Bit of a hack I know, but it works!! 

If anyone is interested in data analysis, ROOT is pretty damn useful. GPL'd, of course.

---

### Post by aks44 on 2008-02-15
> **zenkaon said:**
> OK, the moral of the story is don't use stringstreams as private data members in classes - unless your prepared to write your own copy / assignment operators.

I'd even say: don't use C++ at all unless you're prepared to write (amongst many other things) your own copy / assignment operators. ;)

TBH they are far from the most complicated required work... :)



Just curious (now that you explained it a bit more): is there a reason why you don't use "simple" std::strings instead of stringstreams?

---

### Post by zenkaon on 2008-02-17
Habit :) Never really thought about what to use much. A few years ago a friend told me to use stringstreams as they are better (not real reasons given), I implemented them in my code and have just kinda used them ever since.

I was very happy with how they performed until I encountered this problem. normal std::string lacks the copy / assignment operators as well, so I'll probably just stick to using stringstreams and my hack......I've got bigger fish to fry, complicated classes to write and deadlines to meet.

Strings have always been a bugger, what do you use to deal with them in C++?

---

### Post by aks44 on 2008-02-17
> **zenkaon said:**
> normal std::string lacks the copy / assignment operators as well
They don't:
```
#include <iostream>
int main()
{
  std::string str1 = "Hello";
  std::string str2(str1); // copy ctor
  str1 = str2 + " " +"World"; // assignment
  std::cout << str1 << std::endl;
  return 0;
}
```


> **zenkaon said:**
> what do you use to deal with them in C++?
Either std::string (which is far more complete than you seem to think) for small hacks, or a custom string library (that supports ref-counting, copy on write and all the goodies) for more serious projects.

---

### Post by hswner on 2008-08-18
I was getting a very similar error when trying to push_back an object of class foo into a list bar (also tried using vector).

I think the problem is not only with the string stream's copy / assignment operators. Because I used to have a private fstream object (not a string stream) inside my class. 

Anyway, I stopped using that private fstream object and the problem solved :)

---

### Post by dwhitney67 on 2008-08-18
Just define/implement the copy and assignment methods for your class 'foo'.

For example:
[php]
class foo
{
  public:
    ...
    foo(const foo &f);
    foo & operator=(const foo &f);
    ...
};

...

foo::foo(const foo &f)
{
  text_ << f.text_.str();
}

foo & foo::operator=(const foo &f)
{
  text_ << f.text_.str();
  return *this;
}
[/php]

P.S.  Do you always instantiate all of your objects from the heap??  Very unusual!

---

### Post by dribeas on 2008-08-18
> **zenkaon said:**
> ```

class foo{
	public:
	explicit foo(stringstream* t);
	~foo();
	void sayhello();
	private:
	stringstream text_;         // (1)
};

foo::foo(stringstream* t){
	text_<<t->str();          // (2)
}

foo::~foo(){}

void foo::sayhello(){
	cout<<text_.str()<<endl;   // (3)
}

int main(){
	stringstream* hello=new stringstream;
	*hello<<"Hello World !";

	foo* bar = new foo(hello);
	delete hello;
	bar->sayhello();

	vector<foo>* v_foo = new vector<foo>;
	//v_foo->push_back(*bar);        // (4)

	delete bar;
	delete v_foo;
	return EXIT_SUCCESS;
}

```


Your code seems overly complex for the task at hand. First, if what you want is to keep a string in the object, use a string (std::string) and the problem will be gone. As it has already been pointed out STL containers require (at least) copy constructible types.

I don't agree with the advice of writing a copy/assignment operator for your class in this case. Use a container of pointers and all STL requirements will be automatically fullfilled:
```

int main() 
{  //...
   foo *bar = new foo( hello );
   std::vector<foo*> *v_foo = new std::vector<foo*>();
   v_foo->push_back( bar ); // (1)
}

```

In (1) it is the pointer being copied. Which is always allowed, regardless of whether foo is copy-constructible, copyable or not.

Now, I noticed that you are always creating objects in the heap. Is that intended or are you just used to it from another language (Java)? My complete rewrite of your sample code would be:

```

class foo{
public:
	explicit foo(string const & t);
//	~foo(); // If the class is this simple, default destructor is ok
	void sayhello() const; // non-mutable operation: marked as const
	void changeName( string const & n ); 
private:
	string text_; // plain string
};

foo::foo(string const & t) // pass by constant reference
	: text_(t) // use initialization list whenever possible
{
}

void foo::sayhello() const {
	cout<<text_<<endl;
}

void foo::changeName( string const & n ) {
	text_ = n;
}

int main(){
	foo* bar = new foo("Hello World !"); // only if you do require bar to be heap allocated
	bar->sayhello();

	vector<foo*> v_foo; // (1)
	v_foo->push_back(bar); // pass pointer

	// (2)

	delete bar;
	return EXIT_SUCCESS;
}

```

Here (1) needs a little explanation. First, the vector is not allocated on the heap, but rather on the stack. Besides the fact that now foo is copy constructable and thus a vector of foo will compile, it may not be what you want, as it will create a second foo object that lives inside the vector. Any mutable operation in either bar or *v_foo.begin() will affect only one of the copies probably yielding unexpected behavior. Using a vector of pointers keeps just one instance of the object, and all operations (in (2)), will be visible from both bar and *v_foo.begin().

---

