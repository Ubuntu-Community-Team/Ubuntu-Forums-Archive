---
title: "Learn shell scripting"
date: 2009-07-22
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-22
Could someone please explain a little about what shell is,what is use of scripting.
Are these used in commercial applications?
Are they like c or require languages like perl?
And some good places or books for starters?

---

### Post by akimatsu123 on 2009-07-22
the shell is a CUI (Character User Interface) that allows the user to interact with the system via text commands. an advanced shell like bash, csh, ksh, etc allows a user to write scripts to run repeated tasks. shell scripts aren't "programs" in that they are not executable machine code. it's a "script" that a shell can interpret, much like how you write html/javascript for your browser to interpret/execute. 

the most common shell in ubuntu is BASH. [Here]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html") is a good link to get you started. 

There are also other types of shells, for example if you want a more C-like script, then you can use csh/tcsh. Google is your friend.

---

### Post by kpkeerthi on 2009-07-22
I find [Learning the Bash Shell]("http://www.amazon.com/Learning-bash-Shell-Programming-Nutshell/dp/0596009658/ref=sr_1_1?ie=UTF8&s=books&qid=1248253597&sr=1-1") excellent for beginners.

[Classic Shell Scripting]("http://www.amazon.com/Classic-Shell-Scripting-Arnold-Robbins/dp/0596005954/ref=sr_1_1?ie=UTF8&s=books&qid=1248253648&sr=1-1") could serve you well if you are at intermediate/experienced level, but definitely not for beginners.

---

### Post by MindSz on 2009-07-22
shell scripting kind of reminds me of the old '.bat' files windows used to have.

oh my, I feel so outdated. I'm gonna go listen to my walkman now :P

---

### Post by mali2297 on 2009-07-22
Another useful link for absolute beginners:
[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by abhilashm86 on 2009-07-22
shell scripting, in simple words "putting a collection of shell commands into a file" to do a particluar task, what you do on a command line (terminal) is a shell, mostly you use bash
you can use sh, type sh, you go to sh shell, press ctrl-d to return back:) hope it gave some idea......

---

### Post by benj1 on 2009-07-22
the shell is basically what runs in the terminal look in applications-->accessories-->terminal, like DOS (if youre old enough)

scripting technically is just writing a program that is interpretted by another program (eg perl or python) rather than being compiled (like c), although it tends to be used to describe fairly small programs such as a bash (ubuntus default shell) program to arrange or rename a bunch of files.
some scripting languages, such as python can be used for quite large programs, although they tend to run slower (due to being interpreted rather than compiled)so aren't the best thing to use for resource intensive tasks (such as 3d games).

scripting tends not to be used in commercial applications, basically because its much harder to hide your code(a script is just a plain text file), although scripting is much more heavily used in open source apps, and on the internet.

---

