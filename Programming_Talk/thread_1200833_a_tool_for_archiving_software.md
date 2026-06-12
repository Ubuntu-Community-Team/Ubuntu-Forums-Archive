---
title: "a tool for archiving software"
date: 2009-06-30
forum: Programming Talk
---

### Post by danggrianto on 2009-06-30
hi,
i am a junior software engineer. I need a tool to archive all my scipts and updates. what kind of tool should i use, in ubuntu of course? my friend told me about clearcase.

---

### Post by dbd on 2009-06-30
Very good plan, version control systems are essential when you are working on any significant software project. When you break something you can go back to see old versions to see what you've messed up, and you have an automatic backup. Also, if you ever do programming with other people then you'll need to know how to use them so you can all work together.

I don't know anything about clearcase myself, so can't advise you on that, but I'm a big fan of svn (subversion) myself. You can either run a server on your own machine (great because you are in control, but bad if your hard drive dies or you want to access it from different computers), or use a free online server.  

For info on running the server locally (surprisingly easy) have a look over here:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

If you want to store stuff online then there are many, many options, sourceforge or google code are great if it's open source. But if you want some privacy, or want just to thrown loads of projects in one place and just mess around without sharing them, then I'd strongly recommend beanstalk (but their free service has an 100MB limit).
All you need to do with an online server is install the "subversion" package, and find out the details of how to access your particular online server. To work out how to use the command line utility (I'm sure there are graphical ones too, but I'm ignorant since I just use the stuff built in emacs) just enter "svn --help".


Also, once you've used your version control system for a while, and got to know it, then if you are working on your own then I'd advise using cron to automatically commit your changes every hour or so. Have a look over here:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by soltanis on 2009-06-30
You might also consider looking into using a git repository. As a non-fan of svn and its slow, bumbling nature, I am very impressed by git's flexibility:

