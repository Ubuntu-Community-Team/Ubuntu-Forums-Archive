---
title: "Perl Help"
date: 2007-11-25
forum: Programming Talk
---

### Post by tennvolsmb on 2007-11-25
Okay, so I completely new to perl and I was wondering how to even get started programming with it... Can anyone please help. Do not be rude, I am a beginner just like you once were.

---

### Post by Majorix on 2007-11-25
I have a friendly reminder here; have you also considered learning Python or Ruby? Especially Python is easier to learn and is more widely used in Ubuntu. But if you insist on learning Perl, you could just google "perl tutorial" and I am sure one of them would fit your needs. Cheers.

---

### Post by LaRoza on 2007-11-25
My wiki.

I am assuming you have a reason to learn Perl, although my preference is Python.

---

### Post by tennvolsmb on 2007-11-25
well i have heard perl is better... im trying to learn C and i've heard a good alternate language is perl which makes C easier to learn

---

### Post by LaRoza on 2007-11-25
> **tennvolsmb said:**
> well i have heard perl is better... im trying to learn C and i've heard a good alternate language is perl which makes C easier to learn

You are digging yourself in deep here. Neither are easy to learn as a first language.

Python is better (in my opinion) for many reasons, the one that matters to you is that it is easy to learn, when compared to Perl or C.

Python will enable you to learn programming, without worrying what all of Perl's funny characters mean.

Python is has a different syntax than Perl and C, but it isn't that different:

C
[php]
int factorial(int number)
{
    if (number == 1 || number < 0)
    {
        return 1;
    }
    else
    {
        number *= factorial(number-1);
        return number;
    }
}
[/php]

Python:
[php]
def factorial(number):
    if number == 1 or number < 0:
        return 1
    else:
        number = number * factorial(number-1)
        return number
[/php]

---

### Post by tyoc on 2007-11-25
Some links: 
[http://del.icio.us/soytyoc/dev:learn:perl](http://del.icio.us/soytyoc/dev:learn:perl)

arggg!!!!
```
 http://del.icio.us/soytyoc/dev:learn:perl
``` (I have read little of them).

---

### Post by Siph0n on 2007-11-25
If your trying to learn C, why not just read up on C? There are tons of tutorials and documentation for most of the languages out there...

---

### Post by ThinkBuntu on 2007-11-26
I think that a beginner can certainly start with Perl, especially because of the principle of TMTOWTDI (There's More Than One Way To Do It). This will make things very flexible and allow you to work comfortably in the earlier stages. I remember learning some Perl at age 11, and I didn't find it particularly tough as a first language, I just lost steam because I couldn't get the proper environment on Mac OS 9. As far as funny characters, you'll see $ (scalar) also used in PHP to precede $variables. @ is for @arrays, and % is for %hashes. I'm hazy on what hashes are for, but you get the idea.

I will say this: $ and @ (and %, I guess) make code more readable for me. Although there are many more things in Python and Ruby to make them very readable, these immediately flag the word as an array or scalar variable, which can be very useful when going into someone else's code and working with a small portion.

---

### Post by LaRoza on 2007-11-26
> **ThinkBuntu said:**
> As far as funny characters, you'll see $ (scalar) also used in PHP to precede $variables. @ is for @arrays, and % is for %hashes. I'm hazy on what hashes are for, but you get the idea.


A hash is like a Python dictionary, and is often called an Associative Array. It is an array but with a user defined index.

There are more "funny characters", and they do help sometimes, but they are not needed, and only add more to remember in my opinion.

---

### Post by slavik on 2007-11-26
> **LaRoza said:**
> A hash is like a Python dictionary, and is often called an Associative Array. It is an array but with a user defined index.

There are more "funny characters", and they do help sometimes, but they are not needed, and only add more to remember in my opinion.
what is $blah? a scalar ...
what is @$blah? a dereferenced array. (meaning that $blah is being treated as a reference to an array) :)

---

### Post by nhandler on 2007-11-26
Aside from html, perl was the first real language I learned. I didn't find it too difficult. [This](http://www.sthomas.net/oldpages/roberts-perl-tutorial.htm) guide really helped me learn.

My piece of advice for you is to set a goal. Come up with a program that you would like to make. Then, start by learning the bits of perl that are needed for your project. By the time you are done, you will know most of the basics of perl. That is how I learned. My project was an AIM robot.

---

### Post by shawnhcorey on 2007-11-26
> **Majorix said:**
> I have a friendly reminder here; have you also considered learning Python or Ruby? Especially Python is easier to learn and is more widely used in Ubuntu. But if you insist on learning Perl, you could just google "perl tutorial" and I am sure one of them would fit your needs. Cheers.

Thank you for that spam.  Python is just as difficult to learn as any other programming language.  That's because it is a programming language; it is capable of implementing a [Universal Turing Machine]("http://en.wikipedia.org/wiki/Universal_turing_machine").

But if you want help with Perl, I suggest you sign up to the [perl.org]("http://www.perl.org/") mailing list for [beginners]("http://lists.cpan.org/showlist.cgi?name=beginners").  It's not a tutorial but you can get answers to your questions there, like "I want to learn Perl, can you give me some on-line tutorials?"

For a beginner programmer, I recommend any modern language like Perl, Python, or Ruby.  That's because they take care of a lot of the bookkeeping; they let you concentrate on programming.

---

### Post by pmasiar on 2007-11-29
> **shawnhcorey said:**
> Python is just as difficult to learn as any other programming language.  That's because it is a programming language; it is capable of implementing a [Universal Turing Machine]("http://en.wikipedia.org/wiki/Universal_turing_machine").

Not true. Even if language is turing-complete, it does not mean there are no differences in difficulty of learning them. ASM is Turing-complete too. :-)

That said, Perl and Python are quite similar: dynamically typed garbage-collected languages. Python wins a little in readability, and with strong typing, "1" + 1 is error in Python. Other confusing concepts in Perl is variable auto-vivification, and list/scalar context difference.

> 
For a beginner programmer, I recommend any modern language like Perl, Python, or Ruby.

Agree. Perl makes more sense to experienced admins, who are used to shell , awk, sed etc syntax, Python is more beginner-friendly, IMHO.

---

