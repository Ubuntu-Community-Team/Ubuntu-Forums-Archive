---
title: "Help with classes in c++"
date: 2009-02-05
forum: Programming Talk
---

### Post by Benzaa on 2009-02-05
Hi,

Im having and issue with some classes that Im designing to solve a partial differential equation.

The problem is the communication within the classes.

I have a big class call Equipment

```

class Equipment{
  public:
    int vector<Volumes>;
    int Data;
    void CreateVol(void);
}

class Volume{
  public:
    int DataVolume;
}

```

The member function CreateVolume generates a vector with all the volumes that are going to be used for the solution.

I want to find a way for the objects in the vector to access the data that the Equipment has. I dont want to copy this data in each of the volumes. This could mean to copy it 10000 times.

My first idea was to pass a pointer of the Equipment class (this) to Volume during the construction.

Something like this,

```

Volume::Volume(const Equipment * Parent) {
  m_pParent = Parent;
}

```

But if I do this, the compiler complains.
It says that:

> 
ISO C++ forbids declaration of "Equipment" with no type.


I have no idea what is that suppose to mean?
and I dont know what to do.

Please, if you have any idea I would really appreciate it.

---

### Post by PandaGoat on 2009-02-05
I'm not sure why you are getting that error.  Try adding a semicolon after the last brace in the declaration of the class Equipment or declare it above somewhere before the definition of it ("class Equipment;").

Another option is to make the member, data, static (static int data).  You can think of it like a global variable, although technically it is of the class scope.  It can be accessed in members (you can do this.data in member methods) and globally by doing Equipment::data--it does not need an object.  Any modification of data--accessed through any of the above ways--modifies the same value; there is only one data, and as previously stated, you can think of it as a global variable.

---

### Post by Benzaa on 2009-02-05
Thanks PandaGoat,

I solved the problem by adding:

class Equipment;

at the beggining of the header file.

It seeem that I was doing a circular reference between the two header files.

But now I have another problem. I can not access the Parent variable that stores the pointer "this".

When I try to use the variable with:
m_pParent->Data;
or
(*m_pParent).Data;

I get an error like this one
> 
invalid use of a incomplete type 'struct Equipment'
forward declaration of 'struct Equipment'


Any ideas for this one?

---

### Post by dribeas on 2009-02-05
> **Benzaa said:**
> 

Any ideas for this one?

First things first. What is a forward declaration and what is it for?

A forward declaration is a type (class/enum...) declaration that happens before the real definition of the class, as in:

```

class X; // Class forward declaration

X f(); // Function forward declaration

class X // Real class definition
{
   void method() { f(); }
};

X f() // Function definition
{
   return X();
}

```

Forward declarations are a way of telling the compiler what the symbol being declared will be. They allow the compiler to do some syntax checking.

As in the example above, after X has been forward declared, you can declare a function f() that will return an object of type X. At this point the compiler can check that the declaration of f() is correct. It is a function and returns a class (not an enum, not an int...).

Now, when it comes to the real usage of the type X, the compiler must know more things than just the plain name of the type. For example, for the definition of the f() function, the compiler must know how to construct a variable of type X so that it can be returned, and that requires the compiler to know the complete X class. On the other hand, in the definition of method() you can see that to call a function the compiler does not need to know the insides of the function, just the declaration (it takes no arguments and returns an X).

Finally, the error you are getting is the compiler complaining about you trying to use what might be a member method or attribute from class X, but the fact is that you have only forward declared the type, it cannot check if it really exists or what it represents.

I would suggest that you post your headers (or a simplified version with includes and what is defined / forward declared at each place). Anyway, the short answer is that you must include the header that defines the class that has the m_pParent attribute before the code that tries to use it.

---

### Post by Benzaa on 2009-02-05
Thanks for the help,

I found the problem.

I was including the declarations and definitions together in the same .h file.

In order to correct this crossed reference of the files, I had to make an .h file for the declarations and a .cc file for the definitions.

By doing this, the compiler doesnt get confused with the mixed reference. 

The forward reference has to be used in the header file.

---

