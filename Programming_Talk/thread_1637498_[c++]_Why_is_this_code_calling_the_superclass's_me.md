---
title: "[c++] Why is this code calling the superclass's methods instead of the subclass'?"
date: 2010-12-04
forum: Programming Talk
---

### Post by josephellengar on 2010-12-04
I have attached an archive with my code because there is enough that I can't just post it all in this thread. Anyway, the code seems to be consistently segfaulting in various functions and I have found that it is because the code is calling the superclass's methods, which do nothing. Did I do something wrong with the way I made my functions virtual? Any help would be immensely appreciated.

---

### Post by Queue29 on 2010-12-04
Multinumber looks like it should be an abstract base class.. it's implementation functions are all empty. If this is the case, your function prototypes should look like:

```
virtual Multinumber* operator+(Multinumber&) **= 0**;
```

And there is no need to have the Multinumber.cpp file with a bunch of empty functions.

---

### Post by GeneralZod on 2010-12-04
You've missed out a lot of information that would have been helpful ("calling the superclass's methods, which do nothing" - which class? which methods?) but as a wild stab in the dark, I'll note that none of the virtual operators in MultiNumber (operator+, operator=, etc) appear to be overridden anywhere (for an override to occur, the parameters of the overriding method must match that of the overridden method).

Edit:

Also, g++ quite rightly warns about this:

```

Multinumber& Multinumber::operator=(Multinumber& num)
{
    Multinumber toreturn;
    return toreturn;
}

```

This is undefined behaviour, and will likely cause a crash.

---

### Post by josephellengar on 2010-12-04
> **GeneralZod said:**
> You've missed out a lot of information that would have been helpful ("calling the superclass's methods, which do nothing" - which class? which methods?) but as a wild stab in the dark, I'll note that none of the virtual operators in MultiNumber (operator+, operator=, etc) appear to be overridden anywhere (for an override to occur, the parameters of the overriding method must match that of the overridden method).

Edit:

Also, g++ quite rightly warns about this:

```

Multinumber& Multinumber::operator=(Multinumber& num)
{
    Multinumber toreturn;
    return toreturn;
}

```

This is undefined behaviour, and will likely cause a crash.

The subclasses of Multinumber (Pairs, Complex, Rational) all have functions with covariant data types that override Multinumber's functions. Gdb gave me this output:

```


Starting program: /home/ross/flash/current/CS260/assignment6/exec 
First set:
{6+4i, 5+6i, 8-1i}
Test isfull (initial capacity 10): 0
Making second set with array.
Second set:
{7+6i, 11+22i}
Testing union of two sets and equals operator overload:

Program received signal SIGSEGV, Segmentation fault.
0x00000000004033d8 in operator<< (lhs=..., rhs=...) at Set.cpp:183
183	        lhs << rhs.setArray[i]->object2string() << ", ";

```

So it seems that the problem must be that nothing exists at index [i] of that array. What is up with that? I passed it a parameter in add element and the parameter was dynamically allocated, so what's the problem?

I feel like it has to be this function, that Multinumber's functions are getting called so when I use addElement, nothing is there.  Does anybody know?

```

bool Set::addElement(Multinumber* newElement)
{
	bool success = false;
	if(isFull())
	{
		resize();
	}
	if(!isMember(newElement))
	{
		setArray[numElements] = newElement;
		numElements++;
		success = true;
	}
	return success;
}

```

---

### Post by GeneralZod on 2010-12-04
> **rossholley said:**
> The subclasses of Multinumber (Pairs, Complex, Rational) all have functions with covariant data types that override Multinumber's functions. 


No, Pair, Complex and Rational do not overload any of MultiNumbers' operator+, operator=, operator== as their *parameter types* don't match.  When talking about overriding, "co-variance" is a property of the *return type*.

Aside from that: the cause of the crash is that each Set assumes ownership of its contained MultiNumbers (it deletes them all in the destructor), so copying a set and destroying the original, as happens in e.g. 

```

setc = seta.setUnion(setb);

```

will have setc holding onto a bunch of dangling pointers.

Edit:

Here's a run with some instrumentation put in:

```

First set:
{ ... attempting to print 0x987a0f8
6+4i,  ... attempting to print 0x987a110
5+6i, 8-1i}
Test isfull (initial capacity 10): 0
Making second set with array.
Second set:
{ ... attempting to print 0x987a140
7+6i, 11+22i}
Testing union of two sets and equals operator overload:
Set being deleted
 deleting element 0 **0x987a140**
 ...done
 deleting element 1 0x987a158
 ...done
 deleting element 2 0x987a0f8
 ...done
 deleting element 3 0x987a110
 ...done
 deleting element 4 0x987a128
 ...done
Deletion complete
{ ... attempting to print **0x987a140** <- Uh-oh - we just deleted this!

Program received signal SIGSEGV, Segmentation fault.
0x00000006 in ?? ()


```

