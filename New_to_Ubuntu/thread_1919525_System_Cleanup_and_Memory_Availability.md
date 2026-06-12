---
title: "System Cleanup and Memory Availability"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by LinuXofArabiA on 2012-02-03
Hello Everyone,

Quick question. What is the best way to perform a system cleanup on my Ubuntu to increase speed and efficiency. For example, where would I start (what folders) looking to clear up cache or temporary files that would free up some memory. 

As usual, any links to reading material would be highly appreciated.

Thanks!

---

### Post by raja.genupula on 2012-02-03
install bleachbit that will do the job of cleaning & use software center to get that in a  easy way .

---

### Post by 3rdalbum on 2012-02-03
There's not really much that needs doing. Temporary files get cleared on startup, but as they are files they don't use any memory (only disk space, temporarily).

There is a package cache that you might like to clear - you can use Bleachbit for this. But if you have plenty of hard disk space, you really won't need to clear the package cache. It won't make your computer faster to remove it anyhow.

There's really not much that's necessary on Linux. Only on Windows.

---

### Post by Linux Dutchman on 2012-02-03
i have Bleachbit installed and deborphan. But most of the time i'm not using them. Linux doesn't choke up like Windows does after a period of usage.

There are also some command line commands which you can use:

sudo apt-get autoclean
sudo apt-get autoremove

In synaptic if you click on status (left bottom) and click on Not installed (residual config), those packages which you then see can be removed also. They're just some "left-overs".

---

### Post by LinuXofArabiA on 2012-02-03
[COLOR=Navy]Thank you everyone... I am still left with the feeling that I am looking for something more though.

I guess what I want to know is how to get a handle on my system resources more efficiently. For example I have a laptop with 1GB of DDR RAM that I bought five years ago (I know!). For all practical purposes it serves me just fine, since my use of it is mainly internet browsing, and youtubing. However, whenever I check the system monitor I am finding that almost all of the RAM is in use, and I can 'hear' the inner workings of my laptop, especially on startup, or whenever I download anything. Is 1 GB of RAM not enough any more, even for such uses?

Is there a way I can get better control of my memory distribution?

I know that these questions seem a bit too broad, but I am looking for collecting as much information around the topic, so feel free to chip in with any knowledge you have, even if it doesnt directly answer my questions.

Thanks.[/COLOR]

---

### Post by cryptotheslow on 2012-02-03
Ubuntu is certainly getting a little fatter over time - but that said running 12.04 here with a few tabs up in Firefox has only chomped up ~590MB of RAM - so compared to some other OS's it's pretty lean.

Fire up System Monitor - then look on the Processes tab and sort the list by the memory column and see what is eating your RAM most. People may be able to advise how to reduce usage if they know what applications or processes it is.

Otherwise you may want to consider Xubuntu or Lubuntu for a slimmer, less demanding installation.

---

### Post by LinuXofArabiA on 2012-02-03
> **cryptotheslow said:**
> Ubuntu is certainly getting a little fatter over time - but that said running 12.04 here with a few tabs up in Firefox has only chomped up ~590MB of RAM - so compared to some other OS's it's pretty lean.




[COLOR=Navy]Thanks 'cryptotheslow' for the facts and numbers. This definitely puts things in perspective. Judging by your beans (sounds awkward to say) you seems like you are a power user. I will look into my system monitor and see where my RAM is being wasted.[/COLOR]

---

### Post by d4m1r on 2012-02-03
Few things:

1) 1GB ran is OK for Ubuntu, but I'd upgrade if you can (these days, you can get 2GB for like $20)

2) 11.04 was using about ~300mb on boot, which is nothing, and 11.10 is using about ~400mb. I'd recommend uninstalling all the packages (applications)( you don't use using the software center, or synaptic (preferred). And remove startups things you don't use.

3) Next time install the 64 bit version of Ubuntu because it deals with memory in a slighty more efficient manner.

---

### Post by LinuXofArabiA on 2012-02-03
[COLOR=Navy]Thanks 'd4m1r', I feel like im getting there. Your tips are certainly useful. I have a question though. Is there a way I could learn about each individual process or daemon, say by PID, for example, or by command name? Like is there a command in the terminal that would allow me to learn more about the function of a certain process, or is there an online resource where I could find such info.? You know, instead of by a trial and error approach, or by going and shutting down processes left and right just because they 'look' memory hogs.

Much appreciated. Thanks.

[/COLOR]

---

### Post by cryptotheslow on 2012-02-03
Yes - in the terminal type in 

```
man *processname*
```

e.g.


```
man firefox
```

Alternatively you can access the same information online here:
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)


And no.... by no means am I a "power user" - just been around a while.

---

### Post by LinuXofArabiA on 2012-02-03
Thanks. Appreciate your time.

---

### Post by dagroves on 2012-02-03
I know most of this has been said before but this is what I do and in the exact order that I do them in. (Make sure Ubuntu Tweak and Bleachbit and the Bleachbit Bonus Pack are installed)

Open a terminal and type this in

```

sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove

```Then, open up Ubuntu Tweak as root (in terminal) ```
 sudo ubuntu-tweak 
``` and run the janitor, then open up Bleachbit as root (in terminal) ```
 sudo bleachbit 
``` and run all the cleaners. 

Enjoy a squeaky clean system!

---

