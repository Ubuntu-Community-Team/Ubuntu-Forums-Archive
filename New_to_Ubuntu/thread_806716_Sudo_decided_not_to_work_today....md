---
title: "Sudo decided not to work today..."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-25
Hi folks, 

For some reason, any command which I need to run as sudo decided not to work... Tried rebooting: nothing, tried running nautilus as gksudo: nothing. Can't run synaptic, or run anything under administration... Meaning I'm pretty much dead in the water. What to do? 

EDIT: Now it decided to work, when it wasn't five minutes before. What's going on? 
EDIT: more information which may help. I tried logging in as sudo su and it was successful, but I got a message saying "could not resolve host MYUSERNAME"

-'Mage

---

### Post by jeffus_il on 2008-05-25
> You cannot be frightened of [COLOR=Red]sudo[/COLOR] because you do not know what the [COLOR=Red]sudo[/COLOR] contains and so there is nothing to be afraid of - Jeffamurti

Try visudo and have a look at the definitions file, and try to understand the rules as to who can sudo and when.
use ```
man visudo
```
and ```
man sudoers
``` to get more info and post the sudoers file.
Also make sure you belong to the admin group.

---

### Post by UnWarierMage224 on 2008-05-25
I do belong to the admin group... I'm still not sure about all the visudo stuff, etc.. 

I still, whenever I log in as sudo su or even execute just a sudo command I get the error "unable to resolve host MYUSERNAME"
...

EDIT: synaptic/administrative tools still run very sporadically... Occasionally will get dialog to enter password, other times nothing (when running from system -> administration menu). Also will run sporadically from terminal, sometimes yes, sometimes no...

---

### Post by jeffus_il on 2008-05-25
Yes, that's the problem, sudo needs the host name to be set up, I had the same problem once. Check your /etc/hosts file. I have the following two lines defining my host:
```
127.0.0.1 localhost
127.0.1.1 jeff

```
You need something like this.

---

### Post by mbaker824 on 2008-05-25
> **UnWarierMage224 said:**
> I tried logging in as sudo su and it was successful, but I got a message saying "could not resolve host MYUSERNAME"

You don't need to use 'sudo su'; use one or the other, but not both.  The 'su' command only works if you know the root password, which you probably don't since you're using Ubuntu.

If you want a root terminal, use 'sudo -i'; you'll be asked for your password, and you should be presented with a root terminal (prompt will be # instead of $).  You don't say exactly what command you're trying to execute, but the error message you're getting doesn't point to a sudo permissions problem.  It sounds like the command itself is generating the error.

Try executing this command:
```
sudo cat /etc/sudoers
```

If you get a listing of the file in your terminal, there's no problem with sudo, and you need to look at the command you're trying to execute.  If you can post the command, maybe someone can help.

Mark

---

### Post by crf on 2008-05-25
> **UnWarierMage224 said:**
> 
synaptic/administrative tools still run very sporadically... Occasionally will get dialog to enter password, other times nothing (when running from system -> administration menu). Also will run sporadically from terminal, sometimes yes, sometimes no...

I have this happen too, on occasion, with synaptic and system monitor. They'll do nothing when selected and no password prompt is brought up (sometimes "starting administrative application" can be seen in the bottom panel, but no dialog comes up). There is nothing I can tell that is the matter with my hosts file. So perhaps this is a different problem. My computer is rather old, with little memory.

---

### Post by UnWarierMage224 on 2008-05-25
Hi all, 

Jeff: I edited the etc/hosts file to look like you showed, with the bottom line containing my username. 

I'm still getting sporadic runs of synaptic/any program under the system-administration menu. 

mbaker: when I run sudo cat I get some stuff, first line says "this file must be edited with the visudo command as root", I'm assumming that's what we're looking for? 

Something I just realized may be causing the problem: I recently uninstalled VMware... could that be messing with things? (I just thought about it, sorry for not mentioning it before) 

-'Mage

---

