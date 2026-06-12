---
title: "complexity and efficiency of an algorithm mean the same thing in Big O notation?"
date: 2007-11-09
forum: Programming Talk
---

### Post by nite owl on 2007-11-09
Hi I am a computer science student studying for some upcoming exams.
I have been looking through last years past paper and I see a question asking me to give the complexity of a given algorithm in Big O notation and justify my answer. 

However my text only explains how to calculate the efficiency of an algorithm in Big O notation, These do not sound the same to me though I could be wrong.. Thanks

---

### Post by ranarion on 2007-11-09
First of all, I'm not sure whether this is the right place for such a question, perhaps one of the comp.sci.*-newsgroups might have been better. But I'll try to answer anyway.

This seems to be just a case of ambiguous wording. The big-O-Notation is used to group algorithms into complexity classes according to their *average* complexity. Each algorithm in a class has the same kind of complexity function (ignoring parameters). Such a function describes how many computation steps an algorithm needs for a given input size of *n* datasets (time complexity) or how much memory it needs (space complexity).

For example, all algorithms with O(*n*²) have a complexity function that somehow includes the square of the numer of input datasets, but there may well be a lot more factors in the function. Remember that big-O is only used for partitioning into classes!

Now, when a programmer improves an algorithm so that its runtime complexity decreases from 15*(1.3*n)² to 3*(1.3*n)², he will call it a success in improving the efficiency. True, the code has become faster, but the algorithm is still in O(n²), and in theoretical computing science, one usually talks about increased efficiency only when the revised algorithm falls into a lower complexity class. Keeping with this example, suppose that we only knew one sort algorithm, namely BubbleSort. You can optimize it quite a bit, but for really large sets of input data, it still is slow. The only real efficiency improvement would be to invent a completely new algorithm with O(n log n) and call it, say, Quicksort :-)

I hope that helped!

---

### Post by nite owl on 2007-11-09
Oh ok thanks...So what I am getting from your post is that there isn't a difference, just work out which class it is in i.e. O(n).

The complexity class is a measure of how efficient the program is. Thus they mean the same thing...Just as you said "Ambiguous" wording.

---

### Post by samjh on 2007-11-09
> **nite owl said:**
> I see a question asking me to give the complexity of a given algorithm in Big O notation and justify my answer. 

However my text only explains how to calculate the efficiency of an algorithm in Big O notation, These do not sound the same to me though I could be wrong.. Thanks

Big-O notation is just an abstract way to represent efficiency of a given function on a data set.  Efficiency analysis normally uses a data set n approaching size infinity.  The result of such an analysis using Big-O notation is read something like "order of *insert notation here* time complexity".

I don't know about the distinctions a computational scientist might make between complexity and efficiency using Big-O notation, but from what I learned, the terms "complexity" and "efficiency" expressed in Big-O notation are practically the same thing.

---

### Post by Sporkman on 2007-11-09
> **ranarion said:**
> 
For example, all algorithms with O(*n*²) have a complexity function that somehow includes the square of the numer of input datasets, but there may well be a lot more factors in the function. Remember that big-O is only used for partitioning into classes!


Actually what goes into the O[ ] is the fastest rising term. So, for example, if an algorithm takes a n^2 + b n + c steps to process n elements, then it is O[n^2]. If it takes a n^2 + b 2^n steps, then it is O[2^n].

---

### Post by hod139 on 2007-11-09
> **nite owl said:**
> Hi I am a computer science student studying for some upcoming exams.
I have been looking through last years past paper and I see a question asking me to give the complexity of a given algorithm in Big O notation and justify my answer. 

However my text only explains how to calculate the efficiency of an algorithm in Big O notation, These do not sound the same to me though I could be wrong.. Thanks

They are basically the same thing.  Big-Oh notation is used to categorize an algorithm's growth rate, and this allows one to rigorously compare algorithms/programs.  A more "efficient" algorithm is one that has less "computational complexity".

> **ranarion said:**
>  The big-O-Notation is used to group algorithms into complexity classes according to their *average* complexity

This is wrong, Big-Oh notation is used to capture worst case growth rates of an algorithm.  That is, if the growth rate of the algorithm is less than some function.

To try and clear up some of the confusion in previous posts, you can think of Big-Oh analysis like this.  Assume an algorithm is O(n).  That means that if it takes 4 seconds to run on a dataset of size 100, it will take less than 8 seconds to run on a dataset of size 200.  Doubling the size (n) results in a maximum of doubling the run time.

Assume now that an algorithm is O(n^2).  Now, if it takes 4 seconds to run on a dataset of 100, it will take less than 16 seconds to run on a dataset of size 200.  Here we again doubled the size of the dataset, but the running time grows by the square of the size.

Lastly, assume an algorithm is O(n^5). Again, it takes 4 seconds to run on a dataset of 100.  Now, it will take less than 1024 seconds to run on a dataset of size 200.  Here we again doubled the size of the dataset, but the running time grows by a power of 5.  

This is why there are not many practical algorithms with a running time worst than O(n^3).  Also, you note that in the above analysis, I do not know how long the algorithm will take, I only know that it will be less than some upper bound.  In actuality, it may take far less than the upper bound.

---

### Post by CptPicard on 2007-11-09
> **hod139 said:**
> Big-Oh notation is used to categorize an algorithm's growth rate, and this allows one to rigorously compare algorithms/programs.  A more "efficient" algorithm is one that has less "computational complexity".

But of course the catch is how big your constants are :) It's surprising how often, with sufficiently complex algorithms, in the Big-Oh sense more efficient algorithms are actually way too hulking for small data sets.

---

### Post by ranarion on 2007-11-09
> **hod139 said:**
>  Big-Oh notation is used to capture worst case growth rates of an algorithm.

Of course you're right, that was a leftover from an attempt to include worst case, average and best case analysis. My mistake.

---

### Post by hod139 on 2007-11-09
> **CptPicard said:**
> But of course the catch is how big your constants are :) It's surprising how often, with sufficiently complex algorithms, in the Big-Oh sense more efficient algorithms are actually way too hulking for small data sets.

There is no catch.  Big-Oh analysis is for analyzing the growth rate of a function, not for measuring performance on a data set.

---

### Post by the_unforgiven on 2007-11-10
The Wikipedia article on [Big O Notation]("http://en.wikipedia.org/wiki/Big_O_notation") is very nice - you should read it.

Also, the links given in the references section of the above article are quite helpful - especially, the NIST pages by Paul E. Black - those pages explain the other important functions related to Big O (like little o, omega, Omega and Theta)

The first volume of Knuth's book - "The Art Of Computer Programming" - also has very good discussion on all these functions.

---

### Post by evymetal on 2007-11-11
Just thought I would point out that Big-O notation is used for measuring efficiency of several things.

Complexity (number of cycles)
Memory
Disk Access
Number of machines in a cluser
... whatever is your bottleneck.

It's nearly always used for complexity classes or memory requirements, though.

It's also not too uncommon to specify the "Best Case", "Expected" and "Worst Case" scenario of various algorithms, if they have very wide deviations or a strongly skewed distribution.

---

