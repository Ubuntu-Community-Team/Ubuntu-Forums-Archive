---
title: "[SOLVED] Why is C slower than Java?"
date: 2013-03-08
forum: Programming Talk
---

### Post by usernamer on 2013-03-08
I was always told how C is faster than Java, so I decided to write a few very basic programs to see how much slower it is (if at all) at using basic commands like if, for etc. I compiled my code, and Java was significantly faster (although, as always takes longer to compile). Does Java have some sort of extra stuff built into its for loop so that it can do this more efficiently or something?

Here's my code...

```
public class speed {
    public static void main(String[] args) {
         int count;
         for( count = 0; count <= 1000000000; count++ ) {

         }
         System.out.print( "\n" +count+ "\n" );
     }
}
```

and for C...
```

#include <stdio.h>

int main(void)
{
         int count;
         for( count = 0; count <= 1000000000; count++ ) {
    
         }
         printf( "\n%d\n" ,count );

         return 0;
}
```

Also, does anyone know how to indent your code here? (Since I tried, but it ignores the spaces at the start of each line when you post).

Cheers.

---

### Post by SledgeHammer_999 on 2013-03-08
Probably the printf slows down the output which makes the program to execute slower.

Put your code inside [ code][ /code] tags or [ php][/ php] tags next time.

---

### Post by usernamer on 2013-03-08
Cheers for the input, but I doubt it since the printf is outside the for loop, and the C program once compiled takes around 3 seconds to print, and the java one takes around 1/10th of a second

---

### Post by amingv on 2013-03-08
javac has all optimizations turned on by default whereas gcc doesn't. This means java isn't actually running the loop at all (i.e. it ignores the empty loop).

If you compile your C program like this:

```
gcc -O3 -o speed speed.c # -O3 enables all optimizations
```

Then it just blows the java program out of the water* :)

Either that or give the programs something nontrivial to do while they're inside of the loop so that they don't just skip it (for instance, output the value of *count*)

You can look here for more info on gcc optimization flags: [http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html)

*To be fair: java has some additional overhead because it has to load the jvm, for this particular case I expect the speed for both programs should be pretty close. This isn't much of a speed test, really :)

---

### Post by usernamer on 2013-03-08
Thanks, I suspected it could be something roughly like that... I did originally have more 0's, but the java compiler complained at me :(

---

### Post by usernamer on 2013-03-08
I did try to output the value of count in the for loop as well before (and again just now with optimisations enabled), and java was still around a second quicker.

---

### Post by SledgeHammer_999 on 2013-03-08
> **usernamer said:**
> Cheers for the input, but I doubt it since the printf is outside the for loop, and the C program once compiled takes around 3 seconds to print, and the java one takes around 1/10th of a second

Well, I missed that since you hadn't used code tags... (hint php tags highlight syntax regardless of programming language used)

---

### Post by trent.josephsen on 2013-03-08
I for one refuse to use php tags because marking up non-php code with "PHP" violates the structure of the markup. Like using <blockquote> to indent something that's not a quote. I'd use 'em if they were called something different. (Code tags are good though.)

---

### Post by r-senior on 2013-03-09
Java usually benchmarks around 110-120% of the execution time of C and C++ for equivalent code.

I've got some Eratosthenes sieve programs somewhere that are consistent with this. Exact same algorithm in C, C++, Java, Pascal and Python. Still not a perfect benchmark but more realistic than an empty loop. I'll post them later if you want to play with them.

Speed isn't everything of course; my Python sieve stumbles in around 20-30 times the execution time of C but it's still a great language and quick enough for most general purpose stuff. A GTK+ program written in Python isn't noticeably sluggish compared to one written in C for example.

---

### Post by woxuxow on 2013-03-09
C is so faster than java
java is the slowest programming language i have ever wrote program in

---

### Post by usernamer on 2013-03-09
I'm sure it is generally, but with this example of a for loop and printing a number each time within that loop, it doesn't seem to be the case, which surprised me.

