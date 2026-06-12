---
title: "Which language would fit my needs the best?"
date: 2010-07-25
forum: Programming Talk
---

### Post by Emascu on 2010-07-25
Hello.

I'm a PHP programmer and I'd like to learn a programming language with which I can write actual programs. The idea is to actually install the application on your system and run it like any other application. Eventually, I want to start writing programs for children.
I myself am a linux user, but I will make applications for mainly windows users, but I would like to develop it under ubuntu. So a cross platform language would be the best for as much that is possible (I'd rather just write in one language and export an .exe for windows users and .deb for ubuntu, but something tells me it's not going to be that easy :D ). I'd also rather avoid 'plugin' kind of things as java, because the clients first have to install additional software.

I'm coming from from PHP and I am familiar with the OOP mindset, so I guess I'll adapt quickly to languages based on OOP. But there's a lot of languages to pick from, I don't know the details of all and I can only guess which one would fit my needs the best. So I'm wondering which language do you recommend me?

---

### Post by James78 on 2010-07-25
C++ is a very mature language and has cross compilers for everything. Specifically, you can write your application and cross compile it with mingw32 or mingw64.

Notice however that if I were to write applications for Windows, I'd write them on Windows, because Microsoft has an uncanny way of making sure that only their header files are included on their platform, and you have access to so many more Windows API calls than you can do with Linux because of how that's set up, it's sad but true. Regardless of that you can still very easily do it! QT4 is a cross platform, and you can use that to design your UI, and just include the proper .dll with the program. That's what VLC does, and it looks perfectly good doesn't it!

---

### Post by shadylookin on 2010-07-25
If you rule out languages that require runtime enviroments/interpreters then you're left with compiled languages. Though there's no shortage of options c++ is probably the most popular one.

---

### Post by MattBD on 2010-07-25
> **Emascu said:**
> The idea is to actually install the application on your system and run it like any other application.

You may be able to do that with PHP. I know for a fact that you can definitely do it in Python, even though like PHP that's a scripting language - you can just use the py2exe module to create a Windows executable.

---

### Post by nvteighen on 2010-07-25
If those are the conditions... then C++ or C seem the best options.

---

### Post by Emascu on 2010-07-25
C++ sounds very nice indeed. I've looked around on the net for a bit and everything seems to be visual studio orientated. I do am hoping to do it all on ubuntu though.
> **MattBD said:**
> You may be able to do that with PHP. I know for a  fact that you can definitely do it in Python, even though like PHP  that's a scripting language - you can just use the py2exe module to  create a Windows executable.
I don't think the strength of PHP is in writing apps, even though it may be possible, I rather have a language designed for it.

Python also sounds like a nice language to me. I just looked at some example codes of python and C++ and python makes a lot of sense, while C++ looks very different then php does. It also looks less microsoft orientated.

What are the downsides of python? Why would I pick C++ over python?


Also on an other note, I am curious about other applications I use on regular basis. In which language are most applications built? If I open, lets say Skype or Pidgin.. what language is running on the other end?

---

### Post by MattBD on 2010-07-25
> **Emascu said:**
> What are the downsides of python? Why would I pick C++ over python?
Python is a very readable language, and it's pretty easy to pick up. I've also found it to be more fun to use than virtually any other programming language I've ever tried. It also has a very good interactive mode so you can try out code in that mode to check something works the way you think it does, which is very useful indeed! Also, it's likely that with similar levels of C++ and Python proficiency you'll be able to create an application quicker in Python than in C++.

The only major downside I can think of is that Python, being interpreted, is generally slower. However, that should be less of an issue if you use py2exe, since I believe that it compiles Python applications to bytecode.

---

### Post by MattBD on 2010-07-25
> **Emascu said:**
> Also on an other note, I am curious about other applications I use on regular basis. In which language are most applications built? If I open, lets say Skype or Pidgin.. what language is running on the other end?

Most applications on Linux tend to be written in either C or C++. I think the GTK+ toolkit used to create the GNOME desktop uses C, while the Qt toolkit that KDE uses opts for C++, but there are also bindings available for other languages, including scripting languages.

---

### Post by Emascu on 2010-07-25
> **MattBD said:**
> Python is a very readable language, and it's pretty easy to pick up. I've also found it to be more fun to use than virtually any other programming language I've ever tried. It also has a very good interactive mode so you can try out code in that mode to check something works the way you think it does, which is very useful indeed! Also, it's likely that with similar levels of C++ and Python proficiency you'll be able to create an application quicker in Python than in C++.

The only major downside I can think of is that Python, being interpreted, is generally slower. However, that should be less of an issue if you use py2exe, since I believe that it compiles Python applications to bytecode.
It sounds like a language with a lot of fun and the easy learning-curve makes it a very attractive language.

But how does the install part work? I write the code on ubuntu. Do I need to export (to a .exe?) and I can pass it around to my friends on a windows computer so they can easily install it and use it?

---

### Post by MattBD on 2010-07-25
> **Emascu said:**
> But how does the install part work? I write the code on ubuntu. Do I need to export (to a .exe?) and I can pass it around to my friends on a windows computer so they can easily install it and use it?
Pretty much - there's nothing stopping you from writing it on Ubuntu. py2exe creates a "dist" directory containing all the files you need. I don't think it creates an installable application as such, though - I think it's an exe that you have to run either from the command line or by clicking on it. An alternative I've just found is PyInstaller - don't know if it's any good, but the site indicates that it creates an installer, rather than an exe. However, I think with both py2exe and PyInstaller you need to package it up on Windows - you can't actually do so on Ubuntu.

There's a fair few Python applications that are available on Windows that have been packaged up as normal install packages - the Deluge BitTorrent client is a good example.

---

### Post by nvteighen on 2010-07-25
> **Emascu said:**
> 
What are the downsides of python? Why would I pick C++ over python?


Well, that I always hear using Python for Windows is a bit of a hell... That's why I departed from my usual suggestion in favor of Python. While py2exe makes distribution easy, the issues are related to setting up the development environment.

But if you can solve that and achieve to set it up (which shouldn't be a problem, but...), then, yes, use Python.

---

### Post by ghostdog74 on 2010-07-25
> **Emascu said:**
> Hello.

I'm a PHP programmer and I'd like to learn a programming language with which I can write actual programs. 
you can write programs with PHP as well. Its not just used for the web you know?

---

