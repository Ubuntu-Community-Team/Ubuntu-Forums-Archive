---
title: "git question:  git clone isn't pulling in all branches.  please help"
date: 2008-06-30
forum: Programming Talk
---

### Post by laptoplinux on 2008-06-30
I have a project that I'm using git with.  At the moment, I have a master branch and an experimental branch on my local git repo.  I also have a remote bare git repo on a backup server.  

After pushing my current master and experimental branches to the remote server, I tested things by creating a new directory on my desktop and cloning the remote git repo there.  The problem is, it only picked up the master branch, and I can't figure out how to get a cloning operation to even acknowledge the experimental branch.  

I've only been using git for a couple of days now, so I still know almost nothing about it.  What am I doing wrong?  What do I need to do to make sure that I get all remote branches pulled in to a local directory?

I have performed this test a few times before when I only had a master branch, and things worked fine.

---

### Post by laptoplinux on 2008-07-01
Ok, I understand now.  It only pulls the master branch by default.  I have to go in and explicitly pull the other branches later.

---

