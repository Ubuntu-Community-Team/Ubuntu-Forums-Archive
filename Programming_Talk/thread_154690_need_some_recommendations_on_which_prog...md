---
title: "need some recommendations on which prog.."
date: 2006-04-03
forum: Programming Talk
---

### Post by jingo811 on 2006-04-03
Hi I need some recommendations on which programming languages I should pick?
If I want to handle these situations:

**1.)**
I want to build my own e-shop site hosting the server myself.  By the way I don't know much programming or server setup so....but I will learn [-( even if I'm too old (25) to become a heavy programmer and network administrator within a short period of time.
Besides I'm only aiming towards programming small easy *input-calculate-output* programs ignoring beuty of codes and GUI and fancy stuff like that.  I'm only after functionality and automation!

**2.)**
I want to make a safe transaction system on the website, but I've heard that PHP/MySQL which for the moment is my highest choice of language to learn. Is  very unsecure too use (SQL-injections) for a transaction system or phpBB.
Should I abandon the use of PHP because of these high security issues and pick another language for this task?  Or should I stay with PHP?

**3.)**
Do you know what kind of programming languages and database software is used for banks.  Maybe I should follow their example and use all the stuff that they use or is that irrelevant?

---

### Post by sapo on 2006-04-03
1) Python.

2) PHP isn't insecure, PHP is very easy to learn, so all stupid programmers like it and make stupid stuff, cause PHP allows stupid stuff, this forum was coded in PHP, is it insecure?

3) I don't know.

---

### Post by Schmung on 2006-04-03
Re point 3
SQL/Oracle implementations are whats generally used, at least in my experience with large scale corporate finance - so I would imagine thats a good starting point.

---

### Post by thumper on 2006-04-04
wrt point 3: it is irrelevant what banks use internally.

Any language you choose is going to have limitations, however if you are just starting then I recommend python.

---

### Post by hagen00 on 2006-04-04
1) Quickest and easiest will be PHP. Like someone said, this forum was done in PHP and it's not insecure (I think). By the way, google for something called Zen-Cart. It will make your life a whole lot easier!

---

### Post by jingo811 on 2006-04-04
**1.)**
Tnx for the python language recommendation.  But if I would manage to become a real so so programmer, with gods willing.  I'd see myself like more of a security kind of guy rather than a heavy creator of monster programs like MD5 and such :-k (heavy in the sense of value not size!)
Besides from surfing around security like forums it seems C is the tool of language that's most discussed when it comes to understanding how the enemy thinks...
[B]
4.)[/B]
Even though I haven't earned myself the right to call myself a true programmer yet.  I'm taking a class at school on Matlab an interpreted Array-based-language, not something too aim for I would think.
But does anybody in here now of any open-source equivalence  of Matlab for Linux?
I asked them what it would cost me....around 2.100 bucks man for the basic package :-( they'll never get popular with such prices.

**5.)**
Or you know when in Matlab it uses matrices to store lists of values:
> 
(stored variable)=
1 2 3 4 5 
2 3 4 5 1
4 5 1 2 3
5 1 2 3 4

And then it has it's built-in functions to deduct rows or columns pretty fast and easy.
Would programming such a function with C, Python, etc. be a total headache?
Especially if you have a 50x50 table containing random numbers.

**6.)**
Tnx for the tip on Zen-Cart!  Guess I don't have any excuses left, not to read up on PHP anymore.

**7.) Forums**
By the way I've read from a computer magazine and from ppl on the Internet that **vBulletin**(commercial product) is more secure than **phpBB**(open source).  How did ppl come to that conclusion?  I mean sure phpBB is free so a lot more ppl can get their hands on it and experiment with it intesively.  But vBulletin is also PHP built, being a commercial product can't possibly make it more secure from common SQL-injections right?  Or what is the factor that makes vBulletin more secure than phpBB as ppl claim??

---

### Post by thumper on 2006-04-05
When learning programming languages and programming your first language, while important, does not necessarily impact you on what you are going to do with your career.

My first language was Pascal - and I haven't touched it since leaving university.

Yes learning C is a good idea - if you want to work with C.  You don't need to  know it to be a good programmer.  Every language you know extends your understanding of programming and how the guts of computers work.  C does not have a monopoly on making you a better coder.

If you are intending to be a professional programmer then I'd suggest that you intend to be fluent in at least two or three different programming languages.  Eric Raymond suggested C++, Java, LISP, Perl, and Python at the end of his book "The Cathedral and the Bazaar".

I guess what I am really getting at is - don't write of learning python first just because other apps are written in C.  However, do learn more than just python.  Additional languages make you more "rounded" :)

wrt **5** what is your definition of fast?  What is fast enough?  Working with a 50 x 50 matrix of values is pretty trivial.

---

### Post by Ubuntist on 2006-04-05
[QUOTE=jingo811]****
But does anybody in here now of any open-source equivalence  of Matlab for Linux?[/QUOTE]

You might look at 

1. SciPy, an extension to Python ([www.scipy.org)](www.scipy.org)),
2. Octave ([www.gnu.org/software/octave)](www.gnu.org/software/octave)), or
3. SciLab ([www.scilab.org)](www.scilab.org)).

---

### Post by jingo811 on 2006-04-05
**thumper>>>**
> wrt 5 what is your definition of fast? What is fast enough? Working with a 50 x 50 matrix of values is pretty trivial.
Oh when I wrote 
> And then it has it's built-in functions to deduct rows or columns pretty fast and easy.
Would programming such a function with C, Python, etc. be a total headache?
Especially if you have a 50x50 table containing random numbers.

By fast and easy I refered to Matlabs included functions for eliminating rows and columns, since C and python don't have preprogrammed mathematical functions within themselves.
In short I just wondered if C and python would be a headache if I would manually write similar mathematical functions simulating the matrice layout and operations as seen in Matlab language.
Don't know if that cleared things up or just messed things up even worse :)

---

