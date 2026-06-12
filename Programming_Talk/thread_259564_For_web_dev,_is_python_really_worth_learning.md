---
title: "For web dev, is python *really* worth learning?"
date: 2006-09-17
forum: Programming Talk
---

### Post by Burgresso on 2006-09-17
Hey,

I'm really interested in learning python, but I  want to be sure it's wise to learn it first. I'm a web developer.

Can you *really* build enterprise-class web apps with it - comparable even to PHP, or better? 

Can you do it without using a cgi-bin, perhaps with mod_python instead? If I don't choose to host my projects myself, are their good hosts?

I don't care if not used much, or used often, is trendy or not. I just to be sure it's a quality language - that can build powerful web apps.

Thank you so much. I look forward to enlightenment. :)

regards

burgresso

---

### Post by ciscosurfer on 2006-09-17
Python quite robust as a programming language.  Many, many apps are written in python.  If you're familiar with other languages, python will be easy for you to pick up.  Creating GUI's are easy with the [wxPython environment]("http://www.wxpython.org/").  I don't have much experience creating "enterprise-class" web apps, but do know that python has an extensive language set and can be made to do most anything.

---

### Post by ametade on 2006-09-17
Why don't you take a look at the Django framework. It's something like Ruby on Rails but using python as the programming language:

[http://www.djangoproject.com/](http://www.djangoproject.com/)

---

### Post by droppedd on 2006-09-17
I use PHP, Perl, Java and Python every day at work -- and Python is by far my favorite language to use.
For web development, i'd recommend a good framework with templating - django's probably the best right now, though it does have a bit of a learning curve, but it enforces proper enterprise-style MVC form (like Struts/Hibernate/Spring in Java, or Ruby on Rails). Django has been used to build sites that pull a lot of traffic - and apache with mod_python and django is certainly capable of being just as fast - if not faster - than straight php. [http://wiki.rubyonrails.org/rails/pages/Framework+Performance](http://wiki.rubyonrails.org/rails/pages/Framework+Performance) - a highly flawed analysis of performance of Symfony (a php framework), ruby on rails and mod_pythoned django. (python wins. take it with a grain of salt, it's not a fair comparison, but it should tell you python can hold its own).

php is quicker to pick up than frameworks, and has a *ton* of existing code you can reuse - which makes it the easy choice if the problem you're developing for fits neatly into something there's already a good solution for (like a simple blog, let's say). But PHP also really encourages terrible web coding practices (trust me on that - i wade through hard-coded SQL and mail calls in presentation web code every day and curse the names of the previous programmers at my company). If you were looking for an equivalent in Python you could code straight in Python with straight modpython and maybe one of the bazillion templating langauges like Kid -- but i wouldn't recommend that for anything more than a thrown-together quick website.

Python has such a nice, clean syntax and handy builtin libraries (without going overboard like php's libraries), and the interactive prompt makes learning the language a breeze. But hey - don't take my word for it. You'll probably want to know some php sooner or later anyways, just because everything uses it.They're all just tools; Paul Graham made a few million bucks coding web apps in Lisp 12 years ago. Anything's possible with most modern languages. Take the time to learn the ins and outs of more than one; pick the one that's best for your task, and one that you enjoy working with.

---

### Post by X.Cyclop on 2006-09-18
Google apps are written in Python.:cool:

---

### Post by droppedd on 2006-09-18
erm - well, that's a bit of a generalization. A lot of them are actually written in Java (see: Google web toolkit), but they do use a fair amount of python. 

Google actually hired Guido van Rossum, creator and Benevolent Dictator for Life of Python, to work for them; 50% of his time on Google projects and 50% on Python itself.

---

### Post by X.Cyclop on 2006-09-18
Well. [Why Python?]("http://www.linuxjournal.com/article/3882") :wink:

---

### Post by 3rdalbum on 2006-09-19
I do some web development, though it's not my primary job.

Python is a much nicer language to work with than PHP. PHP does have some great web-related functions built-in, but you can easily get equivilants in the many web frameworks for Python.

Plus, when you know Python, you'll be able to write programs to run on your own computer. You'll be able to write them quickly, debug them quickly, and re-read them easily.

---

### Post by Burgresso on 2006-09-20
Thanks a lot for the responses.

droppedd, I appreciate your input. I use PHP but getting *very* annoyed with its speghetti-like syntax. Sure, you can code it any way you want, but it is too easy code poorly. This makes for cr*ppy code. That's why I'm curious about Python, and I apprecaite your input.

I'll check it out.

---

