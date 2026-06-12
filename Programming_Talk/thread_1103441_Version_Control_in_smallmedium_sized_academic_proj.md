---
title: "Version Control in small/medium sized academic project"
date: 2009-03-22
forum: Programming Talk
---

### Post by thebloggu on 2009-03-22
SVN ? CVS ? Git ? Bzr ?

What do you think ? I have been using dropbox but lately two people were trying to access one file to edit and that created conflicts.

I am seeking ease of use primarily, in order not to waste to many time learning how to use it, and good control of previous versions and revisions.

thanks

---

### Post by Reiger on 2009-03-22
For ease of use I'd say SVN (provided that you don't want to branch + merging often). That's (a) really portable (from one OS+tools to another); (b) essentially the common denominator of nearly all version control systems (anything that can do more fancy things usually has at least a plugin to do SVN); (c) easy to learn as long as you stick to modifying a trunk; and (d) you can work on subtree's of the entire project.

It does require that your University let you use their servers for setting up an SVN service+ project though.

---

### Post by intel on 2009-03-23
You _NEED_ to use git  You can get free hosting, or even host your own, fairly easily.  While git has fairly advanced features, no one's FORCING you to use these complicated features  There's even a good gui (git gui), also a java version (egit) which is integrated into eclipse ide git is also supported on windows(msysgit)  One advantage is that, If later, you need any one of these advanced features,  they are already there!  also, svn creates those irritating ".svn" directories in every directory.  The idea of you & your associates using git now,  is to save you time now & trouble later.  Everyone else will tell you how complicated the git command line is, when most of the time you will only use 3-4 easy commands (if not using gui)  Other than that, good luck with your project.

---

### Post by Xiong Chiamiov on 2009-03-23
SVN is standard, and well-integrated with other software.  I'm personally fond of git, mainly because of the situation described in [this article](http://tomayko.com/writings/the-thing-about-git).  I host [my stuff](http://github.com/xiongchiamiov/) on [github](http://github.com), which is free for open-source projects.  [Assembla](http://www.assembla.com/), however, looks very promising.

---

### Post by thebloggu on 2009-03-23
Thank you very much to all. I have to decide now, even though I am confused. And thank you for the good luck too :)

---

### Post by KLuwak on 2011-03-02
I assume the original poster made his or her decision a long time ago, but I'll weigh in for subsequent readers:

I honestly have to recommend Subversion in most cases.  I personally am using Git, and bringing another collaborator on board inevitably entails a longish discussion of distributed version control workflow.  It's worth it if you're managing a /lot/ of software, if you need to do a lot of branching and merging, if you want to work disconnected from the network and still have versioning, or if svn is too slow.  

The thing is that Git's complicated, and often your collaborators just want to check out the source, make their small edits, and then check it back in, all working with The Official Version.  Subversion does that very well.  Subversion (in newer versions) also makes it easy to check out a subset of all the directories in the repository, which makes a lof of sense when you have multiple papers, or a variety of projects, for example.

I see two main problems with Subversion in this context:  First, setting up access control is hard.  If you're directly accessing the shared repository over NFS (or CIFS, or whatever), the file system permission structure is usually pretty limiting.  And, even if you get the permissions right, there are a lot of ways a user can accidentally change the permissions or create a new file with the wrong permissions, and then yout have to revisit the issue.  If you're accessing the repository through an http server, those problems go away, but you need some sort of administrative access to the server to configure permissions, and that's usually a pain, too.  I've forgotten  what the other problem is, but I have a meeting now!

---

### Post by JupiterV2 on 2011-03-04
Well heck, maybe I'll weigh in too.

When I made my choice between svn, git and bzr I chose bazaar. Free hosting on launchpad.net (just as a git user has with github) and very simple. If you're just doing a one-man project or working with a large distributed group, I've found bzr to be very simple and easy to understand, especially for a programmer's first foray into the world of version control.

That said, I've never really used svn or git extensively, other than to just try them, so I'm more than a little biased.

---

### Post by Aikar on 2011-03-05
I've never used bzr so i can't compare to that, but GIT can be used very similary to SVN.
You just have to map the terminology and understand what one word means in the other.

Think of staging files as selectively choosing which files to commit (just like you would do `svn ci foo/bar.php foo/baz.php` instead of just `svn ci`). Except you can toggle these flags before commit instead of having to do it at commit. (ie finish 1 file, stage it, move to next, work on it before commiting)

Git GUI tools makes staging painless (ie stage all and remove ones you dont want to commit, or vice versa)

Then as for how commits work, think of commits working EXACTLY like SVN, except they are not pushed 'up' to the remote server immediately. they stay in a pending transactional state, in which you can revert a commit. then when your absolutely sure your codes good, you can push up to the remote server.

Basically gives commits a vetting process, and lets you commit even while offline. ie programming on an airplane!

---

