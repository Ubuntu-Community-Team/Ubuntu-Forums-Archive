---
title: "Yet another PHP question - how do you create SINGLETON class"
date: 2009-07-09
forum: Programming Talk
---

### Post by akvino on 2009-07-09
I want to create singleton class (meaning class with one instance only) which would serve as my controller class in OO design.

Few questions - how do I maintain this class/ what syntax do I use for singleton class (STATIC maybe);

in pseudo code I was thinking along these lines:

$class_handle //do I need to make this variable static? 
if class exists (need way to check this)
return class_handle;
else
$handle = new controller()
return class_handle;

---

### Post by Reiger on 2009-07-09
Singletons are globals. Don't bother?

---

### Post by unknownPoster on 2009-07-09
As Reiger said, Singletons introduce Global state into your design, so it's usually considered bad design practice.

That being said, here is one way to implement the Singleton pattern in Java, as described by Bill Pugh:
```

public class Singleton {
   // Private constructor prevents instantiation from other classes
   private Singleton() {}
 
   /**
    * SingletonHolder is loaded on the first execution of Singleton.getInstance() 
    * or the first access to SingletonHolder.INSTANCE, not before.
    */
   private static class SingletonHolder { 
     private static final Singleton INSTANCE = new Singleton();
   }
 
   public static Singleton getInstance() {
     return SingletonHolder.INSTANCE;
   }
 }

```

That being said, if you are wondering why global state is considered bad practice...

A global variable/state can be modified in all scopes. So basically, if Class A depends upon the global, but from anywhere in the program, any other Class can modify this global, potentially breaking Class A. As such, Global state causes programs to not be thread-safe. (If you care about that kind of thing.)

---

### Post by dwhitney67 on 2009-07-09
> **unknownPoster said:**
> ...
That being said, if you are wondering why global state is considered bad practice...

A global variable/state can be modified in all scopes. So basically, if Class A depends upon the global, but from anywhere in the program, any other Class can modify this global, potentially breaking Class A. As such, Global state causes programs to not be thread-safe. (If you care about that kind of thing.)

Sigh!...  Singletons are used quite often in multi-threaded applications.  Just because the instance object can be obtained globally, it does not mean you expose the entire object to every other object.  You only expose what is needed via its public interface.

---

### Post by Reiger on 2009-07-09
True. However it is beside the point of having/not-having Global variables. Sometimes you simply need them (say you want one DB connection handler and not a total of 25000 created as your program progresses of which some 10 have to be Garbage Collected every other second...), but especially in a language like PHP there is no point in beating about the bush there. In Java you have no choice because it forces Objects down your throat to the lowest level; but in PHP you have the simple global keyword for functions that need the global variables.

Also: actually try implementing the Java way of singletons in PHP. Fail awaits you because class properties cannot be automatically assigned anything but a scalar type. That is, something like this will be rejected by the parser/compiler (yes PHP is compiled to byte code):
[php]
class Foo {
  public $bar = new Bar();
}
class Bar {
}
[/php]

---

### Post by dwhitney67 on 2009-07-09
I am not very knowledgeable with PHP, having only studied it for a month last summer.

However, in Java (and for that matter, C++), this is an example of how I would define/implement a singleton object (of course, in C++ the syntax would be different).
```

class Singleton
{
  public static Singleton instance() {
     final Singleton instance = new Singleton();
     return instance;
  }

  private Singleton() {}
}

```

---

### Post by CptPicard on 2009-07-09
That would return a new object each time... :)

```


public class Singleton {


  private static Singleton instance;


  public static synchronized Singleton getInstance() {

    if (instance == null)
       instance = new Singleton();

    return instance;

  }

  
  private Singleton() {}  // Hmm, never tried private constructor
                          // on a top-level public class...

}



```

---

### Post by dwhitney67 on 2009-07-09
> **CptPicard said:**
> That would return a new object each time... :)

You're right.  :-)

I'm getting my C++ and Java constructs confused.  In C++, and C, it is permissible to declare a static object within a function.  I couldn't in Java, so I thought I was covered with the "final" declaration; but that is synonymous with the "const" in C/C++.

---

### Post by akvino on 2009-07-10
So if I am getting this right - you are suggesting against singleton class?

How does one implement controller class???

In my design I currently have

Web Menu -> Forms -> Many Collection Pages that instatiate objects -> Objects with Methods

What I want to do is:

Web Menu -> Forms -> Controller Class with Methods to Call objects -> Objects with Methods

This way I have one Object or one place from which all other objects are instantiated vs. many many many pages instantiating objects!>?

---

### Post by MicahCarrick on 2009-07-10
[http://www.php.net/manual/en/language.oop5.patterns.php]("http://www.php.net/manual/en/language.oop5.patterns.php")

---

### Post by akvino on 2009-07-10
Thanks will read through it...

---

