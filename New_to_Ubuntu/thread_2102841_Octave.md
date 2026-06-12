---
title: "Octave"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by rk101 on 2013-01-08
Hi,

I'm a beginner with Octave and I'm trying to come up with an octave script that actually works.

Could someone kindly tell me what a semicolon means in lets say:
global w = 200;

Thanks

---

### Post by Isaacmarritt on 2013-01-08
i am only a lower end amouture at. .coding but i think it means thats the end of the code

---

### Post by kaushikgaurav on 2013-01-08
> **rk101 said:**
> Hi,

I'm a beginner with Octave and I'm trying to come up with an octave script that actually works.

Could someone kindly tell me what a semicolon means in lets say:
global w = 200;

Thanks
If Octave is the open source version of matlab,

Then ; after any command will hide the result till you recall them.

eg:

w = 200
the response will be printed as "w = 200" in very next line.
This is seldom useful and more often you want to just assign the value to a variable and not print it all the time

Now if you do not want the program to print that result instantaneously then, you should use ; after w = 200.

w = 200;
with this you will have assigned the value of 200 to w but it will not print unless you ask it to.

Chao!
Gaurav

---

### Post by steeldriver on 2013-01-08
yes in most contexts it just suppresses echoing of output from the preceding command e.g.

```
octave:3> x = 100
x =  100
octave:4> x = 100;
octave:5> 

```

It's the same behavior as MATLAB
[http://www.mathworks.com/help/matlab/matlab_prog/symbol-reference.html#bsgigzp-46](http://www.mathworks.com/help/matlab/matlab_prog/symbol-reference.html#bsgigzp-46)

---

### Post by rk101 on 2013-01-09
Thank you everyone for your replies!

---

