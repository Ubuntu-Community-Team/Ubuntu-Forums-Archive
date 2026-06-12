---
title: "Bash vs programming"
date: 2010-05-24
forum: Programming Talk
---

### Post by TheHimself on 2010-05-24
I'm more or less familiar with C but I have difficulty learning bash. :confused: The syntaxes are very different and bash is very unintuitive (which I think has to do with it being an interpreted language and so must be easy to parse). 

The reason need bash is to do things like finding and replacing something in a file or performing something on several files at once. Things for which writing and compiling a program is too much. I'm following the wisdom “There is more Unix-nature in one line of shell script than there is in ten thousand lines of C.” ([http://www.catb.org/~esr/writings/unix-koans/index.html](http://www.catb.org/~esr/writings/unix-koans/index.html))

So, what is your suggestion? Should I learn python instead?

---

### Post by nmccrina on 2010-05-24
If what I need to do is just a repetitive bunch of commands with no looping or I/O I'll put them in a .sh file and be done, but anything more complex than that I usually just do in Python. My two cents. :D

---

### Post by lostinxlation on 2010-05-24
That' why I always use C-shell variants such as tcsh.

---

### Post by dribeas on 2010-05-25
The bash syntax is not really complex. In fact I find it easier than most programming languages. What is it that you find hard to grasp? The main problem with bash is not bash itself, but knowing how the different programs you are calling work (and escaping characters, I agree that is not easy).

Bash is really powerful not for what it offers but for all the functionality that you can get directly from other programs/languages. If you post your concrete need, I am sure someone can help you with it.

---

### Post by TheHimself on 2010-05-25
I meant the syntax of bash *commands* is unintuitive for me. Like that of awk. It makes me feel dumb! For me working with functions like fgets and fputs is much easier. Also all those brackets, parentheses and quotes which when put around expressions give them different meanings are confusing. Here are some specific examples that I've not figures out how to do in bash.

1) Assign something that you read from a  stream (like a number you read from a file) to a variable. Note that the number exists as a string in the file.

2) How to parse a string (say, the command line input) into tokens.

3) How to add a line to a file in a specific position.

---

### Post by uOpt on 2010-05-25
Bourne shell can be pretty powerful, but portable programming on there is a nightmare since you are subject to differences in all the commandline utilities you call. And even "real" arrays require that you move up from general bourne shell to bash.

Learning Python sounds like a good idea.

---

### Post by nmaster on 2010-05-25
> **TheHimself said:**
> I meant the syntax of bash *commands* is unintuitive for me. Like that of awk. It makes me feel dumb! For me working with functions like fgets and fputs is much easier. Also all those brackets, parentheses and quotes which when put around expressions give them different meanings are confusing. Here are some specific examples that I've not figures out how to do in bash.

1) Assign something that you read from a  stream (like a number you read from a file) to a variable. Note that the number exists as a string in the file.

2) How to parse a string (say, the command line input) into tokens.

3) How to add a line to a file in a specific position.
  
it seems like you want to edit text files. bash can be good for that but you're right that it might be easier to use something else. python is one option, but perl might be even better.  it depends on what you want to do and who you talk to.

---

### Post by Dougie187 on 2010-05-25
If you are just finding and replacing things in files, you should use awk or sed. Using those you can write a very simple bash script to find and replace the same thing in several files.

---

### Post by P.ap G on 2010-05-25
If you need to alter a text file use a text editor I use vim but that takes a  little getting used to - try gedit.

---

### Post by nmaster on 2010-05-25
> **Dougie187 said:**
> If you are just finding and replacing things in files, you should use awk or sed. Using those you can write a very simple bash script to find and replace the same thing in several files.

it can be simple, but there is a lot to learn. there is an entire o'reilly book about sed and awk: [http://oreilly.com/catalog/9781565922259](http://oreilly.com/catalog/9781565922259)

if you're looking for syntax that is more like C, using something like python might be easier.  it seems a matter of preference. i guess its up to the OP.

---

### Post by nvteighen on 2010-05-25
Many are implying the same that I'm going to say, but...

bash is a powerful language, but it's intended for writing "glue" between different system utilities. Yes, you can write a massive RPG in bash, but it will be hard because the language is designed and optimized for the purpose I mentioned above.

It seems you need sed and awk, like others have said... but, if you feel more comfortable with general programming languages (although it will be just overkill), you may look at Perl (actually, have a look at it anyway, it's a great language). Python's regexp and string-processing tools are good, but not the strongest you can get.

It all boils down to the well-known mantra: *Use the right tool for each task...*.

---

### Post by jjpcexpert on 2011-08-18
Both Bash and C are programming languages. 

Talk about reviving an old thread!

---

### Post by cgroza on 2011-08-18
> **jjpcexpert said:**
> 
Talk about reviving an old thread!
That was evil. Have some respect for deceased threads. :P

---

