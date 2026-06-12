---
title: "Which Programming Language"
date: 2008-10-28
forum: Programming Talk
---

### Post by tdashroy on 2008-10-28
Alright I have a couple of questions:

Which programming language would you suggest:

1. If I wanted to program a database with a graphical interface that only dealt with data locally(data only from the machine it is on)?

2. If I wanted to program a database with a graphical interface that dealt with sending data over the internet?

3. If I only had the choice of Java, C++, Ruby, Lisp, Perl, or Python, for the above two questions.

Suggestions or opinions of any kind would be greatly appreciated.

---

### Post by jimi_hendrix on 2008-10-28
should be in programming talk...but

1. i dont know

2. i dont know

3. not C++ and i dont think lisp...all three of the scripting languages will probably work as well as java

---

### Post by forger on 2008-10-28
python/perl with gtk2 and glade to design your graphical user interface? :)
[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)
Also, sqlite3 as a database would a wise solution since it's internal/local I think python comes with sqlite3 since 2.5: [http://www.python.org/doc/2.5.2/lib/module-sqlite3.html](http://www.python.org/doc/2.5.2/lib/module-sqlite3.html)

---

### Post by Delever on 2008-10-28
I don't know all possible languages to be able to make good suggestion :).

However, you narrowed down 3rd question, and asked for **any** opinions, so here we go:

It seems that you will be working with business application, where reliability is above everything. In this case I suggest choosing language where compiler checks the most and which have good choices of IDEs. Java.
Java will work probably with any kind of database you choose, has enough (:)) libraries, forces object oriented design, works on different platforms.

Second choice in this case (for me) would be Python. It is not strong typed, so compiler will check less. It can be argued that you can achieve more neat tricks this way, but we are talking stability, not tricks :). And I still have to find good IDE for it. Up to Eclipse's Java level.

I don't know Ruby, Perl, Lisp (huh, i am behind.. (or forward.. (or backward..))), so I leave comments about them to the fans.

About database locality... nowadays I would use SQL based database engine which will be accessed locally in any case... so, it won't matter much. Both Java and Python have enough tools for communication over Internet so I see them equal here too.

---

### Post by LaRoza on 2008-10-28
My biases: Python + C, PHP for web.

> **tdashroy said:**
> 
1. If I wanted to program a database with a graphical interface that only dealt with data locally(data only from the machine it is on)?


OO Base ;)

SQLite is the database library I would use. I would personally use Python as the language.

> **tdashroy said:**
> 
2. If I wanted to program a database with a graphical interface that dealt with sending data over the internet?


I'd do it through a browser, and use a central server with a free RDMS like MySQL and PHP or Python.

Without a browser for the client, I'd use Python to make it.

> **tdashroy said:**
> 
3. If I only had the choice of Java, C++, Ruby, Lisp, Perl, or Python, for the above two questions.

Whichever one I knew the best. Python, in that case.

---

### Post by curvedinfinity on 2008-10-28
I personally use Python, SQLite, and Firefox's SQLite Manager plugin.

Python is the way to go. Its an excellent language that can do just about everything well.

---

### Post by ukera on 2008-10-28
my personal favorite programming language has to be perl.  then C.  not C++ just some C. :)  also I like PHP.  PHP is my favorite language.  PHP ftw.

-ukera

---

### Post by tdashroy on 2008-10-28
Thanks all for your input. One of the reasons I asked these questions was because I was curious what language would best benefit me to learn next. It looks as though Python is a good choice. The other reason is I just wanted to here what others had to say. Thanks again =).

---

### Post by slavik on 2008-10-29
> **tdashroy said:**
> Alright I have a couple of questions:

Which programming language would you suggest:

1. If I wanted to program a database with a graphical interface that only dealt with data locally(data only from the machine it is on)?

2. If I wanted to program a database with a graphical interface that dealt with sending data over the internet?

3. If I only had the choice of Java, C++, Ruby, Lisp, Perl, or Python, for the above two questions.

Suggestions or opinions of any kind would be greatly appreciated.
1. OOo Base
2. OOo Base
3. No need for a language

But if you really want to write your own ...
1. Perl/Python/Ruby
2. Perl/Python/Ruby
3. Perl/Python/Ruby

---

### Post by sheto on 2008-10-29
Answers to your questions :-

1) Sqlite. 

2) MySQL

3) Python

---

### Post by LaRoza on 2008-10-29
> **slavik said:**
> 1. OOo Base
2. OOo Base
3. No need for a language

But if you really want to write your own ...
1. Perl/Python/Ruby
2. Perl/Python/Ruby
3. Perl/Python/Ruby

+1, but can OOo Base do things over the network?

---

### Post by pmasiar on 2008-10-29
> **Delever said:**
> business application, where reliability is above everything. In this case I suggest choosing language where compiler checks the most and which have good choices of IDEs. Java. (...)

Python. It is not strong typed, so compiler will check less. 

This is common misunderstanding, ensuing discussion was helpfully moved by mod to [separate thread](http://ubuntuforums.org/showthread.php?t=962611) but move was unhelpfully not mentioned in this thread, so innocent reader could mistakenly think that opinion quoted above is fact-based, while it is (IMHO) not at all. So, please jump :-)

---

### Post by slavik on 2008-10-29
> **LaRoza said:**
> +1, but can OOo Base do things over the network?
it can connect to any MySQL/PgSQL/etc. server ... it can even connect to a JDBC server. :)

---

### Post by LaRoza on 2008-10-29
> **slavik said:**
> it can connect to any MySQL/PgSQL/etc. server ... it can even connect to a JDBC server. :)

Neat. I haven't used OOo Base or Access much.

---

### Post by slavik on 2008-10-29
Access can't ... it can only use it's own DB engine.

---

