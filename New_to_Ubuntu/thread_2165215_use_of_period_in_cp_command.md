---
title: "use of period in cp command"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by anshul001 on 2013-08-03
hello everyone
im a beginner in ubuntu , so to get some idea in command line i've started reading "The Linux Command Line"
while reading i was not able to understand the meaning of period at the end in this command:
[me@linuxbox playground]$ cp /etc/passwd .
without using period it gives :
ansh@ansh-Lenovo-G580:~/playground$ cp /etc/passwd
cp: missing destination file operand after ‘/etc/passwd’
Try 'cp --help' for more information.

can someone tell me the meaning of period at the end and its importance , in simple terms if possible

---

### Post by kevdog on 2013-08-03
. means current working directory
.. (two periods) means one directory higher in the directory tree.  (for example if you were in /home/user,  typing cd .. would move you to /home)

---

### Post by Bucky Ball on 2013-08-03
What are you actually trying to do? If you want to copy the /etc/passwd directory/file to somewhere else, then:

```
sudo cp /etc/passwd /etc/passwd.backup
```

... would create a copy of 'passwd', file or directory, called 'passwd.backup' in the /etc directory. 

No idea about the '.'. Please use code tags for clarity when posting code. You can use the [code] tags or 'Go Advanced', highlight the code and click the hash '#'.

---

### Post by Bucky Ball on 2013-08-03
The end tag would naturally be [/code]. ;)

---

### Post by anshul001 on 2013-08-04
im sorry for not clarifying this properly 
as stated earlier im a beginner in this and this is actually my first post

in the book using this command :
```
[COLOR=#000000][me@linuxbox playground]$ cp /etc/passwd .[/COLOR]
```
he is trying to copy /etc/passwd file in a new directory named "playground"

so i wanted to ask the meaning of period symbol at the end of the command and why it is imp 

and when i tried doing the same thing without using period it gave me this reply in my terminal :
```
[COLOR=#000000]ansh@ansh-Lenovo-G580:~/playground$ cp /etc/passwd[/COLOR]
```
[COLOR=#000000]cp: missing destination file operand after ‘/etc/passwd’[/COLOR]
[COLOR=#000000]Try 'cp --help' for more information.

now am i using the code tags properly ?[/COLOR]

---

### Post by anshul001 on 2013-08-04
* mistake again 
last command was:

```
[COLOR=#000000]ansh@ansh-Lenovo-G580:~/playground$ cp /etc/passwd[/COLOR]
[COLOR=#000000]cp: missing destination file operand after ‘/etc/passwd’[/COLOR]
[COLOR=#000000]Try 'cp --help' for more information.[/COLOR]
```

---

### Post by anshul001 on 2013-08-04
thanks for replying 
but is it imp to use . at the end of cp command for copying?

---

### Post by Bucky Ball on 2013-08-04
Have no idea about the period in this command, or much about the command, if it is intended to copy /etc/passwd file/directory into a new directory named "playground". What happens when you run the command with the period?

```
sudo mkdir/etc/playground
sudo cp /etc/passwd /etc/playground
```

The first command creates the directory 'playground', the second copies 'passwd' to the directory '/etc/playground'.

---

### Post by deadflowr on 2013-08-04
> **anshul001 said:**
> thanks for replying 
but is it imp to use . at the end of cp command for copying?

Only if you want to copy it into the directory your are currently in.:P
The period stands for the current directory or place you're at.
With each additional period moving up the ladder, as it were, until you reach root /.

But when copying, you need to have a place to copy to.
Thus the missing destination.

---

### Post by anshul001 on 2013-08-04
thanks for your help 
using period at the end also copies the file
i just want to know the meaning and importance of period at the end of the command

---

### Post by anshul001 on 2013-08-04
thanks that really helped a lot

---

### Post by kevdog on 2013-08-04
The command syntax is cp (copy) - (file in current directory) to (destination file or directory).  It requires a source and destination
cp /etc/passwd  makes no sense.  It's like saying copy /etc/passwd to ??????.

cp /etc/passwd .  Means copy the /etc/passwd file to a file named passwd in the current directory (where the command is being typed).  . which means the current directory and fulfills the destination requirement of the proper syntax

---

### Post by tgalati4 on 2013-08-04
The period "." can be used in all sorts of commands.  It simply means "here".  Copy this here, move this file here, executed this file from here.  To run a script file, you need to add execute privileges and then run it from "here":

```
sudo chmod +x mycustomscript.sh
./mycustomscript.sh
```

cd ../../../.. will take you up 4 directories from your current location.

Pay attention to the following differences:

```
cd
cd .
cd ..
```

The first takes you back to your "home" directory from wherever you are.  The second takes you "here", which is where you already are.  The third takes you up one directory.

tgalati4@Mint14-Extensa ~ $ cd
tgalati4@Mint14-Extensa ~ $ cd Desktop/
tgalati4@Mint14-Extensa ~/Desktop $ cd .
tgalati4@Mint14-Extensa ~/Desktop $ cd
tgalati4@Mint14-Extensa ~ $ cd Desktop
tgalati4@Mint14-Extensa ~/Desktop $ cd ..
tgalati4@Mint14-Extensa ~ $ 

The period shows the power of doing nothing in Linux.

---

### Post by ebyeby6 on 2013-08-04
anshul001, also as a general tip, if you type "man" (stands for manual I think) in front of any command you want help on, you will get a lot of information that way. eg:

```

man cp

gives this info

CP(1)                             User Commands                            CP(1)

NAME
       cp - copy files and directories

SYNOPSIS
       cp [OPTION]... [-T] SOURCE DEST
       cp [OPTION]... SOURCE... DIRECTORY
       cp [OPTION]... -t DIRECTORY SOURCE...

DESCRIPTION
       Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

```

From that you can see the the dot is just the DEST (destination) parameter of the copy command.
Once you get used to the way the information is presented by the man command, it's *really* helpful!

---

### Post by anshul001 on 2013-08-05
thanks everyone for helping 
i think im starting to get the hang of things in ubuntu command line

---

