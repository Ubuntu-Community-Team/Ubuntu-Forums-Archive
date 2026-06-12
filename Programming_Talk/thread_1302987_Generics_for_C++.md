---
title: "Generics for C++ ?"
date: 2009-10-27
forum: Programming Talk
---

### Post by shynthriir on 2009-10-27
In Ada there are things called generics, which are kinda like classes I guess, but when you create an instance of a generic, you provide types that belong with it.

In a simple example, you could write a generic function that adds two numbers. Then you can create an instance of that function with int types, to add ints, or float types to add floats, ettc. I know that can be done with overloading, but generics go a step further.

For what I'm doing, I want to create a linked list class, with a list of structs that contain a next pointer, a previous pointer, and then data. The pointers will of course be of the type of the struct, but the data I want to be able to pass in what type of data it is (for each linked list object, that data won't change, but I want to be able to have multiple linked list objects, each one might have a different data type).

If anyone gets what I'm talking about, please let me know.

---

### Post by MadMan2k on 2009-10-27
templates

---

### Post by MadCow108 on 2009-10-27
as said before this is called templates in C++ and there is a whole bunch of generic algorithms in the STL (Standard Template Library) which cover a very wide range of applications
[http://www.cplusplus.com/reference/stl/](http://www.cplusplus.com/reference/stl/)
also a generic linked list already exists: [http://www.cplusplus.com/reference/stl/list/](http://www.cplusplus.com/reference/stl/list/)

small example:
```

#include <iostream>

template<typename T>
T div(T a, T b)
{
  return a/b;
}

int main(void)
{
  double res = div<double>(4.0,3); // explicitly instantiation div of type double, double (-> implicit int->double conversion on 3)
  std::cout << res << std::endl; //1.33
  res = div(4,3); // instantiates div<int> as arguments can be identified as int, int
  std::cout << res << std::endl; //1
}
```

---

### Post by dribeas on 2009-10-27
Templates in C++ is a really complex and powerful tool, much more powerful than generics in either C# or Java. I do not know about ADA generics (but I am interested, so I fire up here some questions if you care to enlighten us).

One of the features that is not present in C# or Java is the specialization of templates: once you define a generic way of performing an operation, you can redefine the same operation in a different more specialized way for a concrete type.

As a simple example, std::advance is defined as:
```

template <class InputIterator, class Distance>
void advance(InputIterator& i, Distance n);

```

And has the effect of advancing the iterator 'n' times. The code is defined for a generic iterator that only has the pre-increment operator, but it is also redefined for random access iterators that implement the 'iterator + distance', so the real implementation complexity is constant for random access iterators while linear for iterators where it cannot be performed faster.

Another example is std::vector<> that has a common implementation for all types but bool. In the bool case it is optimized for memory usage and each bit takes exactly one bit of memory, unlike a regular bool that has an undefined size (in many compilers as much as 4 bytes).

An important feature of templates in C++ is SFINAE (Substitution Failure Is Not An Error), that means that when the compiler determines that a template can be a match for a given group of parameters, if substitution of the types and values into the appropriate template arguments fail, that is not flagged as a compiler error. Only when all possible matching templates have failed and there is no non-templated function that can be applied to that set of arguments the compiler gives up and yields an error.

This is actually some kind of meta-specialization of templates in the sense that it is used to provide different template specializations knowing that in some cases the compiler will fail to match against one template, and then try with a less specialized template and fail (or not)...  The compiler thus selects the best algorithm that can be applied to the actual types.

Are any of these two features present in the ADA generic system?

---

### Post by phrostbyte on 2009-10-27
> **dribeas said:**
> Templates in C++ is a really complex and powerful tool, much more powerful than generics in either C# or Java. I do not know about ADA generics (but I am interested, so I fire up here some questions if you care to enlighten us).

One of the features that is not present in C# or Java is the specialization of templates: once you define a generic way of performing an operation, you can redefine the same operation in a different more specialized way for a concrete type.

As a simple example, std::advance is defined as:
```

template <class InputIterator, class Distance>
void advance(InputIterator& i, Distance n);

```

And has the effect of advancing the iterator 'n' times. The code is defined for a generic iterator that only has the pre-increment operator, but it is also redefined for random access iterators that implement the 'iterator + distance', so the real implementation complexity is constant for random access iterators while linear for iterators where it cannot be performed faster.

Another example is std::vector<> that has a common implementation for all types but bool. In the bool case it is optimized for memory usage and each bit takes exactly one bit of memory, unlike a regular bool that has an undefined size (in many compilers as much as 4 bytes).

An important feature of templates in C++ is SFINAE (Substitution Failure Is Not An Error), that means that when the compiler determines that a template can be a match for a given group of parameters, if substitution of the types and values into the appropriate template arguments fail, that is not flagged as a compiler error. Only when all possible matching templates have failed and there is no non-templated function that can be applied to that set of arguments the compiler gives up and yields an error.

This is actually some kind of meta-specialization of templates in the sense that it is used to provide different template specializations knowing that in some cases the compiler will fail to match against one template, and then try with a less specialized template and fail (or not)...  The compiler thus selects the best algorithm that can be applied to the actual types.

Are any of these two features present in the ADA generic system?

That vector<bool> thing is very cool. 

I think one reason bool might take 1-4 bytes is testing a single bit in many processors is more processor intensive then testing a single byte or even a 32/64-bit word. ](*,)

---

### Post by dribeas on 2009-10-28
> **phrostbyte said:**
> That vector<bool> thing is very cool. 


Don't say that too loud... The specialization feature of C++ templates is a good thing, but most people in the C++ standard committee regret std::vector<bool> for other reasons (such as it not fulfilling the requirements of an STL container, or how the proxy iterators work to deal with the fact that dereferencing the iterator you get to a concrete bit inside another (implementation defined) type)... but yes, being able to override behavior for some particular types is a very powerful tool.

---

### Post by MadCow108 on 2009-10-28
for those reasons vector<bool> will be removed in c++0x and replaced by dynamic_bitset which is not anymore a container in the sense of the others.
There'll also be some macros and defines to ensure compatibility with "old" code

---

