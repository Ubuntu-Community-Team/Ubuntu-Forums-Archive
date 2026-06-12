---
title: "Run hello world in c++"
date: 2008-02-18
forum: Packaging and Compiling Programs
---

### Post by romihim on 2008-02-18
I have been using turbo c(i know itz old) in windows , and and now switching to programming in linux .have used g++ and gdb to run c++ programs,but i wanted an ide like turbo c in linux , which could provide me with good debugging options.So tried anjuta .But itz not running even hello world program.actually anjuta shows only compile option in the build toolbar and rast are greyed out . Plz help ...........

---

### Post by mouse5hi7 on 2008-02-18
its not that hard to learn how to use the g++ compiler.  it would look something like this if your program was call hello.cpp
```

g++ hello.cpp -o hello

```

the g++ hello.cpp compiles that file, and the -o hello names the executable file hello

---

### Post by whitewizardcoder on 2008-02-18
Although I use the command line and gedit for programming, I know that Eclipse has a plugin for C/C++ development.  I've used Eclipse for java before and It's a really nice IDE.  You might want to check it out.

---

### Post by romihim on 2008-02-18
never tried eclipse , but have netbeans 6 ..........not able to use it too...........!!!!!
Actually i m new to c++, hence dont need much functions ,so a light weight ide would do .............
anjuta seems perfect for my needs ..have used it on 6.06 ,a year back ..............den i had no problems running wid anjuta , but now on gutsy ..............dont know ats happening

---

### Post by romihim on 2008-02-18
> **mouse5hi7 said:**
> its not that hard to learn how to use the g++ compiler.  it would look something like this if your program was call hello.cpp
```

g++ hello.cpp -o hello

```

the g++ hello.cpp compiles that file, and the -o hello names the executable file hello

thanx for prompt reply .i use g++, but not comfortable with gdb.........
the only problem comes,is while debugging ......hence the need for ide

---

### Post by romihim on 2008-02-18
actually just found out that if i make a project and then put my code in the project then anjuta is executing cpp code.............
indirect way to solve small prob...........
but wat if i dont want to make a project , just doing normal coding in a file and want to compile it .
is der any way out

---

### Post by perixx on 2008-02-25
I've got no idea if it helps, but Dev-C++ seems to be a pretty nice free IDE to me; but I can't tell if it's possible to compile it under Linux...

perixx

---

### Post by Nemooo on 2008-02-25
Dev-C++ is not downloadable for Linux, though it seems to be on an orderable CD.

[http://www.bloodshed.net/download.html]("http://www.bloodshed.net/download.html")

---

### Post by perixx on 2008-02-25
No, but it's availible as Delphi source:
[http://www.bloodshed.net/dev/devcpp.html]("http://www.bloodshed.net/dev/devcpp.html")

That's why I'm not sure if it can be compiled under Linux - at least not without having a Borland(?) Delphi compiler at hand... or is there maybe a free Delphi compiler availlible somewhere...

perixx

---

### Post by WW on 2008-02-26
Code::Blocks ([http://www.codeblocks.org/](http://www.codeblocks.org/)) is a nice IDE, and it is available for Linux.  Elsewhere in this forum is a long thread about "Your favorite IDE" that you might (or might not!) want to take a look at.

---

### Post by greenkernel on 2008-10-09
> **romihim said:**
> actually just found out that if i make a project and then put my code in the project then anjuta is executing cpp code.............
indirect way to solve small prob...........
but wat if i dont want to make a project , just doing normal coding in a file and want to compile it .
is der any way out
You can write a standalone source code file in Anjuta too.

[LIST=1]
[*]Select "New" from the "File" menu and select "_2_. File" sub-menu.
[*]Choose "Name" and "Type" of your source code file.
[*]A text editor workspace will appear in the right panel to write your source code.
[/LIST]
Done!

Regards
[COLOR="DarkGreen"]
greenkernel[/COLOR]

---

### Post by greenkernel on 2008-10-09
> **romihim said:**
> actually just found out that if i make a project and then put my code in the project then anjuta is executing cpp code.............
indirect way to solve small prob...........
but wat if i dont want to make a project , just doing normal coding in a file and want to compile it .
is der any way out
You can write a standalone source code file in Anjuta too.

[LIST=1]
[*]Select "New" from the "File" menu and select "_2_. File" sub-menu.
[*]Choose "Name" and "Type" of your source code file.
[*]A text editor workspace will appear in the right panel to write your source code.
[*]Save your source code in your desired directory when finished.
[*]Open terminal emulator and type as follows:
> g++ source.cxx -o source
[*]You will get an executable file if nothing is wrong during compiling.
[/LIST]
Done!

Regards
[COLOR="DarkGreen"]
greenkernel[/COLOR]

---

### Post by perixx on 2008-11-01
> Code::Blocks ([http://www.codeblocks.org/](http://www.codeblocks.org/)) is a nice IDE, and it is available for Linux. Elsewhere in this forum is a long thread about "Your favorite IDE" that you might (or might not!) want to take a look at.
Yes, I've used that IDE for a short time meanwhile, I found it really simple and intuitive to use!
Another alternative would be Eclipse with C++ plugin, but the first one is perhaps better for small projects/programs, plain simple and lightweight...

perixx

---

### Post by romihim on 2010-02-20
Thankyou for your replys.

my problem is solved. 

Now i mostly program in devcpp . Today i checked codeblocks(again) , and really liked it , most importantly the functionality of opening a c++ file and run it by press of a key(F9), without going through hassels of creating the project ,unlike other IDE(anjuta,visual c++ etc ) .

Geany is  the next best .

I havent figured out how to debug in codeblocks(i want something like dev cpp) when i havent created a project (wen in project we can easily start debugger ).

I am from India , and most of schools here only allow Turbo C (infact my college too...)
So for all those looking for turboc or itz functionality in linux Go lie this :-
1)Install dosbox(through synaptics or sudo apt-get install dosbox)
2)open dosbox.conf(in your home directory) with gedit .
3)Mount your drives(the partititions where TC is stored)
4)Goto tc/bin
5)open tc.exe
Now you can run all your programs in tc ..
If u store ur programs in tc directory only , no need to go through steps 2 to 5.Just navigate to tc folder in nautilus, right click->openwith dosbox .
thats it .

though TC is not a standard compiler , and is toooo old , still it provides good functionality for small projects and sometimes necessary for school/colege projects .So please dont comment on tc's problems-i know them

---

### Post by romihim on 2010-02-20
One more thing , when using tc through dosbox dont use CTRL-F9 to compile programs as its the dosbox shortcut for exit .Use menus , or the best -map dosbox CTRL-F9 key to something else , like ALT-F4 .

---

