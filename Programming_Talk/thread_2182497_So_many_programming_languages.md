---
title: "So many programming languages"
date: 2013-10-21
forum: Programming Talk
---

### Post by sha1sum on 2013-10-21
Hi guys,

I'm learning to use shell commands and I'm trying to write some basic shell scripts. But as I'm getting a keyhole view of the world of programming, I'm amazed at how many programming languages there are. 

Some of the one's I've heard about: (most of those I just know by name and I have no clue what they do)

C, C++, perl, ruby, java, javascript, PHP and of course good old HTML and CSS and I bet there are more.

Can somebody tell me what the deal is with so many programming languages? Do professional programmers know all of them?

---

### Post by Vaphell on 2013-10-21
the deal is that all these languages are tailored for different things and many of them come to life to fix some perceived shortcoming of other languages.
Some languages are close to metal (eg C) and are best when the performance is top priority, while more abstract ones are slower in exchange for convenience, saving programmers time (eg python). Some are kings of specific tasks, eg there is nothing as powerful when it comes to text manipulation as perl.

No, professional programmers don't know all of them, but know a few and with experience the time to absorb another one, should the need arise, gets shorter and shorter.

---

### Post by sha1sum on 2013-10-22
Thanks, I understand.

---

### Post by sha1sum on 2013-10-22
Okay one more question. You say that for text manipulation nothing is as powerful as perl. I thought that for text manipulation you use gedit. Or vi if you believe that pressing Esc + colon + w + enter is somehow faster than ctrl + s. When you say text manipulation, does that mean editing a lot of text files at once?

---

### Post by trent.josephsen on 2013-10-22
I'll pass over your editor-ignorance, and just mention that Perl does a lot more than you can do with an editor.

For instance, to replace ä with ae in all the .txt files in the current directory:
```
$ perl -pe 's/ä/ae/g' *.txt
```
To change hexadecimal numbers to decimal:
```
$ perl -pe 's/(0x[0-9a-f]+)/hex $1/ige'
```
To display the 10 most commonly used commands in .bash_history:
```
$ perl -ne '/(.*?)\s/; $hash{$1}++ if $1; END { @l = sort { $hash{$b} <=> $hash{$a} } keys %hash; print join($/, @l[0..9]) . $/}' ~/.bash_history
```

And those are just one-liners.

---

### Post by Lars Noodén on 2013-10-22
You can also do in-place editing.

```
$ perl -i.bak -pe 's/ä/ae/g' *.txt
```

That will do the editing in the files, but leave backup copies of the originals with the .bak appended  to the name.  

perl is the tool to go to for string manipulation.

---

### Post by sha1sum on 2013-10-22
That's fascinating. I thought that working with a programming language always involved writing code in a text file and then compiling it to get a piece of software. But I realize that perl is a bit like other commands; you can just type the individual lines in the terminal and get effect. Interesting, I'm going to look into it. Thanks guys :grin:

---

### Post by nathan-b on 2013-10-22
> **sha1sum said:**
> 

Can somebody tell me what the deal is with so many programming languages? Do professional programmers know all of them?

Linus Torvalds knows all of them. That's why he's so awesome. :cool:

---

### Post by Vaphell on 2013-10-22
> **sha1sum said:**
> That's fascinating. I thought that working with a programming language always involved writing code in a text file and then compiling it to get a piece of software. But I realize that perl is a bit like other commands; you can just type the individual lines in the terminal and get effect. Interesting, I'm going to look into it. Thanks guys :grin:

yes, interpreted languages can be made to run like ordinary commands directly in terminal, without creating full blown files. Usually they offer an option to pass the block of code to execute.

Like you have seen with these perl examples
```
perl -pe 'some code'
```
you can do the same with bash and python and awk and ...
```
bash -c '<bash code>'
python -c '<python code>'
awk '<awk code>'
```
most people don't even know that awk is a language and you can write scripts in it, because they only use it in inline mode :)

that's one of main advantages of interpreted/scripting languages. They allow to create quick and sometimes dirty, ad hoc solutions for tasks (especially when they specialize in them like perl in text) that you'd be hard pressed to finish in reasonable time in compiled languages.

---

### Post by King Dude on 2013-10-22
Choose a language that fits your needs best. For example, if you would like your program to have good cross-platform compatibility, Java might be good for that. If you'd like to create an Ubuntu application, I suggest C++ and Python. If you'd like to improve the Linux kernel, I suggest C and (possibly) Assembly.

Personally, I prefer C++, but that's just me.

The most important thing to keep in mind, however, is that a mastery of a single language is tenfold better than just a basic knowledge of multiple languages.

---

### Post by trent.josephsen on 2013-10-23
> **King Dude said:**
> Personally, I prefer C++, but that's just me.

