---
title: "I want to start developing linux Apps, What Language?"
date: 2005-09-17
forum: Programming Talk
---

### Post by zootreeves on 2005-09-17
I already have a good knowledge of PHP & MySQL and some Perl, but I have only ever made web based apps before.

I would like to have a go at writing GTK apps, but I don't really know what language to start with. What are the majority of ubuntu apps made with?

I had a quick go at python, but i don't really like the way everything has to be indented correctly (unless their is a good python editor or something that helps with that, I just used gedit).

mono seems like a nice language and easy to compile with mcs, but does it have the full support of the linux community (I heard that banshee would not be the default ubuntu music player becuase it needs mono)

I also looked into java, php-gtk and C or C++... Any info would be greatly appreciated

---

### Post by geekchic9 on 2005-09-17
Hi,

Python has an editor called IDLE that helps with correct indentation, but here's a hint: Don't mix up tabs with spaces; that is: If you use spaces to indent, don't mix it up with tabs and vice versa. Look IDLE up with synaptic. Python works with Tkinter for a gui to create IDLE, IIRC.

 IANAUD (ubuntu developer), but I know that GNOME apps use GTK+, which, according to [gtk.org,](http://www.gtk.org/) 

"GTK+ has been designed from the ground up to support a range of languages, not only C/C++. Using GTK+ from languages such as Perl and Python (especially in combination with the Glade GUI builder) provides an effective method of rapid application development."

Hope that helps a little,

Morgan

---

### Post by Mike Buksas on 2005-09-17
A good editor is a must with python because of the indenting. A good editor will do the indenting for you, colorize syntax to help you spot errors and even run the intrepeter for you. I use emacs with python-mode. IDLE is supposed to be good also. There are other threads in the forums about this also, for more advice.

Python is the preferred language for applicaitons which are part of Ubuntu, so you may want to give it another go for that reason.

Ultimately, it comes down to finding one that you like and matches what you want to do and your style. Also, you'll eventually learn more than one, so don't worry about picking the "wrong" one now. For rapid development and prototyping, Python is great. If you like working at a lower level of abstraction, or with a greater degree of enforced correctness in the code then C or C++ may be more your thing. 

My advice is to pick a project the motivates you and try different languages at it until one clicks with you and or the project you're working on. Good luck.

---

### Post by mostwanted on 2005-09-19
How about C# on Mono? That's what I'm using.

---

### Post by zootreeves on 2005-09-19
Ok thanks for the advice, I have decided I will have a go with python first, once (if ever) i grasp that i will move onto C# & mono but at the moment I think it's out of my league.

I was wondering whether anyone could help me out with my first attempt. I want to make a little gtk app with two buttons, a "1"  & a "2". When you press the 1 button it will print 1 in the terminal and if you press the 2 button after it will print 3, press it again and it will print 5 etc...

I have attached the python file, it doesn't work though. The script seems to forget the number already pressed when you press another button...

---

### Post by UbuWu on 2005-10-01
I don't have a lot of experience, but I think it is because the Numbertotal variable only exist in Helloworld2.callback, so everytime the function ends, its value is lost. I think you should read some more on variable scopes.

---

### Post by remin8 on 2005-10-01
I would go with C++. It might be a little tough to begin with but you will be able to use C++ for just about anything. It is also a very popular language that you will be able to get a lot of help with.

---

### Post by Kyral on 2005-10-01
Just about anything can be done in C++. But watch out, 'cause people may come down on you if you can write the same thing easier in another language. (Biggest criticism of one of my projects is "WHY THE HELL DID YOU WRITE IT IN C++!?")

---

### Post by dcraven on 2005-10-01
[QUOTE=zootreeves]I have attached the python file, it doesn't work though. The script seems to forget the number already pressed when you press another button...[/QUOTE]
There is a working version of your program [here](http://arker.homelinux.org/~dcraven/first.py). Basically all I did was make Numbertotal an instance variable of the HelloWorld2 class. I also wrapped "data" in the int() function call to turn the string into an integer before performing the addition.
Aside from that, I think it worked fine.
Cheers,
~djc

---

