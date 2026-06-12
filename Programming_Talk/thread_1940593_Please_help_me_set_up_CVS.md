---
title: "Please help me set up CVS"
date: 2012-03-14
forum: Programming Talk
---

### Post by Maheriano on 2012-03-14
For the past year I've been creating a rather large website in PHP using just NotePad and Filezilla. I've got 3 folders on the server - /development/, /staging/ and /admin/. I would develop in development and manually copy files over when things were ready.

Just recently I installed NetBeans for PHP and really like that. Now I'd like to get into versioning and branching so I discovered CVS but cannot figure it out. I installed CVS using the package manager and also Cervisia but don't know how to get my files from the hosting server to show up in Cervisia. And then to get everything to show up in NetBeans so I can edit them.

I looked and looked for tutorials online but there seems to be a lot of running command line arguments and setting up user permissions and things. Isn't there a GUI setup I can use where I don't have administrative access to the hosting server?

Thanks everyone.

---

### Post by JDShu on 2012-03-14
I hate to be "that guy", but I do have to ask if you have a specific reason for using cvs over git, bazaar, or even svn?

From my experience, branching and merging with svn is already a huge pain, and my understanding is that cvs is even older and cruftier, and therefore even harder to manage.

---

### Post by Maheriano on 2012-03-14
None at all, should I use SVN instead? I'll use whatever works best.

---

### Post by JDShu on 2012-03-14
They all have their pros and cons, but I would say that you should avoid cvs.

If you're going to be doing a lot of branching and merging, I would recommend git or bazaar (I've never used bazaar), but otherwise svn is pretty solid.

(I personally use git, because that is what most open source projects have moved to and because github is just too convenient.)

To answer your original general question though, I think before you look for a gui you should try to learn how it the vcs you're using works, regardless of which you choose in the end. It's also actually easier to figure out what you're doing when you start with the command line.

---

### Post by Maheriano on 2012-03-14
I'm checking them out now. How much access do I need to the host? It's just a shared hosting account with some random registrar, will it be just as easy?

---

### Post by Maheriano on 2012-03-15
Does anyone know if it's easy to get SVN working on a shared host? Do I need access to the host server?

---

