---
title: "Possibilities of Python"
date: 2009-05-04
forum: Programming Talk
---

### Post by ade234uk on 2009-05-04
I am just wondering what possibilites there are using Python. Can you create applications on Ubuntu with it?

I have being doing .PHP for a few years, I am no way professional at it but my experience has allowed me to create websites with it.

I am looking for something new to try and possibly extend on my experience.

---

### Post by Kilon on 2009-05-04
> **ade234uk said:**
> I am just wondering what possibilites there are using Python. Can you create applications on Ubuntu with it?

I have being doing .PHP for a few years, I am no way professional at it but my experience has allowed me to create websites with it.

I am looking for something new to try and possibly extend on my experience.

Well python is a very powerful programming language which also happens that is very easy to use and learn. So that basically mean you can use it for anything you require. Ubuntu applications is included in the "anything" term of course. 

Have you got anything specific in your mind ?

---

### Post by ade234uk on 2009-05-04
I recently, well a few days ago visited a website that had tutorial creating bash scripts. I was wondering if you could implement Python with this.

---

### Post by loell on 2009-05-04
yes very much so. :)

---

### Post by jespdj on 2009-05-04
> **ade234uk said:**
> I am just wondering what possibilites there are using Python. Can you create applications on Ubuntu with it?
Absolutely! In fact, Python is a very popular programming language for applications on Ubuntu, some of the applications included with Ubuntu were written in Python.

---

### Post by ade234uk on 2009-05-04
Fantastic, are there any starting points site I could visit?

Have you got any examples in Ubuntu of where Python has been used?

I suppose it is far easier and more flexible to create applications in Python that it is to say something like c++

---

### Post by Kilon on 2009-05-04
> **ade234uk said:**
> I recently, well a few days ago visited a website that had tutorial creating bash scripts. I was wondering if you could implement Python with this.

Actually large part of Ubuntu utilises python to interact with the user or , to do internal processing. So already you can bet that you use python . 

Python comes with its own shell which is more powerful then the terminal. There is even IPYTHON that stretches command line power to the far reaches. So bassically that means that python is "thousand times" more powerful than a bash script. But still because python is very easy to use , you will feel rather familiar with it without a need to spent weeks reading documentation. 

Your experience with PHP will surely help you alot. 

I will say go for it, you have nothing to lose.

---

### Post by geirha on 2009-05-04
Many of the games that installs with Ubuntu by default are written in python. update-manager, alacarte (The main menu editor), software properties are all written in python. There are several others too.

Grab their source and have a look.
```
apt-get source gnome-games
apt-get source update-manager
apt-get source alacarte
...

```
apt-get source will download a tarball of the source, and possibly some patches, to the current directory, and then unpack it and apply the patches.

---

### Post by ghostdog74 on 2009-05-04
> **Kilon said:**
> 
Python comes with its own shell which is more powerful then the terminal
...
So bassically that means that python is "thousand times" more powerful than a bash script. 
This is so damn not true. I hope you get your facts right next time before you post such a comparison.

---

### Post by Kilon on 2009-05-04
> **ghostdog74 said:**
> This is so damn not true. I hope you get your facts right next time before you post such a comparison.

Why ? is there is any doubt that a real programming language offers alot more functionality than bash ?

---

### Post by ooobooontooo on 2009-05-04
If you're starting to learn python, I highly recommend [http://www.diveintopython.org/]("http://www.diveintopython.org/"). Amazing site in my opinion. You can probably stop somewhere in the middle and move on to other sources that talk about your areas of interest.

---

### Post by ghostdog74 on 2009-05-04
> **Kilon said:**
> Why ? is there is any doubt that a real programming language offers alot more functionality than bash ?
 
take a look at this quote you made
> 
Python comes with its own shell which is more powerful then the terminal

if by "terminal", you mean the bash shell, then I am hope you are comparing it against the Python shell only (no modules/libraries allowed, yes that includes os, sys, time etc). With this in mind, how do you justify the Python shell is more powerful than bash shell, 

take a look at this other quote you made
> 
So bassically that means that python is "thousand times" more powerful than a bash script.

i assume you are comparing doing some tasks in Python vs doing the same task with a bash script (with that, it includes the usage of *nix tools). How do you justify that Python's a "1000 times" more powerful than bash script?

don't misunderstand, i am not disapproving of your stand on Python as the next language for the OP, but only on the above 2 comments. If you have done minimal shell , but lots of Python, then don't even start to compare them.

---

