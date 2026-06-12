---
title: "Migrating a program to Ubuntu"
date: 2008-03-06
forum: Programming Talk
---

### Post by Jim42 on 2008-03-06
Ok, this is kind of a vague question, i know, but still I'd like to be pointed in the right direction, or at least any direction :P.

Basically i want to begging learning how to make solutions for Linux, i know it will probably be way different depending on the distros and everything it takes along, but right now I'm interested in Ubuntu.

So, i have a window$ application i would like to migrate, it doesn't have to be pretty since it's a personal project but it has to be functional :P. The program I'm trying to migrate is made on it's majority under Vi$ual Ba$ic and it access an MSSQL database, so I suppose ODBC is a given (unless there's something else linux uses to access databases). I'm guessing I'll have to check on some X programing so i can make the forms and find some way to use odbc or something similar, I have some C/C++ and java knowledge (not even close to a pro, but some).

So my inquire is whether or not there's some language i can get into in order to make this kind of applications and if there is, where can i find it and a tutorial / manual for it? :P (if there's a way to do it with c or java, even better!).

Edit: Oh yeah, forgot to mention i already read the FAQ, can't find a thing about accessing mssql, which is the real problem

---

### Post by pmasiar on 2008-03-06
Linux prefers free software solutions: ubuntu prefers Python, and databases are MySQL, Postgres, and SQLite. No VB and no MSSQL :-)

---

### Post by Jim42 on 2008-03-06
Oh i know that, i actually love MySQL, but since it's a windows application, and i'm not the onlyone in the project, i have to use MSSQL, thus why i wonder if theres something like ODBC that i can use to make a connection.

I've actually been reading a lot of posts, and the "How to help Ubuntu" and python does look like the way to go, i guess i'll read the languages reference, see if i can find something for the above purpose.

---

### Post by schmendrick on 2008-03-06
hi jim,

i am not sure if your program also has a GUI, but i guess so.


actually i would recommend you something that i think most other users here will shake their heads when reading this.

try out monoDevelop. you can code VB there. i dont know how good VB is supported by mono, but C# 2.0 is working like charm on linux so chances are VB will do so too. 

for your DB usage in your program, if you are using ado.net then it is somewhat easy:
then i would suggest getting the mySQL connector for .NET. with that you then can use a mySQL database and your VB code database related code can stay pretty much the same. 
if  you make the effort to write a intelligent wrapper class it will be completely indifferent for the programmer if you connect to MSSQL via windows or to mySQL via linux. 

as for the front-end, well.... i am afraid chances are big that you'll have to rewrite it. there is GTK, a forms-framework support in mono with which you can write your forms, but it is quite different to Windows.Forms. 

i have heard about Windows.Forms being ported by Mono but i dont know the status of this. 

second best option would be to code java i guess. then you have a nice database support and you can code swing or SWT to make your GUI. but you will not be able to reuse any of your code. 

anyways for accessing mySQL databases there are many solutions in all programming languages. just google  for "connector .NET mySQL" or "java mySQL" for getting ready-classes to do so. 

same but a bit more complicated goes for c++, you can look at the mySQL forums. 

hope this helps

---

### Post by pmasiar on 2008-03-06
Of course you can contribute whatever you want. But if you want to contribute to linux something other people can easily use and improve, you are better off using tools other people use. IMHO **MSFT made conscious decision to make Windows incompatible with Unix** (and succeeded): even some trivial things, like path delimiter: \ is escape character in Unix/Linux. Using ' for comments, and # for something else in VB. Etc etc.

So there is some compatibility layers, but many developers see efforts to make proprietary software work as waste: because without sources, you cannot fix it properly, it is just adding patch over a patch. Many people consider creating a free clone more fun, more usefull solution, and "better": because you don't have to follow, you can lead.

You can try the other approach: subvert proprietary app to be build using free tools: MySQL can run on Windows too, and Python runs on Windows, IronPython works on .NET. You can use Java of course, but Java is yet another deliberately incompatible universe.

---

### Post by Zwack on 2008-03-06
To add to what has gone before...

If you're using C++ or Python then you can use [Wxwidgets]("http://www.wxwidgets.org/") to write cross platform GUI apps that can work on multiple platforms.  I don't know if they've added any database access components but they do have the gui parts. 

Z.

---

### Post by WW on 2008-03-06
For what it's worth: [pymssql](http://pymssql.sourceforge.net/). (I've never used it.)

---

### Post by slavik on 2008-03-06
> **pmasiar said:**
> IMHO **MSFT made conscious decision to make Windows incompatible with Unix** (and succeeded): even some trivial things, like path delimiter: \ is escape character in Unix/Linux. Using ' for comments, and # for something else in VB. Etc etc.

\ was a delimeter in CPM, which MS copied/stole/got ideas from/turned into DOS

' is shorthand for REM meaning REMARK, that is how you declare a line to be a comment in BASIC which MS extended/used/etc.

not sure about # though :)

---

### Post by mssever on 2008-03-07
If SQLite suits your needs, it can run on Windows. All it is is a C library.

If SQLite doesn't work, that probably means you're connecting to a DB on a server somewhere, which suggests that you could probably choose a database that works with everything, not just Microsoft, and install that on your server.

---

### Post by Jim42 on 2008-03-07
Ok, i should have given some more important information :P

1) I don't mind rewriting the whole thing in another language, as i said, it's a personal project with no other intention but learning, i was just wondering whats mostly used for linux apps (Looks like python is the way to go, at least for Ubuntu).

2) The database is actually on a server over the web, and i cannot change it, i need to adapt to it somehow, thus the inquire of whether or not there's a way to connect to it ... pyMSSQL looks promising.

3) I do need a GUI, since i was considering Python, i looked into it today, wxPython looks promising, specially for the closs-platform support.

4) I am not, by any means a vb fan, actually i picked this project after it had already being started, i'm just adding stuff and giving support, one of the reasons i want to do it is cause i hate the current code with a pasion ...

Thanks for all the feedback so far, it has opened a good wide of choices i'm looking into atm :).

---

### Post by pmasiar on 2008-03-07
To add you one more option, and learn something cool, consider while rewriting to make it web-based app, with AJAX to added page dynamics. Django and TurboGears are popular Python web app frameworks. They fit for slightly different kinds of app, I prefer TG.

---

