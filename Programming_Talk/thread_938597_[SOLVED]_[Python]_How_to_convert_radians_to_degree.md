---
title: "[SOLVED] [Python] How to convert radians to degrees? Or degrees to radians?"
date: 2008-10-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-05
How to convert radians to degrees or degrees to radians? :confused:

---

### Post by ad_267 on 2008-10-05
degrees = 180 * radians / pi

radians = pi * degrees / 180

Just remember that pi radians is 180 degrees.
The wikipedia page explains it all: [http://en.wikipedia.org/wiki/Radians](http://en.wikipedia.org/wiki/Radians)

In python you can use math.pi to get a value for pi.

---

### Post by cpetercarter on 2008-10-05
A google search for "convert degrees to radians" will tell you that	
1 degree = 0.0174532925 radians, and point you to a number of online converters.

---

### Post by pp. on 2008-10-05
> **ad_267 said:**
> Just remember that pi radians is 180 degrees.

Or - in other words - the circumference of a circle with a radius of one is 2*pi, and the angle covered by a full circle is 360°.

---

### Post by crazyfuturamanoob on 2008-10-05
Is this correct?
```

def rad2deg(radians):
	pi = math.pi
	degrees = 180 * radians / pi
	return degrees
def deg2rad(degrees):
	pi = math.pi
	radians = pi * degrees / 180
	return radians

```

---

### Post by Rhubarb on 2008-10-05
Yes that looks correct crazyfuturamanoob.

---

### Post by LaRoza on 2008-10-05
> **crazyfuturamanoob said:**
> Is this correct?
```

def rad2deg(radians):
	pi = math.pi
	degrees = 180 * radians / pi
	return degrees
def deg2rad(degrees):
	pi = math.pi
	radians = pi * degrees / 180
	return radians

```

Correct, but smelly.

What is with the pi = math.pi?

If you don't want to qualify a namespace, then import math.pi with "from math import pi" then you can use "pi" alone. However, the better way to do it, I think, is this way:

```

def rad2deg(radians):
	degrees = 180 * radians / math.pi
	return degrees
def deg2rad(degrees):
	radians = math.pi * degrees / 180
	return radians

```

---

### Post by issih on 2008-10-05
The point of radians as a measurement system is that the angle in radians multiplied by the radius of a circle gives you the arc length around the perimeter of that circle contained by the angle.

Therefore, as the total circumference of a circle is 2*pi*radius, there are by definition 2*pi radians in one circle.

i.e:
    2*pi radians = 360 degrees 
therefore:
    pi radians = 180 degrees

its always easier to remember why something is what it is than remember an abstract number in my opinion :)

Hope that helps

---

### Post by Wybiral on 2008-10-05
Why don't you just use the math module?

```

import math
print math.radians(90)
print math.degrees(1.5707963)

```

---

### Post by pmasiar on 2008-10-05
...or instead of both pi=math.pi or just plain math.pi, use:

from math import pi

8-)

Wyb's solution is the proper one. Use libraries, they are there for a reason (call C code for arithmetics).

---

### Post by ghostdog74 on 2008-10-06
> **Wybiral said:**
> Why don't you just use the math module?

because then , Python will make him forget his elementary maths. :)

---

### Post by crazyfuturamanoob on 2008-10-06
elementary maths!?!?!? they haven't even taught me da trinometrics yet, nor radians

---

### Post by mike_g on 2008-10-06
IMHO calling functions for something so simple holds no real benefit. By inlining it the code will run faster w/o affecting readabliy:
```
DEG_TO_RAD = 0.0174532925
...
num *= DEG_TO_RAD
```

---

### Post by LaRoza on 2008-10-06
> **mike_g said:**
> IMHO calling functions for something so simple holds no real benefit. By inlining it the code will run faster w/o affecting readabliy:


IMO optimising this is very premature.

---

### Post by mike_g on 2008-10-06
To me it is just as descriptive and requires no extra code, so why not use what works faster?

---

### Post by LaRoza on 2008-10-06
> **mike_g said:**
> To me it is just as descriptive and requires no extra code, so why not use what works faster?

This is not more clear:

num *= DEG_TO_RAD

It works when you know Degrees and Radians, and how to convert, but for someone less familiar, it will be more confusing.

To you it is description, yes, but in programming, one should keep in mind often that others will be reading the code and if there is the possibility others will, it shouldn't be specific to oneself and a function with a short descriptive name and a good docstring is better.

---

