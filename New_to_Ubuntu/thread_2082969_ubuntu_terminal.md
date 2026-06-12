---
title: "ubuntu terminal"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by fr33c0untry on 2012-11-11
can anyone enlighten me about some of the uses of the ubuntu terminal.It looks similar to windows command prompt but what is it that makes it better.specifically can it be used for tweaking please specify come tips.

---

### Post by Abhinav Kumar on 2012-11-11
> **fr33c0untry said:**
> can anyone enlighten me about some of the uses of the ubuntu terminal.It looks similar to windows command prompt but what is it that makes it better.specifically can it be used for tweaking please specify come tips.

Hi,

Terminal is very powerful in linux based OS. It can be used to do any work provided you have the necessary permissions.The ability to club several commands using redirection and pipes is what makes it superior over other types of OS. This also makes several difficult tasks to be accomplished using only a few lines of code.

You can have a look at
*[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/) 			*

:)

Regards,
Abhinav

---

### Post by arpanaut on 2012-11-11
Happy Resources:
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

start reading, it will knock your socks off!

---

### Post by fr33c0untry on 2012-11-11
what about doing tasks like cleaning  registry  ,deleting unwanted files like one would do using ccleaner on windows.or are there utilities for maintainance

---

### Post by w o l f on 2012-11-11
You can install, remove or call any application in your system from the terminal , including the maintenance utilities.

---

### Post by zombifier25 on 2012-11-11
Ubuntu does not use registry, and in general requires little maintenance. There's an utility called BleachBit that cleans junk files like CCleaner, and you can install it via the Software Center, or via the command line:
```
sudo apt-get install bleachbit
```

---

### Post by sandyd on 2012-11-11
> **fr33c0untry said:**
> what about doing tasks like cleaning  registry  ,deleting unwanted files like one would do using ccleaner on windows.or are there utilities for maintainance

Linux is not Windows :)

That said, ubuntu does not have a registry, and the Temp folder is cleared on boot so most temperory files are cleared as well. Of course, as zombifier mentioned above, you can use bleachbit, but I have found in general that Ubuntu does not have a high amount of temporory files to begin with

Generally, Ubuntu does not need any maintenance, other than installing the updates that the Update Manager offers.

---

### Post by vasa1 on 2012-11-11
> **fr33c0untry said:**
> what about doing tasks like cleaning  registry  ,deleting unwanted files like one would do using ccleaner on windows.or are there utilities for maintainance

This is unrelated to the topic of the thread. It's better to have specific threads for specific questions.

---

### Post by jerome1232 on 2012-11-11
The power of the terminal really comes in when you learn about bash scripting.
For example using scripts I can use command line tools to create a custom backup script that executes doing exactly what I want it to do, this comes in handy particularly for administrating systems. I can create custom scripts that monitor my log files and alert me when certain events occur, there is a lot more you can do those are just two examples off the top of my head. Windows does the same thing with what's called power shell, it's just an advanced command line meant for scripting on Windows systems. I don't know how powerful it is when measured up against bash.

---

### Post by Stonecold1995 on 2012-11-11
The command line acts as a text based interface (a CLI) which sits on the operating system and allows you to communicate with it in a language both you and your computer can easily understand.  The same goes with a GUI, except a GUI is (obviously) not text-based.  Command line is more powerful because, with a GUI where you get a few buttons that do a few things, with command line you get a myriad of commands at your disposal so you won't have to be restricted by what buttons and interaction a GUI can support.

---

### Post by fr33c0untry on 2012-11-11
thanks everyone for your replies.sorry about the misconceptions about linux.i've been using windows all my life and its been a month since i have given ubuntu a try.i guess i still have lot to learn but now im convinced that this is much better than windows.thanks especially to those who provided links for information regarding the terminal.

---

### Post by Frogs Hair on 2012-11-11
See the command line leaning sticky on top of this forum.

---

### Post by mcduck on 2012-11-11
I'd say the biggest difference is the fact that so many Linux tools and programs provide a command-line interface, so even though the shell itself and default tools are powerful, what makes it so useful is the ability to combine the functionalities from all the available programs to automatically handle complicated tasks for you.

The command-line interface in current Windows versions isn't too far from Bash in features, and OS X of course gives you exactly the same Bash shell you'd have on Ubuntu, but since you have much less programs with CLI support you are more limited in what you can actually accomplish.

---

