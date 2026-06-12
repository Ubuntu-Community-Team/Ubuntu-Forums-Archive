---
title: "RAD tool for C programming"
date: 2011-12-15
forum: Programming Talk
---

### Post by a.r on 2011-12-15
Hello everyone,
I've searched the forum about a RAD tool for C development, and I saw some different suggestions, as wx, python, ect tools, to be adapted for C dev then, or something like that. I am little confused so I will directly post here in need of your help.

It is several years I develop using Borland C++, and I am looking for something who gives me the same ease of create and manage a project and its files, compiling, and code debug.

The language is C, I don't even think to move to other languages, because I'd like port to ubuntu a win32 console application that is about 20+ years/man of code and about 500k lines. Another reason, is that the application is used in industrial environment and will also do some critical things. Nothing medical, anyway, and another reason is, I don't want touch procedures who have been proved to work right for years.

Yes, I am asking much, but I don't want it all for free. I am open to use also commercial RAD tools, if there are.

If you know about RAD tools right for my needs, please let me know!

TIA, Andrea

---

### Post by trent.josephsen on 2011-12-15
I must admit, I'm a bit confused trying to interpret what you want.  Rapid application development (which I assume is what you mean by RAD) is a programming design methodology.  You don't need special tools to use it.  Furthermore, if you're maintaining code that's already in use, RAD hardly seems to apply; typically you want to adopt a more conservative methodology once you've hit production.  But that's your business.

Borland C++ is an integrated development environment (assuming you're not talking about the compiler alone), and there are a number of options available if you just want an IDE for Linux.  Eclipse is a good cross-platform one, but personally I don't really like IDEs, so maybe someone else could provide an assessment of the IDE options available for Linux.

---

### Post by a.r on 2011-12-15
Hello,
yes, what I need to maintain the provided code is an IDE. Eclipse seems a choose but have read in the forum it still not enough mature for production on its C plugin. Maybe things have changed, I let other experienced users tell me.

I were asking for a RAD tool because, as long I have to be involved in ubuntu stuffs, I'd like do new things using only one tool if possible. A windows example may be something like PowerBuilder, or C++Builder.

Hope I had explained better my needs. IDE sure I need it; and a RAD tool targetting C, a plus.

---

### Post by 11jmb on 2011-12-15
Is Wine not an option?

---

### Post by drdos2006 on 2011-12-15
I like Code::Blocks......

[http://www.codeblocks.org/](http://www.codeblocks.org/)

regards

---

### Post by a.r on 2011-12-16
> **11jmb said:**
> Is Wine not an option?

Hello,
it is not, because I am looking for make my source compiled and running natively on ubuntu. About the windows version, I keep it running on native windows machines, because it will connect to SQL Server database by native interfaces. That is another problem I will have to solve after the IDE one. But maybe I will do another thread about, when I come to that point.

---

### Post by fct on 2011-12-16
Apart from Code:Blocks and Eclipse:

Anjuta - [http://anjuta.org/](http://anjuta.org/)

CodeLite - [http://codelite.org/](http://codelite.org/)

---

### Post by trent.josephsen on 2011-12-16
Perhaps it would help if you listed some features you want, since I still don't really know what you mean by "RAD tool".

Emacs is always an option.

---

### Post by 11jmb on 2011-12-17
> **a.r said:**
> Hello,
it is not, because I am looking for make my source compiled and running natively on ubuntu. 

Just checking. The easy way out is always worth a quick look.


I have heard very good things about Kdevelop (don't you can get it for Windows, though), so you may want to check it out. It is geared towards C/C++, has a lot of useful plugins, and a lot of people seem to like it. 

In my experience, Netbeans and Eclipse have not been nearly as useful for C/C++ as they are for Java (slow and buggy). This was a few years ago, though, so they may have matured some.

Most of my C code is for small projects that I can develop faster with emacs and command line tools, so unfortunately I can't tell you too much about which IDEs you can pick.

If you plan to be developing on windows Code::Blocks is probably your best bet. It has tons of plugins that you may find useful for  your rapid development. Kdevelop is another alternative if you plan to be developing in Linux

---

### Post by a.r on 2011-12-19
Thank you everyone for your hints!

About "RAD tool", I meant a tool who gives me a visual way to create new user interfaces, and have enough "plugins" who lets me able do things without reinventing the wheel every time, as adding a database connection to my applications, and things like that. I mentioned PowerBuilder and Borland Builder as the tools I am using and I am looking for any equivalent in Ubuntu. Some years ago PowerBuilder had also Linux target but Sybase dropped it.

About windows development of my C project, there are no worries about tools who doesn't target windows, I will continue use Borland C++ for windows compiling and debug. The Ubuntu IDE can  target Linux only, both environments will share only the source files, while compiler-related and platform-related system calls are already in their own separate files, most likely I will have "just" to redo them.

---

### Post by 11jmb on 2011-12-19
> **a.r said:**
> 
a tool who gives me a visual way to create new user interfaces

QT Creator and Glade both have gui builders, depending on which graphics toolkit you would rather use.

---

