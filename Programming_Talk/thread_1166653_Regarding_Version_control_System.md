---
title: "Regarding Version control System"
date: 2009-05-21
forum: Programming Talk
---

### Post by codingfreak on 2009-05-21
Hi

I am new into Linux Community. Even though a Windows user started using UBUNTU on my Desktop machine from JAN 2009.

I am about to start my project in C on my Linux machine. So I wanted help regarding the version control system. 

Previously I used Clearcase which had a great GUI support where I can do Checkin and Checkouts without any major commands given in GUI. So is there anything like that in GUI which could help a newbie like me .......

And I do want suggestions from experienced programmers in this community regarding tips to for a newbie who is about to start his fulltime project on C.

---

### Post by hessiess on 2009-05-22
SVN has a large number of GUIs/ integrations with file managers. Though I recommend that you just learn to use the CLI, much more powerful and not so limiting.

Bazaar also looks interesting as it supports both the centralised and decentralised work flows. It also has graphical front ends.

---

### Post by krazyd on 2009-05-22
git is very popular for open source development. For an entertaining explanation of git, see here: [http://tom.preston-werner.com/2009/05/19/the-git-parable.html](http://tom.preston-werner.com/2009/05/19/the-git-parable.html)

---

### Post by codingfreak on 2009-05-22
> **hessiess said:**
> SVN has a large number of GUIs/ integrations with file managers. Though I recommend that you just learn to use the CLI, much more powerful and not so limiting.

Bazaar also looks interesting as it supports both the centralised and decentralised work flows. It also has graphical front ends.

Is Bazaar and SVN GUI are Client and Server based applications ... as the code base will be in the central server and my colleagues can simple use the client to check out the code and create their own copies .... to be frank more like clearcase .....

> **krazyd said:**
> git is very popular for open source development. For an entertaining explanation of git, see here: [http://tom.preston-werner.com/2009/05/19/the-git-parable.html](http://tom.preston-werner.com/2009/05/19/the-git-parable.html)

Yeah I learnt that many popular code base's like Linux kernel are using the GIT. But by default GIT dont seems to have a GUI and there are some third party companies trying to provide GUI for it. Problem is there are hardly any HOW-TO tutorial on how to use those GUI with GIT.

---

### Post by Ferrat on 2009-05-22
Coming from Windows to Linux can be a adjustment but learning to work with the console even though it might slow progress in the beginning will be a great help for later stuff that you might encounter as you are already familiar with it, even though text based might seem frightening at the start you will soon find out how powerful it can be.

---

### Post by hessiess on 2009-05-22
> **codingfreak said:**
> Is Bazaar and SVN GUI are Client and Server based applications ... as the code base will be in the central server and my colleagues can simple use the client to check out the code and create their own copies .... to be frank more like clearcase .....

Yes, they both work as client-server, SVN stores ALL history on the server, bzr can store history locally or on the server, which is advantageous if you wanted to work on something when you don't have a net connection, but don't want the bloat of carrying around the whole repo the rest of the time. SVN supports partial checkouts/commits, whereas bazaar doesn't, at least not currently.

Git always has a complete copy of the repository localy, which is fine so long as you are not storing large binary files in the VCS, in which case your hard drive space won't last long, unless you have a few hundred gig free:).

---

### Post by Tibuda on 2009-05-22
I was really happy with Meld + Command line Git, but I switched to bazzar when I found a [bazaar plugin for Gedit]("http://bazaar-vcs.org/GeditIntegration").

---

