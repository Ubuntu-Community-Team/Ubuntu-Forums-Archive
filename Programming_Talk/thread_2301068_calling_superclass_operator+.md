---
title: "calling superclass operator+"
date: 2015-10-30
forum: Programming Talk
---

### Post by chuchi on 2015-10-30
Hi there!
 

 I know this is maybe a very stupid question, but how can I call the superclass operator+ from the subclass operator+?
 

 This is an example:
 

 ```

 #include <iostream>
 using namespace std;
 

 class Base
 {
 public:
 

   Base operator+(const Base& other)
   {
     Base ret;
 

     return ret;

   }
 };
 

 class Derived: public Base
 {
 public:
 

   Derived operator+(const Derived& other)
   {
     //how can I call Base operator+
 

   }
 };
 

 int main()
 {
   Derived b, b2, b3;
    
   b = b2 + b3;
    
   return 0;
 }
 
```

---

### Post by spjackson on 2015-10-30
Something like this:

```

   Derived operator+(const Derived& other)
   {
        Base that = other;  // object slicing
        Base::operator+(that);
        return *this;
   }

```

---

### Post by chuchi on 2015-10-30
Hi spjackson!

Thank you very much for your reply!

But why are you preventing object slicing in this case?

---

### Post by spjackson on 2015-10-30
> **chuchi said:**
> 
But why are you preventing object slicing in this case?
How else do you propose passing an object of type Base to the base class's + operator?

---

### Post by chuchi on 2015-10-30
I am sorry as I am a newbie in C++. Maybe I did not understand the object slicing.

What would be the problem in passing an object of the Derived class 'other' to the base class's + operator??
```

Base::operator+(other);


```

---

### Post by spjackson on 2015-10-30
Try compiling that.

---

### Post by chuchi on 2015-10-30
Hi spjackson.

The compiler did not throw any error. It is OK and this is the code:

```

#include <iostream>
using namespace std;

class Base
{
public:

  Base operator+(const Base& other)
  {
    cout << "Calling Base operator+"<< endl;
    Base ret;
    return ret;
  }
};

class Derived: public Base
{
public:

  Derived operator+(const Derived& other)
  {
    //how can I call Base operator+
    cout << "Calling Derived operator+"<< endl;
    Base::operator+(other);
    return *this;
  }
};

int main()
{
  Derived b, b2, b3;
  
  b = b2 + b3;
  
  return 0;
}



```

And the output 

```


Calling Derived operator+
Calling Base operator+




```

---

### Post by chuchi on 2015-11-01
Hello,
 

 This is an improved example of what I want to do
 

 ```

 

 #include <iostream>
 using namespace std;
 

 template <class Type>
 class Base
 {
 public:
   int var;
   Base operator+(const Base& other)
   {
     Base ret;
     ret.var = var + other.var;
     return ret;
   }
 };
 

 template <class Type>
 class Derived : public Base<Type>
 {
 public:
 

   Derived operator+(const Derived& other)
   {
     Derived<Type> ret;
     ret = Base<Type>::operator+(other);//error: no match for &#8216;operator=&#8217; (operand types are &#8216;Derived<int>&#8217; and &#8216;Base<int>&#8217;)
     return ret;
   }
 };
 

 int main()
 {
   Derived<int> b, b2, b3;
   b2.var = 2;
   b3.var = 3;
   b = b2 + b3;
   return 0;
 }
 

 
```
 

 How can I call the superclass operator+? The problem are the operand types, as they are superclass (ret) objects....

---

### Post by dwhitney67 on 2015-11-01
Chuchi,

I'm not sure where you learned about implementing overloaded operator methods, but either you referenced a poorly written tutorial or you missed part of the concept.

The overloaded operator methods should manipulate the object being acted on; it should not be creating a temporary object, and then returning a copy of such.  If you want to do such things, then you should define a static method, or some other method (i.e. combination of operator+ and operator=).

Here's some example code, that uses your template (no pun) for the design of the classes.  Note the differences between what I have implemented and what you have.

If you have any questions, please let me know.

```

#include <iostream>


template <typename T>
class Base
{
public:
	Base(const T& value)
		: value(value)
	{
	}

	T getValue() const
	{
		return value;
	}

	Base& operator+(const Base& other)
	{
		value += other.value;

		return *this;
	}

private:
	Base(const Base<T>&);
	Base& operator=(const Base<T>&);

	T value;
};


template <typename T>
class Derived : public Base<T>
{
public:
	explicit Derived(const T& value)
		: Base<T>(value)
	{
	}

	Derived& operator+(const Derived& other)
	{
		Base<T>::operator+(other);

		return *this;
	}

private:
	Derived(const Derived<T>&);
	Derived& operator=(const Derived<T>&);
};


int main()
{
	Derived<int> b1(2);
	Derived<int> b2(3);

	b1 + b2;

	std::cout << b1.getValue() << std::endl;
}

```

