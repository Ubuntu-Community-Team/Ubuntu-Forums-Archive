---
title: "Programming in C"
date: 2012-01-08
forum: Programming Talk
---

### Post by qkzoo on 2012-01-08
Hi.

I don't want to start a religious war, because that's what seems to happen whenever somebody asks for recommendations or direction when it comes to C programming, at least in other forums I've browsed.  So, I'll try to be as specific as I can:

I'm reading "ANSI C Programming Language, 2nd Ed." by Brian W Kernighan and Dennis M. Ritchie.  This book has laid out a pretty decent framework for me to start developing really simple console applications (I'm still reading).  My question is in how to transition from console applications to windowed applications.  I don't really want to learn another language at this point, I'm still struggling with C, so I'd like to stick with it's constructs and what I've learned so far.  Many recommendations I've seen on other websites suggest learning C++ or C# which at this point, I really am not ready, and not interested. 

I have done some object oriented programming in Pascal in the past, for the Palm OS, and some VB stuff way back in the day, but that's about it.  I understand X11 is the window manager for Ubuntu?  (I'm using Lubuntu right now).  So how would I make a natural progression from learning the basic constructs of C to making simple "Hello World" window apps?  

Thanks for any direction here!

Q

---

### Post by pbrane on 2012-01-08
GUI programming in GNU/Linux, e.g. Ubuntu, does not require another programming language. I have written GNOME/GTK apps in C. I prefer C++, but C works just fine. You should research the toolkits for the desktop you plan to write apps for. Lubuntu (LXDE desktop) appears to use GTK+.

You can find tutorials on the web for GTK.
Here is one link: [http://www.gtk.org/]("http://www.gtk.org/documentation.php")

There are tutorials on this page.

---

### Post by qkzoo on 2012-01-08
Thank you, I will check this out :)

---

### Post by Petrolea on 2012-01-08
I'd say GTK too if you're using C, it's not hard to implement it in your code and there are many tutorials and good documentation.

---

### Post by Simian Man on 2012-01-08
There are very few areas where C is the best programming language for the job, and GUI applications is certainly not one of them.  If you are using C for some other purpose, and want to write small GUI programs in the language you know, use GTK+.  Under no circumstances would I ever use C for large GUI applications.

---

### Post by dazman19 on 2012-01-08
Yeh stick to what you are doing. Once you understand C well, you will move onto C++, it took me about 6-12 months to learn C to a level where I decided I need better toolkits, and OOP so I went to Java and C++.

I learn to program graphically in Java, although C was my first programming language. 

Funnily enough i write about 90 percent of my code now days in PHP. (most of the rest is java or C), but that is because i do web applications for my job.

---

### Post by muteXe on 2012-01-09
Do not presume everyone who learns C will move to C++.

---

### Post by Simian Man on 2012-01-09
> **muteXe said:**
> Do not presume everyone who learns C will move to C++.

The concept of "moving to" a programming language is faulty.  Good programmers will know many programming languages and consider their options for each project.  A programmer who sticks with one language for everything is an amateur at best.

---

### Post by MG&amp;TL on 2012-01-09
> **muteXe said:**
> Do not presume everyone who learns C will move to C++.

Thank you, I started on C++. C is now very weird, though, and I kinda wish I had started with C.

---

### Post by Bachstelze on 2012-01-09
> **MG&TL said:**
> Thank you, I started on C++. C is now very weird, though, and I kinda wish I had started with C.

Please don't take this the wrong way, but why are you learning C at all? From your previous posts, it doesn't seem you doo much system programming or other low-level stuff, so if you think C is weird, why bother with it? Personally, C is the only language I consider myself proficient in, and it's enough for me; when I learn new languages (Haskell, Ada...), it's purely for fun so if I think the language is weird, I don't bother with it. Unless you want to get a programming job?

---

### Post by MG&amp;TL on 2012-01-09
> **Bachstelze said:**
> Please don't take this the wrong way, but why are you learning C at all? From your previous posts, it doesn't seem you doo much system programming or other low-level stuff, so if you think C is weird, why bother with it? Personally, C is the only language I consider myself proficient in, and it's enough for me; when I learn new languages (Haskell, Ada...), it's purely for fun so if I think the language is weird, I don't bother with it. Unless you want to get a programming job?

Yeah; and I've done high-level; now I want to do low-level. Sometimes I wish it was the other way around, as some comprehension would be good of the stuff I'm doing.

Also a lot of stuff is written in C; especially the API for several things.

Maybe I should rephrase 'weird'-maybe 'new' is more accurate. Also, I'm a 15-year old programmer, so my tastes change pretty quick. :P Sorry, I must be annoying you experienced people, prodding around here.

---

### Post by Arndt on 2012-01-09
> **Simian Man said:**
> The concept of "moving to" a programming language is faulty.  Good programmers will know many programming languages and consider their options for each project.  A programmer who sticks with one language for everything is an amateur at best.

There are some languages I would rather move from, than to.

---

### Post by karlson on 2012-01-09
Ok.  We've got a virus bot.

---

