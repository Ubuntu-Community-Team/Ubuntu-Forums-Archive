---
title: "Version Control Advice"
date: 2010-08-03
forum: Programming Talk
---

### Post by Jacobian on 2010-08-03
I'd like to add version control to my web-based content management system: What software would you recommend that I look to for inspiration?

My content management system uses a flat file-system database. Most other content management systems use MySQL databases, so their approaches are different.

My goal is to automatically merge changes from two authors who are editing the same document, but in different places. I'd like to merge their changes transparently whenever possible.

In addition, I would like to be able to restore a file to an earlier point in its history; and similarly, be able to revert an entire folder full of files to an earlier state.

I can keep the version control system up-to-date by issuing commands whenever a file is saved or renamed.

I've looked into things like: diff, rdiff-backup, Subversion, Git, Mercurial, and Bazaar.

What I'd really like is something lightweight that stores only a single copy of the website in its current state, plus the reverse-delta differences that are needed to reconstruct any past state.

For example, I wouldn't want to make a new copy of all of the files in the entire website whenever an author begins to edit a page. Instead, there should be only a tiny merge, when the changes are saved.

Does anyone know if there is existing software that is somewhat similar to this?

Or could one of the full version control systems be made to do this efficiently?

I'm willing to do quite a bit of work in order to create a working system. However, I'd like to have a good starting point.

Do you have any suggestions?

---

### Post by ggaaron on 2010-08-07
Have you looked at MoinMoin?  It is a flat file wiki engine with history, diffs and stuff.  Using already available VCS would probably save you a lot of time and bugs - I'd recommend a DVCS then, it would be much easier to use than SVN, CVS or similar.

Happy hacking

---

### Post by Ferrat on 2010-08-07
Just a thought
"My goal is to automatically merge changes from two authors who are editing the same document, but in different places."

This will be difficult to say the least since you don't know (I'm guessing) what parts are being edited and that can easily become very chaotic, you could in theory split the document in to different parts and check them individually upon changes but the risk of a somewhat chaotic content is still present. 

Depending on content this could also create a lot of problems.

---

### Post by peterspeaks on 2011-07-27
We decided to start to use version control for a [website]("http://www.timedoctor.com/biz3.0/git-mecurial-and-cvs-comparison-of-svn-software/") I  maintain/develop with two other people. The process we currently use is  as follows: the website is hosted on a dedicated server. Our development work is also done on this server, but on a copy of the  site in a sub folder of the live website. When the implementation of a  new feature is finished, we copy the changed files from this sub folder  to the live website. To improve our development process we decided to start using version control.

---

