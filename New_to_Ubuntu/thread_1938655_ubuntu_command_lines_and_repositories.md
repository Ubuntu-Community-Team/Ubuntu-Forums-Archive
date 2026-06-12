---
title: "ubuntu command lines and repositories?"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by goodgriefpenfold on 2012-03-10
Good Morning,

I'm really sorry for asking this but I have just come from Windows. I'm really enjoying Ubuntu but i get confused by a lot of the references and terminolgy. I am absoulutely certain this will have been asked before but what are repositries and what is all the command line terminolgogy and how can i use it? Also where can i learn more about it?

Regards

goodgriefpenfold

---

### Post by arpanaut on 2012-03-10
this will get you started with the CLI: [http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

For repositories:  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Good Luck

---

### Post by Megaptera on 2012-03-10
Something else to help with Command Line (quote) "CLI Companion is a tool to store and run Terminal commands from a GUI. People unfamiliar with the Terminal will find CLI Companion a useful way to become acquainted with the Terminal and unlock its potential. Experienced users can use CLI Companion to store their extensive list of commands in a searchable list." Here: [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

---

### Post by audiomick on 2012-03-10
Just a couple of comments...
Don't panic too much about the command line stuff. It is good to know how to use the terminal, there are a number of things that are easier/simpler/quicker/more efficient when done using commands, but on the other hand, there is a graphic tool on Ubuntu for pretty much anything you might need to do during normal use of the computer. I tend to do things using the Graphical Interface, mainly because I can't remember commands for the life of me... ;)

If you ask for help, and only get a quick reply containing some cryptic command, try asking again to see if there is a GUI (Graphical User Interface) way to do it, i.e. something where you point at it with the mouse and click on something. This not to say that you shouldn't try to learn how to use the terminal. You should. It is a great tool. It is just not the only way to do most things, and maybe you don't always need to go that way.

Practically all commands have a man page. They are often very cryptic, short, and seem to assume that you actually already know whatever it is you are reading the man page to find out. I strongly suggest looking at these. With a bit of practice, you come to be able to understand quite a lot, and deduce quite a lot more.
You get to the man pages from the terminal, using the command
```
man <name_of_command>
```

For instance, confronted with the command
```
sudo shutdown -P now
```
which turns off the computer, you can find out what the parts of the command do with
```
man sudo
```
to read about "sudo"
and
```
man shutdown
```
to read about what the command "shutdown" does, and what the -P and the now after the command mean.

---

### Post by forrestcupp on 2012-03-10
One thing you should know is that these days, the average user can do about anything you could possibly want by using the GUI. The average user doesn't really ever even have to use the command line, unless they are following directions given to them.

But if you really have a desire to learn it, check out the link previously mentioned. And since you're new at this, CLI means Command Line Interface.

Edit: audiomick ninja'd me about the doing things the graphical way. :)

---

### Post by goodgriefpenfold on 2012-03-10
Thanks ever so much for the replies. Quite humbled by you all taking the time. 

Kindest Regards

---

