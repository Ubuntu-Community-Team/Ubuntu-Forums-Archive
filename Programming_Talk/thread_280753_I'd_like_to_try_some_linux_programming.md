---
title: "I'd like to try some linux programming"
date: 2006-10-19
forum: Programming Talk
---

### Post by s0c0 on 2006-10-19
I've done some programming on the Windows platform (VB6, .NET, ASP) but I have zero experience in C++, Java, or any other languages primarily used in Linux.

I'd like to try building some simple apps in linux, maybe something dumb like a calculater to get the basics down or even a cli tool.  Any thoughts on what language I should start with and tools I should use.  Does linux have anything near as good for the GUI as the .NET IDE?  If so, thats what I'd like to use, but I'm not opposed to something simple to start with.  Any special packages I need?

Eventually I'd like to begin doing some web 2.0 stuff like ajax so any tips on what linux stuff to use for php, mysql, javascript, and xml stuff is helpfull.  I'm open to pointing me towards some books and websites as well.

Thanks for reading folks.

---

### Post by bdb on 2006-10-20
> **s0c0 said:**
> I've done some programming on the Windows platform (VB6, .NET, ASP) but I have zero experience in C++, Java, or any other languages primarily used in Linux.

I'd like to try building some simple apps in linux, maybe something dumb like a calculater to get the basics down or even a cli tool. Any thoughts on what language I should start with and tools I should use. Does linux have anything near as good for the GUI as the .NET IDE? If so, thats what I'd like to use, but I'm not opposed to something simple to start with. Any special packages I need?

Eventually I'd like to begin doing some web 2.0 stuff like ajax so any tips on what linux stuff to use for php, mysql, javascript, and xml stuff is helpfull. I'm open to pointing me towards some books and websites as well.

Thanks for reading folks.

IDEs that I know of but haven't used
-monodevelop
-eclipse
I would consult these projects for more information.

If you want to do web programming and you already know .net you should try mono. It is an open source implementation of .net. Any xml knowledge will transfer over. Javascript is more dependant on the browser than the server. PHP and mysql I know nothing about.

Good luck and happy programming

---

### Post by theDentist on 2006-10-20
I can give you my non-proffessional experience.  I'm an amature that started with VB6 in windows a few years ago, I wanted more control of the computer than VB6 would let me, so I bought some good books and learnt the fundamentals of C/C++.  The best thing I ever did, It gave me a good background knowledge (well, in my humble opnion)of OOP, and understanding of memory management. I learnt to program the API in Win32, again good background knowledge, then I went on to MFC Visual C++ 6.  The software I use in my surgery I wrote in MFC VC++ 6.
And of course I couldn't resist Ubuntu Linux, so there it is. Buy a gook book, learn C/C++, and move on from there to where you want to go.  With a knowledge of C/C++ you can use the glib,gtk,gnome libraries from a simple editor, although I use Glade myself for the GUI.  Others of course will probably disagree with everything I've said, but It's always good to hear other programmers experiences. Happy programming!   :-D 

Peter

---

### Post by randomnumber on 2006-10-21
If you want to make a calulator I suggest java for a gui over c++. Java is good for gui but is slow compared to c++. In a Calculator program the speed does not matter. I made a solitar game in java for intermediate programming class.

For both java C++
To get use to either one I would suggest using a simple text editor and compiling in a terminal until you get a understanding of the language and how to program. Basicly write a hello world program first. Almost all programs should run in mac, linux or windows. It takes a recompile to run c++ applications in other OS while java programs use a virtual machine and do not need a recompile. The recompile has to be done with a compiler for the OS you want to run it on.

The eclipse program is very nice and I would not want to program with out it but It has a very large learning curve. I actually started with a program called JGrasp. I dont know if it supports linux and I do not recomend it.

If you want a nice text editor that supports highlighting I would just use gedit or kate. Then go back to a terminal to compile. 

Another note: I use the book "Big Java 2nd ed by Cay Horstmann" for programming in java and think it is better than most. It goes over basics very well and is up-to-date with current java 1.5. This is important for ArrayList and String classes.

Java is very different than c++ and is much more object oreinted. It is a very protected language. There are benifits and problems of each. Each has its own type of task it works well for. Ohh and forget java applets, useless.

commands for compiling
java file: javac "filename.java"
c++ file: g++ "filename.extension?"

running a java prgm : java filename ( do not include .class extension)

Basicly: Start slow. Don't get into a application with its own learning curve ontop of the language learning curve, use eclipse for java after you get started.

good luck and dont get discouraged.

---

### Post by Dimitar on 2006-10-21
i say stick to something like vi, or gedit, like randomnumber suggests as your text editor, but i disagree on some things, i think java is an easier language to begin with, it was the first one i started with and now ive moved on to C and C++ mind you, i like C and C++ alot better just because of the freedom, the good thing about java though is that it looks after many things, (memory management, garbage collection) and everything is passed by reference, so you dont need to worry about derefrencing and etc. As for eclipse, you can pretty much use it for any language now days i think, its just about finding the right plugin for it.

Good Luck

---

### Post by 3rdalbum on 2006-10-21
I believe a lot of Web 2.0 stuff is being done in Ruby... in fact, the name "Ruby on Rails" is probably the catch-phrase of the minute.

If you're familiar with .NET, you'll probably feel right at home in Mono. The Gnome developers are really getting behind Mono at the moment, and I'm sure KDE will eventually follow.

---

### Post by randomnumber on 2006-10-21
I am not sure what Dimitar disagrees with. It seems as though Dimitar believes I made the statement that java is harder language to learn or use. I do not see where I made suck a statment and aplogize if that is how someone would see what I said. I would suggest taking a C++ class before java but there is debet over this at our school and I have taken a side on the issue. My opinion is that you need to know how to write one program before learning how to write many programs that work together. It is not the language that I take this opinion about, it is the way the class is taught. I tried to dicribe the debate without pursadeing. Anyway, this type of debate belongs to its own thread.

I agree that java is a easier language and becuase it has memory collection so you can not create a memory leak. Java API makes gui much easier. Pass by reference keeps data protected so that other programs can not modify it.

Example:
   BankAcount tempOne = new BankAcount($5);
   BankAcount tempTwo = new BankAcount($7);
   tempTwo = tempOne;
   tempTwo = new BankAccount($12);
   //this does NOT change tempOne to point to a BanKAccount with $12.
   //also in java this is not a memory leak but in c++ it is.
   //in c++ you would have to dealocat the BankAccount with $7

Exmple2:
   int a = 1
   int b = a
   b = 5
   // a is not equal to 5  at the end.

C++ is a faster language! Faster is intend to discribe runtime. Java has to be run on a virtual machine which is basicly a emulated computer. This means that java is slower. The virtual machine is what alows java prgms to have cross platform compatability. Java runs background applications such as memory collection. Java has gotten faster over the years but c++ faster. 

I use java and have had only a intro course in C++ but in our classes we constantly discribe differences between the two. I am currently in a class called DataStructures and the basics of the class are how data is represented. Our last project is to be written in C++.

---

### Post by Dimitar on 2006-10-22
oh sorry randomnumber! i read it incorrectly, sorry about the misunderstanding.

---

### Post by randomnumber on 2006-10-22
No problem. I thought I made have made a typo that i could not find. I am terrible at profreading and spelling.

---