[http://git-scm.com](http://git-scm.com)

You might also look into this concept: "append-only filesystems".
Read an interesting Wikipedia article on one that was implemented in plan9 (it has since been ported by p9p), where basically you write a file once, then that's it -- you can read it but never modify or delete it. Sounds excellent if you're archiving.

[http://en.wikipedia.org/wiki/Venti](http://en.wikipedia.org/wiki/Venti)
as well as
[http://en.wikipedia.org/wiki/Ext3cow](http://en.wikipedia.org/wiki/Ext3cow)

---

### Post by WRDN on 2009-06-30
I agree with [most] of what dbd said above.

I have been using subversion for a few years and now never undertake a software project without creation a repository first. It may sound like marketing, but after a while, you will start to wonder how you got by without it.
Most things in SVN are easy, and the most important commands are easily:
- svn update (Update your working copy (what you checkout) to HEAD revision (latest revision))
- svn commit -m "My commit message" (Commit your changes. Simple)

There are many others, but you can get by without them.

As dbd mentioned, you can run the repository from a local source (same computer, or another on your network) or use an internet service.
I personally have a webserver that also hosts my repositories. I would recommend doing this, as you will learn much more than if you use a ready-made service.
It is also beneficial because you can greatly customise hooks (things that run at events such as pre/post-commit and pre/post-lock).

I would recommend the Unfuddle service: [http://unfuddle.com/](http://unfuddle.com/)   I have used this in the past for some projects, and it was great. It provides either git/svn repositories, a ticket system, wiki, milestones and messages (like a blog).
With the free account, you are afforded 200Mb storage, max 2 users, 1 project, and unlimited repositories.

[QUOTE=dbd]Also, once you've used your version control system for a while, and got to know it, then if you are working on your own then I'd advise using cron to automatically commit your changes every hour or so. Have a look over here:[/QUOTE]

I do take issue with this. I don't think commits should ever be automatic, as, often when developing software, you will have broken code. This should never be commited to the trunk (main line of development) as far as I'm concerned.
I run a Trac/ViewVC/Doxygen/SVN system for a few people (project with others) and I hope they NEVER commit broken code. The trunk should always be a in a state where you can hit the Compile button, and it will run.
On the otherhand, breaking code in a branch is fine, as these are not the main line, and are meant specifically for testing/ prototyping new features.
The last part of a standard repository is the /tags directory. This contains snapshots of code and other assets. They should never be broken or changed, as they are what most people view as software version releases.

Once you have learned a version control system (e.g. svn, git, perforce, CVS), then you may want to have a look at other tools that can make development smoother. These are mentioned above, but I will describe all of them:

- Trac: A system for tracking bugs, creating wiki pages/documentation, creating roadmaps/milestones, communicating, and browsing source/assets. You can also add plugins e.g. forum, blog, screenshots.

- ViewVC: A system for viewing file revisions/ revision logs/ log messages- this is not possible with the standard way of viewing repositories online (WebDAV)

- Doxygen: A document generator for C,C++, Java, C#, and FORTRAN (among others). It is similar to MSDN (which uses Microsoft Sandbox).

---

### Post by dbd on 2009-06-30
> **dbd said:**
> 
Also, once you've used your version control system for a while, and got to know it, then if you are working on your own then I'd advise using cron to automatically commit your changes every hour or so. Have a look over here:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

> **WRDN said:**
> I agree with [most] of what dbd said above.
I do take issue with this. I don't think commits should ever be automatic, as, often when developing software, you will have broken code. This should never be commited to the trunk (main line of development) as far as I'm concerned.

Yeah, you are right. You should **never** get into the habit of committing broken code, or when you are part way through certain changes. Committing code should always be a decision. Otherwise if you are working on code with a team you could really mess things up for people. It's been a while since I've done much coding so I'd forgotten this. (Although I still can't live without SVN! I nowadays just use it to back up my thesis, which is made up of latex documents. The rules of when it is safe to commit are different there.) Thanks for correcting me :)

---

### Post by Can+~ on 2009-06-30
+1 to svn, plus the [Nautilus SVN plugin]("http://code.google.com/p/nautilussvn/") to get that tortoiseSVN feel.

---

### Post by jpkotta on 2009-07-01
I recommend a DVCS over SVN.  The beauty of a DVCS is that all you need is a local directory.  You don't need to set up a central repository or a server or anything like that (you can if you want to though).  You can easily create different branches and merge them back into the main branch.  Making a new branch is as simple as copying.  

I use Mercurial, soltanis mentioned Git, which seems to have more momentum behind it.  The nice thing about Mercurial is that it works well on Windows and Linux, which was not the case with Git at the time I chose it.  I not only use it for source control at work, but also for keeping track of config files that I edit on my computers, some of which I keep synchronized across all machines.

---

### Post by nvteighen on 2009-07-01
> **jpkotta said:**
> I recommend a DVCS over SVN.  The beauty of a DVCS is that all you need is a local directory.  You don't need to set up a central repository or a server or anything like that (you can if you want to though).  You can easily create different branches and merge them back into the main branch.  Making a new branch is as simple as copying.  

I use Mercurial, soltanis mentioned Git, which seems to have more momentum behind it.  The nice thing about Mercurial is that it works well on Windows and Linux, which was not the case with Git at the time I chose it.  I not only use it for source control at work, but also for keeping track of config files that I edit on my computers, some of which I keep synchronized across all machines.
Besides Git and Mercurial, the other major DCVS is Bazaar (bzr).

---

### Post by fr4nko on 2009-07-01
> **dbd said:**
> Yeah, you are right. You should **never** get into the habit of committing broken code, or when you are part way through certain changes. Committing code should always be a decision. Otherwise if you are working on code with a team you could really mess things up for people.
I agree with that, I think that automatic commit is a bad idea since when you're working on software it can be broken at some moment. A commit should be done when software is in a proper status and you should also make the efforts of giving a meaningful comment.

I'm using also subversion and with [beanstalk]("http://beanstalkapp.com/") you can have a free professional SVN hosting and your repository will be always avaiable from any computer. SVN is also cross platform so you can use it in any OS, Windows, Linux or whatever you prefer.

Francesco

---

### Post by danggrianto on 2009-07-01
thx for all the infos i might try the beanstalk since my code aren't big enough.. i might try the other later when i get used to this stuff..

---

### Post by danggrianto on 2009-07-03
after some researches and studies i think i need to know more about subversion is there any tutorial about subversion? right now i am reading this book [http://svnbook.red-bean.com/en/1.5/svn-book.html#svn.intro.whatis]("http://svnbook.red-bean.com/en/1.5/svn-book.html#svn.intro.whatis")

---

### Post by Mirge on 2009-07-03
I remember the O'Reilly book on Subversion being a decent read...

---

