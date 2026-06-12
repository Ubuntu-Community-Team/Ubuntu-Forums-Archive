---
title: "C, c++"
date: 2011-12-22
forum: Programming Talk
---

### Post by kurotensai on 2011-12-22
Is c++ a better c? Which language do u prefer between c and C++ and why?

---

### Post by Petrolea on 2011-12-22
Can't answer the first question. 

And between C and C++ I prefer C. Many reasons why, but it's too late at night and I really don't feel like writing much now.

---

### Post by robgraves on 2011-12-22
Correct me if I'm wrong as I'm still learning C and C++, but the impression I get is they are essentially siblings, as C++ is C with Object Oriented Programming added, so if you write a program that didn't need the OOP aspect of C++ it would be C (or could be C, again I'm a noob with this myself) whereas if you needed the OOP aspects, you would be more inclined towards C++, but the compiler has to support C++...just my guess at answering that question.

---

### Post by lisati on 2011-12-22
My understanding is that C++ started life as "C with classes" (or something of that nature) and then evolved into a programming language in its own right.

---

### Post by cgroza on 2011-12-22
C++ is a little more than a superset of C. C++ is much more complex and its size is just colossal.
Not to mention the STL, which totaly separates it apart from C.

---

### Post by trent.josephsen on 2011-12-22
> **Petrolea said:**
> Can't answer the first question. 

And between C and C++ I prefer C. Many reasons why, but it's too late at night and I really don't feel like writing much now.
Funny, that's almost word-for-word the response I was considering.

---

### Post by robgraves on 2011-12-23
Actually with a little digging I found this right from the horse's mouth,Bjarne Stroustrup's FAQ,...[http://www2.research.att.com/~bs/bs_faq.html#prerequisite](http://www2.research.att.com/~bs/bs_faq.html#prerequisite)

---

### Post by Arndt on 2011-12-23
> **robgraves said:**
> Actually with a little digging I found this right from the horse's mouth,Bjarne Stroustrup's FAQ,...[http://www2.research.att.com/~bs/bs_faq.html#prerequisite](http://www2.research.att.com/~bs/bs_faq.html#prerequisite)

Stroustrup may be a little biased.

---

### Post by /bin/sh on 2011-12-23
Linus Torvalds said: "C++ is a horrible language. It's made more horrible by the fact that a lot of substandard programmers use it".
[http://en.wikipedia.org/wiki/C++#Criticism]("http://en.wikipedia.org/wiki/C++#Criticism")

---

### Post by Grenage on 2011-12-23
> **/bin/sh said:**
> Linus Torvalds said: "C++ is a horrible language. It's made more horrible by the fact that a lot of substandard programmers use it".
[http://en.wikipedia.org/wiki/C++#Criticism]("http://en.wikipedia.org/wiki/C++#Criticism")

If that man prefixed more of his statements with "I think" or "in my opinion", more people might listen.

Maybe.

---

### Post by Bachstelze on 2011-12-23
> **Grenage said:**
> If that man prefixed more of his statements with "I think" or "in my opinion", more people might listen.

Maybe.

Bitter C++ programmer spotted.

---

### Post by ofnuts on 2011-12-23
When used properly, OO programming makes things easier, and in large C projects, code often ends up implementing OO concepts anyway. C++ then has the benefit of being a standard way of doing OO, and the compiler supports it.

---

### Post by karlson on 2011-12-23
> **kurotensai said:**
> Is c++ a better c? Which language do u prefer between c and C++ and why?

Can I ask a counter question of: Who cares?  Neither one is the universal tool for all problems in life.  Why choose until you need to do something specific?

---

### Post by dargaud on 2011-12-23
> **ofnuts said:**
> When used properly, OO programming makes things easier

Hmmm, you've never had to debug a project where many symbols (such as +, ., [], etc) have been overloaded to make 'clever' operations more 'intuitive'. You simply have NO IDEA of the program flow. Besides the added complexity it's one of the main reasons why I reverted from C++ to C in '95.

---

### Post by Bachstelze on 2011-12-23
> **dargaud said:**
> Hmmm, you've never had to debug a project where many symbols (such as +, ., [], etc) have been overloaded to make 'clever' operations more 'intuitive'. **You simply have NO IDEA of the program flow.** Besides the added complexity it's one of the main reasons why I reverted from C++ to C in '95.

This. My only experience of OO has been one semester of Java, and that was my main grief. When you can overload, then every time you see a function call you have to spend a lot of time just figuring out which code is actually executed.

---

### Post by karlson on 2011-12-23
> **dargaud said:**
> Hmmm, you've never had to debug a project where many symbols (such as +, ., [], etc) have been overloaded to make 'clever' operations more 'intuitive'. You simply have NO IDEA of the program flow. Besides the added complexity it's one of the main reasons why I reverted from C++ to C in '95.

This is not OO Design this is a developer thinking: "WOW! This just looks cool!".  Those idjuts should be made to debug their own project after which this sort of nonsense stops.

I've seen similar thing done in C back in 95 when I looked at the SUNY's(I think) scheme interpreter C code, half of which was written in macros.  There are other examples that I can provide of similar things but you get the point.

---

### Post by ofnuts on 2011-12-23
> **dargaud said:**
> Hmmm, you've never had to debug a project where many symbols (such as +, ., [], etc) have been overloaded to make 'clever' operations more 'intuitive'. You simply have NO IDEA of the program flow. Besides the added complexity it's one of the main reasons why I reverted from C++ to C in '95.This is not really OO, this is operator overloading. Really useful in many cases (the STL uses it, for instance). And if it does what is printed on the box, you don't have to care about what goes inside.

The imagination of some programmers to catch their successors by surprise is endless, and we didn't have to wait for the advent of OO for this. In 370 Assembler, you could come across such gems as :
```

FIVE EQU 8

```

Closer to home, a well thought out "[FONT=Fixedsys]#define[/FONT]" in a header file somewhere can lead to lots of hair pulling (I've encountered "#define static " once)

---

### Post by ofnuts on 2011-12-23
> **Bachstelze said:**
> This. My only experience of OO has been one semester of Java, and that was my main grief. When you can overload, then every time you see a function call you have to spend a lot of time just figuring out which code is actually executed.

With 00 programming, you know what data is used but can't tell which code runs
With procedural programming, you know what code runs but can't tell on which data
With functional programming, since the code can be data, you pray.

---

### Post by Arndt on 2011-12-23
> **ofnuts said:**
> 
Closer to home, a well thought out "[FONT=Fixedsys]#define[/FONT]" in a header file somewhere can lead to lots of hair pulling (I've encountered "#define static " once)

```
#define protected public
```

---

### Post by karlson on 2011-12-23
> **Arndt said:**
> ```
#define protected public
```

The choice of programming language does not protect against morons with access to code.

---

### Post by Odexios on 2011-12-24
> **Grenage said:**
> If that man prefixed more of his statements with "I think" or "in my opinion", more people might listen.

Maybe.I suppose you meant to write "I think that if that man prefixed more of hist statements with "I think" or "in my opinion", more people might listen, in my opinion", sir.

---

### Post by cgroza on 2011-12-24
> **Odexios said:**
> I suppose you meant to write "I think that if that man prefixed more of hist statements with "I think" or "in my opinion", more people might listen, in my opinion", sir.
He did add maybe at the end.

---