### Post by ghostdog74 on 2008-10-06
> **LaRoza said:**
> This is not more clear:

num *= DEG_TO_RAD

It works when you know Degrees and Radians, and how to convert, but for someone less familiar, it will be more confusing.

i know something like radian(arg) looks nicer and understandable than num*=DEG_TO_RAD, however if OP is learning about maths using programming as a tool, it will not do him/her any good if shortcuts like radians, pow etc are used.

---

### Post by LaRoza on 2008-10-06
> **ghostdog74 said:**
> i know something like radian(arg) looks nicer and understandable than num*=DEG_TO_RAD, however if OP is learning about maths using programming as a tool, it will not do him/her any good if shortcuts like radians, pow etc are used.

I am talking more about general programming.

As noted, Python came with everything needed for the task, and doing it manually is a good exercise for those wanting to learn.

In the field though, using the standard library and explicit code is the best I think.

---

### Post by ghostdog74 on 2008-10-06
> **LaRoza said:**
> I am talking more about general programming.

As noted, Python came with everything needed for the task, and doing it manually is a good exercise for those wanting to learn.

In the field though, using the standard library and explicit code is the best I think.
i am talking more about OP's general understand. If you read his posts, i think i remembered he's just 14 or 15 and then he hasn't been taught trigo. Do you think advising him to use radians() , pow() and the shortcuts is good for his understanding of basic math concepts? I also understand what you are talking about, but let's just leave it till maybe OP's in the working world or at least passed his basic maths in school

---

### Post by Wybiral on 2008-10-06
> **mike_g said:**
> IMHO calling functions for something so simple holds no real benefit. By inlining it the code will run faster w/o affecting readabliy:
```
DEG_TO_RAD = 0.0174532925
...
num *= DEG_TO_RAD
```

This is a function call too...

It looks like this: num = num.__mul__(DEG_TO_RAD)

:)

---

### Post by Wybiral on 2008-10-06
> **ghostdog74 said:**
> i am talking more about OP's general understand. If you read his posts, i think i remembered he's just 14 or 15 and then he hasn't been taught trigo. Do you think advising him to use radians() , pow() and the shortcuts is good for his understanding of basic math concepts? I also understand what you are talking about, but let's just leave it till maybe OP's in the working world or at least passed his basic maths in school

Well, the OP didn't go to a math forum, they went to a programming forum. And a smart programmer will use the standard functions. They can learn on their own time, I was just answering a question.

---

### Post by ghostdog74 on 2008-10-06
> **Wybiral said:**
> And a smart programmer will use the standard functions. They can learn on their own time, I was just answering a question.

nobody said using standard functions is wrong. Its just not suitable at this moment in time.

---

### Post by issih on 2008-10-06
For any half decent optimising compiler running anything but the most intensive floating point calculations the differences will be utterly inconsequential.

Therefore I say go with readability and stick to standards as much as possible.

In the end though, if it works, its up to you

---

### Post by Wybiral on 2008-10-06
> **ghostdog74 said:**
> nobody said using standard functions is wrong. Its just not suitable at this moment in time.

OK, I just didn't know I needed to be a patient math teacher to answer simple programming questions :p

---

### Post by mike_g on 2008-10-06
> This is a function call too...

It looks like this: num = num.__mul__(DEG_TO_RAD)
Oh, in that case I guess it makes no difference then. I dident know thats how it works in Python :)

---

### Post by nvteighen on 2008-10-06
> **ghostdog74 said:**
> nobody said using standard functions is wrong. Its just not suitable at this moment in time.

