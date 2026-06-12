---
title: "Singleton question - am I doing something stupid here?"
date: 2010-03-26
forum: Programming Talk
---

### Post by SwedishWings on 2010-03-26
Hi folks, 

I have some code that appear to work fine, but I'd like to know if this could cause problems. The background is:

- I have a base class that is used in more than one application which needs to be a singleton, but also need to be derived in some programs.

This is my structure:

```
#include <iostream>
#include <assert.h>

template <typename T> class SingletonClass
{
protected:
	static T* m_instance;
public:
	SingletonClass()
	{
		assert(! m_instance);
		m_instance = static_cast< T* >(this);
	}
	~SingletonClass()
	{
		assert(m_instance);
		m_instance = NULL;
	}
	static T& Instance()
	{
		assert(m_instance);
		return (*m_instance);
	}
	static T* InstancePtr()
	{
		return m_instance;
	}
};

class Base : public SingletonClass<Base>
{
public:
	Base()
	{
		bas = "Base class\n";
	}
	virtual void bar()
	{
		std::cout << bas;
	}

private:
	std::string bas;
};
template<> Base* SingletonClass<Base::Base>::m_instance = NULL;

class Derived : public Base
{
public:
	Derived()
	{
		deriv = "Derived class\n";
	}
	static Derived& Instance()
	{
		return static_cast<Derived&>(Base::Instance());
	}
	virtual void bar()
	{
		Base::bar();
		std::cout << deriv;
	}
private:
	std::string deriv;
};

int main()
{
    Derived d;
    Derived::Instance().bar();
}

```

Any comments are most welcome!

Thank,
Mike

---

### Post by dwhitney67 on 2010-03-26
Traditionally, when I have worked with Singletons, there can only be one instance of the class object.  To enforce such, the object's constructor was declared private.

All of your classes have public constructors, which makes me question how can you label your classes as 'singletons'?  After all, multiple instances of the classes can be constructed.

Consider the following code, which undoubtedly someone on this forum will find a nit mistake in it:
```

#include <iostream>


// Singleton template class
template <typename T>
class Singleton
{
public:
   static T& instance()
   {
      static T theInstance;
      return theInstance;
   }

protected:
   Singleton() {}
};


// Base template class
template <class T>
class Base : public Singleton<T>
{
public:
   virtual void foo() { std::cout << "Base::foo called." << std::endl; }

protected:
   friend class Singleton<T>;

   Base() {}
};


// Derived class
class Derived : public Base<Derived>
{
public:
   virtual void foo() { std::cout << "Derived::foo called." << std::endl; }

private:
   friend class Base<Derived>;
   friend class Singleton<Derived>;

   Derived() {}
};


int main(void)
{
   Derived::instance().foo();
   Derived::instance().Base<Derived>::foo();
}

```

---

### Post by SwedishWings on 2010-03-26
Thanks for your answer!

> **dwhitney67 said:**
> All of your classes have public constructors, which makes me question how can you label your classes as 'singletons'?  After all, multiple instances of the classes can be constructed.


If instantiating more than one instance, the assertion fail in the singleton constructor: 

```
	SingletonClass()
	{
		assert(! m_instance);
		m_instance = static_cast< T* >(this);
	}

```

I have used similar construction as you provided earlier, but switched to this construction to easier control the order of instantiation. With my construction, you actually have to declare an instance of the singleton somewhere, before calling Instance().

Apart from the differences in implementation and use, can there be any portability issues with wither construction when **deriving** classes?

Thanks,
Mike

---

### Post by Hellkeepa on 2010-03-27
HELLo!

The point of a singleton is that there is only one method of returning the object, and that it will be constructed if there is a need to do so. Forcing one to create an instance of a singleton beforehand is somewhat counter-productive, as this flexibility is removed. A flexibility most singleton usages depend upon, IIUC.

Happy codin'!

---

### Post by SwedishWings on 2010-03-27
> **Hellkeepa said:**
> HELLo!

The point of a singleton is that there is only one method of returning the object, and that it will be constructed if there is a need to do so. Forcing one to create an instance of a singleton beforehand is somewhat counter-productive, as this flexibility is removed. A flexibility most singleton usages depend upon, IIUC.

Happy codin'!

Thanks for your reply! 

Good point. Perhaps my design has flaws, but order of instantiation is actually important as this is a pretty complex 3D rendering engine with some awkward dependencies... I have not yet figured out how to design it better. 

What my question is really all about, is if the construction above can cause problem with different compilers and platforms, as this runs under Linux/M$/OSX.

Regards,
Mike

---

### Post by MadCow108 on 2010-03-27
I personally do not like singletons, especially when you need more than one and these also have dependencies.
It just introduces tons of problems (e.g. dependent destruction!) and make proper testing very hard.
I would consider other approaches like dependency injection.

But if you really want to use them have a look at the book modern C++ design by Andrei Alexandrescu. it has a chapter over advanced singleton design techniques.

---

### Post by SwedishWings on 2010-03-27
> **MadCow108 said:**
> I would consider other approaches like dependency injection.
I have no good experiences so far on dependency injection, but that might of course be a matter of usability in different scenarios.

> **MadCow108 said:**
> But if you really want to use them have a look at the book modern C++ design by Andrei Alexandrescu. it has a chapter over advanced singleton design techniques.

Thanks for the pointer, i read through and concluded that i'm not the first one who have seen the problems with dependencies between singletons. 

Sadly, not a single line mentioned inheritance from singletons. Have anyone seen this in use before? 

One thing i just don't understand, is why authors (gurus?) go such a long way to create complicated generic solutions for very simple problems. The solution in the book is quite complicated (i guess a few pages of code) rather than simply using the model i have above and create/delete the singletons in required order (or for that matter use the most basic techniques of all: create objects on the stack via C/C++ scopes).

Am I a to primitive soul in this brave new world?

Cheers,
Mike

---

### Post by MadCow108 on 2010-03-27
your class only does runtime checking, which might be problematic in complicated programs, you might overlook a case where you create two instances.
Also if someone compiles in NDEBUG mode he can happily create as many instances as he wishes.

This is exactly what the singleton pattern tries to avoid, by moving the job to the compiler.
This does introduce lots of other problems, but I consider this good. It lets you reconsider using a singleton in the first place.
The only case I really found them useful is for logging.

---

