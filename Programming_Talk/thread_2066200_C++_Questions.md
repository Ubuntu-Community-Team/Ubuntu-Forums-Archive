---
title: "C++ Questions"
date: 2012-10-04
forum: Programming Talk
---

### Post by Naulkrinn on 2012-10-04
Here there fellow Ubuntu / Linux users. My names Mike and I'am back again to using Ubuntu on my computer and wanted to know if anyone else uses C++. If you do, where can I learn it from and how do I write it on Ubuntu, etc. Do I need software or anything special? Also is there a post on here or a section that talks about C++. Anything you can tell me would be majorly appreciated. 

- Mike aka Naulkrinn

---

### Post by akoskm on 2012-10-04
I'm not using C++ at all, but you should definitelly search google with the following terms: **c++** **ubuntu**.

The search will return you dozens of Ubuntu related c++ programming posts, including writing, compiling, running, debugging c++ programs on Ubuntu.

Hope this helps.

---

### Post by umesh314 on 2012-10-04
You can use vim editor in terminal for writing your codes.
 
Step 1:
   Launch terminal ( Ctrl + Alt + T ) 
 
Step2:
   Use vim editor . vim <filename.cpp>
 
Step3:
   Once you have written the code. Save and Quit from it (:qw)
 
Step4:
   Use g++ compiler to compile and make executable.
   command:  g++ -o <binary-name(your choice)> <filename.cpp>
   For example -  g++ -o sample mysample.cpp
 
Step5:
   Step4 will create executable "sample" for you. 
   You can run ./sample to execute your program.
 
Hope above info helped you.

---

### Post by Nytram on 2012-10-04
There's a programming section on this forum which you may find useful, it has stickies with links to tutorials for a number of programming languages:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by JamezQ on 2012-10-04
Hey, computer science major here. I've been programming on Ubuntu for years, including c++.

All you need is a c++ compiler,and some kind of editor, such as g++.

umesh314 gave what you need to compile.

If you are new to using linux or programming, you might want to start out with gedit (the default "text editor" in ubuntu). Another option is geany, which has support for c++ and you are able to compile and run without leaving the editor.

Certainly do check out vim and emacs though, but both of them take time to learn.

---

### Post by androssofer on 2012-10-04
> **Naulkrinn said:**
> Here there fellow Ubuntu / Linux users. My names Mike and I'am back again to using Ubuntu on my computer and wanted to know if anyone else uses C++. If you do, where can I learn it from and how do I write it on Ubuntu, etc. Do I need software or anything special? Also is there a post on here or a section that talks about C++. Anything you can tell me would be majorly appreciated. 

- Mike aka Naulkrinn

The advice above is great. I'd simply like to share my experience with C++.

I decided to learn C++ for fun. I read about Qt, which is a GUI based set of C++ libraries and decided to use it. So I learnt C++ by making simple programs in Qt. I installed the 'Qt creator' IDE from the software center. Its a rather nice IDE, and allows the creation of applications nice and quick. Then followed these videos:

[http://www.youtube.com/playlist?list=PL96F340CA97DDD187&feature=mh_lolz](http://www.youtube.com/playlist?list=PL96F340CA97DDD187&feature=mh_lolz)

However is isn't quite standard C++ (you can use standard C++ within Qt if you like tho..). It does allow the creation of rather nice applications fairly quickly.. and gives you enough of the basics to be fun.

So if your just doing it for a hobby try Qt.. if you want to learn C++ professionally the advice above is prob better... :-)

---

### Post by sffvba[e0rt on 2012-10-04
*Thread moved to **Programming Talk**.*


404

---

### Post by Naulkrinn on 2012-10-04
Wow thank you so much guys for the feedback I will definitely look into what all of you have talked about.  I used to write html code for fun. One day I was reading a guide for it when it started talking about C++ code and Java code. Im really interested in it and anything and everything that can help me learn it is awesome to me.

-Mike aka Naulkrinn

---

### Post by Naulkrinn on 2012-10-04
> **JamezQ said:**
> Hey, computer science major here. I've been programming on Ubuntu for years, including c++.

All you need is a c++ compiler,and some kind of editor, such as g++.

umesh314 gave what you need to compile.

If you are new to using linux or programming, you might want to start out with gedit (the default "text editor" in ubuntu). Another option is geany, which has support for c++ and you are able to compile and run without leaving the editor.

Certainly do check out vim and emacs though, but both of them take time to learn.


Thank you so much I appreciate the support.  Is there anything I can make or do special with C++.

---

### Post by MG&amp;TL on 2012-10-04
> **Naulkrinn said:**
> Thank you so much I appreciate the support.  Is there anything I can make or do special with C++.

Everything (almost - DirectX and Winforms being notable examples) you can do on other platforms. :)

---

### Post by Naulkrinn on 2012-10-04
> **MG&TL said:**
> Everything (almost - DirectX and Winforms being notable examples) you can do on other platforms. :)

Is it hard or difficult to compile programs to make? Also is there anything I should write to help me understand its functionality?

---

### Post by zombifier25 on 2012-10-05
Not really. If you want to just write a small program, then a text editor and g++ (the C++ compiler) is okay. Just fire up your favorite text editor, code, save the file (in the home directory for convenience), and type in terminal:
```
g++ /path/to/code.cc -o executable
./executable #to run the progam
```

If you want a dedicated IDE, Geany is good.

---

