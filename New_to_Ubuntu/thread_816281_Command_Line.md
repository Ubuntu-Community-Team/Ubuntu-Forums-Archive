---
title: "Command Line?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by mac143_01 on 2008-06-02
Is there a difference between OpenSUSE and Ubuntu when it comes to commands to use or language in the command line?

If Ubuntu is sudo what is for OpenSUSE? please give me the site where I can learn about the commands of each OS's... THanks!!!

---

### Post by SunnyRabbiera on 2008-06-02
Well suse uses YAST as its packaging tool (inferior to synaptic if you ask me)
and you use su as opposed to sudo.

---

### Post by jeffus_il on 2008-06-02
In general they should be very similar. Most of the commands you run from the command line are separate programs, and sometimes may depend on what you have installed. The command line itself is a program and there are a number to choose from , the most popular today is "bash" which is what is installed by default by most distros (correct me if I am wrong) there is also "sh" "csh" "tcsh" and so on. All have the sh in the name standing for "shell". type "ps" at the prompt and you will see which shell you are running. It will also show you "ps" which is the program you have just run. Try it and post more questions if I have confused you, so that I can confuse you even more.

---

### Post by nick_h on 2008-06-03
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by ChameleonDave on 2008-06-03
> **mac143_01 said:**
> Is there a difference between OpenSUSE and Ubuntu when it comes to commands to use or language in the command line?

If Ubuntu is sudo what is for OpenSUSE? please give me the site where I can learn about the commands of each OS's... THanks!!!
It's just a matter of defaults.  You can configure Ubuntu to use *su* (I have) and SUSE to use *sudo*.

If you find that a command that you are used to is missing on one system, then just go into Synaptic/Yast and install it.

---

### Post by housam on 2008-06-03
[[COLOR="Red"]_here_[/COLOR]]("http://www.oreillynet.com/linux/cmd/") is one site for commands 
and another [[COLOR="red"]_one _[/COLOR]]("http://www.ss64.com/bash/")

---

### Post by Cypher on 2008-06-03
As far as I know, Ubuntu is the only distro that automatically disables the Root account and requires you to use SUDO for admin commands. Other OS' have the Root account, so you could SU into Root to perform the actions. You could also use SUDO, but it isn't something that's automatically setup for you..

The rest of the command line have less to do with the distro being used and more to do with the shell itself. Most modern distro use Bash (Ubuntu now uses Dash) so the syntax is very similar. A few years back, some distros used TCSH or even CSH which had a slightly different syntax..

As far as the various commands used, those are common across all distros as they are standalone programs not affliated with any one particular distro..

---

### Post by ibuclaw on 2008-06-03
There are also aliases that kind of mix things up a bit too.
An alias is a way of taken a long command and shortening it.
ie:
```
alias **ls**='ls --color=auto'
```
So everytime you type in "ls", you are really telling the computer the long form of the command.


I know that in Ubuntu, the following commands
```

l
la
ll

```
are not aliased by default, and so you'd have to type in the long form of the commands instead
```

ls -CF
ls -A
ls -l

```


Whereas in SUSE, I think infact they indeed are enabled! So any SUSE users migrating to Ubuntu may have a small bit of confusion in the terminal before figuring it out.

But the main jelly of it all, as found in the "**/bin**" folder are guaranteed to be exactly the same. The version numbers, different, maybe. But there aren't to be any vast changes that have been done to them anytime soon.

Regards
Iain

---

