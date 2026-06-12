---
title: "Language suggestions?"
date: 2007-02-06
forum: Programming Talk
---

### Post by thedesburrito on 2007-02-06
Hello. I've done some progamming (very very minimal) with Java and it was fun. I want to start programming again and I am looking for a new language, cause, from what I can tell, Java was a bit crappy/slow, albeit multiplatform.

Any suggestions? Thanks.

---

### Post by jblebrun on 2007-02-06
I hear that [the whitespace language]("http://compsoc.dur.ac.uk/whitespace/") is good for beginners!

:twisted:

<runs away>

---

### Post by Wybiral on 2007-02-06
These kind of post's go on forever (everyone likes their own language, that's not a very productive question).

Perhaps instead... What kind of programming are you wanting to do? Any specific type of problem in mind? Those questions will probably get you further. Everyone has different taste and they will encourage you to use their language, but if you know what you want to do, people can help direct you towards the right language for the job.

My personal favorites: Python, Assembly, C, C++

EDIT:

> 
I hear that the whitespace language is good for beginners!



<runs away>


LMAO... Tha's a good one. Better yet, try brainf*ck or my piece of art: ScripTur

---

### Post by kcox5342 on 2007-02-06
There's an excellent guide to beginning Python here:

[http://swaroopch.info/text/Byte_of_Python:Main_Page](http://swaroopch.info/text/Byte_of_Python:Main_Page)

---

### Post by lnostdal on 2007-02-06
*yawn* .. another one

Common Lisp and C

---

### Post by thedesburrito on 2007-02-06
My first goal would be to make a little alarm clock program. I don't expect to be able to do that right away, but that seems like a fun project to start with. I would prefer something that i could use on windows if need be (god forbid).

---

### Post by lnostdal on 2007-02-06
here's an alarm in common lisp:
```

(defun pizzaAlarm (seconds)
  (withThread "pizza-alarm"
    (sleep seconds)
    (error "OMG!! Pizza is rdy! Gogogo!")))

```

when you start it (call the function `pizzaAlarm').. it runs in the background while you continue your hacking, and after *n* seconds a popup will show up with the text "OMG!! Pizza is rdy! Gogogo!" :)

edit: adding a small gui-thingy using gtk+ would be easy by the way :)

---

### Post by maxamillion on 2007-02-06
If you want multi-platform I vote Python.

---

### Post by Dygear on 2007-02-07
I hate the say it, but C. Yeah, I know. It's not the friendly language to learn, but you get so much out of it at the end of the day. And you can go down the the assembly level if you need to. C is pretty much the daddy. If you learn that you'll have no issues with C++ (Just gotta get your head around OOP at that point), PHP, or Java. Also, C is flipping FAST, a damn sight faster then Java for sure.

I myself love PHP, I'm a PHP whore, and I admit it. There is nothing better then it for making very complex applications very fast. While you can't say that it's end all be all, in most cases PHP will do just fine. An example of this would be ... I have a buddy who pretty much is a god at PHP, know it all and could tell you the PHP manual of by heart, he has done it all. We play a game called LFS, and LFS provides us a way into getting information from the engine from udp packets. He made a admin system, that was extendable via plugins (also written in PHP) in PHP. PHP will be good enough in most cases.

---

### Post by pmasiar on 2007-02-07
> **thedesburrito said:**
> Hello. I've done some progamming (very very minimal) with Java and it was fun. I want to start programming again and I am looking for a new language, cause, from what I can tell, Java was a bit crappy/slow, albeit multiplatform.

IMNSHO obvious languge for any beginner is Python. You will learn programing principes without unnecessary complications like strong type enforcement or object obsession of java, or complicated syntax and scoping rules of C. In Python, you will be writing your own programs in weeks, not months.

Python also allows you to try language "one line of code at a time" in python shell - I am not aware of any other mainsrteam language for beginners with this feature. Basic had it years ago (and if added to Basic's popularity), but alas not anymore. Python will be more than enough for most of your projects at the beginner level.

*After* becoming proficient in programming basics (in Python), and if you are still interested in learning more about programming, you may want to learn other languages used in specific areas of your interrest, used by existing projects: C for kernel hacking, C++ for GUI stuff like Gnome nad KDE, Lisp for AI (artificial intelligence), Java for "enterprisey" apps, Python, Perl, Ruby, PHP for web apps, Asembler when time/performance is critical, etc. 

Or you might find that Python, with many libraries, is "good enough" for area of your interest and you are just fine with Python alone. Ubuntu own projects use Python exclusively - easier to maintain, and fast enough. Google is another big user of Python.

There are many languages, each specialized in their own niches. Python's niche is be easy to learn (good for beginners) and scalable :-) , being "good enough" for many (but not most) projects.

I have a little wiki to help you with Python: [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) - and also collection of simple tasks to solve. Enjoy!

---

