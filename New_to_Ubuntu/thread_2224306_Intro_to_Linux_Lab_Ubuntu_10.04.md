---
title: "Intro to Linux Lab Ubuntu 10.04"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by nyjudodad on 2014-05-15
Hi, I am currently in an intro to Linux class.  We are using Ubuntu 10.04 and I am stuck on a lab problem.  Here are the instructions:  

Create    a script called ***get_dirs***    that lists the directories in a directory, trims off any extra    characters, and stores the data in a file called ***current_dirs***.    Run the script and verify the output. Make an [FONT=Courier New]**alias**[/FONT]    for this command called ***gd***.    Check that the alias works then logout and log back in. Check to see    if the alias is still valid
[SIZE=2]
It is an online class and my instructor is currently unavailable.  Up until this point in class I've been doing well but I can't figure out how to complete the directions in the first sentence.  Can anyone help me out?

Thanks in advance
[/SIZE]

---

### Post by HiImTye on 2014-05-15
here's how I  would find all of the *files* in *every directory* from my current  directory, without using the 'find' command and filter the output:
```
ls -alR | grep -vE '^\.|^total|^$|/$' | awk '{print $9}'
```
this is just one option, but it will give you a good idea of how to get and manipulate the output of 'ls'

if you have any specific questions, I'll be happy to help :)

---

### Post by TheFu on 2014-05-15
I will not do your homework. Sorry.  

Usually the lectures would have mentioned the necessary tools for the solution.   **man** is the go-to command for learning this stuff.  Try **apropos directory** - or use google with appropriate keywords in the search. How to find answers - - WITHOUT ASKING FOR HELP -- seems to be the goal of this exercise.  In the end, the kindest thing I can say is "RTFM."

The O'Reiley book "UNIX Power Tools" might be a help, since you seem to be lacking possible ways to accomplish this task.  As is standard with UNIX/Linux, there are at least 100 different ways to solve this.  The "ABSG" is another, longer way to figure out the answer, but it is online and free.

10.04 Desktop has been out of support over a year now, but this task is nothing that would have changed between Linux in 1994 and today. Still, the class should be taught using supported, LTS releases only.   er ... IMHO.

---

