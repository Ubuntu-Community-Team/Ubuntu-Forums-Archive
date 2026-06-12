---
title: "Algorithms"
date: 2007-12-24
forum: Programming Talk
---

### Post by LaRoza on 2007-12-24
I thought I would add something new to this forum, a discussion on algorithms. 

This topic is often overlooked by those learning and is probably the most important thing to learn. Syntax is useless without them. Before this thread hopefully delves deep into the subject, I will start with a simple discussion.

To start the discussion, I will introduce this common and rather simple algorithm. I just was brushing up on my Fortran as you can tell. It is a simple syntax, and you should be able to follow it if you ever used any other statically typed language.

Forgive the odd variable names, but "result" and "sum" are keywords. Also forgive the use of a goto. Although the use of this programming tool is greatly discouraged, Fortran (this is 1977, you know) relies on it. In case you can't tell, it is a "for" loop, rewritten in Fortran.

This algorithm calculated Fibonacci numbers.

[php]
        double precision function Fibonacci (x)
            double precision x,su,i
            integer previous, resul
            i = 0
            previous = -1
            resul = 1
   10       if (i .le. x) then
                i = i + 1
                su = resul + previous
                previous = resul
                resul = su
                goto 10
            end if
            Fibonacci  = resul
            return 
        end
[/php]

Can anyone give any alternatives to this or improve on this, in any language of course.

As you can see, this algorithm is not recursive, even though the Fibonacci series is defined in a recursive manner. Recursion is not used for two reasons: 

0. It greatly reduces the efficiency of the program because the program would spawn two more function calls for any number greater than 1, which in turn would call two and etc.

You can guess what the second reason is.

---

### Post by slavik on 2007-12-24
Just a note, that recursive ways of doing things are only inefficient because it takes time and resources to set up function calls. Even though this should be a language agnostic discussion, there are languages that recognize tail recursion and can optimize it away (prolog, haskel, scheme to name a few).

and you can also use to find a factorial of a number by using a loop (even though it is defined recursively).

In the world of mathematics, recursion is free. :)

---

### Post by ghostdog74 on 2007-12-24
if you look up google, there are many implementations of this algorithm in different languages. so what is it that you want to discuss?

---

### Post by LaRoza on 2007-12-24
> **slavik said:**
> Just a note, that recursive ways of doing things are only inefficient because it takes time and resources to set up function calls. Even though this should be a language agnostic discussion, there are languages that recognize tail recursion and can optimize it away (prolog, haskel, scheme to name a few).

and you can also use to find a factorial of a number by using a loop (even though it is defined recursively).

In the world of mathematics, recursion is free. :)

Fortran isn't one of those languages. Functional languages do not have this problem.

---

### Post by slavik on 2007-12-24
never said it was :) but what problem are you reffering to?

---

### Post by LaRoza on 2007-12-24
> **ghostdog74 said:**
> so what is it that you want to discuss?

Algorithm Design.

This is just a simple well know algorithm to get the discussion started. It is hardly unique or special, except that it is a classic well known algorithm which highlights the importance of a well designed algorithm, not only logically, but based on the tools used. As noted before, if using functional language, one would not do it this way. However, I used a language which doesn't allow recursive functions, and many languages of this type, imperative, wouldn't be efficient recursively.

If you didn't understand my intent, I hope that clears it up.

---

### Post by LaRoza on 2007-12-24
> **slavik said:**
> never said it was :) but what problem are you reffering to?

The inefficiency of recursive function calls. I guess "problem" wasn't the right word. Could you give an alternative version in a functional language?

---

### Post by slavik on 2007-12-24
```

factorial (int x) {
  if x = 0 return 1;
  return x*factorial(x-1);
}
```

factorial function written functionally in C :)

the way functional languages optimize recursion is simply by reusing the original stack frame from the first call.

so when you do a factorial(10) call, imagine the sequence of numbers expanded from 10 to 1 and then multiplied between each other much like it is done in a loop.

every loop can be a recursion, but not every recursion can be a loop. keep that in mind.

---

### Post by LaRoza on 2007-12-24
> **slavik said:**
> ```

factorial (int x) {
  if x = 0 return 1;
  return x*factorial(x-1);
}
```


What is the return type of this function?
```

(defun Fibonacci (n)

( if ( or ( = n 1) (= n 0) )

1

(+ (Fibonacci ( - n 1) )

( Fibonacci (+ n 1) ) ) ) )

```
This Lisp version shows the recursive version in a more natural way, as Lisp is well suited for this sort of algorithm design.

(I didn't test it yet (I am installing GNU Common Lisp now (I recently reinstalled Ubuntu and didn't reinstall all the tools yet (Wow, Lisp can dig deep into your mind))))

-EDIT The Lisp code has a bug, sorry, I am out of practice

---

### Post by wolfbone on 2007-12-24
```
(defun fibonacci (n)
  "Compute the nth Fibonacci number using the method described
   in exercise 1.19 of section 1.2.4 of SICP"
  (if (< n 0) 0
      (labels ((fib (a b p q m)
		 (cond ((= m 0) b)
		       ((evenp m)
			(fib a
			     b
			     (+ (* p p) (* q q))
			     (+ (* q q) (* 2 p q))
			     (/ m 2)))
		       (t (fib (+ (* b q) (* a q) (* a p))
			       (+ (* b p) (* a q))
			       p
			       q
			       (- m 1))))))
	(fib 1 0 0 1 n))))
```

