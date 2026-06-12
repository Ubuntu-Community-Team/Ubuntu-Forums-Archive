---
title: "Modular programming"
date: 2012-06-26
forum: Programming Talk
---

### Post by bobman321123 on 2012-06-26
So, in an ideal program, it would be modular. 
That is, each function would be written to perform a single task, and the main function would act as an outline.

Is it possible then, to write a C or C++ module that would get input, and return an int, and have that C++ module referenced by another language?

If I had a program in python which required user input in 'int' form, could I write a C++ module to return an int and have the python program reference it?

Since it returns an int whether it's written in python or C++, I can't see (in theory) what the problem would be with this.

---

### Post by trent.josephsen on 2012-06-26
Yes and no.

Yes, it's possible (and sometimes quite easy) to write a module in C or C++ to bind with Python and provide a feature that isn't easily or most efficiently done in Python (or Perl, or most scripting languages). Some (maybe most?) of the native Python modules do work this way. Basically you write a function that takes a Python object as an argument, unpack the argument to a bunch of natively typed arguments, and return another Python object containing the return value(s). The process is described in Chapter 22 of *Programming Python*, "Extending Python".

But it's not possible, by any method I'm familiar with, to call **any** arbitrary (let's say) C function from Python directly, without the use of wrapper code written in C. This is because Python passes objects quite differently from C, and Python's 'int' is by no means the same thing as C's 'int'.

This might not be the case for all scripting languages; some of them might well use the same [calling convention](http://en.wikipedia.org/wiki/Calling_convention) and datatypes as a compiled C or C++ program. And it seems I may have seen a Perl module that allows direct use of C code and data somewhere. But whether it would be a good idea is another question. By limiting yourself to native datatypes and calling conventions you discard many of the advantages of using a scripting language in the first place.

Nice sig BTW :)

---

### Post by DangerOnTheRanger on 2012-06-26
Python's standard [ctypes]("http://docs.python.org/library/ctypes.html") module lets you call regular C libraries (and other languages that use the C calling convention, I think) from Python without any wrapper code.

---

### Post by bobman321123 on 2012-06-26
> **trent.josephsen said:**
> 
Nice sig BTW :)

Why thank you :D

---

### Post by trent.josephsen on 2012-06-26
> **DangerOnTheRanger said:**
> Python's standard [ctypes]("http://docs.python.org/library/ctypes.html") module lets you call regular C libraries (and other languages that use the C calling convention, I think) from Python without any wrapper code.
Wow, then I was quite mistaken. Never heard of ctypes before. But I guess that's why I added "by any method I'm familiar with"! Thanks for setting me straight.

---

### Post by satsujinka on 2012-06-27
One of the things I'm curious about is whether or not it would be possible to "share" data types between languages if they already share a compiler.

The main problem is call order and type definitions within the language specification. For example, C int and Haskell Int aren't the same.

If we had a set of languages that only defined their higher level syntax (and not their assembly level details such as how types are represented.) It seems to me that we could have a Python-like language call a C-like language as if the C-like language was the Python-like language.
E.G.
```
//file1.c
#include <stdio.h>
void printStuff(char *stuff) { puts(stuff); }
``````
#file2.py
import file1
printStuff("Hello world")
```

---

### Post by Bachstelze on 2012-06-27
> **bobman321123 said:**
> So, in an ideal program, it would be modular. 

You are very good at repeating what you are told in class, congratulations. :)

---

### Post by trent.josephsen on 2012-06-27
> **satsujinka said:**
> One of the things I'm curious about is whether or not it would be possible to "share" data types between languages if they already share a compiler.

The main problem is call order and type definitions within the language specification. For example, C int and Haskell Int aren't the same.

If we had a set of languages that only defined their higher level syntax (and not their assembly level details such as how types are represented.) It seems to me that we could have a Python-like language call a C-like language as if the C-like language was the Python-like language.
E.G.
```
//file1.c
#include <stdio.h>
void printStuff(char *stuff) { puts(stuff); }
``````
#file2.py
import file1
printStuff("Hello world")
```
Something like Java's autoboxing and unboxing between primitive types and wrapper classes. But then you're dealing with implicitly called conversion routines that may or may not do what you want in every instance... for example, Python strings (unlike C strings) may contain ASCII nuls, and IIRC Python's int is actually a long under the hood. Automatic conversion like you describe would violate the principle "Explicit is better than implicit", and doesn't feel pythonic to me. It could work better in certain other languages with less rigid design rules...

---

### Post by Simian Man on 2012-06-27
> **satsujinka said:**
> One of the things I'm curious about is whether or not it would be possible to "share" data types between languages if they already share a compiler.

The main problem is call order and type definitions within the language specification. For example, C int and Haskell Int aren't the same.

If we had a set of languages that only defined their higher level syntax (and not their assembly level details such as how types are represented.) It seems to me that we could have a Python-like language call a C-like language as if the C-like language was the Python-like language.

That's pretty much the idea behind .NET.

---

### Post by DangerOnTheRanger on 2012-06-27
> **satsujinka said:**
> One of the things I'm curious about is whether or not it would be possible to "share" data types between languages if they already share a compiler.

The main problem is call order and type definitions within the language specification. For example, C int and Haskell Int aren't the same.

If we had a set of languages that only defined their higher level syntax (and not their assembly level details such as how types are represented.) It seems to me that we could have a Python-like language call a C-like language as if the C-like language was the Python-like language.
E.G.
```
//file1.c
#include <stdio.h>
void printStuff(char *stuff) { puts(stuff); }
``````
#file2.py
import file1
printStuff("Hello world")
```

