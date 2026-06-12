---
title: "Question about overloaded operators"
date: 2009-08-03
forum: Programming Talk
---

### Post by Volt9000 on 2009-08-03
I'm working on a matrix class in C++ and have overloaded the parentheses () operator to provide me with element-level access to the matrix elements. I have two overloaded operators like this: one for read-only access to the elements, and one to modify.

However I'm confused as to why the program is using the modifying version instead of the read-only version when I'm simply accessing the element.

I've attached the source to a very-stripped down class along with a test program. I would expect the output to be

```

Modify
Access
Access

```

but instead I get 3 "Modify"s. Perhaps someone can explain to me why this is, and how I can fix it?


I should also note that I've tried the accessor function with a const in front of it, thusly:

```

const double operator()(int, int) const;

```

but I still get the same results.

---

### Post by Habbit on 2009-08-04
The const-version of your method will be used if invoked on a const-object. If the object is not const itself, or being accessed through a const-reference or pointer-to-const, the modifier version will be called even if the return value (which, for a modifier, should be double& and not double) is not actually modified.

---

### Post by dwhitney67 on 2009-08-04
I looked at the OP's code, and it appears that he has defined his overloaded operator()(int, int) correctly, although personally I would have used size_t in lieu of int, and I would have defined the parameters as const.

BEGIN EDIT:  I was wrong below..... IGNORE IGNORE IGNORE
The only issue I found with the code is his access to the array of values; for example:
```

return _data[row * _cols + col];

```
I may be wrong (once again I am posting early in the morning), but instead, shouldn't that be:
```

return _data[row * _rows + col];

```
END EDIT
----------------------------------------------------------------------------
Also, the OP may want to place some error-checking in his accessors so that illegal row/col values are screened out.  Maybe use an assert() or throw an exception.

One last thing... a destructor is needed to free the allocated memory.  Alternatively, store the _data in an auto_ptr.

---

### Post by Habbit on 2009-08-04
> **dwhitney67 said:**
> Alternatively, store the _data in an auto_ptr.
std::auto_ptr will use "delete _data;". The OP needs to use "delete**[]** _data;".

Furthermore, instead of using memset, I would use one of the algorithms in the standard C++ library, such as fill_n. The line ```
memset(_data, 0, _rows * _cols * sizeof(double));
``` would become ```
fill_n(_data, _rows * _cols, 0.0);
```

---

### Post by dwhitney67 on 2009-08-04
> **Habbit said:**
> std::auto_ptr will use "delete _data;". The OP needs to use "delete**[]** _data;".

Yes, thanks for pointing that out; I discovered this issue moments after I posted my reply when I wrote a test program, and ran it with valgrind.

---

### Post by Volt9000 on 2009-08-04
> **Habbit said:**
> The const-version of your method will be used if invoked on a const-object. If the object is not const itself, or being accessed through a const-reference or pointer-to-const, the modifier version will be called even if the return value (which, for a modifier, should be double& and not double) is not actually modified.

I see. So, then is there any way to "force" the program to invoke the const-method? Perhaps by redefining the signature? I only ask because what I would like to be able to do is to calculate things like the determinant and adjoint and store them, so if the user requests them again, as long as the matrix doesn't change, they won't have to be recalculated.

And BTW, the modifier function's return value is indeed double&.

> **dwhitney67 said:**
> I looked at the OP's code, and it appears that he has defined his overloaded operator()(int, int) correctly, although personally I would have used size_t in lieu of int, and I would have defined the parameters as const.

Why size_t instead of int? Isn't size_t just a typedef'd unsigned int? If so, why not just use unsigned?

> Also, the OP may want to place some error-checking in his accessors so that illegal row/col values are screened out.  Maybe use an assert() or throw an exception.
Already have that in my class. The one I posted here was just a heavily-stripped version of the one I implemented for the sake of conciseness.

> One last thing... a destructor is needed to free the allocated memory.  Alternatively, store the _data in an auto_ptr.
Already have that too, see above. :)


> **Habbit said:**
> Furthermore, instead of using memset, I would use one of the algorithms in the standard C++ library, such as fill_n. The line ```
memset(_data, 0, _rows * _cols * sizeof(double));
``` would become ```
fill_n(_data, _rows * _cols, 0.0);
```
I was originally going to use this, but I read somewhere than the fill_n function is inherently less efficient (slower?) than memset because of the way it's implemented.

Is there any advantage to using one over the other? Is fill_n just more C++-ish?

---

### Post by dwhitney67 on 2009-08-04
Go with what works.  I don't think you can get more efficient than memcpy().  I'm ol' school, so I have been using memcpy() for more than 20 years; maybe bytes have "shrunk" since then.

---

### Post by Habbit on 2009-08-04
> **Volt9000 said:**
> Is there any advantage to using one over the other? Is fill_n just more C++-ish?

Using fill_n is safer and more consistent across all uses. While [FONT="monospace"]memset[/FONT] copies the same *byte* over all memory positions in the range, [FONT="monospace"]fill_n[/FONT] assigns every *T*/double slot in the range the value you passed.

