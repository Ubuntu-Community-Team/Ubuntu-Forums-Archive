---
title: "Understanding java and python"
date: 2011-02-16
forum: Programming Talk
---

### Post by CaptainMark on 2011-02-16
Ive recently started learning java and it surprised me how complex the syntax can be, i thought another object language would be a good place to expand my knowledge. The difference not in words or format but the length and complexity were a shock, from the simple fact that javas System.out.println("Hello"); is compared to pythons print('Hello') right to the fact that pythons ```
bannanas=input('How many bannanas can you eat? : ', end='')
print(bannanas)
```is much simpler that java's ```
public class bannanas {
    public static void main{
        reader = new BufferedReader( new inputStreamReader( System.in));
        int bannanas = 0;
        try {
            System.out.print("How many bannanas can you eat? : ");
            bannanas reader.readline();
        } catch( IOException ioe) {
            System.out.println("IO error ocoured"); 
        } // end try
        System.out.println(bannanas);
    } // end main
} // end bannanas
```OK ignore silly errors ive probaly made its not the point, believe me there is one. When trying to understand this I fried my brains, would it be a safe assumption to say that when i code input() in python that behind the scenes input() is being transformed by the python shell and that without me seeing it the shell is actually creating an object similar to the buffered reader object. Its just something id like to understand better??? Oh and please dont bog me down with heavy programming lanuage im just a curious begiinner

---

### Post by worksofcraft on 2011-02-16
> **CaptainMark said:**
> Ive recently started learning java and it surprised me how complex the syntax can be, i thought another object language would be a good place to expand my knowledge. The difference not in words or format but the length and complexity were a shock, from the simple fact that javas System.out.println("Hello"); is compared to pythons print('Hello') right to the fact that pythons ```
bannanas=input('How many bannanas can you eat? : ', end='')
print(bannanas)
```is much simpler that java's ```
public class bannanas {
    public static void main{
        reader = new BufferedReader( new inputStreamReader( System.in));
        int bannanas = 0;
        try {
            System.out.print("How many bannanas can you eat? : ");
            bannanas reader.readline();
        } catch( IOException ioe) {
            System.out.println("IO error ocoured"); 
        } // end try
        System.out.println(bannanas);
    } // end main
} // end bannanas
```OK ignore silly errors ive probaly made its not the point, believe me there is one. When trying to understand this I fried my brains, would it be a safe assumption to say that when i code input() in python that behind the scenes input() is being transformed by the python shell and that without me seeing it the shell is actually creating an object similar to the buffered reader object. Its just something id like to understand better??? Oh and please dont bog me down with heavy programming lanuage im just a curious begiinner

Python does do quite a lot of clever stuff behind the scenes, however in this case I suspect it takes a much more straight forward approach than creating hidden objects and simply writes the prompt to the standard outputs stream and reads the reply from the standard input.

I agree with your view about Java it seems to makes things complicated for the sake of being a "pure" OOP language.

---

### Post by CaptainMark on 2011-02-16
> **worksofcraft said:**
> I agree with your view about Java it seems to makes things complicated for the sake of being a "pure" OOP language.
Haha yeah definately my point, EVERYTHING is done with objects and classes in java, even stuff that seemed so basic in python, at least its helped my oop in python improve

---

### Post by Reiger on 2011-02-16
You are not actually writing remotely equivalent code. This is closer ...
```

import java.io.*;

public class Program {
  public static void main(String[] args) throws IOException {
     BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
     System.out.printf("How many bananas can you eat?%n: ");
     String bananas=br.readLine();
     System.out.print(bananas);
  }
}

```
... but actually, this could be closer still:

```

public class Program {
  public static void main(String[] args) {
    java.io.Console con = System.console();
    String bananas = con.readLine("How many bananas can you eat?%n: ");
    con.format("%s", bananas);
  }
}

```

By the by there is a bug in your Python program, at least it would be a bug once this module were part of a bigger program. Your Python should actually be checking if it *is* the main module:
```

if __name__ = "__main__":
 # only start the program here

