---
title: "Simple Java vs Python question...I think"
date: 2010-06-18
forum: Programming Talk
---

### Post by antman8969 on 2010-06-18
Ok so my friend was playing around on the super computer at his summer job, testing out the processing power with simple, useless scripts so I decided to do the same. Basically I just timed the same function in Python and Java.

Python code:

```
import timeit

def test():
    list1 = []
    list2 = []
    list3 = []
    
    for i in range(5000000):
        list1.append(i)
        list2.append(i)
    
    for i in range(5000000):
        list3.append( list1[i] + list2[i] )
    
    print sum(list2), " ", sum(list1)
    print sum(list3)
    
def main():
    t = timeit.Timer("test.test()", "import test")
    
    time = t.timeit(1)
    print "%0.3f seconds"%time
main()
```

Java code:

```
public class Test {

	public static void main(String [] args){
		long startTime = System.nanoTime();
		long[] list1 = new long[5000000];
		long[] list2 = new long[5000000];
		long[] list3 = new long[5000000];
		
		for(long i = 0; i < 5000000; i++){
			list1[(int)i] = i;
			list2[(int)i] = i;
		}
		
		for(long i = 0; i < 5000000; i++){
			list3[(int)i] = list1[(int)i] + list2[(int)i];
		}
		
		
		long sum2 = 0;
		for(long i = 0; i < 5000000; i++){
			sum2 += list2[(int)i];
		}
		System.out.print(sum2 + "   ");
		
		long sum1 = 0;
		for(long i = 0; i < 5000000; i++){
			sum1 += list1[(int)i];
		}
		System.out.println(sum1+"   ");
		
		
		long sum = 0;
		for(long i = 0; i < 5000000; i++){
			sum += list3[(int)i];
		}
		System.out.println(sum+"\n");
		long endTime = System.nanoTime();
		System.out.println("This program took: "+ ((endTime - startTime)/1000000000.0) + " seconds");
	}
	
}
```

The Python code takes on average around 6 seconds to complete, while the Java code takes .3 seconds.

Is this a mistake in the code I wrote or is there another reason?

---

### Post by Reiger on 2010-06-18
You are not using equivalent code, for starters range() returns the complete list...

---

### Post by Bachstelze on 2010-06-18
> **Reiger said:**
> You are not using equivalent code, for starters range() returns the complete list...

Depends on the Python version. It does not in Python 3.

---

### Post by antman8969 on 2010-06-18
> **Reiger said:**
> You are not using equivalent code, for starters range() returns the complete list...

I'm a beginner, could you elaborate a little more?

---

### Post by Bachstelze on 2010-06-18
> **antman8969 said:**
> I'm a beginner, could you elaborate a little more?

In Python 2, range(10) for example returns [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]. In your code, you have range(5000000) so it must create, allocate memory for, and browse a five-million-element list. This will of course be very inefficient.

Assuming you are using Python 2, of course.

---

### Post by antman8969 on 2010-06-18
> **Bachstelze said:**
> In Python 2, range(10) for example returns [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]. In your code, you have range(5000000) so it must create, allocate memory for, and browse a five-million-element list. This will of course be very inefficient.

Assuming you are using Python 2, of course.

yea I'm using 2.6
I still don't see why that would make the code take 5 seconds longer. Isn't that essentially what I'm doing in java with:

```
int[] list = new int[5000000];
```

---

### Post by gmjs on 2010-06-18
You can use the 'xrange' function rather than 'range' in Python 2 to avoid the excessive memory allocation problem.

---

### Post by antman8969 on 2010-06-18
> **gmjs said:**
> You can use the 'xrange' function rather than 'range' in Python 2 to avoid the excessive memory allocation problem.

lol well that took a half second off the time, but still about 4 seconds longer. Anything else I could be doing?

---

### Post by schauerlich on 2010-06-18
In the python version, you repeatedly append to a list, which means every so often it has to resize the list. In the Java version you allocate the list at the very start, and then only initialize the values.

---

### Post by StephenF on 2010-06-18
> **antman8969 said:**
> Anything else I could be doing?
Well, this task is very artificial for one thing and for another to create the lists and their contents in Python 2.6 you only need.
```

from itertools import izip

list1 = range(5000000)
list2 = range(5000000)
list3 = [x[0] + x[1] for x in izip(list1, list2)]

```
I bet that shaves off some time.

---