### Post by Kilon on 2009-05-04
> **ghostdog74 said:**
>  no modules/libraries allowed, yes that includes os, sys, time etc



of course I am going to include all the modules and libraries that come by default with any python distribution .

That is the python afterall, from one hand like bash is a scripting language on the other hand unlike bash is a programming language as well.

---

### Post by ghostdog74 on 2009-05-04
> **Kilon said:**
> of course I am going to include all the modules and libraries that come by default with any python distribution .

ok, so now you are talking about the whole Python distribution. Well then, bash has its own "modules" too. then how do you justify
"Python comes with its own shell which is more powerful then the terminal"  ?

---

### Post by Kilon on 2009-05-04
> **ghostdog74 said:**
> ok, so now you are talking about the whole Python distribution. Well then, bash has its own "modules" too. then how do you justify
"Python comes with its own shell which is more powerful then the terminal"  ?

python shell is powerful because it provides full support to the python language , in short any python command is accessible. 

I am not saying that bash is useless. It is not,  because bash already provides access to specific functions like updates within a simple command while python would require some extra coding or a direct calls to the bash commands which of course I am sure you will call "cheating" . lol 

But the bottom line is that bash is no programming language. 

1)It is slower

2) Does not report errors as clearly

3) Not as flexible

4) Far less available libraries to access OS functions

5) etc. etc. 

I think the only reason why people still prefer bash instead of python , is because for some type of work bash is still considered the de facto standard as no other programming language that I am aware of can function as bash replacement as python can. 

You ask for me why I think python is "1000 times more" powerful than Bash , well simply the fact that I can call from python shell any command I like , like drawing windows, accessing OpenGl, opening an sqlite3  connection etc. Even if that means adding a library or two to the path.

---

### Post by ghostdog74 on 2009-05-04
> **Kilon said:**
> python shell is powerful because it provides full support to the python language , in short any python command is accessible. 

so too is bash shell.

> 
But the bottom line is that bash is no programming language. 

flawed. please check the meaning of programming language.

> 
1)It is slower

not true. if you disagree with me on this, show an example of how  
slow it is as compared to Python. 

> 
2) Does not report errors as clearly

like how so?

> 
3) Not as flexible

really? examples? 

> 
4) Far less available libraries to access OS functions

really? tar, mv, cp, grep, awk , sed, and many more all these are bash's available libraries. Much like Python's os, sys, re etc. Therefore, the above is still not true.




> 
I think the only reason why people still prefer bash instead of python , 

i did not say the reason i disagree with your 2 comments is about people preferring bash than Python.

---

### Post by Kilon on 2009-05-04
Sorry But I cannot bother to turn this to a Bash vs Python battle. I am getting bored of "VS" battles and really tired. 

If you think that bash is more powerful than python , then good luck at using it . I am new with both , I see no reason in using bash for accessing os functionality that goes beyond the capabilities of gui instead of python. 


PErsonally I always hated bash and preferred GUI. Even the old day when I was using CPM and DOS.

---

### Post by ajackson on 2009-05-04
I don't think that you can readily compare bash and python, both can be used as scripting languages.

But comparing them is like comparing apples and oranges.

---

### Post by ghostdog74 on 2009-05-04
> **Kilon said:**
> Sorry But I cannot bother to turn this to a Bash vs Python battle. I am getting bored of "VS" battles and really tired. 

then be careful next time when you want to "compare" languages. without sufficient knowledge of the languages you want to "compare", don't assume.

> 
If you think that bash is more powerful than python

from all my posts to this thread, i have not mentioned anything that says "bash is more powerful than Python" or vice versa.

> 
I am new with both ,

i am not. that's why i know, they both have merits (and demerits) of their own.

---

### Post by ade234uk on 2009-05-04
This looks interesting. Thanks for all your help.

---

### Post by Kilon on 2009-05-04
> **ghostdog74 said:**
> then be careful next time when you want to "compare" languages. without sufficient knowledge of the languages you want to "compare", don't assume.



That was a good laugh....  So is this a knowledge comparison , your knowledge is bigger than mine.... oh boy ... why did you say so from the start I would not dare to make such claims.... 

Just chill out take and take a big breath , I did not say I agree with you , as to the line of argument "i have been doing this for quite some time and I am better than you ...." does not impress me a bit. You are not the first who is using it and sadly you wont be the last one.

Just offer your opinion and do not try to humiliate others because you might get what you are asking for.  

I had no wish to reply to you , but you throw your bait, and it was pity not to bite.

---

### Post by Elfy on 2009-05-04
OP has thread answered now. Closing thread.

---

