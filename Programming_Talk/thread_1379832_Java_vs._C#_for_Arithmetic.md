---
title: "Java vs. C# for Arithmetic"
date: 2010-01-13
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-01-13
If one was to write a program that required performance, but was pretty simple, just a bunch of arithmetic, which language would be faster - Java or C#?  I know the answer is C or maybe Fortran, but if limited to Java or C#, which would be faster.  Assume the problem just involves floating point addition, subtraction, and division.

Yeah...I got into a debate over computer languages earlier today.  Don't write a program to benchmark, I would like to know the reason why one would be faster than the other.

---

### Post by worseisworser on 2010-01-13
> **SNYP40A1 said:**
> If one was to write a program that required performance, but was pretty simple, just a bunch of arithmetic, which language would be faster - Java or C#?  I know the answer is C or maybe Fortran, but if limited to Java or C#, which would be faster.  Assume the problem just involves floating point addition, subtraction, and division.

Yeah...I got into a debate over computer languages earlier today.  Don't write a program to benchmark, I would like to know the reason why one would be faster than the other.

A reason would be one language having a better compiler and/or run-time than the other. If this sounds obvious; think about the question (edit: but recall that compilers and run-times are *not* trivial or obvious though; so that's the disconnect right there). :}

Also consider that in C; you are the one doing the compiling instead of the computer. That is to say that the same thing applies; the actor just happens to be a human that to a larger extent repeatedly dictates things directly instead of creating or using a computer program (a compiler) that will make the same decisions "for" him (often makes sense considering that the decision making is excruciatingly boring and repetitive *once understood*).

Not testing, benchmarking or profiling really is fail by-default; even just exclusively considering the "simple" set of operations you mention leads to an amazing number of things to consider!

---

### Post by konqueror7 on 2010-01-13
i agree with @worseisworser, its the underlying interpreter/compiler that does the job, and each of these languages got a few alternatives of each,,,i use java most of the time, but also got to use c#, so i got to see a few diff. one thing is operating platforms plays a great role in the performance of these languages. but all in all, it depends on the interpreter/compiler/environment, you don't even notice the performance unless you perform heavy performance test just to see some definitive results... :D

---

### Post by barnex on 2010-01-13
If you go for java, I recommend using sun's jvm for good performance. You can also tweak it with options like -XX:CompileThreshold=1, which will just-in-time compile each function used more than 1 time. This makes the start-up time longer but after the just-in-time-compilation your program will run at nearly native speed.

Also, I've had some luck with gcj, the java-front end of gcc. I've first compiled my sources with javac and then pulled the class files through gcj to get a native executable. I used the gcj option not to check array bounds. In my case ("array intensive" calculations) it gave a 2x speed up. Other typical gcc flags like -O3 can also be passed. (On the downside, multithreading did not work anymore with gcj).

---

### Post by SNYP40A1 on 2010-01-13
> **barnex said:**
> If you go for java, I recommend using sun's jvm for good performance. You can also tweak it with options like -XX:CompileThreshold=1, which will just-in-time compile each function used more than 1 time. This makes the start-up time longer but after the just-in-time-compilation your program will run at nearly native speed.

Also, I've had some luck with gcj, the java-front end of gcc. I've first compiled my sources with javac and then pulled the class files through gcj to get a native executable. I used the gcj option not to check array bounds. In my case ("array intensive" calculations) it gave a 2x speed up. Other typical gcc flags like -O3 can also be passed. (On the downside, multithreading did not work anymore with gcj).

Wait, it's possible to take java class files and compile them to a native executable???  If so, that's quite impressive.  I imagine that it can only handle a subset of the Java language...can it compile Swing too?

konqueror7 and worseisworser, that's basically all I need to know.  I looked at the java vs. C# (or maybe it was Java vs. .NET) wikipedia entry and they never compared performance.  The consensus is that both are worse than C++, but it never really matters.  Even in cases of heavy numerical computation (except for Java where I think some parts are still done in software -- maybe trig) software design is a more dominant factor in performance than language.  Of course, that's a bit ambiguous because it's possible to write a really terrible and inefficient program for a simple task.

---

### Post by crom.osec on 2010-01-13
I've made extensive tests in C# and I can tell that it has same speed as C++ but only after the types are loaded first time in memory (on first use they are compiled so this results in a delay).
I didn't made same tests in Java but from what I've seen is slow and consume a lot of memory.

As far as I know, main difference between Java, C# and C++ is that:

- Java executable contains in fact the high level programmer code (archived) and this code is interpreted by Java Virtual Machine which translate it into commands to the machine, every time when the code is called (this is slow every time compared to C++ or C#).

- C# executable contains an intermediate language which is not machine code but also not programmer code. This code is compiled into machine code at first time when is accessed and next calls to same region of code are done in the machine code. This results in delay on a first time when is run (the time required to compile the intermediate code) and second and so on... calls have no delay. They have same speed as in C++.

- C++ executable contains machine code

---

### Post by CptPicard on 2010-01-13
> **crom.osec said:**
> I've made extensive tests in C# and I can tell that it has same speed as C++

Your C++ probably sucks, is not compiled with optimizations on, or your benchmark does not represent a good comparison. It *is* faster (although by a manageably small constant factor most times), and anyone claiming otherwise isn't testing enough.

My own number-crunching code which is fairly intense and in Java is typically about 50%-100% slower in typical test cases. This difference usually comes from the C++ compiler being able to inline a lot more stuff, so much more ends up happening in registers. I don't know about C#'s behaviour here, but I would suppose that as the general architecture is the same as Java's, a lot of things are objects at end of references, which results in a lot more messing about with the RAM. This is a bottleneck that is hard to get around.

Otherwise, the stuff that does end up in the registers ought to be optimizable pretty much all the same.

> 
I didn't made same tests in Java but from what I've seen is slow and consume a lot of memory.

Well, analogously, I have never been a C# user but considering the above: Java's and C#'s basic architectures are the same, JVM is far more mature and very optimized, and what *I* have seen is the fastest of the non-native languages...

The JVM's memory footprint tends to be larger, that is true.


> 
- Java executable contains in fact the high level programmer code...

Wrong. Both C# and Java are bytecode compiled first and then JIT-compiled into machine-specific instructions before execution. (Well, I assume C# has borrowed JIT-compilation from Java :) )

---

### Post by crom.osec on 2010-01-13
The tests that I've made were generally like this:
- Implement same algorithm in C# and C++ (starting from simple loops to some very complex algorithms for chemistry formulas computing and depicting)
- Run the algorithms in a loop for several iterations, providing identical set of parameters. In order to check the algorithms without caring about the time required by C# to compile the intermediate code I've called first the algorithms once with predefined parameters designed to cover all paths and then executed the loop checking the system time of start and of end.
- The C++ executable was in Release version with full optimisations.
- The loop count was usually starting from 50 (for long time computing algorithms) to 100.000 for fast algorithms.

The time that was obtained in C++ was an average of 0.9 from the time obtained in C# so from my point of view is safe to assume that they have same speed.
All the tests were run on a windows XP machine, no intervention made on machine during the tests and they were only computing tests (without any visual)

"- Java executable contains in fact the high level programmer code... "
My mistake if is not true this. 
I've never studied Java as developer but I've used many Java applications and they had one common point: they were slow.

---

### Post by Bad Sector on 2010-01-13
Actually what is slow in Java is Swing, not Java itself. If you use a more lightweight (but much less capable - Swing might be slow but it can do almost anything a programmer might need and its extremely flexible and extendable) you won't notice much of a difference. Assuming of course the code is written by a good programmer who knows what 'code optimization' is all about and understands the specialities of the JVM (hint: writing fast code in Java is not the same as writing fast code in C/C++).

As for C# vs Java, and assuming we're talking about the major VM implementations (Sun HotSpot for JVM and Microsoft .NET for C#), i would expect the performance of both to be about the same. However since these languages are not really compiled to machine code and the "executables" contain a lot of metadata which can help the VM optimize stuff better, i believe that the performance will differ A LOT between VMs (well, just check the horrible performance of gij for example...).

As for C# vs Java, i would recommend Java since there are much better tools for it available in Linux (i'm talking about Eclipse of course).

---

### Post by cszikszoy on 2010-01-13
> **Bad Sector said:**
> As for C# vs Java, i would recommend Java since there are much better tools for it available in Linux (i'm talking about Eclipse of course).

To play the advocate here... MonoDevelop is a fantastic IDE, and I prefer it to eclipse.

---

### Post by KarlIvan on 2010-01-13
I cant believe this is even an argument...c# by far would be a million times faster (obviously an exaggeration...lets not start flaming) than java

dont get me wrong, i looooovvvvvve java...that being said though

java runs on top of the jvm...and there is massive overhead with java. a simple one line statement in java gets broken up into potentially several dozen or so lines by the compiler. so while it is much easier to program in something like java, rather than c, java provides a much larger overhead, if nothing else because of the jvm.

now, as far as c# goes, im talking out my a#@, lol. i dont know much about c#, other than what ive heard about it, i havent had an opportunity to write in c# yet. that being said, I dont need to know it, or run benchmarks to know, simply because i know how sophisticated java is when it comes to breaking down and running your source code. its great for running really complex programs, but i would recommend something simpler if youre only doing something simple. and if c, or c++ isnt an option, then i can only assume that c# would have much less overhead that java.

that being said, if its just a simple task anyway, then what are you going to do with that extra .001 seconds (just a random number)? if youre not calculating precision time for the space shuttle, or a missile defense system, then this time saving is really unneccessary. write in the language that youre most comfortable with, and make sure its good code instead :)

---

### Post by caelestis2 on 2010-01-13
> **crom.osec said:**
> 
I've never studied Java as developer but I've used many Java applications and they had one common point: they were slow.

Java is not that slow. On my system, arithmetic in C++ vs Java performance is a 3:5 ratio. I blame Swing

C++
[PHP]#include <iostream>
#include <ctime>

int main(int argc, char **argv) {
	std::cout << "How many iterations would you like to run? ";
	long int iterations;
	std::cin >> iterations;

	double pi = 0;
	std::clock_t start, end;

	start = std::clock();
	// pi/4 = 1-1/3+1/5-1/7...
	for (long int i = 0; i < iterations; ++i)
		pi += 1.0/(1+4*i)-1.0/(3+4*i);
	pi *= 4;
	end = std::clock();

	std::cout.precision(30);
	std::cout << pi << std::endl;
	std::cout.precision(4);
	std::cout << "Calculated in " << ((double)(end-start))/CLOCKS_PER_SEC << " seconds.\n";
	return 0;
}[/PHP]

Java
[PHP]import java.util.Scanner;

public class main {
	public static void main(String [] args) {
		System.out.print("How many iterations would you like to run? ");
		long iterations;
		iterations = new Scanner(System.in).nextLong();
		
		double pi = 0;
		long start = System.currentTimeMillis();
		
		// pi/4 = 1-1/3+1/5-1/7...
		for (long i = 0; i < iterations; ++i)
			pi += 1.0/(1+4*i)-1.0/(3+4*i);
		pi *= 4;
		long end = System.currentTimeMillis();

		System.out.println(pi);
		System.out.println("Calculated in " + (end-start)/1000.0 + " seconds");
	}
}[/PHP]

Of course I'm not that good in both languages. :neutral:

---

