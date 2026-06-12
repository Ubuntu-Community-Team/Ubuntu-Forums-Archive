---
title: "new user"
date: 2021-04-06
forum: New to Ubuntu
---

### Post by codeman2500 on 2021-04-06
Hi name is cody I am new to Ubuntu well linux in general anyone have any advice to learn it or understand all the commands.

thanks

---

### Post by Bashing-om on 2021-04-06
codeman2500; Hello - Welcome to Linux in general and Ubuntu in particular :D

As you may  be aware the transition from one operating system to the use of another can be daunting; but, it is not difficult.

As a place to start may I suggest that you read the "stickies" within this forum. There are loads of tutorials - Google is your friend - available. The trick is to differentiate what is now relevant. Ubuntu is developed rapidly and as such may be a fast moving target; old info may no longer apply to the current desk top environment. We do evolve with technology.

Just use the system - basically we have become very user intuitive - when you look under the hood we are here to assist :)

Your own curiosity will be your best guide. The operating system comes with the "Manual". At the terminal execute command:
```

man man

``` that introduces one to the linux world.
You will find the link "PopularPages" in my sig of great help.

[INDENT]My bit to try to help
[/INDENT]

---

### Post by yancek on 2021-04-07
THe Ubuntu documentation at the site linked below is a good starting point.

 [https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)

---

### Post by poorguy on 2021-04-07
A good resource.

