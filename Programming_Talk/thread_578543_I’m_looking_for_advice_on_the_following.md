---
title: "I’m looking for advice on the following:"
date: 2007-10-17
forum: Programming Talk
---

### Post by ithink2020 on 2007-10-17
This might be crazy, but…

I would like to start getting back into C++ programming.  I took a couple classes in collage several years ago, but haven’t used programming since. I’m looking for advice on the following:

1.	Your favorite supported C++ compiler for Ubuntu 
2.	Web sites that have good tutorials and examples to learn from and work on
3.	Someone who would be willing to mentor me via e-mail

My ultimate goal is to get back into programming and help on one or two open source projects that are out there.

---

### Post by xtacocorex on 2007-10-17
```
sudo apt-get install build-essential
```
will install the GNU compilers.
 
As for websites, [http://www.cplusplus.com/](http://www.cplusplus.com/) has a bunch of resources.
 
The sticky threads at the top of the sub-forum have a bunch of links for many different languages, including C++.

---

### Post by LaRoza on 2007-10-17
> **ithink2020 said:**
> This might be crazy, but&#8230;
1.	Your favorite supported C++ compiler for Ubuntu 
2.	Web sites that have good tutorials and examples to learn from and work on
3.	Someone who would be willing to mentor me via e-mail


My wiki, the stickies have all you need or want.

Have fun. If you want to explore other languages, I suggest Python or Perl, because they are much more useful for the most common programming tasks than C++.

My wiki has Ubuntu specific material, but all the tutorials and books (free) are universal.

I can answer a few questions, but for tasks you can PM me, or post on the forum, but attempt to solve problems yourself.

[http://laroza.pbwiki.com/](http://laroza.pbwiki.com/)

---

### Post by aks44 on 2007-10-17
> **ithink2020 said:**
> 3.	Someone who would be willing to mentor me via e-mail

Just post your problems here and you'll be sure to have an answer. :)

The advantage of the forums over e-mail is that other people may benefit from it.


EDIT: LaRoza's advice "*attempt to solve problems yourself*" is the best way IMHO to truly learn: tinker with it, fail, tinker, fail, ask for advice (very important :p), get an explanation, now you *really* know it. ;)

---

### Post by scruff on 2007-10-17
I would like to offer a contradictory opinion to LaRoza. Though you have already expressed your interest in C++, I'd just like to say that I learned several scripting languages (perl, python, bash) before getting into a more serious language like C++ and if I could do it over again, I would have learned C++ first for discipline and solid technique, THEN something like Python. 

Now I am *not* knocking Python. It is an awesome language. However, it does allow too much freedom in the sense that you can get away with extremely sloppy habits that will be harder to break if you move on to something like C or C++.

Start difficult, and easy will become that much easier. Start easy and difficult will become even more so :)

Just my 2 cents...

---

### Post by mjwood0 on 2007-10-17
> **scruff said:**
> I would like to offer a contradictory opinion to LaRoza. Though you have already expressed your interest in C++, I'd just like to say that I learned several scripting languages (perl, python, bash) before getting into a more serious language like C++ and if I could do it over again, I would have learned C++ first for discipline and solid technique, THEN something like Python. 

Now I am *not* knocking Python. It is an awesome language. However, it does allow too much freedom in the sense that you can get away with extremely sloppy habits that will be harder to break if you move on to something like C or C++.

Start difficult, and easy will become that much easier. Start easy and difficult will become even more so :)

Just my 2 cents...

It's odd really.  Trying to learn python I'm constantly confused how I don't have to declare anything a specific type or to cast things when changing types.  It's really nice in a way, but you're right.  The strict type casting of C (or insane typing of Ada) really is a different mindset.

---

### Post by pmasiar on 2007-10-18
It depends on you pain treshold.

Looks like your treshold is pretty high, and you do enjoy the pain. I have more urgent tasks that to figure out how to cast things. IMHO it is up to computer to remember what those are, and do it for me.

Or, as one young Python learner said when I shown him "hello world" in Java: "I pity the fools programming in this crap". he was not impressed. :-)

---

### Post by aks44 on 2007-10-18
> **pmasiar said:**
> I have more urgent tasks that to figure out how to cast things. IMHO it is up to computer to remember what those are, and do it for me.

If you need to cast between types, you're probably doing something wrong (or even something Evil).
The whole point of static typing, IMHO, is to remind the feeble human that an Apple is not a Banana (even though both are a Fruit) and to enforce it. Anyone trying to handle an Apple like a Banana is insane from a design POV, it just means that you badly designed the Fruit parent class.

Just my two cents ;)

---

### Post by Wybiral on 2007-10-18
> **pmasiar said:**
> Or, as one young Python learner said when I shown him "hello world" in Java: "I pity the fools programming in this crap". he was not impressed. :-)

You showed "hello world" to Mr. T? :)

---

### Post by pmasiar on 2007-10-18
> **aks44 said:**
> If you need to cast between types, you're probably doing something wrong (or even something Evil).

I do web programming. When fighting with Struts framework, I often need to pack bunch data in some universal container, and unpack it somewhere else (because in Java, unlike Python, you cannot return multiple values - it has to be a container). And this happens all the time and I cannot be bothered to invent type for it each time. maybe i am too lazy or not enough OO. :-) Or maybe I want just get my job done.

> The whole point of static typing, IMHO, is to remind the feeble human that an Apple is not a Banana (even though both are a Fruit) and to enforce it. 

You have it completely wrong. Whole point of static typing is to inflict you as much pain on feeble humans as possible, BWAHAHAHAHA! And they will come back to ask for more! :twisted:

---

