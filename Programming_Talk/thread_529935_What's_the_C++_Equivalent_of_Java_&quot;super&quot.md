---
title: "What's the C++ Equivalent of Java &quot;super&quot; keyword?"
date: 2007-08-19
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-08-19
Trying to do something like this:

class Animal
{
     public:
     Animal();
     void makenoise() { printf("Generic Animal Noise");
}

class Dog : public Animal()
{
    public:
    Dog() : Animal();
    void makenoise() { printf("Woof");
}

Dog thisdog = new Dog();
printf("Bark like dog");
thisdog.makenoise();
printf("Make noise");
thisdog.super.makenoise();

In the last line, I want to call the makenoise function of the parent animal class.  how?

---

### Post by CptPicard on 2007-08-19
Animal::makenoise().

There is no way (IMO) to generally refer to the superclass in C++ because of multiple inheritance. Anyway, while coding, you should be able to tell which one the superclass is :)

---

### Post by rbprogrammer on 2007-08-19
> **CptPicard said:**
> 
There is no way (IMO) to generally refer to the superclass in C++ because of multiple inheritance... 


i think i have found an answer. try reading this code:
```

#include <cstdio>
using namespace std;

class Animal
{
public:
    Animal() {}
    void makenoise()
    {
        printf("Generic Animal Noise\n");
    }
};

class Dog : public Animal
{
public:
    Dog() : Animal() {}
    void makenoise()
    {
        printf("Woof\n");
    }
};

int main(int argc, char *argv[])
{
    Dog *dogptr = new Dog();
    printf("Bark like dog: ");
    dogptr->makenoise();
    printf("Make noise: ");
    ((Animal*)(dogptr))->makenoise();

    Dog regdog;
    printf("Bark like dog: ");
    regdog.makenoise();
    printf("Make noise: ");
    ((Animal)regdog).makenoise();

    printf("\n");

    return 0;
}

```
****NOTE:**
i have not debugged this much. i have not tried it for multiple inheritance, nor calling a function like:
```
((Animal)regdog).MakeSound();
```
so i dont know what the program will do, especially with multiple inheritance.

also, i put two different notations, one with pointers and one without.  in your example you seemed to mix them.  lol, i could sense the java in you :lolflag: ..

---

### Post by rbprogrammer on 2007-08-19
just thought i would also like to point out that you are using the C printf() function, while using C++'s classes.

dont know if you wanted purely C or wanted to go with C++.  anyway, the code i gave you should work, i think i had to:
```

$ g++ animal.cpp -o animal
$ ./animal

```

i use printf() a lot, for formatting..

---

### Post by CptPicard on 2007-08-19
Yeah, you can upcast a pointer, and  I think ((Animal*)this)->makenoise() would perhaps do, but it's still not equivalent as a solution to the super keyword, which is a generalized superclass reference -- you still need to know what you're casting to -- besides, it assumes the function is virtual for it to work.

Therefore, I still maintain that my solution is the correct, non-ugly-hack way to do it :)

---

### Post by SNYP40A1 on 2007-08-19
Yeah, multiple inheritance is the reason there is no super keyword in C++.  Makes sense.  I'll probably just leave my code as is an have two functions in the "animal" class which do exactly the same thing.

And yeah, I did mix up the pointers :-).  I wish C++ was more like Java...I guess there is .NET...

---

### Post by Mirrorball on 2007-08-19
I think it's a sign of bad design that you need to call the parent function. When you override a function in a child class, it should do what the parent function does in a way that is more adequate for that kind of object. The function was overridden exactly because it doesn't work for the child object. So why would you want to call the function from the parent class? You will be breaking things. And if what they do is different, then their names should be different.

---

### Post by rbprogrammer on 2007-08-19
> **Mirrorball said:**
> I think it's a sign of bad design that you need to call the parent function. When you override a function in a child class, it should do what the parent function does in a way that is more adequate for that kind of object. Why would you want to call the function from the parent class? If what they do is different, then their names should be different.

i think Mirrorball is the most correct.  even though my method of casting works kind of the same way Java's **[FONT="Courier New"]super[/FONT]** does, Mirrorball is correct in saying that naming the child class method is probably not the best way of programming

---

### Post by pmasiar on 2007-08-20
> **CptPicard said:**
> There is no way (IMO) to generally refer to the superclass in C++ because of multiple inheritance. 

Funny but in Python there is super() built-in method:

> 
super( 	type[, object-or-type])
    Return the superclass of type. If the second argument is omitted the super object returned is unbound. 
If the second argument is an object, isinstance(obj, type) must be true. 
If the second argument is a type, issubclass(type2, type) must be true. 
super() only works for new-style classes.

    A typical use for calling a cooperative superclass method is:
```

    class C(B):
        def meth(self, arg):
            super(C, self).meth(arg)

```
    Note that super is implemented as part of the binding process for explicit dotted attribute lookups such as 
