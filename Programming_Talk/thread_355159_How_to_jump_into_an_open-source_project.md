---
title: "How to jump into an open-source project?"
date: 2007-02-06
forum: Programming Talk
---

### Post by raublekick on 2007-02-06
I doubt that I am the only one confused by all this, so hopefully this will be a thread to help clear up some issues. 

My problem is this: I know how to program in several languages. I have a decent amount of experience. I could most likely start up a project on my own and get a somewhat functional app. 

But, there are many projects I have interest in helping out with. Many bugs I would like to squash. The problem is, I have no idea how to get started, where to start, what the general process is for these sorts of things!

I know of CVS and other versioning tools, but I have never used them myself. I have barely a clue how the packaging process works, so when I download source either from the repos or straight from the author(s), I fumble around trying to find what I am looking for. 

Again, this does not seem like a problem that would be unique to me. I have tried my best to follow the guides on Gnome's website but there are so many and no real unified methodology to getting in the game. 

Any helpful knowledge would be greatly appreciated...

---

### Post by jblebrun on 2007-02-06
> **raublekick said:**
> I doubt that I am the only one confused by all this, so hopefully this will be a thread to help clear up some issues. 

My problem is this: I know how to program in several languages. I have a decent amount of experience. I could most likely start up a project on my own and get a somewhat functional app. 

But, there are many projects I have interest in helping out with. Many bugs I would like to squash. The problem is, I have no idea how to get started, where to start, what the general process is for these sorts of things!

I know of CVS and other versioning tools, but I have never used them myself. I have barely a clue how the packaging process works, so when I download source either from the repos or straight from the author(s), I fumble around trying to find what I am looking for. 

Again, this does not seem like a problem that would be unique to me. I have tried my best to follow the guides on Gnome's website but there are so many and no real unified methodology to getting in the game. 

Any helpful knowledge would be greatly appreciated...

The process is really quite open-ended. The exact details will vary from project to project, but it generally looks something like this:

0. Find a list of feature requests or bugs for the software you're interested in. Locate something you'd like to work on. 
1. Get the most current source (usually from CVS or Subversion repositories)
2. Start poking around in the code that is related to the change you want to make
3. Start changing code!
4. If you end up with code that works well, generate a patch, and make it available to the developers. The exact process for this will vary from project to project. 

Don't worry too much about packaging. That part is already taken care of. It looks like the steps you need to take still are:

1. Get comfortable with CVS and Subversion, and what they do, exactly. Understand what the trunk is, what branches are, and what tags are. 
2. Understand what patches are, and how to make them.
3. Find the bug and feature request lists for the software you'd like to help out with.

---

