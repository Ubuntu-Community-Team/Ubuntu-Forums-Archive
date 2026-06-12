---
title: "Need advice on git vs mercurial version control"
date: 2008-06-13
forum: Programming Talk
---

### Post by laptoplinux on 2008-06-13
Soon I'll be setting up a version control system, and I need advice on what to go with.  Here's a little background, since this must be taken into consideration for my decision:

I have never set up or used version control before, so I'll be coming to any system as a fresh learner without habits or concepts picked up from other version control systems.

I am doing research in the field of computational physics.  Learning, understanding, and writing computer calculations on physics problems is my job, not spending 100% of my time trying to master a version control system.

That said, I am prepared to put a little more effort in on the front end if the additional benefits outweigh the additional hassle once code production revs up. In any event, I will probably be learning the system gradually as I go while I initially keep the code and revisions on my local machine as I do now.

I've done some research already.  What I came up with were Subversion, git, mercurial and bazaar.  Subversion is centralized, and it seems that people consider decentralized VCS to be the way to go these days.  Bazaar worries me because it does not seem to be a very popular choice.  Git and Mercurial seem roughly equal, though the common sentiment seems to be that Mercurial is easier to use and adequate for most things whereas Git is more powerful but a bear to learn.  Also, Git only works well for Unix-based systems, but that is no problem for me since the development team uses only OSX and Linux. 

With all that said, I need some advice.  It's hard to pick a clear winner from git and mercurial, and some of the articles on them are 3 years old, which makes them too dated to be relevant.  Case in point, I only started using Linux 3 years ago, and the Linux of today is a completely different and much friendlier beast.

So with all that, I'm looking for advice.  Git or Mercurial (or, if there is a sufficiently compelling reason, Subversion)?  Which one and why?

All help is appreciated.

---

### Post by johnl on 2008-06-13
If you don't have a compelling reason to use a decentralized version control system, subversion is the way to go.

---

### Post by bruce89 on 2008-06-13
git was essentially designed to be a fast copy of Mercurial. I favour git myself, but only because it seems to be the most popular (I can't bring myself to like Bzr).

---

### Post by kung fu buntu on 2008-06-14
I remember googling for comparisons between some CMS, namely: bzr, subversion, git.
I ended up choosing bzr, IIRC its as powerfull as git in terms of features and it "just works (tm)" :D

IMHO that "not enough people use it" criteria is plain wrong. I guess that's how hardware manufacters think about linux.

@bruce89 what is wrong with bzr? Too intuitive? :p

---

### Post by generalguy on 2008-06-14
Mercurial has a decent windows port with gui. msys-git is still in the works.

---

### Post by zoke on 2008-06-16
I too have been looking for a VCS to work with and I started to work with git. So far it seems to be good however threads like these make me wonder if mecurial is a good choice. Large progjects like Mozilla have adopted mecurial to use for their source control. I strongly suggest just getting them both and using them. That way you can find one that has extentions for your text editer, a gui that suits or taste, etc etc. Make a list of things you would like to do with the DVCS and then to them with each. After doing that you should have a clear choice.

---

### Post by dmitrijledkov on 2008-08-07
I had no previous experience either and I started out with git. The times of it being unfriendly are gone. It's quite easy to learn from manpages.

There is so far only one caveat that makes me thing about switching to bzr. Folder is branch container. Therefore when you switch to a different branch your folder changes. I still can't figure out how to build 2 different branches for testing without _actually_ tracking binary blobs in VCS.

In bzr on the other hand folder is a branch therefore you _can_ build every single branch for testing simultaniously.

Following recent developments all of them are very strong, easy to learn and fast enough. Git is the fastest, bzr more friendly, hg dunno =D

---

### Post by LaRoza on 2008-08-08
> **johnl said:**
> If you don't have a compelling reason to use a decentralized version control system, subversion is the way to go.

Are you stupid and ugly :-) [http://www.youtube.com/watch?v=4XpnKHJAok8](http://www.youtube.com/watch?v=4XpnKHJAok8)

---

### Post by laptoplinux on 2008-08-08
Well, I finally decided on git a few weeks ago.  Spent 5 minutes playing around with git and had a first test commit to both my local and remote repository.

Then spent tried to do the same thing with a mercurial repository.  After 10 minutes, still hadn't quite figured it out, so I went with git instead.  That, and what looks like a good git book is coming out in September/October.  (Pragmatic Version Control using Git).  

No hard feelings against hg.  I just went with what I could get up and running the fastest.  Still don't know all there is to know about git, but I know enough to do what I need for now and I'm learning as I go.

---

