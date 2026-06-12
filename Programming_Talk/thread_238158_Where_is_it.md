---
title: "Where is it?"
date: 2006-08-17
forum: Programming Talk
---

### Post by Langstracht on 2006-08-17
I create a file, edit the file, list the file, look at what's in the file, make it executable ... all without a peep from Linux.  

And yet when I execute it (or at least try to execute it), Linux says it isn't there. 

Anyone any idea how I can access it.

TIA

---

### Post by givré on 2006-08-17
did you try executing it with ./<your file>
When you enter a simple command to bash, it will look at you PATH (ie /bin,/sbin,/usr/bin,/usr/sbin) to see if the file exist. When you want to launch a program from an other directory, you have to say him that the file is in this diectory (./ = your currant directory) or you have to specify the complete path (for exemple /home/<you>/<the file>)

---

### Post by Langstracht on 2006-08-17
Hmmm ... I thought I had and it didn't work.  So!  I tried it again.

This time (maybe last time too) it says "Permission denied".  

So maybe I need to be root?  

But I don't understand, all the other commands work in and on the current (home) directory.  Shouldn't I be able to run a command "for me"?

---

### Post by givré on 2006-08-17
> **Langstracht said:**
> So maybe I need to be root?  
All depend of the emplacement of the file, and the permission you have on it (ls -l <the file> to know it), but i guess yes

> **Langstracht said:**
> But I don't understand, all the other commands work in and on the current (home) directory.  Shouldn't I be able to run a command "for me"?
You don't understand. 
When you launch a command from the terminal, for exemple gedit, it will search the file in your PATH (this is a system variable), the PATH contain all the directory that contain  binary (=executable) file of your system (to see it echo $PATH in a terminal)
so with only one command, you can launch a programm whithout given the full path of the file (/usr/bin/gedit for gedit).
But if you want to launch executable file that are not in the PATH, you have to specify the full path to it.
So if you have a script call myscript.sh in /home/me/ you have to launch it
via /home/me/myscript.sh or if you are in /home/me, you can simply launch ./myscript.sh since ./ will be equivalent to /home/me/ (current directory)

You can also edit your PATH to contain more directory, for exemple create a bin directoy in your home and add /home/<you>/bin to the PATH will allow you to launch every script/programm of the directory with a simple command, but that's an other story. :cool:

---

### Post by Langstracht on 2006-08-17
You're right.  I really DON'T understand.  But I hope to before too, too long.

I should have thought to do the ls thing b4.  Having done so I found that the "permission denied" thingy was because the "x" didn't take and the file was not executable.

Having rectified that (and verified it) it does indeed work "as advertised". 

Appreciate your help.

---

