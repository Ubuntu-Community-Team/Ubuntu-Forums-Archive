---
title: "[SOLVED] Problem with running programs compiled in g++"
date: 2007-09-20
forum: Programming Talk
---

### Post by Jakk64 on 2007-09-20
I just installed g++ through the synaptic package manager and it's letting me compile the source into an exe, but when i click on the exe it doesn't do a thing, is there something I am missing here?
Thanks for any help.

---

### Post by cdenley on 2007-09-20
What are you compiling? Does it have a gui? If you run it from the command line, what is the output?

---

### Post by Jakk64 on 2007-09-20
i've been trying the exec command to run it, im new to the terminal so i don't know if this is the correct command, but it says that the file cant be found, and im just trying a simple hello world code to try get the compiler working

---

### Post by aks44 on 2007-09-20
> **Jakk64 said:**
> i've been trying the exec command to run it, im new to the terminal so i don't know if this is the correct command, but it says that the file cant be found, and im just trying a simple hello world code to try get the compiler working

```
$ g++ hello.cpp -o hello
$ ./hello
```

---

### Post by Jakk64 on 2007-09-20
Ah thanks a bunch! Now i can at least get it running from the terminal, but is there something I'm missing which is stopping the program from running from the desktop?

---

### Post by Lord Illidan on 2007-09-20
Not at all. Just navigate to that directory, and double click on the hello file. Then, select Run in Terminal.

EDIT : If you use an IDE like Geany, it can be quite helpful..

---

### Post by Jakk64 on 2007-09-20
ive set the option on the programs properties to open with gnome terminal, but it still wont open when i click it :S

---

### Post by Lord Illidan on 2007-09-20
What happens when you just double click it?

Bah, my mistake...It doesn't work, because it just flashes past too quickly. If you had something that required input, you might see it..

---

### Post by psusi on 2007-09-20
Normally when the shell runs commands, it forks them into a child process, so you can run multiple commands at once, and hit ctrl-c to kill them, or ctrl-z to background the one in the foreground and return to the shell, with it suspended until you choose to either switch it back to the foreground or allow it to run in the background using the fg and bg commands respectively.  

The exec command tells the shell to directly execute the new program without forking.  Once that program ends, there is no shell to return to.  If you open a terminal window and exec ls, you will see the directory listing for a split second then the window will close because there is no longer any shell running in it.  

It is useful sometimes to save a bit of memory by getting rid of the shell you don't plan on using anymore, for instance, if you intend to ssh to another machine, you can exec ssh and then when you end your ssh session, the window will close rather than returning to the shell for you to exit from.

---

### Post by Jakk64 on 2007-09-20
I changed the code to something that required input, however when i tried to open it without the terminal i'm getting nothing, if there was a flash I would assume that i would need something in the code to keep it up, but this seems like i don't have a privilege to open it or something :S

---

### Post by gnusci on 2007-09-20
Why don't you just open a terminal and run it with the simply command line like this:

**> ./hello**

But open the terminal and move to the directory with the program, use **cd** to change the directory, such as:

**> cd /home/Jakk64/hello**

where [COLOR="Red"]Jakk64[/COLOR] it your user name or whatever you using and  [COLOR="Red"]/hello[/COLOR] is the directory where the program is, and then just tripe the instruction above.

---

### Post by Jakk64 on 2007-09-20
Yea, ive used that and it works, when i use my account with the right privileges :P. But if i cant access it from the destop by clicking it, something must be wrong, right? Or am i just being too paranoid.

---

### Post by Lord Illidan on 2007-09-20
I've got a nice solution. It needs some tinkering though.

First, from synaptic or apt-get, install nautilus-actions

```
sudo apt-get install nautilus-actions
```Once that is done, I want you to create a little script. Save it in a directory, and make sure you don't move it around, or else put it in /usr/bin.

So, I would do it like this :

sudo gedit /usr/bin/runinterminal.sh

And copy the following code there. Then, save and quit.

```

#!/usr/bin/env bash


$1
echo "

------------------
(program exited with code: $?)"         


echo "Press return to continue"
#to be more compatible with shells like dash
dummy_var=""
read dummy_var
```After that type : ```
sudo chmod +x /usr/bin/runinterminal.sh
``` so that it has execute permissions.


Now, open System -> Preferences -> Nautilus Actions, and click Add.

I provided this screenshot. You can just copy the whole thing..The LABEL can be anything you want, though.

The path is : gnome-terminal -x runinterminal.sh
The parameters are : %d/%f

Let me know how this goes.

---

### Post by Jakk64 on 2007-09-20
Thank you! i just finished adding it and now i can get them working without having to load up the terminal, thanks a bunch!

---

### Post by Lord Illidan on 2007-09-20
> **Jakk64 said:**
> Thank you! i just finished adding it and now i can get them working without having to load up the terminal, thanks a bunch!

Great! You should experiment with these simple scripts, they can save loads of time.. In the meantime, can you mark this as SOLVED then..since your problem has apparently been solved, no?

---

### Post by dwhitney67 on 2007-09-21
Consider composing a script to launch the program.  For instance:
```
#!/bin/sh

./a.out

echo "press any key to exit."
read ans
```
Ensure that the script is executable:

[FONT="Courier New"]$ chmod u+x script.sh[/FONT]

Now you can double-click on the script, and when prompted, select "Run in Terminal".

---

### Post by Lord Illidan on 2007-09-21
The problem with that is that it requires you to only use one executable a.out or else keep editing the script.

Otherwise what you could do is at the end of every program, add a line requesting a dummy input (like pressing enter). I remember that when I used to do Turbo Pascal at school, we used to end every program with a "readln;" so that it would pause before exiting. Otherwise it would exit too quickly.

---

