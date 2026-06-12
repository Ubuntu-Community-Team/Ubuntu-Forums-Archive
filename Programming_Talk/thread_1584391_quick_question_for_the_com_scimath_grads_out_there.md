---
title: "quick question for the com sci/math grads out there"
date: 2010-09-29
forum: Programming Talk
---

### Post by mo.reina on 2010-09-29
i'm a self taught 'programmer' (2 sems of computer science at uni which don't really amount to anything), so when i come across formulas like the one [here]("http://www.quuxlabs.com/blog/2010/09/matrix-factorization-a-simple-tutorial-and-implementation-in-python/")(used to 'guess' movie ratings) i'm usually at a loss.

my question is does this fall under machine learning/AI, or just under general math (like the stuff you find at khanacademy).

---

### Post by gzarkadas on 2010-09-29
It is definitely *_not_* machine learning/AI. It is an iterative minimisation method used to approximate unknown values, employing linear algebra and differential calculus; thus general math, under your classification.

---

### Post by mo.reina on 2010-09-29
> **gzarkadas said:**
> It is definitely *_not_* machine learning/AI. It is an iterative minimisation method used to approximate unknown values, employing linear algebra and differential calculus; thus general math, under your classification.

cool thanks.

so the next question is... is it 'necessary' to learn this kind of math, machine learning, both, or none?

obviously it depends on what someone wants to do, but i'm speaking from a general point of view.  and if so, where does one go, outside of uni?  i don't think self study is gonna cut it when the topics become this complicated.

---

### Post by gzarkadas on 2010-09-29
The only true requirement for programming is the program to be correct (there is also the need for efficiency, easy maintenance, etc., but all these are useless if the program is not correct).

If you don't understand the math beyond a calculation, you can try find a library that does this for you. If you can't find this library and still want to do it, then it is necessary to understand the math behind the calculation.

There are a lot of online sources for mathematics. You can use Wikipedia and also search the numerous university math departments pages for online lectures and such stuff. Also, you can study the code of programs that do mathematics, to see how things are done and how the algorithms are worked. One such program, for example is [GNU Octave]("http://www.gnu.org/software/octave/"). There are many more under the [math category of the Free Software Directory]("http://directory.fsf.org/category/math/"). And elsewhere, in many places. If you use a free license to your programs, then you have the added benefit that you can copy and modify all of this freely available code to your needs.

It is possible to self-learn anything; though it is definitely more difficult without guidance. But even guidance is something that can be searched for. You can for example search -if you can't or do not want to enter a course- for open-to-attend seminars or workshops in your area on the subjects that interest you. Or you can post questions to related newsgroups and forums, etc. 

It only needs determination. And a well-thought assessment of what you want to achieve, because learning is by default a time consuming process.

---

### Post by worksofcraft on 2010-09-29
To a large extent I agree with the above post, however sometimes there is a whole system and theory you might have to understand before you can really follow how the algorithm works.

e.g. I once had to take an open polytechnic mathematics course on numeric approximations just to be able to produce a decent solution on a job I was doing. We could have hired a methematician or googled solutions but without structured guidance I could not have really understood the theory. That was necessary to make the right choices and adapt it to the specific problem.

---

