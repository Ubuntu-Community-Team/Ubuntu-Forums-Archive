---
title: "Any suggestions to make my code run faster?"
date: 2013-08-07
forum: Programming Talk
---

### Post by Ninja&gt;Master on 2013-08-07
Hi,
I am trying to solve a programming problem on [SPOJ]("http://www.spoj.com/").

The problem is as follows:

> 
 Multiply the given numbers. 
 **Input**

  
*n* [the number of multiplications <= 1000]
*l1 l2* [numbers to multiply (at most 10000 decimal digits each)]
[LEFT]
Text grouped in [ ] does not appear in the input file.
[/LEFT]
 **Output**

  
The results of multiplications.
 **Example**

 Input:
5
4 2
123 43
324 342
0 12
9999 12345

Output:
8
5289
110808
0
123437655



The time limit: 2 seconds
Problem link: [http://www.spoj.com/problems/MUL/](http://www.spoj.com/problems/MUL/)

My code runs fine but when I submit it there it says "Time limit exceed". Can anyone help me make my code faster?

```

t = int(raw_input())
cn = []
answers = []
i = 1

while i <= t:
    x = raw_input()
    cn = x.split(" ")
    answers.append(long(cn[0])*long(cn[1]))
    i += 1

for answer in answers:
    print answer

```

---

### Post by ofnuts on 2013-08-07
Did you try it with very big numbers, and then multiplied that by 1000 to find out your maximum run time?

---

### Post by Vaphell on 2013-08-07
i wonder if it's even possible to pass the test with python. Just look at the accepted solutions, c/c++ across the board and python is what, ~40x slower?

---

### Post by r-senior on 2013-08-07
Given that the title is "Fast Multiplication", I suspect the idea is to implement a clever algorithm rather than use the '*' operator:

[http://en.wikipedia.org/wiki/Multiplication_algorithm#Fast_multiplication_algorithms_for_large_inputs](http://en.wikipedia.org/wiki/Multiplication_algorithm#Fast_multiplication_algorithms_for_large_inputs)

Your solution may produce the correct output, but is probably missing the point of the exercise.

---

### Post by Vaphell on 2013-08-07
i looked at their forum (python related subforum to be exact) - not possible with python. Apparently what gets python solutions killed is int<->string conversion which takes order(s) of magnitude more time than the math itself. Native multiplication utilizes one of the efficient algorithms behind the curtain either way so it's not the reason of failure (though i agree writing a*b is not the point)

---

### Post by Ninja&gt;Master on 2013-08-08
So, I have to rewrite the program in C++ with a different, improved algorithm right? The problem is that the numbers can be very large, so I've to use BigInteger which is quite a problem because in C++ you have to declare variable types and convert b/w them. I chose Python in the first place for this one because there isn't a need to convert b/w the variable types.

---

### Post by ofnuts on 2013-08-08
> **Ninja>Master said:**
> So, I have to rewrite the program in C++ with a different, improved algorithm right? The problem is that the numbers can be very large, so I've to use BigInteger which is quite a problem because in C++ you have to declare variable types and convert b/w them. I chose Python in the first place for this one because there isn't a need to convert b/w the variable types.

This stuff isn't meant to be *easy*. It's even designed so that trivial code won't cut it...

---

### Post by Ninja&gt;Master on 2013-08-08
I get your point. Is there a way in C++ for "BigInteger" types without installing external libraries?

---

### Post by Vaphell on 2013-08-08
> **Ninja>Master said:**
> So, I have to rewrite the program in C++ with a different, improved algorithm right? The problem is that the numbers can be very large, so I've to use BigInteger which is quite a problem because in C++ you have to declare variable types and convert b/w them. I chose Python in the first place for this one because there isn't a need to convert b/w the variable types.

that you don't need to convert by hand doesn't mean it doesn't happen implicitly in the background. Most of these programming tasks require rolling your own solution by hand for huge performance gains over the out-of-the-box options, should they exist.
I imagine C/C++ entries take advantage of the fact that you can take a chunk of memory, fill with it data, exploit 'char is a number too' (to get 0 from '0' just substract 48 or '0') and perform pointer magic. Nothing can beat that in raw speed, convenience is another matter.

---

### Post by Tony Flury on 2013-08-08
You might not get the timelimit you need but my guess would be that adding things to a list at every iteration and then a separate loop to print the results as you have it will will be slow.

---

### Post by ofnuts on 2013-08-08
> **Tony Flury said:**
> You might not get the timelimit you need but my guess would be that adding things to a list at every iteration and then a separate loop to print the results as you have it will will be slow.
This is a rather short list (<=1000 elements) so I doubt this matters compared to the rest.

---

