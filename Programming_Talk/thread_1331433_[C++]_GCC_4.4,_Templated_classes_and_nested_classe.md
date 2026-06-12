---
title: "[C++] GCC 4.4, Templated classes and nested classes"
date: 2009-11-19
forum: Programming Talk
---

### Post by deadimp on 2009-11-19
I'm having trouble compiling code with classes nested inside a templated class, at least with my version of GCC.

I am trying to build the following code:
```
	template<typename T>
class A
{
	T x;
public:
	class D
	{
		T x;
	};
};

	template<typename T>
class B : public A<T>
{
public:
	void stuff()
	{
		D b;
	}
};

int main()
{
	A<int>::D x;
	return 0;
}
```

The errors returned are:
```
test.cpp: In member function ‘void B<T>::stuff()’:
test.cpp:23: error: ‘D’ was not declared in this scope
test.cpp:23: error: expected ‘;’ before ‘b’
```

If I remove the templates and typedef T as an int, I receive no errors.

I have compiled this on a different version of GCC (a remote one on our school's servers) and it works fine.

Anyone know why this happens? Anyone know of a workaround?

My local GCC version output is "gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8)".
The remote version is "gcc version 3.2.2 20030222 (Red Hat Linux 3.2.2-5)".

---

### Post by dwhitney67 on 2009-11-19
Try
```

void stuff()
{
   typename A<T>::D b;
}

```
Btw, do you realize that class D's member data is private, right?  In other words, as it is, you will not have access to it.

---

### Post by Habbit on 2009-11-19
An explanation for dwhitney's suggestion: your class template B is inheriting from A<T>, which is a not-fully-determined template class. Then, you try to instance A<T>::D (actually, plainly D), which is a member of A<T>... It should work, right?

Wrong. Imagine there was a specialization A<char> which didn't contain D as a member type. As this is allowed by the language, it does not recognize dependent names as types unless you so specify (with the "typename" keyword). Then, you are assuring the compiler that A<T>::D shall exist and be a type, so the template itself will compile, but an error would be raised when instantiating B<char>, for it would require the inexistent type A<char>::D.

---

### Post by dribeas on 2009-11-19
> **Habbit said:**
> Wrong. Imagine there was a specialization A<char> which didn't contain D as a member type. As this is allowed by the language, it does not recognize dependent names as types unless you so specify (with the "typename" keyword).

That is actually the second part of the problem, but before that comes into play, the issue is why D is not recognized (not as a type, but recognized at all).

When you write:

```

template <typename T> class A { ... }; //indentation define for concision, not readability here
template <typename T> class B : public A<T> {
   void func() {
      D x;
   }
}

```

The compiler cannot determine by itself that D is a dependent name, and you must help it there (not with the typename keyword, but rather with the full specification of what D is):

```

//...
void func() {
   A<T>::D x;
}

```

At this point the name has become dependent (it is a subpart of A<T> that depends itself on the template argument T), and the concrete error in the question will go away. Now the problem is the one that Habbit addresses:

'error: dependent-name ‘A::D’ is parsed as a non-type, but instantiation yields a type'

The name is identified by the compiler as a dependent name, and A is a class template and it assumes that D will be a static member of class template A, instead of a type within the first pass check of the templated code, but during the second pass (with the concrete type instantiated into the template) the dependent name becomes a type. That is where adding the typename keyword helps:

```

//...
void func() {
   typename A<T>::D x;
}

```

When you add the typename keyword you are telling the compiler that the dependent name must be considered as a type during the first pass compilation checks of the template.

---

