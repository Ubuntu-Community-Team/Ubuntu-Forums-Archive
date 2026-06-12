---
title: "Problems while updating"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by aneblanc on 2013-07-13
I did a regular weekly update and at the end got this message:

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
 Furthermore run the following command in a Terminal: apt-get install -f

Now I have a now entry sign symbol in the top bar and I noticed that the computer is slower and few programs don't work properly. I use Opera as my favorite browser.

I tried apt-get-install-f in the terminal but it is an unknown command. I don't know what are third party repositories and don't what it means to disable them.

---

### Post by claracc on 2013-07-13
You have not run correctly the command, you have to write:

> sudo apt-get install -f

you will be ask for your pass, introduce it and enter.

The third party repositories are the sites from which you can download the software packages to install in your ubuntu system. Please read: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) it can give you certain clues to solve your problem

---

### Post by Werne on 2013-07-13
Which OS? Which version? And how did you update?

By the way...
> **aneblanc said:**
> apt-get-install-f
It's not "apt-get-install-f", it's:
```
sudo apt-get install -f
```
Or if you like to write more:
```
sudo apt-get install --fix-broken
```
It fixes broken packages by obtaining other packages they depend on, provided that they are in the repositories. The above command "should" resolve the issue, not 100% guaranteed though.

---

