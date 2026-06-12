---
title: "Um...Why am I supposed to love interfaces?"
date: 2009-05-11
forum: Programming Talk
---

### Post by fiddler616 on 2009-05-11
Hello,

I've been wondering about interfaces. I haven't formally learned about them, but from what I understand an interfaces defines a bunch of methods, but doesn't define what they *do*, and then you can implement that in a class, and you'll be required to recreate those methods as part of the class.

And I've gotta admit, it's kind of cute using them for stuff like Java applets.

But it seems like all in all, it's a bit useless. What do interfaces do that documentation like this
> Please use the following method names:
foo()
bar(int x)
spam(String type)
eggs(String size, Chicken donor, Farm farm)
OK, thanks.
won't do?

And I notice that the other language I know--Python--doesn't even have them ([failed PEP]("http://www.python.org/dev/peps/pep-0245/")).

So...am I just missing something?

---

### Post by kknd on 2009-05-11
Python, Lua, etc doesn't need interfaces because of the type system.

In C++ and Java, you need it , because the type checking is done at compile time (think about the case you are using polymorphism).

---

### Post by issih on 2009-05-11
One potential benefit is that it allows you to gain some of the benefits of multiple inheritance without all of the problems that can bring.

In essence, in the same way as defining a superclass with those methods will mean that any instances of a subclass of that superclass will have those methods available, implementing an interface also provides that guarantee, consequently you can type a variable as the interface, in the same way you can type it as the superclass.

The point of an interface then is to allow this behaviour for potentially wildly different classes, which come from entirely different type hierarchys. As long as the class implements an interface, it MUST provide those methods, and any variables of that class can be typed as the interface.

By not having the interface define the methods at all but merely require their existence, we can avoid problems associated with multiple inheritance (e.g. having multiple definitions of the same method in both superclass definitions, and the resultant problems of disambiguation).

In many ways, you can think of an interface as an allowed form of multiple inheritance, where the secondary superclass is strictly abstract in order to avoid difficulties.

Languages that are dynamically typed simply don't need these kind of structures.

Hope that helps

---

### Post by Reiger on 2009-05-11
Interfaces aren't a bunch of methods. Interfaces are part of the principle that you "code by contract": an Interface constitutes a binding contract between implementing thing (who is required to supply as per Interface specs) and using thing. If you break it: your app crashes/won't build. :P

Why you would love them? ... Well if only for the fact that at least in Java you can write your Javadoc only once using them: the doc strings are inherited. Plus of course that writing backends which can be swapped on the fly is now feasible. Better yet you can exchange code from two different (virtual) locations better if you use Interfaces: it does not require you to supply at least one working implementation of the interface until it is necessary to have it.

---

### Post by grepgav on 2009-05-11
You don't necessarily have to "love" them, but for statically typed OO languages they can be useful for creating generic and flexible code. Other people have made many valid points - here is a brief, trivial example which may help give understanding to it:

Let's say you have an interface Shape that defines just a single function:
int getArea()

Then you have three classes: Circle, Square, and Triangle, all of which implement this interface. All three have different methods of calculating the area, but you could then have an array of Shapes.

You could then sum the areas of the entire array, no matter what types of shapes they are.

Now this same behavior could be done with a superclass and method overriding in this situation. However, lets say you had another class that was not a shape. 

Lets say you had a class called Floor, and for some reason (not realistic) you wanted to include it with the shapes. A Floor could also implement the Shapes interface and then be handled in the same manner. It wouldn't make sense for Floor to be a subclass of a Shapes superclass, so the interface would be needed.

Interfaces are also nice because I believe you can implement multiple interfaces, but inheritance for a subclass only can be of one superclass for a given class.

---

### Post by fiddler616 on 2009-05-11
@everyone: Thanks! I'm slowly understanding (if not grokking).

> **grepgav said:**
> It wouldn't make sense for Floor to be a subclass of a Shapes superclass, so the interface would be needed.
I see where you're coming from, but it's hardly fair to say that
```
public class Floor implements Shape
```
is better than
```
public class Floor extends Shape
```

And I'm with you guys about type-checking and whatnot, and definitely understand the interface vs. superclass issue, it just seems a little funny to have such a formal way of saying "Please use these methods."

