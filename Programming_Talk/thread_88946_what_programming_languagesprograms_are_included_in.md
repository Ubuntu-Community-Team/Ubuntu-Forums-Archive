---
title: "what programming languages/programs are included in Ubuntu?"
date: 2005-11-11
forum: Programming Talk
---

### Post by UbuntUser4389 on 2005-11-11
I woud like to get into programming. I know that python is included with Ubuntu and Perl maybe?? My question is what other languages are included and what program do you use to write your programs in??

Also, do you believe that there are people that could NEVER learn a programming language just because it doesn't make sense in their mind? I think I am one of these people. I got into Qbasic for DOS and I can do HTML, but when I got to the more advanced stuff in Qbasic I got really confused an none of it made sense at all!

Thanks a TON!

---

### Post by gerbman on 2005-11-11
[QUOTE=UbuntUser4389]I woud like to get into programming. I know that python is included with Ubuntu and Perl maybe?? My question is what other languages are included and what program do you use to write your programs in??[/QUOTE]

C++ is easy to install, and I use Emacs (awesome, IMHO).  Java + NetBeans IDE is another easy/free install.  

[QUOTE=UbuntUser4389]Also, do you believe that there are people that could NEVER learn a programming language just because it doesn't make sense in their mind? I think I am one of these people. I got into Qbasic for DOS and I can do HTML, but when I got to the more advanced stuff in Qbasic I got really confused an none of it made sense at all!

Thanks a TON![/QUOTE]

A lot of it has to do with how much experience you have had with computers and math in general (as programming is just applied mathematics).  Someone who grew up with math might take to programming more easily than someone who majored in, say, art.  But we shouldn't make generalizations; I'm sure there are plenty of artsy people who are great programmers and just as many math people who are lousy programmers.  It's really a function of how much work you put into developing your skill set.  

Of course the more advanced aspects of programming are going to be confusing, you shouldn't be surprised by that.  Some things take a long time to really understand.  I don't think you have to take a college course to learn most of what's important, but some sort of structure is necessary (maybe from a good book).

---

### Post by thumper on 2005-11-11
Also in the repositories I think you can find:
lisp, ruby, ml, fortran, scheme, pascal and I'm sure many more.

I would suggest though to start with python.

---

### Post by UbuntUser4389 on 2005-11-11
If I do want to start with Python (which is very likely) how do I save the file I make in Emacs or Gedit?? I mean what file extension do I use?? And how do I run the program???

Thanks a TON!

---

### Post by Quest-Master on 2005-11-11
Just.. click save as in Gedit, and make sure it is saved as a .py file. Pop open a terminal, go to the directory where you saved the script, and type in "python ***.py", where "***" is the name of your .py file.

---

### Post by Pathogenix on 2005-11-11
[QUOTE=UbuntUser4389]
Also, do you believe that there are people that could NEVER learn a programming language just because it doesn't make sense in their mind? I think I am one of these people. I got into Qbasic for DOS and I can do HTML, but when I got to the more advanced stuff in Qbasic I got really confused an none of it made sense at all![/QUOTE]

Nope, not for a second. Coding is like any other skill, it just takes time to learn it and a few bruises from banging your head off the desk.

I think a lot of people have trouble because it *looks* really complicated. Just remember that computers are stupid: if they can understand Python (or C, or Java, or even BrainFuck for heavens' sake) then so can you... but it might take a bit longer ;) Python is a nice language because everything works in a pythonic way... there aren't many nasty surprises and the syntax is just lovely.

[http://en.wikipedia.org/wiki/Brainfuck](http://en.wikipedia.org/wiki/Brainfuck) by the way, if you're curious. SNUSP is also fun, for sufficiently small values of fun.

---

### Post by Buffalo Soldier on 2005-11-11
[QUOTE=UbuntUser4389]If I do want to start with Python (which is very likely) how do I save the file I make in Emacs or Gedit?? I mean what file extension do I use?? And how do I run the program???

Thanks a TON![/QUOTE]Here's what I usualy do:[list=1]
[*] Right click on desktop -> Create Document -> Empty File
[*] Rename file to anything with .py extension
[*] First line in file must be:```
#!/usr/bin/python
```Example:```
#!/usr/bin/python
print "Game Over"
raw_input("\n\nPress the enter key to exit.")
```
[*] Save file
[*] Set your python script as executable. Right click on the file -> Properties -> Permisions -> check Execute.
[*] To run your script, double click it. A message window will pop up asking "Run or Display?", choose 'Run in Terminal'.
[/list]

Note: If you want to keep the window terminal open after pressing ENTER, change the terminal window settings.
Go to ->Edit -> Current Profile -> Title and Command -> When command exits: Hold the terminal open.

---

### Post by Luke Redpath on 2005-11-11
[QUOTE=Buffalo Soldier]Here's what I usualy do:[list=1]
[*] Right click on desktop -> Create Document -> Empty File
[*] Rename file to anything with .py extension
[*] First line in file must be:```
#!/usr/bin/python
```Example:```
#!/usr/bin/python
print "Game Over"
raw_input("\n\nPress the enter key to exit.")
```
[*] Save file
[*] Set your python script as executable. Right click on the file -> Properties -> Permisions -> check Execute.
[*] To run your script, double click it. A message window will pop up asking "Run or Display?", choose 'Run in Terminal'.
[/list]

Note: If you want to keep the window terminal open after pressing ENTER, change the terminal window settings.
Go to ->Edit -> Current Profile -> Title and Command -> When command exits: Hold the terminal open.[/QUOTE]

All that clicking seems a bit long winded to me!

```

echo '#!/usr/bin/python' > mynewfile.py && chmod +x mynewfile.py

```

---

### Post by Buffalo Soldier on 2005-11-12
[QUOTE=Luke Redpath]All that clicking seems a bit long winded to me!

```

echo '#!/usr/bin/python' > mynewfile.py && chmod +x mynewfile.py

```[/QUOTE]Feel the force of the CLI :) I should be using more of the force next time.

---