---

### Post by chuchi on 2015-11-01
Hello dwhitney67,

Thank you very much! Your solution is what I was looking for!

I am having some C++ classes where they taught me operator+ should operate to build and return a new object, rather than operate the object being acted on. 

Surfing the net I also found this two links:

[http://www.tutorialspoint.com/cplusplus/binary_operators_overloading.htm](http://www.tutorialspoint.com/cplusplus/binary_operators_overloading.htm)

[http://www.codingunit.com/cplusplus-tutorial-unary-and-binary-operator-overloading-and-static-members](http://www.codingunit.com/cplusplus-tutorial-unary-and-binary-operator-overloading-and-static-members)

Which support the idea of building and returning a new object.

I am pretty new in C++ and do not know which approach is the right one.... maybe it depends on the project? Could you please give me some advice?

---

### Post by spjackson on 2015-11-02
As a user of a class, if I write
```

   c = a + b;

```
where a,b,c are all objects of this class, I would not be expecting a or b to be changed.

This doesn't happen for POD types, nor for std::string. Indeed, I'd expect operator+ to be declared const, e.g.
```

    Derived operator+(const Derived& other) const
    {
        // TODO
    }

```

---

### Post by dwhitney67 on 2015-11-02
Undoubtedly as you already know, there are multiple ways to solve a problem.  However, it is common practice to define overloaded operator method as a manipulator of the object.  If you want to define an overloaded operator method (or function) which does _not _manipulate the object, then it is best practice to declare a free-function.

Here's a modified example program showing such (and the commented out code of what you were originally inquiring about):
```

#include <iostream>


template <typename T>
class Base
{
public:
	// constructor
	Base(const T& value)
		: value(value)
	{
	}

	T getValue() const
	{
		return value;
	}

#if 0
	const Base operator+(const Base& other) const
	{
		return Base<T>(this->value + other.value);
	}
#endif

private:
	T value;
};


template <typename T>
class Derived : public Base<T>
{
public:
	// constructor
	Derived(const T& value)
		: Base<T>(value)
	{
	}

	// copy-constructor
	Derived(const Base<T>& base)
		: Base<T>(base)
	{
	}

#if 0
	const Derived operator+(const Derived& other) const
	{
		return Base<T>::operator+(other);
	}
#endif
};


#if 1
template<typename T>
Base<T> operator+(const Base<T>& lhs, const Base<T>& rhs)
{
	return Base<T>(lhs.getValue() + rhs.getValue());
}

template<typename T>
Derived<T> operator+(const Derived<T>& lhs, const Derived<T>& rhs)
{
	return operator+(reinterpret_cast<const Base<T>&>(lhs), reinterpret_cast<const Base<T>&>(rhs));
}
#endif

int main()
{
	Derived<int> b1(2);
	Derived<int> b2(7);
	Derived<int> b3 = b1 + b2;

	b2 = b1 + b2;

	std::cout << b2.getValue() << std::endl;
	std::cout << b3.getValue() << std::endl;
}

```

---

### Post by chuchi on 2015-11-03
Hi spjackson!

Thanks again for your reply! I did not know about POD types, I am learning a lot here.

But I am dealing with a much more complex class and to simplify I just put this exmple. 

 
dwhitney67 
Your solution was very good to me also, thanks a lot! But I would have to learn more about reinterpret_cast...

Anyway I kept surfing and this subject seems to be very popular and are different approaches. I found one of them interesting and would like to know your opinion. 

As spjackson said, I would not expect nor b or c to me modified in this expression:

a = b + c

So the idea is to create a new method (add) that acts on the object being called and then create a copy from this, execute the new method on the copy and return the copy.

```


#include <iostream>
using namespace std;

template <class Type>
class Base
{
public:
  int var;
  
  Base(int v):var(v){}
  
  Base operator+(const Base& other)
  {
    Base<Type> ret = *this;
    ret.add(other);
    return ret;
  }
  
  protected:
    void add(const Base& other)
    {
      var += other.var; //all the logic to add objects would be here
    }
};

template <class Type>
class Derived : public Base<Type>
{
public:
  
  Derived(int v = 0) : Base<Type>(v)
  {}
  
  Derived operator+(const Derived& other)
  {
    Derived<Type> ret = *this;
    ret.add(other);
    return ret;
  }
  
};

int main()
{
  Derived<int> b1(1), b2(2), b3; 
  b3 = b1 + b2;
  cout << b3.var << endl;
  return 0;
}


```

What do you think about this approach?


Thank you all for your help!

---

