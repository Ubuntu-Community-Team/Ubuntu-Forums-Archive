---
title: "how come there is no virus on Linux products?"
date: 2008-09-20
forum: Recurring Discussions
---

### Post by ieBrazil on 2008-09-20
How?

Can any knower, expert on this explain me?

tnx! you know, I'm lay on it.




ieBrazil

---

### Post by oneadvent on 2008-09-20
To do any serious damage to a *nix system you must have root privileges, whereas in windows you do not. 

Furthermore any holes in security are caught by "code critics" and fixed as quickly as they could be, much faster than it would take for one rouge out there to create a virus, and much quicker than it would take for it to spread.

Here is some reading you can do:

[http://www.linuxtopia.org/LinuxSecurity/](http://www.linuxtopia.org/LinuxSecurity/)

---

### Post by ieBrazil on 2008-09-20
How?

can anybody one out there explain this to me, a lay person on the issue?

Tnx in advance.




ieBrazil

---

### Post by Monotoko on 2008-09-20
Thanks, iv been wondering that too

---

### Post by cariboo on 2008-09-20
For a little more info on viruses have a look at this page:

[http://en.wikipedia.org/wiki/Linux_Viruses](http://en.wikipedia.org/wiki/Linux_Viruses)

The article is a little bit alarmist, as the writer doesn't explain in plain english what it takes to get a virus in a linux distribution, and that all of these are just proof of concepts. 

The only reason to use an antivurs product is as he says if you are using samba and you store a lot of microsoft office documents or if you forward a lot of email from windows users.

Jim

---

### Post by aysiu on 2008-09-20
There are, actually, and they scan for Windows viruses, the only viruses that are a real threat.

Antivirus can be a handy thing for a mail server to run, as it can stop mass distribution of viruses to various computers.

Antivirus on home Windows computers is pretty much useless or redundant (useless if you are not smart about your computing habits, and redundant if you are smart about your computing habits).

Antivirus fails on two fronts:

1. As far as detecting viruses based on definitions, it's reactive instead of proactive, and won't be able to detect viruses that are newly created.

2. As far as identifying viruses based on the file properties, this kind of guesswork leads to a lot of false positives, which leads to either increased paranoia or to a general mistrust of what the anti-virus software identifies as "infected."

These three measures alone are far more effective and less resource-intensive than anti-virus:

1. Back up your important personal files regularly, and make sure that backup medium is not constantly on and connected to your computer.

2. Use a proper least user privilege system by which your everyday account does not have direct access (without password authentication at least) to system files. Ubuntu and Mac OS X already are set up this way, allowing administrators to be limited users most of the time and then temporarily escalating to full administrative (or "root")  privileges for particular tasks. Other Linux distros (not Ubuntu) allow you to temporarily log in as root for those particular tasks. On Windows XP, you can install SuRun to get such a secure environment.

3. Educate yourself on how to avoid social engineering attacks.

Basically, anti-virus for home user is basically a scam. It's not needed, and there are better ways to secure your computer.

Why aren't Linux viruses rampant?

Most Linux distributions default setups are not conducive to automated rampant system compromise (unless the user is tricked into running said program).

---