### Post by mbaker824 on 2008-05-25
> **UnWarierMage224 said:**
> mbaker: when I run sudo cat I get some stuff, first line says "this file must be edited with the visudo command as root", I'm assumming that's what we're looking for?

Yes, you're seeing the contents of the sudoers file.  If sudo were not working correctly, you would have received this error message:
```
cat: sudoers: Permission denied
```

Since sudo is working properly, the command you're trying to execute appears to be generating the error, and it appears to be a command that is trying to access something over the network.  Please post the command that is generating the error.

Mark

---

### Post by niteshifter on 2008-05-25
Hi,

> You don't need to use 'sudo su'; use one or the other, but not both. The 'su' command only works if you know the root password, which you probably don't since you're using Ubuntu.


Not true. Below is what happens on my system. The root password has never been set. Each session was ended with Ctrl+D:

```
dlk@dlk-lt-1420:~$ sudo su
root@dlk-lt-1420:/home/dlk# exit

```
```

dlk@dlk-lt-1420:~$ sudo -i
root@dlk-lt-1420:~# logout

```
Note the response to Ctrl+D in each case: su exited, sudo -i logged out. There are differences in the environment set up in each, most notable is where you'll be:

sudo -i puts you in /root
sudo su puts you at your home directory (note the prompt above).

Also sudo su does not log commands (syslog) nor will access controls be in place. So says the man page, but auth.log catches start and stops of sudo su, catches only start of a sudo -i session.

If we're not confused enough yet ;) there's the Root Terminal available under Applications/System Tools - it's like sudo su - you'll be in /home/username but $SHLVL will be 1, not 2, and $SUDO_COMMAND will be different from the other two. It's close is also not caught in auth.log.

In other words, either sudo su or sudo -i or Root Terminal works, but it's best to know the differences here. Folks should stick with sudo -i for a root terminal that acts and looks like a "for real" UNIX root (or use Root Terminal) and only use sudo su when it's particular characteristics are needed (which is hardly ever). 

Indeed the desire for a running terminal at root should always be prefaced with the question "do I really need it?" as 99.99% of the time just plain sudo <command> in a plain terminal is all one needs.

---

### Post by UnWarierMage224 on 2008-05-26
Hmm... maybe I am giving you all the wrong information. 
 
as an example of what is occurring, if I open up the system menu, go to administration, and click Synaptic Package Manager I get what CRF gets: 

> 
synaptic/administrative tools still run very sporadically... Occasionally will get dialog to enter password, other times nothing (when running from system -> administration menu). Also will run sporadically from terminal, sometimes yes, sometimes no...

I have this happen too, on occasion, with synaptic and system monitor. They'll do nothing when selected and no password prompt is brought up (sometimes "starting administrative application" can be seen in the bottom panel, but no dialog comes up).


If I try to run any other program under the administrative tools menu, example: Login Window, all I see is the same thing - a bar in the bottom panel, but no dialog. The bar disappears after a few seconds. 

If I try to run any administrative program from the terminal, such as running gksudo synaptic, the same thing happens - bar but no dialog. 