---

### Post by LaRoza on 2007-12-24
> **wolfbone said:**
> ```
(defun fibonacci (n)
  "Compute the nth Fibonacci number using the method described
   in exercise 1.19 of section 1.2.4 of SICP"
  (if (< n 0) 0
      (labels ((fib (a b p q m)
		 (cond ((= m 0) b)
		       ((evenp m)
			(fib a
			     b
			     (+ (* p p) (* q q))
			     (+ (* q q) (* 2 p q))
			     (/ m 2)))
		       (t (fib (+ (* b q) (* a q) (* a p))
			       (+ (* b p) (* a q))
			       p
			       q
			       (- m 1))))))
	(fib 1 0 0 1 n))))
```

Could you explain that for the less skilled? (Me)

---

### Post by ghostdog74 on 2007-12-24
1) [fibo]("http://cubbi.com/fibonacci.html")
2) [fibo]("http://www.scriptol.org/fibonacci-any-programming-language.html")

---

### Post by wolfbone on 2007-12-24
> **LaRoza said:**
> Could you explain that for the less skilled? (Me)

It;'s explained here: 

[http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-11.html#%_sec_1.2.4](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-11.html#%_sec_1.2.4)

(scroll down to exercise 1.19)

---

### Post by pedro_orange on 2007-12-24
Lol - is this purposefully obfuscated? 

I'm sure it would be easier to read that in binary!

Back to topic. Algorithm design cannot be discussed without perfomance issues, and this is where the Big O notation comes in. 
The Fibonacci sequence has a number of implementations - which in turn will all have different perfomance considerations.

After reading this post I searched the net a bit and found an interesting lecture which discusses all of this - [http://www.ics.uci.edu/~eppstein/161/960109.html](http://www.ics.uci.edu/~eppstein/161/960109.html)

Enjoy.

---

### Post by xtacocorex on 2007-12-24
I've been told to never to recursion to find factorials in my Numerical Methods classes, wastes too much time and there are easier methods for it, which I can't find the code I where I needed factorials. :(

I do know what I did though, since all my numbers were greater than 1, I didn't need to worry about the zero case and since the factorial was inside other calculations, I just multiplied by the current number of the factorial (in my case it was 1/current_n because that's how the equation broke out).

Here is an example of a non-recursive factorial function in FORTRAN 90.
```

INTEGER FUNCTION FACTORIAL(X)
        INTEGER, INTENT(IN) :: X
        INTEGER :: I

        ! INITIALIZE FACTORIAL
        FACTORIAL = 1
        
        ! FIGURE OUT IF X IS ZERO
        IF (X .EQ. 0) THEN
                RETURN
        ELSE
                ! LOOP THROUGH TO FIND FACTORIAL
                DO I = 2, X
                        FACTORIAL = FACTORIAL * I
                END DO
        END IF

END FUNCTION FACTORIAL

```

LaRoza, what sort of other algorithms do you have in mind?  I have a tri-diagonal matrix solver, 4th order Runge-Kutta code, an Integral solver.  Those are pretty standard codes for Numerical Methods that won't differ much between syntaxi.

---

### Post by Majorix on 2007-12-24
Recursion greatly increases the RAM and CPU used. [http://shootout.alioth.debian.org/gp4/benchmark.php?test=recursive&lang=all](http://shootout.alioth.debian.org/gp4/benchmark.php?test=recursive&lang=all)

And it is hard to understand for the first-timer or casual programmer.

---

### Post by wolfbone on 2007-12-24
> **Majorix said:**
> Recursion greatly increases the RAM and CPU used. [http://shootout.alioth.debian.org/gp4/benchmark.php?test=recursive&lang=all](http://shootout.alioth.debian.org/gp4/benchmark.php?test=recursive&lang=all)

And it is hard to understand for the first-timer or casual programmer.

If the SBCL compiler is failing to optimize my tail recursive functions, I should file a bug report! Anyway, I expect a lot of things are hard to understand for the first-timer or casual programmer. Perhaps we should make a list and avoid discussing any of them? ;-)

---

### Post by LaRoza on 2007-12-24
> **xtacocorex said:**
> I've been told to never to recursion to find factorials in my Numerical Methods classes, wastes too much time and there are easier methods for it, which I can't find the code I where I needed factorials. :(

LaRoza, what sort of other algorithms do you have in mind?  I have a tri-diagonal matrix solver, 4th order Runge-Kutta code, an Integral solver.  Those are pretty standard codes for Numerical Methods that won't differ much between syntaxi.

In some languages, recursion is encouraged because they do not waste resources. That is why the Lisp version was recursive.

I intended this discussion to be about alogorithms in general, so you can introduce any new algorithms or consideration on the subject.

(It should be more interesting than the "which language" threads)

---

### Post by Majorix on 2007-12-24
> **wolfbone said:**
> If the SBCL compiler is failing to optimize my tail recursive functions, I should file a bug report! Anyway, I expect a lot of things are hard to understand for the first-timer or casual programmer. Perhaps we should make a list and avoid discussing any of them? ;-)
What kind of first-timer are we talking about? I had no difficulties with anything except recursive functions when I first started learning programming. Lately, I find that functional programming concepts are bugging me.

---

### Post by LaRoza on 2007-12-24
> **Majorix said:**
> What kind of first-timer are we talking about? I had no difficulties with anything except recursive functions when I first started learning programming.

People with a stronger interest in Math find recursive functions easier to understand, as they often are the exact copy of the definition of an algorithm.

---

### Post by wolfbone on 2007-12-24
> **Majorix said:**
> What kind of first-timer are we talking about? 

That was my point:  you may be talking about first-timers, but given it was LaRoza who started this thread (and given the subject s/he chose), I don't really know why!

[QUOTE=LaRoza]I thought I would add something new to this forum, a discussion on algorithms.[/QUOTE]

---

### Post by revanthedarth on 2007-12-24
Fibonacci numbers is the first example of dynamic programming. To compute all fibonacci numbers from 0 to n, you may use this:

```

int fibo[N]; //means integer array of size N
fibo[0] = 1; fibo[1] = 1;
for(int i=2; i<N; i++)
fibo[i] = fibo[i-1] + fibo[i-2];

```
Pseudo-code:
```

create an array fibo of size N
set zeroth and first element of fibo 1
then, for each i (i>1), set i.th element sum of i-1.th element  and i-2.th element

```
When you use recursive, you would do that:
Fibo(20) = Fibo(19) + Fibo(18 ) = Fibo(18 ) + Fibo(17) + Fibo(18 ) ... (Notice Fibo(18 ) computed twice, and Fibo(17) even more)

Dynamic programming is about not computing what you already did.

But know that Fibonacci is a special example, in which you can compute any element with 3 variables.

---

### Post by slavik on 2007-12-24
> **LaRoza said:**
> People with a stronger interest in Math find recursive functions easier to understand, as they often are the exact copy of the definition of an algorithm.
This is why some CS professors say that a functional language (read: Scheme) should be the first programming language. Those same professors also think that computer science should be like medical school, you go to college for a hard science (math, physics, engineering, etc.) and only after that you learn computer science.

---

### Post by uljanow on 2007-12-24
You could optimize fibonacci with memoization.

---

### Post by LaRoza on 2007-12-24
> **uljanow said:**
> You could optimize fibonacci with memoization.

Could you give an example? Definition of [memoization]("http://en.wikipedia.org/wiki/Memoization") for reference

---

### Post by revanthedarth on 2007-12-24
How? I can't see a better way to compute Fibonacci numbers from 1 to N.

---

### Post by CptPicard on 2007-12-24
Well, people have been using memoization in this thread already many many times, talking of arrays and using just 3 variables...

---

### Post by LaRoza on 2007-12-24
> **CptPicard said:**
> Well, people have been using memoization in this thread already many many times, talking of arrays and using just 3 variables...

I thought the poster was going to further optimize the function. (I use the one I posted first mentally, although others are in this thread)

---

### Post by revanthedarth on 2007-12-24
Oh, sorry. I thought it was something different than i used or mentioned.

---

### Post by CptPicard on 2007-12-24
> **LaRoza said:**
> I thought the poster was going to further optimize the function. (I use the one I posted first mentally, although others are in this thread)

Memoization is simply the practice of stuffing already computed values into RAM for later reuse, which is being done in the solutions provided. Memoization and dynamic programming are pretty much one and the same really...

---

### Post by uljanow on 2007-12-24
Fibonacci is not a good example for memoization because you can simply calculate the numbers from bottom-up. On the other hand if you have a recursive algorithm which calculates same intermediate results but not all you can use already calculated results which leads to less recursive function calls.

```

int mem[20] = {0};

int fib(int n)
{
    if (n == 1 || n == 2) return 1;
    if (!n) return 0;

    if (mem[n]) return mem[n];

    return mem[n] = fib(n - 1) + fib(n - 2);
}

```

> Memoization and dynamic programming are pretty much one and the same really...ACK

---

### Post by stroyan on 2007-12-26
You could use a closed form equation.
That depends on floating point power instead of integer iteration. ```
        double precision function Fibonacci_closed (x)
            double precision x, s5, r
            s5 = 5.0D0 ** 0.5D0
            r = ((((1.0D0+s5)/2.0D0)**x)-(((1.0D0-s5)/2.0D0)**x))/s5
            Fibonacci_closed  = r
            return 
        end
```or```
        double precision function Fibonacci_closed2 (x)
            double precision x, golden, s5
            s5 = 5.0D0 ** 0.5D0
            golden = (1.0D0 + s5) / 2.0D0
            Fibonacci_closed2 = ((golden**x)-((-golden)**-x))/s5
            return 
        end
```
That starts to get imprecise, (incorrect) answers around x=66.
(But your original algorithm gets into trouble much sooner if you don't change "integer" to "integer*8".

---

