---
title: "Python vs. Java speed difference."
date: 2011-07-13
forum: Programming Talk
---

### Post by stchman on 2011-07-13
Hello all, I read an interesting article that claimed Python's speed in standard output was far greater than Java.  I ran a little test on the same machine.

Java code:
```

public class ConsoleTest {
    public static void main( String[] args ) {
        for ( int i = 0; i < 200000; i++ ) {
            System.out.println( i );
        }
    }
}

```

Python code:
```

for x in xrange( 200000 ):
    print x

```

I ran these two programs and Java's ability to print to the terminal was shall we say about 2X faster than Python.

Now granted this is only one test, but it proved to go Java's way.

---

### Post by juancarlospaco on 2011-07-13
Dude...  its not the same test...

---

### Post by NovaAesa on 2011-07-13
Link to you interesting article? I'm always very skeptical when someone says Python is faster than XYZ language. There are many many great things about Python, but speed isn't one of them.

---

### Post by TwoEars on 2011-07-13
> **stchman said:**
> Hello all, I read an interesting article that claimed Python's speed in standard output was far greater than Java.  I ran a little test on the same machine.

Java code:
```

public class ConsoleTest {
    public static void main( String[] args ) {
        for ( int i = 0; i < 200000; i++ ) {
            System.out.println( i );
        }
    }
}

```

Python code:
```

for x in xrange( 200000 ):
    print x

```

I ran these two programs and Java's ability to print to the terminal was shall we say about 2X faster than Python.

Now granted this is only one test, but it proved to go Java's way.

Actually, it proves nothing. It's a given that Java is faster (btw, your testing "system" is not through nor reliable) - you don't use standard Python for speed, you use it for readability and rapid prototyping.

If you're using Python for execution speed, you're doing it wrong. Different languages are suited for different things. Python is not suited for execution speed, but it is for development speed ;)

Java is not the "end of all languages", and there are many reasons to dislike it, and many to like it. The same applies for every language.

---

### Post by Marlonsm on 2011-07-13
I don't know much Java, so I can't test it too, but there are many languages that beat Python in speed, including C (and variants).
The point of Python isn't really about speed of executing, it's about simplicity when you're developing the code.
As your own test shows, you needed 7 lines of code in Java, with lots of symbols and marks, to do what Python did in 2 simple lines.

The language of choice depends heavily on you goal.

Some time ago I needed to do a script to rename hundreds of files in a folder, giving each one a random number. For this, I used Python, mostly because it's the language I know the best, but also because I didn't really need to save those milliseconds of processing time, I'd rather save time while coding it.
Sure, a good Java programmer can code faster than I do in Python, but the point is that, with my limited knowledge of programming, Python was the best choice this time.
But for programs that need fast executing, Python isn't the best choice.

---

### Post by Arndt on 2011-07-13
> **stchman said:**
> Hello all, I read an interesting article that claimed Python's speed in standard output was far greater than Java.  I ran a little test on the same machine.

Java code:
```

public class ConsoleTest {
    public static void main( String[] args ) {
        for ( int i = 0; i < 200000; i++ ) {
            System.out.println( i );
        }
    }
}

```

Python code:
```

for x in xrange( 200000 ):
    print x

```

I ran these two programs and Java's ability to print to the terminal was shall we say about 2X faster than Python.

Now granted this is only one test, but it proved to go Java's way.

You should also test the loop speed itself, without doing anything in the loop.

---

### Post by Marlonsm on 2011-07-13
> **Arndt said:**
> You should also test the loop speed itself, without doing anything in the loop.

I tested the loop in Python, it runs so fast that wouldn't change the results.

---

### Post by akabigbro on 2011-07-13
time python consoletest.py

1...

real	0m3.017s
user	0m0.340s
sys	0m0.460s

2...

real	0m3.206s
user	0m0.400s
sys	0m0.390s

3...

real	0m3.247s
user	0m0.460s
sys	0m0.370s


time java ConsoleTest

1...

real	0m3.386s
user	0m1.170s
sys	0m0.570s

2...

real	0m3.391s
user	0m1.160s
sys	0m0.570s

3...

real	0m3.371s
user	0m1.170s
sys	0m0.580s

really negligible difference.

---

### Post by cgroza on 2011-07-13
In the Java version, you are simply incrementing an int, in the Python version you use a whole different concept : generator functions. So your test is far from reliable.