### Post by antman8969 on 2010-06-18
> **StephenF said:**
> Well, this task is very artificial for one thing and for another to create the lists and their contents in Python 2.6 you only need.
```

from itertools import izip

list1 = range(5000000)
list2 = range(5000000)
list3 = [x[0] + x[1] for x in izip(list1, list2)]

```
I bet that shaves off some time.

good suggestion. It's now down to three seconds lol. Still 3 seconds longer than java tho.  From what I can see the initial problem stemmed from not understanding exactly what the python functions were doing. 

Java only does what I tell it, so when I make a list and allocate memory for it, thats all it does. I thought I knew python better than java, but I guess I don't know whats going on behind the scenes

---

### Post by StephenF on 2010-06-19
Java is half way between a compiled and an interpreted language while Python supports code introspection and modification _at run time_. There is a trade-off between flexibility and speed. Clearly Python is not a good choice for filling huge arrays with sequential numerical data.

Supposing the aim of the exercise was to get the results and not worry about how they were attained:
```

    sum1 = sum(xrange(5000000))
    print sum1, " ", sum1
    print sum1 * 2

```
In this example no array was allocated or filled but the computation was achieved regardless.

I make it 0.67 seconds.

---

### Post by Queue29 on 2010-06-19
> **StephenF said:**
> Java is half way between a compiled and an interpreted language while Python supports code introspection and modification _at run time_. There is a trade-off between flexibility and speed. Clearly Python is not a good choice for filling huge arrays with sequential numerical data.

Supposing the aim of the exercise was to get the results and not worry about how they were attained:
```

    sum1 = sum(xrange(5000000))
    print sum1, " ", sum1
    print sum1 * 2

```
In this example no array was allocated or filled but the computation was achieved regardless.

I make it 0.67 seconds.

If you're going to do that, I may as well do this:

```
System.out.println("12499997500000   12499997500000");
System.out.println("24999995000000");
System.out.println("0.00 seconds");
```

Python is slow. There are no iffs, ands, or buts about it. 

[http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=python&lang2=java](http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=python&lang2=java)

---

