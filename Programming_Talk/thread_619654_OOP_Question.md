---
title: "OOP Question"
date: 2007-11-21
forum: Programming Talk
---

### Post by Nekiruhs on 2007-11-21
I understand the value of objects and methods in OOP. I just don't understand Private and Public variables and methods. I know what they do, I just don't understand why people would use it. Why would I try to hide data from being accessed by me later in my program?

---

### Post by tyoc on 2007-11-21
Because people love to have secrets?:KS

:guitar:

Normally you will "hide" a member if you want it only be accessed certain way. I mean if you "really care" that a certain process or chain of them (OK change process to method or algorithm) is used for change a certain value, htus you hide the value and only expose the method or chain of methods with a single method (lol). that is the only way that from my point of view is valid to hide things, I not see other reasons for that.



As a side point, you normally will end giving the value in question, it is still not accessible from the object, but if you give it away, then at less is not really "hided" for example some like the following pseudo-nothing:

```
class SomeClass:
    private carefullWithMe
   private m1{blah blah bla}
   private m2{super blah! blah! bla!}
   public SecuenceOfComputations{ carefullWithMe = me.m1() + me.m2(carefullWithMe)}
  public getRes{return carefullWithMe}
```If you see, yes you have hide carefullWithMe for direct usage in a instance of the class (aka an object instance), but at end you can retrieve the protected value with getRes ;), still you cant access "directly" the value inside the object instance... and even more, if you have a set method over that member... thus hell ya you cant modify the protected val like you want without call SecuenceOfComputations... ;) and store it again. In oteher words, there is no sense (from my point of view... also should cause a fatall error XD in compiler or related checker... lol) in have something protected when it have get... and even more set methid over it (in fact **both of them**), a private or protected that can be used like you access public members?? shame on me!!!

---

### Post by LaRoza on 2007-11-21
> **Nekiruhs said:**
> I understand the value of objects and methods in OOP. I just don't understand Private and Public variables and methods. I know what they do, I just don't understand why people would use it. Why would I try to hide data from being accessed by me later in my program?

Take this example:

[php]
class Person:
    def  __init__(self,name="J Doe"):
        self.name = name
        self.sex = self.assign_sex() 

    def assign_sex():
        i = randint.randint(0,1)
        if i == 0:
            return 'F'
        if i == 1:
            return 'M'
[/php]

This shows a simple Person object, that takes an optional parameter, which assigns a name. The default is "J Doe" (John or Jane)

You'll see that a sex is assigned randomly, like real life. This attribute, sex, is not something that can be easily changed, so it should be private. Of course, a member function could alter it, like a "sex_change_operation()" method, but you don't want it to be changed accidently.

The function which assigns the sex, in my mind, returns a string of "M" or "F". This function should be private, because using this function outside of the of the the internal use of the contructor doesn't make sense, consider the following:

[php]
#! /usr/bin/python
from Person import Person

me = Person('LaRoza')
me.assign_sex()
[/php]

What is the use of a method which returns a character? It is for internal use only.

Note: I was using Python, which doesn't use the "private" and "public" keywords, but the convention of name methods and attributes with a double underscore, which I didn't do.

---

### Post by Wybiral on 2007-11-21
People often like to code black-box objects. The user of that object should only need to know how the outside interface works. Sometimes to do so you make certain members private. Those are only meant for use by your object itself. This is a way of commenting (saying "HEY, this is only meant to be accessed by the object") and a way of preventing misuse. Leaving too much open makes it easier for the user of the object to improperly use those members.

---

### Post by dwhitney67 on 2007-11-22
The technical term that you probably seek is known as "data encapsulation".

By hiding (declaring private) data members of a class object, you can guard against other classes or functions from depending upon these data items to be available through the course of the life-cycle of a software component.

If for instance you create a class called MyList, and you decide to employ the use of an STL list as the container to store data items, then fine.  Your public methods should provide an interface where one can add items, delete items, or examine items from the list.

If in the future, you decide to replace the STL list with a vector, or some other object, then the public interface that others have relied upon should not change, thus not affecting their code.  That's not to say your implementation code, which relies on private data members will remain the same; there's a high probability it will need to be changed.

However, because your changes are to the internals of your class, it does not affect outside/external references to such.  Hence the concept of data encapsulation.  You hide the data containers, but provide the necessary interfaces (methods) for external modules to use.

P.S.  Sometimes an overlooked fact... in C++, a structure and a class are identical in every means, with one exception.  By default, all data members and methods declared within a struct are deemed to be public.  In a class, they are private.

---

### Post by Ramses de Norre on 2007-11-22
It makes your code easily modifiable, as outlined above, and it takes away a lot of complexity. If you write a library to take care of a complex task, the programmer that uses your library shouldn't worry about that complex task anymore, he shouldn't be thinking of how to solve it because you already did. The only thing the programmer must have is a well-documented interface to the library.

All his focus can then go to solving his problem using your library, not to the problem your library solves.

---

### Post by Siph0n on 2007-11-22
I always found the use of public and privates attributes and methods mostly important when working on a team. If I make an attribute and I don't want to change it after the first time of setting it, I know not to change it. However, another programmer working on the same project may not know that.... So you make it private, and when he tries to change it, he will see that it's not possible. Just my 2 cents :)

---

