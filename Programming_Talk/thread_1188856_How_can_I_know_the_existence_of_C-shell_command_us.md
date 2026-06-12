---
title: "How can I know the existence of C-shell command using TCL script ?"
date: 2009-06-16
forum: Programming Talk
---

### Post by tusharv on 2009-06-16
Hi All,

I am working with TCL/TK.
In TCL, How can I know the existence of any C-shell command ?

Suppose there is command called "awk" in C-shell.
Now if this command does not exist in some other machine, then how can I come to know about that in TCL ?

Thanks,
Tushar

---

### Post by stevescripts on 2009-06-16
Tushar,

Personally, I would only count on the existance of awk on unix/linux like systems, and would simply check the contents of $tcl_platform(platform).

Otherwise, why not just catch the result of executing a simple awk script in a variable, and check the contents of the variable.

Hope this answers your question.

Steve

---

### Post by soltanis on 2009-06-16
Generally speaking, most UNIX systems have a Kernighan-compliant awk. If they don't, they're broken.

---

### Post by tusharv on 2009-06-17
> **soltanis said:**
> Generally speaking, most UNIX systems have a Kernighan-compliant awk. If they don't, they're broken.

Hi,

I am giving just an example of "awk" command.
Suppose I have installed one software and using its command in the TCL script. Now if I try to run this script to another PC where that particular software is not installed then this script will give the Error ... 
So How can I make sure that If the software installed then only execute that command otherwise give the error message.

Like I have installed mplayer in my machine and using mplayer command in tcl script. Now If I try to run this command in another PC then It will give the Error as mplayer is not installed in it. So How can I decide whether the command exists or not. if exists then only run the command otherwise not.

Thanks,
Tusharv

---

### Post by stevescripts on 2009-06-18
Tushar,

Well, we could go into a bit of detail on how to check for executables, but let me ask, would you rather learn how to check, or how to create a single-file executable, that wraps(includes, say mplayer), so that you could run it on computers that don't have mplayer installed?

Steve

---

### Post by tusharv on 2009-06-19
> **stevescripts said:**
> Tushar,

Well, we could go into a bit of detail on how to check for executables, but let me ask, would you rather learn how to check, or how to create a single-file executable, that wraps(includes, say mplayer), so that you could run it on computers that don't have mplayer installed?

Steve

Steve,

I want to create a single file executable that includes the mplayer command, that should run in all system regardless the mplayer installation. If mplayer is installed in particular system then it will run the command and if the mplayer is not installed then it should give the error message and execute the next lines of code. Means I want to check the existence of the mplayer command in the system.

Thanks,
Tusharv

---

### Post by tusharv on 2009-06-23
> Steve,

I want to create a single file executable that includes the mplayer command, that should run in all system regardless the mplayer installation. If mplayer is installed in particular system then it will run the command and if the mplayer is not installed then it should give the error message and execute the next lines of code. Means I want to check the existence of the mplayer command in the system.

Thanks,
Tusharv 


No any idea ???

Isn't it possible in TCL ?

---

### Post by stevescripts on 2009-06-23
Tusharv,

We are having a "*failure to communicate*" here at some level ...

1. If you have a script that does what you want, with the exception of
handling the lack of an mplayer install, please post the code, and I will try to show you how to handle the error.

2. If you want to learn how to deliver a single-file executable, that
**includes** the mplayer executable, I will try to show you how to do so.

Steve

---

### Post by tusharv on 2009-06-24
> 1. If you have a script that does what you want, with the exception of
handling the lack of an mplayer install, please post the code, and I will try to show you how to handle the error.

Steve,

Here I have written a small script, that includes mplayer command.
```
#!/usr/bin/tclsh

puts "Starting Mplayer"
exec mplayer
puts "Mplayer executed."
```

This script will be executed if the mplayer is installed in system otherwise it will give **following** error and the execution will be terminated.
Error : ```
Starting Mplayer
couldn't execute "mplayer": no such file or directory
    while executing
"exec mplayer"
    (file "./mplayer.tcl" line 4)

```

So How can I bypass the mplayer command if it is not installed in system ?

Thanks,
Tusharv

---

### Post by stevescripts on 2009-06-24
Tusharv,

It is usually a good idea, if you are going to exec an external program, to do so in the background.

Does this basically do what you want?

```

#! /usr/bin/tclsh

catch {exec mplayer &} res

if {![string is integer -strict $res]} {
puts "No mplayer installed on this computer!"
}

```

You could continue your script to do something else, after determining no mplayer is installed.  (NOTE: if mplayer is installed, the variable res will contain the PID)

Hope this helps.

Steve

---

### Post by tusharv on 2009-06-26
yes steve,

it helps lot thanks,
Tusharv

---

