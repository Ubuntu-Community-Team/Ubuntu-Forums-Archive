---
title: "[c++] questions about polymorphism, dynamic binding, virtual functions"
date: 2010-11-24
forum: Programming Talk
---

### Post by josephellengar on 2010-11-24
Hello. I pretty much have the gist of what I am trying to do in the title. For the assignment that I am working on, I have to write a program that manages various types of numbers. I have a superclass, multinumber, with various functions:

```

	virtual Multinumber operator+(Multinumber);
	virtual Multinumber& operator=(Multinumber);
	virtual bool operator==(Multinumber);
	virtual string object2string();
	virtual void makeobject(double, double)=0;

```
Then I have three subclasses (Pairs, Complex, and Rational), and in each of these subclasses I have to override each of these functions. This is turning out to be quite problematic though because the parameters for the virtual functions in Multinumber are of type Multinumber, and Multinumber is, obviously, an abstract class. I was hoping that since the other three classes are inherited from Multinumber the compiler wouldn't mind if I, for example, defined a function in Complex as

```

Complex operator+(Complex);

```

But the compiler is not recognizing this as the same function definition.
The class, Multinumber, looks like this:
```


#include "Multinumber.h"
using namespace std;

Multinumber::operator+(Multinumber num)
{
}

Multinumber::operator=(Multinumber num)
{
}

Multinumber::operator==(Multinumber num)
{
}

Multinumber::object2string()
{
}

Multinumber::makeobject(double x, double y)
{
}

```


 In essence, I am trying to make all of the above functions dynamically binded but using different parameters so that I can use them polymorphically in a set data structure (for example, I cannot add a "Complex" to a "Rational.") Am I doing this incorrectly? I think I understand the theory behind it, but I am a little confused. Thank you for any help you can give me. If needed, I have included the relevant code as an attachment.

---

### Post by dwhitney67 on 2010-11-24
You have got to get into the habit of passing complex (no pun wrt your current work) parameters by reference, and to declare them as const if you do not plan to modify them.  Ditto for any methods you declare; if they do not modify class data, then declare them as const.

Oh, btw, your example functions also need to return the instance of object being operated on.

For example:
```

#include "Multinumber.h"

// NOT NEEDED (well, at least not yet) using namespace std;

Multinumber&
Multinumber::operator+(const Multinumber& num)
{
   ...

   return *this;
}

Multinumber&
Multinumber::operator=(const Multinumber& num)
{
   ...

   return *this;
}

bool
Multinumber::operator==(const Multinumber& num)
{

   return ...;
}

std::string
Multinumber::object2string() const
{
   std::string theStr;

   ...

   return theStr;
}

// No need to implement this; you declared it as an abstract
// method (ie pure virtual).
// void makeObject(const double, const double);

```
Wrt to the last method (makeObject), are you sure you want it as pure-virtual?  If so, it will preclude you from instantiating a Multinumber object.  Thus some of your other methods will not be able to be implemented.

---

### Post by josephellengar on 2010-11-24
> **dwhitney67 said:**
> You have got to get into the habit of passing complex (no pun wrt your current work) parameters by reference, and to declare them as const if you do not plan to modify them.  Ditto for any methods you declare; if they do not modify class data, then declare them as const.

Oh, btw, your example functions also need to return the instance of object being operated on.

For example:
```

#include "Multinumber.h"

// NOT NEEDED (well, at least not yet) using namespace std;

Multinumber&
Multinumber::operator+(const Multinumber& num)
{
   ...

   return *this;
}

Multinumber&
Multinumber::operator=(const Multinumber& num)
{
   ...

   return *this;
}

bool
Multinumber::operator==(const Multinumber& num)
{

   return ...;
}

std::string
Multinumber::object2string() const
{
   std::string theStr;

   ...

   return theStr;
}

// No need to implement this; you declared it as an abstract
// method (ie pure virtual).
// void makeObject(const double, const double);

```
Wrt to the last method (makeObject), are you sure you want it as pure-virtual?  If so, it will preclude you from instantiating a Multinumber object.  Thus some of your other methods will not be able to be implemented.

Yes, I definitely want the last element to be pure virtual. The goal is to just have the Multinumber class be something that can be referenced in the set that I have, so that I can manage different types of numbers polymorphically in that set. I do not ever intend to instantiate a Multinumber object. That was why I left my functions all with empty brackets.

But was my only problem that I wasn't passing the parameters by reference? If so, when I declare, for example,

```

Complex::operator==(const Complex& num]

```

It will recognize it as an override of the above function? I do have Complex inheriting Multinumber.

Also, just out of curiosity, why does it matter if I have any return statement at all in a function within a virtual class? Shouldn't the compiler know that these functions will never be used?

---

### Post by dwhitney67 on 2010-11-25
If you want Multinumber to be an abstract class AND you have no intention of implementing any code for this class, then I recommend that you make all of it's functions pure-virtual.

These two functions are NOT the same:
```

class Multinumber
{
public:
   ...

   Multinumber(const Multinumber& other);

   ...
};

class Complex : public Multinumber
{
public:
   ...

   Complex(const Complex& other);

   ...
};

```
I don't know why you would think they are.

> 
Also, just out of curiosity, why does it matter if I have any return statement at all in a function within a virtual class? Shouldn't the compiler know that these functions will never be used?

Are you kidding?  You require a return value from a function that is declared to return one.  If you do not want to return a value, then declare the function as returning void.

The compiler checks the syntax of your code and can check the legality of some of it.  But it cannot deduce your intent; in other words, it cannot provide feedback on your design.

Finally, there is a distinct difference between a virtual function and a pure-virtual function.  The former requires that you implement the function; the latter does not.

A class is considered abstract if it contains at least one pure-virtual function.  An abstract class cannot be instantiated.

If you require further assistance, please present your design.  If might offer more insight in what you are attempting to accomplish.

---

### Post by josephellengar on 2010-11-25
Well, I believe I understand what you were talking about above, but I've run into another problem.

With functions such as this one:

```

const Multinumber& Complex::operator+(const Multinumber & rhs) const
{
    return Complex(real + rhs.real, imag + rhs.imag);
}

```

The compiler is telling me that Multinumber has no member named real or imag, which it doesn't. This function will only be called when the Multinumber &rhs is a Complex, which does have these members. But I can't figure out a way to tweak my code so that the compiler is able to see this. Thank you very much for your help and as you requested I am attaching a class diagram and my code so far to this message.

---

### Post by dwhitney67 on 2010-11-26
I could not find within your design where you defined this method:
```

const Multinumber& Complex::operator+(const Multinumber & rhs) const

```
Is this something that you decided to spontaneously add to your code?

As for the compiler error and the statement you made, if you know that you will always pass a Complex object to that function, then IMO you should declare that; for example:
```

const Complex& Complex::operator+(const Complex& rhs) const

```
Alternatively, you can play Russian roulette, and do something like:
```

const Multinumber& Complex::operator+(const Multinumber & rhs) const
{
   try {
      const Complex& complex = dynamic_cast<const Complex&>(rhs);
      ...
   }
   catch (std::exception& e) {
      std::cerr << e.what() << std::endl;
   }

   return *this;
}

```

---

