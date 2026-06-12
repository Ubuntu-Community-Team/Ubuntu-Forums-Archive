---
title: "need help with managing sourcecode"
date: 2010-05-10
forum: Programming Talk
---

### Post by icodemonkey on 2010-05-10
OK have asked this before but got no responses.

I need help with managing a folder of source code (see breakdown below) but i don't know enough about the truck load of different ways to manage it.
so what I'm asking is what is the best way and how do i set it up to a basic working level. Or is setting up a git/svn/cvs server a better way to go>


**************break down***************

folder has 3 folders in it called code base, working and notes.

codebase/ ----> has two folders in it. 1st is the source code library folder. 2nd is the snippets folder
(both sorted by <lang>/<app type>/<app name>).

working is just that. the folder i put what ever I'm working on in
same as notes its just a folder for putting notes in

now how do i keep the source code library folder and the snippets folder a). up to date. b). find what I'm looking for?

---

### Post by tookyourtime on 2010-05-10
SVN is the most useful thing I that I have ever overlooked.

It had the same working folder concept that your talking about. You work on files there, then whenever you want you commit it. All the changes are saved throughout time meaning you dont have multlple backups, etc and a whole manner of amazing other things.

Look into that.

Edit: Oh and the reason I avoided it was the server thing. It turns out it works just the same locally.

---

### Post by Portmanteaufu on 2010-05-10
SVN is a good system. It's been long enough that practically everything that needs to support version management supports SVN.

From what I understand, [Bazaar ]("http://bazaar.canonical.com/en/") is pretty excellent in that it only takes a couple of commands to get your stuff under version control and doesn't require a server. Plus, you can use your local Bazaar tools / archives [to interact with other CM systems.]("http://doc.bazaar.canonical.com/migration/en/why-switch-to-bazaar.html#plays-well-with-others")

---

### Post by soltanis on 2010-05-10
> **icodemonkey said:**
> OK have asked this before but got no responses.

I need help with managing a folder of source code (see breakdown below) but i don't know enough about the truck load of different ways to manage it.
so what I'm asking is what is the best way and how do i set it up to a basic working level. Or is setting up a git/svn/cvs server a better way to go>


**************break down***************

folder has 3 folders in it called code base, working and notes.

codebase/ ----> has two folders in it. 1st is the source code library folder. 2nd is the snippets folder
(both sorted by <lang>/<app type>/<app name>).

working is just that. the folder i put what ever I'm working on in
same as notes its just a folder for putting notes in

now how do i keep the source code library folder and the snippets folder a). up to date. b). find what I'm looking for?

Not sure of all of what you're asking, but git is even better than subversion in this task. There's a bit of a learning curve to doing more advanced things like branching off copies, but once you do, you can really go nuts with it. Some people recommend that you make a branch as you add features to your working codebase; git can take care of merging everything together when the time comes.

This is a good tutorial for getting started:

[http://toolmantim.com/thoughts/setting_up_a_new_remote_git_repository](http://toolmantim.com/thoughts/setting_up_a_new_remote_git_repository)

---

### Post by icodemonkey on 2010-05-10
ok nutshell version: need some way of managing source code of different langs locally but have no idea how to go about it.
looked at the tutorial you linked to and it was for remote not local. but still handy.

---

### Post by jeffathehutt on 2010-05-10
Git is very easy to use locally as well.  Check out [this link]("http://progit.org/book/") for an online book that explains how to use git both locally and on a server. :)

---

### Post by icodemonkey on 2010-05-10
@[jeffathehutt]("http://ubuntuforums.org/member.php?u=48102"): that did it! thanks

---

