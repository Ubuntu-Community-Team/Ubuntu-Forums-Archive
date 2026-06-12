---
title: "svn list coming up empty"
date: 2010-10-23
forum: Packaging and Compiling Programs
---

### Post by holiday on 2010-10-23
I was stupidly backing up my svn using a plain cp -u. 

I understand now why we backup dumps.

Anyway, I found on these forums a method of rescuing a repository that had been so stupidly backed-up. Here's the trick:

$ svnadmin create /var/svn/repos/treasure 
$ cp -r treasure/* /var/svn/repos/treasure 

where the source treasure is the backed-up copy.

And this works great on the transitional server - an old and overused machine that I trust enough as a temporary drop box, but not enough to make a real server. 

In rebuilding my "trusted" server, I decided to this time build it with thoughtful permissions. 

I followed this tutorial:

[http://svn.haxx.se/dev/archive-2004-03/0253.shtml](http://svn.haxx.se/dev/archive-2004-03/0253.shtml)

And now I'm in a mess. 

I'm working with two repositories - src and fic.

For each repository, permissions are recursively svnadmin:svnusers. I know that's a bit ham-fisted but I'll do it again once I get this bit figured out.

I, as a member of svnusers, can svn list src and see my files, but the same for fic comes back empty. The same result for file:/// and svn+ssh. 

Even for root. 

The du output for the two directories shows appropriate size.

Has this happened to anyone else? Is the solution obvious?

---

