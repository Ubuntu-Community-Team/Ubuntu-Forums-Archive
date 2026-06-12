---
title: "Learning to program in D"
date: 2008-09-11
forum: Programming Talk
---

### Post by Aeph on 2008-09-11
I've heard good things about the D programming language and am interested in learning. The biggest problem (aside from compiling code when I'm running Windows) is that I have not been able to find any good or even relatively complete tutorials on the subject.

Has anyone found any good way to learn D?

---

### Post by Kadrus on 2008-09-11
Dsource have some nice tutorials and a good community as well.
[http://dsource.org/projects/tutorials/wiki](http://dsource.org/projects/tutorials/wiki)
You might want to purchase this book as well,if you are able
[http://www.apress.com/book/view/1590599608](http://www.apress.com/book/view/1590599608)
The book teaches  you about D and the Tango library.

---

### Post by LaRoza on 2008-09-11
Try my wiki.

---

### Post by Kadrus on 2008-09-11
> **LaRoza said:**
> Try my wiki.
Your wiki links to Dsource as well ;)

---

### Post by Aeph on 2008-09-17
I feel that I'm missing something very simple. I can't compile/run my code (I would assume that D is a compiled language). Not even from the terminal. I'm pretty sure I have the correct packages installed, but it wouldn't work. I have the same problem in Windows. I couldn't even get the Eclipse plug-in to work.

Any advice?

---

### Post by LaRoza on 2008-09-17
> **Aeph said:**
> I feel that I'm missing something very simple. I can't compile/run my code (I would assume that D is a compiled language). Not even from the terminal. I'm pretty sure I have the correct packages installed, but it wouldn't work. I have the same problem in Windows. I couldn't even get the Eclipse plug-in to work.

Any advice?

Tell us what you you did ;)

D is compiled.
("install" is an alias for "sudo aptitude install")
```

~/p$install gdc
[sudo] password for laroza: 
...
~/p$cat p.d
import std.stdio;
 
int main(char[][] args) 
{
    char x;
    writefln("Who are you? ");
    char name[] = readln();
    writefln("Hello %s",name);
    return 0;
}
~/p$gdc p.d
~/p$./a.out
Who are you? 
laroza
Hello laroza
~/p$

```

---

### Post by Aeph on 2008-09-19
Say I put this in the terminal:
```
gdc ~/Desktop/hello.d
```
It doesn't do anything. So I assume there is more that I need to do. However, I don't have any idea what that is.

---

### Post by LaRoza on 2008-09-19
> **Aeph said:**
> 
It doesn't do anything. So I assume there is more that I need to do. However, I don't have any idea what that is.

What do you mean? It shouldn't say anything if it worked. Programs throw errors on errors, not when it worked.

---

### Post by Kadrus on 2008-09-19
I thanked you by accident clicking for the quick reply button.(oops)
Aeph,if the compiler shows no error,that means the program works,and will be outputed to your desktop.

---

### Post by Aeph on 2008-09-19
> **Kadrus said:**
> Aeph,if the compiler shows no error,that means the program works,and will be outputed to your desktop.

Okay, I tried it again, and for some reason it only seems to compile when I cd to the directory first instead of using the entire location name. When I compile with GDC, I get a file called a.out. When I compile in DMD, I get a hello.o file and another called hello. I do not know what to do with any of these files.

---

### Post by LaRoza on 2008-09-19
> **Aeph said:**
> Okay, I tried it again, and for some reason it only seems to compile when I cd to the directory first instead of using the entire location name. When I compile with GDC, I get a file called a.out. When I compile in DMD, I get a hello.o file and another called hello. I do not know what to do with any of these files.

a.out is the default file name for an executable.

```

man gdc

```

My second post shows an entire example of what to do.

---

### Post by Kadrus on 2008-09-19
Aeph,if a.out is outputted to the Desktop,then you can run your program from terminal.
```
./a.out
```
this should show your program.

---

### Post by Aeph on 2008-09-19
Okay, I see. Is there a way to compile it into an executable file (not necessarily .exe)?

---

### Post by LaRoza on 2008-09-19
> **Aeph said:**
> Okay, I see. Is there a way to compile it into an executable file (not necessarily .exe)?

It is compiled to an executable file. It is in the ELF format.

You can specific a name for it, but I suggest you read the man page like I suggested ;)

---

### Post by Kadrus on 2008-09-19
Well you can make a makefile that runs your program through a command.
./programname.
[GNU Make]("http://www.gnu.org/software/make/manual/make.html")

---

