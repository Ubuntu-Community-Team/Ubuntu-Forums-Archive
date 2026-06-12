---
title: "OOP - Object Oriented Programming"
date: 2014-12-19
forum: Programming Talk
---

### Post by flaymond on 2014-12-19
Hello guys, I'm learning Python 2 and found it very easy to understand. As we all know, Python is an OOP language. It's very weird and I'm stuck at it because I don't understand what is it about. Does OOP is a must learn in ***every*** programming language? What can we do with this OOP features? Is there any others programming language that not use OOP? Help me! I really don't understand what is OOP and what is the use for! :(


Thanks!


EDIT - I already try find the answer on Wiki and I really don't understand since it's similar to module/library in Python. Seriously, what can we do with OOP? That it can make your life easier to programming?

---

### Post by ofnuts on 2014-12-19
Python isn't an OOP language. It's an OO-capable language but unlike other languages (Smaltalk, Java...) it doesn't enforce OO programming.

OO is a mindset/method. It's definitely useful to know, even if it is not the silver bullet that solves all development problems.

---

### Post by flaymond on 2014-12-19
Oh. I didn't know about that. How can I be a good OO programmer? I just programming a few of very simple game on the python console...and it's very easy to understand than OO ...It's very confusing. I'm using Learn Python The Hardway book (3rd edition), and I see the book trying to explaining  me in real world concept. I still don't get it. Why *class *is not same as *object *while both refer to the same meaning. Should I be a good procedural programmer first (like learning C?), than move to C++ or Java to learn OO? I learn choose Python because I want to understand the concept of high-level (actually whole concept) programming. I think OO is easy before I learn, now I'm really stuck at it....should I skip and start learn C? then move to C++/Java?

---

### Post by sudodus on 2014-12-19
It might be a good idea to mix reading books and tutorials with real programming. Don't forget the programming! Try to find something that you want to create (start with something simple - make a program that can do it -  then maybe you can think how it can be made in a more elegant way - more structure - re-use building blocks - easier work flow - think of it as part of a set of programs - ... - or how it can be made in different programming languages, without and with objects etc.

-o-

Try to make your programs simple - easy to understand for the programmer or maintainer - easy to use for the system builder - easy to use for the end user. (It is not easy to make programs simple - it is easier to make them too complicated - but *plan* to make them as simple as possible.)

A very complicated task can be solved with system built from a lot of simple tools.

---

### Post by ofnuts on 2014-12-19
> **InterProg said:**
> Oh. I didn't know about that. How can I be a good OO programmer? I just programming a few of very simple game on the python console...and it's very easy to understand than OO ...It's very confusing. I'm using Learn Python The Hardway book (3rd edition), and I see the book trying to explaining  me in real world concept. I still don't get it. Why *class *is not same as *object *while both refer to the same meaning. Should I be a good procedural programmer first (like learning C?), than move to C++ or Java to learn OO? I learn choose Python because I want to understand the concept of high-level (actually whole concept) programming. I think OO is easy before I learn, now I'm really stuck at it....should I skip and start learn C? then move to C++/Java?

Class and object aren't the same thing. An object is an "instance" of a  class. A class defines a set of attributes/data and a behavior  (methods). An object is a specific set of data values. Under the hood,  UbuntuForums is probably using a "User" class (with attributes such as  name, email, password, list of posts...). When needed they create  instances of that class where the name is "InterProg" or "Ofnuts" (and  matching other attributes). 

A subclass is a class that shares  most of its behavior with a base class. The benefit for the programmer  is that you only have to define the differences: additional methods and  attributes, or methods that replace the ones in the base class (aka  "overload"). For instance they can have a Moderator class which for most  purposes is like a User class. If they add new things for Users (for  instance a FaceBook id) this will also apply to  Moderators.

You can use Python to learn some OO programming because you can do OO in Python. But you aren't forced to.

---

### Post by flaymond on 2014-12-19
Aah, maybe I need to develop my coding skill before I learn OOP. I just create a few simple game, not much experience yet. I will move to C i think....I want to understand how computer background worked first, then I will try to learn the OOP method to develop my skill in programming. I need to understand "why" before I understand "how". Thanks for the advice Ofnuts and Sudodus, you guys are  really kind for helping me to at least understand(a little bit) OOP and change the strategy of learning. I hope when I'm ready and gathered enough experience an knowledges, I can develop Ubuntu together with you guys! :KS

---

### Post by CptPicard on 2014-12-20
> **InterProg said:**
> I need to understand "why" before I understand "how".

I actually do not really believe that understanding the "low level" represented by C necessarily helps you with understanding the ideas behind OOP, although you can certainly write OOP-ish C.

The idea of OOP can be boiled down to the following: There are items of data (things representing the properties of, say, "a car"), and in addition to these items containing just data, they also contain operations on this data. So your car object might have an operation that makes it go forward, and you'd make it happen by saying car.drive(). In your application you can have multiple cars with their separate sets of properties. The definition that all these instances of cars share in common is the class of the car.

Further, these classes can be seen as hierarchies from the most general to the most specific. All cars can "drive" and they have a "position", but only some specific types of car, have more specific operations; maybe some particular makes of cars have a better implementation of "drive" that makes them go faster...

---