---

### Post by TwoEars on 2011-07-13
> **akabigbro said:**
> time python consoletest.py

1...

real	0m3.017s
user	0m0.340s
sys	0m0.460s

2...

real	0m3.206s
user	0m0.400s
sys	0m0.390s

3...

real	0m3.247s
user	0m0.460s
sys	0m0.370s


time java ConsoleTest

1...

real	0m3.386s
user	0m1.170s
sys	0m0.570s

2...

real	0m3.391s
user	0m1.160s
sys	0m0.570s

3...

real	0m3.371s
user	0m1.170s
sys	0m0.580s

really negligible difference.

In this case, most of the speed is in IO (in fact, almost all of it). Java isn't the fastest with IO with terminals. Java will also be slowed down in this case by the large startup overhead.

Anyway, as previously stated, it's a poor test.
For a better comparison, check out - [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

---

### Post by juancarlospaco on 2011-07-14
> **cgroza said:**
> in the java version, you are simply incrementing an int, in the python version you use a whole different concept : Generator functions. So your test is far from reliable.

+1

---

### Post by igouy on 2011-07-14
> **stchman said:**
> Hello all, I read an interesting article that claimed Python's speed in standard output was far greater than Java.  I ran a little test on the same machine.
Looks like you read the old Glyph Lefkowitz [[COLOR="Blue"]_nonsense_[/COLOR]]("http://www.reddit.com/r/programming/comments/24ynh/python_vs_java_an_update_to_a_subjective_speed/c257hz"), which now begins - "[[COLOR="Blue"]_Please Note:_[/COLOR]]("http://www.twistedmatrix.com/users/glyph/rant/python-vs-java.html") this page was last updated in 2000. Its conclusions are no longer relevant. **Its data was dubious at the time and flat-out wrong now.** I have no intention to update it, but I will gladly link to something more recent."

---

### Post by Shin_Gouki2501 on 2011-07-14
> **TwoEars said:**
> In this case, most of the speed is in IO (in fact, almost all of it). Java isn't the fastest with IO with terminals. Java will also be slowed down in this case by the large startup overhead.

Anyway, as previously stated, it's a poor test.
For a better comparison, check out - [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

I totally agree THIS is 'real' benchmarking: [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

also note, scala ( which offers nice scripitng abilitys TOO) and java's place :)

---

### Post by igouy on 2011-07-14
> **akabigbro said:**
> time python consoletest.py ... really negligible difference.
[LIST=1]
[*]Maybe 99% of the measured time is taken by the terminal window :-) 

Instead try ```
time python consoletest.py > /dev/null
```

[*]Java is forcing flush on every println, just tell it not to!

```
import java.io.*;
public class ConsoleTest {
    public static void main(String[] args) {
        PrintWriter out = new PrintWriter(System.out,false);
        for (int i = 0; i < 200000; i++) out.println(i);
    }
}
```

[*]JVM startup will take a few tenths of a second, so to understand how much time is being taken to do the work of the Java program measure longer running programs -

200,000
```
$ time python ConsoleTest.py > /dev/null
real	0m0.133s
user	0m0.130s
sys	0m0.000s

$ time /usr/local/src/jdk1.6.0_25/bin/java ConsoleTest > /dev/null
real	0m0.173s
user	0m0.220s
sys	0m0.060s
```

[*]200,000,000
```
$ time python ConsoleTest.py > /dev/null
real	1m47.895s
user	1m47.790s
sys	0m0.070s

$ time /usr/local/src/jdk1.6.0_25/bin/java ConsoleTest > /dev/null
real	0m59.334s
user	0m59.760s
sys	0m0.150s
```

[*]Why would you expect anything other than a "really negligible difference" when all the programs do is print a single line of text, over and over and over ... :-)

[/LIST]

---

### Post by cgroza on 2011-07-14
> **igouy said:**
> 
[LIST=1]
[*]Why would you expect anything other than a "really negligible difference" when all the programs do is print a single line of text, over and over and over ... :-)
[/LIST]

No wonder, a Java loop runs faster than a python loop... You should get that python on a JIT, and then we're talking. :P

---

### Post by idoitprone on 2011-07-14
Dude, do you realize java can almost keep up with C++....Java just have a high overhead.

Never compare a compiled language with a scripting one. There is usually no comparison

I hope this thread does not become a programming flame war

---