No, nobody said that... but how can you say this is not suitable for using standard functions? If this is not the case, which one will be? If a language gives you a facility, use it! It's there to help you, otherwise either you're using the wrong language (which doesn't seem the case) or you're misusing the language by not using what it gives you...

---

### Post by LaRoza on 2008-10-06
> **ghostdog74 said:**
> i am talking more about OP's general understand. If you read his posts, i think i remembered he's just 14 or 15 and then he hasn't been taught trigo. Do you think advising him to use radians() , pow() and the shortcuts is good for his understanding of basic math concepts? I also understand what you are talking about, but let's just leave it till maybe OP's in the working world or at least passed his basic maths in school

I get your point, although I think if someone doesn't know the math, the calls to radians(), etc make more sense, as they "just work".

Excel (I just had a course in at college, so I can use it as an example, OO probably has similiar things) has many functions built in. The most useful I think are the financial ones. It can do complex economic calculations with only a few arguments. Sure, I know squat about how it works, but that wasn't what I was doing.

Now, as a learning device, you are right, but from a programming standpoint, not knowing the inner workings of a function (only its argument(s) and return value) is a plus I think.

---

### Post by pp. on 2008-10-06
> **LaRoza said:**
> from a programming standpoint, not knowing the inner workings of a function (only its argument(s) and return value) is a plus I think.

Generally, yes. That also gives rise to some epic fails if you not only don't know how the function is implemented but also haven't a clear understanding of what it actually does.

---

### Post by LaRoza on 2008-10-06
> **pp. said:**
> Generally, yes. That also gives rise to some epic fails if you not only don't know how the function is implemented but also haven't a clear understanding of what it actually does.

That is why I mentioned the arguments and return value.

---

### Post by Canis familiaris on 2008-10-06
> **LaRoza said:**
> 
Now, as a learning device, you are right, but from a programming standpoint, not knowing the inner workings of a function (only its argument(s) and return value) is a plus I think.
Why?
Maybe yes if limited to hardcore mathematics, but take case of Strings i n C. Knowing the inner working of functions such as strcpy, strcmp, strrev helps a lot in understanding the concepts of strings in C. Isn't it?

---

### Post by LaRoza on 2008-10-06
> **Anurag_panda said:**
> Why?
Maybe yes if limited to hardcore mathematics, but take case of Strings i n C. Knowing the inner working of functions such as strcpy, strcmp, strrev helps a lot in understanding the concepts of strings in C. Isn't it?

There are no strings in C, they are arrays. Understanding the concept, yes, but if I know that function() does what I want, I don't need to know how.

So, to solve a math problem, one uses a computer to find the answer, not learn how to find the answer.

---

### Post by Canis familiaris on 2008-10-06
> **LaRoza said:**
> There are no strings in C, they are arrays. Understanding the concept, yes, but if I know that function() does what I want, I don't need to know how.
Strings are arrays of type char in C. ;)

> 
So, to solve a math problem, one uses a computer to find the answer, not learn how to find the answer.

For a user Yes. For a Programmer - Depends.

---

### Post by LaRoza on 2008-10-06
> **Anurag_panda said:**
> Strings are arrays of type char in C. ;)

They are still just arrays. 

> 
For a user Yes. For a Programmer - Depends.

It depends on the programmer. A math or science person using program for their own ends, would likely know already the internal workings of the algorithm used and would obviously know the ones they write themselves. A person hired to program for scientists wouldn't need to know beyond what they had to write. If scientist B said to write a program which takes the result of this experiment, multiplies it by pi then writes the answer to a database with the experiment number, the programmer just has to know pi is a number and found in math.pi (this is very simplified, most people would know something about pi). Calculating pi or understanding its history isn't important. Same thing with more advanced things. If I had to write an algorithm to do trig, which I am not not strong in anymore, I could do it with a reference book and the standard library and get it working without needing to really understand what the uses or whys of trig.

---

### Post by ghostdog74 on 2008-10-06
> **nvteighen said:**
> No, nobody said that... but how can you say this is not suitable for using standard functions? 

i said its not suitable because judging from OP's post history and the fact that he mentioned he is not taught trigo yet, giving him a shortcut answer like radians() will not help him learn his basic maths at all.
 
> 
If this is not the case, which one will be? If a language gives you a facility, use it! 

i didn't say you can't. Just not the right method to teach OP at the moment. I am sure i do not need to emphasize that again.

---

### Post by nvteighen on 2008-10-07
> **ghostdog74 said:**
> i said its not suitable because judging from OP's post history and the fact that he mentioned he is not taught trigo yet, giving him a shortcut answer like radians() will not help him learn his basic maths at all.
 

i didn't say you can't. Just not the right method to teach OP at the moment. I am sure i do not need to emphasize that again.
Ah, thanks. I misunderstood; I though you were talking about the Std. Lib.!

And yes, even though you could use trigonometric functions in a program without knowing any trigonometry, the best would be to first learn it and then program. Specially because trigonometric functions have such amount of interrelations that knowing the most basic and trivial (e.g. sin²(x) + cos²(x) = 1 or csc(x) = 1/sin(x)) will help you to analyse the problem better... maybe not for the specific OP's current problem, but possibly for those in the future.

---

### Post by ghostdog74 on 2008-10-07
> **nvteighen said:**
> the best would be to first learn it and then program.
exactly :)

---

