---
title: "What is the purpose of lisp"
date: 2013-06-01
forum: Programming Talk
---

### Post by imu96 on 2013-06-01
Hi. I recently started learning common lisp from Peter Norvig's book [http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming](http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming) .I've now gotten through the first two chapters and have now solved several of the first 20 problems on projecteuler.net using lisp (but not all). I'm really starting to appreciate what a great language it is but I'm not sure what it is used for in real life. I've searched the internet and I've seen vague answers to this question like it is used for "prototyping" and for "badly specified problems". 

<p>To my knowledge, while C is also a "general" programming language like lisp, it is a particularly good language for systems programming since it is low level. Assembly has similar uses but is lower level and less readable. Java is used because of the JVM so you don't have to port applications written in it across operating systems and Clojure for the same reason but if you think that Java is ugly or you just like lisp. R is apparently extremely good for statistical programming.</p>

So in conclusion I'm just wondering what good are languages such as common lisp and python in the grand scheme of things. What is their specialty? Are better for GUIs, or what is their purpose among these other alternatives. I've learned bits and pieces of programming languages in the past such as C, C++, Java and Python, but common lisp is my first serious attempt to get into programming. Thanks in advance.

---

### Post by xb12x on 2013-06-01
> **imu96 said:**
> I'm not sure what it is used for in real life.

That is a valid question if your goal is to be a working, professional developer.

If so, I suggest that you pick an area of development you are interested in and then find its most popular language on a site such as the Tiobe Index. An example: If you are interested in system-level development (my particular expertise) learn 'C'. 