---

### Post by grepgav on 2009-05-12
> **fiddler616 said:**
> @everyone: Thanks! I'm slowly understanding (if not grokking).


I see where you're coming from, but it's hardly fair to say that
```
public class Floor implements Shape
```
is better than
```
public class Floor extends Shape
```

And I'm with you guys about type-checking and whatnot, and definitely understand the interface vs. superclass issue, it just seems a little funny to have such a formal way of saying "Please use these methods."

Inheritance is not only indicative of behaviour - but also semantics. If you use inheritance for two unrelated classes, the whole class hierarchy loses a lot of it's value.

What if Floor was a subclass of a Surface class, but you still want to be able to treat it as a Shape for the purposes of area calculation? At that point, an interface is the answer.

Shape is not a good example of an interface. A better example would be something like HasArea (just for this trivial example).

An interface could just be saying the class has some method of giving a certain attribute semantically.

It's not about "please use these methods" it is more about a contract saying that it guarantees to implement that method, so even if you don't know the exact type of the object you know for sure at least a subset of it's behaviour.

[http://en.wikipedia.org/wiki/Interface_(Java](http://en.wikipedia.org/wiki/Interface_(Java))

---

### Post by issih on 2009-05-12
The main point, is that by using an interface it moves from being "please use these methods" as you put it to a cast iron guarantee that those methods are there.

This guarantee is what allows you to type an variable of an object as the interface it implements, as the compiler can be 100% certain that those methods are there when they are called.

Without the guarantee, the compiler can't type the object as anything other than its actual class or one of its superclass, as those are the only guaranteed methods it knows about.

Being able to type as the interface allows you to do things like throw a bunch of arbitrary objects into a set, then access them all as a common interface without ever caring what the actual type of any given object is.

Hope that helps

---

### Post by bruce89 on 2009-05-12
Interfaces in GObject can actually have implementations. The only real difference between them and abstract classes in GObject is therefore the fact that classes can implement multiple interfaces, but can only have one parent class.

---

### Post by Can+~ on 2009-05-12
> **fiddler616 said:**
> @everyone: Thanks! I'm slowly understanding (if not grokking).

Let's say that [mammals]("http://en.wikipedia.org/wiki/Mammal") are animals that can give birth (not egg), are hot-blooded, etc.

Now let's say that other creatures, such as reptiles, birds use eggs.

So you have your hierarchy Animal - Mammal - Giraffe for example, that's ok, but what happens with the [Platypus]("http://en.wikipedia.org/wiki/Platypus")? It's a mammal that lay eggs, how can you derive such a creature from a Mammal?

Platypus extends Mammals implements Oviparous

Another example, your son will share some physical attributes with you, but if he may not decide to study your own career, or follow your steps, he'll probably "implement" a life of it's own.

In more crude terms, Interfaces and such are workarounds for statically typed languages which lack Polymorphism, for objects that have or may have different behaviours. In python you would add the attribute/method on runtime and, if an object doesn't know how to quack, it's not a duck ([duck typing]("http://en.wikipedia.org/wiki/Duck_typing")).

---

### Post by fiddler616 on 2009-05-12
> **Can+~ said:**
> 
Platypus extends Mammals implements Oviparous

This was one of the best sentences I've seen in Programming Talk in the past few months :) .

I think I get it though--albeit if talk of compilers left me a bit lost.

One of my mental obstacles (which actually extends to most of OOP in general) is that I read the [Zen of Python]("http://www.python.org/dev/peps/pep-0020/") (which I try to apply to Java too. Sue me.)  with "simple is better than complex" before "beautiful is better than ugly." It'd be simpler to just bolt Oviparous methods onto my Platypus, but more beautiful to use an interface.

---

### Post by slavik on 2009-05-12
because you wrote a framework that accepts a foreign object and you want to make sure that the object will have some guaranteed functionality, you can enforce this in your code rather than just documentation and comments

---

### Post by monkeyking on 2009-05-12
If you are working on a project with some other programmers.

And you need them to implement some stuff,
and you don't care about how they do it,
as long as your part can use their part.

Then just give them an interface to implement.

---