---

### Post by josephellengar on 2010-12-04
> **GeneralZod said:**
> No, Pair, Complex and Rational do not overload any of MultiNumbers' operator+, operator=, operator== as their *parameter types* don't match.  When talking about overriding, "co-variance" is a property of the *return type*.

Aside from that: the cause of the crash is that each Set assumes ownership of its contained MultiNumbers (it deletes them all in the destructor), so copying a set and destroying the original, as happens in e.g. 

```

setc = seta.setUnion(setb);

```

will have setc holding onto a bunch of dangling pointers.

Edit:

Here's a run with some instrumentation put in:

```

First set:
{ ... attempting to print 0x987a0f8
6+4i,  ... attempting to print 0x987a110
5+6i, 8-1i}
Test isfull (initial capacity 10): 0
Making second set with array.
Second set:
{ ... attempting to print 0x987a140
7+6i, 11+22i}
Testing union of two sets and equals operator overload:
Set being deleted
 deleting element 0 **0x987a140**
 ...done
 deleting element 1 0x987a158
 ...done
 deleting element 2 0x987a0f8
 ...done
 deleting element 3 0x987a110
 ...done
 deleting element 4 0x987a128
 ...done
Deletion complete
{ ... attempting to print **0x987a140** <- Uh-oh - we just deleted this!

Program received signal SIGSEGV, Segmentation fault.
0x00000006 in ?? ()


```

What would you suggest I change my parameter types to then? Do I need to change the parameter types? But I do understand what you mean about deleting the elements. That was dumb of me.

---

### Post by GeneralZod on 2010-12-04
> **rossholley said:**
> What would you suggest I change my parameter types to then?

*If* you want those operators to be virtual, then I don't really see any other option but for the parameters to always be Multinumbers i.e.


```

Rational::operator+(const Multinumber &rhs) 

```

instead of

```

Rational::operator+(const Rational &rhs) 

```

which, of course, throws up plenty of other issues :/

What is the goal of this assignment?

---

### Post by josephellengar on 2010-12-04
> **GeneralZod said:**
> *If* you want those operators to be virtual, then I don't really see any other option but for the parameters to always be Multinumbers i.e.


```

Rational::operator+(const Multinumber &rhs) 

```

instead of

```

Rational::operator+(const Rational &rhs) 

```

which, of course, throws up plenty of other issues :/

What is the goal of this assignment?

The goal of the assignment is polymorphism. But I originally had those parameters as Multinumber and my prof explicitly said that that was wrong. I am so confused. The summary in the specs is:
```

Design and implement a Set that stores objects of type MultiNumber. A ‘set’ is a collection of
entities that share some common properties. Elements in a Set are typically not ordered. A set may
not contain duplicates. Elements in the Set are stored using some aggregate data type, such as an array.
For this project, you will use dynamic memory management, i.e. elements will be stored in a dynamic
array. Complex and Rational are specializations of MultiNumber. Therefore, the user should be
able to manipulate Sets of Complex numbers, or Rational numbers. However, the user should not
be able to create Sets of MultiNumbers.

```

---

### Post by GeneralZod on 2010-12-04
Is there any part of the specs that actually *says* that you should be able to e.g. add two Multinumbers together, or anything about the set of methods/ operations a so-called "Multinumber" should be able to perform? There's no mention of it in the excerpt given.  

It could be the case that she doesn't care about that and only cares about you creating a Set class that is able to store a bunch of items in some arbitrary class hierarchy.

---

### Post by josephellengar on 2010-12-04
> **GeneralZod said:**
> Is there any part of the specs that actually *says* that you should be able to e.g. add two Multinumbers together, or anything about the set of methods/ operations a so-called "Multinumber" should be able to perform? There's no mention of it in the excerpt given.  

It could be the case that she doesn't care about that and only cares about you creating a Set class that is able to store a bunch of items in some arbitrary class hierarchy.

No. The specs say specifically that Multinumber should never be instantiated. Everything is just a Multinumber*.

---

### Post by worksofcraft on 2010-12-04
> **rossholley said:**
> No. The specs say specifically that Multinumber should never be instantiated. Everything is just a Multinumber*.

As Queue29 said in post #2 you need to make Multinumber a **virtual base class** (by defining at least one of it's virtual method = 0).

That will ensure that they are never instantiated. You can handle all the derived classes as references or pointers to Multinumbers knowing they will never actually be one.

---