[https://linuxjourney.com/](https://linuxjourney.com/)

---

### Post by TheFu on 2021-04-07
> **codeman2500 said:**
> Hi name is cody I am new to Ubuntu well linux in general anyone have any advice to learn it or understand all the commands.

Excellent advice.

There isn't any way to learn and know all the commands.  We need to learn to search for commands and read the local manual pages, which spell out in detail what each command was intended to accomplish, options, inputs, and outputs.

There are free online courses, free youtube videos, free books, local Linux groups, paid classes of all sorts, and online support tools to help understand what commands, options, inputs will do.

If you want to be a typical home users, then you can learn as you go.  Use ubuntu daily, as much as possible.  More time is better. When you don't know how to accomplish some task, figure that out. Ask for help - specify the end goal in the question, not what you think are the steps. Explain what you've tried already, in detail.

If you want to be an admin, then start with the basics.  Learn multi-user systems, users, groups, permissions, processes, process management, how to connect to other systems (ssh), run remote commands, modify settings on local and remote systems, and don't use a GUI for any of these things. Unix/Linux Admins barely use the GUI.

If you want to be a programmer, then learn to be a lite-admin, permissions and simple process management, but also learn the language(s) you plan to program using.

[https://explainshell.com/](https://explainshell.com/) - enter commands with options, etc. and it will pull up manpage entries.
All the long-time Linux users get asked the same question a few times a month. When I was teaching free Linux skills sessions at a local University, I wrote this article: [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

---

### Post by ActionParsnip on 2021-04-07
Just use the OS. Most likely the same way you learned how to use Windows....yes? Do that

---

### Post by equi000 on 2021-04-09
I switched from Windows to Ubuntu/Linux about a year ago. I have known Unix some 25 years ago, so I did not remember a lot, just a little about the shell and a few basic commands for file handling.

But I was surprised how seldom you need to use the shell for typical user tasks meanwhile.
In fact I got my Ubuntu running well, with printer, scanner, NAS, camera, lots of audio/video applications ... typing no more than a dozen command-&#8222;lines&#8220; in the terminal. Everything else works fine with the graphical UI - almost like in Windows. The tricky thing is to find these few commands to setup some specific thing that does not work out of the box. Sometimes you need to install some additional package. This takes some time for searching and some trying.

Certainly by using the shell you can do some jobs faster, some things you can not do graphically at all ... but for most of the time for a &#8222;normal&#8220; user this is not necessary.

Usually you do not need to remember many commands. Use the search to find the solution for many typical tasks.
For example: 
- I had to mount an additional Windows partition... Can easily looked up how to do.
- I wanted to mount my FritzBox NAS... Can easily looked up how to do. However you need to know how to install Samba... Can be looked up.
- Had to install a printer driver... complete install package was available from the printer homepage. Just had to start the batch file.

One thing you need to know: what &#8222;sudo&#8220; means!

In short: I do not know any of these commands and their parameters from memory - but my Ubuntu is doing the job very well ;-)
I always have a big smile in my face, when Ubuntu starts up 5 times faster than Windows, and shuts down in 1 second.

---

### Post by The Cog on 2021-04-09
> **poorguy said:**
> A good resource.
[https://linuxjourney.com/](https://linuxjourney.com/)
That's a nice gentle lightweight intro - for some reason I have not come accross that site before.

One thing I would add. Remember that your home directory (/home/username) is your normal habitat and playground. Outside of that home directory there be dragons. You need to use sudo (run as administrator) to change almost anything, and a good number of things can be bad to touch so take extra care. Try to get used to the idea that you operate either as a normal user inside your home, or as a sysadmin when you are outside your home. 

Don't try to learn it all - it can't be done. Learn what you must to be able to get things done, and what interests you. Last week I learned that Ctrl-W deletes the word left of the cursor on the command line. Combined with up arrow to repeat the last command, wow that's useful. But it took me 20+ years to discover that, and I'm not bitter just still learning.

Oh, and get used to using highlight the middle-click to copy and paste text. It's quicker than normal copy/paste and when you get used to it you can use both They have different buffers so you can combine whan you need to copy/paste two differnet bits of text.

Good luck and happy learning.

---

### Post by TheFu on 2021-04-09
Everyone has gaps in their knowledge.  Old guys too.  I'd been moving ssh public keys around the hard way for 15 yrs before someone asked why I wasn't using **ssh-copy-id**?  All the kids knew about it - most of the "old guys" didn't.

And don't get me started about when **sort -h** got added.  I didn't know about the -h option being added to many GNU tools. Changed my world, completely. 
```
$ du -sh *|sort -h
0       run
4.0K    crash
4.0K    local
4.0K    mail
4.0K    metrics
4.0K    opt
20K     tmp
612K    www
1.1M    snap
5.8M    backups
6.4M    spool
274M    log
1.4G    lib
1.7G    cache
```
See that?  It knows that 1G is larger than 274M and 612K!

I just worked through all the questions for the [https://linuxjourney.com/](https://linuxjourney.com/) site - all of them.  Seems reasonable to start out, even good.  Nothing in depth, but a good survey of different parts of a Unix/Linux system.  Though the **cat** and **tar** parts aren't what I'd say.  They should spend time on useful commands - cat abuse is a real problem from beginners.  I use **tac** 100x more often than cat.  GNU tar doesn't use any switches, though they are allowed.  **tar cvf** is correct.  That all happened when the BSD and sysV change happened.  sysV had to make options just a tiny-bit different for some reason.  That's why we have **ps aux** and **ps -eaf** - the same, but one is sysV and the other BSD.

---

### Post by grahammechanical on 2021-04-09
If you are serious about experimenting with Linux commands be prepared to re-install. It is the quickest and simplest way of fixing a broken operating system. Alternatively, dual boot with another installation of Ubuntu and do all your experimenting with the second installation. 

Regards

---

### Post by him610 on 2021-04-09
You can learn an awful lot by just by following the threads of other people's issues in these forums. It has helped me a great deal over the years. I don't recall ever asking a question because I could always find the answer if I ever had an issue. There are a lot of people who frequent these forums who really know their stuff.

---

### Post by rsteinmetz70112 on 2021-04-11
Just use Linux. 

When you have an issues google the exact problem. If you are stumped come here for Ubuntu questions. Some people here are very knowledgeable and helpful, but help yourself out by providing as complete a description of what your are trying to accomplish as you can. It will save you answering a lot of questions.

Good lunch with you new adventure.

---

### Post by ActionParsnip on 2021-04-11
Just use the OS. Are you versed with Windows? If so, how did you learn how to use it....do that

---

### Post by werner123 on 2021-04-12
I'm new here too and wanted to ask this question too, but saw this thread and all the information I wanted to know. Thank you all and have a good day!

---

