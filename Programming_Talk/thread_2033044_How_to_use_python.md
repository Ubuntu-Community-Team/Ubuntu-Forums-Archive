---
title: "How to use python?"
date: 2012-07-25
forum: Programming Talk
---

### Post by Sarys on 2012-07-25
I'd like to know how to use Python. I tried few tutorials but nothing worked....

---

### Post by drmrgd on 2012-07-25
This is a pretty vague and open-ended question.  If you're having problems loading the editor, let us know.  If you're having problems getting a specific script to work, maybe posting the code will be more helpful so that we see what you're doing wrong. Alternatively, Google searches for the error you're encountering and looking at the documentation for the version you're using might help you with functions and syntax that you can't quite understand:

[http://www.python.org/doc/](http://www.python.org/doc/)

---

### Post by Sarys on 2012-07-25
> **drmrgd said:**
> This is a pretty vague and open-ended question.  If you're having problems loading the editor, let us know.  If you're having problems getting a specific script to work, maybe posting the code will be more helpful so that we see what you're doing wrong. Alternatively, Google searches for the error you're encountering and looking at the documentation for the version you're using might help you with functions and syntax that you can't quite understand:

[http://www.python.org/doc/](http://www.python.org/doc/)

Basicly I'm not sure how to start the program and how to program with python

---

### Post by drmrgd on 2012-07-25
Here are a couple links to help you get started:

[http://www.linuxtopia.org/online_books/programming_books/python_programming/index.html](http://www.linuxtopia.org/online_books/programming_books/python_programming/index.html)
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python)
[http://learnpythonthehardway.org/book/](http://learnpythonthehardway.org/book/)

There are dozens more if you just Google search Python tutorial, or introduction to Python, etc.

These links will also show you how to access Python and use it from the terminal, as well as some information on using IDEs if you prefer to go that route.  

That should get you started.  Have fun!

---

### Post by Sarys on 2012-07-25
> **drmrgd said:**
> Here are a couple links to help you get started:

[http://www.linuxtopia.org/online_books/programming_books/python_programming/index.html](http://www.linuxtopia.org/online_books/programming_books/python_programming/index.html)
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python)
[http://learnpythonthehardway.org/book/](http://learnpythonthehardway.org/book/)

There are dozens more if you just Google search Python tutorial, or introduction to Python, etc.

These links will also show you how to access Python and use it from the terminal, as well as some information on using IDEs if you prefer to go that route.  

That should get you started.  Have fun!

Problem is that those codes need more than one line of code. I can write more than one line because it runs it every time I press enter

---

### Post by greenpeace on 2012-07-25
> **Sarys said:**
> I can write more than one line because it runs it every time I press enter

Just open up any text editor (gedit for example) and write your code there and then save it.

then run it in the terminal with the following command

```
python file_name.py
```

---

### Post by qamelian on 2012-07-25
deleted.

---

### Post by FatFrog on 2012-07-25
You may want to pickup a book for python beginners if you don't have any experience. I am also new to Python and and reading Python Programming for the Absolute Beginner(3rd edition). So far, I've found it really  helpful.

---

### Post by Sarys on 2012-07-25
> **FatFrog said:**
> You may want to pickup a book for python beginners if you don't have any experience. I am also new to Python and and reading Python Programming for the Absolute Beginner(3rd edition). So far, I've found it really  helpful.

Good idea I try to keep my eyes open for helpful book.

EDIT: and where should I save the text file? And to confirm I need to write the code to text editor and run it in terminal python?

---

### Post by greenpeace on 2012-07-25
> **Sarys said:**
> where should I save the text file? 

well, that's up to you and how you want to organise your files!  I personally have a folder in my home directory called:
```
code/python/
```
and all my code goes into there... same thing for php, perl etc.


> **Sarys said:**
> And to confirm I need to write the code to text editor and run it in terminal python?

Yes, use any text editor and save the following text into a file:

```

message = "woo"
for i in range(10):
    print message

```

save it as **woo.py** and then run the following command, from the directory where the file is saved:

```
python woo.py
```

and there you have a multi-line python script.

---

### Post by Sarys on 2012-07-25
> **greenpeace said:**
>  run the following command, from the directory where the file is saved:

Run from the directory? um...how?

---

### Post by greenpeace on 2012-07-25
> **Sarys said:**
> Run from the directory? um...how?

well, if you save it as (I'll assume your username is "sarys"): **/home/sarys/woo.py**

then open your terminal, and it will open already in that directory, so you just need to run ```
python woo.py
```

if you save it in /home/sarys/code/woo.py then when you open your terminal you will need to use the **cd** command to change directory first.  The two commands should then look like: ```

sarys@pc:~$ **cd code**
sarys@pc:~/code$ **python woo.py**

```

The actual commands are in bold above to make it a little clearer

---

### Post by Angus1 on 2012-07-25
I know nothing about python, but I was at the same point you were a few days ago trying to compile C++ in ubuntu. If it's the same for python, you need to set the terminal to the directory your code file is saved in by entering cd the your directory, so for me, if I saved the file in a folder called python, in my home directory, it would be 'cd /home/angus/python' then 'python my_file.py'.

Edit: Beaten too it

---

### Post by madjr on 2012-07-25
> How to use python?

here is also some resources from a similar question:

[http://askubuntu.com/questions/8209/what-is-the-best-way-to-develop-apps-for-ubuntu](http://askubuntu.com/questions/8209/what-is-the-best-way-to-develop-apps-for-ubuntu)

---

### Post by memilanuk on 2012-07-25
Seriously.  Use the links given to you earlier.

Specifically: [www.learnpythonthehardway.org](www.learnpythonthehardway.org)

More specifically:  [http://learnpythonthehardway.org/book/ex0.html]("http://learnpythonthehardway.org/book/ex0.html")

The first section on setup answers about 99% of the questions you've asked since.

---

### Post by Tony Flury on 2012-07-25
> **Sarys said:**
> Problem is that those codes need more than one line of code. I can write more than one line because it runs it every time I press enter

Actually - that feature of the python console can be really useful - as it helps you to test and debug fragments of code and see what each line does, without having to write the code and run a debugger.

Good luck with python - hopefully you will soon get to grips with it.

---

### Post by madjr on 2012-07-25
> **memilanuk said:**
> Seriously.  Use the links given to you earlier.

Specifically: [www.learnpythonthehardway.org](www.learnpythonthehardway.org)


The first section on setup answers about 99% of the questions you've asked since.


*the hard way is easier* :)

[http://learnpythonthehardway.org/book/intro.html](http://learnpythonthehardway.org/book/intro.html)


love that!

---

