---
title: "What should I try ?"
date: 2007-10-02
forum: Programming Talk
---

### Post by Dr Small on 2007-10-02
Ok. The only programming language I have ever tried was Php, but I sorta ran out of things to make and try, so I eventually got bored with it.

Now, I have no idea about computer programming languages, so I am hoping someone will suggest to me as to which one would be best, for what I want to try to do, after I attempt to learn the language.

I want to build some application in the Gnome environment, that basically looks like the screenshot attached. What language would you recommend that I could use to make it ?

By the way, that screenshot, is a picture I made in the Gimp :p
Thanks!
Dr Small

---

### Post by CptPicard on 2007-10-02
Read the stickies.

Use Python.

---

### Post by MicahCarrick on 2007-10-02
For developing GNOME applications you'll probably want to use the GTK+ libraries. GTK+ is just the libraries for the graphic interface, and is the library that GNOME is based on. Which programming language you use to work with GTK+ is up to you.

A lot of people will suggest Python as it takes care of a lot of the work for you. GTK+ is written in C, however, there are language "bindings" to just about any other language you can think of--including PHP! 

Python and GTK+ is known as PyGTK, PHP and GTK+ is known as PHP-GTK. Google either of them and you'll find plenty of articles and tutorials.

If you feel like giving C a try, you could try reading  [Tutorial: Simple Gnome Application Using libglade and C/GTK+]("http://www.micahcarrick.com/03-02-2006/gnome-programming-tutorial.html")

---

### Post by pmasiar on 2007-10-02
Learn Python first (command-line, without GUI). Then wxPython, then C + wxWidgets. 

See sticky and wiki in my sig for links.

---

### Post by slavik on 2007-10-02
I am not going to say "use Python" or "use C" or even "use Perl" ... what I will say is "use anything that has libglade and gtk bindings) which is C, C++, Perl, Python, Ruby, and more. :)

---

### Post by pmasiar on 2007-10-03
Well, for a person with little programming experience, and that in PHP, suggesting C++ (among others) or even C is NOT a good advice. 

And you could suggest Perl, we know you prefer Perl to anythying else :-) - but again, we all discussed many times here that Perl would be more confusing to a beginner that Python is.

Ruby is almost as good as Python, only little more perlish, and with less libraries... so after eliminating all less-then-optimal choices, Python is the one remaining. :-)

---

