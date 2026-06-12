---
title: "Java question"
date: 2006-05-30
forum: Programming Talk
---

### Post by Phil_McCrackin on 2006-05-30
Just a programming question here. I am reading a book on Java and learning myself. I am profficient in C/C++ so I am not new to most of the logic, structures, etc.

Some of what has thrown me off (unecessarily) is simply the terminology (ex: a method is a function, etc). 

I am really befuddled about packages and interfaces. As far as I can tell a package is simply a file to store similar classes. An interface well...let's just say I have not achieved enlightenment. I learn from implementation usually and am trying to compile this sample program consisting of 3 files in the same package. The first class compiled no problem but the second is getting 4 error messages everywhere I try to implement the first...see code:

this class compiled:
Item.java
```
package com.prefect.ecommerce;

import java.util.*;

public class Item implements Comparable {
	private String id;
	private String name;
	private double retail;
	private int quantity;
	private double price;

	Item(String idIn, String nameIn, String retailIn, String quanIn) {
	id = idIn;
	name = nameIn;
	retail = Double.parseDouble(retailIn);
	quantity = Integer.parseInt(quanIn);

	if (quantity > 400)
		price = retail * .5D;
	else if (quantity > 200)
		price = retail * .6D;
	else
		price = retail * .7D;
	price = Math.floor( price * 100 + .5 ) / 100;
	}

	public int compareTo(Object obj) {
		Item temp = (Item)obj;
		if (this.price < temp.price)
			return 1;
		else if (this.price > temp.price)
			return -1;
		return 0;
	}

	public String getId() {
		return id;
	}

	public String getName() {
		return name;
	}

	public double getRetail() {
	return retail;
	}
	
	public int getQuantity() {
	return quantity;
	}
	
	public double getPrice() {
	return price;
	}
}

```

this one will not:
Storefront.java
```
package com.prefect.ecommerce;

import java.util.*;

public class Storefront {
	private LinkedList catalog = new LinkedList();

	public void addItem(String id, String name, String price, String quant) {
	Item it = new Item(id, name, price, quant);
	catalog.add(it);
	}

	public Item getItem(int i) {
		return (Item)catalog.get(i);
	}
	
	public int getSize() {
		return catalog.size();
	}
	
	public void sort() {
		Collections.sort(catalog);
	}
}

```

here are my error messages:
```
theadmin@stub:~/Programming/Java/com/prefect/ecommerce$ javac Storefront.java
Storefront.java:13: cannot resolve symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
        public Item getItem(int i) {
               ^
Storefront.java:9: cannot resolve symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
        Item it = new Item(id, name, price, quant);
        ^
Storefront.java:9: cannot resolve symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
        Item it = new Item(id, name, price, quant);
                      ^
Storefront.java:14: cannot resolve symbol
symbol  : class Item
location: class com.prefect.ecommerce.Storefront
                return (Item)catalog.get(i);
                        ^
4 errors

```

If someone can tell me what is wrong, I would be very grateful. Syntactically I can't find anything wrong. Of course my eyes are bulging out now and I'm tire so I could be wrong.

Thanks in advance!

-Phil McCrackin

---

### Post by yaaarrrgg on 2006-05-30
on interfaces:

interfaces in java are used in place of multiple inhertence in c++.  This avoids some problems (like where a extends b and c, which both extend d).

you might think of interfaces as a contract that says "I promise these function definitions will be defined..."  Then a class can implement mulitple interfaces.  In other words, you are making more promises about the class.  This is useful for example,. since you can treat interfaces somewhat like classes, in that methods can accept an interface as an argument.   Or, you can declare them, and cast a class to an interface.

on your compiling problem:

if you are using packages,  you don't compile in the same directory as the files.  you actually compile at the root level of the packages folders.   for example, i would create create a src and bin directory.  put the com folder in the src.  if you are in the top folder, you should be able to compile with:

```

javac -sourcepath ./src  -d ./bin

```

