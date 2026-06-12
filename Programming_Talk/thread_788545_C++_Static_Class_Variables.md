---
title: "C++ Static Class Variables"
date: 2008-05-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-05-09
I am developing a class which has a subclass.  There will be multiple instances of the class, but there should only be one instance of the subclass to which all classes have a pointer to.  So I am thinking that the class has a static pointer to the subclass, which is initialized to NULL, and then once the first class is created, it makes an instance of the subclass and has the subclass pointer point to the new subclass.  Then all other instances of the class created afterwards just check the static pointer, see that it is not null and do not create any more subclasses.  In Java, this would be easy to do because all pointers are initialized to null.  However, in C++ I need to initialize the pointer to NULL only before the first instance of the main class is created.  When the other instances of the class come along, I do not want to reinitialize the subclass pointer to NULL and consequently create more subclasses.  How do I do this?

---

### Post by dwhitney67 on 2008-05-09
You want to create a Singleton object.  There are a couple of ways to do this:

One way:
[PHP]
#include <iostream>

using namespace std;


class Base
{
  public:
    Base() {}

    virtual ~Base() {}
};


class Singleton : public Base
{
  public:
    static Singleton & instance()
    {
      if (!m_single)
        m_single = new Singleton;

      return *m_single;
    }

    virtual ~Singleton() {}

    void doSomething() { cout << "Singleton is doing something!" << endl; }

  private:
    Singleton() : Base() {}

    static Singleton *m_single;
};


// Initialize static member data
Singleton * Singleton::m_single = 0;


int main()
{
  Singleton::instance().doSomething();
}

[/PHP]

Another way:
[PHP]
#include <iostream>

using namespace std;


class Base
{
  public:
    Base() {}

    virtual ~Base() {}
};


class Singleton : public Base
{
  public:
    static Singleton & instance()
    {
      static Singleton single;

      return single;
    }

    virtual ~Singleton() {}

    void doSomething() { cout << "Singleton is doing something!" << endl; }

  private:
    Singleton() : Base() {}
};


int main()
{
  Singleton::instance().doSomething();
}
[/PHP]

---

### Post by dempl_dempl on 2008-05-09
> **SNYP40A1 said:**
> I am developing a class which has a subclass.  There will be multiple instances of the class, but there should only be one instance of the subclass to which all classes have a pointer to.  So I am thinking that the class has a static pointer to the subclass, which is initialized to NULL, and then once the first class is created, it makes an instance of the subclass and has the subclass pointer point to the new subclass.  Then all other instances of the class created afterwards just check the static pointer, see that it is not null and do not create any more subclasses.  In Java, this would be easy to do because all pointers are initialized to null.  However, in C++ I need to initialize the pointer to NULL only before the first instance of the main class is created.  When the other instances of the class come along, I do not want to reinitialize the subclass pointer to NULL and consequently create more subclasses.  How do I do this?

Besides the **singleton**, you should also look for   **auto_ptr**   class.

---

### Post by SNYP40A1 on 2008-05-10
Thanks for the advice.  I went with option #2 above and so far, it seems to be working.

---

### Post by SNYP40A1 on 2008-05-13
I think I ran into a problem.  If I have several instances of a given class (but all of the same class) which each share only one instance of the subclass using the singleton class as described above, things seem to work.  However, if I make different classes which inherit from the one class (which gets a singleton subclass), it seems that things no longer work.  I print out the memory address of the subclass as an integer and I see different addresses.

So if I have one class, call it class B, which has a singleton subclass call it class A, how can I inherit off this class to create classes C, D, and E and still have only one instance of subclass A among all instances of classes C, D, and E.  Is this possible in C++?

---

### Post by dwhitney67 on 2008-05-13
It would be helpful to have a UML diagram.

Anyhow, is this what you are referring to??
[PHP]
class Base
{
  public:   // or protected, up to your design?
    Base()
    virtual ~Base();
};

class Singleton : public Base()
{
  ...
};

class NonSingleton_One : public Base()
{
  ...
};

