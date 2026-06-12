---
title: "Reasons for linux security"
date: 2008-12-05
forum: Recurring Discussions
---

### Post by Benzaa on 2008-12-05
I have been using ubuntu (in various flavors) for almost a year now in my personal computer. 

Since I installed the OS, i noticed that it didnt have an antivirus install as default.

My first thought was, !!!uhhh, that's weird!!!

From my (regrettable) years of using windows, I got used to the idea that is compulsory to use an antivirus, otherwise your computer may be hacked and your life secrets stolen. Probably, your computer may even explode (that's what they made me believe) .

My question is, what makes ubuntu/linux so secure?

I would like to have some solid reasons. I want to use them against the computer administrator in my school. He does not allow me to install ubuntu in my working laptop.

I am tired of waiting almost 5 min for the computer to starts (if I am lucky).

Waiting for the anti-virus settings to be read could be a frustrating experience.

---

### Post by cb951303 on 2008-12-05
[http://tuxramblings.wordpress.com/2008/11/17/why-linux-is-more-secure-than-windows/](http://tuxramblings.wordpress.com/2008/11/17/why-linux-is-more-secure-than-windows/)

[http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html](http://freewebsoftwarereviews.blogspot.com/2007/12/why-linux-is-more-secure-than-windows.html)

---

### Post by SpenceMakesSense on 2008-12-05
for me I like how before installing ANYTHING it asks for my passwords so if there is some program trying to install that I dont trust I can just cancel. Also all viruses are written for windows. So they cant work work with linux.

---

### Post by Dr Small on 2008-12-05
Linux's permission and user system is what makes the system so secure. Viruses can not execute if they do not have permission to, and can not write/edit/remove stuff from the filesystem because it is owned by root.

The worst thing a virus could do (and you would have to manually execute it) would be to erase your entire $HOME directory. The system will still remain running, because of the user system and permissions.

There are a few viruses in the wild for Linux, but nothing compared to Window's known thousands where a user must painfully scan for viruses every time the system is booted. Anyone can write a virus; but the hole that they are exploiting is the *user* instead of the system. It's called Social Engineering (SE).

---

### Post by Delever on 2008-12-05
First of all, majority of malware and viruses are Designed for Windows (TM). And by majority, i mean major majority, so major that it is very major. Uh... This may not be solid enough reason :). You know, it is like... Bricks falling from roofs. They do fall, once in a while. Yet people walk near buildings without fear for some reason.

There are more reasons why it is more secure, for example:
- Malicious programs need to be made executable and executed by user to damage user's files.
- Malicious programs need to be executed with sudo (some privileges) to damage system files or start spying on you in the background or modify startup process, etc.

---

### Post by tjwoosta on 2008-12-05
your schools admin probably just dont want you installing ubuntu because he himself is not familiar with linux


if you had to keep track of every single computer in the school and you were not familliar with linux would you allow people to install it?



with that said i will provide some an interesting link
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/]("http://www.itsecurity.com/features/ubuntu-secure-install-resource/")

---

### Post by Benzaa on 2008-12-05
> **tjwoosta said:**
> your schools admin probably just dont want you installing ubuntu because he himself is not familiar with linux


if you had to keep track of every single computer in the school and you were not familliar with linux would you allow people to install it?



with that said i will provide some an interesting link
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/]("http://www.itsecurity.com/features/ubuntu-secure-install-resource/")


But if you are a system administrator, isnt it your job to be familiar with different OS?

and, I think it is easier to track changes in a linux computer than in a windows ?

Am i wrong??

---

### Post by lswb on 2008-12-05
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

