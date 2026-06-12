---
title: "[HELP!]  Howto make programs??"
date: 2009-07-15
forum: Programming Talk
---

### Post by Lollating on 2009-07-15
Hi,

How can I make programs with Ubuntu
I can Pogram in windows very good
But I want to program In Ubuntu aswell


PLEASE HELP!


greets Lollating,

---

### Post by TeoBigusGeekus on 2009-07-15
Which language(s) are you interested in?

---

### Post by Lollating on 2009-07-15
I heard of g++
I think thats good/normal :s
what do you think about it?

---

### Post by RedRat on 2009-07-15
This is an interesting question since I am interested also in doing this. Are there programs for C++, C, or C# that are similar to those for Windows programing environment that use a graphical interface? I have played around in the Windows world a couple of years ago and wouldn't mind trying it in Ubuntu. 

I have seen a couple of comments on the compiler to use, either c++ or g++, which should one use.

---

### Post by cholericfun on 2009-07-15
what do you program in under windows (e.g. VC++) ?
if thats the case, g++ is practically the same.

you can also download intels c++ which is free as a single user licence.

as far as i know there are no gui's for any progaming in linux (even if-who cares...)
as for whether c++ or g++ or whatever is "better", just try it out, for the most part (or all?) the code is the same,
so just run either compiler over it and see whats faster.

---

### Post by TeoBigusGeekus on 2009-07-15
So you are interested in C++.
```
sudo apt-get install build-essential
```
For starters.
Then 
```
sudo apt-get install geany
```
for a good programming IDE (Geany uses g++).

If you prefer the command line
[http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html]("http://www.ubuntugeek.com/how-to-install-c-and-c-compilers-in-ubuntu-and-testing-your-first-c-and-c-program.html")

---

### Post by lovinglinux on 2009-07-15
[Programming Tools and References](http://ubuntuforums.org/showthread.php?t=1006662)
[Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming](http://ubuntuforums.org/showthread.php?t=1006666)

Forums:

[Development & Programming](http://ubuntuforums.org/forumdisplay.php?f=310)
[list][*] [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39)
[*] [Packaging and Compiling Programs](http://ubuntuforums.org/forumdisplay.php?f=44)[/list]

---

### Post by RedRat on 2009-07-15
> **cholericfun said:**
> what do you program in under windows (e.g. VC++) ?
if thats the case, g++ is practically the same.

you can also download intels c++ which is free as a single user licence.

as far as i know there are no gui's for any progaming in linux (even if-who cares...)
as for whether c++ or g++ or whatever is "better", just try it out, for the most part (or all?) the code is the same,
so just run either compiler over it and see whats faster.

I played around with Visual C++ and it had some things that made creating the individual windows quite easy, building them from scratch was a bit of a pain.

---

### Post by Lollating on 2009-07-15
Oh wow [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094")

thats EXACTLY what i was searching for!
ty!!!

---

### Post by credobyte on 2009-07-15
> **Lollating said:**
> I heard of g++
I think thats good/normal :s
what do you think about it?

Are you really a programmer ? g++ isn't a programming language - it's a compiler ( more over, available on almost all platforms ).
[https://help.ubuntu.com/8.04/programming/C/index.html](https://help.ubuntu.com/8.04/programming/C/index.html) - happy reading ;)

---

### Post by Mornedhel on 2009-07-15
> **RedRat said:**
> I played around with Visual C++ and it had some things that made creating the individual windows quite easy, building them from scratch was a bit of a pain.

If you are running Gnome or any other GTK+ based environment, I would recommend Glade to build your windows, although if you're trying to learn programming you should stay away from GUIs for now (I mean away from GUI building, not IDEs). It's pretty neat since you can build GTK+ windows and then use the resulting interface from any language that supports libglade.

For starters, though, just program command-line applications, there are less things to track and you can focus on the language (also seriously, if you're learning, you don't need to include GTK+ in your Hello World program).

> as far as i know there are no gui's for any progaming in linux (even if-who cares...)

Uh whuh what ? Anjuta, Emacs, Geany (already mentioned)... there are quite a lot. Although you *can* develop without an IDE, using just an editor, and command-line version control/documentation generation/building process/gdb/etc., most Linux IDEs do make some things simpler.

---

### Post by c0mput3r_n3rD on 2009-07-15
> **Lollating said:**
> I heard of g++
I think thats good/normal :s
what do you think about it?

Just a side note; most Windows compilers (Dev c++ i'm sure about) actually use the g++ compiler to compile C/C++ code :)

---

### Post by JordyD on 2009-07-15
> **lovinglinux said:**
> [Programming Tools and References](http://ubuntuforums.org/showthread.php?t=1006662)
[Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming](http://ubuntuforums.org/showthread.php?t=1006666)

Forums:

[Development & Programming](http://ubuntuforums.org/forumdisplay.php?f=310)
[list][*] [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39)
[*] [Packaging and Compiling Programs](http://ubuntuforums.org/forumdisplay.php?f=44)[/list]

^This should have been a thread-killer. We do have stickies for this, to avoid this question being asked so often.

---

### Post by Lollating on 2009-07-16
Im posting this in Absolute beginner talk,
dont expect I know everything of Ubuntu/Linux :s

---

### Post by jespdj on 2009-07-16
> **Lollating said:**
> Lollating: Ubunt user since Friday 11 Juli 2009
Funny. 11 July 2009 was a Saturday in the world that I live in. Was it a Friday where you live? ;)

---

