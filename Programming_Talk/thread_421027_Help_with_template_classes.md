---
title: "Help with template classes"
date: 2007-04-24
forum: Programming Talk
---

### Post by aquavitae on 2007-04-24
Hi

Is there a way to refer to a template class without specifying the template parameter?  I want to do something like this:
```

template <typename T> class MyClass;
vector<MyClass*> list;

```
I want to do this so that 'list' can contain an assortment of MyClass<int>, MyClass<bool> and MyClass<string>
 but obviously I can't compile it because MyClass isn't a complete type.

---

### Post by hod139 on 2007-04-24
You wouldn't use generics to accomplish what you want.  You want to use polymorphism  and inheritance.  For an example, see: [http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6](http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.6)

If you still have more questions after reading that, post back for clarifications.

---

### Post by harun on 2007-04-24
You can create a small class similar to this:

```

class CItem  {
public:
	CItem();
	virtual ~CItem();

public:
	string m_sSomeString;
	int    m_iSomeInt;
	bool   m_bSomeBool;
};

```

Then have a vector of them:
```

    vector<CItem> l_Items;

```

Not sure if this is what you are shooting for though.

---

### Post by amo-ej1 on 2007-04-24
Whoow that's one ugly void * ;-)

---

### Post by aquavitae on 2007-05-02
Thanks for the suggestion, hod139, but I don't quite see how that will help.  Could you explain please?

Harun, I'd thought of something like that, but I don't really like the memory implications.  A the moment I'm using Qt's QVariant, but I don't know what that's like with memory, and the type conversions are messy.  In any case, this isn't a once off problem, I keep on wanting to do something like that, and its not always possible to restrict it to int, boot and string.

---

### Post by cwaldbieser on 2007-05-02
> **aquavitae said:**
> Thanks for the suggestion, hod139, but I don't quite see how that will help.  Could you explain please?

Harun, I'd thought of something like that, but I don't really like the memory implications.  A the moment I'm using Qt's QVariant, but I don't know what that's like with memory, and the type conversions are messy.  In any case, this isn't a once off problem, I keep on wanting to do something like that, and its not always possible to restrict it to int, boot and string.

In C++, templates are basically code generators.  They create complete types at compile time.  When you actually compile your code, your MyClass<T> will be resolved to a MyClass<int> or MyClass<bool> or whatever.

You want to create a list that can hold different types at **runtime**.  The example that harun gave you shows that you want the 3 different data types, but it has the problem you pointed out that it requires memory for all three data types.  If you want to add more types, your class grows and grows...

One approach to this problem is a discriminated union, sometimes called a variant.  It looks something like:
```

union SomeData
{
int type_field; //1=int, 2=string. 3=bool
int int_;
string double_;
bool bool_;
};

```
This uses memory roughly equal to the largest data type, but it still has a number of problems.  You still need to monkey around with the union to add types, and the compiler can't help you with type mismatches, since you are making runtime decisions.  So this is generally not the best idea.

In "Effective C++ Second Edition" (by Scott Meyers), understanding the difference between inheritence and templates is covered beatifully in item #41.  Meyers goes on to show how you can use templates and private inheritance to create the type of class you want and have some measure of type safety in item #42.

Basically, with the inheritence route, you want to do something like this:

Create an virtual base class that provides the interface to your other types.  Let's call it ABC.  Your concrete types could inherit from it.

Now your list can be:
```

std::vector<ABC*> list;

```

Pointers to the base class can be stored in the list.  When the objects are accessed through the base class pointer, methods on the concrete class will be called.

Remember, that MyClass<int> and MyClass<bool> *are* a concrete types!

---

### Post by aquavitae on 2007-05-04
Hmm, It seems like inheritance is the best way then.  But how would I deal with member functions that rely on the template definition.  e.g. T MyClass::function() ?  I can't overload on return type, so if I define it in the base class, I won't be able to use it in the inherited template classes, will I?

---

### Post by cwaldbieser on 2007-05-04
> **aquavitae said:**
> Hmm, It seems like inheritance is the best way then.  But how would I deal with member functions that rely on the template definition.  e.g. T MyClass::function() ?  I can't overload on return type, so if I define it in the base class, I won't be able to use it in the inherited template classes, will I?
That is true; you cannot overload on the return type.  Without changing your design, there are still options, but the ones I can think of have shortcomings:

I think you are forced to handle each different type of object differently at that point, so you are stuck doing downcasts:

(not tested/compiled!)
```

MyClass* p= /*item from your list*/;
if (DerivedClass<int>* pdci = dynamic_cast<DerivedClass<int>* >(p) )
{
    //do int specific stuff
}
else if (DerivedClass<bool>* pdci = dynamic_cast<DerivedClass<bool>* >(p) )
{
    //do bool specific stuff
}
else
{
    //Error!  Not one of your anticipated types!
}

```

This is not really an ideal situation, though.  It means if you need to add a new type, you have to monkey around with this code.

---

### Post by hod139 on 2007-05-04
> **aquavitae said:**
> Hmm, It seems like inheritance is the best way then.  But how would I deal with member functions that rely on the template definition.  e.g. T MyClass::function() ?  I can't overload on return type, so if I define it in the base class, I won't be able to use it in the inherited template classes, will I?
Why do you need generics?  You want a heterogeneous list right?   In the link I gave in my first post, it covered how to do this.  I will try and explain their example.  Say you want a list of Vehicles, but you don't know what type of vehicle each item is.  You will have some base class
```

class Vehicle {
 public:
   *// performs the "foo-bar" operation*
   virtual void fooBar() = 0;
 };

```

Now somewhere in your code you will have a list of vehicles ```
  typedef std::vector<Vehicle*>  VehicleList;
```

and on this list you want to do some operation.
```

void myCode(VehicleList& v)
 {
   for (VehicleList::iterator p = v.begin(); p != v.end(); ++p) {
     Vehicle& v = **p;  *// just for shorthand*
 
     *// generic code that works for any vehicle...*
     *...*
 
     *// perform the "foo-bar" operation.*
     v.fooBar();
 
     *// generic code that works for any vehicle...*
     *...*
   }
 }

```

For each derived class of vehicle, you can override that function: 
```

  class Car : public Vehicle {
 public:
   virtual void fooBar();
 };
 
 void Car::fooBar()
 {
   *// car-specific code that does "foo-bar" on 'this'*
   *...*  *&#8592; this is the code that was in {...} of if (v is a Car)*
 }
 
 class Truck : public Vehicle {
 public:
   virtual void fooBar();
 };
 
 void Truck::fooBar()
 {
   *// truck-specific code that does "foo-bar" on 'this'*
   *...*  *&#8592; this is the code that was in {...} of if (v is a Truck)*
 }

```
That's it.  No need for generics to make a heterogenous list, or am I missing something?

---

### Post by aquavitae on 2007-05-07
Ah, it looks so obvious - how did I miss it!  And that would also solve the problem of return types - just return a Vehicle, and if its done right there's no need to cast it.  Thanks!

---