"super(C, self).__getitem__(name)". 
Accordingly, super is undefined for implicit lookups using statements or operators such as "super(C, self)[name]". 


and [improved version](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/286195)

IMHO even multiple inheritance is not against using super, if there is known search order: In python, it is deep-first, left-to-right. First superclass with method wins.

Of course unless I am missing something, multiple inheritance is not my daily fare :-)

---

### Post by slavik on 2007-08-20
also, shouldn't makenoise in class Animal be declared virtual?

---

### Post by martindorey on 2009-04-11
Casting a pointer to a Dog to a pointer to an Animal only does the right thing because makenoise isn't virtual.  makenoise would need to be virtual in a more realistic example, exactly for the opposite effect than the one presented here - when asked to make a noise via its Animal interface, a Dog should bark.

Casting a Dog to an Animal constructs a temporary, unnamed Animal, copying that Animal's fields from the Dog.  Animal would probably be abstract in a more realistic example, which would prevent this solution from working.

The right solution is Animal::makenoise(), as CptPicard said.  Where multiple inheritance isn't in play, you can define:

typedef Animal Base;

And refer to Base::makenoise.  "Base::" is perhaps the more conventional name in C++ for "super.".

---

### Post by scourge on 2009-04-11
> **Mirrorball said:**
> I think it's a sign of bad design that you need to call the parent function. When you override a function in a child class, it should do what the parent function does in a way that is more adequate for that kind of object. The function was overridden exactly because it doesn't work for the child object. So why would you want to call the function from the parent class? You will be breaking things. And if what they do is different, then their names should be different.

There's nothing wrong with calling the parent function. In fact, unless the parent function is pure virtual you're often expected to call it from a subclass' implementation. Inherited methods are not necessarily supposed to replace the base method, but to extend it.

Take a look at Qt for example, which has some of the most elegantly designed C++ libraries. The documentation for many of the abstract classes says something like "Subclasses that reimplement this function must call the base implementation...".

---

### Post by dribeas on 2009-04-11
@rbprogrammer: You are slicing the object: creating an Animal object that is not the Dog object but a copy (using the copy constructor in Animal if defined) and then calling the method on the temporary Animal object. This seems to work in the example as the example function does not have any side effects, but would not in the general case:

```

class Animal
{
public:
   Animal( int x ) : x_( x ) {}
   void set( int x ) { x_ = x; }
   int get() const { return x_; }
protected:
  int x_;
};
class Dog
{
public:
   Dog( int x ) : Animal( x ) {}
   void set( int x ) { x_ = x*2; }
};
int main()
{
   Dog d( 1 );
   static_cast<Animal>(Dog).set( 5 );
   std::cout << d.get << std::endl; // will output 1, d.x_ is unchanged
}

```

@slavik: It should (or not) be declared virtual if you want polymorphism (or not). The most common use case is that make_noise() is in fact a polymorphic call (you want to get your animal to make a noise, but that noise is dependent on the animal you have). So, yes, I would make it virtual. And that takes me to another comment:

@CptPicard: in this case (as it is not marked virtual) casting the pointers would be equivalent, but in the case where the method is declared virtual, the code executed will be that of the real type of the element. That is, in the original example, with virtuals on:

```

static_cast<Animal*>(&regdog)->make_noise(); // bark
static_cast<Animal>(regdog).make_noise(); // generic noise
static_cast<Animal&>(regdog).make_noise(); // bark again

```

That is because casting the pointers will maintain polymorphism (as references): the object pointed is unchanged, just the pointer. Casting the objects will create a temporary object 'slicing' (that is the common term) the original. The result of the cast is not a Dog anymore, but a generic Animal.

---

### Post by dribeas on 2009-04-11
> **scourge said:**
> 
Take a look at Qt for example, which has some of the most elegantly designed C++ libraries. The documentation for many of the abstract classes says something like "Subclasses that reimplement this function must call the base implementation...".

QT is by no means one of the 'most elegantly designed C++ libraries'. If you want good C++ code, go for Boost, Adobe Source Libraries, PoCo... QT has some really nice features but the implementation is by no means elegant.

I agree that it is often needed to call the bases method from within the derived method, but that is not what the post was about. The post deals with calling a base method *from ouside the object*. If a method is reimplemented in a derived class, it is, as it was said before, because the original implementation does not fit the derived object. And the derived object knows.

If the derived class wants to call the base method, it can easily do it, but it is an implementation decision. Outsiders cannot know what it can imply in the implementation. And it can sometimes break running code by breaking invariants of the derived class that are not present in the base class.

Consider a vector implementation vector1 where you can set the maximum expected size with a method call (say: reserve( 10 )) that changes a protected value reserve_ but that completely ignores it. At each push_back it will allocate the new memory and copy the element there. Now you could extend the class with a vector2, that provides basically the same operations. The difference is that when the user calls reserve() the class will acquire all the memory at that point. In the derived class, push_back operations only trigger memory allocation if size()>=reserve().

