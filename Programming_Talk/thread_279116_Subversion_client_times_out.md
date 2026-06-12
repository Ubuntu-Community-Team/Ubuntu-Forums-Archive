---
title: "Subversion client times out"
date: 2006-10-17
forum: Programming Talk
---

### Post by yippy on 2006-10-17
I installed Subversion recently, and converted my old CVS repository with cvs2svn.  I set up svnserve as an inetd service on the default port so I could connect from other machines.  Now when I use the svn client once in a while it works, but usually it sits there for about a minute before the connection times out.  Connecting to the same server through ssh or http I get a response immediately, and that machine is hosting several sites getting a fair amount of traffic all day long, so I know it's not the network.

Has anyone else run into this?

---