```
That Python code is actually much the same thing as the "public static void main(String[] args)" method in Java. Convention. In Python the interpreter always starts your code so you are responsible for the check; whereas in Java the JVM only starts code it is instructed to and then it will look for the magic method and invoke it with the commandline arguments.

---

### Post by forrestcupp on 2011-02-16
Python is meant to be a very simple language. You can't really judge other languages by Python. Just be glad that Java has garbage collection, which makes it much easier than C++.

---

### Post by nvteighen on 2011-02-17
Well, Java is a static-typed language... That adds a lot of verbosity and also a lot of mechanisms in order to make runtime behaivor be checkable at compile-time. Also, there's a point where C-based syntax becomes more an obstacle despite the alleged advantage of similarity with other languages.

Common Lisp is a pure OOP language and isn't like this. (Ok, maybe not a fair comparison as Lisp has almost no syntax...).

---

### Post by wmcbrine on 2011-02-17
> **Reiger said:**
> By the by there is a bug in your Python program, at least it would be a bug once this module were part of a bigger program.No, that's not a bug. Not everything *has* to be able to work as a module in Python.

---

### Post by CptPicard on 2011-02-17
> **forrestcupp said:**
> Python is meant to be a very simple language.

I'd say this is an understatement of Python -- I'd rather say  it is meant to be a language that demonstrates a very clean language design, and the ideas you get from dynamic typing which cut back on declarations a *lot*.

Simple perhaps in some sense, but only in that sense that it is more efficient at expressing things that may not be simple.

---

### Post by forrestcupp on 2011-02-17
> **CptPicard said:**
> I'd say this is an understatement of Python -- I'd rather say  it is meant to be a language that demonstrates a very clean language design, and the ideas you get from dynamic typing which cut back on declarations a *lot*.

Simple perhaps in some sense, but only in that sense that it is more efficient at expressing things that may not be simple.

One way to look at it is that the more a programming language does for you, the less control you have. But there are a lot of times you don't really need that kind of control.

It's all about what you need for your project. I've used Python for some projects and C++ for others that had that need. I recently used Visual Basic because that was the best tool for that job. Now I'm working through the Android SDK, so I have to use Java.

I love Python, but honestly, there aren't that many times in the real world that Python is the right tool for the job. Not because it's inferior, but because of the big popularity contest.

---

### Post by CptPicard on 2011-02-18
> **forrestcupp said:**
> One way to look at it is that the more a programming language does for you, the less control you have. But there are a lot of times you don't really need that kind of control.

Yes, that's the low- vs. high-level language debate. I find it difficult to believe the claims that the low-level building blocks would somehow magically grant their user the ability to actually write everything from scratch for some given problem domain (and apparently even more so because they "give more control"), especially considering that the difference between the two implementations is that the high-level language's *implementation* is just a mapping between two computationally *equivalent* representations of the problem *that has nothing to do with the actual problem* in the theoretical sense, because otherwise, the two would not be computationally equivalent!

Think about it. 

On the other hand, high-level languages can give you abstract building blocks (btw, why do low-level programmers wield "abstract" as a curse word?) that shape your entire thinking of "what is" in the computable sphere of functions in general; once you understand that part, the low-level implementation in terms of some architecture is mere implementation detail.

---

### Post by forrestcupp on 2011-02-18
> **CptPicard said:**
> Yes, that's the low- vs. high-level language debate. I find it difficult to believe the claims that the low-level building blocks would somehow magically grant their user the ability to actually write everything from scratch for some given problem domain (and apparently even more so because they "give more control"), especially considering that the difference between the two implementations is that the high-level language's *implementation* is just a mapping between two computationally *equivalent* representations of the problem *that has nothing to do with the actual problem* in the theoretical sense, because otherwise, the two would not be computationally equivalent!


There's a lot more to the debate than that. You can't deny there are speed differences between a program natively compiled by a lower level language and the same one written in a higher level language that uses some kind of interpreter or JIT compiler. Even PyGame is basically a Python wrapper for the SDL library, which was written in C.

But like I said, you use the right tool for the job. Sometimes raw speed isn't what you need. Sometimes you just need to get something done quickly. It's not all about Python or C++; it's about what's needed for the job in front of you.

---

### Post by Some Penguin on 2011-02-18
The Reader/Stream division is actually a very UNIX-y setup; i.e. they're very similar to pipes.  An InputStreamReader doesn't particularly care what InputStream you pass it, and can interpret it according to your specified charset encoding (since platform encoding might be != intended encoding of file might be != internal Java character representation).   The underlying InputStream might instead be from an getContent() call of an HttpEntity (and thus from an active HTTP connection); the reader doesn't care.  

Projects at Apache, SF, Google et al can then compose multiple base classes into more convenient wrappers if deemed appropriate.  *shrug*  It would be fairly simple to write a Function<InputStream, Iterable<String>> (where Function is from Google's Guava package; it's a very basic interface where Function<S,T> has a method 'apply' that accepts an S and returns a T) if for instance you read Strings a lot; the one catch would be that the returned object should implement both Closeable and Iterable, and it's not a bad idea to have a CloseableIterable interface to emphasize this.

---

### Post by CptPicard on 2011-02-18
> **forrestcupp said:**
> There's a lot more to the debate than that. You can't deny there are speed differences...

No, there is not anything more to the debate, and I'm not denying anything. Execution speed is merely a kind of side-effect of a certain kind of an implementation; as long as you implement something Turing-complete in terms of Turing-complete X, it will run fast on that Turing-complete X. This is not relevant to anything I'm interested in, really.

Computability is a much more abstract phenomenon, and understanding it in general is what I've always been after...

---

