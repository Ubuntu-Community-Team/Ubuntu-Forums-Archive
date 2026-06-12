---
title: "Basic R Help - Random Number Generator"
date: 2011-02-03
forum: Programming Talk
---

### Post by amyt_04 on 2011-02-03
Working on a project for a class, but I'm completely stuck. 

I need to find a random number generator algorithm that will produce the  SAME 100000 numbers each time from 0 to 1 on a uniform distribution,  and it cannot be runif. I cannot download a package.

I'm new to this, and I've tried everything, sample(), rnorm(), random  package. The list goes on and on. I've been working on this for about 20  hours over the past three days with no luck. All of them produce  DIFFERENT random numbers, but I can't seem to find anything that  produces the same ones.

---

### Post by amyt_04 on 2011-02-03
Further explanation, he sent me this email:

"Your question: Must our RNG have an even or close to even distribution?  Does it need to guarantee randomness to a certain precision? Must it be  inclusive of 0 and 1?
 
Answer:I do not want randomness with extreme precision or with period  one billion. I want that your team knows how to generate the random in  [0,1]. Hence, you can use a simple random number generator. For example,  I easily found one one the web and I wrote in R without using any seed  function; I knows if I repeat many times I get always the same numbers  but here we want just show the basic idea."

---

### Post by worksofcraft on 2011-02-03
You can download files with true random numbers in them from [http://www.random.org/files/](http://www.random.org/files/) then when you read from them you will always get the same truly random sequence :lolflag:

---

### Post by MadCow108 on 2011-02-03
homework questions are not really welcome so here only a fraction of a possible solution:
x_n = (a * x_n-1 + b) mod c

the values of the parameters a, b and c are extremely important and not trivial to figure out, I'll let that to your analysis  (or googling) skills (hint randu)

---