Opening up system monitor, I see a bunch of gksu processes (each one corresponding to each thing I've tried to run. Example right now is I tried to run synaptic twice, then gtkorphan, then login window.) So, there are several gksu processes, each one has a sleeping status, isn't using the CPU at all, and each has a unique ID #. 

I have not closed any of those gksu processes... trying some stuff and I will tell what happens. 

So right now I'm going to try to run synaptic again (From the system - administrative tools menu), just for illustrative purposes... and now it decided to work. 

running login window (from the menu): now it decided to work
running gtkorphan (from the menu): now it decided to work

running gksudo gtkorphan (from the terminal): nothing. bottom bar with "starting administrative tools", which disappeared after a while. also in the terminal is the following line: my username with the command I ran, and a black flashing cursor underneath. 

closed the terminal, and I'm running gksudo synaptic in a new terminal. 
running gksudo synaptic: nothing. bottom bar with "starting administrative tools", which disappeared after a while. also in the terminal is the following line: my username with the command I ran, and a black flashing cursor underneath. 

ok so I just looked at the system monitor: I see a gksudo process, which is sleeping, with its own process id... 

All this weird behavior started up yesterday morning. I had not fiddled with any system files before that point... 

Sorry this is maddeningly long. 

-'Mage

---

### Post by mbaker824 on 2008-05-26
> **niteshifter said:**
> sudo -i puts you in /root
sudo su puts you at your home directory (note the prompt above).

All true, and I stand corrected.  I was trying to keep it uncomplicated, since we're in an Absolute Beginner forum, but you're absolutely right.

Mark

---

### Post by mbaker824 on 2008-05-26
> **UnWarierMage224 said:**
> If I try to run any other program under the administrative tools menu, example: Login Window, all I see is the same thing - a bar in the bottom panel, but no dialog. The bar disappears after a few seconds. 

If I try to run any administrative program from the terminal, such as running gksudo synaptic, the same thing happens - bar but no dialog.


So, the programs are trying to run, but are unable to for some reason - that's why you see "Starting..." on the panel and it goes away after a while.  The failures should be logged, so you might check the system log to see if it gives you any explanation.

You could also try running Synaptic (or another program that isn't working) from a terminal using sudo instead of gksu - you might get more information on the cause of the failure in the terminal.

```
sudo synaptic
```

When I've seen this happen, it's usually been a permissions issue - typically that the file in question is not marked executable.  What seems really odd here is that it works sometimes, but not others.

Mark

---

### Post by UnWarierMage224 on 2008-05-26
Mark: 

Testing using synaptic and gdmsetup. 

Ran synaptic from the system --> administration menu while looking at var/log/auth.log - entry popped up "unable to resolve host MYUSERNAME". 

Ran synaptic from terminal using sudo synaptic --> It was successful (synaptic loaded) but I still got that same error message in the terminal 

Also ran gdmsetup from terminal using sudo gdmsetup --> was successful but still got the same error message. 

tried running gdmsetup from the system --> administration menu while looking at the log. Didn't run and got the same error msgs. 

-'Mage

---

### Post by mesaverde on 2008-05-26
Okay I have the same problem as you guys. What I have found is that if you try to install or uninstall a program with Add/Remove Applications, you only get the "timer" icon and nothing happens. I will see Starting Administration on the status bar. It runs for awhile and then quits leaving the Add/Remove Applications window open with the timer icon running.

If I then kill the window (I put the Force Quit button on the panel) and try Add/Remove again, then I get the password prompt. It always works the second time. I'd be interested in knowing if this works for you too.

Clearly this is not how it should work and there is some configuration setting that is busted. I would really love to fix this as it is the only spoiler so far with Ubuntu 8.04. The trade-off for all this security is the pain in the neck problems!

---

### Post by karth on 2008-05-26
Had this issue of Administration apps not doing anything, just hanging at launch time

Solved it on my box by adding

```
127.0.0.1  MYMACHINENAME
```

in /etc/hosts, replace MYMACHINENAME by your box's name. You can find it on the System tab of the System Monitor.

---

### Post by mesaverde on 2008-05-26
> **karth said:**
> Had this issue of Administration apps not doing anything, just hanging at launch time

Solved it on my box by adding

```
127.0.0.1  MYMACHINENAME
```

in /etc/hosts, replace MYMACHINENAME by your box's name. You can find it on the System tab of the System Monitor.

Well that did the job for me. My hosts file had 

```
127.0.1.1  MYMACHINENAME.WORKGROUPNAME
```

I added ```
127.0.0.1  MYMACHINENAME
``` rebooted and Add/Remove worked first time.

Thanks Karth

---

### Post by UnWarierMage224 on 2008-05-26
Thanks, Karth! 

Worked like a charm! 

-'Mage 

Thank you also to everyone who helped.

---

