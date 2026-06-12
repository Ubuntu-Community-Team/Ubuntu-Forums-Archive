---
title: "C compiler - problems using Geany"
date: 2008-05-15
forum: Packaging and Compiling Programs
---

### Post by TekNullOG on 2008-05-15
I am really new to programming so my questions may sound really stupid but any help would be appreciated.

I have a summer class where I am learning C. Obviously everyone is using Windows in class but I decided I would try to keep up using my Ubuntu laptop.

I started using Geany for writing my code because you can apparently easily compile and execute your code from within the program. Makes it easy for testing and is super similar to what my class mates are using in Windows.

Geany manages to compile a small program without errors but when I go to execute it, nothing happens.

I imagine that 2 solutions are possible.

Either I could try to get Geany to work or I could learn how to do it in a Terminal Window.

I would appreciate any help possible since I am falling behind in my school work.

Please try to be the most descriptive possible since I am really new to this.

Thanks in advance

---

### Post by g2g591 on 2008-05-15
usually small programs only produce output if ran from a terminal window because they dont have any gui. just go to where you put the program and run ./programname (or run /whre/it/is/program

---

### Post by TekNullOG on 2008-05-15
thanks for the help

I tried what you told me but I get an error. I even ran the command as root to avoid any permission problems.

> 
seance02# ./exemple.o
bash: ./exemple.o: Permission denied


I then checked if I had permission to execute the file.

> 
-rwxr-xr-x 1 alex alex   1370 2008-05-08 20:13 exemple.c
-rwxr-xr-x 1 alex alex   1260 2008-05-15 12:47 exemple.o


My program is written in exemple.c. When I compile, it creates exemple.o which I imagine is what I am suppose to try to run.

Am I missing something? 

Sorry for all this beginner programming stuff. I hope that once I advance in my various classes I'll be able to eventually give back to the community too.

---

### Post by TekNullOG on 2008-05-15
I found why Geany is not executing the program once i compiled it. 

It gives me this error message: "Failed to execute the terminal program"

I don't quite understand the message. Is it failing to find or execute the the terminal or to execute the program in the terminal?

Anyways, I am trying to supply the most information possible as I search for possible solutions myself. Hope this helps a little

---

### Post by LaRoza on 2008-05-15
> **eightinches said:**
> 
My program is written in exemple.c. When I compile, it creates exemple.o which I imagine is what I am suppose to try to run.

Am I missing something? 

Sorry for all this beginner programming stuff. I hope that once I advance in my various classes I'll be able to eventually give back to the community too.

Yes, that is the object file. It isn't linked.

See the sticky in the programming talk for how to compile and run C programs.

---

### Post by TekNullOG on 2008-05-16
Thanks for the help. gcc works great.

Fun command line tool!

---

### Post by cyrus_smith on 2008-06-03
Please i am having the very same problem ?? 
can u advice me to what have u done to over come this problem??

---

### Post by jtrindle on 2008-06-04
It says that when you try to execute a module that doesn't have "main" in it.  I don't think geany is out-of-the-box capable of handling multiple source files in a project.... you need to create a makefile.

It's failing to execute the program *in* the terminal, not the terminal.  This is because build by default just does

gcc -o filename filename.c

and filename.c won't link by itself unless it contains main.

---

### Post by Tzetko on 2008-06-18
Just to elaborate a bit. My first useful post, whoopy!!

You don't have to run gcc from terminal.
When Geany compiles the source file it uses the following command:

gcc -Wall -c source.c

So if you click Compile it executes this command.
The -c option explicitly says to gcc not to link the file.

However if you click Build it executes gcc without -c and so it links.
You can change the command under Build->Set Includes and Arguments. 
So in this case, no -c good, -c bad.

---

### Post by cerubim on 2009-02-10
Easiest would be to use Build -> Build (F9) and then Build -> Execute (F5).

---

### Post by Killkyo on 2010-06-05
Thank you, Thank you, Thank you! F9 F5 works perfectly.:KS

---