also, you should be able to run the program with a line like:

```

java -cp ./bin com.prefect.ecommerce.StoreFront

```

or... whatever your main class is.

---

### Post by LordHunter317 on 2006-05-30
[QUOTE=Phil_McCrackin]Some of what has thrown me off (unecessarily) is simply the terminology (ex: a method is a function, etc).[/quote]This is standard OOP terminology. Most of the C++ community uses method over function, or uses them interchangably. 

> I am really befuddled about packages and interfaces. As far as I can tell a package is simply a file to store similar classes.A package is a namespace, which can be nested.  They also happen to determine what directory your source and binary files must go in (absolutely retarded, no need to say it). 

> An interface well...let's just say I have not achieved enlightenment.In C++, a pure virtual class with no implemented methods whatsoever.

---

### Post by Phil_McCrackin on 2006-05-30
Excellent! Thank you both. That makes much more sense now. I was kind of getting the impression that interfaces were the sub for only being able to inherit from one superclass.
> This is standard OOP terminology. Most of the C++ community uses method over function, or uses them interchangably.

Unfortunately, I'm discovering that this is partly my problem. I haven't ever been part of any "community" at all. All I've learned was from college courses and this is the terminology in the text books and what I was tested over. Seems to have it's advantages and disadvantages. I have just not been creative enough (and busy with my 2yo) to come up with any worth while projects to gain any worthy  experience. I'm hoping hanging around here using open source will inspire me :D 

Well, I'm babbling. 
Thanks again!

---

### Post by LordHunter317 on 2006-05-30
[QUOTE=Phil_McCrackin]Excellent! Thank you both. That makes much more sense now. I was kind of getting the impression that interfaces were the sub for only being able to inherit from one superclass.[/quote]They are in part, but they play a natural role in a class hiearchary anyway.  They just are also used as a way to provide MI (C# does this too) in Java.

You'll find in Java (less so in C#) that interfaces are obviously an incomplete solution and you'll have to work around this in other ways: inner classes, anonymous inner class (faux closures, which is also retarded), and very rarely via simply having two distinct classes and using composition.
 
If you do any GUI or SAX/JAXP programming, you'll understand what I'm talking about immediately.  C# lacks these problems due to including delegates and events as native features of the language, instead of implementing them as as classes.  In C#, they are also classes, but they work fundamentally differently.

One note when come from the C++ world that trips many people up: Java "references" are really pointers.  Like pointers, they can be reseated or made to point to another object.  References in C++ are immutable, they can never be made to point to someone else.  

Also, Java only has pass-by-value, just like C.  Passing a pointer is used to simulate pass-by-reference, but if you change what the pointer points to in the caller, the callee is unaffected.  

The rules are somewhat simpler in Java over C since you can only get a pointer to object-types.

And if you don't believe me in any of the above, write some code and test it ;)

---

### Post by tht00 on 2006-05-30
[QUOTE=LordHunter317]This is standard OOP terminology. Most of the C++ community uses method over function, or uses them interchangably.[/QUOTE]

I use 'method' when nothing (or multiple things-- back through the arguements) is/are getting returned.  I use 'function' when one variable is returned.

[QUOTE=LordHunter317]In C++, a pure virtual class with no implemented methods whatsoever.[/QUOTE]

I tend to think of interfaces as classes with only prototypes.

---

### Post by LordHunter317 on 2006-05-30
> **tht00]I use 'method' when nothing (or multiple things-- back through the arguements) is/are getting returned.  I use 'function' when one variable is returned.[/quote]My point is there isn't a formal distinction and many people do not make one said:**
> I tend to think of interfaces as classes with only prototypes.That's perfectly correct, but I mentioned what I did because that's how you implement interfaces in C++.  C++ doesn't have an explict interface keyword.

---

### Post by thumper on 2006-05-30
Just to stick my boot in...

I also use methods and functions interchangably, although talk more about methods for objects functions and functions for vanilla or template functions that are not bound to an instance of an object.

