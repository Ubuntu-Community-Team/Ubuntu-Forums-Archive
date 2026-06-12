---
title: "Newbie requests advice on programming language"
date: 2006-06-12
forum: Programming Talk
---

### Post by ketsugi on 2006-06-12
Hi, I'm relatively new to the Linux world (I've played with Redhat 7/8/9 and Ubuntu Warty/Hoary/Breezy before) but I only really started using it regularly as a desktop environment since Dapper Flight 6.

Now I'd like to get started on developing applications for Gnome, and I'm not sure where to begin. I have some experience with C (mostly writing command-line applications for a Programming in Unix course) and Java, and am most familiar with PHP (which is totally unsuitable for desktop applications as I'm well aware).

I'm wondering if I should bother dabbling with Ruby-Gtk, or if you guys would recommend I dive straight into writing in C, with the standard Gtk libraries.

Are there any friendly guides to getting started with Gtk programming in C?

Also, any thoughts about Mono?

---

### Post by ltmon on 2006-06-12
I love Ruby as a language, but am not sure if the Ruby-GTK bindings are quite up to scratch.

I would recommend PyGnome before diving into native applications.  It's really easy, mature and there are plenty of tutorials and resources on the web.

---

### Post by ketsugi on 2006-06-12
Hmm, I was hoping not to have to learn *another* new language, but then I suppose Python (and Perl, eventually) would be good languages to at least have some basic familiarity with.

Thanks, I'll go look into it.

---

### Post by Engnome on 2006-06-12
[QUOTE=ketsugi] and am most familiar with PHP (which is totally unsuitable for desktop applications as I'm well aware).
[/QUOTE]

I started out with PHP but wanted to do desktop apps, so when i stumbled upon Perl I really liked it. (its almost the same as PHP, I even copy pasted some previous PHP code into my perl scripts) Making a little game atm. Using glade and libglade to get the gui. If you are interested in trying it post back and I'll post some good resources I've found.

---

### Post by ketsugi on 2006-06-13
I'm currently looking into Python, which seems like an interesting language I'll probably have fun with, and which is nearly as ubiquitous on *nix systems as Perl is.

I'll probably dabble with Perl eventually, but I don't want to try and learn too many new scripting languages at one go.

---

### Post by QMario on 2006-06-14
[QUOTE=ketsugi]I'm currently looking into Python, which seems like an interesting language I'll probably have fun with, and which is nearly as ubiquitous on *nix systems as Perl is.

I'll probably dabble with Perl eventually, but I don't want to try and learn too many new scripting languages at one go.[/QUOTE]

You can try to learn C++, since coming from C, it shouldn't be too difficult for you to learn. I personally thought that C++ would be difficult to learn, but it is quite fun and easy only if you practice your coding skills. :KS

---

### Post by LordHunter317 on 2006-06-14
[QUOTE=QMario]You can try to learn C++, since coming from C, it shouldn't be too difficult for you to learn. I personally thought that C++ would be difficult to learn, but it is quite fun and easy only if you practice your coding skills. :KS[/QUOTE]Except that C and C++ are totally different languages with totally different best practices and behaviors.  It won't be any easy transition.  If anything, it'll make things harder.

---

### Post by ketsugi on 2006-06-14
[QUOTE=LordHunter317]Except that C and C++ are totally different languages with totally different best practices and behaviors.  It won't be any easy transition.  If anything, it'll make things harder.[/QUOTE]

But if I understand it correctly, C++ should be in many ways similar to Java, yes? I'm familiar with Java because my idiotic university decided to teach Java as an introductory language instead of C, and thereafter forced me into developing J2EE applications.

If C++ is similar enough to Java in terms of syntax, then perhaps that would be a good alternative.

In the meantime I'm hammering something out with PyGnome and Glade...

---

### Post by LordHunter317 on 2006-06-14
[QUOTE=ketsugi]But if I understand it correctly, C++ should be in many ways similar to Java, yes?[/quote]Not especially, no.  Again, it's largely a best practices thing.  C++ also has many advanced language features Java does not have.  

> If C++ is similar enough to Java in terms of syntax, then perhaps that would be a good alternative.Syntax similarities is the least important reason to switch.  In fact, it's a total non-reason.

---

### Post by nythrix on 2006-06-15
LordHunter17 is right. Don't let their syntaxes fool you. C++ may be everything but it is definitely NOT like java (or C#). Java is a mid-range AUDI or BMW. Comfortable, easy to drive and full of electronics that keep you on-road. C++ is an old style Land Rover or Jeep. You can drive through a corn field but your *** will take some nasty kicks if you're not careful.
Generally speaking, a comfortable language is more popular than a powerful but "wild" language. That's why nobody uses assembler nowadays (that would be a motocross bike with a ferrari engine :D).

My suggestion: stick with Java or C#.

---

### Post by bieber on 2006-06-15
Heh.  I love assembly.  If not for the portability issue, I'd still use it.

I like C++.  You can use it pretty much like C when you don't need OO, but when you must have it, it's there.

---

### Post by maddog39 on 2006-12-23
LoL. Havn't any of you guys heard of PHP-GTK. >??

[http://gtk.php.net/](http://gtk.php.net/)    Enjoy! :)

I am a 2 years active PHP developer and when I found PHP-GTK I was exstatic, had many ideas. Going to start a PHP-IDE in it soon (every IDE in linux in my opinion sucks). PHP-GTK 2 using GTK+2.0 requires PHP 5, luckily for me, my PHP book focused on PHP5, its not that much different and is 98% backwards compatible with PHP4 so you shouldn't have any problems.

Although if only Ubuntu or any other distro came with the PHP interpreter by default. :/ Well before your compile PHP-GTK:
```
sudo apt-get install php5-common php5-cli php5-sqlite libgtk2.0-dev
```And here is a text file with the default PHP info in which you can find paths to php.ini etc.
[http://madbb.ath.cx/~maddog39/phpinfo.txt]("http://madbb.ath.cx/%7Emaddog39/phpinfo.txt")

All it is, is the result of:
php -i > phpinfo.txt     or
php -r "phpinfo();" > phpinfo.txt

Then just compile the PHP-GTK2.0.0 source from tarball as usual:
./configure && make && sudo make install

---

### Post by Wybiral on 2006-12-23
This post is like 6 month old... But, since it was brought up: ASM, C, C++, and Python are all great languages to learn.

ASM when I want to write small, fast routines, you can even do low-level graphics with it using an external lib (libsvga for example).

C for similar reasons that I use ASM, except C has the added bonus of being 1000X times faster and easier to write in. Naturally, it doesn't give you the same amount of freedom ASM gives you, but it's still rather nice.

C++ when I need to tackle larger projects. C++ is simple brilliant for dealing with difficult forms of data (especially 3d graphics) it also has the advantage that C has with being fast, and very very easy to write it.

Python... Python is a real work of art. Surprisingly fast for a scripting language. Extendable with C and C++ (which allows for two way communication between the two when embedded, and the ability to write python modules in C/C++ when compiled to a shared object). Python has similar features for handling complex data like C++ has, as well as a host of odd routines that really make programming in it simple. But, definitely the best part is when you find something you need in python (which is rare) like a binding to a lib that it doesn't support... You can just write your own binding using C/C++. It is also really easy to convert code from python into C++ which is very nice.

---

### Post by n3gbz on 2006-12-23
Python (or variation) is quickly becoming my favorite.  wxPython for a GUI is highly recommended by many experts.  It is cross-platform and has an easy learning curve.  

A fairly new website, [ShowMeDo.com]("http://showmedo.com/") hosts a set of five tutorial videos useful to those just starting with wxPython (among about 50 Python tutorials).

---

