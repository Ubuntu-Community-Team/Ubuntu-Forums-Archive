---
title: "Which version control system do you prefer?"
date: 2015-01-18
forum: Programming Talk
---

### Post by pavelexpertov on 2015-01-18
Hi, at the moment I am at University and I am having fun nailing down assignments!!!! However, when I was reading an article with some useful tips for programming career, it said I should learn using revision version control system. I understand now that these systems help track changes as well as make different version of the same program with different bits of code here and there. That is what I needed all along instead of copy and paste in my projects!!! However, I have some questions relating to this topic:
1. Which version control system would you use if you were doing small and difficult projects on your own?
2. Which '                              ' would you use if you were in a team?
3. Should I use github and its server (if I understand correctly it is a revision system too) to store my code online, or should I store them locally?
Thank you in advance!!!
P.S. I use ubuntu as a development environment, but is it possible for you guys to recommend the systems for Windows? I am using visual studio 2013 at the moment for my assignments and I have no idea if it has version control or not. Also, does android studio have its own revision control system?

---

### Post by trent.josephsen on 2015-01-18
I use Git for my personal projects. Mercurial is another option but I never gave it much of a chance and now I'm set in my ways. I've also used SVN and Perforce for work but they both frustrate me.

You can use Git in Windows. I've done it, but don't really remember how difficult it is; I guess that's a good sign. [The Pro Git book](http://git-scm.com/book/en/v2) mentions using it with Visual Studio, and is also a decent learning resource for Git itself.

Github is not a revision control system, it's just a hosting service for ordinary Git repositories (plus some other extras, like a wiki and a ticketing system). Bitbucket and Gitorious are others that offer the same basic thing; Bitbucket also works with Mercurial. You don't need to bother with those unless you want to.

---

### Post by Rocket2DMn on 2015-01-19
I'd like to make a few points here.  First, learning a VCS (version control system) is a great idea.  If you are a CS (or similar) major, you will need to learn a VCS at some point. The most common ones you're likely to see in industry is SVN and Git.  Git is esp. popular with FOSS.  Obligatory warning: I would be wary about using them on course assignments without instructor/TA support so you don't screw up anything with your assignments before they are submitted.  In short, don't let the extra tool cause you to perform worse on your assignments due to errors using it.  /warning.

For single projects, Git would be my preference.  It is a distributed VCS that does not require a central server, every copy of the code is a complete copy of the repository.  However, sites like Github make collaboration simple by offering free hosting.  I would NOT use Github for course work though, since your code is make public - you don't want other students to see your code.  It is possible to get some benefits like a few private repositories for free if you are a student - see [https://education.github.com/](https://education.github.com/) - I recommend signing up for that.

I actually prefer SVN where possible, even though it requires a central repository, meaning you must have access whenever you commit changes.  It especially works well for hosting multiple (usually related) projects in one repository.  I feel like the learning curve is slightly less, and there are good tools for Windows (see TortoiseSVN) and Linux (search for a tool for your desktop environment).

All VCS's have best practices that you should read up on, like how to structure code and how they handle branching and tagging (capabilities you're not likely to use right away, but will need to know about).  I believe VS has support for both SVN and Git, though I haven't used VS in a really long time so I'm not sure what form that support takes.

---

### Post by pavelexpertov on 2015-01-19
Hey guys, thank you for your posts and I will start learning to use git!!!!! At least I will be more efficient :)!!!!

---