class NonSingleton_Two : public Base()
{
  ...
};[/PHP]

If this is what you are referring to, then yes (obviously) it can be done.  The Singleton class cannot be subclassed because its constructor should be declared private.  If you followed the instructions I gave in my first post, then it is impossible to have two instances of Singleton.

---

### Post by SNYP40A1 on 2008-05-13
That's not quite what I had in mind.  Say we have a class A which is a singleton object.  I can have a bunch of instances of different classes all reference one instance of the singleton object A.  That's what I was able to do last week.  I ran into a problem where I have class B get an instance of the singleton object, then I have classes X, Y, and Z inherit from B.  It seems that all instances of X share the same instance of the singleton object, A.  However, instances of classes X, Y, and Z all have different instances of singleton object A -- I see different pointer addresses when I print out A's address.

---

### Post by dempl_dempl on 2008-05-13
> 

So if I have one class, call it class B, which has a singleton subclass call it class A, how can I inherit off this class to create classes C, D, and E and still have only one instance of subclass A among all instances of classes C, D, and E.  Is this possible in C++?



No. It's impossible in general. Actually, what you suggest , is  insane :) , but idea is cool :D .  

In this particular case, You don't do sub-classing (IS-a) , you'll do  a HAS-A relationship. 

e.g. All of those B,C,D, E  will have a member which holds a reference  to Singleton A.

Cheers!

---

### Post by SNYP40A1 on 2008-05-13
Humm...I was afraid of that.  Actually, all I really need to do is access one variable inside that class A.  I guess I could move the variable up inside B and declare it as static.  Then I could access / modify it from all classes which inherit from B.

---

### Post by JupiterV2 on 2008-05-13
I think what the OP had in mind, is in effect, the following:

[php]

class Data
{
    int data1; /* or whatever data you want to store */
    
  public:
    Data() {}
    ~Data() {}
};

class Base
{
        /* a class to manipulate data */
	Data* d;
	
  public:
  	Base() {}
  	Base(Data* dat) { d = dat; }
  	virtual ~Base() {}
	
	void store_data() {}
	void manipulate_data() {}
};

class Someclass1 : public Base
{
  public:
    Someclass1(Data* dat) : Base::Base(dat) {}    
    ~Someclass1() {}
  
  /* ... more declarations */
};


class Someclass2 : public Base
{ 
  public:
    Someclass2(Data* dat) : Base::Base(dat) {}
    ~Someclass2() {}
};

int main()
{
    Data* pData = new Data;
    
    Someclass1 s1(pData);
    Someclass2 s2(pData);
    
    delete pData;
    
    return 0;
}[/php]

There may be a better way but I think this illustrates what the OP maybe had in mind...

---

### Post by SNYP40A1 on 2008-05-14
> **JupiterV2 said:**
> I think what the OP had in mind, is in effect, the following:

[php]

class Data
{
    int data1; /* or whatever data you want to store */
    
  public:
    Data() {}
    ~Data() {}
};

class Base
{
        /* a class to manipulate data */
	Data* d;
	
  public:
  	Base() {}
  	Base(Data* dat) { d = dat; }
  	virtual ~Base() {}
	
	void store_data() {}
	void manipulate_data() {}
};

class Someclass1 : public Base
{
  public:
    Someclass1(Data* dat) : Base::Base(dat) {}    
    ~Someclass1() {}
  
  /* ... more declarations */
};


class Someclass2 : public Base
{ 
  public:
    Someclass2(Data* dat) : Base::Base(dat) {}
    ~Someclass2() {}
};

int main()
{
    Data* pData = new Data;
    
    Someclass1 s1(pData);
    Someclass2 s2(pData);
    
    delete pData;
    
    return 0;
}[/php]

There may be a better way but I think this illustrates what the OP maybe had in mind...

