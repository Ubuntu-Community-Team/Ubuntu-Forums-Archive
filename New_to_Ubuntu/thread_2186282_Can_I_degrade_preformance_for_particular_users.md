---
title: "Can I degrade preformance for particular users?"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by skitter on 2013-11-06
I know this is an odd request, and may seem inappropriate.  I can assure you that I own the system I want to do this to. The reason is simple- we have a "children's PC", but the children prefer my PC as it's much more powerful. My SO gets upset if I don't allow the children to use my PC when I'm not using it. I'd prefer that they don't touch it as they have their own. So there you have it- I'm not looking for interpersonal relationship advice, but just a way to make my PC less desirable (slow) when they're logged on it.                                                                                                                                                                                                                                                                                                                             *edit- to clarify a bit,  usage is pretty much limited to youtube / playing flash games.  Perhaps some sort of bandwidth throttling is the best way to go?

---

### Post by Derek Karpinski on 2013-11-06
[http://www.thinkwiki.org/wiki/How_to_use_cpufrequtils](http://www.thinkwiki.org/wiki/How_to_use_cpufrequtils)

---

### Post by deadflowr on 2013-11-06
You can try adding a bunch of applications to their user(s)

First, I assume they have their own user(s).
If not, make new users for them,.
Make sure the new user you make are normal/standard users.

Then log into the new user and open "startup applications"
Then add applications that will start up when that user logs in.
This will require you to know the commands to launch said applications.

Beats me though, on which apps would be best to add.

---

### Post by Frogs Hair on 2013-11-06
being confined to the guest account with no way to save personal settings may disgorge them from wanting to use the computer, but you may be doing that already and it won't slow it down .

---

### Post by walterorlin on 2013-11-06
Why not install something lightweight on the childrens pc so it gets faster?

---

### Post by skitter on 2013-11-06
> **walterorlin said:**
> Why not install something lightweight on the childrens pc so it gets faster?  It's not just the speed, but the large monitor, nice speakers, etc.  Giving their PC a tune up might be worth while, but my previous attempts were wasted time.

---

### Post by inclusivedisjunction on 2013-11-06
I've never messed with it too much, but you could try adjusting some settings in /etc/security/limits.conf. For example, a line like:

```


username hard as 65536


```

would limit each process to a maximum of 64 MB of RAM for *username*. I'm not sure how well it would work for your use, though. A lot of applications don't need anywhere near that much RAM.

---

### Post by buzzingrobot on 2013-11-06
Hmmm.  I think if you manage to slow things down, the kids will ask you to fix it.

And, they will quickly notice that the thing isn't slower when *you* use it.  They will then add two plus two and get four.

---

### Post by bapoumba on 2013-11-07
> **skitter said:**
> It's not just the speed, but the large monitor, nice speakers, etc.  Giving their PC a tune up might be worth while, but my previous attempts were wasted time.
Depends on their age. When my kids were young, they had an account on mine, with no admin rights, that they would use only when I was around. I have not looked for recent ubuntu releases, but I recall I had cut access to some apps somehow on the machine itself (or allowed only some items on their account) and on the internet box too (access hours). Sorry it was some time ago and I'm not sure I had taken notes, I'll look. Now they are either young adults or teenagers, with their own machines (second hands) all running Linux. Some of them I had to tune up for them to be able to watch DVD, Youtube & Co, and play games. My own drawback was on a Xbox that I could delay up to the eldest one 16th bday..

I agree with buzzingrobot, they may notice that it gets slow when they use it and not when you use it.

But to answer your question, running a large backup when they log in may slow all the processes down.
Another idea would be to slow down particular processes (internet access, browsers or games). Sorry I have no experience, here are a couple links that you may find interesting :
[http://stackoverflow.com/questions/2216383/how-to-slow-down-a-process](http://stackoverflow.com/questions/2216383/how-to-slow-down-a-process)
[http://unix.stackexchange.com/questions/18869/slow-down-a-process-without-affecting-other-processes](http://unix.stackexchange.com/questions/18869/slow-down-a-process-without-affecting-other-processes)

---

### Post by colinszt180 on 2013-11-07
my 10yr old son got his mother to 'kick my ass' for trying to make parental control policy on my childrens computer... my best advice is to suck it up, and annoy the hell out of them about correct internet behaviour when they are using your computer!

---

### Post by Bucky Ball on 2013-11-07
A suggestion, although a little involved.

If you have spare disk space, make some free space and do a minimal install alongside your main install. That way, you install the programs from the ground up. Anything you don't want them to access, don't install. 

When the machine boots and they get to the grub list, they select their install and login. Sure, they can select your install, but unless they know your password ...

Just a thought. ;)

---

### Post by Bucky Ball on 2013-11-07
A suggestion, although a little involved.

If you have spare disk space, make some free space and do minimal install. That way, you install the programs from the ground up. Anything you don't want them to access, don't install. 

When the machine boots and they get to the grub list, they select their install and login. Sure, they can select your install, but unless they know your password ...

Just a thought. ;)

---

### Post by newb85 on 2013-11-07
> **bapoumba said:**
> Depends on their age. When my kids were young, they had an account on mine, with no admin rights, that they would use only when I was around. I have not looked for recent ubuntu releases, but I recall I had cut access to some apps somehow on the machine itself (or allowed only some items on their account) and on the internet box too (access hours). Sorry it was some time ago and I'm not sure I had taken notes, I'll look. Now they are either young adults or teenagers, with their own machines (second hands) all running Linux. Some of them I had to tune up for them to be able to watch DVD, Youtube & Co, and play games. My own drawback was on a Xbox that I could delay up to the eldest one 16th bday..

I agree with buzzingrobot, they may notice that it gets slow when they use it and not when you use it.

But to answer your question, running a large backup when they log in may slow all the processes down.
Another idea would be to slow down particular processes (internet access, browsers or games). Sorry I have no experience, here are a couple links that you may find interesting :
[http://stackoverflow.com/questions/2216383/how-to-slow-down-a-process](http://stackoverflow.com/questions/2216383/how-to-slow-down-a-process)
[http://unix.stackexchange.com/questions/18869/slow-down-a-process-without-affecting-other-processes](http://unix.stackexchange.com/questions/18869/slow-down-a-process-without-affecting-other-processes)

It sounds like you were using gnome-nanny.   Unfortunately, with t the introduction of Unity it developed problems working with Ubuntu and was eventually removed from the repositories.

---

### Post by bapoumba on 2013-11-09
> **newb85 said:**
> It sounds like you were using gnome-nanny.   Unfortunately, with t the introduction of Unity it developed problems working with Ubuntu and was eventually removed from the repositories.

Ah, may be, I do not recall. This machine died a few years ago, and i moved my stuff to a new one. At the time, there was not much to backup from their accounts. I've had several machines since then and kept only the "important" things.

---

