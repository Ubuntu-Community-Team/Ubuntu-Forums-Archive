---
title: "Quick java question (imitating python functionality)"
date: 2013-05-21
forum: Programming Talk
---

### Post by flyingsliverfin on 2013-05-21
Hi there,
I need to translate a program I have in python to Java. I ran across a problem that made me wonder about the basic functionality of the Java.

In python, you can reassign a function to a new name. So for instance, i can do
```
def test(info): print info
tmp = test
tmp(A) #prints variable A via test function
```

In Java, can I do something similar to this?

---

### Post by trent.josephsen on 2013-05-21
You can do something similar, but with non-negligible boilerplate code and slightly different semantics. It would look something like this -- it's been a while since I did Java so I could be terribly wrong:

```
/* in DisplayFunction.java */
interface DisplayFunction { void run(String info); }

/* in your program */
DisplayFunction test = new DisplayFunction() {
    void run(String info) {
        System.out.println(info);
    }
};

test.run(A); // prints the value of A
DisplayFunction tmp = test;
tmp.run(A); // same thing
```

In English, I created an interface that has one method, and instantiated it by defining the method in-line. Now I have a "function" object (test) that is a first-class object and can be "called" by invoking its run() method. Closures work, but closed-over values are immutable, so they can't save state. Given the application domain of Java, this is probably a good thing.

This technique probably has some fancy name in the Design Patterns book. I wouldn't recommend it; there are usually less warty ways to achieve dynamic function calls in a language without first-class functions. Every once in a while it may come in handy though.

---

### Post by ofnuts on 2013-05-22
> **trent.josephsen said:**
> 
This technique probably has some fancy name in the Design Patterns book.

A "function object" or "functor". Warty, but the usual way to do it in Java.

---

### Post by flyingsliverfin on 2013-05-31
Ah, so basically you're pointing a new variable to the same object, and then using that reference correct? So essentially the same thing I guess

---

### Post by schauerlich on 2013-05-31
> **trent.josephsen said:**
> You can do something similar, but with non-negligible boilerplate code and slightly different semantics. It would look something like this -- it's been a while since I did Java so I could be terribly wrong:


You can also use the Callable interface for unary methods, which gives you the benefit of being able to pass it to standard library methods.

> Closures work, but closed-over values are immutable, so they can't save state. Given the application domain of Java, this is probably a good thing.

This is almost correct. Closed over primitives are properly immutable. However, closed over objects are not; only their references are immutable. This means you can't assign a new object to the same reference, but you can mutate the object that the reference points to.

```
List<String> list = new ArrayList<>();
Runnable run = new Runnable() {
    @Override
    void run() {
        list.add("foo"); // legal
        list = new ArrayList<>(); // illegal
    }
}
```
In fact, the above code will fail to compile because [FONT=Courier New]list[/FONT] is not declared final.

> This technique probably has some fancy name in the Design Patterns book. I wouldn't recommend it; there are usually less warty ways to achieve dynamic function calls in a language without first-class functions. Every once in a while it may come in handy though.

Unfortunately, the lambdas coming in Java 8 are merely syntactic sugar over this design pattern. Oracle will not sacrifice backwards compatibility for a proper first class function type.

---

### Post by Leuchten on 2013-05-31
> **schauerlich said:**
> 
Unfortunately, the lambdas coming in Java 8 are merely syntactic sugar over this design pattern. Oracle will not sacrifice backwards compatibility for a proper first class function type.

If the syntactic sugar is good enough, is there any reason to sacrifice backwards compatibility for proper first class functions? For example, in scala I can write 

```


val fib: Int = (n: Int) => n match { 
  case 0 => 0 
  case 1 => 1 
  case n => fib(n-1) + fib(n-2)
}

def a(x: Int, y: Int) = x + y
val b = a _ 

```

to my heart's content. It doesn't matter that my lambdas and functions are functors under the sheets, because I never write functor code at all.

---

### Post by trent.josephsen on 2013-05-31
> **schauerlich said:**
> This is almost correct. Closed over primitives are properly immutable. However, closed over objects are not; only their references are immutable. This means you can't assign a new object to the same reference, but you can mutate the object that the reference points to.

:idea: Aha! Thanks for that correction; that does make a bit more sense. (Not a tremendous amount of sense, but some more.)

---

### Post by schauerlich on 2013-05-31
> **Leuchten said:**
> If the syntactic sugar is good enough, is there any reason to sacrifice backwards compatibility for proper first class functions? For example, in scala I can write 

```


val fib: Int = (n: Int) => n match { 
  case 0 => 0 
  case 1 => 1 
  case n => fib(n-1) + fib(n-2)
}

def a(x: Int, y: Int) = x + y
val b = a _ 

```

to my heart's content. It doesn't matter that my lambdas and functions are functors under the sheets, because I never write functor code at all.

It's largely aesthetic reasons; types for functional interfaces are not explicitly functional, the types are less readable, and the call sites do not look the same (func.call(arg1, arg2) vs func(arg1, arg2)).

 There are also the aforementioned issues with lexical scoping and variable capture that don't operate like they do in other languages.

---

### Post by trent.josephsen on 2013-05-31
This seems a lot like the distinction between primitive types and objects, and the new standard looks to be "resolving" it in much the same way.

---

### Post by Leuchten on 2013-05-31
> **schauerlich said:**
> It's largely aesthetic reasons; types for functional interfaces are not explicitly functional, the types are less readable, and the call sites do not look the same (func.call(arg1, arg2) vs func(arg1, arg2)).

 There are also the aforementioned issues with lexical scoping and variable capture that don't operate like they do in other languages.


This can be handled with syntatic sugar. All of scala's anonymous functions are defined like:

```

trait Function6[-T1,-T2,-T3,-T4,-T5,-T6,+R] extends AnyRef {
  def apply(t1: T1, t2: T2, t3: T3, t4: T4, t5: T5, t6: T6): R
}

```

but the type ends up looking like:

```
  (Int, Float, BigInt, String, Char, Double) => Boolean 
```

because of syntatic sugar. Java sadly doesn't go that far and leaves a lot to be desired with its syntatic sugar for function literals, but with enough there is little to no difference. As for variable capture issues, that can also be sidestepped with functors, though I'm not entirely how scala does it:

```

var a = 5
val b = (x: Int) => a += x
b(10) //a now equals 15

```

Java could probably do all of that without breaking backwards compatibility, but they haven't for some reason. Java 8, last I checked, allowed you to mutate closed over variables if they were class members, not variables local to a function. I don't know if that's still the case or not.

---

