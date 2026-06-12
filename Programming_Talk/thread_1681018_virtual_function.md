---
title: "virtual function???"
date: 2011-02-03
forum: Programming Talk
---

### Post by Praveen30 on 2011-02-03
i got to know virtual function is a important concept of object oriented programming..it is not just the overriding and overloading..if anyone really wants to excel in object oriented programming then it is very much required...so can anyone please tell me what is this and why is it required???

---

### Post by Zugzwang on 2011-02-03
The wikipedia article seems to be usable in this case: [http://en.wikipedia.org/wiki/Virtual_function](http://en.wikipedia.org/wiki/Virtual_function)

Do you have any questions regarding this article?

---

### Post by Ferrat on 2011-02-03
Virtual functions lets you override a "standard" 

for ex. in games overriding functions is extremely useful as you can have a generic response and then use virtual functions that let you override those without bothering with the other functions. 

Say you have a basic class named Unit for your RTS game, in this are functions for attack, movement etc.

Well you want to use more or less the same basics for attack but you want a mounted unit and there for movement is different but still uses the same argument inputs. 

Using virtual functions you can use the class unit as a base and then build a mounted unit class on-top of that with minimal effort, just changing the movement function while all other functions are the same as basic unit functions. 

Also say you want ranged units but they move just the same but attack in a different way, then you just build a class called ranged_unit and just add the new attack function in that and keeping the basic movement function. 


This way you minimize your work and make the program more efficient, it also makes it easier to get an overview of objects and where the different functions reside.

---

### Post by Praveen30 on 2011-02-03
> **Zugzwang said:**
> The wikipedia article seems to be usable in this case: [http://en.wikipedia.org/wiki/Virtual_function](http://en.wikipedia.org/wiki/Virtual_function)

Do you have any questions regarding this article?

It is written here--

The distinction between virtual and non-virtual resolves this ambiguity.

is this the main work of virtual function?? it means we can use virtual function in case of inheritance only and it  uses overriding....is it true??

---

### Post by nvteighen on 2011-02-03
The thing about virtual functions is that they "bind" the method to the object rather to the type. This is may a bit hard to get in abstract, so let me show some code to you.

You know that you can override a method of a parent class in any of its children, so that you can specify a particular behaivor for the objects of that child class. For example:

```

#include <iostream>

class Animal
{
public:
    Animal() {}

    void talk()
    {
        std::cout << "..." << std::endl;
    }
};

class Cat : public Animal
{
public:
    void talk()
    {
        std::cout << "Meow!" << std::endl;
    }
};

class Dog : public Animal
{
public:
    void talk()
    {
        std::cout << "Woof!" << std::endl;
    }
};

int main(void)
{
    Animal someAnimal;
    Cat someCat;
    Dog someDog;

    someAnimal.talk();
    someCat.talk();
    someDog.talk();

    return 0;
}

```

And it works flawlessly. It prints "...", "Meow!", "Woof!" as expected.

The problem is that, sometimes, you may know that some object is an Animal, but not whether it is a Cat or a Dog. In those situations, you surely know that you can declare the object to be an Animal... But look what it happens with this code:

```

#include <iostream>

class Animal
{
public:
    Animal() {}

    void talk()
    {
        std::cout << "..." << std::endl;
    }
};

class Cat : public Animal
{
public:
    void talk()
    {
        std::cout << "Meow!" << std::endl;
    }
};

class Dog : public Animal
{
public:
    void talk()
    {
        std::cout << "Woof!" << std::endl;
    }
};

void make_it_talk(Animal& myAnimal)
{
    /* Ok, this is a bit silly, but it's for explanatory purposes. I'm using a
     * reference as argument actually to simplify stuff... */

    myAnimal.talk();
}

int main(void)
{
    Animal someAnimal;
    Cat someCat;
    Dog someDog;

    make_it_talk(someAnimal);
    make_it_talk(someCat);
    make_it_talk(someDog);

    return 0;
}

```

The important aspect here, despite the stupid example of calling the talk method indirectly via a procedure, is that in make_it_talk the object passed as an argument is declared as a reference to an Animal, even though what was passed could have been a reference to a Cat or to a Dog too. So, even though a Cat and a Dog were passed, respectively, in the second and third calls to make_it_talk, the output will be "...", "...", "...".

Why? Well, because the type of the object is declared to be Animal (well, we're using a reference to an Animal...), so Animal::talk is used even though the object passed is a Cat or a Dog.

Here's where virtual comes in. Virtual methods are chosen not by the type declared, but by the object's "real nature". Try this:

```

#include <iostream>

class Animal
{
public:
    Animal() {}

    virtual void talk()
    {
        std::cout << "..." << std::endl;
    }
};

class Cat : public Animal
{
public:
    Cat() {}

    virtual void talk()
    {
        std::cout << "Meow!" << std::endl;
    }
};

class Dog : public Animal
{
public:
    Dog() {}

    virtual void talk()
    {
        std::cout << "Woof!" << std::endl;
    }
};

void make_it_talk(Animal& myAnimal)
{
    /* Ok, this is a bit silly, but it's for explanatory purposes. I'm using a
     * reference as argument actually to simplify stuff... */

    myAnimal.talk();
}

int main(void)
{
    Animal someAnimal;
    Cat someCat;
    Dog someDog;

    make_it_talk(someAnimal);
    make_it_talk(someCat);
    make_it_talk(someDog);

    return 0;
}

```

See, despite having declared the parameter as a reference to an Animal object, by having it declared as virtual, the talk method becomes executed depending on what the object really is.

---

### Post by Praveen30 on 2011-02-03
Such a nice explanation, thanks.

---

### Post by Tony Flury on 2011-02-04
> **Praveen30 said:**
> i got to know virtual function is a important concept of object oriented programming..it is not just the overriding and overloading..if anyone really wants to excel in object oriented programming then it is very much required...so can anyone please tell me what is this and why is it required???

in python every method is virtual - as everything is derived from the type of the object - the type of an object does not have to be declared in every procedure, function etc.

---

### Post by nvteighen on 2011-02-04
> **Tony Flury said:**
> in python every method is virtual - as everything is derived from the type of the object - the type of an object does not have to be declared in every procedure, function etc.

Hehe... I was convinced this thread was specifically on C++... Reading the original post again, I see it wasn't.

Ok, this doesn't invalidate my post, of course. But it's true that the 'virtual' keyword hassle is mostly a C++-specific issue. Java or Python make everything virtual by default. Look at these examples:

```

# Python

class Animal(object):
    def talk(self):
        print("...")

class Cat(Animal):
    def talk(self):
        print("Meow!")

class Dog(Animal):
    def talk(self):
        print("Woof")

def make_it_talk(something):
    something.talk() # Ah, the joys of dynamic typing: we just assume this
                     # object has a talk method when reaching this point of
                     # execution.

def main():
    someAnimal = Animal()
    someCat = Cat()
    someDog = Dog()

    make_it_talk(someAnimal)
    make_it_talk(someCat)
    make_it_talk(someDog)

# Boilerplate to make the module start from main() unless imported as a library.
if __name__ == "__main__":
    main()

```

```

// Java

class Animal
{
    public void talk()
    {
        System.out.println("...");
    }
}

class Cat extends Animal
{
    public void talk()
    {
        System.out.println("Meow!");
    }
}

class Dog extends Animal
{
    public void talk()
    {
        System.out.println("Woof!");
    }
}

public class Main
{
    private static void make_it_talk(Animal someAnimal)
    {
        someAnimal.talk();
    }

    public static void main(String[] argv)
    {
        Animal someAnimal = new Animal();
        Cat someCat = new Cat();
        Dog someDog = new Dog();

        make_it_talk(someAnimal);
        make_it_talk(someCat);
        make_it_talk(someDog);
    }   
}

```

I wanted to show both Python and Java to show how two radically different languages concur in the way of doing this particular thing. As you see, there's no explicit declaration as 'virtual' because everything already is... methods are executed taking the "nature" of the object in account rather than the particular type it has been declared as. It's also quite interesting to see this considering that Java is a static-typed language like C++, so the need for a 'virtual' keyword in C++ doesn't come from the typing discipline. In Python this much clearer: in a language where almost everything is resolved at runtime, it's quite obvious to have methods be chosen according to what the object *is* at that particular moment.

---

### Post by Rany Albeg on 2011-02-04
**nvteighen**, 
You should get a medal on this explanation, **thank you!**

---

### Post by nvteighen on 2011-02-05
> **Rany Albeg said:**
> **nvteighen**, 
You should get a medal on this explanation, **thank you!**

:)

---

