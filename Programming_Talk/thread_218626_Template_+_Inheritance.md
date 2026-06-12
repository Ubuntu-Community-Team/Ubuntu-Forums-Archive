---
title: "Template + Inheritance"
date: 2006-07-18
forum: Programming Talk
---

### Post by era86 on 2006-07-18
Lets say I have a class A

template< typename T >
class A
{
protected:
int i;
};

and class B

template< typename T >
class B : public A< T >
{
public:
int geti( void ) { return i; }
};

now geti should be able to access i in A right?

---

### Post by LordHunter317 on 2006-07-18
This code works for me with MS VC++:```
#include <iostream>

namespace
{
	template<typename T>
	class A
	{
	protected:
		int i_;

	public:
		explicit A(int i) : i_(i)
		{}
	};

	template<typename T>
	class B : public A<T>
	{
	public:
		explicit B(int i) : A(i)
		{}
		
		int i() const { return i_; }
	};
}

int
main()
{
	B<int> foo(5);

	std::cout << foo.i() << "\n";
}
```Next time, I recommend trying something this simple for yourself.  Then, if you don't understand why, ask why. :)

---

### Post by era86 on 2006-07-19
Sorry. I guess it's my compiler. It wasn't working for me that's why I asked. Sorry again!

---

### Post by LordHunter317 on 2006-07-19
In that case, posting the compiler error messages would have been helpful.  Always give all the information you have.

---

### Post by era86 on 2006-07-19
Ok.. this will not compile for me, I am guessing I did it right, but the compiler says that i was not declared in this scope.

template< typename T >
class A
{
protected:
int i;
};

template< typename T >
class B : public A< T >
{
public:
int geti( void ) { return i; }
void seti( int j ) { i = j }
};

int main ( void )
{
B< int > foo;

foo.seti( 5 );

std::cout << foo.geti() << "\n";

return 0;
}

main.cpp: In member function &#8216;int B<T>::geti()&#8217;:
main.cpp:29: error: &#8216;i&#8217; was not declared in this scope
main.cpp: In member function &#8216;void B<T>::seti(int)&#8217;:
main.cpp:30: error: &#8216;i&#8217; was not declared in this scope

---

### Post by LordHunter317 on 2006-07-19
No, it's a name scoping rule that strictly-confirming compilers flag (and MSVC does if you turn off extensions via /Za).

Anyway, due to specialization rules, the compiler can't actually assume that any inherited memebers exist in a templated base class.  

I could do something like this:```
template <typename T>
class Base {
public:
   bool isFoo() const { // something about foo }
   bool isBar() const { // something about bar }
};

template<>
class Base<MyType> {
public:
   // don't define isFoo
   bool isBar() const { // something about bar }
};
```Now, if I define an class inheriting base like so:```

template<typename T>
class Child : public Base<T> {
public:
   bool doTest() const { isFoo(); }
}
```it's obvious that this won't work if the template parameter for Child is 'MyType', because Base<MyType> doesn't have a definition for 'isFoo()'. 

As such, all names in a templatized base class are hidden.  There are three solutions:[list=1][*]Use this-> to implicitly note that the member is inherited[*]Use a using declaration to import the function from the base class scope[*]Use an explict scope declaration.  This is undesirible for virtuals because it kills dynamic binding but is **mandatory** in a few situations, mainly accessing the base constructor in an initialization list.[/list]

Anyway, my corrected code is as follows:```
#include <iostream>

namespace
{
	template<typename T>
	class A
	{
	protected:
		int i_;

	public:
		explicit A(int i) : i_(i)
		{}
	};

	template<typename T>
	class B : public A<T>
	{
	public:
		explicit B(int i) : A<T>::A(i)
		{}
		
		int i() const { return this->i_; }
	};
}

int
main()
{
	B<int> foo(5);

	std::cout << foo.i() << "\n";
}
```I trust you can fix your code based on this.  

BTW, Scott Meyer covers this in Item 43 of *Effective C++*.  Thanks to Scott for beating me with the correctness hammer again.

---

### Post by era86 on 2006-07-19
Wow.. thank you so much for that. You definately helped me clear up some things!

---