### Post by Linux Dutchman on 2012-02-04
Ubuntu Tweak is a tool i don't recommend to new users or inexperienced users. The reason not using Ubuntu Tweak is that it can add packages/repositories of sites which bypasses the rights management system of Ubuntu which verifies the repositories. Like this, there's a big change that users add unstable or corrupt packages which can destroy a good working system.

And also, with Ubuntu Tweak an inexperienced user can remove things which also can destroy a good running system.

Only if you know what you're doing (experienced users) you could use Ubuntu Tweak.

---

### Post by Kixtosh on 2012-02-04
LinuXofArabiA, I don't remember your system specifications from some of your other threads, but I agree with what has been suggested already: Ubuntu is already very efficient with memory and does not slow down over time either. If you want a snappier system, probably the two best options available to you are:

[LIST]
[*]Try lightweight alternatives, although I have found these make very little difference in real performance for machines with even moderate specifications (they are most useful for machines with very modest specifications).
[*]Add a Solid State Hard Drive to your computer.
[/LIST]
With my simple Core 2 Duo 1.2 GHz CPU, 2 GB of RAM and integrated graphics laptop with a SSD, I boot Ubuntu in twenty seconds, and shut down in three. I can open my first Firefox session from a cold boot in two or three seconds, and just one second after that. This is much better than Windows, but there is some lag with some applications from a cold boot.

Adding extra RAM and attempting to clean things up are solutions that can help significantly with Windows, but that are unlikely to help revolutionize your performance with Ubuntu in my opinion. My system almost never uses even 0.5 GB of RAM, and I've never caught it making use of Swap either, for instance. If you're unhappy with performance currently and/or expecting everything to happen within one second, your only  solution is probably to get a new computer with appropriate  specifications ... preferably including a SSD.

---

### Post by LinuXofArabiA on 2012-02-04
[QUOTE=Kixtosh;11663871

Adding extra RAM and attempting to clean things up are solutions that can help significantly with Windows, but that are unlikely to help revolutionize your performance with Ubuntu in my opinion. My system almost never uses even 0.5 GB of RAM, and I've never caught it making use of Swap either, for instance. If you're unhappy with performance currently and/or expecting everything to happen within one second, your only  solution is probably to get a new computer with appropriate  specifications ... preferably including a SSD.[/QUOTE]


Thanks Kixtosh. Acutally, I am not complaining at all, im just wondering about the level of control I can get out of Ubuntu on system resources. I have a question which havent been answer so far, which is how to learn more about a specific process once I use 'top' in the CLI. There are many processes and simply typing 'man' infront of their names doesnt necessarily show up a manual for them. This works for Firefox, but not others.

Also, how did you know that you system uses 0.5 GB of RAM. could you be more specific as to how you found out that number. Like exact details as to where I could find that number on my system?

Thanks

---

### Post by cryptotheslow on 2012-02-05
To find current memory usage:

In the terminal:
```
free -m
```This will output a display like this:
```
             total       used       free     shared    buffers     cached
Mem:          3858       1366       2491          0         87        727
-/+ buffers/cache:        551       3306
Swap:         2519          0       2519

```
That is showing memory usage in MB. It can be slightly confusing but the number of interest is the first one on the 2nd line - in my case here **551**. The "used" on the 1st line includes memory that is used for disk cache / buffered for applications but not actually in use so could be released immediately for other use if required.

There's a good explanation here:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

As for the processes you can't find man pages for - either ask away here or resort to your favourite search engine.

Enjoy :)

---

### Post by ikt on 2012-02-05
Generally 3 types of desktop distro's.

Fat - try to do everything and then some
Thin - try to do just enough while using the least amount of resources possible
You decide - Distro's like Arch, Gentoo, Slackware etc which give you complete control from the start, though installation time, difficulty and learning curve go through the roof.

When it comes to older style laptops Xubuntu and Lubuntu are definitely the kings here, tweaking Ubuntu will only get you so far.

---

### Post by Kixtosh on 2012-02-05
> **cryptotheslow said:**
> To find current memory usage:

In the terminal:
```
free -m
``` ... the number of interest is the first one on the 2nd line - in my case here **551**. ...This "number of interest" also matches what is shown in the System Monitor:

[LIST]
[*]There is a System tab which will give a brief description of the system, similar to Pause+Break in Windows.
[*]There is a "Processes" Tab which currently indicates that most memory on my system is  being used by Firefox (162 MiB, which is what I would expect).
[*]The "Resources" tab shows CPU load, Memory and Swap usage, and Network history. My memory usage is currently 366 MiB with three  browser Windows open on two desktops, totaling eight open browser tabs  altogether. This is the number which matches the second line result of the Terminal command above.
[*]The "File Systems" tab gives a brief description of the drives currently in use.
[/LIST]
In Lucid Lynx 10.0 LTS, the System Monitor is by default in the *System > Administration* Menu, from the Top Panel. It's very simple, and equates to the Task Monitor in Windows, more or less. Another, more complete option is the System Profiler and Benchmark. It's included by default in some distros, in fact:

[LIST]
[*]Can be installed very simply from the Ubuntu Software Center. Just type "System Profiler" in the USC search box, and then click install.
[*]Will install by default in Lucid Lynx in the *Applications* Menu.
[/LIST]

---

### Post by LinuXofArabiA on 2012-02-05
[COLOR=Navy]Thanks guys. Excellent info altogether. I will leave this thread for one more day just in case, and then I will re-tag as SOLVED.

Thanks again :D[/COLOR]

---

