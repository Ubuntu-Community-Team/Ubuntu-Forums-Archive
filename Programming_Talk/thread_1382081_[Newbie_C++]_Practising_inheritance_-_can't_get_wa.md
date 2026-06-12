---
title: "[Newbie C++] Practising inheritance - can't get wanted outcome"
date: 2010-01-15
forum: Programming Talk
---

### Post by dodle on 2010-01-15
In my code I am trying to show that a cat purrs and a dog barks.  But as it is right now, the output shows that they do not.  Can you help me with my error?  

[php]#include <iostream>
#include <string>
using namespace std;

class Mammal  //create base class
{
};

class Cat : public Mammal  //derived class of Mammal
{
public:
  bool purr;  //show that a cat purrs
};

class Dog : public Mammal  //derived class of Mammal
{
public:
  bool bark;  //show that a dog barks
};

int main()
{
  Cat Tiger;
  Dog Fido;
  if (Tiger.purr)  //if purr is a member of Cat, return true
  {
    cout << "Tiger purrs" << endl;
  }
  else  //if purr is returned as false
  {
    cout << "Tiger does not purr" << endl;
  }
  if (Fido.bark)  //if bark is a member of Dog, return true
  {
    cout << "Fido barks" << endl;
  }
  else  //if bark is returned as false
  {
    cout << "Fido does not bark" << endl;
  }
  return 0;
}
[/php]

**Edit: **Now that I look at it, my problem has nothing to do with inheritance >_<

---

### Post by DGortze380 on 2010-01-15
> **dodle said:**
> In my code I am trying to show that a cat purrs and a dog barks.  But as it is right now, the output shows that they do not.  Can you help me with my error?  

[php]#include <iostream>
#include <string>
using namespace std;

class Mammal  //create base class
{
};

class Cat : public Mammal  //derived class of Mammal
{
public:
  bool purr;  //show that a cat purrs
};

class Dog : public Mammal  //derived class of Mammal
{
public:
  bool bark;  //show that a dog barks
};

int main()
{
  Cat Tiger;
  Dog Fido;
  if (Tiger.purr)  //if purr is a member of Cat, return true
  {
    cout << "Tiger purrs" << endl;
  }
  else  //if purr is returned as false
  {
    cout << "Tiger does not purr" << endl;
  }
  if (Fido.bark)  //if bark is a member of Dog, return true
  {
    cout << "Fido barks" << endl;
  }
  else  //if bark is returned as false
  {
    cout << "Fido does not bark" << endl;
  }
  return 0;
}
[/php]

**Edit: **Now that I look at it, my problem has nothing to do with inheritance >_<

Correct. You're not inheriting anything yet.

You created two bools, but never assigned them values.

---

### Post by SunSpyda on 2010-01-15
> **DGortze380 said:**
> Correct. You're not inheriting anything yet.

You created two bools, but never assigned them values.

True, but the bool values will either have a garbage bit in them, or the compiler will set them to false (depending on the compiler)... so the cout command should still execute.

---

### Post by dodle on 2010-01-15
I've tried doing:
[php]bool purr = true;[/php]

but the compiler complains:
```
test.cpp:12: error: ISO C++ forbids initialization of member `purr'
test.cpp:12: error: making `purr' static
test.cpp:12: error: ISO C++ forbids in-class initialization of non-const static
member `purr'

```

---

### Post by caelestis2 on 2010-01-15
You cannot set the bool to a value because a class is a template for instantiated objects. In other words, a prototype cannot already have its final form.

When you declare the object is when the values will be set.

To do this you use constructor methods.

```

class Cat : public Mammal {
  bool purr;
public:
  Cat() {
    purr = true;
  }
  bool isPurring() { return purr; }
}

```

then isPurring(); will return true

The constructor Cat() is called during instantiation such as

Cat cat;

and sets purr to true.

---

### Post by issih on 2010-01-15
You don't set the value of a member variable like that.

You need to create a constructor method that initialises the variable you can do this in a couple of ways:

1) set variable within constructors code.
```

class Cat : public Mammal  //derived class of Mammal
{
  public:
    Cat(){
        purr = true;
    }
    bool purr;  //show that a cat purrs
};

```

2) Use an initialisation list
```

class Cat : public Mammal  //derived class of Mammal
{
  public:
    Cat():
    purr(true)
    {}

    bool purr;  //show that a cat purrs
};

```

The constructor is called when you create a Cat object, and therefore the purr field is set.


All in all though if you want to play with inheritance, I suggest you make a void method called speak on your mammal class, that contains just:

```

void speak(){
    cout<<"hello"<<endl;
}