The primary problem with this idea is that different languages *represent* datatypes - say, an integer - in different manners. Python represents it as a Python object (an instance of class "int", C represents it as a straight (32-bit) integer, and I believe most other languages use one of these approaches as well. The other problem is that some languages have type declarations that others don't - for example, Python has no equivalent for C's const char *, and C has no equivalent for a Python class.

Now, if you implement multiple languages running on top of the same interpreter/VM (or using the same calling convention, which is how GObject works), you could make them talk to each other with minimal-to-no effort. Jython and IronPython are the two examples that come to my mind of this.

On top of the above two issues, some languages do not have a compiler as such (they have bytecode compilers, but that's completely different), like Python and Lua.

---

### Post by satsujinka on 2012-06-27
@trent
There'd be no need for boxing/unboxing. The types would be implemented exactly the same. Please note, I was using C and Python as example syntax, in truth the code belongs to two entirely different (to be made) languages. Or to be more precise, I imagine the code being two different syntaxes for the exact same language. Thus it isn't so much calling to a different language as it is files formatted differently.
@Danger
See above, they aren't different data types here. The examples were out of familiarity not out of intent.
Similarly, lacking a compiler is of no interest here. I'm thinking about making a compiler that could do this kind of thing.

The real important part of my first post, was simply that I was curious whether or not it would be possible to remove the data type representation definitions from a language, and still have enough information to make a compiler. If there is, then there's no reason why a compiler collection couldn't share representations across languages. This in turn makes the resulting languages better at inter-operating with one another.

The over all goal is this: I want to code in my syntax of choice. I can't necessarily do that at work. If the syntaxes were interchangeable (and transparently inter-operable) then convincing my boss of letting me code my way would be easier.

Of course, a source to source compiler could do the job... but those aren't quite as interesting.

---

### Post by Simian Man on 2012-06-27
> **satsujinka said:**
> Or to be more precise, I imagine the code being two different syntaxes for the exact same language. Thus it isn't so much calling to a different language as it is files formatted differently.

The over all goal is this: I want to code in my syntax of choice. I can't necessarily do that at work. If the syntaxes were interchangeable (and transparently inter-operable) then convincing my boss of letting me code my way would be easier.

Syntax is the least important thing when it comes to different programming languages.  If you take the data types, and operational model of C, and give it the syntax of Python, then you're still basically programming in C.  You wouldn't get any of the benefits that a language like Python actually gives you.

The closest thing to what you want is a set of languages that target the same platform like how all .NET languages can inter-operate by virtue of being compiled to the same virtual machine.  But that's different than what you describe.

---

### Post by satsujinka on 2012-06-27
I disagree, syntax is hugely important for how you use a language. In point of fact I'd argue that the operational model of C would vanish if you used Python syntax. As a sort of example, Java and C share most of their type systems (usage wise) and most of their syntax, however, Java's syntax's emphasis on objects makes the languages feel very different. C is capable of doing OO like Java, but the lack of convenient syntax makes doing so clumsy, despite no real feature difference (garbage collection doesn't make a huge difference, Go feels very much like C to me and it's garbage collected.)

Alternately, what I'm describing is domain specific languages. Housed under a common roof and accessible to one another. So for example, one language might deal with OO, and a non-OO language may access the first's objects as structs with function pointers embedded inside it (that's probably not the best way of doing it, but that's besides the point.)

---

### Post by Simian Man on 2012-06-28
> **satsujinka said:**
> I disagree, syntax is hugely important for how you use a language. In point of fact I'd argue that the operational model of C would vanish if you used Python syntax. As a sort of example, Java and C share most of their type systems (usage wise) and most of their syntax, however, Java's syntax's emphasis on objects makes the languages feel very different. C is capable of doing OO like Java, but the lack of convenient syntax makes doing so clumsy, despite no real feature difference (garbage collection doesn't make a huge difference, Go feels very much like C to me and it's garbage collected.)

Java and C don't share most of their type system - in fact they are very different.  Java does not have unsigned types, stack objects, or pointers.  And C doesn't have access restricted types (private and protected), reference types, real strings, reflection, or even definitions of how big integers are.  They also have very different rules about type conversions.

In fact Java was designed to keep the syntax as close to C as possible while changing the underlying types and operational model.  If anything this proves my point that these things make the language much more than the syntax.

I program in C for my job, and I can assure you that I don't miss the ability to use classes over having to use structs and functions or having to use curly braces instead of whitespace or any other syntactical issues.  What I miss from higher level languages are the abstractions they provide such as garbage collection, genericity, closures, pattern matching, and so on.  I also miss having a higher level type system including real strings, lists and such.

---

### Post by bobman321123 on 2012-06-28
> **Bachstelze said:**
> You are very good at repeating what you are told in class, congratulations. :)

No classes I've ever taken have ever told me that.
My Java teacher told me to throw the whole bunch in one file. 

What I said has been from my experience thus far.

---

### Post by satsujinka on 2012-06-28
> **Simian Man said:**
> Java and C don't share most of their type system - in fact they are very different.  Java does not have unsigned types, stack objects, or pointers.  And C doesn't have access restricted types (private and protected), reference types, real strings, reflection, or even definitions of how big integers are.  They also have very different rules about type conversions.

In fact Java was designed to keep the syntax as close to C as possible while changing the underlying types and operational model.  If anything this proves my point that these things make the language much more than the syntax.

I program in C for my job, and I can assure you that I don't miss the ability to use classes over having to use structs and functions or having to use curly braces instead of whitespace or any other syntactical issues.  What I miss from higher level languages are the abstractions they provide such as garbage collection, genericity, closures, pattern matching, and so on.  I also miss having a higher level type system including real strings, lists and such.

I have a sneaking suspicion that you're focusing far too much on indentation/block creation rules and not on the full scope of syntax.

I gave a perfect example of the power of syntax. Java adds class syntax (based off struct syntax) to C's syntax and as a result feels totally different. Sure, Java lacks pointers (GC+ references make up for this though) and C lacks restricted types (why you'd want them, I don't know) ... etc. but these are all minor details in the type system. An int in Java is identical in usage to C's, same with char, etc. It isn't even a remote stretch of the mind to come up with a code segment that is valid in both languages and does the same thing.

That said, I don't care about classes. The above is not an improvement for me. It was merely an example of how radically a language can change in model simply by expanding syntax.

Your argument from authority is also uninteresting. I'm also a programmer by trade. I use Java at work, but would prefer C (I do plenty of C development in my own time.) I like C. The things you complain about it lacking are utterly trivial to me. Char arrays work fine, manual memory management is simple, generics are only marginally useful (coming from someone who loves Haskell...,) lists are easily created (syntax!!! would be nice though,) I've never used closures in languages that have them, etc.

All of my complaints about C are syntactical. I want list syntax. I want simpler parsing rules (like Go's left-right rules.) I would like the standard libraries to be cleaned of the cruft they've developed over the years (gets().) Syntax is the biggest enabler of features. However, you can't just throw all the syntax in one language (that's a mess just look at C++.) Which is why I'd like to create a system of languages that group relevant syntaxes together (each one good at something) and allow them easy access to one another (though you will have to learn what is equivalent to what.)

---

### Post by Simian Man on 2012-06-28
> **satsujinka said:**
> I have a sneaking suspicion that you're focusing far too much on indentation/block creation rules and not on the full scope of syntax.
Nope, I just gave that as an example, I know what syntax means.

> **satsujinka said:**
> I gave a perfect example of the power of syntax. Java adds class syntax (based off struct syntax) to C's syntax and as a result feels totally different. Sure, Java lacks pointers (GC+ references make up for this though) and C lacks restricted types (why you'd want them, I don't know) ... etc. but these are all minor details in the type system. An int in Java is identical in usage to C's, same with char, etc. It isn't even a remote stretch of the mind to come up with a code segment that is valid in both languages and does the same thing.

That said, I don't care about classes. The above is not an improvement for me. It was merely an example of how radically a language can change in model simply by expanding syntax.

Let's look at some code:
```

// C:
typedef struct {
  char name[NAME_SIZE];
  int age;
  Person* owner;
} Dog;

void walk(Dog* dog) {
}

// Java:
public class Dog {
  private String name;
  private int age;
  private Person owner;

  public void walk( ) {
  }
}

```

Here the major difference between these two pieces of code is NOT that one uses a struct and a function, while the other uses a class and a method.  That is the syntax, and it doesn't really matter.  Much more important are the semantic differences.  In the C code we use an array of characters to represent the name, we don't know how many bits are given to the age field, we use a pointer to represent the dog's owner (which may be NULL), and the data members of the struct are of course open to be changed by any piece of code - all of which are different in the Java code.  Those are the important differences.  Syntax changes alone don't "radically" change the nature of a programming language.

> **satsujinka said:**
> Your argument from authority is also uninteresting. I'm also a programmer by trade. I use Java at work, but would prefer C (I do plenty of C development in my own time.) I like C. The things you complain about it lacking are utterly trivial to me. Char arrays work fine, manual memory management is simple, generics are only marginally useful (coming from someone who loves Haskell...,) lists are easily created (syntax!!! would be nice though,) I've never used closures in languages that have them, etc.

It wasn't an argument from authority, I was just telling you what I miss being primarily a C programmer.  If you think the difference between a class and a struct is a big issue, but don't see much difference between manual and automatic memory management, or don't see the value of generic programming...well I don't know what to tell you :).  By the way, how can you love Haskell, but never have used a closure?  You either don't understand what a closure is, or you haven't really used Haskell too much.

---

### Post by satsujinka on 2012-06-28
We may have to agree to disagree on the importance of syntax, but here's one last try to convince you:
> **Simian Man said:**
> Nope, I just gave that as an example, I know what syntax means.
Let's look at some code:
```

// C:
typedef struct {
  char name[NAME_SIZE];
  int age;
  Person* owner;
} Dog;

void walk(Dog* dog) {
}

// Java:
public class Dog {
  private String name;
  private int age;
  private Person owner;

  public void walk( ) {
  }
}

```

Here the major difference between these two pieces of code is NOT that one uses a struct and a function, while the other uses a class and a method.  That is the syntax, and it doesn't really matter.  Much more important are the semantic differences.  In the C code we use an array of characters to represent the name, we don't know how many bits are given to the age field, we use a pointer to represent the dog's owner (which may be NULL), and the data members of the struct are of course open to be changed by any piece of code - all of which are different in the Java code.  Those are the important differences.  Syntax changes alone don't "radically" change the nature of a programming language.

Yet all of the differences are mere syntax differences. The Person owner in Java can also be null (no semantic difference there.) You could have used a char array to represent the name of the dog (instead you used syntactic sugar for a char vector.) I will agree that the semantics of the object are different from those of the struct (due to the whole public/private thing.) So you got 1 right. Everything else is just a syntactic difference.

> **Simian Man said:**
> 
It wasn't an argument from authority, I was just telling you what I miss being primarily a C programmer.  If you think the difference between a class and a struct is a big issue, but don't see much difference between manual and automatic memory management, or don't see the value of generic programming...well I don't know what to tell you :).  By the way, how can you love Haskell, but never have used a closure?  You either don't understand what a closure is, or you haven't really used Haskell too much.
Sorry for taking it as such. However, "I do x for a living" is a common argument from authority.
I should probably point out that I haven't said classes are hugely different from structs. Inheritance is a part of "class syntax". Having such syntax changes the way people program, they start forming inheritance trees. You could form them in C, however, it's annoying so people generally don't.

Closures are just one way of passing information. It's, however,
not a feature I ever needed to use (I've thought about using them, but they don't really add anything.) At the end of the day a closure is just sugar for a function call with a pointer to the currently available variables.

