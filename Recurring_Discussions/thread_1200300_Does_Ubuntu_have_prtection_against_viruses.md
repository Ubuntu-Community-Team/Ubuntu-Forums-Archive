---
title: "Does Ubuntu have prtection against viruses"
date: 2009-06-29
forum: Recurring Discussions
---

### Post by Victor43 on 2009-06-29
Looking to find out if Ubuntu comes with some form of antivirus protection against trojans and worms and spyware ? If not can someone recommend such a program to download ?
 
Thanks in advance.
 
Victor

---

### Post by aysiu on 2009-06-29
You should read this:
[Ubuntu Security](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by jonian_g on 2009-06-29
There are no viruses for linux. You don't need an antivirus.

---

### Post by aysiu on 2009-06-29
> **jonian_g said:**
> There are no viruses for linux. You don't need an antivirus.
More importantly, if a virus appeared suddenly, having antivirus installed would not protect you from it.

---

### Post by Blood//Stain//Child on 2009-06-29
> **aysiu said:**
> More importantly, if a virus appeared suddenly, having antivirus installed would not protect you from it.

That statement is not true. Any extra layer of defence is a good thing.

---

### Post by Tibuda on 2009-06-29
> **Blood//Stain//Child said:**
> That statement is not true. Any extra layer of defence is a good thing.

It is true. All the AntiVirus available for Linux only scans for Windows virus. The "extra layer of defence" will only waste your computer resources.

---

### Post by aysiu on 2009-06-29
> **Blood//Stain//Child said:**
> That statement is not true. Any extra layer of defence is a good thing.
I agree with your last statement, but it doesn't contradict what I said.

A strong password is a layer of defense. Education about social engineering and trojans is a layer of defense. Properly configured AppArmor is a layer of defense. Installing software only from the repositories is a layer of defense.

Antivirus is not a layer of defense. Antivirus is a placebo.

---

### Post by monsterstack on 2009-06-29
> **Blood//Stain//Child said:**
> That statement is not true. Any extra layer of defence is a good thing.

Vulnerabilities in Linux are patched quickly. About a thousand or so known pieces of malware have been made for Linux, and not one of them still works on modern Linux software. Antvirus definitions have the same nature. If a piece of malware has been made in the last couple of days, your virus scanner *will not know about it*. It will report your system as being free from malware. It will lie to you. This is a bad thing. If you wait long enough, the virus scanner software will have been updated; but by the time that happens, the software with the vulnerabilities to allow that malware will also have been patched. Therefore rendering your AV software completely useless.

---

### Post by Blood//Stain//Child on 2009-06-29
> **danielrmt said:**
> It is true. All the AntiVirus available for Linux only scans for Windows virus. The "extra layer of defence" will only waste your computer resources.

No they don't. Several scan for known Linux malware. avast! for instance. 

> **aysiu said:**
> I agree with your last statement, but it doesn't contradict what I said.

A strong password is a layer of defense. Education about social engineering and trojans is a layer of defense. Properly configured AppArmor is a layer of defense. Installing software only from the repositories is a layer of defense.

Antivirus is not a layer of defense. Antivirus is a placebo.

True. Ubuntu should really use a separate root password as well.

> **monsterstack said:**
> Vulnerabilities in Linux are patched quickly. About a thousand or so known pieces of malware have been made for Linux, and not one of them still works on modern Linux software. Antvirus definitions have the same nature. If a piece of malware has been made in the last couple of days, your virus scanner *will not know about it*. It will report your system as being free from malware. It will lie to you. This is a bad thing. If you wait long enough, the virus scanner software will have been updated; but by the time that happens, the software with the vulnerabilities to allow that malware will also have been patched. Therefore rendering your AV software completely useless.

AntiVirus is not a placebo if it is implemented well. That really is a strange and ill-informed statement to make. As for definitions, your are absolutely correct.

---

### Post by rookcifer on 2009-06-29
> **Blood//Stain//Child said:**
> No they don't. Several scan for known Linux malware. avast! for instance. 

There are no known Linux viruses *in the wild.*


> AntiVirus is not a placebo if it is implemented well. That really is a strange and ill-informed statement to make. As for definitions, your are absolutely correct.

How exactly does one "implement" AV "well?"  The truth is AV is a Windows thing perpetuated by companies that make millions of dollars doing it.  The only reason AV software exists in the first place is because of the inherently insecure design of Windows (especially prior to Vista).  The only way to become "infected" on a Linux machine is to be monumentally dumb (much dumber than you have to be on Windows).  If one follows the advice already given in this thread, then AV is a complete waste of resources.

---

### Post by dtoronto on 2009-06-29
Clam AV has virus protection for Linux

[www.clamav.net/](www.clamav.net/)

---

### Post by philcamlin on 2009-06-29
i have bit defender just in case for when i download music p2p 
because i put it on my aache and use it for my dads windows pc :popcorn:

---

### Post by Maxplayer14 on 2009-06-30
You can get it if you want.  It does come with spell check too.

---

### Post by dragos2 on 2009-06-30
There are viruses for Linux, but there are very few worms, so you can hardly get exploited and infected. And if you are up to date changes to get infected while using linux are so low that they shoul not be taken into consideration.

---

### Post by lisati on 2009-06-30
The best defense against malware, regardless of OS, is to leave the computer switched off. Failing that, exercising some good sense about web sites you visit, emails you read, and files you open will go a long way to protecting you. And having some kind of tools available won't hurt.....

---

### Post by Bios Element on 2009-06-30
> **dragos2 said:**
> There are viruses for Linux, but there are very few worms, so you can hardly get exploited and infected. And if you are up to date changes to get infected while using linux are so low that they shoul not be taken into consideration.

Any "exploits" come from social engineering. And nothing can protect people from themselves.

---

### Post by ELD on 2009-06-30
> **Bios Element said:**
> Any "exploits" come from social engineering. And nothing can protect people from themselves.

So very true, most of the time the Virus is a silly user clicking a silly link or downloading something silly. I learnt my mistakes about that some time ago.

---

### Post by xouns on 2009-06-30
To answer the question, yes there is.
To follow up on the question: it is hardly needed to use AV-software on a Linux only machine, unless to protect your friends. You should read the link in the second post.

My 2 cents: I don't use AV on my linux system, but do use AV on my Windows XP and WIndows 7 installations (same PC). I standard have java-script disabled to protect my windows when inside Ubuntu. That's all.

---

### Post by gjoellee on 2009-06-30
The virus has to know your root or sudo password to do much harm anyway. This means that a person has to hack your computer and then somehow get the password before the person creates a virus especially for your computer.

Please tell me if a am very wrong here!

---

### Post by Bios Element on 2009-06-30
> **gjoellee said:**
> The virus has to know your root or sudo password to do much harm anyway. This means that a person has to hack your computer and then somehow get the password before the person creates a virus especially for your computer.

Please tell me if a am very wrong here!

You are wrong. Read my previous post.

---

### Post by gjoellee on 2009-06-30
> **Bios Element said:**
> You are wrong. Read my previous post.

aaahhhhhh....:KS

---

### Post by mkrahmeh on 2009-06-30
> **gjoellee said:**
> The virus has to know your root or sudo password to do much harm anyway. This means that a person has to hack your computer and then somehow get the password before the person creates a virus especially for your computer.

Please tell me if a am very wrong here!
in that sense, windows is just as secure as linux then; problem with windows partially is not with how it is designed, but with how people use it, it is the most common to log in as admins, granting admin privileges and system files access to viruses that come to the admin's workspace.
thats why it is not recommended to log in as root all the time, other than executing unintended commands in the terminal, as far as i know  

> **Bios Element said:**
> You are wrong. Read my previous post.
usually malicious files make their way to the user's memory/home folders causing problems to the extent of that user's power over the system, in which case he is not wrong..social engineering is a different issue

---

### Post by tarps87 on 2009-06-30
> **mkrahmeh said:**
> [QUOTE=gjoellee;7539025]The virus has to know your root or sudo password to do much harm anyway. This means that a person has to hack your computer and then somehow get the password before the person creates a virus especially for your computer.

Please tell me if a am very wrong here!

in that sense, windows is just as secure as linux then; problem with windows partially is not with how it is designed, but with how people use it, it is the most common to log in as admins, granting admin privileges and system files access to viruses that come to the admin's workspace.
thats why it is not recommended to log in as root all the time, other than executing unintended commands in the terminal, as far as i know  
...[/QUOTE]

The main difference between the to OS's in this sense (not including the way the user uses it) is the lack of real multi user support and default file permissions in windows. It is slowly improving but this is by additions not a redesign.
If you think about it to install programs in windows you need to be logged in as an admin where as in GNU/Linux you can open a terminal and switch user to root or 'super user privileges'.
This is the main reason I use xp with an admin account, it takes long enough just to login in once without having to logout and back in starting up all your programs again, etc. Well that and I only use it for two games.

p.s. mkrahmeh you have no longer killed this thread

---

### Post by mkrahmeh on 2009-07-01
> **tarps87 said:**
> p.s. mkrahmeh you have no longer kill this thread

:lolflag:
you made my day

---

