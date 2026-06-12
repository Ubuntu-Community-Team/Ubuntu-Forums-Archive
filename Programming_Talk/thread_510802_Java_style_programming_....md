---
title: "Java style programming ..."
date: 2007-07-27
forum: Programming Talk
---

### Post by slavik on 2007-07-27
just saw something done in python that I have seen done in Java as a standard of some sort ...

```

class such_and_such {
  blah func() {}
  private this;
  private that;
  [COLOR="Red"]**main**[/COLOR] () { print "something" }
}

s = new such_and_such;
s.main();

```

my question is: What is the point of allocating a new class when it will be a singleton anyway ... ?

---

### Post by samjh on 2007-07-27
Impossible to answer without a context.

Why are you creating a class?  What is it supposed to do?  What is that "something" you are talking about?'

If you are talking about the main method, you've coded it wrong.  It should be just:
```
public class whatever {
    public static void main(String[] args) {
        // insert code
    }
}
```The main method is where program execution starts.  The class in which the main method belongs, is basically the name of the class that is executed when you run the program.  So in this case, the name of the program is "whatever".

---

### Post by zanglang on 2007-07-27
samjh, that was probably Python, but coded in Java style. ;) (Although the braces and semicolons probably didn't have to be there...)

When transiting from a enterprisey language like Java that places this huge emphasis on OO design and style to something so incredibly simplistic as Python, I guess it's pretty hard to drop your old habits. :)

---

### Post by samjh on 2007-07-28
> **zanglang said:**
> samjh, that was probably Python, but coded in Java style. ;) (Although the braces and semicolons probably didn't have to be there...)That's what I'm wondering.  It a weird Java-Python hybrid.

---

### Post by slavik on 2007-07-28
that's my point ... it should be like in your example. but what I see a lot is people moving the main() into something like run(), then in main allocate an instance of themselve and cann the run method. (needless to say, they don't bother to pass the system arguments)

---

### Post by rekahsoft on 2007-07-28
> **samjh said:**
> That's what I'm wondering.  It a weird Java-Python hybrid.

it could have been jython; or an attempt at python by a java coder :P

---

### Post by Note360 on 2007-07-28
i have no idea what that is, but it is probably near valid jython.

---

### Post by thomasaaron on 2007-07-28
To answer the question (I think):

You write a single class and save it as <classname>.java.
Then you can call it from anywhere else in the project with: classname.method(), etc...

Plus (and I'm very new to Java), I'm finding it nice to be able to track down and change a class that needs modification if it is in its own file and not somewhere in the middle of a file with many classes defined.

Hope that makes sense.

---

### Post by pmasiar on 2007-07-28
> **rekahsoft said:**
> it could have been jython; or an attempt at python by a java coder :P

Jython has exactly same syntax as Python (called also CPython).

Python is build on top of C libraries, Jython is build on top of JVM (and can call Java classes and inherit drom them). There is another implementation of Python on top of .NET, called IronPython. They all share the same syntax, differences are in libraries - JVM and .NET lacks some libraries present in CPython, but language syntax is the same.

---

### Post by kknd on 2007-07-28
> **slavik said:**
> just saw something done in python that I have seen done in Java as a standard of some sort ...

```

class such_and_such {
  blah func() {}
  private this;
  private that;
  [COLOR="Red"]**main**[/COLOR] () { print "something" }
}

s = new such_and_such;
s.main();

```

my question is: What is the point of allocating a new class when it will be a singleton anyway ... ?

I don't get it. This is not a singleton at all.

A singleton in Java:

```

public class TestSing
{
        private static final TestSing inst = new TestSing();
        private TestSing() {}
       
        TestSing getInstance()
        {
                return inst;
        }
}


```

---

### Post by bbzbryce on 2007-07-28
> **thomasaaron said:**
> To answer the question (I think):

You write a single class and save it as <classname>.java.
Then you can call it from anywhere else in the project with: classname.method(), etc...

Plus (and I'm very new to Java), I'm finding it nice to be able to track down and change a class that needs modification if it is in its own file and not somewhere in the middle of a file with many classes defined.

Hope that makes sense.

You may know this but you can define multiple classes in a single java file, in addition to inline classes.

---

### Post by slavik on 2007-07-29
> **kknd said:**
> I don't get it. This is not a singleton at all.

A singleton in Java:

```

public class TestSing
{
        private static final TestSing inst = new TestSing();
        private TestSing() {}
       
        TestSing getInstance()
        {
                return inst;
        }
}


```
I know what a singleton is ... my point is that when someone creates the class and instead of having all the code in main(), they put it into a function named run() or something, then inside main(), allocate the object (a copy of itself basically) and then cann that new object's run() function ... basically, the only reason I used the singleton is because you only need 1 copy of the object that is your whole program anyway.

---

### Post by steve.horsley on 2007-07-29
Something like:
```
public class SudokuPuzzle {
    public void run() {
        blah blah
    }
}

public static void main(String[] args) {
    SudokuPuzzle p = new SudokuPuzzle();
    p.run();
}
```

First, in object oriented programming it can help to describe the problem in english, and then whenever that description contains a "the", "a" etc, the description is describing an object - create a class to represent that object. This produces classes that closely match the problem, and can help get the structure of the solution problem right and clearly understood, In this context, "a Sudoku Puzzle" is ripe for being a class that contains all the sub-components of the problem. So creating a Sudoku Puzzle object is a logical first step. And the problem in hand almoxt certainly only calls for just one puzzle.

Second, in java, writing functions and methods that belong to an object is natural. Writing code that is common to all members of a class - "static" code that doesn't actually need a class instance for it to be invoked on feels slightly unnatural and requires use of the static keyword. Writing code that doesn't belong to a class at all simply isn't supported by the language. 

Creating an instance of an object to represent the whole of the program is not a particularly odd thing to do. In any OO language/solution.

---

### Post by pmasiar on 2007-07-29
BTW proper method name in this case is not "run" but "execute". See also  [Execution in the Kingdom of Nouns](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html) :-)

```
public class SudokuPuzzle {
    public void execute() {
        blah blah
    }
}
}
```

> **steve.horsley said:**
> Creating an instance of an object to represent the whole of the program is not a particularly odd thing to do. In any OO language/solution.

This is true - in Java world, verb cannot exist by itself,  without the nouns (objects). This is why Java is called not object-oriented but object-obsessed :-) Situation of verbs in Java is very like situation of women in fundamentalist muslim country.

Sorry could not resist - but OP *did* asked about the Java style :-)

---

