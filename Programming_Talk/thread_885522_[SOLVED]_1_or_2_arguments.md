---
title: "[SOLVED] 1 or 2 arguments???"
date: 2008-08-10
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-10
I got this thing, written in python:
```
class MyClass(object):
    def myfuction(argument):
        print str(argument)

myclass = MyClass()

myclass.myfunction(3)

```

Now, why it keeps telling me "myfunction takes exactly 2 arguments, only 1 given"?? :confused:

What is this? A bug in the python programming language? :( :confused: Or did I do something wrong? How to fix this??

---

### Post by Lster on 2008-08-10
[PHP]
class MyClass(object):
    def myfunction(this, argument):
        print argument

myclass = MyClass()

myclass.myfunction(3)
[/PHP]

I've bolded the changed bits.

I think, in Python, class functions take an extra parameter which is the class itself. I called that argument "this".

[http://docs.python.org/tut/node11.html](http://docs.python.org/tut/node11.html)

---

### Post by NovaAesa on 2008-08-10
This is right, but you don't have to "pass" that parameter in the traditional sense because it is automatically passed for you. This was one of the most confusing (and counter-intuitive) things that I found about Python.

---

### Post by ghostdog74 on 2008-08-10
@OP, its called "self". Please read the docs, especially the [tutorial](http://docs.python.org/tut/node11.html). Its explained.

---

### Post by nvteighen on 2008-08-10
What happens is that the "real way" to call an argument of a class function is like this:

[PHP]
a = MyClass(zzz)
MyClass.myfunction(a, argument)
[/PHP]

Test it, it will work! So, that's why you have to pass the object name as first argument when declaring the function inside the class. Usually, "self" is used, but you can choose "this" or whatever you like more; the only requirement is that you place it as first argument.

But, of course, instead of writing line 2, you can write a.myfunction(argument), which is the usual way to do this... Python will translate it for you.

---

### Post by crazyfuturamanoob on 2008-08-10
What are 'this' and 'self'? And which is the right answer? This, or self?

E: And I don't understand manuals, because I am a beginner (wasn't it obvious?), 
and my mother tongue is NOT english. So please do not offer me manuals. I don't read them.

E2: Could you post a single, clear, example, because all these different ways make me confused.

---

### Post by NovaAesa on 2008-08-10
The standard convention is to use "self". But you can really use whatever you are comfortable with. Some people like to use "this" instead because it reminds them of the good old days of C++ and Java.

---

### Post by ghostdog74 on 2008-08-10
> **crazyfuturamanoob said:**
> 
and my mother tongue is NOT english. So please do not offer me manuals. I don't read them.

this seems like an excuse and not a very good one. You post in English don't you? If you don't read manuals, how would you know how it works? In fact, the Python docs site has a link to [Non english documents](http://wiki.python.org/moin/Languages). 

> 
E2: Could you post a single, clear, example, because all these different ways make me confused.
follow what is written in the official docs and you should not go wrong. The doc uses "self".

---

### Post by nvteighen on 2008-08-10
You'd be surprised how many of us here aren't native English speakers...

---

### Post by crazyfuturamanoob on 2008-08-10
Ok I got it. Thanks.

I never make up good excuses.. :(
But manual are boring even if they are in my language, I just *can't* read them.

---

### Post by NovaAesa on 2008-08-10
[quote="nvteighen"]You'd be surprised how many of us here aren't native English speakers...[/quote]

I would say that most of the people here aren't (unless you include the tainted American version of Engish as real English). Lol, just kidding, English is English.

So what is your native tongue, crazyfuturamanoob? Chances are you language will be on the list that ghostdog74 provided.

---

### Post by fiddler616 on 2008-08-10
> **crazyfuturamanoob said:**
> 
E: And I don't understand manuals, because I am a beginner (wasn't it obvious?), 
and my mother tongue is NOT english. So please do not offer me manuals. I don't read them.
If nothing else, read a good [tutorial]("http://www.ibiblio.org/g2swap/byteofpython/read/index.html"), because you're a beginner, and if you don't have enough English for that, and can't be bothered to find translations, then please deal with that yourself.

---

### Post by nvteighen on 2008-08-10
If it's a Romance language, I'll be glad to help. Spanish (my native tongue), Italian (active/passive), Portuguese (passive), Catalan (passive), Galician (passive) and some French (also passive).

Ah, German too (both active and passive).

---

### Post by pmasiar on 2008-08-10
> **crazyfuturamanoob said:**
> E: And I don't understand manuals, because I am a beginner (wasn't it obvious?), 
and my mother tongue is NOT english. So please do not offer me manuals. I don't read them.

E2: Could you post a single, clear, example, because all these different ways make me confused.

So you basically require us to write you your custom book, because you cannot be bothered reading any of existing ones? And if you cannot read  English comfortably, maybe less arrogant way would be to ask for a good tutorial in any of language you do know how to read, instead of trashing all (good and valid) advice and letting us guess what language you prefer?

BTW as a beginner, don't waste time on OOP before you mastered basics, Python is not Java and you can get away without OOP (using existing classes but not creating your own) for quite a long time. Which information you would already know if you bothered to read guides linked in sticky...

Just because you did not found good intro books, it does not mean that they do not exist - just the opposite, they do, and sticky FAQ (my wiki) links to  best of them. It accumulates maybe a century of experience of different people. You ignore it at your own risk.

And if you want to become a hacker, you need to develop some tolerance to pain, endurance when  overcoming obstacles. Just now, obstacle you face is beginner tutorial - if you want to start your career by whining and looking for shortcuts, you may save time for us and yourself and just give up now. Seriously. Programming is hard (even if fun), and Python is as easy way to get there as it gets: if you do not believe me, try learning C++ instead :-)

---

### Post by pmasiar on 2008-08-10
> **NovaAesa said:**
>  This (self as required method parameter) was one of the most confusing (and counter-intuitive) things that I found about Python.

It is because you learned C++ way first, and you judge Python based on your pre-existing knowledge. For people learning C++, 'magical' reference to current instance must be introduced by reserved keyword, 'this'. And referencing instance's properties via self.x is IMHO much more obvious than checking up declaration is property is declared, or is it a method's internal variable.

Just because second language is different from the first you learned it does not mean it is wrong - quite possibly, old way might be less intuitive for beginners without your pre-existing knowledge.

---

### Post by crazyfuturamanoob on 2008-08-10
You seem to be very intrested in about my language, finnish. 

I have found some tutorials, and even one good book (I don't have it anymore, it was from library) in finnish, 
but there are so few finnish tutorials and books (which aren't even up-to date), that it is easiear to just ask here.

---

### Post by ghostdog74 on 2008-08-10
i find it odd, that you can post in English, or did someone write and translate for you? If you can read english, there's no reason you can't read english manuals.

---

### Post by nvteighen on 2008-08-10
> **crazyfuturamanoob said:**
> You seem to be very intrested in about my language, finnish.

Out of my scope! (Some Latin or Basque, maybe?)

---

### Post by pmasiar on 2008-08-10
> **crazyfuturamanoob said:**
> You seem to be very intrested in about my language, finnish. 

I have found some tutorials, and even one good book (I don't have it anymore, it was from library) in finnish, 
but there are so few finnish tutorials and books (which aren't even up-to date), that it is easiear to just ask here.

In fact, I **AM** interested in Finnish (I had even a private discussion with Finnish member of the forum, CptPicard). But of course I do not care about what is your mother language - only as far as knowing it might help me (or others) to give you better, more relevant advice. I do not judge others based on mother language: my original language is not English either :-) And spell-checker does help, even if not 100% :-)

Maybe if you did found good book, decent man's action would be to buy it and read it? Instead of asking us to write you one, for free? :-)

Of course it is easier to ask, but whole free software is based on 'paying forward': you cannot only leech without planning to give back. We help you as other helped us. But we also worked hard to learn what we know, did not expected from others wasting time on tasks we are better doing ourselves: ask for help, but do your own homework.

---

### Post by mssever on 2008-08-10
> **crazyfuturamanoob said:**
> E: And I don't understand manuals, because I am a beginner (wasn't it obvious?), 
and my mother tongue is NOT english. So please do not offer me manuals. I don't read them.
If you can't (or won't) understand manuals, then you won't be successful in learning programming (or even in learning Linux well). You might as well give up now.

---

### Post by NovaAesa on 2008-08-10
> **pmasiar said:**
> It is because you learned C++ way first, and you judge Python based on your pre-existing knowledge. For people learning C++, 'magical' reference to current instance must be introduced by reserved keyword, 'this'. And referencing instance's properties via self.x is IMHO much more obvious than checking up declaration is property is declared, or is it a method's internal variable.

Just because second language is different from the first you learned it does not mean it is wrong - quite possibly, old way might be less intuitive for beginners without your pre-existing knowledge.

Sorry if I came across a bit preachy about that. Actually, my first language was Visual Basic 6, my second was Python, my third Java, and my fourth was (is?) C++. That seemed like a fairly logical way to do things, from easier languages to harder ones (the VB was back from my Windows days :P). Python was my first foray into OOP (and even them I don't think I "got" it), and this thing with having a different number of variables in the member method declaration and where it is used I found very confusing. I remember sitting in front of my computer for 3 hours fiddling with this exact problem trying to work out what was going on. I guess the moral of the story is, unless you want to be frustrated by programming, read them manual! (I hope I don't get an infraction for that, I almost said that 4 letter acronym that we're not meant to say :P)

---

### Post by lisati on 2008-08-10
> **crazyfuturamanoob said:**
> What are 'this' and 'self'? And which is the right answer? This, or self?

E: And I don't understand manuals, because I am a beginner (wasn't it obvious?), 
and my mother tongue is NOT english. So please do not offer me manuals. I don't read them.

E2: Could you post a single, clear, example, because all these different ways make me confused.

[www.freetranslation.com](www.freetranslation.com) might be of some help.

---

### Post by pmasiar on 2008-08-10
> **NovaAesa said:**
> having a different number of variables in the member method declaration and where it is used I found very confusing. I remember sitting in front of my computer for 3 hours fiddling with this exact problem trying to work out what was going on.

That's why I advice every beginner to skip OOP and become competent procedural programmer first. Luckily with Python it is possible and easy, unlike Java or C++.

Couple months later, when defining a function or managing a loop is not a problem anymore, when you defined couple of your own complex data structures using dictionaries, you can look at OOP, read the manual, and it will just click. 

> I guess the moral of the story is, unless you want to be frustrated by programming, read them manual! ... I almost said that 4 letter acronym that we're not meant to say :P)

RTFM, which stands for Read The Fine Manual? :-) It's always the first advice :-)

