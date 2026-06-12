---
title: "Apt-get with no CD"
date: 2006-04-01
forum: Repositories &amp; Backports
---

### Post by isandir on 2006-04-01
Hey guys,

I borrowed a cd to install ubuntu linux on my computer.  Now i am trying to use apt-get to install emacs and it keeps prompting me to insert and install cd that i do not have.  Is there a way to force apt-get to get emacs from the internet? Thanks.

Isandir

---

### Post by isandir on 2006-04-01
I couldn't find this with search but i've been just reading through posts and i think i found my answer.  Feel free to ignore.

---

### Post by CAPS LOCK CARL on 2007-07-20
Thanks for posting your solution to help the rest of us out, big guy. It's unfortunate that this 2-year-old post is the first Google result for "apt-get ubuntu no cd".

Here is the solution, then, for anybody else who knows nothing about apt and happens to do what I did and google for it:

1) Open up the file **/etc/apt/sources.list** . This contains info about all the repositories apt-get checks.
2) Find lines "**deb cdrom: blah blah**". The ones with "**cdrom:**" are CD-based sources.
3) Remove those lines, or comment them out by adding a **#** in front of them.

Por ejamplo:

[FONT="Courier New"][COLOR="Blue"]**#**deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted[/COLOR]
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
...[/font]

---

### Post by larry_zsh on 2007-07-26
thanks CAPS LOCK CARL spot on!
-larry_zsh

---

