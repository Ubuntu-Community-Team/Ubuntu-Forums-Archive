---
title: "Programming for solving math problems"
date: 2012-05-21
forum: Programming Talk
---

### Post by TheHimself on 2012-05-21
Well, I'm a mathematician who knows some C programming however I've never used programming for solving math problems. Now I have a combinatorial/topological problem that I want to study using computer (and it's very cycle-consuming) however I see that C is not the easiest way to implement such a program. For example I need to do a loop for all N-tuples of +1 or -1 (there are 2^N of them where N is a variable). However I don't know how to implement loops of variable nestedness in C. [Well, one can map the numbers between 1 and 2^N onto such N-tuples but that's not very natural.]

Is there any programming language particularly suitable for combinatorial math problems? Or I have to go for Mathematica or Maple?

---

### Post by Bachstelze on 2012-05-21
More specific, please! A lot of scientists or mathematicians think they can give a vague description of their problem, and people can instantly come up with a solution. No. Be more specific about what you want your program to do. Ideally, write pseudocode.

---

### Post by hailholyghost on 2012-05-21
I think what you need is Perl or Python.  They are meant to be faster to program than C, while not necessarily as fast to execute.

Both are pretty easy to learn, but from what I understand Python is better at mathematics-heavy jobs, while Perl is better at text-processing.

Maybe you could post what you've tried so far?

---

### Post by TheHimself on 2012-05-21
I'm not asking you to "solve" my problem. I'm just looking for the right programming language which just now I come to realize it may be Python. My math problem is looking at a specific arrangement of curves in the plane and finding specific subarrangements in it. Something like "How many triangles you see in the picture" but with a twist.

---

### Post by Bachstelze on 2012-05-21
In order to tell you what the right programming language is for the problem at hand, we need to have a good idea about what the problem is from a computing point of view. "Curves in the plane" tells us nothing. How are those curves represented?

---

### Post by LemursDontExist on 2012-05-22
As Bachstelze noted, it's hard to answer without more information.  For ease of programming I invariably recommend Python, but if computational speed really is critical, then Python might not be good enough.

I might suggest checking out Haskell.  Combinatorial problems which can be quite involved in C often come out to one liners in Haskell, and it can perform comparably to C for many purposes.  The learning curve on Haskell tends to be very steep though since most people aren't used to functional programming.  Still, as a mathematician you're likely to find the syntax of Haskell more natural than most people do.

That said, there really is no algorithm that you can implement in another language that can't be implemented in C fairly straight forwardly.  In particular to get a variable depth of loops in any language you'll generally use recursion.  Just write a function that does the loop and calls itself inside the loop as needed.

Anyway, Haskell does recursion very naturally, so that's another reason to check it out!

---

### Post by roelforg on 2012-05-23
I sometimes write little c++ programs to do repetitive math homework.
(like when you get stuff like x2+6x+8 and you need to get the Y=0 points, our math book has 2 useful excersizes and then 3 more of mindless repeating the same calc and that's exactly what computers are good at!)

---

### Post by Simian Man on 2012-05-23
Without knowing more about your problem, I'd suggest Python with [NumPy]("http://numpy.scipy.org/").

---

### Post by 3Miro on 2012-05-23
If you want to nest a number of for-loops, you can write a "configure" script to generate the needed C code. A more "elegant" solution would be to use recursion, although it would be hard to help without knowing more about your problem.

I am a continuous PDE/Control/UQ person, however, in my limited exposure to discrete math most of the algorithms are very susceptible to recursion.

---

### Post by roelforg on 2012-05-23
I even once made my computer do all my math homework for a day...
And it actually worked!
It was complete with "natural"* output.
 
*=it outputted the calculations and stuff as if i made the calculations myself by hand.

---

### Post by pbrane on 2012-05-23
You should look at GNU-Octave (or Matlab). You can quickly work out an algorithm and then code it in whatever language you want to, if you even need to at that point.

---

### Post by Erdaron on 2012-05-23
Dynamic array sizing can be done in C++ with a trick, I believe, but I haven't touched this language in well over a decade. However, it is basically an automatic feature in Python. You initialize an array an then just keep adding stuff to it.

Numpy speeds up numerical computation in Python tremendously, but it largely relies on fixed-size arrays. You can get around that by constantly merging arrays of existing and new data (using numpy.hstack() or numpy.vstack()), but likely costs you some of the speed advantage. Though at least you can still do array operations without explicitly using iteration, which rocks.

(Also also, while numpy arrays are fixed-size, their size can be set at run time, it does not have to be hard-coded.)

If you are affiliated with a university, you may be able to get a MathCAD license for a reasonably small cost ($50-100). I have found that MathCAD is fantastic for quickly prototyping math problems. You can figure out algorithm quirks and then change over to a more serious language, like Python or Haskel for the heavy lifting.

There is also [scipy]("http://scipy.org/") and [scipy kits]("http://scikits.appspot.com/scikits"). And also [this site]("http://www.lfd.uci.edu/~gohlke/pythonlibs/") that has various Python libraries compiled for x64, and included a wealth of various science- and math-related libraries.

---

### Post by roelforg on 2012-05-23
> **Erdaron said:**
> Dynamic array sizing can be done in C++ with a trick, I believe, but I haven't touched this language in well over a decade.

 
That "trick" could be one of:
* vector
* map
* list
* plain old malloc/realloc/free
etc

---

### Post by Barrucadu on 2012-05-23
If you're trying to have a variable level of nesting of your loops, you're approaching the problem incorrectly. Recursion is probably what you want (although, without any real information on your problem, I'm just guessing here).

---

### Post by LemursDontExist on 2012-05-25
Just to strengthen the case for Haskell a bit, here's some code to do something for all (1, -1) N-tuples:
```
nTuples 0 xs = [[]]
nTuples n xs = [x:ys | x <- xs, ys <- nTuples (n - 1) xs]

result n args = [doSomething ntuple args | ntuple <- nTuples n [1, -1]]
```
Where doSomething would be a function that returns the value you want for each N-tuple, and args is just whatever other arguments you want.  Haskell has lazy evaluation, so the elements of nTuples are only calculated as needed.

I sat down to write the same code in C for a side by side comparison, but once I realized that the general way to do it involved passing a function pointer as a callback I decided I had better things to do with my time.

---

### Post by samitharansara on 2012-05-25
I would recommend Python, and Spyder.  I used to do lot of mathematics in Matlab, but as far as the speed of learning, the easiness of programming, availabilities of free libraries, dynamism, and beauty are concerned Python + Spyder combination rocks ahead..

---

### Post by TheHimself on 2012-05-28
OK, here is a better description of my problem. I have a graph with 2^N vertices whose edges are labeled by numbers 1 to N. And I'm looking for subgraphs which are loops with N edges such that each one of the labels occurs once. There are more conditions to be satisfied but they are difficult to describe rigorously.  For example the loop must bound an N-gon in the plane.

As I said before I'm not asking you to solve my problem; my question is if there is any library, etc. that would make working with such a problem easier or more natural.

PS. I just found python-graph.

---

### Post by LemursDontExist on 2012-05-28
I'm going to still encourage you to use Haskell!

Haskell really shines for these sorts of problems.  I haven't yet gotten around to doing any graph theory in Haskell, but I know there are a number of libraries.  Check out [this one]("http://hackage.haskell.org/packages/archive/containers/0.2.0.1/doc/html/Data-Graph.html") maybe.

Haskell is quite popular for discrete math work because the functional programming paradigm fits naturally with the way mathematical problems tend to be phrased.

---

### Post by pcman312 on 2012-06-04
For a mathematician, I'd probably recommend either Matlab or R. If you're interested in learning more about programming in general, I'd probably recommend either python, perl, or Java to start. Java does have a bunch of built in Math libraries that may help with whatever problems you have. Python probably also has libraries to help, but I find that Java has a pretty extensive community of library developers, so there's a good chance there's a combinatorics library in Java out there. A quick google search gives me a few: [http://code.google.com/p/combinatoricslib/](http://code.google.com/p/combinatoricslib/) [http://maths.uncommons.org/](http://maths.uncommons.org/)

---

### Post by schauerlich on 2012-06-04
> **TheHimself said:**
> OK, here is a better description of my problem. I have a graph with 2^N vertices whose edges are labeled by numbers 1 to N. And I'm looking for subgraphs which are loops with N edges such that each one of the labels occurs once. There are more conditions to be satisfied but they are difficult to describe rigorously.  For example the loop must bound an N-gon in the plane.

As I said before I'm not asking you to solve my problem; my question is if there is any library, etc. that would make working with such a problem easier or more natural.

PS. I just found python-graph.

Does your problem reduce to [finding a hamiltonian path](http://en.wikipedia.org/wiki/Hamiltonian_path)? If so, be careful. Hamiltonian-path is an NP-complete problem, so any solution you come up with is bound to be really (infeasibly) slow for moderately sized inputs. I don't know enough about your problem, though - the solution space may be considerably smaller given the constraints (especially the N-gon constraint).

---

### Post by ratcheer on 2012-06-04
Sage

Tim

---

### Post by schauerlich on 2012-06-04
> **ratcheer said:**
> Sage

Tim

4chan is that way ------>

---

### Post by Lux Perpetua on 2012-06-06
From your description of your problem, it sounds simple enough to be approached from a huge variety of programming languages, including C. The benefits I see of going with C are (1) you already have experience in it, so you're not starting from scratch; (2) a simple C implementation is likely to be much faster than a simple implementation in many other languages; and (3) it's worth knowing C and therefore worth doing exercises that increase your proficiency with the language.

You can't have "loops of variable nestedness in C"; that concept simply doesn't exist. The solution to most problems of this nature is to use recursion. Here's a start:

```

void recursive_computation(int *array, int n, int k) {
    if (k == n) {
        /* Basis case */
        do_stuff_with_array(array, n);
    } else {
        begin[k] = 1;
        recursive_computation(array, n, k+1);
        begin[k] = -1;
        recursive_computation(array, n, k+1);
    }
}

void do_computation(int *array, int n) {
    recursive_computation(array, n, 0);
}

```

Like I said, this can be approached from many different languages. For what they're worth, here are my opinions on a few:

**Matlab** - I'd avoid it for a variety of reasons. The most obvious one is that it isn't free (in any sense of the word), and another one is that it's just not a great programming language. The exception to this recommendation is if there is a specific Matlab function or library (or a third-party package that's only written for Matlab) that you need for your work. I suggest Python with Numpy/Scipy and Matplotlib as a better alternative for most situations. 

**Octave** - Too similar to Matlab. Yes, it's free, but it's still not a great language, and it doesn't have as many features as Matlab (last time I checked).

**Python** - Excellent, and it's a good "default" language when you don't have a specific reason to use a different one. It's very widely supported, and many third-party libraries have bindings for it, which makes it very attractive for many purposes. The main downside is performance, but it usually isn't *that* bad (except when it is). 

**Python/Numpy/Scipy** - Great for mathematical work ***if*** you can *vectorize* most of your number-crunching, i.e., express it in terms of array operations in lieu of explicit loops. Otherwise, it may not be much better than "plain" Python (without Numpy/Scipy). It's not clear to me how much Numpy & Scipy buy you for purely combinatorial calculations, since they're really geared toward numerical stuff. 

**Haskell** - Excellent, especially for problems that are naturally solved recursively. It seems particularly suited for your specific problem, as others have stated. 

**C/C++** - Don't rule them out. A simple algorithm implemented in C or C++ may be 10-1000 times faster (depending on many factors) than a direct translation to Python. The downside is that it's just more difficult to write correct code in C or C++.

---

