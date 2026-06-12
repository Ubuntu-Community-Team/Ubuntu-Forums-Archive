---
title: "Batch files"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by jwn-2 on 2014-02-26
Questions:

1) What is the ubuntu equavalent of a windows batch file (file.bat), and how do you create it?

2) Where can I find a list of commands/instructions/programs that can be used in such a ¨batch file¨?

---

### Post by slickymaster on 2014-02-26
You need to learn to write bash scripts. These are the Linux equivalent of windows batch files.

There's a lot of material available for you to start, and the following are just a random selection:
[Advanced Bash-Scripting Guide]("http://www.tldp.org/LDP/abs/html/index.html")
[BASH Programming - Introduction HOW-TO]("http://www.linuxdoc.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
[Linux - Learning the shell]("http://linuxcommand.org/learning_the_shell.php")
[Bash FAQ - Greg's Wiki]("http://mywiki.wooledge.org/BashFAQ")
[Bash Hackers Wiki Frontpage [Bash Hackers Wiki]]("http://wiki.bash-hackers.org/doku.php")

---

### Post by The Cog on 2014-02-26
Simple questions, but complicated answers.

A text file with commands in it like that is called a script. The name is not important although they are sometimes given a .sh extension (meaning shell). I general the **first line** of such a script file will be
```
#!/bin/sh
```
or 
```
#!/bin/bash
```
which tells the OS to use either the sh or the bash command interpreter to run the script. Other interpreters such as /bin/perl or /bin/python can be invoked instead, for scripts written in other languages. I think (not totally sure) that if not specified the default is to use /bin/sh/ as the interpreter.

These scripts must be marked as executable before they can be executed (this is a property of the file, much like being read-only).
You can create them with a text editor - gedit is probably already on your system and it's rather better than notepad.

As for the commands/instructions that go in such a file, that depends on the language. Assuming you are writing a shell script (sh or bash), there are two aspects. The syntax for writing loops, making decisions (if this then do that etc) is best picked up from a tutorial, google for "bash tutorial".  slickymaster has given a good set of links. These scripts can launch other programs to do things just like bat files. Any of the thousands of commands in /bin and /usr/bin are candidates but some are written especially for use in scripts. The ones most commonly used will crop up in the tutorials, mine are probably grep, sed and sort.

---

### Post by jwn-2 on 2014-02-26
Thanks guys, I will follow that up.

---