[http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

By the way, according to most sites, Lisp is a poor choice if your goal is to work (get paid) as a developer.

---

### Post by Mikeb85 on 2013-06-02
> **imu96 said:**
> Hi. I recently started learning common lisp from Peter Norvig's book [http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming](http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming) .I've now gotten through the first two chapters and have now solved several of the first 20 problems on projecteuler.net using lisp (but not all). I'm really starting to appreciate what a great language it is but I'm not sure what it is used for in real life. I've searched the internet and I've seen vague answers to this question like it is used for "prototyping" and for "badly specified problems". 

<p>To my knowledge, while C is also a "general" programming language like lisp, it is a particularly good language for systems programming since it is low level. Assembly has similar uses but is lower level and less readable. Java is used because of the JVM so you don't have to port applications written in it across operating systems and Clojure for the same reason but if you think that Java is ugly or you just like lisp. R is apparently extremely good for statistical programming.</p>

So in conclusion I'm just wondering what good are languages such as common lisp and python in the grand scheme of things. What is their specialty? Are better for GUIs, or what is their purpose among these other alternatives. I've learned bits and pieces of programming languages in the past such as C, C++, Java and Python, but common lisp is my first serious attempt to get into programming. Thanks in advance.

Lisp is, in part, a piece of history.  It's many decades old, and even though it's not widely used today, ideas from Lisp have made their way into nearly every other modern language.  Python, Ruby, Javascript, Clojure, and many other modern languages were influenced by Lisp.  Lisp was the first language to have garbage collection.  

In real life Lisp can be used for many things, server side scripting seems to be the most practical nowadays, and it's also used for scientific programming, statistics, finance, and alot of other things that we'll probably never see.  It's advantages are that it's incredibly flexible, development in Lisp is very efficient, it can be very fast (SBCL is faster than pretty much any other dynamic language), it's cross-platform, and it can be used in any paradigm.  The disadvantages are that it's complicated, the syntax can be esoteric, and few people use it (thus libraries can be hard to find).  

Ruby, Python, Javascript, and other languages influenced by Lisp are among the most widely used languages today.

---

### Post by Leuchten on 2013-06-02
> **imu96 said:**
> Hi. I recently started learning common lisp from Peter Norvig's book [http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming](http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming) .I've now gotten through the first two chapters and have now solved several of the first 20 problems on projecteuler.net using lisp (but not all). I'm really starting to appreciate what a great language it is but I'm not sure what it is used for in real life. I've searched the internet and I've seen vague answers to this question like it is used for "prototyping" and for "badly specified problems". 

<p>To my knowledge, while C is also a "general" programming language like lisp, it is a particularly good language for systems programming since it is low level. Assembly has similar uses but is lower level and less readable. Java is used because of the JVM so you don't have to port applications written in it across operating systems and Clojure for the same reason but if you think that Java is ugly or you just like lisp. R is apparently extremely good for statistical programming.</p>

So in conclusion I'm just wondering what good are languages such as common lisp and python in the grand scheme of things. What is their specialty? Are better for GUIs, or what is their purpose among these other alternatives. I've learned bits and pieces of programming languages in the past such as C, C++, Java and Python, but common lisp is my first serious attempt to get into programming. Thanks in advance.

Common lisp is not used for a ton nowadays, but in the past it was the systems programming language for lisp machines. Clojure seems to be a very good choice if you want to do general application development as IIRC it's currently the most popular lisp flavor and has seamless access not only to its own libraries, but java's as well.

Python and common lisp don't have a specific specialty, but they are nice for prototyping and producing working apps quickly.

---

### Post by ofnuts on 2013-06-02
> **imu96 said:**
> Hi. I recently started learning common lisp from Peter Norvig's book [http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming](http://www.goodreads.com/book/show/83884.Paradigms_of_Artificial_Intelligence_Programming) .I've now gotten through the first two chapters and have now solved several of the first 20 problems on projecteuler.net using lisp (but not all). I'm really starting to appreciate what a great language it is but I'm not sure what it is used for in real life. I've searched the internet and I've seen vague answers to this question like it is used for "prototyping" and for "badly specified problems". 

<p>To my knowledge, while C is also a "general" programming language like lisp, it is a particularly good language for systems programming since it is low level. Assembly has similar uses but is lower level and less readable. Java is used because of the JVM so you don't have to port applications written in it across operating systems and Clojure for the same reason but if you think that Java is ugly or you just like lisp. R is apparently extremely good for statistical programming.</p>

So in conclusion I'm just wondering what good are languages such as common lisp and python in the grand scheme of things. What is their specialty? Are better for GUIs, or what is their purpose among these other alternatives. I've learned bits and pieces of programming languages in the past such as C, C++, Java and Python, but common lisp is my first serious attempt to get into programming. Thanks in advance.
Lisp was written to run on hardware with less processing power than an entry-level MP3 player, so it still is a rather efficient and compact interpreter. However it also means that its programmer-friendly features can run on a 70's-era machine, so that makes it pretty ugly by today's standards.

Python is a quite different matter, it's a very good general-purpose language to write quick-and-not-so-dirty code: typically, one-shot programs, or programs where the speed of the language isn't too important (scripts). A standard Linux system has plenty of little bits of python  (637 of them under /usr, 10 under /etc on my Ubuntu).

---

### Post by nvteighen on 2013-06-02
Well, Lisp is a high-level language as others are. In principle, whenever you need something that is high level, you may use it. The only drawback of Common Lisp is that, although most implementations are able to generate executables (you can also just use scripts), these executables are huge because they include a Lisp runtime. Clojure has solved this in an obvious way: as it depends on the JVM, well, the runtime is already there :P

In my opinion, Lisp is more a school of thought than anything else. I use it for my toy projects, because I like to experiment with its features, but I'm sure that, when I need to write something a bit more serious, I prefer to use Python or even Perl... Heck, we should be happy to have all this diversity! :)

---

### Post by xb12x on 2013-06-02
> **nvteighen said:**
> Clojure has solved this in an obvious way: as it depends on the JVM, well, the runtime is already there

This got me to wondering just how pervasive the JVM is on PC's. The extermes I found using a simple google search are 70% and 90%. Even if it's 'only' 70% I'm a little suprised it's that high.

---

### Post by aquatabby on 2013-06-08
> **imu96 said:**
> ...

So in conclusion I'm just wondering what good are languages such as common lisp and python in the grand scheme of things. What is their specialty? Are better for GUIs, or what is their purpose among these other alternatives. I've learned bits and pieces of programming languages in the past such as C, C++, Java and Python, but common lisp is my first serious attempt to get into programming. Thanks in advance.

My first real job was as a Lisp programmer, so I'm biased - but Lisp is a very elegant language to learn. It has functional and O-O features that put languages like Java and C# to shame. Python is catching up, but using the functional feature of Python are clumsy compared to Lisp.

It's not a mainstream language in industry. I think the main reason for this is a lack of a standardised GUI, and the way in which packages are imported (essential for anything other than trivial projects) is messy compared to Python/Java/C#.

So, I'd say it's a good language to learn about programming, especially functional and O-O programming, which is why many universities still use it. Once you have learned to code in Lisp, you can learn the syntax of other languages quite easily.

---

### Post by xytron on 2013-06-10
I'm looking at a book called _The Programming Language LISP:__Its Operation and Applications by _Edmund C. Berkeley and Daniel G. Bobrow, editors
The M.I.T. Press.  

It states that;


>  Lisp is designed primarily for processing data consisting
of  lists of symbols. It has been used for symbolic calculations
in differential and integral calculus , electrical circuit theory,
mathematical logic , game playing, and other fields of intelligent
handling of symbols


I think that sums it up quite well.  You certainly wouldn't use Lisp for a GUI.  In part that's what holds Lisp back, some of the more capable interpreters for Lisp are quite expensive and the free ones have very non-standard and weak GUI capabilities.

The only notable application written in Lisp that I use is the Axiom computer algebra system, I can't think of any popular applications    that are written in Lisp.

It's a terrific language to explore and program with but oddly it's also rather limited in many ways for modern programming.

---

### Post by Mikeb85 on 2013-06-10
> **xytron said:**
> 
I think that sums it up quite well.  You certainly wouldn't use Lisp for a GUI.  In part that's what holds Lisp back, some of the more capable interpreters for Lisp are quite expensive and the free ones have very non-standard and weak GUI capabilities.

The only notable application written in Lisp that I use is the Axiom computer algebra system, I can't think of any popular applications    that are written in Lisp.

Emacs is quite popular, and Maxima computer algebra system.  Clojure is an up and coming Lisp, I know of at least a few Android apps written in Clojure, and some startups and financial corporations using it.

> **xytron said:**
> 
It's a terrific language to explore and program with but oddly it's also rather limited in many ways for modern programming.

Lisps like Clojure and Shen are as modern as any non-Lisp languages...

---

### Post by CptPicard on 2013-06-10
And if you think of Common Lisp in combination with CLOS, I would love to hear actual examples of how that is limited in comparison to modern languages. The whole fascination of Lisp for me lies in the fact that it is somehow a minimal distance away from everything else... but we certainly need to exclude "practicalities" such as non-existence of certain libraries and such. Those kinds of deficiencies can be fixed, they are not the fault of the language itself.

---

