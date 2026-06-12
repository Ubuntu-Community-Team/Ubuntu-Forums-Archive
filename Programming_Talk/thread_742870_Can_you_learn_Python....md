---
title: "Can you learn Python..."
date: 2008-04-02
forum: Programming Talk
---

### Post by swatto on 2008-04-02
Hi all,

I recieved my copy of Core Python Programming 2nd edition - it is about 1000+ pages which is good in a way but I feel that I will get bored reading all of it in a chunk and also forget most of it.  

Could I learn Python by just taking bits from the book I need to make a specific program? - Somebody said to me it depends on how much of the 'basics' you know but I don't know what that quite means.

Cheers for any help on this. :)

---

### Post by tseliot on 2008-04-02
> **swatto said:**
> Could I learn Python by just taking bits from the book I need to make a specific program? - Somebody said to me it depends on how much of the 'basics' you know but I don't know what that quite means.
Knowing something about you would help us give you an appropriate answer, for example
:
1) Do you know how object oriented programming works i.e. what classes and objects are?

2) Have you got previous programming experience (even with another language)?

While I'm convinced that putting things into practice is a good way to avoid forgetting what you learn, if your experience is not enough for what you're trying to do, you might end up wasting a lot of time trying do things which are covered in the book or (even worse) writing bad code.

---

### Post by swatto on 2008-04-02
> **tseliot said:**
> Knowing something about you would help us give you an appropriate answer, for example
:
1) Do you know how object oriented programming works i.e. what classes and objects are?

2) Have you got previous programming experience (even with another language)?

While I'm convinced that putting things into practice is a good way to avoid forgetting what you learn, if your experience is not enough for what you're trying to do, you might end up wasting a lot of time trying do things which are covered in the book or (even worse) writing bad code.

Hi tseliot,

1) I haven't gone into this at all really so I might be completely wrong :redface: - A class is kind of like a 'blueprint' for an object which I think is an instance of a class.  All things in Python are treated as objects?

2) Ive only dabbled in the very very basics (so haven't ever done OO programming) with a bunch of different languages - VB, C, C++, Perl, PHP.

---

### Post by tseliot on 2008-04-02
> **swatto said:**
> Hi tseliot,

1) I haven't gone into this at all really so I might be completely wrong :redface: - A class is kind of like a 'blueprint' for an object which I think is an instance of a class.  All things in Python are treated as objects?
You can write code without classes and objects, however I warmly recommend you to study object oriented programming.

> **swatto said:**
> 2) Ive only dabbled in the very very basics (so haven't ever done OO programming) with a bunch of different languages - VB, C, C++, Perl, PHP.
Not bad ;)

Try not to start with a complicated project. For example don't try to write GUI programs (which BTW require object oriented programming, at least in Python) or programs which should solve problems which are too complicated. What are you planning to work on?

---

### Post by swatto on 2008-04-02
> **tseliot said:**
> You can write code without classes and objects, however I warmly recommend you to study object oriented programming.


Not bad ;)

Try not to start with a complicated project. For example don't try to write GUI programs (which BTW require object oriented programming, at least in Python) or programs which should solve problems which are too complicated. What are you planning to work on?

Im not really sure what to work on (need to get an imagination first :lolflag:)  - I will probably just be making quick small scripts until I improve my knowledge significantly enough to actually make a proper application that use different modules.  For example at the moment Im just looking at messing with two scripts to see what modifying them slightly does - one of the scripts takes user input to create a text file and write lines to the file depending on what the user inputs, the second script just reads the specified text file line by line and returns the output.

---

### Post by tseliot on 2008-04-02
That's ok. Curiosity is good ;)

---

### Post by pmasiar on 2008-04-02
> **swatto said:**
> 1A class is kind of like a 'blueprint' for an object which I think is an instance of a class.  All things in Python are treated as objects?

Yes, everything is object. You can play with it in Python shell: create some object, say **x = open('file.name')** (open a file), then enter **dir(x)** to see what is in that object (all the methods). you can also get docstring of any method by **help(x.methodname)**

In my experience, better analogy for class than "blueprint" is cookie-cutter: you can create cookies with it, each object shares some attributes (shape), but has some individual attributes when created (frosting). And of course cookie is rather different from the cutter to make it.

> 2) Ive only dabbled in the very very basics (so haven't ever done OO programming) with a bunch of different languages - VB, C, C++, Perl, PHP.

Core Python might be good second book, but to get you started, try "Dive into Python": it is a book for people who know programming in other languages, and just need to know how Python does it. If that is too hard, try "Byte of Python".

BTW, all this is explained in sticky FAQ, do read it; and make suggestion if something is not obvious enough. Wiki in my sig has many links, and also training tasks for beginners.

---

### Post by tseliot on 2008-04-02
> **pmasiar said:**
> Yes, everything is object.
True, but (as you know) you don't necessarily need to be aware of it in order to write Python code. This is what I meant.

---

### Post by pmasiar on 2008-04-02
I agree.

Regarding OOP, I recommend anyone to learn how to **use and understand** existing objects from libraries (incliding mentioned dir() and help() ) way before trying to define your own objects. As tseliot mentioned, you can do away without defining your own objects for quite a long time. But you cannot use Python without understanding objects, methods, etc: everything is an object.

So we both are right :-)

---

### Post by swatto on 2008-04-02
> **pmasiar said:**
> 
Core Python might be good second book, but to get you started, try "Dive into Python": it is a book for people who know programming in other languages, and just need to know how Python does it. If that is too hard, try "Byte of Python".

BTW, all this is explained in sticky FAQ, do read it; and make suggestion if something is not obvious enough. Wiki in my sig has many links, and also training tasks for beginners.

Thanks for your reply too pmasiar - ive read and created all the scripts that are in the 'A Byte of Python' book - I then ordered the Core Python book.  Ive also been reading How to think like a Python Programmer which I find really really good.

---

### Post by pmasiar on 2008-04-02
OK, now you need to start programming: PythonChallenge is good start, my wiki has links to many training tasks. Reading docs is boring, reading something related to problem you have is exciting. So to make reading exciting, you need to have problems to solve.

---

### Post by swatto on 2008-04-02
Cheers both of you - appreciated :)

---

