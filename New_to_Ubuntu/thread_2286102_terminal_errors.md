---
title: "terminal errors"
date: 2015-07-10
forum: New to Ubuntu
---

### Post by Gerald_Hourihan on 2015-07-10
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I was installing Pipeline prior to installing Silverlight.
Terminal appeared to stop with some message about EULA agreement and MSconfig fonts and installation would not continue and no buttons available to agree so i closed the terminal. Pipeline is still not installed but because of errors I cannot restart install.

What now?

---

### Post by QIII on 2015-07-10
Pipelight is an alternative to Silverlight.  Silverlight does not work with Linux.

The error you are getting indicates you have two package installation applications running at the same time.  Make sure to close the terminal and the Software Center and use only one at a time.  (If you have synaptic installed, shut that down too.)

---

### Post by oldos2er on 2015-07-10
Use the Tab and Enter keys to agree with the mscorefonts EULA.

---

### Post by Gerald_Hourihan on 2015-07-10
I closed terminal and logged out. when I restart the terminal and enter sudo apt-get install pipelight multi I get an error msg E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 Sorry but I do not know where to go from here

---

### Post by Gerald_Hourihan on 2015-07-10
thanks for info. if ii get the other part of my problem i will use this Appreciate help

---

### Post by oldos2er on 2015-07-10
As QIII said, be sure you don't have any other package managers open when you run that command. That includes Update Manager and Software Center, among others.

---

### Post by steeldriver on 2015-07-10
If you force-quit the installation, then it may have left a stale lock file - if you are certain that no other process is holding the lock, you may need to manually delete the lock file

---

### Post by Gerald_Hourihan on 2015-07-10
sorry to be so slow but how would i find this lock file to delete?

---

### Post by Bashing-om on 2015-07-10
Gerald_Hourihan; Hello;

It is a process of learning. And this may be more than you want to know.
This terminal command Should tell you whats locking dpkg.
```

lsof /var/lib/dpkg/lock

```
check to make sure you still don't have a package manager running.
Example:
```

ps -e | grep apt

```
24674 pts/4    00:02:06 apt-get
Uh-oh. In this example, apt-get is running!
Then- if you can not back out gracefully:
The following will try to shut down apt-get gracefully.
```

sudo pkill -1 apt-get

```

If the lock condition is still present:
Now Then, try and remove the lock: 
```

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
sudo fuser -cuk /var/cache/apt/archives/lock; sudo rm -f /var/cache/apt/archives/lock

```

Highly suggested to "consult the manual" here:
```

man lsof
man fuser

```
so you are aware of what we are doing and the why.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Gerald_Hourihan on 2015-07-10
when i type in 
lsof /var/lib/dpkg/lock I do not get any response. it just returns to the command prompt. But when I type ps -e | grep apt I get the following message
 3518 ?        00:33:52 apt-get
 5026 ?        00:00:00 update-apt-xapi

What do I do with this info? presumably these are the two things running which caused the lock up.Do I just continue with your sudo fuser suggestion??? 
Meanwhile I will be reading the manual on lsof and fuser. Thanks

---

### Post by Bashing-om on 2015-07-10
Gerald_Hourihan; Humm ...

Not what I had expected:
> 
lsof /var/lib/dpkg/lock I do not get any response.

indicates there is no lock on the package manager.
However,then :
I am not too sure what to make of:
> 
ps -e | grep apt I get the following message
3518 ? 00:33:52 apt-get
5026 ? 00:00:00 update-apt-xapi

Which seems to indicate that apt is running an update .
rerun the command and see if update is still running, and also what does 
```

top

```
show for apt - if anything - . 'q' to "quit" from top.

We do not want to (p)kill apt-get if it is in progress of updates .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by earruda on 2015-07-20
This is caused by another instance of the package manager running while you try to run an apt-get install, for example.
You should wait for the command to finish, or kill it, but killing it may not solve your problem, as it may leve the lock file there. In this case, you will need to remove it with an *rm* command. See this question: [http://askubuntu.com/questions/498102/how-do-i-unlock-var-lib-dpkg-lock](http://askubuntu.com/questions/498102/how-do-i-unlock-var-lib-dpkg-lock)

---

