---
title: "Specific-ness or General knowledge?"
date: 2008-01-26
forum: Programming Talk
---

### Post by DanielJackins on 2008-01-26
I was just wondering if it is generally smarter to learn the ins and outs of one language, or to familiarize yourself as well as possible with many different languages?

I know HTML and CSS fairly well, and am starting to learn PHP. After that I plan on moving to something like C++ or Python.

---

### Post by popch on 2008-01-26
I find it most useful to have a broad knowledge of programming languages including a few less usual ones.

Unfortunately, I came by this knowledge by actually learning and using most of them.

---

### Post by y-lee on 2008-01-26
I suppose it would depend upon what you are trying to get out of  programming. It takes a long time to learn the "ins and out of a language", for C++ at least 5 years.  you might want to read this article,[Computer Science Education: Where Are the Software Engineers of Tomorrow?l]("http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html"), which had been discussed on several programming blogs i read, both pro and con. I sort of agree with him on languages choices except I'm not sure about Ada...don't know it. Python is popular and pretty cool and easier than C++. I might also add it really helps to learn some ASM, ya don't have to be a guru in it but it will help one understand what is REALLY going on.

---

### Post by LaRoza on 2008-01-26
> **DanielJackins said:**
> I was just wondering if it is generally smarter to learn the ins and outs of one language, or to familiarize yourself as well as possible with many different languages?

I know HTML and CSS fairly well, and am starting to learn PHP. After that I plan on moving to something like C++ or Python.

Learn as much as you can, but don't dilute your knowledge.

When starting, stick with one langauge until you get a good handle on it. Then explore.

I usually stick with Python, PHP, C and ECMAScript for all of my programming, but I play with as many others as I can.

---

### Post by DanielJackins on 2008-01-26
Okay, thanks for the opinions :)

Also, one last question;

Whats the difference (if any) between programming in Linux or in Windows?

---

### Post by pmasiar on 2008-01-26
Language is a tool for solving problems. Always look for the best tool for the job. Different jobs require different tools.

It does not do you any good to know just a little from many languages if you don't know at least one of them deeply enough to solve most problems in the area where you specializes. But also it might be waste of time to spend time learning 5 different languages solving problems in same niche.

Python is generally considered as good language for beginners. Is simple enough so it is easy to learn, powerfull enough so you can solve real problems with it, scales reasonably good for bigger projects. It is more complicated than LOGO (which was designed for total beginners), it is slower than C, and for big projects languages like Java, C++ or Ada have more total control on modules, but Python is single language in a sweet spot between all of them. And is good for web-based apps too.

Decide in what area you want to specialize, then learn one language, deeply enough. Then, learn languages from other areas. Learn C (or even better, ASM) to understand what is happening down there, close to the metal. Learn very high level language, like Lisp, Scala, or Forth, to expand your mind. Then you might want to learn C# or Java to get some boring job... :-)

---

### Post by LaRoza on 2008-01-26
> **DanielJackins said:**
> 
Whats the difference (if any) between programming in Linux or in Windows?

Not much.

If you use cross platform and standardized languages, most code work perfectly on either.

Windows has its own Microsoft development tools, but one can easily use Python, C, Ruby, C++, and others in place of .NET.

If you learn Ansii C, all you need is a compliant compiler. The Python interpreter is the same with each version number on each platform.

(You can do Windows/Linux specific stuff with these languages, if you wanted to)

Most GNU tools are available for Linux, and in fact, Cygwin brings almost the entire Linux platform to Windows.

---

### Post by popch on 2008-01-26
> **LaRoza said:**
> Not much..

Unless, of course, you want to do things which are specific to one of the platforms. 

Also, some functions are provided by every OS although the particulars might be quite different. In those cases, it can become something of a challenge to write a program which works correctly in every environment.

These are but special cases. Otherwise I can verify what LaRoza already said.

---

### Post by LaRoza on 2008-01-26
> **popch said:**
> Unless, of course, you want to do things which are specific to one of the platforms. 

Also, some functions are provided by every OS although the particulars might be quite different. In those cases, it can become something of a challenge to write a program which works correctly in every environment.

These are but special cases. Otherwise I can verify what LaRoza already said.

"Not much" not "No difference"

Of course, using VBScript makes sense sometimes and using the Shell is the best way. 

