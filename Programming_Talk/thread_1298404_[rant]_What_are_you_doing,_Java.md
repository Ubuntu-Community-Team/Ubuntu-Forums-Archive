---
title: "[rant] What are you doing, Java?"
date: 2009-10-22
forum: Programming Talk
---

### Post by fiddler616 on 2009-10-22
I apologize upfront for the rantishness of this post, but I really want to get this off my chest.

I've been using Java for about a year, and Python for a year and a half. I use Java a lot more often--for my CompSci class. And the following really bugs me:
[LIST]
[*]Exponents: Math.pow(x, 2) is ugly and cumbersome (in fact, for small powers I've taken to just using multiple multiplications).
[*]Compare the following:
```
 linebreak = "-" * 80
```
```
 String linebreak = "";
for(int i = 0; i < 80; i++)
{
    linebreak += "-";
}
```
This comes up more often than you might think, and every time it's infuriating. On a related note, I haven't found an easy way to get a string backwards (like string[::-1] in Python), or every nth character in a string (like string[::n]).

[*] Type casting is still idiosyncratic. Today I had an ArrayList of Integers (not ints--that's not allowed), and I wanted the character whose ASCII value was the integer. I kept getting type errors, and upon asking my teacher for help, she pronounced that she'd have to get back to me (this was after trying several things in my code, and looking up a few things in the API. And don't just say she's a bad teacher--she's really quite good). And wrapper classes seem hackish to me. Especially stuff like Integer.parseString(). Why can't I just cast a string to an int?

[*] Arrays and ArrayLists are very similar data structures, but they weren't written polymorphically (was that phrased right?). array[i] += 3 works, but for ArrayLists it turns into something like arrayList.set(i, arrayList.get(i) + 3) (Disclaimer: I might have switched the order of the arguments).

[*] I still haven't heard a good reason for the necessity of putting "break;" at the end of each case for a switch statement.

[*] Strings have a method called length() that returns the length. Arrays have a field (?) called length instead. Why can't they be the same?

[*] Everything is just *long*. ArrayIndexOutOfBoundsException. System.out.println() (PS-Shouldn't that be print**L**n? Or, if we're really going for stylistic consistency, shouldn't it be the ghastly "printLine"?). Etcetera.

[/LIST]
This is just what came to me off the top of my head, I'm sure there's a bit more. But what I want to know is this: Am I crazy and hyper-sensitive? And: Are there good reasons for all of the above?

Thanks.

---

### Post by Can+~ on 2009-10-22
> **fiddler616 said:**
> I still haven't heard a good reason for the necessity of putting "break;" at the end of each case for a switch statement.

There's a good reason for that. It will try several cases, so you can write code that works for more cases, like:

[PHP]switch (something)
{
    case 1:
    case 2:
    case 3:
    case 4: doSomethingForManyCases... ; break;
}[/PHP]

And this is not just Java, C has it also. Although I still prefer the dictionary-function pointer way in python, oh well...

> Everything is just *long*. ArrayIndexOutOfBoundsException. System.out.println() (PS-Shouldn't that be print**L**n? Or, if we're really going for stylistic consistency, shouldn't it be the ghastly "printLine"?). Etcetera.

Actually, that's my #1 complaint.

---

### Post by fiddler616 on 2009-10-22
> **Can+~ said:**
> [PHP]switch (something)
{
    case 1:
    case 2:
    case 3:
    case 4: doSomethingForManyCases... ; break;
}[/PHP]



I guess that's fair / makes sense. Although I feel like I might rather have
```

case 1 || 2 || 3 || 4: doSomething()

```
Oh! Wait--is the following valid?*
```

case 1: foo();
case 2: 
case 3: bar();
case 4: spam(); break;
case 5: eggs();

```
(If 1, do foo(), bar() and spam(), if 2 or 3, just do bar() and spam(), etc.) If so, then I might see where they're coming from.

*I'm ashamed that I'm asking this, but I don't have Java installed :/

---

### Post by Can+~ on 2009-10-22
> **fiddler616 said:**
> I guess that's fair / makes sense. Although I feel like I might rather have
```

case 1 || 2 || 3 || 4: doSomething()

```
Oh! Wait--is the following valid?*
```

case 1: foo();
case 2: 
case 3: bar();
case 4: spam(); break;
case 5: eggs();

```
(If 1, do foo(), bar() and spam(), if 2 or 3, just do bar() and spam(), etc.) If so, then I might see where they're coming from.

It does.

---

### Post by fiddler616 on 2009-10-22
Thanks.

---

### Post by HotCupOfJava on 2009-10-23
Your frustration is understandable. Python's original designer was looking to create a language that drew upon the many positive aspects of other languages he was familiar with. Even I, a regular Java user, must confess that the result (Python) is a language that is much more intuitive than Java (or anything else) in most cases. 

There are little things that bug me about Python - for instance I don't like the way it does 'for' loops...

But it is a very attractive language - I decided to add it to my arsenal after looking into it. I am of course much more familiar with Java, and for that reason will probably continue to rely upon it more heavily. But I am looking forward to taking advantage of what Python has to offer...

---

### Post by Arndt on 2009-10-23
> **fiddler616 said:**
> 
[*]Compare the following:
```
 linebreak = "-" * 80
```
```
 String linebreak = "";
for(int i = 0; i < 80; i++)
{
    linebreak += "-";
}
```
This comes up more often than you might think, and every time it's infuriating. On a related note, I haven't found an easy way to get a string backwards (like string[::-1] in Python), or every nth character in a string (like string[::n]).



Why not write a function, if it occurs often?

---

### Post by NovaAesa on 2009-10-23
I have to agree on the exponent thing. When I want to use ints rather than doubles, I have my own math class that has a whole heap of static methods that I have written. Exponents can be very efficiently performed with dynamic programming. Simply use the recursive relation:
```

b^p = b^(p/2) * b^(p/2)  if p is even
b^p = b * b^(p-1)        if p is odd
b^p = b                  if p is 1

```

For finding a specific char in a String object, you can use the String method charAt(int index).

For a repeated char, try something like:
```

char[] a = new char[10];
Arrays.fill(a, 'g');
String str = new String(a);

```
I would say that needing a repeated char in real life is pretty unlikely. Same with reversing a string. The only place where I have come accross these sorts of problems is in programming classes when you are being taught about loops and they want to give you a simple problem to solve.

I don't really see what the problem is with casting an int to a char... that works just like any other standard casting between primitive types.

Re: ArrayLists and Arrays, I thing the word you are looking for is orthogonal rather than polymorphic. ArrayLists work exactly the same as many other advanced data structures so are very orthogonal in that sense (because of the use of Interfaces mostly). Arrays are commonly used and such have shortcuts to access and modify elements.

Having long names makes things very readable. With a good IDE there isn't actually much more typing.

Once again, arrays are more minimalistic, hence have a field length rather than a method.

As for the break in the switch statement.. I have to agree there!

I <3 Java =]
(and Python too, but not as much as Java)

---

### Post by CptPicard on 2009-10-23
> **fiddler616 said:**
> 
[*]Exponents: Math.pow(x, 2) is ugly and cumbersome (in fact, for small powers I've taken to just using multiple multiplications).
[*]Compare the following:
```
 linebreak = "-" * 80
```
```
 String linebreak = "";
for(int i = 0; i < 80; i++)
{
    linebreak += "-";
}
```


Well, Java prefers to keep actual syntactic elements rather strictly specified (esp. arithmetic operations are for primitive types) because it doesn't want to start looking like it has anything like operator overloading... which can be confusing syntactic sugar. I wouldn't worry about the use of function there instead of a syntactic sugar-element to replace it; the usage of string * number is on the other hand on the fringe of the level of meaning you want to be able to assign to a base syntactic construct in a language like Java.

Oh, and about the wrapper classes -- they are there because Java makes a strong distinction between primitive values on stack and objects on the heap. You need to have an object reference value, a kind of handle (pointer) on the stack, in order to have the actual object on the heap. In case of primitive types, all you have is the int on the stack; and that is not an object and it does not behave as an object. If you want an object, it's got to be an Integer, in which case it's on the heap, and the reference is on the stack.

> Why can't I just cast a string to an int?

Because a string *is not* an int. IMO you misunderstand the type system if you say that you should be able to "cast" between the two. And again, Java is a bit too low-level in its philosophy to do automagic conversions -- it would require quite a bit of additions into the language to specify, say, python-style converter functions.

> **HotCupOfJava said:**
> 
There are little things that bug me about Python - for instance I don't like the way it does 'for' loops...


Well, the most common case of usage of a for loop is iteration over a sequence, even when it is done by explicitly producing indexes into some collection. Doing anything else than producing either the sequence items, or a sequence of numbers, is fairly rare, so that can be offloaded to some usage of while and explicit manipulation of some variables....

---

### Post by fct on 2009-10-23
> **fiddler616 said:**
> Type casting is still idiosyncratic. Today I had an ArrayList of Integers (not ints--that's not allowed), and I wanted the character whose ASCII value was the integer. I kept getting type errors, and upon asking my teacher for help, she pronounced that she'd have to get back to me (this was after trying several things in my code, and looking up a few things in the API. And don't just say she's a bad teacher--she's really quite good).

What was the problem? Also, Collections like ArrayList hold objects, not types. At the level of the VM distinguishing between an int and a reference to an instance in a Collection seems like a problematic feature to implement, IMO.

> And wrapper classes seem hackish to me. Especially stuff like Integer.parseString(). Why can't I just cast a string to an int?

int is a type, not a class like String. Casting works on type <-> type or class <-> class, doesn't mix other possibilities.

Not sure about this, but I think type casting (i.e.: int to char) throws no Exceptions you can handle. That would also translate to class -> type, unlike the NumberFormatException you'd get with parseInt().

> Arrays and ArrayLists are very similar data structures, but they weren't written polymorphically (was that phrased right?). array[i] += 3 works, but for ArrayLists it turns into something like arrayList.set(i, arrayList.get(i) + 3) (Disclaimer: I might have switched the order of the arguments).



Strings have a method called length() that returns the length. Arrays have a field (?) called length instead. Why can't they be the same?

Arrays and ArrayLists are completely different beasts even if they hold the same purpose.

Arrays are immutable, once you make "int []array = new int[10];" the size won't change for the life of the instance. Any size change implies substitution of the array instance for a new one. 

Hence "length" in arrays is a final (unmodifiable) field set at the constructor which can be accessed carelessly without a function call, also a good choice for optimization. size() in collections like ArrayList accesses a private field in the class that internally changes its value according to functions like "trimSize()".

Thanks to that an array can also have all its contents (or references to contents) held in the VM memory in contiguous positions (which optimizes access times).

Same reasoning flows with "get(i)" versus "[i]". While I can't be 100% sure on this, I'm quite sure Java's "[i]" accessor wasn't implemented to deal with a changing list lengths + capability to hold different types / objects. [x] probably relies on a base position in memory + x increments, which doesn't quite mix well with Collections.

> Everything is just *long*. ArrayIndexOutOfBoundsException. System.out.println() 

I like that, it's quite descriptive. Tells you that you did something like array[i] where i is lesser than 0 or greater than the allocated size.

> 
This is just what came to me off the top of my head, I'm sure there's a bit more. But what I want to know is this: Am I crazy and hyper-sensitive? And: Are there good reasons for all of the above?

Thanks.

You prefer the design of the Python language. On the other hand I like it when the language is restrictive enough to make me think if I'm really doing what I should do at compile time.

But most of your design complaints seem based on technical restrictions of Java, not a premeditated design to make your life harder. ;)

---

### Post by HotCupOfJava on 2009-10-23
> **CptPicard said:**
> 
Well, the most common case of usage of a for loop is iteration over a sequence, even when it is done by explicitly producing indexes into some collection. Doing anything else than producing either the sequence items, or a sequence of numbers, is fairly rare, so that can be offloaded to some usage of while and explicit manipulation of some variables....

You are right, of course - it is one of those situations where I find myself wanting to do things "the Java way" even though the language is NOT Java. 

But that is another reason for becoming familiar with another language - so I can perhaps gain another perspective...

---

### Post by bonefry on 2009-10-23
> **fct said:**
> Also, Collections like ArrayList hold objects, not types. At the level of the VM distinguishing between an int and a reference to an instance in a Collection seems like a problematic feature to implement, IMO.
No, not really. When the compiler (or the JVM) encounters an ArrayList<int> it could simply generate a class where all generic types in ArrayList have been replaced with ints. That's not difficult and it has been done before, but changes in the JVM would've been required, and the JVM bytecode has been practically frozen.

The problem with Java is that the primitives are "special" introduced for performance considerations. You can't define your own class that you could allocate on the stack as in C++ or C#. That's why "int" is not equivalent to an Integer, and that's why the boxing/unboxing rules have gotchas that you have to be aware of (an Integer can be null for one).  Because primitive types are exceptions to the design, having an ArrayList<int> would also be an exception, and it hinders future developments of the language.

Another problem is that generics are functioning through type-erasure, all the information on the generic types not being available at runtime. So introducing special behavior for primitives wasn't consistent.

> **fct said:**
> Arrays and ArrayLists are completely different beasts even if they hold the same purpose.
Holding the same purpose is a real problem. A language should strive to have orthogonal features, otherwise you have to deal with all kinds of crap down the road.

> **fct said:**
> Thanks to that an array can also have all its contents (or references to contents) held in the VM memory in contiguous positions (which optimizes access times).
I don't think this is an issue anymore.

I haven't looked at any source code, but ArrayLists are probably using arrays internally anyway ... and on overflow I would simply create another array and copy the old one, or use both remembering the offsets and do the math.

I don't think this is an issue because the garbage-collector is pretty good at defragmenting memory.

The only valid reason for arrays, and against ArrayList (in regards to performance) is with the required type-casting. If they would've had implemented reified generics, that would have been a non-issue.

> **fct said:**
> You prefer the design of the Python language. On the other hand I like it when the language is restrictive enough to make me think if I'm really doing what I should do at compile time.
I have a different opinion here.

I've worked with a couple of big Java projects, and the code was in general not well thought out and hard to read. The problem with a language that guards against shooting yourself in the foot is that mediocre developers always find creative ways of shooting themselves in the foot anyway, and good developers don't have the tools to do a good job.

And the choices of the language have been rather poor. They banned operator overloading, but they didn't took NULLs out ... which historically have been the source of many more problems than operator overloading. 

They also introduced checked exceptions, but didn't provide some guidelines for using them. And they where a bad idea anyway, because in practice checked-exceptions are actually reducing the code quality. I've seen this in the projects I worked on, you can also see it in popular projects like Apache Tomcat (in many places it has ... catch (Exception e) {}). And checked exceptions have a tendency to break the encapsulation of an object. There are also many people that share this view ... 
[LIST]
[*] [Checked exceptions, I love you but you have to go]("http://googletesting.blogspot.com/2009/09/checked-exceptions-i-love-you-but-you.html")
[*] [Does Java need Checked Exceptions?]("http://www.mindview.net/Etc/Discussions/CheckedExceptions")
[*] [The trouble with checked exceptions]("http://www.artima.com/intv/handcuffs.html")
[/LIST]

Instead of checked exceptions, they could have added contracts (both runtime and compile-time). Those would've been a lot more useful and a lot less intrusive.

In every other profession "concise" is equivalent to readable and probably error-free (math, medicine, physics). You can see this in software as well ... which is the most likely code to have a bug ... 100 lines of Java code, or 30 lines of code written in something else?

You may say that this doesn't happen if you're careful, that you can also write concise Java code, but the language itself is against it, the community is against it, the culture around it is against it.

To see the real difference between Python and Java, try programming in Java without an IDE. Do the same in Python. There's a huge difference right there.

Some people say "well, you wouldn't want Perl instead, would you?". Then you haven't taken a look at how [modern Perl]("http://www.catalystframework.org/") is built.

The problem with Java is that all those long-names, plus the standard ways of doing things in *very* imperative ways (as opposed to declarative) can quickly transform a code-base into a mindfuck game as much as a convoluted Perl one-liner is. And in the case of a Perl one-liner, at least you have fewer chars to read (not having to scroll vertically or looking in 10 dozen class files).

I still like Java though for its performance. I'm actually thinking of creating a new language for the JVM that will be practically Java, with all the cruft removed, and with some nice features added (like closures, reified generics, contracts, operator overloading, mixins, aspects, not having to wrap functions and code inside classes, etc...). I tried Scala, but its design is awkward, inconsistent and some features where added without proper consideration of their impact.

---

### Post by Can+~ on 2009-10-23
> **bonefry said:**
> 
They also introduced checked exceptions, but didn't provide some guidelines for using them. And they where a bad idea anyway, because in practice checked-exceptions are actually reducing the code quality. I've seen this in the projects I worked on, you can also see it in popular projects like Apache Tomcat (in many places it has ... catch (Exception e) {}). And checked exceptions have a tendency to break the encapsulation of an object. There are also many people that share this view ... 
[LIST]
[*] [Checked exceptions, I love you but you have to go]("http://googletesting.blogspot.com/2009/09/checked-exceptions-i-love-you-but-you.html")
[*] [Does Java need Checked Exceptions?]("http://www.mindview.net/Etc/Discussions/CheckedExceptions")
[*] [The trouble with checked exceptions]("http://www.artima.com/intv/handcuffs.html")
[/LIST]

Instead of checked exceptions, they could have added contracts.


YES, YES, Y-E-S, YES. I completely forgot about this one. Having the compiler shout at you saying "you missed an exception here" was nice, the first time. The following 20 times I noticed how useless exceptions had become.

It's pretty much like Vista's UAC, it becomes so annoying, that you just click yes. Here, the compiler exceptions force you to add something, anything, I end up putting a print statement, what other thing to do? If the file is not found during runtime, then tell me that, I can't do jack without said file.

> I still like Java though for its performance. I'm actually thinking of creating a new language for the JVM that will be practically Java, with all the cruft removed, and with some nice features added (like closures, reified generics, contracts, operator overloading, mixins, aspects, not having to wrap functions and code inside classes, etc...). I tried Scala, but its design is awkward, inconsistent and some features where added without proper consideration of their impact.

You could plugin those missing things in Python or Jython (unless you want the statically typed).

---

### Post by fiddler616 on 2009-10-23
Well bonefry pretty much said everything I was thinking except a thousand times more articulately and thoroughly. But to reiterate:
[QUOTE=fct]Arrays and ArrayLists are completely different beasts even if they hold the same purpose.[/QUOTE]
I don't *care* if they're separate beasts--they do almost exactly the same thing, and should be handled in almost exactly the same way. I feel bad that I keep talking about Python, but the relevant example would be lists and tuples: different beasts, but operating them is very similar.

---