Generics are useful, if you really need type-safety (like if you're making a collection.) Otherwise, no. Contract/interface/typeclass based coding fulfills the same role and does it better (and is easier to implement.)

To top my argument off, nearly every feature we've been talking about is syntactic sugar. 
Closures -> functions -> lambdas (in functional languages)
Classes -> structs and functions
Generics -> name mangled functions/data types (C++ style templates do this)
Strings -> char arrays/vectors/lists
Pattern matching -> comparisons

Basically, the only feature discussed that isn't sugar is garbage collection.

---

### Post by Barrucadu on 2012-06-29
> **satsujinka said:**
> Yet all of the differences are mere syntax differences. The Person owner in Java can also be null (no semantic difference there.) You could have used a char array to represent the name of the dog (instead you used syntactic sugar for a char vector.) I will agree that the semantics of the object are different from those of the struct (due to the whole public/private thing.) So you got 1 right. Everything else is just a syntactic difference.

In addition, the C string has a maximum length whereas the Java string does not; the values of the C types are all undefined whereas they have defined defaults in Java; and the C owner is a pointer whereas the Java owner is a reference.

The two snippets of code don't just look different, they have different meanings.

---

### Post by satsujinka on 2012-06-29
> **Barrucadu said:**
> In addition, the C string has a maximum length whereas the Java string does not; the values of the C types are all undefined whereas they have defined defaults in Java; and the C owner is a pointer whereas the Java owner is a reference.

The two snippets of code don't just look different, they have different meanings.

Java char arrays have length limits too, what's your point?

As I said, Java String is a vector not an array. You could make a C char vector that would work exactly like Java String (save for some minor syntax issues with it not being a built-in.)

Defined defaults don't change the meaning of an int. It's syntactic sugar. Define a rule "int i;" -> "int i = 0;", there you go, built in default.

References are nearly identical to pointers. They really only lack arithmetic. However, just like a pointer, references can be valid or null.

The two code segments are only not identical semantically, because they were created unequal. Either replace "char *" with an implementation of "String" or vice versa. Make function pointers embeded in Dog (struct) that point to walk and implementations of every method of Java's Object. Create a constructor function for the dog struct (Java uses one for its objects,) here setup the function pointers and initialize the members of Dog. (default values, yay!) Now, "Dog dog = new_Dog();" could be equivalent to "Dog dog = new Dog()" and the two dogs would have the same semantic meaning.

If anything, this only reinforces my point. Java's syntax makes the above process easier. It's more work in C (which is why it's done less often and why you didn't realize that the code wasn't even trying to do the same thing.)

tl;dr. If two things aren't semantically the same, then you're talking about different things. Stop. Figure out what would be equivalent and then you'll find out how important syntax is.

---

### Post by trent.josephsen on 2012-06-29
Let's take a more concrete example.

C:
```
#include <stdio.h>
#include <stdlib.h>

typedef struct _dog {
    void (*speak)(void);
} *Dog;

typedef struct _chihuahua {
    struct _dog parent;
    void (*speak)(void);
} *Chihuahua;

/* Member methods */
void Dog_speak(void) { puts("Woof, woof"); }

void Chihuahua_speak(void) { puts("Yip, yip"); }

/* Constructors */
Dog new_Dog(void) {
	struct _dog *p = malloc(sizeof *p);
	p->speak = Dog_speak;
	return p;
}

Chihuahua new_Chihuahua(void) {
	struct _chihuahua *p = malloc(sizeof *p);
	struct _dog parent = { Dog_speak };
	p->parent = parent;
	p->speak = Chihuahua_speak;
	return p;
}

/* Main routine */
int main(void)
{
	Dog fifi = (Dog)new_Chihuahua();
	fifi->speak();
}
```

Java:
```
class Dog {
	void speak(void) { System.out.println("Woof, woof"); }
}

class Chihuahua extends Dog {
	void speak(void) { System.out.println("Yip, yip"); }
}

class MainProgram {
	public static void main(String[] args) {
		Dog d = new Chihuahua();
		d.speak();
	}
}
```

Semantically different enough for you?

Java's type system is **orders of magnitude more complex and nuanced** than anything C has to offer. I'm giving a simple, obvious example. The idea that Java shares C's type system is ludicrous; the notion that Java is OOP-focused *because of* its syntax, doubly so.

---

### Post by Simian Man on 2012-06-30
> **satsujinka said:**
> Closures are just one way of passing information. It's, however,
not a feature I ever needed to use (I've thought about using them, but they don't really add anything.) At the end of the day a closure is just sugar for a function call with a pointer to the currently available variables.
A closure is not just syntactic sugar.  In C, local variables die when you return from the function, so even if you pass a pointer to them, you won't be able to reference them safely.

> **satsujinka said:**
> Generics are useful, if you really need type-safety (like if you're making a collection.) Otherwise, no. Contract/interface/typeclass based coding fulfills the same role and does it better (and is easier to implement.)
I disagree here, generics are incredibly useful.  I can't believe you would consider type safety to be superfluous.

> **satsujinka said:**
> To top my argument off, nearly every feature we've been talking about is syntactic sugar. 
Closures -> functions -> lambdas (in functional languages)
Classes -> structs and functions
Generics -> name mangled functions/data types (C++ style templates do this)
Strings -> char arrays/vectors/lists
Pattern matching -> comparisons
I've already explained that closures are not just syntactic sugar.  Classes are not syntactic sugar either as you can't emulate access modifiers with syntax.  Generics are definitely not just name mangled functions.  Write a version of the C++ std::sort in C that provides transparent, static type safety if you don't believe me.  Powerful pattern matching systems also can't be reduced to comparisons with mere syntax.

It seems to me that when you learn a new language, you just learn to use it the way you use other languages, so the only things that stand out to you are the syntactical differences.  For example, you see Java classes and think that the only difference between them and C structs + function pointers is syntax.  You learn Haskell but apparently don't see the value in its powerful generic type system or closures which are a fundamental element in functional programming.

---

### Post by satsujinka on 2012-06-30
> **trent.josephsen said:**
> Let's take a more concrete example.

C:
```
#include <stdio.h>
#include <stdlib.h>

typedef struct _dog {
    void (*speak)(void);
} *Dog;

typedef struct _chihuahua {
    struct _dog parent;
    void (*speak)(void);
} *Chihuahua;

/* Member methods */
void Dog_speak(void) { puts("Woof, woof"); }

void Chihuahua_speak(void) { puts("Yip, yip"); }

/* Constructors */
Dog new_Dog(void) {
	struct _dog *p = malloc(sizeof *p);
	p->speak = Dog_speak;
	return p;
}

Chihuahua new_Chihuahua(void) {
	struct _chihuahua *p = malloc(sizeof *p);
	struct _dog parent = { Dog_speak };
	p->parent = parent;
	p->speak = Chihuahua_speak;
	return p;
}

/* Main routine */
int main(void)
{
	Dog fifi = (Dog)new_Chihuahua();
	fifi->speak();
}
```

Java:
```
class Dog {
	void speak(void) { System.out.println("Woof, woof"); }
}

class Chihuahua extends Dog {
	void speak(void) { System.out.println("Yip, yip"); }
}

class MainProgram {
	public static void main(String[] args) {
		Dog d = new Chihuahua();
		d.speak();
	}
}
```

Semantically different enough for you?

Java's type system is **orders of magnitude more complex and nuanced** than anything C has to offer. I'm giving a simple, obvious example. The idea that Java shares C's type system is ludicrous; the notion that Java is OOP-focused *because of* its syntax, doubly so.

You seem to have the wrong definition of semantics... because those two 
segments are semantically the same. They may not be implemented the same way (I don't know how exactly Java represents objects,) but the do the same things using the same concept (inheritance, construction, and member access.)
Java's syntax was designed for being OO-focused. Not the other way around. However, the addition of OO syntax makes it much easier to use then the C version (notice the code size difference above.)

@Simian
Closures are not about local scope. Closures are about the surrounding scope. A pointer to something in a closure will die when the closure finishes, just as it would in any other function. The benefit of a closure is that you can capture the surrounding scope and not have to pass a pointer into your function (because the variable is included in the closure's scope.)

Type-safety is of little concern 90% of the time, because you're probably using a concrete type already. Collections are one of the major benefactees of generics. There are others, but they're mostly corner cases (like if you want to extend several types all at once.)

C++ templates are used to generate name mangled functions (the compiler then selects the correct name-mangled function to call.) There's really no two ways about it. This is what C++ does. Haskell doesn't do this. Haskell borrows the untyped type system of C-- (which it compiles to,) this makes Haskell's types a mere formality (so there's no need to cast or name mangle.)

Access modifiers are a compiler enforced convention. I already explained that. Yes, you cannot emulate it... because there is no code difference between a public and private variable. The compiler merely enforces access rules (because it's entirely spottable at compile time.)

I think it's funny that you accuse me of not adapting my mental model of computation to the language after having accused me of finding classes to be the bee's knees. It's really quite simple, I like to think about how an abstraction (such as classes, generics, or closures) could be implemented. For example, classes are an abstraction based on structs. Every language (save maybe Java) converted classes to structs at some point in its development. Thus it is a simple fact that class syntax can be mapped to struct syntax (though it'll take a lot more code in struct syntax.) This is the very definition of syntactic sugar.

---

### Post by trent.josephsen on 2012-06-30
@satsujinka: You missed the entire point of my post. Run them.

---

### Post by gardnan on 2012-06-30
> **trent.josephsen said:**
> 

C:
```
#include <stdio.h>
#include <stdlib.h>

typedef struct _dog {
    void (*speak)(void);
} *Dog;

typedef struct _chihuahua {
    struct _dog parent;
    void (*speak)(void);
} *Chihuahua;

/* Member methods */
void Dog_speak(void) { puts("Woof, woof"); }

void Chihuahua_speak(void) { puts("Yip, yip"); }

/* Constructors */
Dog new_Dog(void) {
	struct _dog *p = malloc(sizeof *p);
	p->speak = Dog_speak;
	return p;
}

Chihuahua new_Chihuahua(void) {
	struct _chihuahua *p = malloc(sizeof *p);
	struct _dog parent = { Dog_speak };
	p->parent = parent;
	p->speak = Chihuahua_speak;
	return p;
}

/* Main routine */
int main(void)
{
	Dog fifi = (Dog)new_Chihuahua();
	fifi->speak();
}
```



I am not sure exactly, but I think this example is trying to show that C can't behave polymorphically, (i.e prints "Woof woof" rather than "Yip yip"). However, to get "Yip yip" instead, all you have to do is switch the 'parent' and 'speak' definitions in the C structure. This is not to disprove your point, but I think that a better example of C's shortcomings is data inheritance/extension. I have had some hairy situations with that myself.

---

### Post by CptPicard on 2012-06-30
Hey, cool, a some kind of variant of the high vs. low level languages thread! The eternal point of contention here...

To get arguments-from-authority out of the way, yes, I am also a professional programmer but I am a professional programmer as a side-effect of my interest in programming languages and algorithmics, not the other way around...

> **satsujinka said:**
> I disagree, syntax is hugely important for how you use a language.

Syntax is superficial; it's just the outwardly visible notation of what the language "means" -- a ruleset of how to label those things. I get this impression that you actually give syntax a bit broader an interpretation that crosses into the domain of semantics and therefore say that it's *syntax* that changes how you use a language, and not the underlying meaning of the constructs that have been selected for that language, which would be my position on the matter.

> 
 In point of fact I'd argue that the operational model of C would vanish if you used Python syntax.

Do you mean implementing also the things that would be Python instead of C? And how would you handle something like explicit pointer type semantics when those things just fundamentally are not there in Python, regardless of the fact that Python also obviously lacks syntax for them then?

> 
 As a sort of example, Java and C share most of their type systems (usage wise) and most of their syntax, however, Java's syntax's emphasis on objects makes the languages feel very different.

I'm not sure I can share the sentiment... Java is a strongly-typed language where the idea of the type hierarchy is very explicit, and there's internal functionality to dispatch function calls according to the implicit "this parameter"... the idea of function call ownership is an idea onto its own, not just some artifact of syntax.

Of course Java needs to outwardly *represent* the classes with something and have syntactic tools to describe these ideas.

> **satsujinka said:**
> 
I gave a perfect example of the power of syntax.

I'd go as far as say that syntax alone has no power at all -- it alone doesn't "do" anything :p

> 
 Java adds class syntax (based off struct syntax) to C's syntax and as a result feels totally different.

It feels different because it behaves different and stresses certain things in its design. It's not just the syntax, it is what single-inheritance OOP means and how it affects your thinking about the issues you're working on.

> manual memory management is simple

Maybe simple in idea, tedious, boring and error-prone in real life and larger projects. Hence as it is a computer-solvable problem, it's been solved by computer.

I can sort-of appreciate your argument though that GC is such a major underlying language feature that it's difficult to come up with analogues in other languages apart from actually writing a garbage collector.

> 
, generics are only marginally useful

Depends. If you want a static-typed language with an efficient compiler, having bounds on the type of the items in your collection can be handy. Note that this is not a statement on Java, its generics are mostly just painful...

> 
 (coming from someone who loves Haskell...,) lists are easily created (syntax!!! would be nice though,)

Wouldn't that be the very definition of utterly trivial syntactic sugar though that has no real impact on the kinds of programs you'd construct?

>  I've never used closures in languages that have them, etc.

As Simian Man said, this is very unlikely, especially if you "love" Haskell (that is, you actually do anything non-trivial with it). Generally speaking, closures tend to be quite central to the design philosophy to any language that does have them, so not having made use of them sounds rather weird.

> 
All of my complaints about C are syntactical. I want list syntax. 

No, you want also the actual lists, and just to throw something off the top of my hat, some kind of ability to manage the relevant memory as well, perhaps.

> Syntax is the biggest enabler of features.

Syntax merely gives a notation to features. You can have outright arbitrary syntax, you have more parseable classes of syntax. Formulating a certain syntax doesn't enable anything, it just describes things. We need nvteighen our resident linguist here to clarify this for you :)

> However, you can't just throw all the syntax in one language (that's a mess just look at C++.)

Why it is a mess is that all the underlying stuff just conflicts, as well. Not just their representations.

> Which is why I'd like to create a system of languages that group relevant syntaxes together (each one good at something) and allow them easy access to one another

Again, I get the feeling that your sense of "syntax" is broader than mine. Check out Lisp; it's a general abstract-syntax-tree language with all the fundamentally necessary things, and everything else "syntactically" built on top of that minimal core.

> 
Yet all of the differences are mere syntax differences.

I find this is the core of your argument and of many "it's just syntactic sugar"-arguments -- and the way to counter it is to state that all of our programming languages worthy of the name are Turing-complete to begin with. You can always implement one in terms of the other, so you can call anything "syntactic sugar" on top of some random host language if you want to. If this is the case, the argument is irrelevant and uninteresting, and we can stop.

However, all the programming language design issues that are of interest really deal with what we do to make the language behave more humanly understandable than a string of ones and zeroes... and of course, we have to implement the functionality somehow. 

> 
Closures are just one way of passing information.

Closures are a remarkably theoretically fundamentally important idea. If you start designing a language from predicate logic on, you run into the closure of a clause pretty early on. You can derive a lot of interesting other stuff from them; for example, object-oriented-programming (you can encapsulate the member variables into the closure).

Sometimes I get the feeling that there are just two completely separate mindsets in programmers and it's almost impossible to bridge the gap -- there are ones who look at things in terms of the executing hardware, and those who look at what abstractly "is" and the executing environment is an afterthought. If in any sense competent, both seem to understand how things work in terms of the other's mindset, but the core "self" of the person as a programmer is tied to one or the other...

> At the end of the day a closure is just sugar for a function call with a pointer to the currently available variables.

May I commend you for actually understanding closures on this level? Most people who critique them don't understand how they'd go about implementing something akin to them in C.

Of course, if a language just "knows" what the available context is, and is capable of managing the whole runtime scope of those values (which requires GC), it's a rather strong service offered compared to having to actually implement something like closures on a case by case basis.

Then there of course are really interesting things like continuations that you can do with closures and tail-call optimizations that would be rather difficult to do in C... but of course, as I said, as per Turing-completeness, you of course always fundamentally *can*. That is not the issue here.

---

### Post by trent.josephsen on 2012-06-30
> **gardnan said:**
> I am not sure exactly, but I think this example is trying to show that C can't behave polymorphically, (i.e prints "Woof woof" rather than "Yip yip"). However, to get "Yip yip" instead, all you have to do is switch the 'parent' and 'speak' definitions in the C structure. This is not to disprove your point, but I think that a better example of C's shortcomings is data inheritance/extension. I have had some hairy situations with that myself.
You are correct about the object of my example, but your suggested solution misses the point. Reordering the struct members to get a different output is still not polymorphic, and fails for more complicated structures. In fact, the example would have undefined behavior if the `parent` and `speak` members were switched, because a pointer-to-struct-_chihuahua can't be safely converted to a pointer-to-struct-_dog unless the struct _dog member is the first element in the struct.

---

### Post by satsujinka on 2012-06-30
@CptPicard
I lost the post I was composing, but I'll try to capture it again.

Syntax may be superficial, but people are too. We use syntax to represent concepts, if a concept is useful to us we'd prefer to have a simple representation for it. My example (that seems to have backfired on me) was that using objects and inheritance in Java is much easier than C. I claim this is due to Java having extra syntax rather than C lacking features (glib does just fine, it's just full of boilerplate code.)

I've studied Scheme, is that acceptable instead of Lisp? :)

I mentioned elsewhere that generics are hugely useful for creating collections.

Unless Haskell uses closures behind my back I haven't used them. Generally, the way I design programs tend not to need to pass in huge numbers of arguments (one use case of closures.) Similarly, I'm not overly fond of continuations.

I seem to use "syntactic sugar" differently than expected, because I was using it to denote a simplified syntax for a concept (existing is considered simplifying.)

@all
To make it really clear here's my logic:
We use concepts to design programs.
We represent these concepts with syntax.
We prefer easier things to harder things.
A concept is easy to use if its syntax is easy to use.
Therefore, we will prefer using concepts whose syntax is easy to use.
Similarly, we will prefer a language that has concepts we like and they are easy to use.

Thus, syntax is a major consideration for any language.

There are, of course, other considerations. Such as type system.

---

### Post by schauerlich on 2012-06-30
> **satsujinka said:**
> Unless Haskell uses closures behind my back I haven't used them. Generally, the way I design programs tend not to need to pass in huge numbers of arguments (one use case of closures.) Similarly, I'm not overly fond of continuations.

Haskell is constantly using closures. Every time you make a function call you are using closures. Using Haskell and not understanding that you're using closures everywhere is really missing the point in a fundamental way.


> 
@all
To make it really clear here's my logic:
We use concepts to design programs.
We represent these concepts with syntax.
We prefer easier things to harder things.
A concept is easy to use if its syntax is easy to use.
Therefore, we will prefer using concepts whose syntax is easy to use.
Similarly, we will prefer a language that has concepts we like and they are easy to use.

Thus, syntax is a major consideration for any language.

And what others are trying to say is that syntax is really a secondary consideration. The design of the language and the features it supports are much more important in how you write programs and model problems in that language. Syntax is just a way to formalize those ideas. You are saying that Java provides convenient syntax for OOP, and thus people write OO programs in it. You could write OO in C, but it's a pain, so you don't.

What we are saying is that Java, by design, is an OO language. It is pervasive in the design of the language. It is inescapable. C, on the other hand, does not support OOP natively. You can simulate it, but ideas like inheritance and polymorphism are simply *missing* from the language design. Note that I have not mentioned syntax yet. You could just as easily have replaced Java's syntax with something completely different, and still maintain the semantics of the language. I could rewrite a language that is functionally and semantically equivalent to Java with a Lisp-like syntax, and nothing would change.

That is not to say that syntax and semantics are completely divorced. Of course, to be practical, a language will provide convenient syntax for the kinds of things the language designers had in mind when writing the language. This naturally overlaps with the semantics. And yes, when you implement features, you must provide some way to access them via the syntax of the language. But it is a matter of causality: syntax presupposes semantics, not vice versa.

---

### Post by satsujinka on 2012-07-01
> **schauerlich said:**
> Haskell is constantly using closures. Every time you make a function call you are using closures. Using Haskell and not understanding that you're using closures everywhere is really missing the point in a fundamental way.

In which case Haskell is using them behind my back. This is not the same as me using closures. Nor is it missing the point. It's a minor implementation detail of no consequence to the user.

Further, it's entirely possible that GHC is optimizing away any closures. Meaning I truly might not be using them... the behavior is unchanged either way, so I repeat Haskell using closures behind my back is not an important detail.

That said, I probably could have guessed that the implementation was closures, considering I knew Haskell used currying to generate functions (Haskell is named after the guy who invented currying after all.)

> **schauerlich said:**
> 
And what others are trying to say is that syntax is really a secondary consideration. The design of the language and the features it supports are much more important in how you write programs and model problems in that language. Syntax is just a way to formalize those ideas. You are saying that Java provides convenient syntax for OOP, and thus people write OO programs in it. You could write OO in C, but it's a pain, so you don't.

What we are saying is that Java, by design, is an OO language. It is pervasive in the design of the language. It is inescapable. C, on the other hand, does not support OOP natively. You can simulate it, but ideas like inheritance and polymorphism are simply *missing* from the language design. Note that I have not mentioned syntax yet. You could just as easily have replaced Java's syntax with something completely different, and still maintain the semantics of the language. I could rewrite a language that is functionally and semantically equivalent to Java with a Lisp-like syntax, and nothing would change.

That is not to say that syntax and semantics are completely divorced. Of course, to be practical, a language will provide convenient syntax for the kinds of things the language designers had in mind when writing the language. This naturally overlaps with the semantics. And yes, when you implement features, you must provide some way to access them via the syntax of the language. But it is a matter of causality: syntax presupposes semantics, not vice versa.
The problem is that "the design of a language" includes its syntax. The features a language supports is defined by it having a syntax for the feature. Languages are syntactic entities, you cannot talk about a language and not be talking about syntax.

So long as a language supports your concepts of choice, you're right syntax will be a secondary consideration. However, consider this: If you want to use inheritance and/or polymorphism are you more likely to choose Java or C?

I think the answer is fairly obvious. Further, it shows that languages don't necessarily support the same features. Thus it is (still) important to you what the syntax is like (remember having a feature is equivalent to having a syntax.)

Which brings me back to my original suggestion (I'll rehash it to use verbiage that you're more comfortable with.) Wouldn't it be nice to have a set of languages that can easily talk to one another and provide a wide/complete coverage of features? A set of languages that would make your choice of features unimportant to the project as a whole? So you can use OO (for example,) I can use functional, and someone else can use logical programming; without any impedance mismatch between them.

tl;dr. Linguistics 101: semantics is built upon syntax. In languages, it actually is the case that semantics presuppose syntax.

---

### Post by trent.josephsen on 2012-07-01
> **satsujinka said:**
> However, consider this: If you want to use inheritance and/or polymorphism are you more likely to choose Java or C?
If you want to use polymorphism, you're *forced* to use Java because *C doesn't support it*. Sure, you could write an abstraction layer in C that achieved something like polymorphism -- but at that point you're no longer using a **language feature**, regardless of the **syntax** you choose.

---

### Post by schauerlich on 2012-07-01
> **satsujinka said:**
> Further, it's entirely possible that GHC is optimizing away any closures. Meaning I truly might not be using them... the behavior is unchanged either way, so I repeat Haskell using closures behind my back is not an important detail.

Pervasive currying is not an unimportant implementation detail. It is a fundamental piece of design philosophy for the language. You may not use lambdas explicitly (eg, \x -> x + x), but that is only because Haskell provides many convenient ways to avoid it. Note, though, that most of these aren't built into the language - the foundations of currying and closures make the language powerful enough to implement them in Haskell directly. If you do something non-trivial in Haskell, you will without a doubt use closures frequently, even without including currying.


> 
The problem is that "the design of a language" includes its syntax. The features a language supports is defined by it having a syntax for the feature. Languages are syntactic entities, you cannot talk about a language and not be talking about syntax.

Again, you are reversing the causality. When someone is designing a language, they think "hmm...  I want the language to do *this*. What's a convenient syntax for *this*?" They do not say "This syntax looks kind of cool, I wonder what it should do..." The features a language supports are defined by the language implementers writing code to perform those tasks. Have you written an interpreter before? There are (at least) two phases to most interpreters: parsing, and execution. Parsing is the ONLY stage in which syntax matters whatsoever. A parser breaks up the stream of text from the file into an abstract representation of the program which is syntax-independent (called the abstract syntax tree, AST). It expresses relationships between computational entities. I could take this AST and emit a completely different language syntax-wise that preserved the semantics. It is this AST that gets fed into the execution engine of the interpreter, *where the features of language are defined and executed*. Not in the parser, but the execution engine, which is independent of syntax.

> 
So long as a language supports your concepts of choice, you're right syntax will be a secondary consideration. However, consider this: If you want to use inheritance and/or polymorphism are you more likely to choose Java or C?

C simply does not support inheritance or polymorphism. Java could support these things with completely different syntax. I don't see how this supports your point. Yes, C does not provide syntax for features it does not support. But it doesn't fail to provide support for these features *because* it lacks the syntax for them; rather, it lacks syntax for them because it does not support those features.

> Thus it is (still) important to you what the syntax is like (remember having a feature is equivalent to having a syntax.)

No. That is simply an incorrect statement. Having syntax is the result of having a feature. One is a consequence of another. They are not equivalent.

Consider lisp: when it comes down to it (and you ignore reader macros), there's really only about 4-5 grammar rules: you have an sexpression, which is either an atom or a list; and lists, which can contain any number of atoms and lists recursively. That is the only syntax that exists in the language. The rest of the language is implemented in terms of special forms, which for the most part could even be implemented in the language itself. There are only a few fundamental forms (lambda being one of them), but these are not encoded in the syntax; they are purely semantic entities.

> 
Which brings me back to my original suggestion (I'll rehash it to use verbiage that you're more comfortable with.) Wouldn't it be nice to have a set of languages that can easily talk to one another and provide a wide/complete coverage of features? A set of languages that would make your choice of features unimportant to the project as a whole? So you can use OO (for example,) I can use functional, and someone else can use logical programming; without any impedance mismatch between them.

Yes, it's called the JVM/.NET.

> 
tl;dr. Linguistics 101: semantics is built upon syntax. In languages, it actually is the case that semantics presuppose syntax.

You picked the wrong programmer to talk about linguistics with. :)

---

### Post by satsujinka on 2012-07-01
> **schauerlich said:**
> Pervasive currying is not an unimportant implementation detail. It is a fundamental piece of design philosophy for the language. You may not use lambdas explicitly (eg, \x -> x + x), but that is only because Haskell provides many convenient ways to avoid it. Note, though, that most of these aren't built into the language - the foundations of currying and closures make the language powerful enough to implement them in Haskell directly. If you do something non-trivial in Haskell, you will without a doubt use closures frequently, even without including currying.

As I said before, if it makes no difference to a user how something is done, then it is by definition an unimportant implementation detail.
Further, it isn't closures that are fundamental. It's lambdas and currying which create implicit closures. Something cannot be fundamental if it is composed of other entities.
Perhaps I just design my programs better, so I don't need to use closures? After all, I've written a Scheme interpreter in Haskell. Is that trivial enough for you?

Though I should probably clarify something, just as I don't consider myself to be using closures if the language creates them. I don't consider myself to be using closures if I'm not accessing information outside the local scope. Since technically, anonymous functions are closures, I just don't use them as such (so I state I don't use closures, I use lambdas.)

> **schauerlich said:**
> 
Again, you are reversing the causality. When someone is designing a language, they think "hmm...  I want the language to do *this*. What's a convenient syntax for *this*?" They do not say "This syntax looks kind of cool, I wonder what it should do..." The features a language supports are defined by the language implementers writing code to perform those tasks. Have you written an interpreter before? There are (at least) two phases to most interpreters: parsing, and execution. Parsing is the ONLY stage in which syntax matters whatsoever. A parser breaks up the stream of text from the file into an abstract representation of the program which is syntax-independent (called the abstract syntax tree, AST). It expresses relationships between computational entities. I could take this AST and emit a completely different language syntax-wise that preserved the semantics. It is this AST that gets fed into the execution engine of the interpreter, *where the features of language are defined and executed*. Not in the parser, but the execution engine, which is independent of syntax.



C simply does not support inheritance or polymorphism. Java could support these things with completely different syntax. I don't see how this supports your point. Yes, C does not provide syntax for features it does not support. But it doesn't fail to provide support for these features *because* it lacks the syntax for them; rather, it lacks syntax for them because it does not support those features.



No. That is simply an incorrect statement. Having syntax is the result of having a feature. One is a consequence of another. They are not equivalent.

Consider lisp: when it comes down to it (and you ignore reader macros), there's really only about 4-5 grammar rules: you have an sexpression, which is either an atom or a list; and lists, which can contain any number of atoms and lists recursively. That is the only syntax that exists in the language. The rest of the language is implemented in terms of special forms, which for the most part could even be implemented in the language itself. There are only a few fundamental forms (lambda being one of them), but these are not encoded in the syntax; they are purely semantic entities.


You are still incorrect. It's not surprising, because we aren't talking about the same things.

It is simple fact that, in language, semantics arises from syntax. In order to know the semantics you must first parse the syntax. This is where my attention lies.

That said, in the creation of a language the process is reversed. You have a concept and you want to express it. So you choose a syntax. This is where you focus most of your attention.

Btw, yes I have written an interpreter before (for Scheme.)As you state an interpreter does the following: You parse the target language syntax. Then you generate syntax for your execution engine (an AST tree.) Then you feed that to the engine.

As you can see, two out of those three steps involve syntax. If the majority of the work is syntactical, how can you say it's a minor part? As I said before, being able to generate a random syntax does not reduce the value of syntax.

Next off, C does in fact have a syntax for polymorphism. It's just implicit (and up to you to create.) As for Lisp, you're still missing the point. Lisp's syntax is very flexible, as you said the majority of the language can be written in the language itself. This doesn't make them pure semantic entities, it makes them composite syntactic entities (syntax created from syntax.) This is the building block of all computer science, abstractions built upon abstractions allowing one to define complex behavior simply.


> **schauerlich said:**
> 
Yes, it's called the JVM/.NET.


Superficially, yes those do qualify. However, I was thinking more of a system to render syntax completely personal. Meaning a system of languages that compile to the same (human readable) language (which would take care of type differences and what not, since it's all the same language.) Admittedly, I didn't make this distinct.

> **schauerlich said:**
> 
You picked the wrong programmer to talk about linguistics with. :)
Because you'd fail a linguistics class? ;p

---

### Post by schauerlich on 2012-07-01
> **satsujinka said:**
> As I said before, if it makes no difference to a user how something is done, then it is by definition an unimportant implementation detail.

Calling anonymous functions an unimportant implementation detail of a purely functional programming language is missing the point. It is a very important concept from a language design perspective.

> Perhaps I just design my programs better, so I don't need to use closures? After all, I've written a Scheme interpreter in Haskell. Is that trivial enough for you?

Again, claiming a well designed Haskell program doesn't need closures is just ludicrous.

> 
Though I should probably clarify something, just as I don't consider myself to be using closures if the language creates them. I don't consider myself to be using closures if I'm not accessing information outside the local scope. Since technically, anonymous functions are closures, I just don't use them as such (so I state I don't use closures, I use lambdas.)

You've never done something like this?

```
f k xs = map (k *) xs
```

Obviously this is a trivial example, but it's still creating a closure. This kind of thing is everywhere in Haskell code.

> 
It is simple fact that, in language, semantics arises from syntax. In order to know the semantics you must first parse the syntax. This is where my attention lies.

That said, in the creation of a language the process is reversed. You have a concept and you want to express it. So you choose a syntax. This is where you focus most of your attention.


You are stating one and then implying the other. You are saying because you must understand the syntax to understand the semantics, that the syntax is fundamental and the semantics are derived. In fact, it is the reverse. Semantics are fundamental and syntax is used to transmit it. Just because you need to be able to read the Latin alphabet to understand written English does not mean that the alphabet is fundamental and the English Language is derived. Languages were spoken long before they were written. And perhaps more crucially, humans had thoughts before they spoke (since speech is just another encoding of meaning).

> 
Btw, yes I have written an interpreter before (for Scheme.)As you state an interpreter does the following: You parse the target language syntax. Then you generate syntax for your execution engine (an AST tree.) Then you feed that to the engine.

As you can see, two out of those three steps involve syntax. If the majority of the work is syntactical, how can you say it's a minor part? As I said before, being able to generate a random syntax does not reduce the value of syntax.

Okay, but what is an AST without the execution engine to run it? It is semantically void without some behavior associated with it. This behavior is not part of the syntax, or the AST. It is defined independently of it.

> 
Next off, C does in fact have a syntax for polymorphism. It's just implicit (and up to you to create.) 

All general purpose programming languages are Turing-complete. Any language can be implemented in terms of any other language. What you are trying to say is true (you can have polymorphism in C), but is trivial. C does not have syntax for polymorphism; polymorphism is not part of the C language definition. C has the ability to implement polymorphism, but that is not the same as C supporting it natively. By your statement, C also has syntax for IRC clients and window managers, which is absurd.

> As for Lisp, you're still missing the point. Lisp's syntax is very flexible, as you said the majority of the language can be written in the language itself. This doesn't make them pure semantic entities, it makes them composite syntactic entities (syntax created from syntax.) This is the building block of all computer science, abstractions built upon abstractions allowing one to define complex behavior simply.

Ah, but they are NOT defined in terms of syntax. There is absolutely no syntactic difference between forms built into the language and forms you define yourself. The only syntax is s-expressions. Abstractions are not syntax; abstractions are semantic. You rewrite the meaning of the computation in terms of a simpler or more convenient model. And you build abstractions by writing syntax, but only as a means to an end. Syntax encode semantics, but be careful not to conflate an idea with a representation of that idea.

> 
Superficially, yes those do qualify. However, I was thinking more of a system to render syntax completely personal. Meaning a system of languages that compile to the same (human readable) language (which would take care of type differences and what not, since it's all the same language.) Admittedly, I didn't make this distinct.

I'm not sure I understand the difference, other than that you'd prefer it to compile to a language higher level than assembly (or JVM/CLR bytecode). There are languages which compile to C (or other higher level programming languages).


> Because you'd fail a linguistics class? ;p
No, because I've actually taken some.

---

### Post by CptPicard on 2012-07-01
> 
Further, it isn't closures that are fundamental. It's lambdas and currying which create implicit closures. Something cannot be fundamental if it is composed of other entities.

The concept of closures in a programming language is not "composed of" those things. A language either "knows" what the local visible bindings are at the anonymous function's definition site, or it doesn't. It's easy to see how having closures enables currying; conversely I'm having a hard time thinking of a case where I could have the ability to curry functions and build general-case closure functionality on top of that. You would have to at least figure out the scope of the closure yourself and curry your function for each of those values in the scope.

> 
Perhaps I just design my programs better, so I don't need to use closures? After all, I've written a Scheme interpreter in Haskell. Is that trivial enough for you?

Did your Scheme interpreter support closures, then?

I never understood the mindset that writing things without making use of language features is a sign of better program design, especially in a case like this where we're dealing with functional programming, hence closures being one of the core points... your idea that avoiding them makes a program's structure superior seems rather arbitrary, in particular if it is borne out of some kind of "C can do callbacks so at least lambdas are fine" kind of mindset.

> It is simple fact that, in language, semantics arises from syntax. In order to know the semantics you must first parse the syntax. This is where my attention lies.

Of course you need to "read in order to understand", but it's still just a collection of symbols arranged according to a grammar. Meaning comes from knowing what the symbols represent; and the grammar then says what kind of things can go together in what kinds of ways -- possibly creating more meaning (most expressive programming languages tend to allow for such interesting recombinations). But even in those cases the syntax serves the purpose of enabling descriptions of those combinations; they don't "come into being" by someone deciding that you can but A next to B and then magic happens.


> 
As you can see, two out of those three steps involve syntax. If the majority of the work is syntactical, how can you say it's a minor part?

Both of those syntax-steps are actually rather boring from a computation standpoint -- writing parsers for example is a well-understood problem that has general solutions that don't even have anything to do with what is later on done with the code that is being read in. So in the syntax-management steps, we're actually solving a wholly separate parsing problem.

> 
Next off, C does in fact have a syntax for polymorphism. It's just implicit (and up to you to create.)

Most empathically, no, C does not have syntax for polymorphism, for as long as this conversation remains in any sense meaningful. If you're going to start talking about "implicit" syntaxes, the entire conversation can pretty much be abandoned, as we're down to just saying that *any language has syntax for anything*, you just need to code it!


> As for Lisp, you're still missing the point. Lisp's syntax is very flexible, as you said the majority of the language can be written in the language itself.

This is because Lisp is almost a no-syntax language; too much syntax just simply adds rules of what you can't do. When the outward representation is general and does not get too much in the way, you can bend it to do pretty much anything.

> This is the building block of all computer science, abstractions built upon abstractions allowing one to define complex behavior simply.

This is somewhat comparable to the argument that "it's all just library calls anyway" that I sometimes hear from the low-level-language proponent crowd. IMO the really interesting ideas in programming language design in particular do not deal with what you can build as some kind of "libraries" with existing features; the the interesting ones are the big-idea, all-encompassing language features that alter how you do things. These are the things that, if they did not exist, would be difficult or "impossible" to implement in terms of the language without the features -- and while it would be "possible" to write code to implement the features, we would no longer be speaking of the same language.

You know, if it really was all in the syntax, parsing wouldn't be a generally rather solved problem; you couldn't parse without knowing anything about what you'll do with your end result; and most importantly here, we'd have much better static code analysis tools. We could just look at the code and say what it does. But because it's just syntax, having the grammar according to which our code is correct is not going to help us any with how our code actually behaves -- see halting problem and friends...

---

### Post by satsujinka on 2012-07-01
@schauerlich

If you can't understand that computers execute commands with only syntax then I'll never manage to convince you that semantics do in fact arise out of syntax. It doesn't matter in the slightest that humans have concepts first. Nor does it matter that humans code using concepts, those concepts are entirely lost to the computer. The CPU doesn't have any way of determining meaning. It is only a symbol (e.g. Syntax) processing unit. Please, if you don't understand then read Turing and Searle's works.

Nor do I really care that you feel that using any anonymous function is using a closure. I made it perfectly clear that I don't consider \ x -> x to be a closure. It is utterly unimportant to me that that be a closure (because you must understand that there's no requirement for that to be the case.) When I do something like the following, then and only then will I consider myself to be using a closure.
```
add x = (\ y -> y+x)
```

I dont't see anything absurd about having syntax for irc or window managers. If you can make syntax for objects or functions why not syntax for programs?

If you wish to call composite syntax semantics, you're free to do so. It's dishonest, but so long as you make it clear there's no problem with it.

@CptPicard 
I don't remember whether or not my interpreter did. I think so, on account of it having proper lexical scope, but I don't remember. I don't really think that not using closures makes me better, I was more making a jab at schauerlich for implying that closures are necessary in any non-trivial work.
As for syntax being a solved problem. I would still claim that in support of syntax being important. It's so important that people felt the need to solve the problem early in the computer sciences.

---

### Post by schauerlich on 2012-07-02
> **satsujinka said:**
> @schauerlich

If you can't understand that computers execute commands with only syntax then I'll never manage to convince you that semantics do in fact arise out of syntax. It doesn't matter in the slightest that humans have concepts first. Nor does it matter that humans code using concepts, those concepts are entirely lost to the computer. The CPU doesn't have any way of determining meaning. It is only a symbol (e.g. Syntax) processing unit. Please, if you don't understand then read Turing and Searle's works.


This is a red herring. No one claimed that computers understand programs in a strong-AI sense. Semantics in a Turing machine (and thus programming language) are governed by the state transitions and what symbols are written. The computer does not understand them, but it follows them. It is only the human who designed the machine for whom they have meaning.

> 
Nor do I really care that you feel that using any anonymous function is using a closure. I made it perfectly clear that I don't consider \ x -> x to be a closure.

Okay. You are wrong.

> I dont't see anything absurd about having syntax for irc or window managers. If you can make syntax for objects or functions why not syntax for programs?

What is absurd is equating a program which implements an irc client "syntax" for an irc client. There is syntax for function/struct definitions and function calls, and a series of functions calls can implement an IRC client, but there is no syntax for that IRC client.

---

### Post by CptPicard on 2012-07-02
> 
I dont't see anything absurd about having syntax for irc or window managers. If you can make syntax for objects or functions why not syntax for programs?

Because you have an infinite number of programs, so you'd just be growing a huge set of particular syntax for particular programs, instead of creating a flexible minimal syntax that lets you build those things... this "implicit syntax" concept you made up.

> 
If you wish to call composite syntax semantics

The thing is, the stuff really is not "composite syntax" if it is not somehow a combination of grammar rules. Of course, if anything that is a product of a computation from a grammar is "composite syntax", then this is once again a rather meaningless discussion.

> 
I don't remember whether or not my interpreter did. I think so, on account of it having proper lexical scope,

You can easily have lexical scope without supporting closures.

> I would still claim that in support of syntax being important. It's so important that people felt the need to solve the problem early in the computer sciences.

I really am not surprised that parsing is one of the first problems that are of interest regardless of whether it is important in the sense that we're discussing here, simply because it's a very useful problem to solve anyway -- and as a computer takes in symbolic input in order to solve a problem, it's also not surprising that studying the formal rules of constructing that input and then recognizing whether a string is part of the language is also a way to study computation in general.

The point was about parsers solving a completely different problem to the program being parsed. If your C compiler parses a C program, the parsing phase essentially is able to tell you if you've got a valid C program. It does nothing in terms of actually executing what the program describes. So the syntax of C doesn't yet do anything.

> **schauerlich said:**
> 
Okay. You are wrong.


Hate to have to disagree with you as we generally are on the same side in these discussions; in general parlance, anonymous functions are called closures, but what the closure actually is, is the set of visible bindings that are outside the local internal scope of the lambda. That lambdas == closures is such a broadly spread misconception that it is becoming a fact on its own... Haskell of course always does give all lambdas a closure you can use, but don't have to -- just don't refer to any of the bindings outside of the local scope.

---

### Post by trent.josephsen on 2012-07-02
I find it amusing to note that the argument currently going on is over the semantics of the word "syntax".

---

### Post by schauerlich on 2012-07-02
> **CptPicard said:**
> Hate to have to disagree with you as we generally are on the same side in these discussions; in general parlance, anonymous functions are called closures, but what the closure actually is, is the set of visible bindings that are outside the local internal scope of the lambda. That lambdas == closures is such a broadly spread misconception that it is becoming a fact on its own... Haskell of course always does give all lambdas a closure you can use, but don't have to -- just don't refer to any of the bindings outside of the local scope.

Right, I know that anonymous functions are not synonymous with closures. But Haskell creates a closure (at least theoretically), even if there is nothing to bind. In my mind a closure that captures no variables is still a closure, in the same way that the empty set is still a set. I know that not all anonymous functions are closures, but Haskell's are. I am aware of the distinction you're making. Perhaps I mixed up my terminology.

---

### Post by satsujinka on 2012-07-02
@schauerlich
To put it simply, what you call semantics are actually just syntax rules. There is no meaning in a computer's actions. Semantics reside only in the heads of humans. This is why it is important to note that computers don't understand what they're doing, because you can't have semantics in a system without understanding.

Semantics are the interpretation by humans of what the syntax is supposed to represent. As I've said, since we humans with our concepts created the system, it does in fact appear to be the case that semantics come first. However, this is not obvious. There are several theories of mind that state that without language it is impossible to think (that without language it's impossible to understand meaning.) The problem is, that there's no way to verify this one way or the other. You need language to communicate, but if you have language then you can think... but if you can't think without it you also can't communicate that. This is why I state that semantics arises from syntax. We all can derive meaning from syntax, but it's not clear if it's possible to have meaning without syntax.

> **CptPicard said:**
> Because you have an infinite number of programs, so you'd just be growing a huge set of particular syntax for particular programs, instead of creating a flexible minimal syntax that lets you build those things... this "implicit syntax" concept you made up.

I may have made up the concept, but the idea of having syntax for a particular program is not new. [Language Oriented Programming]("http://en.wikipedia.org/wiki/Language-oriented_programming") is all about creating syntax that makes your problem easy, in effect creating a syntax for a program.
> **CptPicard said:**
> 
The thing is, the stuff really is not "composite syntax" if it is not somehow a combination of grammar rules. Of course, if anything that is a product of a computation from a grammar is "composite syntax", then this is once again a rather meaningless discussion.

Again I made up the term to describe the situation. To put it differently, the form of a function is a grammar rule. Combining functions (to produce a new effect) is akin to creating a new rule under the name of that function (via substitution to be simple about it.)
> **CptPicard said:**
> 
You can easily have lexical scope without supporting closures.

True, however, closures can fall out of it. I didn't keep the interpreter, so I've no way of knowing and I never tested closures... so there's really no way of knowing.
> **CptPicard said:**
> 
I really am not surprised that parsing is one of the first problems that are of interest regardless of whether it is important in the sense that we're discussing here, simply because it's a very useful problem to solve anyway -- and as a computer takes in symbolic input in order to solve a problem, it's also not surprising that studying the formal rules of constructing that input and then recognizing whether a string is part of the language is also a way to study computation in general.

The point was about parsers solving a completely different problem to the program being parsed. If your C compiler parses a C program, the parsing phase essentially is able to tell you if you've got a valid C program. It does nothing in terms of actually executing what the program describes. So the syntax of C doesn't yet do anything.

No, but the syntax of the machine code generated (which itself is nothing but a syntax) does do things (given you have a computer.) And, optimizing compilers notwithstanding, we can map between C and machine code. So it is valid to say that the C code does what the machine code does (which is specify what operations a computer should perform.)

---

### Post by 11jmb on 2012-07-02
> **satsujinka said:**
> 
And, optimizing compilers notwithstanding, we can map between C and machine code.


you can map between any programming language and machine code, otherwise it wouldn't run. This sounds especially wrong coming from somebody who is essentially arguing that all languages are equal because of turing equivalence.

> **satsujinka said:**
> 
So it is valid to say that the C code does what the machine code does (which is specify what operations a computer should perform.)

No, C is a layer of abstraction between the programmer and the machine code. In exchange for the ability to write architecture-specific code, C allows a programmer to spend less time developing more portable code. 

I'd say the heart of software development lies in the ability to embrace abstraction. Even assembly code makes abstractions such as hierarchical memory. Even though you dismiss an abstraction which gives you more expressive power as "syntactic sugar", you miss the point that we consciously make a tradeoff between development time and the level of detail at which we can control our programs. Sometimes a fine level of detail is needed, such as a portion of the work I do which ends up on smaller devices. The entire point is to pick the layer of abstraction which best suits your needs.

---

### Post by satsujinka on 2012-07-03
> **11jmb said:**
> you can map between any programming language and machine code, otherwise it wouldn't run. This sounds especially wrong coming from somebody who is essentially arguing that all languages are equal because of turing equivalence.



No, C is a layer of abstraction between the programmer and the machine code. In exchange for the ability to write architecture-specific code, C allows a programmer to spend less time developing more portable code. 

I'd say the heart of software development lies in the ability to embrace abstraction. Even assembly code makes abstractions such as hierarchical memory. Even though you dismiss an abstraction which gives you more expressive power as "syntactic sugar", you miss the point that we consciously make a tradeoff between development time and the level of detail at which we can control our programs. Sometimes a fine level of detail is needed, such as a portion of the work I do which ends up on smaller devices. The entire point is to pick the layer of abstraction which best suits your needs.
My point about optimizing compilers is that you can't easily map back to C from machine code. Obviously, mapping to machine code isn't the problem.
Otherwise, I believe I cleared up that when I say "just syntactic sugar" I'm not being dismissive. I'm merely stating the fact that you can reduce the expression to a lower level. Naturally, having higher level abstractions is a good thing.
If it's still not clear, my initial comments about generics and closures; were on a different topic than that of syntax. At the time, I was merely expressing that I don't find those features to be frequently useful (I later commented that that is not the same as saying they shouldn't exist, and that the comment should have been taken to only be a statement of limitation.)

---

### Post by Simian Man on 2012-07-03
> **satsujinka said:**
> My point about optimizing compilers is that you can't easily map back to C from machine code. Obviously, mapping to machine code isn't the problem.
Otherwise, I believe I cleared up that when I say "just syntactic sugar" I'm not being dismissive. I'm merely stating the fact that you can reduce the expression to a lower level. Naturally, having higher level abstractions is a good thing.

I think this is the heart of your misunderstanding.  Just because you can map one language to another doesn't mean you can do so using syntax alone.  Yes you can map things like closures, templates objects and whatever else to C or even assembly - that's how these things are ultimately implemented.  But that doesn't mean it's just syntax in between.  You can't get a C compiler, fiddle with the yacc parser, and make come up with a language where you can use any of these features, because the rest of the language has no conception of them!  You could only make relatively superficial changes.

---

### Post by trent.josephsen on 2012-07-03
The heart of satsujinka's misunderstanding is here:

> **satsujinka said:**
> @schauerlich
To put it simply, what you call semantics are actually just syntax rules.

As long as sat insists on this, no further progress can be made.

---

### Post by satsujinka on 2012-07-03
> **Simian Man said:**
> I think this is the heart of your misunderstanding.  Just because you can map one language to another doesn't mean you can do so using syntax alone.  Yes you can map things like closures, templates objects and whatever else to C or even assembly - that's how these things are ultimately implemented.  But that doesn't mean it's just syntax in between.  You can't get a C compiler, fiddle with the yacc parser, and make come up with a language where you can use any of these features, because the rest of the language has no conception of them!  You could only make relatively superficial changes.
If what you're saying is true, then there would be no new language features. Happily, it **is** the case that you can get a C compiler and fiddle with it a bit and end up with any/all of those features. Several languages started off this way, off the top of my head I can think of two Go and C++.

@trent
There's been several layers to this discussion, so perhaps I missed it, but maybe you could provide a clear proof that I'm incorrect? Though I'd understand if you don't want to, because any proof requires axioms and I may simply not accept your axioms (likewise, you don't seem to share mine.)

---

### Post by Barrucadu on 2012-07-03
> **satsujinka said:**
> If what you're saying is true, then there would be no new language features. Happily, it **is** the case that you can get a C compiler and fiddle with it a bit and end up with any/all of those features. Several languages started off this way, off the top of my head I can think of two Go and C++.

Yes, you *can* get a C compiler and fiddle with it to make it support new language features, *but not through purely syntactic means*! If that were the case, you could just, say, take GCC's parser and add support for dynamic typing, which is obviously wrong.

---

### Post by satsujinka on 2012-07-03
> **Barrucadu said:**
> Yes, you *can* get a C compiler and fiddle with it to make it support new language features, *but not through purely syntactic means*! If that were the case, you could just, say, take GCC's parser and add support for dynamic typing, which is obviously wrong.
It is not obviously wrong. You can indeed convert dynamic types into static types using a syntactic map. Consider Python's default implementation. Now, that's not to say it's easy. It would be tremendously difficult to "just" take GCC's parser and add support for dynamic typing, but it is doable.
Adding features is "just" a matter of figuring out the lower level representation, the higher level representation, and producing a map between those representations. It's not a simple task but it is a purely syntactic one.

---

### Post by trent.josephsen on 2012-07-03
> **satsujinka said:**
> There's been several layers to this discussion, so perhaps I missed it, but maybe you could provide a clear proof that I'm incorrect? Though I'd understand if you don't want to, because any proof requires axioms and I may simply not accept your axioms (likewise, you don't seem to share mine.)

It's not a question of axioms. It's a question of...

wait for it...

**semantics**!

So you don't think it's useful to make a distinction between semantics and syntax. Fine, whatever, if it works for you. But if you insist that there *is* no difference, you're going to run into trouble, because you are the only person in the world I'm aware of who insists on such an equivalence.

It's something like insisting that yellow and green are the same color... or maybe more like saying that yellow is just a type of green. I mean, nobody can really contradict such a statement because it boils down to an ultimately subjective judgment call (what is the longest wavelength of light that can be considered "green"?), but the bottom line is that if you insist on calling yellow, green, you're still not talking about the same thing as everyone else.

Communication depends on shared meaning. If you insist on calling semantics a subset of syntax, you are merely obstructing communication. I'd encourage you to adopt the common meaning, not adhere to your own definition.

However, I think this thread has been going nowhere for two or three pages now, and I'm going to let this be my last word. I have better things to do than argue meta-semantics.

---

### Post by satsujinka on 2012-07-03
> **trent.josephsen said:**
> It's not a question of axioms. It's a question of...

wait for it...

**semantics**!

So you don't think it's useful to make a distinction between semantics  and syntax. Fine, whatever, if it works for you. But if you insist that  there *is* no difference, you're going to run into trouble, because  you are the only person in the world I'm aware of who insists on such  an equivalence.

It's something like insisting that yellow and green are the same  color... or maybe more like saying that yellow is just a type of green. I  mean, nobody can really contradict such a statement because it boils  down to an ultimately subjective judgment call (what is the longest  wavelength of light that can be considered "green"?), but the bottom  line is that if you insist on calling yellow, green, you're still not  talking about the same thing as everyone else.

Communication depends on shared meaning. If you insist on calling  semantics a subset of syntax, you are merely obstructing communication.  I'd encourage you to adopt the common meaning, not adhere to your own  definition.

However, I think this thread has been going nowhere for two or three  pages now, and I'm going to let this be my last word. I have better  things to do than argue meta-semantics.
I suppose it's no point arguing if this is your last post (but I can't help but try to provoke another response.)
I am using the common definition of semantics. At least, as it is on [wikipedia]("http://en.wikipedia.org/wiki/Semantics"). Admittedly, I was conflating syntax and [pragmatics]("http://en.wikipedia.org/wiki/Pragmatics"). I haven't been discussing what a syntax means (semantics,) but how a syntax is used (pragmatics.)

Another  point of contention seems to be that I accept user defined syntax as  syntax for the language in question. (ex. I accept user defined object  notation in C as being the same as C having an object notation.) Perhaps  a more clear statement might be that C has an object pattern (in the  same vein that the Visitor pattern gives OO languages double dispatch.)

So  to use slightly clearer language. Depending on how you model a program  you'll choose different languages. Specifically, you'll choose languages  that have a specified (hopefully convenient) syntax for the patterns  you want to use. Having too many patterns in one language makes the  language hard to understand and probably a little too verbose (say C++.)  Therefore, it is better to use a language that closely fits your  patterns (it'll be clearer and have more convenient syntax -> meaning  less code and faster development.) However, if you use multiple  languages (because there's multiple pattern domains) you end up with  needing a translation layer between them (usually written in C.) This is  time consuming and detracts from the fun of programming. Therefore,  these languages should "know" about one another in such a way that they  can directly inter-operate (knowledge may come in the form of being  translated to the same language/bytecode as in the case in REBOL +  JVM/.NET respectively.) 

This argument is also the fuel of my  "syntax is really important" argument. Having specified syntax for a  pattern (if well designed) will change how you program (ex. object  pattern in C versus object syntax in Java.) 

I happen to not  "need" all of the patterns available to me and so in my dialog with  Simian Man I stated that I don't miss those patterns when using C. What I  do miss is a more modern look and, since I really like Haskell's lists,  I miss lists (admittedly, that relies on pattern matching, however, I  can't say I miss pattern matching in general, because I only miss it in  the form of lists.) Which got combined with my preference to explicitly  pass variables (and not use closures, even if they are available to me)  as meaning "look at me, I'm so great, I don't need your smelly high  level features." When in reality I dearly adore them... I just don't  miss them when I don't have them.

---

### Post by trent.josephsen on 2012-07-03
10/10

---

