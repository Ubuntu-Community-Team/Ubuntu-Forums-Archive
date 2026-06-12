---
title: "A question about operator overloading"
date: 2011-02-09
forum: Programming Talk
---

### Post by TheHimself on 2011-02-09
Imagine we have a class which has a variable length array as a part. If we want to overload the = operator for this class we need to allocate some memory for the new object (for a in a=b). Now if we want to overload + as well we need to allocate memory for the result.

 This implies that already in something like a=b+c we a have memory leak! The reason is that some memory is allocated to store the result of b+c and then another chunk of the same size is allocated for a. Am I missing something?

---

### Post by MadCow108 on 2011-02-09
that what destructors are for.
in the destructor you free the memory again.

a=b+c; does following:
use binary + operator to create temporary result b+c
use assignment operator (or copy constructor) to assign temp result to a
destroy temporary result b+c

---

### Post by worksofcraft on 2011-02-09
> **MadCow108 said:**
> that what destructors are for.
in the destructor you free the memory again.

a=b+c; does following:
use binary + operator to create temporary result b+c
use assignment operator (or copy constructor) to assign temp result to a
destroy temporary result b+c

This is in deed an essential purpose for destructors

another consideration is that the compiler optimization is usually smart enough to construct temporary result b+c right where the final result needs to be (in a) so that it doesn't have to call the copy constructor on return from your overloaded + operator.

---

### Post by MadCow108 on 2011-02-09
> **worksofcraft said:**
> This is in deed an essential purpose for destructors

another consideration is that the compiler optimization is usually smart enough to construct temporary result b+c right where the final result needs to be (in a) so that it doesn't have to call the copy constructor on return from your overloaded + operator.

dependent on the complexity of the operators the compiler may not be able to avoid the temporary.
To avoid unnecessary temporaries one can use e.g. expression templates.
Very useful for linear algebra computations (see e.g. Blitz++).

or you can use unary operators

---

### Post by TheHimself on 2011-02-09
Thanks. I wrote a destructor for the class and put a print command in it. For a short program which simply declares 3 objects a,b,c and then
```
c=a+b
```

the destructor was called 4 times. I think once for each of a,b,c and once for the result of a+b. Interesting!

---

### Post by worksofcraft on 2011-02-09
> **TheHimself said:**
> Thanks. I wrote a destructor for the class and put a print command in it. For a short program which simply declares 3 objects a,b,c and then
```
c=a+b
```

the destructor was called 4 times. I think once for each of a,b,c and once for the result of a+b. Interesting!

That's strange...

it only gets called 3 times for me :shock:
```

$ g++ destruct.cpp
$ ./a.out
mystruct destroyed with i=3
mystruct destroyed with i=2
mystruct destroyed with i=1

```

is the output from this:
[php]
// g++ destruct.cpp
#include <cstdio>

struct my_struct {
	int i;
	// no implicit type casts
	explicit my_struct(int ii): i(ii) {}

	// log destructions
	~my_struct() {
		printf("mystruct destroyed with i=%d\n", i);
	}


private:
	// invalidite copying
	my_struct & operator= (const my_struct &);
//	my_struct(const my_struct &);
};

my_struct operator+ (const my_struct &a, const my_struct &b) {
		return my_struct(a.i + b.i);
}

int main() {
	my_struct a(1), b(2);
	my_struct c = a+b;
	return 0;
}
[/php]

---

### Post by MadCow108 on 2011-02-09
in this simple case the compiler can do *named return value optimization*
do this:
```

my_struct c = a+b+b;

```
and you have a temporary a+b created.
This temp can be expensive (e.g. allocation of an temporary buffer when the buffer c could be used directly)

this situation can be avoided with move sematics instead of copy which is included in c++0x:
[http://anubis.dkuug.dk/jtc1/sc22/wg21/docs/papers/2002/n1377.htm](http://anubis.dkuug.dk/jtc1/sc22/wg21/docs/papers/2002/n1377.htm)


the optimization can also break down for a+b for certain operator implementations.
e.g. when you change your operator to this (just an example, you can get the optimization to work again with a simple change):
```

my_struct operator+ (const my_struct &a, const my_struct &b) { 
  my_struct tmp(a.i+b.i);
  if (a.i == 3)
    return my_struct(5);
  return tmp;
} 

```
> 
mystruct destroyed with i=3
mystruct destroyed with i=3
mystruct destroyed with i=2
mystruct destroyed with i=1



---

### Post by worksofcraft on 2011-02-09
> **MadCow108 said:**
> in this simple case the compiler can do *named return value optimization*
do this:
```

my_struct c = a+b+b;

```
and you have a temporary a+b created.
This temp can be expensive (e.g. allocation of an temporary buffer when the buffer c could be used directly)

this situation can be avoided with move sematics instead of copy which is included in c++0x:
[http://anubis.dkuug.dk/jtc1/sc22/wg21/docs/papers/2002/n1377.htm](http://anubis.dkuug.dk/jtc1/sc22/wg21/docs/papers/2002/n1377.htm)


the optimization can also break down for a+b for certain operator implementations.
e.g. when you change your operator to this (just an example, you can get the optimization to work again with a simple change):
```

my_struct operator+ (const my_struct &a, const my_struct &b) { 
  my_struct tmp(a.i+b.i);
  if (a.i == 3)
    return my_struct(5);
  return tmp;
} 

```

That is true, but OTOH, there **is** a conceptual intermediate result in that c = a+b+b; It might not be very evident with this trivial class that just contains an integer, but say it was some kind of multi dimensional array then it does have to exist somewhere at some stage!

IMO it wouldn't be right to construct it as a premature "c" and then construct another final result over the top as other elements in the temporary may be used while calculating the new ones in the result (e.g. matrix multiply).

In the case where you really wanted that to happen then you could always program it with appropriate statements e.g. using a += operator as the second step. 

IMO the current return result optimization with conditionals is perhaps over cautious. TBH, I think the language could have been improved by having explicit ability to identify said result that you are working on before actually returning: I had some vague idea of "that" pointer in analogy to the "this" pointer we already know...

Now when it comes to "move semantics" I must say I currently think it's yet another one of those things in the new c++0x standard that is just going beyond what still allows reasonable maintainability of C++ code but that was topic of[ a different tread]("http://ubuntuforums.org/showthread.php?t=1681934") recently ;)

---

