---
title: "c video tutorials"
date: 2007-11-29
forum: Programming Talk
---

### Post by limac on 2007-11-29
hello,

I was just wondering if there are any C programming language video tutorials. If not what can be the best tutorial that I can use to learn C.

Thnx

---

### Post by iharrold on 2007-11-29
Do you have a back ground in another language?  Or are you fresh to programming?

[www.cppreference.com](www.cppreference.com)
[www.cplusplus.com/reference/](www.cplusplus.com/reference/)
[http://www.research.att.com/~bs/C++.html](http://www.research.att.com/~bs/C++.html)

I find very useful for standard libraries.  With lots of examples.

For books I recommend Stroustrup and his books

[http://www.research.att.com/~bs/3rd.html](http://www.research.att.com/~bs/3rd.html)

---

### Post by limac on 2007-11-29
I am fresh to prgramming. 

Thnx

---

### Post by Vox754 on 2007-11-29
> **limac said:**
> hello,

I was just wondering if there are any C programming language video tutorials. If not what can be the best tutorial that I can use to learn C.

Thnx

This is simply silly!

Come on people, if you are a "fresh programmer" you cannot be seriously asking about video tutorials.
If you really want to become good at programming you need to learn by yourself by reading, studying and actually doing some hard work.

I don't know what else to say... Use Python? It's easier than C?
The threads referenced by the stickies already have excellent information for those who will put some effort to learning a programming language.

If you want to be taken seriously do not under any circumstance use "Thx" or "Thnx".

---

### Post by Compyx on 2007-11-30
> **iharrold said:**
> Do you have a back ground in another language?  Or are you fresh to programming?

[www.cppreference.com](www.cppreference.com)
[www.cplusplus.com/reference/](www.cplusplus.com/reference/)
[http://www.research.att.com/~bs/C++.html](http://www.research.att.com/~bs/C++.html)

I find very useful for standard libraries.  With lots of examples.

For books I recommend Stroustrup and his books

[http://www.research.att.com/~bs/3rd.html](http://www.research.att.com/~bs/3rd.html)

How would these links help someone trying to learn C? These are all about C++, which is a different language.

Here's a video about pointers: [http://www.cs.stanford.edu/cslibrary/PointerFunCBig.avi]("http://www.cs.stanford.edu/cslibrary/PointerFunCBig.avi")

But like others have said, learning to program takes a lot a time and effort. And although C is my favourite language, I wouldn't recommend it as a first language. I think Python is much more suited as a first language, it's relatively easy to learn and pretty clean, and it teaches good habits. Check out [LaRoza]("http://ubuntuforums.org/member.php?u=266234")'s sig, he has some useful links about Python.

---

### Post by limac on 2007-12-01
thanks I think I'll go with python first too. but in what ways can python be useful.

---

### Post by limac on 2007-12-01
and also how can i run or open diveintopython that already installed into my system?

---

### Post by Majorix on 2007-12-01
Dive Into Python is installed on your system under /usr/share/doc/diveintopython .

And Python is well... Easy to learn yet strong. That's the power of a "scripting" language, which are becoming more and more popular against complex "programming" languages.

EDIT: Don't read Dive into Python if you are new to programming. It's more for more advanced programmers.

---

### Post by limac on 2007-12-01
and what compiler can i use for python?

---

### Post by xeth_delta on 2007-12-01
You could also have a look at this website [http://www.mindview.net/]("http://www.mindview.net/"). It has many programming resources. You can download the PDF version of "Thinking in C" from there.

Since you are a beginner I could recommend you also a book called "Sam's teach yourself C in 21 days". (see EDIT 2)

Xeth

[EDIT] More programming resources here: [http://www.physicsforums.com/showthread.php?t=15689]("http://www.physicsforums.com/showthread.php?t=15689")
[EDIT 2] After short talk with a fellow forum member, I realized that the title could create some confusion in that one should not think that after 21 days one becomes an expert. I still think "Sam's teach yourself C in 21 days" is a good book for beginners, but one has to be realistic. It will offer a basic understanding of the language with clear examples, from which one can further improve. To become a great programmer, one needs a lot of exercise.

---

### Post by Majorix on 2007-12-01
Python usually isn't compiled. But if you still want to, you can do this:
```
python -c "import py_compile; py_compile.compile('*module_name_here*')" 
```

---

### Post by Kadrus on 2007-12-01
> **limac said:**
> and what compiler can i use for python?
Python is an interpreted language..it doesn't have any compilers..
Open terminal and type  "python"
and you can start using it 
or type a python code in gedit save the file  "something.py"
open terminal and type  "python something.py" and you see the program
You can use IDLE as Integrated development environment for Python
Open terminal and type:
```
sudo apt-get install idle
```

---

### Post by limac on 2007-12-01
> **xeth_delta said:**
> You could also have a look at this website [http://www.mindview.net/]("http://www.mindview.net/"). It has many programming resources. You can download the PDF version of "Thinking in C" from there.

Since you are a beginner I could recommend you also a book called "Sam's teach yourself C in 21 days"

Xeth

[EDIT] More programming resources here: [http://www.physicsforums.com/showthread.php?t=15689]("http://www.physicsforums.com/showthread.php?t=15689")

thanks

---

### Post by aks44 on 2007-12-01
> **xeth_delta said:**
> "Sam's teach yourself C in 21 days"

Such claims are quite misleading IMO.
[That short article](http://www.norvig.com/21-days.html) sums it up quite well. :roll:

---

### Post by xeth_delta on 2007-12-01
> **aks44 said:**
> [http://www.norvig.com/21-days.html](http://www.norvig.com/21-days.html) :roll:

aks44: I did not not suggest that book in the hope that he will become a programmer in just 21 days. That would be not reallistic. We know very well that the skills needed to be proficient in a programming language are acquired over a long period of time, and especially exercise, exercise and exercise yet again.

I suggested he could read that because it happens to have really clear and easy examples that will be useful to a beginner, and after finishing the book he will have at least a general understanding of how to write a program in C.

I apologize if I am misunderstanding you, but I think the irony in your reply to my suggestion is not justified.

Xeth

---

### Post by LaRoza on 2007-12-01
> **Kadrus said:**
> Python is an interpreted language..it doesn't have any compilers..


Yes it does, in fact, it has many.

---

### Post by aks44 on 2007-12-01
> **xeth_delta said:**
> I did not not suggest that book in the hope that he will become a programmer in just 21 days. That would be not reallistic. We know very well that the skills needed to be proficient in a programming language are acquired over a long period of time, and especially exercise, exercise and exercise yet again.
[...]
I apologize if I am misunderstanding you, but I think the irony in your reply to my suggestion is not justified.

I know *you* didn't mean that the OP would be able to learn C in a few days. But I mentioned that link (which you probably already knew) just to make sure the OP realizes that.
FWIW the irony wasn't aimed at you, but at the book's title itself. In fact, any book claiming this sort of things is at best quite misleading IMHO.

Sorry for the confusion. Post edited to lower the risk of misunderstanding.

---

### Post by xeth_delta on 2007-12-01
> **aks44 said:**
> I know *you* didn't mean that the OP would be able to learn C in a few days. But I mentioned that link (which you probably already knew) just to make sure the OP realizes that.
FWIW the irony wasn't aimed at you, but at the book's title itself. In fact, any book claiming this sort of things is at best quite misleading IMHO.

Sorry for the confusion. Post edited to lower the risk of misunderstanding.

Ok, I imagined that it might have been a misunderstanding. I'm sorry about that, too.
I agree with you that the title could be misleading, but still believe that for a novice the comtents is not bad at all. It leads to a basic understading of the language from which one can build build more complete skills and read more advanced topics.

I will also edit my original post to make it clear that one needs quit a few more days than 21 to become a programmer.

Xeth

---

### Post by bruce89 on 2007-12-01
Arrrggggghhhh, what is it with Python these days?

---

### Post by LaRoza on 2007-12-01
> **bruce89 said:**
> Arrrggggghhhh, what is it with Python these days?

Are you having trouble with it?

---

