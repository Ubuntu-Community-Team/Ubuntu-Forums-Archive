---
title: "Where do I Start?"
date: 2008-12-03
forum: Programming Talk
---

### Post by sbooder on 2008-12-03
Hi All,
            I hope I am posting in the correct forum, I do not know if this is just for legit programmers or not.

I would like to learn programming for Linux, but have no idea where to start.

I have only ever written in html before, but I would like to in the end write programmes for Linux, particularly Ubuntu.

Any help would be most appreciated.

Simon.

PS, I realise I will have to start with the very basics, but is OK by me.

---

### Post by Delever on 2008-12-03
Create new empty file named "program.py", inside of it write one line:

```
print "Hello World"
```

Now you have a program that prints "Hello world" in console.

Run it by opening console and typing:

```
python program.py
```

Now apply this example to any language you want to try, you just need to find tutorial for that particular language (look at the stickies).

And this is the starting point on which you build more, you can use existing python (or not python) libraries, run examples, and learn.

---

### Post by sbooder on 2008-12-03
Thanks Delever,
                 The one thing that always confuses me is, which language I should start with?  I know this might be down to the individual but when you know nothing it is good to have a starting point.

---

### Post by tinny on 2008-12-03
You should really look at the Python programming language. Python is VERY popular in the Linux world.

Have a look at this
[http://learnpython.pbwiki.com/](http://learnpython.pbwiki.com/)

(From pmasiar's signature, pmasiar is a big proponent for Python)

---

### Post by Sorivenul on 2008-12-03
The Stickies at the top of this Forum offer some great advice:[URL="http://ubuntuforums.org/showthread.php?t=796494"]
Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming[/URL]
[Programming Tools and References for Many Languages]("http://ubuntuforums.org/showthread.php?t=796493")

To throw in my two cents, Python is a good language to begin with.  I find it to be one of the easiest to understand, however, the big plus is that there are so many users on these forums who use and support it.  Feel free to choose whatever you wish, though, as this is about choice.

---

### Post by dannytatom on 2008-12-03
I had the same question, though I would like to focus on UI design & development.  I too only have experience in XHTML & CSS.  My question is, what are the differences between Python and C, pros & cons, etc?

@Sorivenul I didn't see your post until after I replied, thanks for the links.

---

### Post by Sorivenul on 2008-12-03
> **dannytatom said:**
> I had the same question, though I would like to focus on UI design & development.  I too only have experience in XHTML & CSS.  My question is, what are the differences between Python and C, pros & cons, etc?

Again, read the Stickies.  :)  They really are helpful.

The differences between Python and C are many, and in this case Google may be your friend.  However, if you want a comparison of some popular languages via source code look [here]("http://www.dmh2000.com/cjpr/cmpframe.html").  Examples include Java, C++, Ruby, and Python.  This comparison is part of a larger [essay]("http://www.dmh2000.com/cjpr/index.shtml"), which while dated is still interesting.

Aside from that, the "pros and cons" of a language will vary from user to user.

---

### Post by nvteighen on 2008-12-03
> **dannytatom said:**
> I had the same question, though I would like to focus on UI design & development.  I too only have experience in XHTML & CSS.  My question is, what are the differences between Python and C, pros & cons, etc?

@Sorivenul I didn't see your post until after I replied, thanks for the links.

Well, UIs should run on top of good code, so it's better you start learning the basics with horribly-looking text-based interfaces and then step up into design.

Python vs. C... is useless to compare them, because they're meant for different stuff. 

C was designed for operating system, system utilities or time-critical programming, because it gives you a lot of control over the computer's internals: memory specially. But, that gives you more responsability, as you'll have to deal with that elements manually... and a good portion of your code will be devoted just for setting and tweaking stuff in order to be able to do what you want. For example, forget about strings... you don't have strings in C... and you even don't have real arrays...

Python and all higher abstraction level languages focus on what you want to do by hiding away all the computer's machinery and giving you built-in concepts like lists, strings, etc. Of course, this has a cost: you lose speed as you need an interpreter/virtual machine in between your application and the computer, but you gain in development speed because these languages are a way much friendlier and intuitive to human mind than the low-level languages, that focus on the machine instead.

I'd suggest you to learn programming in Python and then, start learning C.

---

### Post by rharriso on 2008-12-03
If you want work on UI, I would recommend looking at some what you see is what you get tools, Netbeans does a fantastic job of this for Java development. Although Java interfaces are super crunchy. I'm certain there are other tools for different languages.

---

### Post by rharriso on 2008-12-03
If you want work on UI, I would recommend looking at some what you see is what you get tools, Netbeans does a fantastic job of this for Java development. Although Java interfaces are super crunchy. I'm certain there are other tools for different languages. Hand coding interfaces is something I had to do for school, and will never do again.

---

### Post by jimi_hendrix on 2008-12-03
> **sbooder said:**
> Thanks Delever,
The one thing that always confuses me is, which language I should start with?

what ever language you want...some are easier than others but if your motivated you will succeed...

i would advise python though because its a lot most programs around here use...though there are some other good ones (i learned with C# but thats mainly for windows stuff) you will get good help with python here

---

### Post by mmix on 2008-12-07
learn c

---

### Post by wmcbrine on 2008-12-07
C is no language for beginners, unless your aim is to discourage them.

---

### Post by sbooder on 2008-12-07
Thanks for all the help guys.  I have gone with the consensus and started with python.  That is pretty much the reason I did not thank you all earlier, I have been learning since I got the first couple of posts. I am having fun.

Thanks again all.

---

