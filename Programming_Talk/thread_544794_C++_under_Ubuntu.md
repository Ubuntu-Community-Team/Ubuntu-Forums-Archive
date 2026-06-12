---
title: "C++ under Ubuntu?"
date: 2007-09-06
forum: Programming Talk
---

### Post by lifeinoleg on 2007-09-06
Hi,

I just started a beginners C++ class. Problem is, I have Fiesty installed on my laptop, but we're using Visual Studio 2005 in class.

I'd like to practice/do assignments at home, but I have no idea how to go about this since VS is not a linux program.

Any suggestions on what I can use to write/compile C++ under Ubuntu?

Thanks.

---

### Post by linux noooob on 2007-09-06
go to add/remove tab and search wine it is an emulator for windows that lets you run windows apps without the ram consumption. also i am trying to self teach my self c++ and i use kdevelop it is awesome it is very good with showing errors and other things but it does suck at compiling

---

### Post by Buffalo Soldier on 2007-09-06
installing the **build-essential** package gives you all the basic tools for programming.
```
sudo apt-get install build-essential
```

And you also might be intereted in [Anjuta]("http://anjuta.sourceforge.net/screen-shots").


[https://help.ubuntu.com/community/Programming](https://help.ubuntu.com/community/Programming)

---

### Post by ryno519 on 2007-09-06
> **lifeinoleg said:**
> Hi,

I just started a beginners C++ class. Problem is, I have Fiesty installed on my laptop, but we're using Visual Studio 2005 in class.

I'd like to practice/do assignments at home, but I have no idea how to go about this since VS is not a linux program.

Any suggestions on what I can use to write/compile C++ under Ubuntu?

Thanks.

Either get g++ and KDevelop or Anjuta or you could install a virtual machine with XP on it and do the development that way. All really depends on what your teacher wants. If he wants you to hand in Visual Studio 2005 projects then you will need to have Windows and Visual Studio 2005 installed. If he wants you to hand in binary files you will also need Windows. If he just wants the raw source code then you can do it in Ubuntu, but when I was in college that wasn't the case.

I'd ask your teacher if it's okay to do your assignments in GNU/Linux and see what he says.

---

### Post by rharriso on 2007-09-07
I recommend an almost bare bones approach. Use g++ compiler, but use one of the GUI editors for scripting, it really helps organize your thoughts when you're beginning, as you continue, you'll eventually want to go with simpler text editors like nano or Pico. I like using my mouse though.

---

### Post by gnusci on 2007-09-07
Because you are new I will recommend you to learn programming using a simple shell. Using shell with give you more knowledge abut the Linux system and the compiling process itself.

Anyway if you want to use and IDE I also recommend you to try KDevelop:

[http://www.kdevelop.org/](http://www.kdevelop.org/)

---

### Post by daxumaming on 2007-09-11
Nah, Wine can't handle Visual Studio, I already tried. I also tried installing an older version, Visual C++ 6, but it just won't install.
But here's my thoughts..... You do have a problem.

Source codes from Visual Studio is very much incompatible with an IDE used in Linux. It'll be fine if you're doing command-line programs, but for everything else... I don't think you're instructor would accept a source code unfamiliar with him/her. You do, however, need to give him/her a heads up that you'll be practicing at home using Ubuntu, this way, he wouldn't be surprised when you turn over your work.

The method of teaching in VS is also incompatible with your IDE. You'll only get confused.

KDevelop is really good, but it's a pain to setup. You need a few more packages that isn't automatically installed when you apt-get KDevelop. Check this site out: [http://startingcpp.blogspot.com/2007/06/kdevelop-and-problems-on-kubuntu.html](http://startingcpp.blogspot.com/2007/06/kdevelop-and-problems-on-kubuntu.html)

If you have Ubuntu or Xubuntu, then I suggest you use Anjuta. It's really great. However, it does have problems with Feisty - even the maintainer complained about it. If you want to use Anjuta, use the unofficial repository. See: [http://anjuta.org/downloads](http://anjuta.org/downloads)

And, if you're doing simple stuff, then a simple text editor would do it's job. But if you insist on using an IDE, check out Geany. It's fast and very much reliable.

Lastly, if you're really intent on going through with your Visual Studio class, then I suggest you switch back to using Windows and VS. There's really no way you could understand the lessons when you're working on Ubuntu. Trust me, I've tried that too. I ended up not learning a thing. Besides, Visual Studio lessons mostly focus on teaching you the tool/s, not C++. One last option I can recommend is to drop that class and find one that offers programming in Open Source or Google Learn C++ and just teach yourself the language. To me, teaching myself is the best option.

---

### Post by Shortey on 2007-09-11
Since U only started coding, I think that Geany will do the job. You can do object oriented programming, but not visual. For that purpouse use mono, it supports .net 1.1 but it doesn't have an IDE yet. 

I think Geany is the best choice for begginers, KDevelop is more complicated.
Or install Eclipse and the C++ plugin. But that will do the same job as Geany.

---

### Post by JimmyBEng on 2007-09-12
If you are getting started in C++, coding with gedit and a command line compiler shouldn't be bad (see Buffalo Soldier's post above).  And at a beginner level you probably won't have to do anything platform-specific, so if code compiles using gcc, it should compile in visual studio.  Just make sure it runs fine in visual studio before you hand it in (just in case).  Mentioning it to teacher is also a good idea, they may have some suggestions.

---

### Post by vl_ado on 2007-09-12
> **lifeinoleg said:**
> Hi,

I just started a beginners C++ class. Problem is, I have Fiesty installed on my laptop, but we're using Visual Studio 2005 in class.

I'd like to practice/do assignments at home, but I have no idea how to go about this since VS is not a linux program.

Any suggestions on what I can use to write/compile C++ under Ubuntu?

Thanks.

Hi there try using Eclipse because it runs under linux as well and it's perfect for programing with .net also [http://www.eclipse.org/](http://www.eclipse.org/)

---

### Post by glok_twen on 2007-09-12
as an aside, the single best book i ever read in learning to use c++ was tom swan's book on gnu c++

[http://www.amazon.com/Swans-Linux-Professional-Dev-Guide/dp/0789721538](http://www.amazon.com/Swans-Linux-Professional-Dev-Guide/dp/0789721538)

of course there are a billion books on c++. what i love about this one is it shows you all the stuff you need to create c++ from the command line. plus it is by far the clearest read in teaching you what c++ really is at its essence, all from square 1.

with this book's approach you can get by using vim, g++, gdb and make. eventually valgrind may be helpful as well.

---

