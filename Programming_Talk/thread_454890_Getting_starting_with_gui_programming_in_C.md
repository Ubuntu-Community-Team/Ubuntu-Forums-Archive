---
title: "Getting starting with gui programming in C"
date: 2007-05-26
forum: Programming Talk
---

### Post by aoper on 2007-05-26
I have done a lot of simple console programs in c, and I found it pretty easy to learn. I have covered all the basics, I took a course in C programming last semester and did well. I have started looking at some GUI libraries and they seem pretty intimidating. What is the easiest way to start GUI programming in C?

---

### Post by WW on 2007-05-26
Just dive in.  Don't overanalyze the choice of which GUI library to use--pick one and start using it.  GTK+ is fine; you can install it with the command
```

sudo apt-get install    libgtk2.0-dev

```
Then go to the [the tutorial]("http://www.gtk.org/tutorial/") and get to work.

---

### Post by theDentist on 2007-05-26
I assume you want to program Linux, then the post before me is the best advice.  :)  For Windows get a good book and learn to program the API with an editor and compiler like the now free Borland V5.5.  This should be done only as a learning exercise as programming a GUI like that in windows is very time consuming and there are easier ways to do it, but it is a great way to learn how it all works and gives you good background knowledge that I often have been thankful for. By the way, the only header to include when programming like this is windows.h.  In Linux the situation is a lot clearer, as explained earlier.

---

### Post by aoper on 2007-05-26
I started the GTK tutorial, and it's making sense. It seems like there is a lot to learn, but it is not that difficult.

---

### Post by rekahsoft on 2007-05-26
> **aoper said:**
> I started the GTK tutorial, and it's making sense. It seems like there is a lot to learn, but it is not that difficult.

yes there is tons to learn...i have been working on learning gtkmm (the gtk+ C++ wrapper) for some time now...although it has been getting harder as the year comes to a close with exams and summatives)

---

### Post by Nirose on 2010-09-25
The tutorial link is down. is there any other resource i should look into.

---

### Post by worseisworser on 2010-09-25
The first hit googling "gtk tutorial" leads to the same tutorial, Nirose:
  [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

---

### Post by BenB1 on 2012-10-24
> **aoper said:**
> I have done a lot of simple console programs in c, and I found it pretty easy to learn. I have covered all the basics, I took a course in C programming last semester and did well. I have started looking at some GUI libraries and they seem pretty intimidating. What is the easiest way to start GUI programming in C?

Thank you for asking this question. It is nice to access the answer/s, once a question has been asked. 

I've been working in Debian, doing lots of bash scripts porting them to zenity. My wife's brother-in-law whom is studying to be a system administrator suggested I upgrade to "real" programming.

To that end I'm studying Perl, C and sometimes guiltily Lisp. Although I am veering away from Emacs Lisp for personal reason/s. Again, thanks for asking the question.:)

---

### Post by satsujinka on 2012-10-24
> **BenB1 said:**
> Thank you for asking this question. It is nice to access the answer/s, once a question has been asked. 

I've been working in Debian, doing lots of bash scripts porting them to zenity. My wife's brother-in-law whom is studying to be a system administrator suggested I upgrade to "real" programming.

To that end I'm studying Perl, C and sometimes guiltily Lisp. Although I am veering away from Emacs Lisp for personal reason/s. Again, thanks for asking the question.:)

There's no need to feel guilty about studying Lisp. It's a great family of languages.

---

### Post by Odexios on 2012-10-25
I've been trying to get started with GUI programming in C for a long time, but I'm always stopping before getting to a point where I can be even just a little productive.

I've been trying to get the hang of GTK, and to do that I've started many times to study The Official GNOME 2 Developer's Guide. I'm always stopping shortly after the gobject chapters; I guess it's just too much information before even starting to be able to do something for me.

Just a rant post; I know I could start with a tutorial which could get me on the run more quickly, but any time I try that I feel I'm cutting corners because I'm not able to do something in a certain way, and I suddenly lose interest.

---