If you are looking for a community, have a look at something like ACCU.

---

### Post by Phil_McCrackin on 2006-05-30
lol WOW! Well, I stirred up the hive about method vs. function. Since the two are synonamous, and what I have learned is not incorrect (at least I hope not since this is what is taught at Okalahoma State for the computer science degree), I will do as I have been where this is concerned (Java/methods, C/C++/functions). Since everyone else uses them interchangably, there should really be no problem with communication.

I truly appreciate the input on the other stuff. Sometimes it just helps to initially think of things as to how they relate to what you know. Like if you learn Chinese, you think of nihaoma as *meaning* "how are you" ...of which one could also say the reverse but we relate to what we know. Looking at an interface as a class with only prototypes does actually help (at least the structure).

I am primarily wanting to learn Java for GUI and graphics related things. It really seems to be a limited language (compared to C++) for anything else. It is more geared to cross-platform and graphics as C++ is more geared to application. Since it is a subset of C++, I thought it would be easy enough to learn on my own and with the exception of a few structural differences, it is.

I will check out the ACCU. I am finding it very helpful to have others input and influence where programming is concerned. We never know it ALL and I truly believe that it is an art. So many ways to achieve the same ends and everyone has their own syle. It is good to learn from one another.

---

### Post by yaaarrrgg on 2006-05-31
[QUOTE=LordHunter317]In C++, a pure virtual class with no implemented methods whatsoever.[/QUOTE]

[QUOTE=tht00]I tend to think of interfaces as classes with only prototypes.[/QUOTE]

That's a good way to understand them, although might also cause some confusion, since Java has abstract classes too (classes with only prototypes).

This link has an overview of some of the similarities and differences between the two:

[http://mindprod.com/jgloss/interfacevsabstract.html](http://mindprod.com/jgloss/interfacevsabstract.html)

---

### Post by LordHunter317 on 2006-06-01
[QUOTE=yaaarrrgg]That's a good way to understand them, although might also cause some confusion, since Java has abstract classes too (classes with only prototypes).[/quote]This is incorrect.  Interfaces have only prototypes.

An abstract class must have at least one prototype, but that is the only rule placed upon it.

Obivously, once can see from these definitions that interfaces are a subset of abstract classes.  This is why C++ doesn't need to distinguish.  Java and C#'s need to distinguish comes from language-enforced limitations on hieharchy, not any special intrinsic properties of interfaces.  As an aside, it's worth noting that many, but not all, of the problems associated with MI still occur in Java and C#.

---

### Post by kunnk on 2006-06-01
Hmm, i dont think interface is subset of abstract class. You can implement in your real class many interfaces, but you can extend only one abstract class. This is why its recommended to "program to an interface, not an implementation", as it makes code more flexible and powerful.

---

### Post by thumper on 2006-06-01
[QUOTE=kunnk]Hmm, i dont think interface is subset of abstract class. You can implement in your real class many interfaces, but you can extend only one abstract class. This is why its recommended to "program to an interface, not an implementation", as it makes code more flexible and powerful.[/QUOTE]
I think that **LordHunter317** is talking about C++ when he says that interface is a subset of abstract class.

This statement I agree with.  Since a C++ interface is normally a class that only has pure virtual methods, then it is a subset of all possible abstract classes.

---

### Post by yaaarrrgg on 2006-06-01
[QUOTE=LordHunter317]This is incorrect.  Interfaces have only prototypes.

An abstract class must have at least one prototype, but that is the only rule placed upon it.

Obivously, once can see from these definitions that interfaces are a subset of abstract classes.  This is why C++ doesn't need to distinguish.  Java and C#'s need to distinguish comes from language-enforced limitations on hieharchy, not any special intrinsic properties of interfaces.  As an aside, it's worth noting that many, but not all, of the problems associated with MI still occur in Java and C#.[/QUOTE]

Yes, that's correct.

What I meant was: In Java you can have abstract classes with only prototypes.  Would these be called "pure" abstract classes?

This is an area of difference between C++ and Java that might cause some confusion to someone switching over.

With the above definitions, it's not clear what the difference is between a "pure" abstract class and an interface.  I would say MI, although of course, interfaces are only a partial solution, and are also useful (perhaps more) for other things.

I agree though, Java artificially imposes some restrictions here, in an attempt to help the programmer.  Does it create as many problems as it solves?  I don't know...

---

### Post by LordHunter317 on 2006-06-01
[QUOTE=thumper]I think that **LordHunter317** is talking about C++ when he says that interface is a subset of abstract class.[/quote]I was speaking in conceptual terms, but it's also applicable to C++.

[quote=yaaarrrgg]What I meant was: In Java you can have abstract classes with only prototypes. Would these be called "pure" abstract classes?[/quote]I suppose so, yes.  One would have to question why you would ever have such a thing in Java though and not use an interface instead.

> With the above definitions, it's not clear what the difference is between a "pure" abstract class and an interface.Conceptually, there isn't.  In Java and C#, the only difference is the role they can play in an inheritance hierarchy.

> agree though, Java artificially imposes some restrictions here, in an attempt to help the programmer. Does it create as many problems as it solves? I don't know...Java?  Probably does.  C#? Probably not.

---

### Post by kunnk on 2006-06-02
[QUOTE=LordHunter317]I was speaking in conceptual terms, but it's also applicable to C++.[/QUOTE]

Statement that interface is subset of abstract class is NOT applicable for java.

---

### Post by LordHunter317 on 2006-06-03
No, it holds *conceptually*.  There is a semantic difference in Java, and I noted that.  I can create any interface as an abstract class.  It's impossible to create an interface that cannot be directly mapped to an abstract class in Java.  That means *conceptually*, interfaces are subsets of abstract classes.

That's important to know even if in Java, there is an important semantic difference (which I also noted, please read more carefully).

---

### Post by Joltzman on 2011-03-19
Hi, I am having the same problem as Phil_McCrakin. I'm reading Teach Yourself Java 6 in 21 days and I'm stuck at week six with Item.class and Storefront.class. I can't compile Storefront.class and I'm getting the identical 4 errors where Item objects are causing errors. The book does a terrible job instructing how to compile these classes when they are part of a package that your created.

I created the root directory as the book instructed, C:\dev\java. I placed the Item.class file in the ecommerce folder (c:\dev\java\org\cadenhead\ecommerce) I had been trying to compile Storefront from the file where I store the programs by book chapter which up until now has worked fine. I read in this forum that you must compile from the root directory but I must be missing something. Please help. I'm stuck.

Here's what happens:
 C:\JavaPrograms\ch6>javac Storefront.java
  Storefront.java:15: cannot find symbol
  symbol  : class Item
  location: class org.cadenhead.ecommerce.Storefront
      public Item getItem(int i) {
             ^
  Storefront.java:11: cannot find symbol
  symbol  : class Item
  location: class org.cadenhead.ecommerce.Storefront
          Item it = new Item(id, name, price, quant);
          ^
  Storefront.java:11: cannot find symbol
  symbol  : class Item
  location: class org.cadenhead.ecommerce.Storefront
          Item it = new Item(id, name, price, quant);
                        ^
  Storefront.java:16: cannot find symbol
  symbol  : class Item
  location: class org.cadenhead.ecommerce.Storefront
          return (Item)catalog.get(i);
                  ^
  Note: Storefront.java uses unchecked or unsafe operations.
  Note: Recompile with -Xlint:unchecked for details.
  4 errors
  
my file structure is C:\dev\java\org\cadenhead\ecommerce

I tried c:\javac -sourcepath ./dev  -d ./java but it didn't work and I do have a classpath variable for this set up. My brain is fried. any help would be appreciated. Thanks.

---

### Post by howefield on 2011-03-19
Please start a fresh thread, referencing this if needs be.

---

