---
title: "package install idea"
date: 2007-10-11
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-10-11
Hey Guys

I was wondering if anyone has seen the suggestion that you get when you type a command in xterm and you don't have it installed?

It says something like "the command you typed is not installed please type sudo apt-get install <insert name of package> to install".

What i was wondering is this, why cant it just say "the command you typed is not installed, would you like it installed now? (Y/N)".

Any pointers on which package source this new feature could be added to would be great, or if you thinks its already been done, let me know.

Mike

---

### Post by Ramses de Norre on 2007-10-11
How does xterm now in which package a command resides? And what if two (conflicting) packages have each their own implementation of that command?

---

### Post by milosz.galazka on 2007-10-11
```
$ dpkg -l command-not-found
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nazwa          Wersja         Opis
+++-==============-==============-============================================
ii  command-not-fo 0.2.8ubuntu1   Suggest installation of packages in interact

```

And take look at /etc/bash.bashrc and /etc/bash_not_command_found

---

### Post by Mickeysofine1972 on 2007-10-14
Thanks for the head up!

the scripts lead to a Python file called /usr/share/pycentral/command-not-found/site-packages/CommandNotFound/CommandNotFound.py

this seems to be the main file that does the job so I'm gonna see if I can add a bit more code to it to add this functionality.

I will post my version after if anyone is interested, also, does anyone know how I might get this submitted into the Ubuntu Distro?

Mike

---

### Post by Tomosaur on 2007-10-14
> **Mickeysofine1972 said:**
> Thanks for the head up!

the scripts lead to a Python file called /usr/share/pycentral/command-not-found/site-packages/CommandNotFound/CommandNotFound.py

this seems to be the main file that does the job so I'm gonna see if I can add a bit more code to it to add this functionality.

I will post my version after if anyone is interested, also, does anyone know how I might get this submitted into the Ubuntu Distro?

Mike

Go to this page: [https://launchpad.net/command-not-found](https://launchpad.net/command-not-found), download the **development** version, make your changes, and submit a patch.

You will also need to make an account on launchpad in order to submit patches.

Good luck!

---

### Post by Mickeysofine1972 on 2007-10-14
Thanks for the heads up!

I did a little change and it seems to work so emailed it to Zygmunt the guy looking after the 'for gutsy' branch to see what he thinks

I attached the code here so anyone who wants it can install it.

All you do is:
```

sudo cp CommandNotFound.py /usr/share/pycentral/command-not-found/site-packages/CommandNotFound/

```

I tested this under feisty btw so let me know what happens to it under gutsy please if you do give it a whirl.

Mike

---

### Post by milosz.galazka on 2007-10-14
Good work! I just tried it under gutsy and it works very well :)

---

### Post by Mickeysofine1972 on 2007-10-14
> **milosz.galazka said:**
> Good work! I just tried it under gutsy and it works very well :)

:popcorn::guitar::popcorn:

Kewl! glad to see it works

Mike

---

### Post by bobbocanfly on 2007-10-14
Very cool. Just submitted some stuff for the development (Gutsy+1?) version. I love little projects like this that are really simple but really useful.

---

### Post by Mickeysofine1972 on 2007-10-15
I didn't have the time/patience to work out how to get this into the launchpad code so I just emailed it to the main guy that has write perms for this.

Is there a howto for joining in projects on launchpad and submitting patches etc?

Mike

---

### Post by Tomosaur on 2007-10-15
> **Mickeysofine1972 said:**
> I didn't have the time/patience to work out how to get this into the launchpad code so I just emailed it to the main guy that has write perms for this.

Is there a howto for joining in projects on launchpad and submitting patches etc?

Mike

Generally speaking you should just join the project mailing list, then write a short email introducing yourself, and attach your patch. That way everyone on the project can check your patch and if they like it, they may decide to merge it.

---

