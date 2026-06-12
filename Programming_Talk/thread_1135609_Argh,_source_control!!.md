---
title: "Argh, source control!!"
date: 2009-04-24
forum: Programming Talk
---

### Post by dgrafix on 2009-04-24
Are there any nice and simple svn type apps for linux that are actually useable without needing a degree in it?

I want to to create a simple repository on a network (nfs) drive that i can store projects and check in / out code on all my machines (eg, Desktop, Server and assorted laptops/web-books). I have tried to use SVN but it just doesnt seem to work for me at all. It checks stuff out in the wrong places, doubles up projects within projects and i have no clue what its doing, and the manual is like a years study and while the terminal command line has its place and is great, its just not -better- for this kind of thing. I have tried various GUI's for svn but none of them seem to work the way i expect either.

I am sure SVN is the mutts-nuts but its just... overkill.

Something like MS sourcesafe (without the multitude of bugs) but project based rather than individual files, would be perfect.

---

### Post by dwhitney67 on 2009-04-24
cvs and rcs are two options; they are easy to use.

---

### Post by stevescripts on 2009-04-24
Another option - Fossil - from the creator of SQLite:

[http://www.fossil-scm.org/index.html/doc/tip/www/index.wiki](http://www.fossil-scm.org/index.html/doc/tip/www/index.wiki)

---

### Post by .Maleficus. on 2009-04-24
You could try out Bazaar and Git, they seem to be pretty popular.  Git was actually made to do version control on the Linux kernel.  And, if you ever decide to release your project, both Bazaar and Git have online hosting/bug/etc sites (Launchpad and Github respectively).

---

### Post by hessiess on 2009-04-24
The two main types of revision control are
centralised:
----All history is stored in a central repository, working copies contain
----only a single revision, no history at-all. Advantages that the working
----copies are small, and there are always at least two copies of the newest
----revision(repository and working copie(s), which can easeny be stored on
----different disks. examples are CVS/SVN.

distributed:
----Every working copy contains a complete repository history, this allows
----files to be committed/reverted without internet assess. Disadvantages
----of these systems is that storing a local repository can use a *LOT* of
----disk space, espetilly if the VCS is being used to store large binary
----files. Most of thse systems require SSH for network support, so don't
----work over HTTP proxies verry easely. An example of a distributed VCS
----is GIT.

SVN can be somewhat confusing because there is no 'tree' as such, parts of the repository can be checked out just as easily as the whole repository. bzr is easier in this respect because it manages a tree of files(no partial checkouts), and supports both the centralised and distributed modles, but it still needs SSH for networking.

---

### Post by cszikszoy on 2009-04-24
> **hessiess said:**
> but it still needs SSH for networking.

You don't have to use SSH with bzr.  Take a look here:
[http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html#branching-a-project](http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html#branching-a-project)

I've used bzr quite a bit, it's a really nice VCS.

---

### Post by mmix on 2009-04-25
everyone seems to have their own opinion, so here is mine, :)

try mercurial with nfs
[http://www.selenic.com/mercurial/w3c-talk/](http://www.selenic.com/mercurial/w3c-talk/)

---

### Post by hessiess on 2009-04-27
> **cszikszoy said:**
> You don't have to use SSH with bzr.  Take a look here:
[http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html#branching-a-project](http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html#branching-a-project)

I've used bzr quite a bit, it's a really nice VCS.

Still HTTP accsess is read-only.

---

### Post by t3tech on 2009-04-27
I've settled on using Bazaar myself. After looking at the various options it seemed to be the most flexible and best suited for my needs. Most of my development is solo work. 

The documentation for bazaar I think is pretty decent and it wasn't all that difficult to implement for my projects. I'd say there's a learning curve to overcome with any of the source control packages though. I've done programming for several years but never used any dedicated source control package before about a year ago, besides svn and cvs source checkouts for compiling software releases, and they all seemed like greek to me for using in a development capacity. :)

---

### Post by soltanis on 2009-04-28
Git, git!

Seriously, when I got fed up with subversion, I switched to git. God, you don't know how great it is when your versioning control system works.

---

### Post by sujoy on 2009-04-28
+1 for git. its easy once you get over the initial one week. git-magic can be a nice beginner friendly tutorial. and the ability to work offline is great, since i prefer to have the version control data on a separate machine that i may not be connected to all the time.

---

### Post by abraham.varricatt on 2009-04-28
> **dgrafix said:**
>  but project based rather than individual files, would be perfect.

That sounds like a job for svn to me. How are you setting this up? I'm not familiar with NFS drives, but I've setup svn servers running on a local hard-disk and I've had no problems with the clients either.

At worst, I had trouble getting apache to authenticate users, but that was not too difficult to fix either.

---

### Post by ZuLuuuuuu on 2009-04-28
I switched from SVN to Bazaar recently and I am glad so far. But my reasons for switching wasn't that SVN is not working or hard to learn. Actually, Bazaar, Git and Mercurial are even more complicated and hard to learn. Not too much, though.

My advice would be to switch to a modern VCS (Version Control System) like Bazaar, Git or Mercurial considering you are still not familiar with SVN yet and give time to get familiar with your choice by reading the documents chapter by chapter.

For Bazaar:

[http://bazaar-vcs.org](http://bazaar-vcs.org) (Official web site)

[http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html](http://doc.bazaar-vcs.org/bzr.dev/en/user-guide/index.html) (Very good tutorial to get familiar with both version control systems and Bazaar in particular)

---