Yes, that's it.  Sorry for not making it more clear.  The base class creates one instance of the Data class.  Then 4 other classes (in my case) inherit from the Base class, these are represented above by the classes Someclass1 and Someclass2.  Actually, what I would really like to do is have only one instance of the base class (which creates on instance of the Data class -- no need for singleton object) and then have Someclass1 and Someclass2 inherit from Base class such that there is really only one instance of Base class constructed.  But as a previous poster pointed out, this is insane.  However, it would be good enough if the data1 field of the Data class could be accessed from all the Someclass1, Someclass2, Someclass3, etc.  So if I move it into Base class and then make it static, that should work, I think / hope.

---

### Post by dwhitney67 on 2008-05-14
Yes, that would work.

[PHP]class Data   // or struct if you wish
{
 ...
};

class Base
{
  protected:
    Base(...) {...}
  private:
    static Data m_data;
};

class A : public Base
{
  ...
};

class B : public Base
{
  ...
};

// initialize/construct static member data (this is generally done in
// .cpp file)
Data Base::m_data;[/PHP]

---

### Post by SNYP40A1 on 2008-05-14
> **dwhitney67 said:**
> Yes, that would work.

[PHP]class Data   // or struct if you wish
{
 ...
};

class Base
{
  protected:
    Base(...) {...}
  private:
    static Data m_data;
};

class A : public Base
{
  ...
};

class B : public Base
{
  ...
};

// initialize/construct static member data (this is generally done in
// .cpp file)
Data Base::m_data;[/PHP]

I thought about this some more last night.  I am not sure if this would work, actually.  Would that one variable above, Base::m_data really be static across class A and class B?  Or would it just be static across all instances of class A, and there would be a second instance which is static across all instances of class B?  It seems like I might run into the same problem that I saw before.

---

### Post by dwhitney67 on 2008-05-14
It will be static across all instances, whether A, B, C or D.  

Why don't you write yourself a mini-program to verify!

---

### Post by SNYP40A1 on 2008-05-14
So how come the variable was not static across all classes when it was in the Data class instead of the Base class?

---

### Post by dwhitney67 on 2008-05-14
Because maybe you programmed something incorrectly??

I should not have to be burdened with this, but here's some trivial code...

(Btw, I do not prefer to declare static data within Data structure itself; it would be better to declare Data as a member of Base and define it as static at that point). 

Data.h:
[PHP]#ifndef DATA_H
#define DATA_H

#include <iostream>

struct Data
{
  static int value;

  friend std::ostream& operator<<( std::ostream& os, const Data &data )
  {
    os << data.value;
    return os;
  }
};

// initialize static data member
int Data::value = 0;

#endif[/PHP]

Base.h:
[PHP]#ifndef BASE_H
#define BASE_H

#include "Data.h"

class Base
{
  public:
    virtual ~Base() {}

    void setValue( int value )
    {
      m_data.value = value;
    }

    const Data & getData() const
    {
      return m_data;
    }

  protected:
    Base() {}

  private:
    Data m_data;
};

#endif[/PHP]

A.h:
[PHP]#ifndef A_H
#define A_H

#include "Base.h"

class A : public Base
{
  public:
    A() : Base() {}
    virtual ~A() {}
};

#endif[/PHP]

B.h:
[PHP]#ifndef B_H
#define B_H

#include "Base.h"

class B : public Base
{
  public:
    B() : Base() {}
    virtual ~B() {}
};

#endif[/PHP]

Main.cpp:
[PHP]#include "A.h"
#include "B.h"
#include <iostream>

using std::cout;
using std::endl;

int main()
{
  A a;
  B b;

  a.setValue( 5 );
  b.setValue( 50 );

  cout << a.getData() << endl;
  cout << b.getData() << endl;

  return 0;
}[/PHP]

---

### Post by SNYP40A1 on 2008-05-14
dwhitney67, I think you are correct.  I believe that I did something wrong because I ran your code, and slightly modified it to match my case and it still gives 50 50 as the output.  My case was slightly different because the data integer is not static and the Data object is a singleton class rather than a struct (which is why the data integer does not need to be static).  The modified code is below.  I appreciate your help.

Data.h

[PHP]
#ifndef DATA_H
#define DATA_H

#include <iostream>

