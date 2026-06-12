---
title: "What to do after Python?"
date: 2009-05-01
forum: Programming Talk
---

### Post by sam191 on 2009-05-01
Hello everyone!

I am new here and this is my first post. I am a junior in high school and want to pursue a degree in Computer Science. I have just recently start programming(couple of months ago). I started with Python since every forum I went to recommended it. 

I was wondering what I should do now that I've learned Python. I went through two or three beginners Python books and feel like I understand the basics fairly well. 

Now I'm wondering if I should start learning C, or should I strive to become a Python expert before moving on? I've dipped my toes in C++ and C# before. And a lot of others are recommending Java as a second language.

I am also slightly interested in Web Development, but am not too familiar with that road. 

Any help/suggestions or a push in the right direction are appreciated! 

_Sam

---

### Post by nvteighen on 2009-05-01
IMO, learning a second language is more determined by what you're interested to do and what not. Of course, it'd be advisable to learn something different to Python so you can expand your horizon much more than by learning a similar language like Perl, for example.

If I were you, I'd go for C. First, all programmers should know it, because of its historical value and because it's a great language to introduce you in low-level programming (compared to Forth, for example). And it will make you learn C-like languages (C++, Java, C#, Objective-C, Perl) much more easily and those are a big group that covers a wide range of different tasks.

Java may be the choice if you want to make some work on a project using it, but being a high-level language, it may not add too much of what you've learned in Python.

Anyway, as I said at the beginning, the choice of the second language is not as critical as the choice of the first one. And don't stop using Python...

---

### Post by sujoy on 2009-05-01
imo learning a language is different than reading a couple of books on it. since you are interested in web development, i would suggest you take a look at django, pylons etc.

in order to really learn a language you need to implement a non-trivial project in it.

---

### Post by UBForty on 2009-05-01
> a great language to introduce you in low-level programming (compared to Forth, for example)

Are you suggesting that Forth is unsuitable to teach low-level programming? Are you serious? Forth has been used for ages for low-level systems programming on embedded controllers and even as a CPU assembly language. The Novix 4000 CPU was a stack machine CPU which used Forth as its assembly language, it had a rather modest transistor count and clock frequency but it outperformed any other 16 bit CPU at the time. For example, the first prototype computer built with it didn't have any graphics card, so they wrote a virtual graphics card in Forth which generated the modulated signal for a CRT directly from software, it still had a higher frame rate than any existing VGA card on the market at the time. Short of programming in assembly directly, it doesn't get more system level than Forth. It's an excellent language to teach/learn low-level and hardware level programming, far more suitable than C for that purpose.

In fact Forth is an excellent language to learn the fundamentals of stack machines and CPUs. Worthwhile considering. I am not saying people should develop their software in Forth, but as a teaching tool for fundamentals it is a very good choice.

---

### Post by hessiess on 2009-05-01
Try implementing a CMS in python.

(You may also want to lern PHP as a lot of hoasting providers(espetly the cheeper ones) offer it only)

---

### Post by nvteighen on 2009-05-01
> **UBForty said:**
> Are you suggesting that Forth is unsuitable to teach low-level programming? Are you serious? Forth has been used for ages for low-level systems programming on embedded controllers and even as a CPU assembly language. The Novix 4000 CPU was a stack machine CPU which used Forth as its assembly language, it had a rather modest transistor count and clock frequency but it outperformed any other 16 bit CPU at the time. For example, the first prototype computer built with it didn't have any graphics card, so they wrote a virtual graphics card in Forth which generated the modulated signal for a CRT directly from software, it still had a higher frame rate than any existing VGA card on the market at the time. Short of programming in assembly directly, it doesn't get more system level than Forth. It's an excellent language to teach/learn low-level and hardware level programming, far more suitable than C for that purpose.

In fact Forth is an excellent language to learn the fundamentals of stack machines and CPUs. Worthwhile considering. I am not saying people should develop their software in Forth, but as a teaching tool for fundamentals it is a very good choice.
The issue with Forth is that there is too little documentation for it and is a pretty hard language to manage. In theory, being stack-based makes it much more suitable, but sadly it's the extra-programming context which doesn't help. That's why I think that C is a better option for low-level programming...

A rather lame reason, but true...

---

### Post by eye208 on 2009-05-01
> **sam191 said:**
> Any help/suggestions or a push in the right direction are appreciated!
One benefit of open source is that you can see what languages other people are using. For example, if you are interested in desktop application development, find out what language the big applications you are using now are written in. And then learn that language.

If you want to develop web applications, find out what language has been used to develop some of the most frequently used web applications (wikis, forums, blogs etc.). Then learn that language.

Don't waste your time learning obscure languages that almost no one is using. And don't waste your time learning redundant languages. For example, now that you have learned Python, learning yet another scripting language (Perl, PHP, Ruby, Lua etc.) is probably not a good idea at this point. And once you know Java, learning yet another VM-based language (C#, VB.NET) doesn't make much sense either. You can still do that later, but for now, try to diversify. Knowing the best tools of several worlds will make you a more versatile programmer.

---

### Post by UBForty on 2009-05-01
> **nvteighen said:**
> The issue with Forth is that there is too little documentation for it and is a pretty hard language to manage. In theory, being stack-based makes it much more suitable, but sadly it's the extra-programming context which doesn't help. That's why I think that C is a better option for low-level programming...

Like I said, it is an excellent language to learn the fundamentals and for that purpose it is better than C, and probably even better suited than Pascal or Modula-2, the classic teaching languages. Whether you want to use it afterwards for real projects is a different matter and depends on other factors than the language itself, but we were talking about learning/teaching.

As far as documentation is concerned, I disagree. One of the top ten computer science classics is "Thinking Forth", an absolute must read IMO. It is available online, too, so you don't even have to spend any money on it:

[http://thinking-forth.sourceforge.net/]("http://thinking-forth.sourceforge.net/")

This is all the documentation you ever need for using Forth as a "learn the fundamentals" tool.

---

### Post by nvteighen on 2009-05-01
> **UBForty said:**
> Like I said, it is an excellent language to learn the fundamentals and for that purpose it is better than C, and probably even better suited than Pascal or Modula-2, the classic teaching languages. Whether you want to use it afterwards for real projects is a different matter and depends on other factors than the language itself, but we were talking about learning/teaching.

As far as documentation is concerned, I disagree. One of the top ten computer science classics is "Thinking Forth", an absolute must read IMO. It is available online, too, so you don't even have to spend any money on it:

[http://thinking-forth.sourceforge.net/]("http://thinking-forth.sourceforge.net/")

This is all the documentation you ever need for using Forth as a "learn the fundamentals" tool.
It seems I was misinformed. Thanks! It's nice to learn and you never stop learning actually :)

@OP: Add Forth to your list!

---

### Post by grepgav on 2009-05-01
If you plan on studying CS I would recommend learning C now. I am in my third year of my CS program and I was very glad to know some C going in, some classes expect you to know it or you will have to just pick it up along the way, so knowing a good basis of the language will help you tremendously.

Of course languages used differ among schools, but most will have some sort of exposure to C for operating system programming.

---

### Post by dandaman0061 on 2009-05-01
Tally me up for the recommendation of learning C or C++ also.  They do some things fundamentally different than Python.  Pointers/references come to my mind immediately.

Whereas python hides most of this with it's reference model (everything is a reference), C makes you deal with them directly (for better or worse).
for example: in python you can't [s]modify a variable[/s] change which object a variable points to through a function without assigning it to the result.

```

def swap(a, b):
   a, b = b, a
   return (a, b)

# what won't work
swap(a, b)
# what you have to do:
a, b = swap(a, b)

```

BUT in C you can make the swap function actually modify variables just by calling swap(a, b) using pointers (for better or worse).

Also, types is a whole other issue to get into.

And as a last push; learning C/C++ WILL increase your python skills as well if you ever get into writing modules in C and importing them in python.

---

### Post by Can+~ on 2009-05-01
> **dandaman0061 said:**
> for example: in python you can't modify a variable through a function without assigning it to the result.

You can't? really?

[PHP]#!/usr/bin/python

def byreference(pointer):
	pointer[0] = 2

a = [3, 1, 6]

print a

byreference(a)

print a[/PHP]

Lists, Tuples, Dictionaries and most objects are internally handed as pointers. Even the "self" keyword is a pointer to it's own instance (pretty much like C++'s or Java's this).


As for the OP: +1 to learn C, more important than learning languages, is learning paradigms, Python already taught you about Object Oriented and Functional and a bit imperative, C will really show you what imperative means, and let you understand how some of the python internals work.

---

### Post by sam191 on 2009-05-01
Thanks for all of the suggestions! I am really liking this community. 

Let me clear things up a little. I am actually getting a degree in Software Engineering. But here (University of Washington) CS and SE are almost identical. The only difference is more comp classes in SE as opposed to more "humanities/social sciences" classes in CS. 

They teach Java here, and although I haven't tried Java yet I have tried C#. I didn't really like it. I felt like I knew "how to code" but I didn't understand "why" or what was really going on. That's what also bugged me in Python, although I wrote some pretty handy scripts.  

Hence, my choice to follow up with C. I have a copy of K&R "The C Programming Language" and will look into that soon. However, I also have some projects I would like to do in Python, can anyone recommend some novice/advanced books? Right now I'm thinking, Core Python Programming -> Expert Python Programming.

---

### Post by Luggy on 2009-05-01
C or C++ is great because one thing Python does not really teach you is how to create and use pointers and every programmer worth this salt should know pointers like the back of his hand.

However, while I did a lot of C++ in Uni (taking C++ in high school really helped with that) I know lots of schools like to teach Java or C# and getting a good foundation in whatever you end up being taught later really takes the edge off.

---

### Post by dandaman0061 on 2009-05-01
> **Can+~ said:**
> 
Lists, Tuples, Dictionaries and most objects are internally handed as pointers. Even the "self" keyword is a pointer to it's own instance (pretty much like C++'s or Java's this).

You are correct on this, and had it on my mind when I was writing my post, but I didn't want to get too into which variables are passed by value vs. by reference.  But as you seem to know, try doing the same with ints or changing the object that your reference is pointing to inside of a function.
e.g.
```

def assign_new_object(b):
    print id(b)   # addr 1
    b = object()
    print id(b)   # addr 2

a = object()
print id(a)       # addr 1
assign_new_object(a)
print id(a)       # still addr 1
```
That was what I was trying to get across that could be done in C.  You can MODIFY the 'b' object within functions (assign attrs, add/change keys to a dict, etc..) but you cannot change where the original points... without some major trickery (or returning it and assigning the return value)

ANYWAY as for the OP's question of more advanced python books... my advice would be to stay away from the O'Reilly 'Programming Python'.  I admire the author, but this book has been pretty useless to me.  As a reference, I find the index severely lacking and google and the online python documentation to be much quicker, more up to date, and much more helpful.  Personally, I wouldn't focus on books so much at all at this point.  Look for the 'programmers tutorial' on the python.org website and skim through the Library reference.

OR for more fun and probably better experience, try dinking with some open-source python projects such as XBMC (previously xbox-media center (runs on Linux & don't need an xbox)), dig through the plugins and see how others write their code, add to them, or write your own.  There are always requests for more plugins on their forums.  This is kind of hit and miss though, as some people's python code is IMHO very unorganized and shouldn't be learned from.  Other advice is if you're serious about Python, make sure you read and follow PEP008 (The style guidelines)... learn them when you are starting out, make them a habit.

[http://www.python.org/dev/peps/pep-0008/]("http://www.python.org/dev/peps/pep-0008/")

<end of rant>

---

### Post by mmix on 2009-05-01
> **nvteighen said:**
> 
If I were you, I'd go for C. First, all programmers should know it

Agreed, plus, Unix (recommend: Advanced Programming in the UNIX(R) Environment (2nd Edition): i have one) and assembly programming language.

---

### Post by sam191 on 2009-05-01
Thanks for all of the replies. 

I really want to make sure that I have a strong foundation and follow the correct path in this field, so I really appreciate all of the advice! 

I am thinking of sticking with Python for now and learning C in the summer(it doesn't seem too difficult), because I would really like to complete a project in Python before moving on.  

Just curios though, I skimmed through the part on pointers/arrays in the K&R book, and it seems to me like they are similar to lists/indexing in Python. Basically recalling a variable from a certain location in memory. Is there any truth to this, or am I way off?

Edit: Never mind, lol, I just googled it. Looks like I have a lot more ahead of me than I first thought.

---

### Post by disabledaccount01 on 2009-05-02
Message removed by author.

---

### Post by eye208 on 2009-05-02
> **Luggy said:**
> C or C++ is great because one thing Python does not really teach you is how to create and use pointers and every programmer worth this salt should know pointers like the back of his hand.
Every C++ programmer worth his salt should know how to write programs **without** pointers.

---

### Post by slavik on 2009-05-02
> **eye208 said:**
> Every C++ programmer worth his salt should know how to write programs **without** pointers.
there goes 'new' out the window ...

---

### Post by eye208 on 2009-05-02
> **slavik said:**
> there goes 'new' out the window ...
'new' is still around, but 'delete' goes out the window. ;)

---

### Post by CptPicard on 2009-05-02
> **nvteighen said:**
> 
If I were you, I'd go for C. First, all programmers should know it, because of its historical value and because it's a great language to introduce you in low-level programming (compared to Forth, for example). And it will make you learn C-like languages (C++, Java, C#, Objective-C, Perl) much more easily and those are a big group that covers a wide range of different tasks.


While I agree with the suggestion (C after Python), I am not all that certain that learning C helps all that much in learning those C-like languages you mention... you're ignoring the fact that the commonality is essentially the basic control structures, which are essentially a triviality. In languages like C++, Java and C# the big issue is static-typed OOP, where the core thing to actually learn is object-oriented design. Learning all the design patterns you're expected to be able to make use of was, interestingly, the hardest thing I had to do while learning...

---

### Post by txcrackers on 2009-05-02
Learning a language is the most trivial part of software development - **using** the (any) language to do something "useful" is the hard part.

---

### Post by nvteighen on 2009-05-02
> **CptPicard said:**
> While I agree with the suggestion (C after Python), I am not all that certain that learning C helps all that much in learning those C-like languages you mention... you're ignoring the fact that the commonality is essentially the basic control structures, which are essentially a triviality. In languages like C++, Java and C# the big issue is static-typed OOP, where the core thing to actually learn is object-oriented design. Learning all the design patterns you're expected to be able to make use of was, interestingly, the hardest thing I had to do while learning...
I see what you mean, but I was actually thinking on the structured/OOP programming compared to functional programming and other paradigms. I mean, the abstraction means you get in all those languages are similar, plus the static-typeness common to all of them except Perl... That's what I wanted to mean... :p

---

### Post by Dwood15 on 2009-05-02
I know this might seem rather stupid but depending on one's level of technical knowledge with programming you may want to just look at learning Quake C so you can get immediate application (pun not intended) for learning it. 

If you're learning to program on your own, doing so when you can get immediate results helps push you through the hardest parts.

---

### Post by DocForbin on 2009-05-02
Java is a good choice, IMHO. It will be an easy transition from python. It's the most widely used language in the world. There is heavy emphasis on design patters that are useful in many languages.

But yeah, learn C :)

---

### Post by Luggy on 2009-05-02
> **eye208 said:**
> Every C++ programmer worth his salt should know how to write programs **without** pointers.

I'm not saying that the best C++ programmers dynamically allocate all their variables, but pointers are useful tools that have there place and it's good to properly understand how they work.

If all you do with C++ is code for fun then you can go ahead and think that pointers are big and scary and never use them. But I challenge you to say that you can be a professional C++ programmer and never have know how pointers work.

---

### Post by sam191 on 2009-05-04
Wow, a lot of replies since I was gone.

Anyway, I have decided on broadening my knowledge of Python before going into C.

Now the real question. I am down to two books and can't decide which one to choose. 

"Learning Python" by Mark Lutz

or 

"Core Python Programming" by Wesley Chun?

I realize that there are free books online, but I am looking for a complete, thorough intro course that I can physically have in my hands. 

Thanks again!

---

### Post by ibuclaw on 2009-05-04
> **txcrackers said:**
> Learning a language is the most trivial part of software development - **using** the (any) language to do something "useful" is the hard part.

txcrackers++

The question you should be asking is "What area do I want to program in?"

I - possibly by complete accident - got into text manipulation, regular expressions, lexers and compiler's compilers.
And as such, the tools on the table I took were C, Perl and recently Haskell.

Now, you will indefinitely have a different outlook on programming, and will want to look into creating something else, so the £MILLION question,
"What do I want to program that both I, and others will use/find useful in carrying out in daily/weekly tasks?"

Regards
Iain

---

