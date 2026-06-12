---
title: "A few questions about svn"
date: 2009-01-28
forum: Programming Talk
---

### Post by kerryhall on 2009-01-28
Version control should be one of the FIRST things you learn when it comes to programming. My "version control" for the past ?? years has been putting various revisions in different folders. I hope to leave that far behind me.

I have a few questions about svn. First of all, if I do something like

```
sudo svnadmin create /svnrepos

```

How do I list all the repos I have created? How do I delete repos if I ever want to? I have read the docs for svnadmin, but I can't seem to find what I am looking for.

Secondly, if I do something like

```
sudo svn import /projects/myrailsproject file:///svnrepos/myrailsproject

```

How do I tell what projects have been imported? How do I delete projects that have been imported? How do I make sure than only an authenticated user knows what projects I am working on?

Thirdly, I have been following this tutorial a bit:
[http://www.tonyspencer.com/2007/03/02/setup-a-subversion-server-in-4-minutes/](http://www.tonyspencer.com/2007/03/02/setup-a-subversion-server-in-4-minutes/)

Do I need to add my user to a group in order to commit revisions or import projects? For the two above examples, should I have not have used sudo? I'm still a bit rusty when it comes to Linux users, permissions, and groups.

Finally, should I use svn+ssh for checkout? Or should I use apache's svn module? How do I keep my repos secure? I am hosting a web site on the same server that I use for svn. I do not want the public to be able to view my code, or indeed, even know that I have an svn server running unless they know the password. How would I set this up?

Whew! I think that is it. I'm probably making this a lot more complicated than it needs to be. :)

---

### Post by bruce89 on 2009-01-28
Using a "traditional" RCS these days for personal projects is likely to be overkill. Nowadays, DVCSs are much more common. I don't want to tell you what to use, but I'll say that there are several choices. The great thing about them is you don't have to install a server to do anything with them.

The main ones are git, Bazaar and Monotone.

---

### Post by kerryhall on 2009-01-29
Hmmm, maybe I will look into those. Perhaps I'll post a "CVS vs SVN vs GIT vs Monotone vs Bazaar" thread. ;)

For now, do you know the answers to the questions I posted?

Thanks!

---

### Post by NathanB on 2009-01-29
> **kerryhall said:**
> 
For now, do you know the answers to the questions I posted?


Did you try the Subversion mailing lists?

[http://subversion.tigris.org/mailing-lists.html](http://subversion.tigris.org/mailing-lists.html)

---

### Post by jpkotta on 2009-01-29
I agree with bruce89, DVCS are better.  You can always use them the same way (more or less) as a centralized VCS, plus they are easier to use for simple projects where it's more about history than managing several peoples' work.  I use [Mercurial]("http://www.selenic.com/mercurial/wiki/"), for both software and things like hand-edited config files.

---

### Post by kerryhall on 2009-01-30
I haven't tried the Subversion mailing lists yet, I like these forums. :D


Alllrightttt...I guess I'll try a DVCS. Git seems pretty widely used, I think I'll give that a try.

Thanks everyone!

---

### Post by Andcor on 2009-01-30
Regarding your questions. A svn-repos are just a collection of files. Therefore there isn't any database containing information about all the repos you have made and you can simple delete the folder containing the repos if you don't want it any more.

---

### Post by kerryhall on 2009-02-18
Thanks Andcor! So far I have found subversion to be incredibly useful.

---

### Post by hastur on 2009-02-19
hi,

there is a very complete "Svn Book" freely available [http://svnbook.red-bean.com/nightly/en/svn-book.pdf]("http://svnbook.red-bean.com/nightly/en/svn-book.pdf"). It may be a bit longer than a tutorial, but includes everything from day-to-day use to svn admin, managing svn users, and setting up a server.
there are also free svn servers available for managing softare (with or without svn) on the web.

---

### Post by kerryhall on 2009-02-20
Hell yeah, thanks for that!

---