Using standard languages, like Ansii C, and interpreted languages like Python are the same on most platforms.

Of course, one can write Windows specific C and use Python with *nix only functions, and in fact, I do it sometimes. Like my system restore program, it probably won't work at all on Windows in any way and will likely throw errors.

---

### Post by pmasiar on 2008-01-27
HTML and CSS are not exactly programming languages. You have clue now that syntax is important, and computer cannot make sense of file if it has obvious typo, but not much more is relevant to programming.

Looks like you try to create dynamic web pages with PHP. I would recommend for you to take a break and learn programming first, in a simpler environment: in plain text/commandline. And using simpler language, Python.

After you get feeling about programming, module design, debugging, data structures, and all that, you can learn other programming languages (like PHP) rather quickly. It is often just different syntax to express the same concepts, and Python's syntax is the easiests. 

Debugging code is rather different from finding errors in HTML/CSS: you cannot see result, it is just status of all variables which went wrong and something unexpected happened.

---

### Post by LaRoza on 2008-01-27
> **pmasiar said:**
> 
Looks like you try to create dynamic web pages with PHP. I would recommend for you to take a break and learn programming first, in a simpler environment: in plain text/commandline. And using simpler language, Python.

Debugging code is rather different from finding errors in HTML/CSS: you cannot see result, it is just status of all variables which went wrong and something unexpected happened.

In my opinion, and experience, learning server side scripting is a very good way to learn programming IF the person already knows XHTML and CSS.

Most of my programming is web based, and I think in terms of the web when programming. 

PHP is good for the goals stated, and is in an area that the OP is comfortable.

Debugging code on the server is easy. You get errors just like you do in Python with line numbers.

There is almost everything that Python has, with a different syntax, and no namespaces. The lack of namespaces is the worst thing about the language. Also, PHP has two forms of the for loop, one like Python, one like C...

---

### Post by pmasiar on 2008-01-27
> **LaRoza said:**
> PHP is good for the goals stated, and is in an area that the OP is comfortable.

OP plans to lern Python anyway, so IMHO he may as well start with it. PHP (without the namespaces) has about 5000 functions, core Python is simpler to learn. Data structures are quite similar, PHP is just closer to Perl and all the sigils.

I would recommend OP to take a look at Python, try Python shell (where you can learn language syntax on line at a time) for couple hours/days. If PHP after that still makes more sense, maybe OP is one of the 5% of people who does not "get" Python, nothing wrong with that.

> Debugging code on the server is easy. You get errors just like you do in Python with line numbers.

Learning language in shell is even simpler, IMHO. Syntax errors are easy, but logical errors result in a traceback, which might, and more often might not, be related immediately to what went wrong.

BTW Python can give you nice traceback on CGI server (with colors), if you use cgitb module.

---

### Post by LaRoza on 2008-01-27
> **pmasiar said:**
> PHP (without the namespaces) has about 5000 functions, core Python is simpler to learn. 

I would recommend OP to take a look at Python, try Python shell (where you can learn language syntax on line at a time) for couple hours/days. If PHP after that still makes more sense, maybe OP is one of the 5% of people who does not "get" Python, nothing wrong with that.


I hate that about PHP.... I have a habit of naming functions oddly in all of my programming to avoid collisions because of PHP.

For programming, I'd recommend Python too. (But oddly, I feel an urge to recommend Java...)

---

### Post by pmasiar on 2008-01-27
> **LaRoza said:**
>  (But oddly, I feel an urge to recommend Java...)

It's a clear sign you should go sleep. That's bad. You, and recommending Java? 

Or you are stuck in job searching mode? Then again, get some sleep... It is not that desperately bad I hope. :-) New search, new hope, will start in the morning.

---

### Post by LaRoza on 2008-01-27
> **pmasiar said:**
> It's a clear sign you should go sleep. That's bad. You, and recommending Java? 

Or you are stuck in job searching mode? Then again, get some sleep... It is not that desperately bad I hope. :-) New search, new hope, will start in the morning.

It was a joke :)

I am wide awake.

Even in my nightmares Java is absent. 

I have been reading H.P. Lovecraft at night, now that leads to some cool dreams. 

No, I found a good place for a job. Need to apply now. Why haven't I? No ink in my printer.

I actually got up a few hours ago.

---

