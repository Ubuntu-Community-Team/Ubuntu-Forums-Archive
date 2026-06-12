---
title: "Beginner at C++, looking for information (Exercises)"
date: 2010-02-04
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-04
Hello World;

The times I have entered Hello World into C++ must be countless, but that doesn't mean I haven't been playing around. I am a university student in the UK and I am doing a Bachelor of Science in Information Communication Technology. Unfortunately, this hasn't helped in my desire to become a programmer as much as I thought it would. In fact I was incredibly naive.

One major disadvantage was the fact that on one particular module, my primary language was Java. Unfortunately I found Java to be a clunky unyielding programming language which left much to be desired, perhaps a major factor in my disapproval for this language lay in how the module was taught and by whom. Later I rediscovered my desire to learn a language and off I went, only later finding that C++ would be a better programming language to learn. 

It was around this time that I felt that learning C++ isn't something done in a lecture but something someone should do in their own free time and not because they need to learn a language but because they feel the desire to learn it. This is where my query comes in. 

After running through numerous tutorials I have found them to slowly become tedious, now that's not because they're not useful, it's because I'm not doing anything with the knowledge and in order to learn a language being productive with that language is key. (Perhaps why I'm still familiar with the basics of Japanese). 

What I'd like to know is, are there any exercises out there that I could use to help improve my knowledge of C++, programs that are functional and do things perhaps? But something on the level of a beginner -> medium. I don't mean tutorials, because I have found numerous adequate supplies of tutorials on the net. 

An example of an Exercise would be to: Correct the programming in this code. (The solution would be to insert an extra line of code, correct syntax etc) or another exercise could be "Modify the programming to change the functionality from that of a number search to a word searcher." The solution being to change the input section to String/Char input instead of Int input, and change the present data from numbers to words? 

If anyone can help or supply basic exercises or feel they want to see just how often I've read through the tutorials, please let me know. 

if (forum == false)
{ 
cout << "Let a moderator know";
}

---

### Post by ibuclaw on 2010-02-04
A nice site for mental challenges that will help you learn a language inners, cans and cants.
[http://projecteuler.net/](http://projecteuler.net/)

Regards
Iain

---

### Post by Ravenshade on 2010-02-04
Interesting, this looks more like a Haskell place, which has it's use in my current field of study on the face of it at least. I'll report back after using it. Thanks for the input.

---

### Post by Queue29 on 2010-02-04
> **Ravenshade said:**
> Interesting, this looks more like a Haskell place, which has it's use in my current field of study on the face of it at least. I'll report back after using it. Thanks for the input.

It's not language specific at all. A lot of mathematicians do those problems with pencil and paper. I managed to get to level 1 on c++ alone, but switched to Java/Python to make life easier. Those problems will force you to learn how to use the gmp (or other big integer libraries), but not much else about how to program. They're math problems solved using CS as a tool, not the kind of problems used to teach CS.

If you want CS problems, I suggest javabat: [http://javabat.com/](http://javabat.com/)

Yes, it's java and not c++, but at your level, that's irrelevant. The syntax necessary to solve these problems is nearly identical.

---

### Post by Ravenshade on 2010-02-04
I am...struggling with Project Euler. I thought my math was good, I came out of school with decent GCSE grades (UK grades) a B...I was always in the higher set. Yet the easiest question is eluding me *sigh*

On the other hand, it did give me valuable insights into how the syntax forms and what I can do with different variables to make them do different things. Unfortunately, not being able to figure out the formulae has contributed to my downfall on that subject and I have a small stack of paper with notes, trying to crack the formula by reverse engineering. 

I've even got someone who's better at the subject than myself >.> and she's still working at it. Bless her heart. 

Maybe someone with a degree in the subject might be able to help >_<

On a more programming note, I'll be sure to look into that site.

---

### Post by Queue29 on 2010-02-05
The trick for #1 is the % operator, which returns the remainder of int division between two numbers. For example, 44%2 will return 0, because 2 is a **factor **of 44. 

Enough of a hint?

---

### Post by abhilashm86 on 2010-02-05
i'm on your same way, try this, more of real world problems....[http://uva.onlinejudge.org/](http://uva.onlinejudge.org/)

---

### Post by Ravenshade on 2010-02-05
Thanks again!

Unfortunately Queue % isn't one of my strong suits. So far I've managed to do #1 using this method

```

int y = 0;
int yresult = 0;

while (y<10)
{
y=y+3 //to solve multiples of three
yresult = yresult + y //adds to total
}


```The solution to multiples of five goes the exact same way. Unfortunately, I keep getting an extra multiple... >.< 

I haven't done factors in so damn long, only just relearned what a factorial was. o_o. The things you forget when you go to a rubbish college.

EDIT::

Maybe I'm a little thick but I can't solve the problems on either site. I am a complete novice at C++ compared to those problems.

---

