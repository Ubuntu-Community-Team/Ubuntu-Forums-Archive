---
title: "Commiting to the past in Git"
date: 2010-05-27
forum: Programming Talk
---

### Post by altonbr on 2010-05-27
I have a whole bunch of projects that are organized into folders by the date they were edited. Terrible I know, but that's how I operated for some time. Now I'm thankfully using git (after a short stint at work with svn) and I want to post some of my project on github.com.

I can simply upload the projects starting from today's latest version, but I want to have my full revision history, including the date. bzr has a flag called '--commit-time' in bzr 2.1 (Ubuntu 10.04 Lucid Lynx only) but I can't seem to find a flag like that for git.

The only suggestion I have is to edit the environment using ```
env GIT_AUTHOR_DATE="1987-10-31 23:15:00 -0500"
``` or ```
env GIT_COMMITER_DATE="1987-10-31 23:15:00 -0500"
```

Is this correct? And would I change this before every 'git commit -a'? And what about 'git merge'?

---

### Post by trent.josephsen on 2010-05-27
In your position, I would simply commit each previous version in order and put the timestamp of the original in the commit message.  You could set up a script to do that without too much trouble.

---

### Post by altonbr on 2010-05-27
> **trent.josephsen said:**
> In your position, I would simply commit each previous version in order and put the timestamp of the original in the commit message.  You could set up a script to do that without too much trouble.
I've written all sorts of bash scripts before, so that's not a problem, but how could I start with a folder called '20070405' and end with '20100527' with git knowing all the addition/removal of files. I figured I'd have to do it manually. And is that timestamp the GIT_AUTHOR_DATE/GIT_COMMITER_DATE I was speaking of?

---

### Post by trent.josephsen on 2010-05-27
I was referring to using the name of the directory (possibly in some altered form) as (part of) the commit message and letting the metadata fall where it may.  I presume the important thing is getting all the revisions in the correct order, with the record of the date being a secondary concern.  In other words, you couldn't use Git to search by date, but if you really needed to you could sort back through commit messages to find a specific date.

This might not be what you need, but to be honest, I've never had to care about what specific date I wrote some particular code (for other reasons than pure curiosity).  Left to myself, I'd archive the old versions for reference and put only the latest under revision control.  It might sting for a while (although if you've been doing it this way for ages, probably no more than usual), but in 6 months how frequently will you be returning to those old versions?

---

### Post by altonbr on 2010-05-28
> **trent.josephsen said:**
> I was referring to using the name of the directory (possibly in some altered form) as (part of) the commit message and letting the metadata fall where it may.  I presume the important thing is getting all the revisions in the correct order, with the record of the date being a secondary concern.  In other words, you couldn't use Git to search by date, but if you really needed to you could sort back through commit messages to find a specific date.

This might not be what you need, but to be honest, I've never had to care about what specific date I wrote some particular code (for other reasons than pure curiosity).  Left to myself, I'd archive the old versions for reference and put only the latest under revision control.  It might sting for a while (although if you've been doing it this way for ages, probably no more than usual), but in 6 months how frequently will you be returning to those old versions?
That's very very true. I'll just put the date in the commit message. Thanks for your help and logical thinking.

---

