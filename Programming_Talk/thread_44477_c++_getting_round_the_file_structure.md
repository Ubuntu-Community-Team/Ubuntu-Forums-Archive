---
title: "c++: getting round the file structure"
date: 2005-06-26
forum: Programming Talk
---

### Post by robert crowther on 2005-06-26
Any c++ programmers out there?

I've written my first c++ program. I'd like it to scan my system to locate some files.

I really don't know how to do this. Niether of my reference books have any details on such things, they only cover in/out to files the programmer has already identified.

I find this easy enough to understand - c++ is supposed to be portable, whereas file tree implementations are not.

A web search recovered nothing of interest, and since I don't know where to start, I don't know what to search for...

I looked at 'boost', which seemed to fit my needs, but the ubuntu package doesn't work on my system - even the example programs crash out of compiling. 

Yet programs all over the world, written in c++, are writing .rc files, config files, searching for file types, etc.

I looked at invoking shell commands, and got as far as 'system', but I need to understand the mechanism - I might be looking for 30 files I would like my program to look at.

I don't need a huge explaination, just a pointer to how this is done - get me off the blocks.


Cheers!

Robert

---

### Post by thumper on 2005-06-26
I'd try to take another look at boost.  I didn't use the deb package, but instead got the most up to date tar ball from the boost website and built that.

For writing and reading files, use the file streams.  std::ifstream, std:: ofstream, and std::fstream, you should definately have some reference to that in your books.

If you haven't already got it, get "The C++ Standard Library: A Tutorial and Reference" by Nicolai Josuttis.  It really is the best standard library reference I have come across.

---

### Post by LordHunter317 on 2005-06-26
The boost stuff in Ubuntu ought to work fine.  If you got errors, it could help to post htem.

They provide some directory portability stuff, but it's not perfect.  Using the opendir()/readdir() and friends is the UNIX way to do it.

What are you're trying to do?  It may be better not to do this in C++, depending on your goal.

---

### Post by robert crowther on 2005-06-27
Thanks for both replies, they both contain advice that shed a little light on the problem, but I'm still no nearer...

Firstly, the Boost package didn't work on my system. It unpacked fine, all libraries seem to be present, but responded with errors when I tried to run any of my programs, and also fails with the supplied example programs. I pointed my program at the headers, but keep getting errors.

I went away and recovered the Boost source files, and tried to build the latest version. This is something I am now regretting. The build has failed, in some way, with the boost library headers clearly addressing the wrong places. I now have unusable files splattered all round my previously clean system. Guess I'll have to clean it up by hand...

I really feel I'm barking up the wrong tree with Boost. A quick install to recover one command, fine, but a full compile of many many Mb's for one simple action... not really. I've never loaded a program with Boost as a dependancy, either, so all those who write in c++ don't use it, yet they can recover files. For example, a music editor can look at directory and recover the .wav files.

Anyway, a little more detail on what I would like to do.  I'd like to go to a directory, (the name of which I can supply), scan the contents for files of a certain type (eg. *.txt), and return this list in some form readable by my c++ program. I have no problems handling the files, once I know what they are!

In a shell script, this is easy as, say

ls [some directory] |grep .*\.txt

(If I recall my bash alright)

leading me on to ...s point, that this may be better done some other way. Quite right too, I have no doubt I could do this easily in Python or Ruby. It just so happens that I'm fixed on c++, and I've got other projects in mind which will go, as a whole, much easier in c++, so I'd like to solve this little problem...

I've got two tacks at the moment. One is, I've got a Gtkmm front panel, which is returning me a directory and file names. Maybe I can find or build a wiget that will recover more than one filename?

Tack two is that there must be a system command somewhere. How does Bash search for files? Where does the operating system store its file structure?


Any pointers very much appreciated....



Robert

---

### Post by LordHunter317 on 2005-06-27
[QUOTE=robert crowther]Firstly, the Boost package didn't work on my system. It unpacked fine, all libraries seem to be present, but responded with errors when I tried to run any of my programs, and also fails with the supplied example programs.[/quote]Something else is seriously wrong with your system then. Save for boost::python, boost::threads and a few other libraries, all of boost is **compile-time**, not run-time dependencies.  This is because all the code is written with templates, and the code is generated at compile time.  There's generally nothing to link with boost.

> I pointed my program at the headers, but keep getting errors.How?  **No one can help you if you don't post what you did and what error messages you got**.  This is self-help 101.  

> I've never loaded a program with Boost as a dependancy, either,You have, you probably just don't know it.  Like I said, compile-time depenicies.   I don't think I've ever written an non-example C++ program that doesn't use something in boost.

> Tack two is that there must be a system command somewhere. How does Bash search for files? Where does the operating system store its file structure?I umm, named the functions in an eariler post.  Perhaps you shold go back and re-read it, then use apropos, man, and google online for examples using those functions.

They're all standard C functions provided by POSIX.

---

### Post by robert crowther on 2005-06-27
Easy there.

First, can I appologise to Lord Hunter? I was feeling a little snappish after two evenings on this one, and I just didn't read your post fully.Yeah, I know, I should take care online, but my dialup costs a lot of money, and that can get me hasty. Anyway, here's a thankyou, if that's ok. I was completly stuck, and I couldn't have found my way forward without your help.

As for error messages, I'm sorry if I gave the impression I wanted Boost sorting out. I don't. As for using it, I think its pretty valuable that I know what it is, what it provides, and now have an idea what the various libraries can do. Perhaps there will come a time when I, like you, will find it integral to what I do.

I should also have mentioned something else, which is that I am new to computers. What I learned about c++, I learned last week. When you mention POSIX, and whatever else, there's a strong chance I don't know what you are talking about. I've done an awful lot of googling round both your posts trying to pick up the thread.

Before you posted the above, I went back, because it seemed like you two really know what you're talking about, to see what leads I could follow, and saw exactly what you were talking about. I sat right down, googled, wrote the routine, came back on to thank you both for your help... and found I'd upset you some. Again, I can only thank you both, for my now working routine, and my rapidly expanded understanding of compuers.

Yours


Robert

---

### Post by LordHunter317 on 2005-06-27
It's just fustrating when I point people in the right direction, even listing functions to investigate further, and they don't appear to see it.  I understand you didn't see them as you were in a hurry.  But I have no way of knowing that's why.

Also, saying something "doesn't work" without providing any more is something that really irks me, FWIW.  Lots of technical issues could be resolved near instanteously if you just posted the last shell command you ran and the output you got.  It's not personally directed at you, it's just a general fustration of mine.

---

### Post by thumper on 2005-06-29
I'll just add to LordHunder317's comment, when you have a problem it really helps to give more info.  Better to give too much rather than too little.

Eg.
1)  Here is the source that I am trying to compile/run.
2)  This is the command I used to compile it
3)  This is my LD_LIBRARY_PATH when executing
4)  This is the output I get when trying to run it

Tim

---

### Post by LordHunter317 on 2005-06-29
Just to clarify something I left ambiguous before, unless the boost::filesystem libraries don't do what you want, use them if you're writing C++.

opendir() and friends just happen to be the UNIX way to do it.  Only use them if they can provide something boost::filesystem can't, which isn't likely to be anything you need.

---