```

then overwrite that method in the the Cat and Dog classes to print purr and woof respectively.

You can then play with setting those methods all to be virtual and use references/pointers to investigate polymorphism....thats where the magic lies.

Hope that helps

---

### Post by dodle on 2010-01-15
Thanks caelestis2 and issih, that is very helpful.  I will play with that.

---

### Post by c0mput3r_n3rD on 2010-01-15
> **dodle said:**
> In my code I am trying to show that a cat purrs and a dog barks.  But as it is right now, the output shows that they do not.  Can you help me with my error?  

[php]#include <iostream>
#include <string>
using namespace std;

class Mammal  //create base class
{
};

class Cat : public Mammal  //derived class of Mammal
{
public:
  bool purr;  //show that a cat purrs
};

class Dog : public Mammal  //derived class of Mammal
{
public:
  bool bark;  //show that a dog barks
};

int main()
{
  Cat Tiger;
  Dog Fido;
  if (Tiger.purr)  //if purr is a member of Cat, return true
  {
    cout << "Tiger purrs" << endl;
  }
  else  //if purr is returned as false
  {
    cout << "Tiger does not purr" << endl;
  }
  if (Fido.bark)  //if bark is a member of Dog, return true
  {
    cout << "Fido barks" << endl;
  }
  else  //if bark is returned as false
  {
    cout << "Fido does not bark" << endl;
  }
  return 0;
}
[/php]**Edit: **Now that I look at it, my problem has nothing to do with inheritance >_<

Just want to mention that you should make your variables private.  Otherwise there is no point of maker you setter/getter functions public.  You also have to make initializing function in your public section a "mammal()" so that you have a function to create an instance of your mammal!!!!  This goes for your cat and dog as well!!!!
I attached a simple inheritance project I wrote for school to demonstrate how to use inheritance properly.  You can also learn how to create a class because you haven't gotten through that yet.  I think you're getting a little ahead of yourself.  If you try to run through a programming language too fast you'll miss things, and if you miss things you'll never be able to write more than what you can copy from the source you're using to learn...

---

### Post by caelestis2 on 2010-01-15
> **c0mput3r_n3rD said:**
> Just want to mention that you should make your variables private.  Otherwise there is no point of maker you setter/getter functions public.  You also have to make initializing function in your public section a "mammal()" so that you have a function to create an instance of your mammal!!!!  This goes for your cat and dog as well!!!!


My example put the purr variable outside of the public: variable making it private. It is a good practice to make the variable private and make setter and getter methods. Why? Becuase when you start using your class often in lots of different files, you may want to change the implementation of setting it, so if you already are using it as a function to set the value, all you have to do is change it.

You do not have to make a constructor for Mammal, if the compiler sees no constructor, it will make a default one. Same goes for destructors.

---

### Post by c0mput3r_n3rD on 2010-01-16
> **caelestis2 said:**
> My example put the purr variable outside of the public: variable making it private. It is a good practice to make the variable private and make setter and getter methods. Why? Becuase when you start using your class often in lots of different files, you may want to change the implementation of setting it, so if you already are using it as a function to set the value, all you have to do is change it.

You do not have to make a constructor for Mammal, if the compiler sees no constructor, it will make a default one. Same goes for destructors.


Right, you may not *have *to make a default constructor, though you should, and is good practice.  This is especially true for when you start writing classes that need variables passed to it when you create an instance, and it's not a good thing that he hasn't done this yet before getting into inheritance.  My comment about default constructors and creating instances was probably knowledge unknown to him

Edit:  And with the private sector, I never heard in my years of programming in c++ that variables not in any sector are automatically deemed private (and I don't really feel like testing it), but again, it's something that he probably doesn't know, and should be done *every time* you create a class.  There are standards to writing to writing c++ code, and it's not just for others programmers reading and using it, it's for a clarity and readability.  You can pick out what you think is wrong with my explanation to him, but fact is I'm teaching him something that should be listened to, and telling him other things are just confusing.  What I wrote previously was standardized, readable code along with teaching him about classes.

---

### Post by caelestis2 on 2010-01-16
I guess you are a lot more strict with your code than I am. I learned that classes have its members private by default on all implementations, and structs are the exact same as classes except their members are public by default. Modifying my above code for structs:

```

struct Cat : public Mammal {
  Cat() {
    purr = true;
  }
  bool isPurring() { return purr; }
private:
  bool purr;
};

```

But I think you should listen to him, code clarity is good. I'm just lazy.

---

### Post by c0mput3r_n3rD on 2010-01-16
> **caelestis2 said:**
> I guess you are a lot more strict with your code than I am. I learned that classes have its members private by default on all implementations, and structs are the exact same as classes except their members are public by default. Modifying my above code for structs:

```

struct Cat : public Mammal {
  Cat() {
    purr = true;
  }
  bool isPurring() { return purr; }
private:
  bool purr;
};

```But I think you should listen to him, code clarity is good. I'm just lazy.


Haha I guess I am a little bit more strict, but definitely for learning purposes it helps.  I definitely learned something though and may just try doing it.... maybe... :)

---

### Post by dwhitney67 on 2010-01-16
> **caelestis2 said:**
> I learned that classes have its members private by default on all implementations, and structs are the exact same as classes except their members are public by default.

And you learned well.  The statement you made above is true.

---

