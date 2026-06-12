---
title: "C/C++ compiler and installation"
date: 2006-02-04
forum: Programming Talk
---

### Post by user_of_gnomes on 2006-02-04
Hello,

I switched to Linux not too long ago, but found myself unable to continue studying C/C++. All the books I have assume that you have Windows installed and therefore do not explain how to install a compiler (or find the proper compiler for that matter)under Linux.

I tried g++ but it doesn't make sense to me, it seems like I have to run it from the command line. Not my cup of tea. Plus, I don't understand where I'd have to write down the code before compiling it. 

One compiler I liked was the one offered by bloodshed.net (Dev C++) there seems to be a Linux version but I don't even understand how to install binary packages, I only know how to operate the synaptic packet manager.

Any recommendations and instructions? 

Any recommendations on good (beginner) books on C/C++ are welcome as well. (As long as they're not written by Stephen Randy Davis.. ) 

Thanks in advance!

---

### Post by Adrian on 2006-02-04
[QUOTE=UbuntuRaptor]Any recommendations and instructions? 
[/QUOTE]

You want to install an IDE (Integrated Development Environment). I'd recommend KDevelop (the **kdevelop3** package) or Anjuta (the **anjuta** package). Enable the extra repositories (as desribed [here]("http://www.psychocats.net/linux/sources.php")) and install them (one of them or both) using Synaptic. You must also install the **build-essential** package, if you haven't done that already

> 
Any recommendations on good (beginner) books on C/C++ are welcome as well. (As long as they're not written by Stephen Randy Davis.. ) 


If you don't mind reading digital documents, here are two free books:
[http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html)

---

### Post by user_of_gnomes on 2006-02-04
> You want to install an IDE (Integrated Development Environment). I'd recommend KDevelop (the kdevelop3 package) or Anjuta (the anjuta) package. Enable the extra repositories (as desribed here) and install them (one of them or both) using Synaptic. You must also install the build-essential package, if you haven't done that already

Thanks for the instructions, Adrian. Kdevelop seems like a compiler I've been looking for. Even looks a wee-bit like Dev C++. 

> If you don't mind reading digital documents, here are two free books:

Looks good, I'll be sure to give those a read. What books on C/C++ did you read and find useful if you don't mind me asking?

---

### Post by Adrian on 2006-02-04
[QUOTE=UbuntuRaptor]Thanks for the instructions, Adrian. Kdevelop seems like a compiler I've been looking for. Even looks a wee-bit like Dev C++. 
[/QUOTE]
I use KDevelop myself, and I'm perfectly happy with it.

> What books on C/C++ did you read and find useful if you don't mind me asking?

This:
[http://www.amazon.com/gp/product/0201721481/](http://www.amazon.com/gp/product/0201721481/)
was the first C++ book I read, in 1997. It's very nice for people who already know a little programming (I knew C and Java), but I don't know if I would recommend it to someone without any previous programming experience (however, they say that the new 4th edition is easier).

Regarding C books... I borrowed everything the library could offer in the beginning of the 90's :)

---

### Post by user_of_gnomes on 2006-02-05
[QUOTE=Adrian]This:
[http://www.amazon.com/gp/product/0201721481/](http://www.amazon.com/gp/product/0201721481/)
was the first C++ book I read, in 1997. It's very nice for people who already know a little programming (I knew C and Java), but I don't know if I would recommend it to someone without any previous programming experience (however, they say that the new 4th edition is easier).

Regarding C books... I borrowed everything the library could offer in the beginning of the 90's :)[/QUOTE]
 
Unfortunately, all the libraries I have access to future only one book, and that one book happens to be written by Steven Randy *"4 bits equal 1 byte"* Davis. :neutral: 

I'll look into the books you gave me, thanks a lot!

---

### Post by Viro on 2006-02-05
Thinking in C++ volumes 1 and 2 are very good books on C++. They're available for free from the author's website at [http://www.mindview.net](http://www.mindview.net). Volume 1 covers the core C++ language, while volume 2 goes into much more advanced stuff. Definitely worth a read.

---

### Post by user_of_gnomes on 2006-02-05
[QUOTE=Viro]Thinking in C++ volumes 1 and 2 are very good books on C++. They're available for free from the author's website at [http://www.mindview.net](http://www.mindview.net). Volume 1 covers the core C++ language, while volume 2 goes into much more advanced stuff. Definitely worth a read.[/QUOTE]

Thanks, allready recommended by Adrian, though. But since it's been recommended before any other book twice I guess it's definitely worth a good a read. ;)

---

### Post by Lord Illidan on 2006-02-05
[quote=UbuntuRaptor]Hello,

I switched to Linux not too long ago, but found myself unable to continue studying C/C++. All the books I have assume that you have Windows installed and therefore do not explain how to install a compiler (or find the proper compiler for that matter)under Linux.

I tried g++ but it doesn't make sense to me, it seems like I have to run it from the command line. Not my cup of tea. Plus, I don't understand where I'd have to write down the code before compiling it. 

One compiler I liked was the one offered by bloodshed.net (Dev C++) there seems to be a Linux version but I don't even understand how to install binary packages, I only know how to operate the synaptic packet manager.

Any recommendations and instructions? 

Any recommendations on good (beginner) books on C/C++ are welcome as well. (As long as they're not written by Stephen Randy Davis.. ) 

Thanks in advance![/quote]

About g++, it is actually quite simple. First you write the c++ program in a text editor, like vi, kate, or nano... take your pick. Just don't write it in Open Office, because compilers cannot understand the formatting symbols. If for some perverse reason you want to use OOffice, then don't use formatting, and save in .txt

Let's say you saved the file as [I]example.cpp

[/I]All you have to do is open a terminal and type in the same directory:

```
g++ example.cpp -o example
```

This will compile the code and generate a binary called example. You can then run the binary with

```
./example
```

Cheers!

---

### Post by user_of_gnomes on 2006-02-06
Sounds easy enough. I'll give that a shot too, just to see how it works. But I still prefer being able to type code and compile in the same program. :)

---

### Post by Revert on 2006-02-06
If you like compiling in the same program, you also might consider a few text editors with compiler integration.  SciTE's my personal favorite, although there's also Jedit and a few others, but they're much more lightweight in comparison to bulky IDEs like Eclipse and such, and they still let you compile and run a console inside it.

---

### Post by Crazy Man on 2006-02-09
Personally, I recommend using gvim for editing (apt-get install vim-gtk) if you're used to vi at all. you can compile inside the editor by doing:

<esc>:!g++ ...

where ... are your command line arguments. Unlike Scite, you can include linker options, which is essential if you're going to be using different engines/frameworks for development (such as allegro or GLUT).

---

### Post by user_of_gnomes on 2006-02-09
> which is essential if you're going to be using different engines/frameworks for development (such as allegro or GLUT).

So far I am not even certain what the phrase *calling a function* means,  but thanks for the input, though. :D

---