### Post by Shin_Gouki2501 on 2010-06-19
nice to see some people ( in a linux forum! :O) acknowledge/ realise the strength of java. And if the jvm evolves even further : [http://blog.headius.com/2010/06/my-short-list-of-key-missing-jvm.html](http://blog.headius.com/2010/06/my-short-list-of-key-missing-jvm.html)
It might be even more useful to Linux than it is today!

---

### Post by schauerlich on 2010-06-19
> **Queue29 said:**
> If you're going to do that, I may as well do this:

```
System.out.println("12499997500000   12499997500000");
System.out.println("24999995000000");
System.out.println("0.00 seconds");
``` There's no calculation going on there, though. The python version did the calculation, it just did it more efficiently (with generators).

> Python is slow. There are no iffs, ands, or buts about it. 
Relatively, yeah.

---

### Post by Unterseeboot_234 on 2010-06-19
Yeah, it surprised me, but python was way down in the list of language benchmark testing of any google site you search for. eg:
[http://shootout.alioth.debian.org/u32/which-programming-languages-are-fastest.php]("http://shootout.alioth.debian.org/u32/which-programming-languages-are-fastest.php")

And when you want to crunch numbers, python is great for overtime pay, but terrible for contract work.

Remarkable, GNU g++ / gCC hold their own in racehorse comparisons if we speak of a variety of tasks. They still use Fortran on the super computers, and for a reason.

---

### Post by slavik on 2010-06-19
hadoop is written in java.
google's mapreduce is written in c++ with bindings to python.

the greatest issue in super computing is I/O. I/O is slow. when you have a cluster and a gbit network between all nodes and switches powerful enough to switch all ports in realtime (backplane switching at gbit * number of gbit ports), it is still not fast enough to move data when you are I/O bound.

Take amount of one work unit - B bits and see how long it takes to process it - T seconds. you now have a processing rate of B/T. Multiply this by 1/T (x). You now have xB/1 sec. xB meaning how many bits you process per second. if we consider network latency to be insignificant (otherwise it's difficult to calculate numbers). if xB is greater than the speed of the network (let's say 1gigabit) then you will be I/O bound by the network, since that is the slowest link. I am not considering disk speed on the assumption that your data is either generated or stored completely in RAM and disk access is not needed (or data is cached in memory already).

then there are the following things you want to do:
1. minimize the need I/O (less talk = more speed)
2. increase xB by more efficient code
3. if possible, bundle/change ifrastructure of data/nodes so that xB is less than the network speed.

With that in mind, I have to say that your code is not 'good'

If you have a multi cpu system, try re-writing your code in C with openmp (gcc 4.12 has openmp). one of the issues in code in general is that it is very serial. (although sometimes series is better than parallel due to locking mechanisms not reacting fast enough).

---

### Post by soltanis on 2010-06-19
Hello C.

[php]
#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>

#define lsize 5000000

int
main(int argc, char** argv) {
    uint64_t* list1, *list2, *list3;
    uint64_t sum, i;

    list1 = malloc(sizeof(uint64_t) * lsize);
    list2 = malloc(sizeof(uint64_t) * lsize);
    list3 = malloc(sizeof(uint64_t) * lsize);

    if (!list1 || !list2 || !list3) {
        perror("malloc");
        exit(1);
    }

#pragma omp parallel for
    for (i = 0; i < lsize; i++) {
        list1[i] = i;
        list2[i] = i;
    }

#pragma omp parallel for
    for (i = 0; i < lsize; i++) {
        list3[i] = list1[i] + list2[i];
    }

    sum = 0;
#pragma omp parallel for
    for (i = 0; i < lsize; i++) {
        sum += list2[i];
    }
    printf("%ld   ", sum);

    sum = 0;
#pragma omp parallel for
    for (i = 0; i < lsize; i++) {
        sum += list1[i];
    }
    printf("%ld\n", sum);

    sum = 0;
#pragma omp parallel for
    for (i = 0; i < lsize; i++) {
        sum += list3[i];
    }
    printf("%ld\n", sum);

    return 0;
}
[/php]

Without OpenMP, this thing takes 0.136 real seconds on my system. With OpenMP, that drops to about 0.134 ~ 0.135. In any case, this is not a particularly difficult problem for a computer to actually *do* (which is why it's pretty artificial), but hopefully it's taught you a thing or two about why not to use python in speed-intensive applications (it's best used in things which interact with humans, I think, where its more simple syntax prevails over computation power).

---

### Post by donsy on 2010-06-20
-

---

### Post by schauerlich on 2010-06-20
> **donsy said:**
> it lacks auto increment/decrement

Not sure what you mean by that.

---

### Post by donsy on 2010-06-20
> **schauerlich said:**
> Not sure what you mean by that.

-

---

### Post by wmcbrine on 2010-06-20
> **donsy said:**
> I should have said it lacks the auto increment/decrement operators, as in n++, n--, ++n, --n. I don't consider n += 1 an equivalent.I'm sorry, but that's the silliest objection to Python I've ever seen.

---

### Post by Can+~ on 2010-06-20
> **wmcbrine said:**
> I'm sorry, but that's the silliest objection to Python I've ever seen.

Agreed.

---

### Post by schauerlich on 2010-06-20
> **wmcbrine said:**
> I'm sorry, but that's the silliest objection to Python I've ever seen.

> **Can+~ said:**
> Agreed.

agreement++

also, 90% of the cases where you'd use ++ are replaced by python's for loop.

---

### Post by trent.josephsen on 2010-06-20
> **schauerlich said:**
> agreement++

also, 90% of the cases where you'd use ++ are replaced by python's for loop.

Don't forget about iterators.

---

### Post by LKjell on 2010-06-21
The for loop in python is so hard to use. You sort of have to think another way...

```
for (int i = 0, j = a; i < a ; i++, j--)
    for (int k = i; k < j; k++) 
```

---

### Post by ssam on 2010-06-21
yes python loops are slow. if you are doing anything with numbers you can use numpy though:

```

import numpy
def test2():
    list1 = numpy.arange(5000000)
    list2 = numpy.arange(5000000)

    list3 = list1 + list2
    print list1.sum(), list2.sum()
    print list3.sum()

```
gives me 0.187 seconds

---

### Post by StephenF on 2010-06-21
> **ssam said:**
> yes python loops are slow. if you are doing anything with numbers you can use numpy though:

```

import numpy
def test2():
    list1 = numpy.arange(5000000)
    list2 = numpy.arange(5000000)

    list3 = list1 + list2
    print list1.sum(), list2.sum()
    print list3.sum()

```
gives me 0.187 seconds
Playing rough are we?

Each element of the list when graphed gives y = x or f(x) = x so if we take the anti-derivative so that F' = f then F = x ** 2 / 2 but 5000000 is one higher than the last element in the list so I will make allowance for that as well.
```

def F(x):
    return x ** 2 // 2

def test():
    sum1 = F(5000000 - 1)
    sum2 = F(5000000 - 1) 
    print sum1, " ", sum2
    print sum1 + sum2

```
Run time: 43.8 microseconds. :lolflag:

---

### Post by wmcbrine on 2010-06-21
> **LKjell said:**
> The for loop in python is so hard to use.Just the opposite is true, IMHO. The Python for loop is a far more natural construct than the C-style loop, for most cases where you'd want a loop.

> *You sort of have to think another way...*That much, I agree with.

> ```
for (int i = 0, j = a; i < a ; i++, j--)
    for (int k = i; k < j; k++)
```

I think this is a somewhat contrived example -- being able to initialize and increment/decrement multiple variables in the "for" statement is a cute feature, but not all that common, never actually *needed*, and questionable in terms of readability. Anyway, here's the Python for the above:

```
for i in range(a):
    j = a - i
    for k in range(i, j):
```

---

### Post by michaelcochez on 2010-06-22
I've tried to make a way of closely mimicking the python syntax in Java:
```
for i in range(a):
     j = a - i
     for k in range(i, j):
             print k
```can be written as:
```
for (Integer i : new Range(a)){
    int j = a - i;
    for (Integer k : new Range (i, j)){
        System.out.println(k);
     }
}
```provided this class:
```

import java.util.Iterator;
import java.util.NoSuchElementException;

public class Range implements Iterable<Integer> {
    private final int start;
    private final int end;
    private final int step;

    public Range(int end) {
        this(0, end, 1);
    }

    public Range(int start, int end) {
        this(start, end, 1);
    }

    public Range(int start, int end, int step) {
        this.start = start;
        this.end = end;
        this.step = step;
    }

    @Override
    public Iterator<Integer> iterator() {

        return new Iterator<Integer>() {
            private int nextElement = Range.this.start;

            @Override
            public boolean hasNext() {
                return this.nextElement < Range.this.end;
            }

            @Override
            public Integer next() {
                if (this.nextElement < Range.this.end) {
                    int returnValue = this.nextElement;
                    this.nextElement += Range.this.step;
                    return Integer.valueOf(returnValue);
                } else {
                    throw new NoSuchElementException();
                }
            }

            @Override
            public void remove() {
                throw new UnsupportedOperationException("A range is immutable");
            }
        };
    }
}
```

edit:
Remark that elements of the range are only generated when needed. This range class cannot be used straight away to get a list of integers.

---

### Post by Can+~ on 2010-06-22
> **raf_kig said:**
> And yet you continue to 'enlighten' us with your solid advice instead of asking questions and trying to learn something. Reading your posts I can't decide whether I want to laugh or cry.

We get our fair share of 1337 kiddies around here, they soon learn how to fit.

And, for the OP (I finally read the code carefully): Python's [] are lists, which are being compared to Java's Array, two different data structures altogether. Transversing a list is way more expensive, due to the need of reading the next pointer, instead of, you know, calculating a offset distance from the base.

And if python is slower, so be it, an hour of my life is way more precious that the one millisecond of my processor.

---

### Post by slavik on 2010-06-22
traversing a list is no more expensive than traversing an array. assignment vs. addition. both take almost no time since the data needed is already in L2 cache.

---

### Post by Can+~ on 2010-06-22
> **slavik said:**
> traversing a list is no more expensive than traversing an array. assignment vs. addition. both take almost no time since the data needed is already in L2 cache.

That's... quite a valid point there. Actually, I was referring to this:

[PHP]    for i in range(5000000):
        list1.append(i)[/PHP]

This needs to constantly jump to the end of the list (unless python has something like a end pointer, which probably has) and resize it. Whereas, the Java example had the space already reserved, and it just a matter of filling in the blanks according to the index, so it transverses and fills.

But yeah, I probably was a bit poor at writing.

---

### Post by slavik on 2010-06-22
yes, appending to a list like that is bad. it is best if you can tell a list that it will have that many things (C++ vector does this).

in Perl, you can assign the last element you want and the array will get autoresized.

ie:
```

my @array = ();
$array[50000] = 0;

```

Also, in your example, you are creating a list, generating values and then assign them one at a time, a much better solution would be:
```

list = range(500000)

```

---

### Post by Can+~ on 2010-06-22
> **slavik said:**
> Also, in your example, you are creating a list, generating values and then assign them one at a time, a much better solution would be:
```

list = range(500000)

```

I was quoting OP's code.

---

