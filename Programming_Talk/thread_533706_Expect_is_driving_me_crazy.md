---
title: "Expect is driving me crazy"
date: 2007-08-24
forum: Programming Talk
---

### Post by eentonig on 2007-08-24
Can anybody give me some good pointers or easy, yet extensive, tutorials for expect?

[COLOR="Red"]**What I need:**[/COLOR]
I have a list of devices (routers) which do not all have the same passwords.
I regularly need to:
 - Update configuration on all of those routers.
 - Do some repetitive troubleshooting and export that to a file.

[COLOR="Red"]**What I want:**[/COLOR]

I want to write a script that does the following.

I run the script with a list of hostnames as parameters (or input them from a file). The script should then  lookup the corresponding login credentials for that hostname(s) in the specified file, login to the device, perform some commands and output the result of [some|the] commands to another file.

[COLOR="Red"]**What would be totally awsome:**[/COLOR]
If I could easily use allow for flexibility by having the script to ask for 2 files.
- 1. File with input which hostnames to work on
(- 2. File which lists the commands to perform for this run.)

---

### Post by A3sthetix on 2007-08-24
What did you Expect!? (I know, I know... it's lame, but I had to)

Do you have any experience programming in Python? You could setup a Python script to do this. There's a ton of tutorials online. The script can make a text screen pop-up and prompt you:

Press 1 to select a command
Press 2 to select a hostname
Press R to run

---

### Post by eentonig on 2007-08-24
I need several commands to run. And the same list of commands against several host.

And i did 'Expect' to have a hard time. Just not this hard. I'm having difficulties in getting a grasp on the commandline syntax that expect expects (sigh). I don't get how to declare variable, redirect output to a file, etc...

I'm not a bright light in programming. But declaring variables, redirecting input and  output are things that I usually get by looking at examples. But when I follow the examples I find, I just get slammed around the head with error messages.

---

### Post by pmasiar on 2007-08-24
> **eentonig said:**
>  I'm having difficulties in getting a grasp on the commandline syntax that expect expects (sigh). I don't get how to declare variable, redirect output to a file, etc...

I don't want to learn yet another scripting language to script yet another tasks. That's why I learned Python, which is universal programming language, and can script it all (and do other things).

Using python, I would generate scripts (with server name, password, and commands to execute), and then execute them using os module: [http://docs.python.org/modindex.html](http://docs.python.org/modindex.html)

---

### Post by A3sthetix on 2007-08-24
I'm not too familiar with Expect, but from what I read, it's more just to run a bunch of simple terminal type commands. I don't think handling variables is its thing. I have a Windows background... I know .BAT file programming is a pain in the teester. That's why I loved C++.

I really think you should try your hand at Python scripting. You might have an easier time.

---

### Post by apetresc on 2007-08-24
> **A3sthetix said:**
> I'm not too familiar with Expect, but from what I read, it's more just to run a bunch of simple terminal type commands. I don't think handling variables is its thing.
Actually, Expect is just an extension of the Tcl language; it can do *anything* Tcl can do. It's just a package on top of it. And Tcl can do quite a lot, it's a powerful language.

To answer the OP, Expect is woefully undocumented online, but there is an excellent book about it "Exploring Expect", which is FULLY AVAILABLE through Google Books, just do a google search on the title. Gotta love Google Books :)

Anyway, good luck with your app! Once you get the hang of it, Expect is super-handy and super-powerful.

---

### Post by eentonig on 2007-08-26
Ah, thanks AdrianP.

---

### Post by eentonig on 2007-08-26
Hmmm. Apparently, it's not fully available. But only large parts.

---

