---
title: "subversion commiting, merging, etc."
date: 2008-03-03
forum: Programming Talk
---

### Post by chocolatetoothpaste on 2008-03-03
Ok,  here is the scenario:  Me, web developer, works in office.  Person #2: web designer, works from home.  There is a web developing server in my office, which we both use to program on.  I installed subversion, setup a repo, all went well.  I created a folder on my machine (called vsl), I used TortoiseSVN to check out the entire site.  I made some changes, used "commit", and it shows that the new file was allegedly commited.  Here's the problem: when I look at the on the actual server, it still shows the old file.  So, then I have to use "svn update", then the machine has the new version of the file.  I need the repo to auto update, then to move the file from the repo to the /var/www/html dir so I can view the changes on the server.  Can anyone help with this, or am I missing something?

---

### Post by pmasiar on 2008-03-04
You can look at post-commit hooks, where you can add update command for another working copy, but I would advise against it. 

You need to have individual development working copies, integration/testing working copy, and production working copy. So you can test your changes integrated with other changes before deploying into production.

Then deploying is just single 'svn update' command - and you can do it when you want, and don't have to test (including regression testing) after every change.

You may also want to look at TRAC: [http://trac.edgewall.org/](http://trac.edgewall.org/) . It is integrated SVN repository, code viewer, bug tracker and wiki for docs - all you need for software development in one neat package.

---

