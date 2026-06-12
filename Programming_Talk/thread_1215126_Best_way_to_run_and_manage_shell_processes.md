---
title: "Best way to run and manage shell processes"
date: 2009-07-16
forum: Programming Talk
---

### Post by master_kernel on 2009-07-16
I was thinking about converting the BASH script I use in KernelCheck to Perl, since it has to read from a configuration file and backquotes aren't really the safest way to get shell output. What it currently does is it runs some tasks, gets the retcode of each command and aborts if it isn't zero.

I was reading *Learning Perl* and I came across the processes section. Which, in your opinion, is the best way to run/manage processes in a script? The processes are run consecutively, and I don't really like spawning off grandchildren and great-grandchildren off of a process.

---

### Post by JordyD on 2009-07-16
I voted bash because you can just use bg, fg and jobs. Very easy and simple.

I wouldn't put much faith in my vote though. I've never used Perl and never managed processes with Python. :D

---

### Post by ahmatti on 2009-07-17
Python has the subprocess module that gives you a lot of options for this. I really like KernelCheck so hopefully you'll find a good solution!

---

### Post by c0mput3r_n3rD on 2009-07-17
I voted BASH because it's easy to handle your processes from the terminal.

---

### Post by lavinog on 2009-07-17
> **master_kernel said:**
>  since it has to read from a configuration file and backquotes aren't really the safest way to get shell output. 

Can't you change the backquotes to the $(command) format?

---

### Post by master_kernel on 2009-07-17
> **lavinog said:**
> Can't you change the backquotes to the $(command) format?

It's still tough; I remember having trouble even when I did that. It kept trying to run whatever was inside it. Ex: I would do VAR=$(echo hi) and it would come up with a bash error saying it can't find the 'hi' command instead of assigning the output to the variable.

---

### Post by JordyD on 2009-07-17
> **master_kernel said:**
> It's still tough; I remember having trouble even when I did that. It kept trying to run whatever was inside it. Ex: I would do VAR=$(echo hi) and it would come up with a bash error saying it can't find the 'hi' command instead of assigning the output to the variable.

Perhaps it's not in the assignment, but what happens later? Of course this example could be one that happened to work well.
```
jordy@centurion:~$ VAR=$(echo hi)
jordy@centurion:~$ $VAR
The program 'hi' is currently not installed.  You can install it by typing:
sudo apt-get install hmake
bash: hi: command not found
jordy@centurion:~$ echo $VAR
hi
jordy@centurion:~$ 

```

---

### Post by lavinog on 2009-07-17
> **master_kernel said:**
> I was thinking about converting the BASH script I use in KernelCheck to Perl, since it has to read from a configuration file and backquotes aren't really the safest way to get shell output. What it currently does is it runs some tasks, gets the retcode of each command and aborts if it isn't zero.

I was reading *Learning Perl* and I came across the processes section. Which, in your opinion, is the best way to run/manage processes in a script? The processes are run consecutively, and I don't really like spawning off grandchildren and great-grandchildren off of a process.

I only found one file that was a bash script in your source. Everything else was python. Why wouldn't you stick with python?
I don't think there would really be any advantage either way.
Nice program though.

---

### Post by master_kernel on 2009-07-18
> **lavinog said:**
> I only found one file that was a bash script in your source. Everything else was python. Why wouldn't you stick with python?
I don't think there would really be any advantage either way.
Nice program though.
That bash script is all that's left of KernelCheck 1.0.0. I used it back when I didn't really know a lot of Python, and it just became kind of native. I'll wait for the results of this poll to decide whether I'll keep it or not.

---

