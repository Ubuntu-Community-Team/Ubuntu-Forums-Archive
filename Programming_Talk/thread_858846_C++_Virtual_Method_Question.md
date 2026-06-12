---
title: "C++ Virtual Method Question"
date: 2008-07-14
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-14
If I declare a method of some C++ class to be virtual and I then inherit from that class and provide a new implementation for that method, but I don't use the virtual keyword, is it the method of the class that extends the base class still virtual?

Something like this:

class Animal
{
   public:
   Animal();
   virtual void Eat();
}

class Dog
{
   public:
   Dog();
   void Eat();
}

And then somewhere later, if I do:

Animal someanimal = new Dog();
someanimal.Eat();

Which Eat function gets called on that last line?  The one in Dog or the one in Animal?

---

### Post by slavik on 2008-07-14
no it's not.

class A { virtual print("I am A"); }
class B : public A { print("I am B"); }
class C : public B { print("I am C"); }

not sure what g++ will say, but I am sure you can't override a non-virtual method (in Java all methods are virtual by default).

---

### Post by Quikee on 2008-07-14
> **SNYP40A1 said:**
> If I declare a method of some C++ class to be virtual and I then inherit from that class and provide a new implementation for that method, but I don't use the virtual keyword, is it the method of the class that extends the base class still virtual?

Something like this:

class Animal
{
   public:
   Animal();
   virtual void Eat();
}

class Dog
{
   public:
   Dog();
   void Eat();
}

And then somewhere later, if I do:

Animal someanimal = new Dog();
someanimal.Eat();

Which Eat function gets called on that last line?  The one in Dog or the one in Animal?

Dog.Eat(); is called. This is one of C++ weirdness - you have to define your method "virtual" so that polymorphism works as it was meant to work in OOP (I consider Smalltalk the reference implementation of a OO language).

Also if you want to also call Eat() from Animal - you can explicitly do so by calling Animal::Eat(); (something like super() call in Java, but explicit because of multiple inheritance).

---

### Post by SNYP40A1 on 2008-07-14
> **Quikee said:**
> Dog.Eat(); is called. This is one of C++ weirdness - you have to define your method "virtual" so that polymorphism works as it was meant to work in OOP (I consider Smalltalk the reference implementation of a OO language).

Also if you want to also call Eat() from Animal - you can explicitly do so by calling Animal::Eat(); (something like super() call in Java, but explicit because of multiple inheritance).

I appreciate C++ for performance, but it really does feel like an outdated language sometimes.  For example, I should just be able to list whatever files I want to include and not have to worry about #IFNDEF statements.  The compiler should be able to just figure it out and resolve dependence cycles automatically as the Java compiler does.  Although that's a complaint about the compiler and not necessarily the language.

---

### Post by Sockerdrickan on 2008-07-14
Yeah that was under the belt SNYP40A1 and I'm sure there are times when you want this.

---

### Post by jim_24601 on 2008-07-14
> **SNYP40A1 said:**
> If I declare a method of some C++ class to be virtual and I then inherit from that class and provide a new implementation for that method, but I don't use the virtual keyword, is it the method of the class that extends the base class still virtual?

Something like this:

class Animal
{
   public:
   Animal();
   virtual void Eat();
}

class Dog
{
   public:
   Dog();
   void Eat();
}

And then somewhere later, if I do:

Animal someanimal = new Dog();
someanimal.Eat();

Which Eat function gets called on that last line?  The one in Dog or the one in Animal?

Well, in your case nothing is called because you have a typo. The type of 'new Dog' is Dog* and cannot be cast to Animal. If you wrote

```
Animal* someanimal = new Dog;
someanimal->Eat();
```

then Dog's Eat() method would be called. A method that is declared as virtual in the base class is virtual for ever more; the derived class need not explicitly declare it virtual if/when it overrides it.

Header include guards? I don't even see them any more (I just see blonde, brunette, redhead...) A decent IDE will put them in for you anyway when you create a header.

And I'm not at all sure that having everything virtual by default is a good idea. There are reasons for defining a class that don't require it to be polymorphic, and I abominate code generation tools that make every member protected and every method virtual because they assume you're going to create labyrinthine and n00bish inheritance hierarchies...

---

### Post by jim_24601 on 2008-07-14
> **slavik said:**
> no it's not.

Yes it is.

> 
class A { virtual print("I am A"); }
class B : public A { print("I am B"); }
class C : public B { print("I am C"); }

not sure what g++ will say,

Whatever it says won't be very polite, because this is nonsense. If you said, for example

```

class A { public: virtual void print() { cout << "I am A\n"; } };
class B : public A { void print() { cout << "I am B\n"; } };
class C : public B { void print() { cout << "I am C\n"; } };

```

and then called them thus

```

A* a = new A;
A* b = new B;
A* c = new C;
a->print();
b->print();
c->print();

```

you would get the output

```

I am A
I am B
I am C

```

> but I am sure you can't override a non-virtual method (in Java all methods are virtual by default).

You can't, but that's not what the question asked.

---

