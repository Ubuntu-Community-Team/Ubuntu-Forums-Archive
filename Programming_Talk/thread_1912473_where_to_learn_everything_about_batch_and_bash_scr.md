---
title: "where to learn everything about batch and bash scriping?"
date: 2012-01-20
forum: Programming Talk
---

### Post by hockey97 on 2012-01-20
Hi, I want to learn how to code in batch and bash.

I already know some stuff in batch.

like 

```
 @echo off
```

and much more stuff like how to create folders, create files, delete folders, delete files, how to open programs and run them and how to pause the program and wait for user input. 

that is about it.

I think I am ready to learn some more intermediate stuff.

From some posts here it looks like it's a programming lango.

someone here was asking how to do things with arrays in bash.

now, I always thought batch and bash is nothing but a command center for the OS.  I never though it was actually a programming language.


So, where can I start to learn batch and bash, want to learn batch first. Since I am already on a windows os computer.

Any ideas?

---

### Post by JRV on 2012-01-20
Here are two sites I would recommend:

[http://ss64.com/bash/](http://ss64.com/bash/)
[http://freeos.com/guides/lsst/](http://freeos.com/guides/lsst/)

---

### Post by Telengard C64 on 2012-01-20
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by hockey97 on 2012-01-20
> **JRV said:**
> Here are two sites I would recommend:

[http://ss64.com/bash/](http://ss64.com/bash/)
[http://freeos.com/guides/lsst/](http://freeos.com/guides/lsst/)

Thanks been looking for a good tutorial like that.


I have my own server using freebsd 8.1 

do you think unix OS'S uses bash?

if so, would this help me with managing my server?

I plan to host website with the server using via apache.

I was thinking to try and have my php scripts run bash scripts.

to at least help me. Like if a hard drive is full or close to being full.. then I need a shell script and a php script that will start saving the files in a new external hard drive.

I am trying to find a way to automate the links. So, if new files are created and stored in a new hard drive my website could still link to the proper file path.

---

### Post by CharlesA on 2012-01-20
> **Telengard C64 said:**
> [http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)
That is an awesome thread. Bash Pitfalls = win.

---

### Post by sisco311 on 2012-01-20
> **hockey97 said:**
> 
From some posts here it looks like it's a programming lango.


Nope, it's a shell: [http://en.wikipedia.org/wiki/Shell_(computing](http://en.wikipedia.org/wiki/Shell_(computing))

[http://en.wikipedia.org/wiki/Comparison_of_command_shells](http://en.wikipedia.org/wiki/Comparison_of_command_shells)

From the BashGuide @ Greg's Wiki (link in my sig):

> 
BASH is an acronym for Bourne Again Shell. It is based on the Bourne shell and is mostly compatible with its features. 

Shells are command interpreters. They are applications that provide users with the ability to give commands to their operating system interactively, or to execute batches of commands quickly. In no way are they required for the execution of programs; they are merely a layer between system function calls and the user. 

Think of a shell as a way for you to speak to your system. Your system doesn't need it for most of its work, but it is an excellent interface between you and what your system can offer. It allows you to perform basic math, run basic tests and execute applications. More importantly, it allows you to combine these operations and connect applications to each other to perform complex and automated tasks. 

BASH is not your operating system. It is not your window manager. It is not your terminal (but it oftens runs inside your terminal). It does not control your mouse or keyboard. It does not configure your system, activate your screensaver, or open your files when you double-click them. It is generally not involved in launching applications from your window manager or desktop environment. It's important to understand that BASH is only an interface for you to execute statements (using BASH syntax), either at the interactive BASH prompt or via BASH scripts.


> **hockey97 said:**
> 
now, I always thought batch and bash is nothing but a command center for the OS.  I never though it was actually a programming language.


A batch file is a command.com (MS-DOS and Windows 9.X) or cmd.exe (Windows NT) script. A script is a text file containing a series of commands to be executed by the shell.


> **hockey97 said:**
> 
I have my own server using freebsd 8.1 

do you think unix OS'S uses bash?


If memory serves, the default shell on FreeBSD is tcsh.

Bash is generally considered to be the *de facto* shell standard in the Unix/Linux world and sh is considered to be the *de jure* one.

---

### Post by Telengard C64 on 2012-01-20
AFAIK Bash is the default shell on most Linux distros. Distros can choose any shell they wish though, and I know of at least one where **zsh** is the default shell.

BSDs are another story.

---

### Post by hockey97 on 2012-01-20
So could bash scripts... help me out?  I know it's a shell.

Yet, I didn't know shells can function the same ways as a programming language. Like have if statements and loops etc.

but is it possible to write a bash script that can help me out with my hosting services? like monitor if a hard drive is about to be full... I want to create some automation where it will search for a new hard drive or a hard drive with free space on the network and then utilize them and update my php scripts so that files like images or text files can be saved on that new hard drive rather then the one that is about to get full. 

I need some kind of automation. Maybe even where it will text message my phone when such things occurs.

---

### Post by Telengard C64 on 2012-01-20
> **hockey97 said:**
> So could bash scripts... help me out?  I know it's a shell.

Probably.

> Yet, I didn't know shells can function the same ways as a programming language. Like have if statements and loops etc.

Yes.

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)

---

### Post by Vaphell on 2012-01-21
Differenciating between programming in programming languages and shell scripting is imo a hair splitting. Scripting utilizes the same concepts of logic, loops and flow control programming languages use.
If shell is not a programming language but a shell, python probably isn't a programming language either ;-) It comes with its own shell and you can do all stuff 1 line at a time or use that thing called script :)

---

### Post by sisco311 on 2012-01-21
> **hockey97 said:**
> So could bash scripts... help me out?  I know it's a shell.

Yet, I didn't know shells can function the same ways as a programming language. Like have if statements and loops etc.

but is it possible to write a bash script that can help me out with my hosting services? like monitor if a hard drive is about to be full... I want to create some automation where it will search for a new hard drive or a hard drive with free space on the network and then utilize them and update my php scripts so that files like images or text files can be saved on that new hard drive rather then the one that is about to get full. 

I need some kind of automation. Maybe even where it will text message my phone when such things occurs.

Yes, you could use Bash & the utilities provided by the OS. But, the real question is: Is Bash the right tool for the job? And I can't answer that. :)

I think you should start a new threat for this. Someone with more experience in web hosting will probably help you out.

---

### Post by CharlesA on 2012-01-21
I'm not quite sure why you'd go thru the effort of making a ton of scripts to monitor a server when there is [Nagios]("http://www.nagios.org/").

I use a simple bash script to tell me disk usage on my home server, but that is only so I know how much space i have left for backups. If it's something like a web server, Nagios would probably be better.

---

### Post by hockey97 on 2012-01-23
> **CharlesA said:**
> I'm not quite sure why you'd go thru the effort of making a ton of scripts to monitor a server when there is [Nagios]("http://www.nagios.org/").

I use a simple bash script to tell me disk usage on my home server, but that is only so I know how much space i have left for backups. If it's something like a web server, Nagios would probably be better.

I might use that software. I need to make a script myself.

that it will talk with my website aka php scripts.

If the hard drive is getting low what I want is the script to do 3 things.

scan for another hard drive that isn't full but never used. Scan it via the network. If there isn't any hard drives free then send my cellphone a text message to remind me I need to order more hard drives.

Then if it does detect a new not used hard drive. Then I need to create folders in that hard drive for my website.

Then update my php scripts to use the new path so if anyone is uploading a image that it will be stored on the new hard drive.

however, I would still use that old hard drive until it's  full and then make the changes.

All I want to have to do is buy the hard drives and connect the hard drives to the network.

that is it. I am a college student and I can't be at home 24/7. I am pretty sure college will fill up most of my time which will cause me to forget to order more hard drives.

Yet, if I do have free time like on winter break or spring break etc. I would use that time to work strictly on new features for my website.

So, I need a bash script to interact with my php scripts.

The script isn't just to monitor the server. It's to actually act upon conditions.

I need it to interact with my php scripts. Where the script will first keep checking on how much storage space we have and then when it gets to like 80% full. It will check on the internal network since I plan to buy NAS hard drives that connects via the network. I want the script to check the network for accessible hard drives and then check how much space it has on that drive.

I want it to figure out on it's own which hard drives via the network it's allowed to access. Like I have computers on the network too but I don't want the server to utilize my personal computers hard drive as new storage for the website.

I just want the network drives to be accessible for my server and then have the batch file check the storage space. If it's a empty hard drive then I want the batch script go make sure it can connect to it properly. Then go back to my php script and make appropriate changes to my scripts to change the directory path to the new hard drive but before that the bash script should already make empty folders on the hard drive. 


I want the server to be automated as much as possible. I was hoping to have the server where I set it up once and it will take care of the rest meaning. I won't have to monkey with it until or unless I decide to make some huge improvements.

So, I need to setup a system where all I do is order hard drives and plug them into the network. Then just monitor things and make improvements. 

something that simple. Even the backup system needs to be in a way where I can get the server back online within seconds.

---

