---
title: "C++: Importing a member function from a less-specialized template class"
date: 2009-10-19
forum: Programming Talk
---

### Post by Habbit on 2009-10-19
Greetings, resident gurus. For a pet project I'm doing I find myself in need of some information, which the Holy Oracle Google has failed to uncover:

Let's say I have some class template, A<T>, which defines a member function "void foo(const T&);". Let's further say that I want to specialize that template, creating A<int>. As everybody knows, there is no "foo" defined by default, so I have to define it again (because I don't want my class to be some vector<bool>)... However, given that the implementation of A<int>::foo would be that of A<T>::foo with a simple s/T/int/g, can I be saved the task of writing it again? 

Here is a simplified version of my code: ```
template<typename NumT>
struct num_traits {
	// Generic low-performance implementation
	static NumT pow(NumT base, uint32_t exp) {
		NumT ret = 1;
		for (uint32_t i = 0; i < exp; ++i)
			ret *= base;
		return ret;
	}
};

template<>
struct num_traits<uint64_t> {
	// This fails, because the compiler thinks I'm trying to
	// import a member from the same class I'm writing
	using num_traits<uint64_t>::pow;
	
	// What I want is some magic line that saves me from writing this:
	static uint64_t pow(uint64_t base, uint32_t exp) {
		uint64_t ret = 1;
		for (uint32_t i = 0; i < exp; ++i)
			ret *= base;
		return ret;
	}
};
```

---

### Post by dwhitney67 on 2009-10-19
> **Habbit said:**
> ...
As everybody knows, there is no "foo" defined by default, so I have to define it again (because I don't want my class to be some vector<bool>)...

Uh no, I don't know.  What are you talking about?

> However, given that the implementation of A<int>::foo would be that of A<T>::foo with a simple s/T/int/g, can I be saved the task of writing it again?

s/T/int/g???  What's this?

Does the code below not meet your specifications?
```

#include <stdint.h>
#include <iostream>

template <class NumT>
struct NumTraits {
   static uint64_t pow(NumT base, uint32_t exp) {
      uint64_t ret = 1;
      for (uint32_t i = 0; i < exp; ++i) {
         ret *= base;
      }
      return ret;
   }
};


int main()
{
   NumTraits<uint64_t> nt;
   std::cout << "10^3 = " << nt.pow(10, 3) << std::endl;

   // or

   std::cout << "5^2 = " << NumTraits<uint64_t>::pow(5,2) << std::endl;
}

```

---

### Post by Habbit on 2009-10-20
> **dwhitney67 said:**
> Uh no, I don't know.  What are you talking about?When you specialize a template, you start from scratch and don't "inherit" any members from the parent (less-specialized) template. That's why I mentioned vector<bool>

> **dwhitney67 said:**
> s/T/int/g???  What's this?A textual substitution of T by int. Sorry, I thought a sed one-liner would be obvious enough in these forums.

> **dwhitney67 said:**
> Does the code below not meet your specifications?No, because I *need* num_traits<T> to be specialized for uint64_t for *other* reasons (say, another function "bar"). It's just the implementation of "foo" which would be the same in the general template and the specialized version.

---

### Post by dribeas on 2009-10-20
> **Habbit said:**
> ```
template<typename NumT>
struct num_traits {
	// Generic low-performance implementation
	static NumT pow(NumT base, uint32_t exp) {
		NumT ret = 1;
		for (uint32_t i = 0; i < exp; ++i)
			ret *= base;
		return ret;
	}
};
```

Just add a new level of indirection. Implement the operation as a free function template and just call it from within your traits:

```

namespace detail {
   template <typename T>
   T pow( T base, uint32_t exp ) 
   { ... }
}
template <typename T>
struct num_traits {
   static T pow( T base, uint32_t exp ) 
   { return detail::pow(base,exp); }
};
template <>
struct num_traits<uint64_t> {
   static uint64_t pow( uint64_t base, uint32_t exp )
   { return detail::pow(base,exp); }
};

```

---

### Post by TheStatsMan on 2009-10-20
If you want to only specialise some member functions then you can do it using static polymorphism

example:
```

template<typename T, typename TypeFooA>
class Foo
{
    public:
        void foo1{
            ...
        }
        void fooVar{
            vfunc.foo()
        }
        
    private:
        Variablefunc vfunc;

};
//this class contains functions you want to specialise
template<typename T>
class Foo1
{
    public:
        void foo(){
            ...
        }
};

//sepcialisation
template<>
class Foo1<specialtype>
{
    public:
        void foo(){
            ...
        }
};


int main()
{
    //instatiate as follows
    Foo<specialtype,Foo1<specialtype> >  classA;
}

```Let me know if this doesn't make sense. If it is just one small function you may not want to bother with this approach.

---

### Post by Habbit on 2009-10-20
Oh, now I see... Well, I had hoped a syntactically sweeter route would be possible, but it seems that it is not. Thanks to you both.

---

### Post by interval1066 on 2009-10-20
Curious to know what a "syntactically sweeter route" would be considering the problem you posed and what modern compilers are capable of. If you need to override virtual functions then TheStatsMan's solution is your best bet.

---

### Post by Habbit on 2009-10-20
Well, for me a better solution from the syntactic sugar standpoint would let the "using" keyword import members from a less-specialized class template into a specialization. In other words, the following code would be legal, and import the "pow" function from num_traits<T> into its specialized version: ```
template<typename NumT>
struct num_traits {
	static NumT pow(NumT base, uint32_t exp) {
		NumT ret = 1;
		for (uint32_t i = 0; i < exp; ++i)
			ret *= base;
		return ret;
	}
};

template<>
struct num_traits<uint64_t> {
	using num_traits<uint64_t>::pow; // Not legal C++
};
```

Currently, the "using" declaration with that syntax only lets you import members inherited from base classes (for example, that's how you'd make a member inherited from a private base visible). As a less-specialized version of a class template is not a supertype of the more-specialized version (and, in fact, both can have completely different inheritance hierarchies), the "using" declaration as-is does not work. My current implementation would be along the lines of this simplified snippet: ```
template<typename int_t>
struct num_traits_genimpl {
	static int_t pow(int_t base, uint32_t exp) {
		int_t ret = 1;
		for (uint32_t i = 0; i < exp; ++i)
			ret *= base;
		return ret;
	}
};

template<typename NumT>
struct num_traits;

template<>
class num_traits<int64_t> : private num_traits_genimpl<int64_t> {
	typedef num_traits_genimpl<int64_t> _genimpl;
public:
	using _genimpl::pow;
	// More members
};
```

---