---

### Post by NovaAesa on 2008-08-11
> **pmasiar said:**
> RTFM, which stands for Read The Fine Manual? :-) It's always the first advice :-)
I whole heartedly agree with you =]
The world would run much more smoothly if people would do that before asking for assistance! It's against the CoC though, hence the reason it's not the best thing to say around here :(

---

### Post by pmasiar on 2008-08-11
> **NovaAesa said:**
> [RTFM is] against the CoC though, hence the reason it's not the best thing to say around here :(

Not quite. RTFM will never get you into a problem if you accompany it with a link to FM which is supposed to be R.

---

### Post by fiddler616 on 2008-09-07
> **crazyfuturamanoob said:**
> You seem to be very intrested in about my language, finnish. 

I have found some tutorials, and even one good book (I don't have it anymore, it was from library) in finnish, 
but there are so few finnish tutorials and books (which aren't even up-to date), that it is easiear to just ask here.
I find it impossible to believe that there are no Python tutorials in Finnish.
It is ***NOT*** easier to just ask here! There is so much 'background' stuff you need to learn that asking for help on the forums for each and every thing would be time-consuming and inefficient (in addition to getting everybody mad at you).
This is one of those things where you try to back down and apologize as soon as possible, because the more arrogant, self-centered things (OK, OK, strong language, I'm sorry). Um, the more you try to rationalize yourself, the more exercised people are going to get.

---

