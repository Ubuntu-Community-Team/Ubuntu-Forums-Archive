---
title: "prompt, (not 'command prompt')"
date: 2011-03-05
forum: Programming Talk
---

### Post by jmg158 on 2011-03-05
i was wondering if there was a command that would wait for a button to be pressed, and then automatically move on. 

like for example, consider that I had created a function t() and y(). I was wondering if there was a way that I could prompt for a letter (t or y I suppose) and then by using that single keystroke (I suppose the important part is not-hitting-enter/return) the script would continue running. 

I believe there is something in C but I can't remember it at the moment exactly. Thanks for your help.

---

### Post by lisati on 2011-03-05
The first thing that comes to mind at the moment is getch()

---

### Post by trent.josephsen on 2011-03-05
That works, if there is nothing else in the input stream, and if you're okay with discarding it (and not pausing) when there inevitably is.

Not to say it can't be done -- but it should be done robustly.

---

### Post by foxmuldr on 2011-03-05
> **jmg158 said:**
> i was wondering if there was a command that would wait for a button to be pressed, and then automatically move on. 

like for example, consider that I had created a function t() and y(). I was wondering if there was a way that I could prompt for a letter (t or y I suppose) and then by using that single keystroke (I suppose the important part is not-hitting-enter/return) the script would continue running. 

I believe there is something in C but I can't remember it at the moment exactly. Thanks for your help.

Something like Norton's old Batch Enhancer (be.exe) program in DOS is needed here in Linux. It would provide a simple GUI way to prompt for data, and return it in a file, or as characters in stdin, etc.

Sounds like a project to work on, if such an animal doesn't already exist.  Would be very handy for those ridiculously text-based install scrips we see so often in Linux.

Is there an app like that for Linux?

- Rick C. Hodgin

---

### Post by nvteighen on 2011-03-05
ncurses... it's a C library that allows creating "TUIs" ("Text User Interfaces") and it has lots of bindings for lots of languages. It's more or less a standard library in UNIX and Unix-like OSs, so you don't even have to tell people to install it.

So, if you want to have a prompt that reacts as soon as you type on character in the prompt, that's the best solution.

That's what lisati refers to with int getch(void), which is part of that library. But for making it work like you seem to want, you'd have to set some environment settings with other features of the ncurses library.

Is this what you want?

---

### Post by jmg158 on 2011-03-05
Actually I'm not sure if this is or is not what I was looking for. Let me give an example of the type of functionality I'm looking for. 

I'm looking for a linux command that would prompt the user for a single character response, and then react *according* to that response without needing to press enter. for example...

"would you like to run this script again y/n?" or something similar....

excuse my ignorance here but looking up getch, it seems to be a c command. is there a linux equivalent?

---

### Post by foxmuldr on 2011-03-05
> **jmg158 said:**
> Actually I'm not sure if this is or is not what I was looking for. Let me give an example of the type of functionality I'm looking for. 

I'm looking for a linux command that would prompt the user for a single character response, and then react *according* to that response without needing to press enter. for example...

"would you like to run this script again y/n?" or something similar....

excuse my ignorance here but looking up getch, it seems to be a c command. is there a linux equivalent?

It is a C command using the C library functions. But, there is something like the TinyCC (Tiny C Compiler) which allows you to run uncompiled C code from the command line, meaning you could do something like "tinycc return(getch())" and it would work.

I don't know the exact syntax, and the command may have to be a file with the actual program in it, but it does execute without having the binary from raw source code from the command line.

- Rick C. Hodgin

---

### Post by nvteighen on 2011-03-06
You're confusing the C Standard getchar() with the ncurses getch(). The former will just ask for a character, but needs you to hit enter/return and the latter is customizable.

Now, about "Linux commands" vs. "C commands": if what you want is to write a shell script, then what you need is a shell scripting language. But if what you want is to write a C program, what you want are libraries that give you the functionality you want.

---

### Post by jmg158 on 2011-03-07
yes, I suppose that I could write it in c but I was hoping to just keep writing it in linux because I know so little about it. it looks like my best bet to have something with a quick response would be to write an entirely c program? I can't imagine that writing a shell script that uses tcc to run a c program every time its needed, would be very efficient...

---

### Post by wojox on 2011-03-07
> **jmg158 said:**
> yes, I suppose that I could write it in c but I was hoping to just keep writing it in linux because I know so little about it. it looks like my best bet to have something with a quick response would be to write an entirely c program? I can't imagine that writing a shell script that uses tcc to run a c program every time its needed, would be very efficient...

Write a bash script. That will do what you want.

---

### Post by Vox754 on 2011-03-08
> **jmg158 said:**
> yes, I suppose that I could write it in c but I was hoping to just **keep writing it in linux** because I know so little about it. it looks like my best bet to have something with a quick response would be to write an entirely c program? I can't imagine that writing a shell script that uses tcc to run a c program every time its needed, would be very efficient...

You are making me mad!

Why do you say that you are going to "write it in linux", using "linux commands"?

Linux is not a programming language!!!

Probably you are calling "linux commands" what you type when you open the terminal. The terminal runs the shell, called "Bash".

And then you are mixing the "curses" library (thanks nvteighen), and then "tcc" (thanks foxmuldr), that has nothing to do with your problem!

What you want is a way to automate a set of responses, for this you can use "expect", which is sort of an extension to the Tcl language.

With "expect", you literally expect a string, such as "would you like to run this script again y/n?" and provide it automatically an answer.

That is, you prepare a script that expects several questions, and provide it with the answers.

Read on "Tcl expect": [http://wiki.tcl.tk/201](http://wiki.tcl.tk/201)

```

#!/usr/bin/expect --
set timeout 30
spawn /usr/local/bin/scp -P 36000 user@ip:/data/myfile  /data1
expect {           
    "password:" {
        send "password\r"
    } "yes/no)?" {
        send "yes\r"
        set timeout -1
    } timeout {
        exit
    } eof {
        exit
    }
}

```

---

### Post by jmg158 on 2011-03-10
okay, well haha as the original post said, I'm completely new to this so I'm so sorry for "making you mad"

anyway, I looked into it and it turns out to be very simple. 

-n determines the amount of characters in the prompt before it returns.

read -p "What song: " -n 1 input

That's what I'm using and it works pretty well so far.

---