In this case you were lucky that the bit pattern for 0.0 was all zeros, or, in fact, some bit pattern with all bytes in each T/double identical to each other (by the way, didn't new[] default-initialize arrays, which for POD types means zero-initialization?). In other words, had you wanted to initialize the array to, say, 1.0, memset would have not cut it, while fill_n would have worked just the same, and without having to worry about sizeof(double) and IEEE-754 bit patterns.

---

### Post by Volt9000 on 2009-08-04
Alright.
What about my original query?

What I'd like to do is calculate certain computationally-heavy properties only once, and then access the saved values whenever the user requests them, and calculate only as necessary. The only time I would have to recalculate is when the user changes an element, hence the problem.

Bottom line:
I need to be able to distinguish between an element access just for reading, or an element access for changing.

Any way to do this?

---

### Post by Habbit on 2009-08-04
That usually calls for the concept of a "property". One way to implement them is Java-like accesor methods: "const T& getX() const" and "void setX(const T&)" methods. When you set the property value in the setX method, you perform all required heavy computations, so that getX only performs fast reads.

A more C++-ish, but more requiring of the programmer, would be to use some T_proxy class to implement the get/set semantics: you'd have an "operator T() const" which would do the "get", and implement an overloaded "Tproxy& operator=(const T&)" assignment operator to do the "set" and perform your computations. Your class would then expose these Tproxy instances instead of instances of T itself.

This last approach certainly looks _way_ cleaner on user code, but is more of a pain to the implementer: you have to weigh the pros and cons.

---

### Post by Volt9000 on 2009-08-04
> **Habbit said:**
> That usually calls for the concept of a "property". One way to implement them is Java-like accesor methods: "const T& getX() const" and "void setX(const T&)" methods. When you set the property value in the setX method, you perform all required heavy computations, so that getX only performs fast reads.

A more C++-ish, but more requiring of the programmer, would be to use some T_proxy class to implement the get/set semantics: you'd have an "operator T() const" which would do the "get", and implement an overloaded "Tproxy& operator=(const T&)" assignment operator to do the "set" and perform your computations. Your class would then expose these Tproxy instances instead of instances of T itself.

This last approach certainly looks _way_ cleaner on user code, but is more of a pain to the implementer: you have to weigh the pros and cons.

I really wanted to avoid the Get and Set functions, they're kind of a pain. It's a helluva lot easier to just use () as I'm doing.

Even if I use those proxies as you suggested, wouldn't I just run into the same problem as I am now? That non-const accesses will call the modifier function instead of the read-only function?

---

### Post by issih on 2009-08-04
I suspect this is exactly what habbit was describing, but you could have it so that the accessor method () returns a proxy object that wraps the pointer to the matrix element, rather than returning the pointer itself.

You then have the proxy object overload the assignment operator "=" so that when you set the proxy object equal to a new value it can set the new value and kick off any required reprocessing.

you essentially implement a pointer class that overloads the assignment operator.

Hope that helps

---

### Post by dribeas on 2009-08-06
You cannot control from within your class which overload will be called. From the user code you can use explicit casts to downgrade a non-const reference into a const reference. The problem is that this will be cumbersome for the user.

The proposed solution of offering a proxy object that provides an operator= overload that takes a double as argument is good even if limited. It is impossible to provide a clear, transparent proxy into another object, but you can get close to it. The problem is that the user will have the fake idea that she is working with real double's inside your matrix and some operations will fail abruptly or even become impossible. For most cases it will be nice and fancy but it can bite back.

The proposed proxy would have a operator=(double) that will flag the matrix as modified and produce the change. That operation is clear in semantics. You would also need a cast operator into double so that the user can read the value without changing it so the interface would offer:

```

class proxy
{
// constructors and other details ommited
   operator double () const;     // obtains  value (read only)
   proxy& operator=( double d ); // flags change
};

```

Now this allows for the following uses:

```

void f1( double d );
void f2( double const & d );
void f3( double & d );

void test( Matrix & matrix, size_t i, size_t j ) {
   double v = matrix( i, j ); // accessor will return proxy, will cast into double
   matrix(i,j) = 10.5; // accessor will return proxy, proxy will use operator=
   f1( matrix(i,j) );  // proxy and cast
   f2( matrix(i,j) );  // proxy and cast will create temporary, const & bound to temporary
// f3( matrix(i,j) );  // fail: cannot obtain non-const & from proxy
}

```

As you see, you cannot call a function that takes a double as a non-const reference. That requires a non-temporary double object to bind the reference to. Calling such a function with te intermediate object would require:

```

double tmp = matrix( i, j ); // access in a read-only fashion
f3( tmp );                   // call f3 with the auto variable
matrix( i, j ) = tmp;        // set the value back into the array 

```

Which is rather cumbersome. Of course, there are only so many functions that take doubles as references, so it might be admisable. Any attempt to provide a transparent solution by creating a conversion from the proxy into a non-const reference will endup either with ambiguities that the caller will have to deal with (in the same way that she would have to do to force calling the const matrix accessor in the first time and thus the added complexity would be worthless)

Besides the strangeness in the behavior shown above, the proxy will add an extra cost to all operations that work on a non-const matrix (you could keep the non-proxied version in the constant accessor). The cost, assuming perfect inlining of all proxy calls and RVO when possible, would be at least the cost of copying a reference/pointer into the matrix plus the offset (either as a pointer to the real value, an offset into the _data array or the two coordinates).

---

### Post by issih on 2009-08-07
Nice post dribeas, well thought out, I'd not spent nearly that much effort on it :)

---