If a user does call the parent reserve() method on a derived vector, the reserve_ field will be updated, but memory will not be allocated. The next push_back will assume that since this is a vector2 element and reserve_ is high enough, then no memory needs to be acquired and suddendly your application dies.

Of course, the implementor of vector2 can call if she wants the parent's method:

```

void vector2::reserve( int x ) {
   ensure_buffer_capacity( x );
   vector1::reserve( x ); // update the reserved_ field and any operation the base does
}

```

But it is not up to the external user to decide.

---

### Post by scourge on 2009-04-12
> **dribeas said:**
> QT is by no means one of the 'most elegantly designed C++ libraries'. If you want good C++ code, go for Boost, Adobe Source Libraries, PoCo... QT has some really nice features but the implementation is by no means elegant.

I guess that's subjective. I think Qt's interfaces are clean and well designed, and their class hierarchy makes a lot of sense. Boost is seriously powerful and highly optimized, but to me it looks like a big template mess.

> I agree that it is often needed to call the bases method from within the derived method, but that is not what the post was about. The post deals with calling a base method *from ouside the object*.

To me it wasn't obvious that the poster I quoted was talking about calling the base method from outside, even if the OP was. If so, then we agree, that would be ridiculous.

---

### Post by dwhitney67 on 2009-04-12
The code as the OP has presented is replete with syntax errors; here's the syntactically correct listing, although I rewrote the main() function.

```

#include <cstdio>

class Animal
{
  public:
    Animal() {}
    void makenoise() { printf("Generic Animal Noise\n"); }
};

class Dog : public Animal
{
  public:
    Dog() : Animal() {}
    void makenoise() { printf("Woof\n"); }
};

int main()
{
  Dog cujo;

  // this calls the Dog's makenoise() method
  cujo.makenoise();

  // this calls Animal's makenoise() method
  cujo.Animal::makenoise();
}

```

All of the dogs and other types of animals I have seen never make a "generic" noise, thus in this particular app, the base-class makenoise() method should be declared as a pure-virtual, thus forcing subclasses to implement it to be representative of the particular animal.

---

### Post by evaklo on 2010-08-10
> **Mirrorball said:**
> I think it's a sign of bad design that you need to call the parent function. When you override a function in a child class, it should do what the parent function does in a way that is more adequate for that kind of object. The function was overridden exactly because it doesn't work for the child object. So why would you want to call the function from the parent class? You will be breaking things. And if what they do is different, then their names should be different.


I'm sorry, but you are wrong. Calling methods of your superclass is a better design pattern, the clearest example is the Template Method. 
You subclass from an object to inheritence behaviour, and redefine it when necessary. So in most cases calling your super class should be the way to go.

---

### Post by dwhitney67 on 2010-08-10
> **evaklo said:**
> I'm sorry, but you are wrong. Calling methods of your superclass is a better design pattern, the clearest example is the Template Method. 
You subclass from an object to inheritence behaviour, and redefine it when necessary. So in most cases calling your super class should be the way to go.

Although you are correct, did you have to resurrect a thread that is over a year old?

---

### Post by evaklo on 2010-08-10
> **dwhitney67 said:**
> Although you are correct, did you have to resurrect a thread that is over a year old?

I'm sorry, I didn't notice that. I've just started programming in C++ and I got accross this post.
Bye :p

---

### Post by interval1066 on 2010-08-10
An object can be used as its own type or as an object of its base type. In addition it can be manipulated through an address of the base type. Taking the address of an object (either a pointer or a reference) and treating it as the address of the base type is called upcasting in C++, and is perfectly legal, and being multiply or singly inherent makes no difference.

---

### Post by dribeas on 2010-08-10
The proper way of doing this is by qualifying the function that you are calling in exactly the same way that you would do to call a function that has been hidden. Note that this disables dynamic method dispatch:

```

class Animal {
public:
    virtual void sound() { std::cout << "dunno" << std::endl; }
};
class Dog : public Animal {
public:
    virtual void sound() { std::cout << "bark" << std::endl; }
};
int main() {
   Dog dog;
   dog.sound();  // bark
   dog.Animal::sound(); // dunno
   ((Animal)dog).sound();   // 1
   ((Animal&)dog).sound(); // 2
}

```

Note 1: The code marked with 1 is actually an static_cast<Animal>(dog), and while it will seem to work in this case, the code is actually creating a copy of the Animal subobject and calling the method on that copy --i.e. if the method modified any state, the change would not be visible in the 'dog' object.

Note 2: The code marked with 2 will create a reference of type Animal to the 'dog' object. The problem with this approach is that if the method is virtual, like in my example, the virtual dispatch mechanism will kick in and dispatch the call to the most derived object, which in this case is of type ' Dog' --i.e. calling a virtual method through a reference of type base or derived will produce exactly the same result.

---

