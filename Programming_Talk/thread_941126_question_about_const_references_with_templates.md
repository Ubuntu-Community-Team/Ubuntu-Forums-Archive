---
title: "question about const references with templates"
date: 2008-10-07
forum: Programming Talk
---

### Post by rogersce on 2008-10-07
Hi, I have a question I'm wondering if someone could help explain it to me. I have two classes, C1 and C2. C2 instantiates C1 once and then also declares a const reference to this instance. C2 has a template function that calls a non-const member function of C1 using the const reference. 

A const reference calling a non-const member function should generate a compiler error. However, I've found that when this is done inside a template function, it in fact does not generate a compile error unless you actually write code to invoke the function in C2 with the const ref to C1. I've pasted the code below to illustrate this:

class Class1
{
public:
	void mutate() {}
};

class Class2
{
public:
	Class2() : c1ref(c1){}
	template<typename T> void my_func(T &some_param){c1ref.mutate();}
	Class1 c1;
	const Class1 &c1ref;
};


int main()
{
	Class2 c2;

	double x = 3.14;

        /*program compiles just fine as is, unexpectedly.
          uncommenting line below generates a compiler error */
	//c2.my_func(x);
	return 0;
}


Any ideas on why the compiler (the GCC C++ compiler) does this? Thanks!

---

### Post by dwhitney67 on 2008-10-08
My first reaction was to inquire why are you keeping a reference of an object you have already instantiated?  But do as you please.

Aside from that, it would be helpful to see the compiler error.  If I had to guess what the error is, I bet it is complaining that you are calling mutate() which is a non-const method, whereas c1ref is a const reference to an object.

P.S.  When you compile your code, always pass the -Wall (and perhaps -pedantic) options to the compiler.  Even with that c2.my_func(x) statement commented out, your code produces a warning/error.

---

### Post by dribeas on 2008-10-08
EDIT: Accidental double post. Read below.

---

### Post by dribeas on 2008-10-08
Templates are only compiled if and when they are instantiated. You can test this with 'nm --demangle' over your generated binary. You will not find any my_func symbol (when the line is commented). Then whenever you instantiate the template for the first time (in a compilation unit) the compiler will validate the template, validate the instantiation of the template and compile it, generating the appropriate symbol (in your case: void Class2::my_func( double const & ) ), that is, if the code is correct. 

There are a couple of reasons for this 'lazy compilation' of templates. First, even if not most important, is compile time: the compiler does not need to work out the template if it will never be used. More importantly, up to the point where the template is instantiated the compiler does not even know what the generated code must look like. (In your case the error will replicate for all and any template parameter type, but in general templates fail to compile due to operations on the templated type, which cannot be checked until instantiation). And then again, even in this case, the compiler does not know if you are going to provide a template specialization later on, one that will not fail to compile.


As a side note on initialization lists: 

> **rogersce said:**
> 
class Class2
{
public:
[COLOR="Red"]	Class2() : c1ref(c1){}[/COLOR]
	template<typename T> void my_func(T &some_param){c1ref.mutate();}
[COLOR="Red"]	Class1 c1;
	const Class1 &c1ref;[/COLOR]
};


It is advisable to explicitly initialize all member attributes in the initialization lists of the compiler, and dependencies on the order or initialization of the attributes should be avoided. The reason is that it quite easy to make mistakes there:

```

class X:
public:
   X( int x );
private:
   int b_;
   int a_;
};
X::X() : a_( x ), b_( a_ ) {}

```

In the code above, even if it seems that b_ is initialized with the value of x, it is not. The compiler will reorder the initialization list so that it coincides with the order in which members are declared:

```

// compiler generates equivalent to:
X::X( int x ) : b_( a_ ), a_( x ) {}

```

Which means that b_ will get an undefined value. In this short example it is quite easy to verify the order, but at some point in time while maintaining your code things won't be as clear.

In your case, the order of initialization is correct, so you won't run into trouble, but avoiding this anti-idiom will make your code just a little safer.

---