The most important thing to keep in mind, however, is that a mastery of a single language is tenfold better than just a basic knowledge of multiple languages.
You can find [url=
http://ubuntuforums.org/showthread.php?t=1873951&p=11418085#post11418085]my[/url] [opinion](http://ubuntuforums.org/showthread.php?t=2002517&p=12023844#post12023844) [on](http://ubuntuforums.org/showthread.php?t=1873951&page=2&p=11421156#post11421156) [C++](http://ubuntuforums.org/showthread.php?t=2003553&p=12026382#post12026382) elsewhere.

As for mastery, we [just had](http://ubuntuforums.org/showthread.php?t=2179521) that discussion. In principle, I agree: being really good at one thing is better than being mediocre at a bunch of things, and this applies in other realms besides programming. But if you're looking to make a career of programming, like the OP of that other thread, you'll find yourself on the road to mastery much quicker if you have a broader range of experience early. Few people can afford to specialize from the get-go.

Hobbyists may feel free to disregard the above paragraph :)

---

### Post by King Dude on 2013-10-23
> **trent.josephsen said:**
> You can find [my]("http://<br />http://ubuntuforums.org/showthread.php?t=1873951&p=11418085#post11418085") [opinion]("http://ubuntuforums.org/showthread.php?t=2002517&p=12023844#post12023844") [on]("http://ubuntuforums.org/showthread.php?t=1873951&page=2&p=11421156#post11421156") [C++]("http://ubuntuforums.org/showthread.php?t=2003553&p=12026382#post12026382") elsewhere.

As for mastery, we [just had]("http://ubuntuforums.org/showthread.php?t=2179521") that discussion. In principle, I agree: being really good at one thing is better than being mediocre at a bunch of things, and this applies in other realms besides programming. But if you're looking to make a career of programming, like the OP of that other thread, you'll find yourself on the road to mastery much quicker if you have a broader range of experience early. Few people can afford to specialize from the get-go.

Hobbyists may feel free to disregard the above paragraph :)
I never said C++ was the superior language. I just said that it's what I prefer.

---

### Post by trent.josephsen on 2013-10-23
I didn't say you did, but it's all good :) Language wars are fun sometimes but I really just wanted to address the other point.

---

### Post by Scott_DuBois on 2013-10-25
> **sha1sum said:**
> That's fascinating. I thought that working with a programming language always involved writing code in a text file and then compiling it to get a piece of software. But I realize that perl is a bit like other commands; you can just type the individual lines in the terminal and get effect. Interesting, I'm going to look into it. Thanks guys :grin:

When I started to learn programming I had the same questions, which one? My first language was Basic back in 1983 on an old C64 and a lot has changed since then. The key to deciding which one is knowing first what you wish to accomplish. Each language is tailored towards accomplishing a specific type of task. With so many languages to choose from it can be rather daunting to decide which one is best, particularly when first starting to learn. Java is probably one of the more popular languages as it touts the "write once, deploy everywhere" motto but, it's rather slow compared to C or C++ which runs native compared to relying on a virtual machine. If your interest is in building a first GUI program just to "get your feet wet" then I would suggest Java and using an IDE (Integrated Development Environment) such as NetBeans or Eclipse. 

Of course you also need some material to get you going. One of my instructors at my university turned me on to this website where you can download complete books on all kinds of programming languages with easy to follow step-by-step instructions that will keep you both busy and entertained for some time. The material is not the most recent releases but, they are new enough to be completely relevant to today's standards.

---

### Post by trent.josephsen on 2013-10-25
> **Scott_DuBois said:**
> Of course you also need some material to get you going. One of my instructors at my university turned me on to this website where you can download complete books on all kinds of programming languages with easy to follow step-by-step instructions that will keep you both busy and entertained for some time. The material is not the most recent releases but, they are new enough to be completely relevant to today's standards.
You may not be aware that the books on the page you linked are not provided through legal channels, which is against the forum rules.

There are plenty of free online resources without legal problems, such as [A Byte of Python](http://swaroopch.com/notes/python/) which has good reviews, and I've heard good things about [cplusplus.com](cplusplus.com) and [cprogramming.com](cprogramming.com), although I haven't used any of those. (My personal favorite introductory programming text is *Learning Perl*.)

---

### Post by llanitedave on 2013-10-26
Java is not my first choice, but it's NOT slow.

---

### Post by hwindle83 on 2013-11-06
It depends what you want to use your programming skills for. You can't learn all languages equally, unless it's how to write very simple programs in each. I've picked 1-3 languages to learn in depth.

I do web development - so I'm learning Python in depth (for things like Django), PHP and HTML. I never really think of HTML as a programming language, more document markup. Learning databases (SQL) becomes more like a programming language for the more advanced uses of it, like writing procedures.

For writing programs for KDE/razor-qt - learn C++, because that's what all the qt programs use.

For easy programming languages, shell scripting is sort of easy but the syntax is very different from Python. Python is fairly easy to get started in as is JavaScript.

---

### Post by sha1sum on 2013-11-07
I see a few people commenting on my thread that only have one bean. The only conclusion I can draw is that they made an account just for answering my question. Thanks guys! Much appreciated. (And all you other people too of course).

Right now I'm (still) learning bash, and I'm using it to write simple scripts (the last one I made is one that imitates the seq command. It's very simple, but still requires some attention to neatly program it.) After that I'm planning on learning perl and I've already found a nice book on it. I've read that perl was designed by a human linguist, so I'm curious to learn how it works.

After that... hmm.. I think I'll look at the source code of my favorite shell command (guess which one) and some other programs, see in which language they were written, and then decide if I'll learn another one.

---

