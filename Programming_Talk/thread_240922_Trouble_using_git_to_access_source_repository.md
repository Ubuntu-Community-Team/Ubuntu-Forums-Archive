---
title: "Trouble using git to access source repository"
date: 2006-08-21
forum: Programming Talk
---

### Post by shousonhill on 2006-08-21
this is my first
attempt using a version control system.  I am working off the  "Sugar
on Ubuntu Linux" guide on the OLPCWiki
[http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux](http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux)

I have loaded all of the prerequisite packages.  When I run
sudo git clone git://dev.laptop.org/sugar-jhbuild

I get the following message "git is not called gitfm"
Press Return to run gitfm

I hit return and then I get

gitfm: fatal error: 'chdir' failed: permission denied

Atfirst I thought I might have an access problem on the remote site.  I have since tried to creat a repository from scratch

when I run

sudo gitfm init-db

I get the same error.  I figure there is something wrong w/ my git installation.  Any ideas? thanks

---

### Post by endlessrain on 2007-07-18
this worked for me and sounds like i had the same problem as you
i forgot which thread it was in but...


sudo update-alternatives --config git
choose #2: git-scm

---