---

### Post by r-senior on 2013-03-09
I don't suggest this is a flawless benchmark, it's no more than idle amusement ...

```

$ make benchmark
[COLOR="#FF0000"]time ./eratc
C

real	0m9.573s
user	0m9.557s
sys	0m0.008s[/COLOR]
[COLOR="#008000"]time ./eratcxx
C++

real	0m10.580s
user	0m10.557s
sys	0m0.012s[/COLOR]
[COLOR="#0000FF"]time ./eratp
Pascal

real	0m11.969s
user	0m11.941s
sys	0m0.016s[/COLOR]
[COLOR="#800080"]time java Erat
Java

real	0m11.220s
user	0m11.245s
sys	0m0.076s[/COLOR]
[COLOR="#8B4513"]time ./eratpy.py
Python (only 1/10 of the iterations)

real	0m36.453s
user	0m36.350s
sys	0m0.056s
[/COLOR]
```

Note that the Python version only runs 1/10 of the iterations, so you could extrapolate that to ~365s. It can be compiled of course, if anyone wants to try that (or to eliminate the sqrt). Source code attached -- you'll need Free Pascal installed to try the Pascal, or just remove it from the Makefile.

[ATTACH]239971[/ATTACH]

---

### Post by ofnuts on 2013-03-09
> **MustafaJF said:**
> C is so faster than java
java is the slowest programming language i have ever wrote program in
Then you haven't tried many...

---

### Post by ofnuts on 2013-03-09
> **r-senior said:**
> Java usually benchmarks around 110-120% of the execution time of C and C++ for equivalent code.

I've got some Eratosthenes sieve programs somewhere that are consistent with this. Exact same algorithm in C, C++, Java, Pascal and Python. Still not a perfect benchmark but more realistic than an empty loop. I'll post them later if you want to play with them.
I have converted a prime factor extraction from C to Java and Java is more like 80% slower than C for this. But then there are different Java runtimes (using IBM JDK 1.6).

---

### Post by woxuxow on 2013-03-09
> **ofnuts said:**
> Then you haven't tried many...

If "C - C++ - C# - JAVA - Pascal - ASP.net - ASP classic" are not many
yeah, you are right.

---

### Post by trent.josephsen on 2013-03-09
I think ofnuts meant that you really don't have far to look to find a language implementation that underperforms Java (for some applications), so saying it's the slowest thing you've ever used says more about the range of your experience than the limitations of Java itself. (It probably also says something about the kind of programs you write; Java performs better with straight mathematics than heavy text manipulation, for instance.)

Python and LabVIEW come to mind as fairly popular languages that I've used that may underperform in certain areas when compared to Java.

---

### Post by woxuxow on 2013-03-10
dear trent.josephsen it dosn`t matter what our frient meant : the java, the program i written in java or ... 
java is slow, maybe not the slowest but it is slower than C - C++ - Python - even C#

---

### Post by KdotJ on 2013-03-10
> **MustafaJF said:**
> dear trent.josephsen it dosn`t matter what our frient meant : the java, the program i written in java or ... 
java is slow, maybe not the slowest but it is slower than C - C++ - Python - even C#


Then perhaps you need to go back and redesign that Java program. I struggle to see how a python implementation of a program is faster than the same program implemented in Java.

---

### Post by r-senior on 2013-03-10
Could you give us a timed example where Python runs faster than an equivalent Java program written with a modern JDK and JVM?

---

### Post by CptPicard on 2013-03-11
I honestly would love to get some examples as well. :) I have written my fair share of number-crunchers and algorithm implementations in my time in all of Java, C and Python, and generally Java is almost always performant enough not to justify implementation in C because of Java's speed of development, while Python likewise tends to choke very quickly indeed...

---

### Post by woxuxow on 2013-03-11
I`m not programing in java or python anymore 
if want the same program that has been written in java or python in c++ then i`ll do it.

---

