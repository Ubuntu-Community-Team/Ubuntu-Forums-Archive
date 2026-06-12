---
title: "I want to be a super user!"
date: 2007-02-12
forum: Programming Talk
---

### Post by sri1025 on 2007-02-12
Hi all,

I have been using Ubuntu for more than a year now but never as the main Operting System. I always loved Windows XP and I have continued to use that. But now, it's kind of boring. I want to learn Linux and master it and become a power user.

I generally do programming in Java but recently I started programming in Python. Eventhough Python can also be programmed on Windows, I have to finally deploy them on Linux machines, so it doesn't make sense for me to still use Windows.

But I also don't want to become a Linux System Administrator per se. I just want to be a power user of the Linux shell and other things related to Linux. Basically I want to get to a stage where I should be able to figure out things on my own even if I don't know it. For example, I had to recently find out how to install Apache Web Server on Ubuntu. I didn't even have a clue, it's okay if I don't know things before hand, but I would like to get to a stage where I would want myself to make educated guesses instead of posting a question straight-away in forums.

I know practice is the only thing that will make me do these things, but I would also like to have your suggestions. May be a good book or some online materials and ofcourse your own tips.

Thank you,
Srikanth

---

### Post by FenrisAbraxas on 2007-02-12
> **sri1025 said:**
> Hi all,

I have been using Ubuntu for more than a year now but never as the main Operting System. I always loved Windows XP and I have continued to use that. But now, it's kind of boring. I want to learn Linux and master it and become a power user.

I generally do programming in Java but recently I started programming in Python. Eventhough Python can also be programmed on Windows, I have to finally deploy them on Linux machines, so it doesn't make sense for me to still use Windows.

But I also don't want to become a Linux System Administrator per se. I just want to be a power user of the Linux shell and other things related to Linux. Basically I want to get to a stage where I should be able to figure out things on my own even if I don't know it. For example, I had to recently find out how to install Apache Web Server on Ubuntu. I didn't even have a clue, it's okay if I don't know things before hand, but I would like to get to a stage where I would want myself to make educated guesses instead of posting a question straight-away in forums.

I know practice is the only thing that will make me do these things, but I would also like to have your suggestions. May be a good book or some online materials and ofcourse your own tips.

Thank you,
Srikanth

I considered myself a Linux power user, but the "i want to figure things on my own" would never make sense :P.

Thats why there are Documentation on installation, configuration and usage. IMO what you want is to be an average Linux admin. 

My advice is: read about shell programming/scripting, understand the config files, read documentation of Linux in general (proper use of the CLI especially).

Just one example. Most of the advices in this forums tell you something like this:

>  sudo gksudo /etc/apt/sources.list
Then add the following line:
some.apt.dir someVersion
Save and quit


That can be done with a simple:
```

sudo echo "some.apt.dir someVersion" >> /etc/apt/sources.list

```

Also if you want to become a power user, get used to the CLI make it your best friend (and  when you go to a Windows CMD you will miss all of the Linux CLI features xD).

another thing. man use man :P the manual pages are the best thing to start if you like konqueror it's even easier to read manual pages. Just point it to man://appYouWantTheManual and there you go an easy to read manual page :).

Good Luck in your quest for power.

---

### Post by Choad on 2007-02-12
well how to install depends on your distribution

every distro with the build tools can compile from source... so thats your "1 size fits all" answer, but for pre-compiled packages it is distribution specific.

it mostly boils down to deb or rpm. ubuntu uses deb/apt-get. synaptic is the gui package manager. you can install apache from there

the kind of ability you are tlking about will only come with time and experience. think how long you've used windows for. now think how long you've used linux.

---

### Post by Spinelli on 2007-02-12
Here are three guides I would recommend reading.

This one is an introduction to the Linux command line.
[http://tldp.org/LDP/intro-linux/html/]("http://tldp.org/LDP/intro-linux/html/")

This one is an introduction to shell scripting.
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/]("http://www.tldp.org/LDP/Bash-Beginners-Guide/html/")

This one is the most in depth Linux guide I have ever come across.
[http://rute.2038bug.com/index.html.gz]("http://rute.2038bug.com/index.html.gz")

Start reading the manual pages. Start with this one.
```
man man
```

Use Slackware for a while.
[http://www.slackware.com/]("http://www.slackware.com/")

---

### Post by Ramses de Norre on 2007-02-12
> **FenrisAbraxas said:**
> Just one example. Most of the advices in this forums tell you something like this:

> sudo gksudo /etc/apt/sources.list
Then add the following line:
some.apt.dir someVersion
Save and quit

That can be done with a simple:
```

sudo echo "some.apt.dir someVersion" >> /etc/apt/sources.list

```
I'm afraid you'll have to read up on properly using the cli yourself too... Because the command you showed wont work. The ">>" operator is handled by the shell and the sudo command has no influence on it, thus unless you run bash as root (probably one of the most unsafe things to do) you wont have write privileges on your sources.list. Even worse: the use of sudo is totally redundant, you should never use sudo with echo since every user can write text to stdout...
The correct way to do what you want to achieve is by using tee instead of ">>", thus the line will be like this: ```
echo "..."|sudo tee -a /etc/apt/sources.list
```

For the original question: the more you use linux and try solving problems with cli, the more knowledge you'll gain.

---

### Post by RChickenMan on 2007-02-15
How about building your own linux from scratch?  [www.linuxfromscratch.org](www.linuxfromscratch.org)

---

### Post by lee797 on 2007-02-16
>  This one is the most in depth Linux guide I have ever come across.
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)Great link, I've just stayed up a good five hours past my bedtime reading  this book.

---

### Post by RedSquirrel on 2007-02-24
> **sri1025 said:**
> Hi all,

But I also don't want to become a Linux System Administrator per se. I just want to be a power user of the Linux shell and other things related to Linux. Basically I want to get to a stage where I should be able to figure out things on my own even if I don't know it. For example, I had to recently find out how to install Apache Web Server on Ubuntu. I didn't even have a clue, it's okay if I don't know things before hand, but I would like to get to a stage where I would want myself to make educated guesses instead of posting a question straight-away in forums.

I know practice is the only thing that will make me do these things, but I would also like to have your suggestions. May be a good book or some online materials and ofcourse your own tips.

Thank you,
Srikanth


It will take a fair bit of time and experience to get to the stage of making "educated guesses" and even more to get to the stage of knowing *for sure* what the procedure is or how to solve a given problem.

In terms of online materials:

When you encounter something you don't know how to do or if you get a strange error, try doing some research on your own before asking in a forum.

Google is very helpful, actually. It's pretty rare that your problem hasn't been encountered before. There are some good answers out there, but you have to take them with a grain of salt. Depending on what you're trying to do, realize that you could damage your system by blindly following advice. Even advice in these forums is way off sometimes. Make backups before you try things.

---