class Data
{
  public:
	static Data& getDataInstance()
	  {
		static Data singleton;
		return singleton;
	  }
    
    virtual ~Data() {}

    void setValue( int value )
    {
      m_value = value;
    }

    int getData()
    {
      return m_value;
    }

  private:
    Data() { m_value = 0; };
    int m_value;
};

// initialize static data member
//int Data::m_value = 0;

#endif  
[/PHP]

Base.h
[PHP]
#ifndef BASE_H
#define BASE_H

#include "Data.h"

class Base
{
  public:
    virtual ~Base() {}

    void setValue( int value )
    {
      m_data->setValue(value);
    }

    int getData()
    {
      return m_data->getData();
    }

  protected:
    Base() { m_data = &Data::getDataInstance(); }

  private:
    Data *m_data;
};

#endif  
[/PHP]

A.h:
[PHP]
#ifndef A_H
#define A_H

#include "Base.h"

class A : public Base
{
  public:
    A() : Base() {}
    virtual ~A() {}
};

#endif 
[/PHP]

B.h:
[PHP]
#ifndef B_H
#define B_H

#include "Base.h"

class B : public Base
{
  public:
    B() : Base() {}
    virtual ~B() {}
};

#endif  
[/PHP]

main.cpp:
[PHP]
#include "A.h"
#include "B.h"
#include <iostream>

using std::cout;
using std::endl;

int main()
{
  A a;
  B b;

  a.setValue( 5 );
  b.setValue( 50 );

  cout << a.getData() << endl;
  cout << b.getData() << endl;

  return 0;
}  
[/PHP]

---

### Post by dwhitney67 on 2008-05-14
One little comment... it might be easier if you changed these lines:

[PHP]
  ...
  protected:
    Base() { m_data = &Data::getDataInstance(); }

  private:
    Data *m_data;
  ...
[/PHP]

to
[PHP]
  ...
  protected:
    Base() : m_data( Data::instance() ) {}

  private:
    Data & m_data;
  ...
[/PHP]

This way when you use m_data, you can use it without have to dereference it as if it were a pointer.  Something like:

[PHP]m_data.getData();[/PHP]

The other, possibly more notable thing, is that normally one would not encapsulate a singleton object within a class such as you have done.  There is nothing to prevent other classes from skipping around your Base class when accessing the singleton.

Anyhow, I'm glad you sorted out the problem you were having.

---

### Post by SNYP40A1 on 2008-05-15
> **dwhitney67 said:**
> One little comment... it might be easier if you changed these lines:

[PHP]
  ...
  protected:
    Base() { m_data = &Data::getDataInstance(); }

  private:
    Data *m_data;
  ...
[/PHP]

to
[PHP]
  ...
  protected:
    Base() : m_data( Data::instance() ) {}

  private:
    Data & m_data;
  ...
[/PHP]

This way when you use m_data, you can use it without have to dereference it as if it were a pointer.  Something like:

[PHP]m_data.getData();[/PHP]

The other, possibly more notable thing, is that normally one would not encapsulate a singleton object within a class such as you have done.  There is nothing to prevent other classes from skipping around your Base class when accessing the singleton.

Anyhow, I'm glad you sorted out the problem you were having.

Yes, I like the second version that you posted better, but can you explain what this line is doing:

Base() : m_data( Data::instance() ) {}

I do not understand what the syntax means.  Looks like Base is inheriting from an instance rather than a class.  Also, m_data is an instance of Data?  Is that what it means?

---

### Post by dwhitney67 on 2008-05-15
Examine this code:

[PHP]public:
  // constructor
  SubClass()
     : BaseClass(),
       m_value(0)
  {
  }
  ...
private:
  int m_value;[/PHP]

Basically the member data m_value is being initialized to a zero.  This area is typically where member data is initialized, but doesn't have to be (can be done in constructor body).  The exception to this rule is when dealing with member data that has been defined as a reference.

In regards to the other code I provided earlier, you are initializing a member object that is defined as a reference (as opposed to a pointer).  It must be done as indicated, and not in the body of the constructor (otherwise, g++ generates error).

---

