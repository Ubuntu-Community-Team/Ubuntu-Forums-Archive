---
title: "Need a hint"
date: 2008-03-08
forum: Programming Talk
---

### Post by baumgc on 2008-03-08
This is a part of a homework assignment. I read the sticky, and I think this is acceptable. I don't want an answer, but I would appreciate a point in the right direction:

I have three doubles in a set like following:
(3.2,5.3,6.1)

How could I pull out the doubles and toss out the "(,,,)"

This is C/C++.
Thanks and I won't be offended if no one responds.

---

### Post by Jessehk on 2008-03-08
What do you mean, you have them "in a set"?

Are they in an array, or formatted that way in a text file? Or something else?

---

### Post by baumgc on 2008-03-08
They are in a txt input file.
I have the getline, they come in fine.

I need to take each number out separately and assign it to a double that I have ready for them.

EDIT:
It's like this:
I  (1.1,2.2,3.3)
D (4.4,5.5,6.6)
D (7.7,8.8,9.9)

I have the I's and D's dealt with. What I would like is a link to a site that might have a method or some generic code that I can adapt to my problem.

---

### Post by LaRoza on 2008-03-08
> **baumgc said:**
> They are in a txt input file.
I have the getline, they come in fine.

I need to take each number out separately and assign it to a double that I have ready for them.

What language are you using? You gave two.

---

### Post by baumgc on 2008-03-08
C++ for all intensive purposes. 
We've just started getting into the C++ elements right now, but we've been using C up to this point.
This is what my professor says anyway

EDIT: There can be any number of spaces between everything, here's an example:
I _____________(2.2_________,___1.2, 4.6_________) where _ = whitespace

I could do it easy with just: I (2.2,1.2,4.6), using ignores or something, but the code wouldn't be generic enough. This is where I'm having trouble.

---

### Post by LaRoza on 2008-03-08
> **baumgc said:**
> C++ for all intensive purposes. 
We've just started getting into the C++ elements right now, but we've been using C up to this point.
This is what my professor says anyway.

Your professor probably doesn't understand C++ then, as it is an entirely different language.

See scanf and fscanf for C.

---

### Post by baumgc on 2008-03-08
> **LaRoza said:**
> Your professor probably doesn't understand C++ then, as it is an entirely different language.

See scanf and fscanf for C.

It was my professor last semester.
He said: "C++ = C, C++ has classes, templates, objects, overloading and polymorphism." 
I'm pretty sure that's what he said, but 

Regardless, scanf looks good. I'll see what I can do with it. Anything else?

---

### Post by LaRoza on 2008-03-08
> **baumgc said:**
> It was my professor last semester.
He said: "C++ = C, C++ has classes, templates, objects, overloading and polymorphism." 
I'm pretty sure that's what he said, but 

Regardless, scanf looks good. I'll see what I can do with it. Anything else?

fscanf :)

That should be all you need to get started :)

[http://en.wikipedia.org/wiki/Scanf](http://en.wikipedia.org/wiki/Scanf)

As a note:

C++ == C++
C == C
Objective-C = C + Objects.

C++ is not a super set of C, Objective-C is though.

C++ was based off C, and is large compatible with it, but it is very different and should be kep separate.

---

### Post by baumgc on 2008-03-08
Thanks, I'll roll with it and see what happens.

---

### Post by LaRoza on 2008-03-08
> **baumgc said:**
> Thanks, I'll roll with it and see what happens.

Good luck :)

I always wondered what a programming class would be like...

---

### Post by baumgc on 2008-03-08
> **LaRoza said:**
> Good luck :)

I always wondered what a programming class would be like...

*shakes fist*
You people and your ability to teach yourself!

It's not easy. I know it's what I want to do, but we had a rough first semester with some random guy they pulled from texas a week before school started. 
He talked about being a certified public accountant more than programming.

Anyway, as an 18 year old, freshly in college, with no previous knowledge of programming,.... with that old bumbling dolt. 

Okay, I'm done complaining.

---

### Post by CptPicard on 2008-03-08
Better get used to "teaching yourself" -- it's the geek way, and the best way. :)

As a matter of fact, I learned all sorts of other interesting stuff in my CS degree. Like, what to code, and most importantly, of what kind of pieces so that you don't reinvent the wheel. "Programming" I always learned myself, never from class...

---

### Post by LaRoza on 2008-03-08
> **baumgc said:**
> *shakes fist*
You people and your ability to teach yourself!

It's not easy. I know it's what I want to do, but we had a rough first semester with some random guy they pulled from texas a week before school started. 
He talked about being a certified public accountant more than programming.

Anyway, as an 18 year old, freshly in college, with no previous knowledge of programming,.... with that old bumbling dolt. 

Okay, I'm done complaining.

You will see soon that you will be able to teach yourself more than the school.

Now, the school will be helpful in other areas, project management, algorithms, data structures and such.

Learning a language is easy, using it, that is hard :)

I am 20, freshly out of college.

---

### Post by CptPicard on 2008-03-08
> **LaRoza said:**
> 
I am 20, freshly out of college.

Congrats, re age++. :)

---

### Post by LaRoza on 2008-03-08
> **CptPicard said:**
> Congrats, re age++. :)

Thanks, it was in early February (it isn't on my profile, and I didn't mention it explicitly)

---

### Post by baumgc on 2008-03-09
> **CptPicard said:**
> Congrats, re age++. :)

I thought you were talking to me.
My birthday was 2 days ago. Didn't think my birthday was out in the open..., so thought you were a stalker!

I emailed my professor and he said scanf could be used but he had other things in mind.

He said atof, and nothing else.
I can't figure out how to use it however.

---

### Post by LaRoza on 2008-03-09
> **baumgc said:**
> I thought you were talking to me.
My birthday was 2 days ago. Didn't think my birthday was out in the open..., so thought you were a stalker!

I emailed my professor and he said scanf could be used but he had other things in mind.

He said atof, and nothing else.
I can't figure out how to use it however.

atof is "ascii to float", it will be able to convert an ascii character to a number.

I think fscanf is the better way.

float x = atof("20")

Happy birthday :)

---

