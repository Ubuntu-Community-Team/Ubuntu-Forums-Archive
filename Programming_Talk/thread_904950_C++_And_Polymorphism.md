---
title: "C++ And Polymorphism"
date: 2008-08-29
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-29
I started with Java then came to C++
So here are questions about polymorphism

Say i have classes like this
[PHP]class Base {
	public:
		virtual void func0();
}

class Kid1: public Base {
	public:
		void func0() {
			/*does somthing*/
		}
		int func1() {
			return 1;
		}
}

class Kid2: public Base {
	public:
		void func0() {
			/*does somthing else*/
		}
		int func2() {
			return 2;
		}
}[/PHP]

These are tasks that could be accomplished in Java, how about c++. Please tell me if there are any dangers regarding this (data loss, error, core dumps, etc.).

I didn't write all the inits and stuff, just assume. Please know a little Java so you can relate and explain better

```
/*Task 1*/
Base b0 = Kid1();
b0.func0;

/*Task 2*/
Base b0 = Kid1();
b0.func0;
Kid1 k0 = (Kid1)b0;

/*Task 3*/
Base * b0 = new Base[2];
b0[0] = Kid1();
b0[1] = Kid2();
b0[0].func0();
b0[1].func0();
```

---

### Post by dwhitney67 on 2008-08-30
It can be done in C++.

A couple things to you need to address though...

For your Base class as defined in your OP, you will need to implement the func0() method.  Alternatively you can declare func0() to be "pure virtual"; that is, assign a zero to the end of it.  This will make Base an abstract class.
[PHP]virtual void func0() = 0;[/PHP]

Concerning the "main" program, remember that in Java you have "handles", but in C++ you have objects declared on the stack or allocated from the heap.

So to test polymorphism in C++, something like the following will work (barring of course any compile problems I may have introduced!):

[php]
/*Task 1*/
Base *b0 = new Kid1();
b0->func0();

/*Task 2*/
Base *b1 = new Kid1();
b1->func0();
Kid1 *k1 = dynamic_cast<Kid1*>(b1);
b1->func1();   // will not compile!
k1->func1();   // ok
k1->func0();   // ok

/*Task 3*/
Base *b2[2];
b2[0] = new Kid1();
b2[1] = new Kid2();
b2[0]->func0();
b2[1]->func0();

/*Task 4*/
Kid1 k2;
Base *b3 = &k2;
b3->func0();

/*Task 5*/
Kid2 *nullKid = dynamic_cast<Kid2*>(b3);   // dynamic_cast fails!

...
[/php]
P.S.  Avoid using C-style casts when converting from a Base-object to a child-object.  Use dynamic_cast<> to ensure that the object is indeed the object you expect it to be.  If the object is something other than what you expect, dynamic_cast<> returns a null pointer.

---

### Post by Mr.Macdonald on 2008-08-30
how about these

So if i wished to have an array of Bases that could be casted to children i need
```
Base ** bases = new Base*[10]
bases[0] = new Kid1()
(dynamic_cast<Kid1*>(bases[0])).func1();
```

and how about overriding a data type
[PHP]class Par {
	int dat;
}

class Kid {
	double dat;
}[/PHP]

do i need
virtual int dat;

---

### Post by dribeas on 2008-08-30
You can downcast any time you want:

```
Base *b = new Derived;
dynamic_cast<Derived*>(b)->exec_derived_only_method();

```

This is a simplified version of your code above, but that would also work. (BTW, there is an error in using . instead of -> when calling func1() in your code)

In any given level of the hierarchy you can 'hide' inherited parameters:
```

class Base {
	int data_;
	void f() {
		//... use data [1] 
	}
};
class Derived : public Base {
	double data_;
	void g() {
		//... use data [2]
		//... use inherited data as: Base::data_
	}
};

```

Methods in Base will only have access to Base::data_ (int), while methods in Derived can have access to Base::data_ (int, fully qualifying) and Derived::data_ (double). The same happens with virtual methods, if the object is of type Derived, they will have access to both attributes, while if they are at Base level they will only see Base attributes.

Only methods can be virtual.

---

