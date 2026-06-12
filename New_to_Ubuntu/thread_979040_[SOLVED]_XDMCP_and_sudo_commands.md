---
title: "[SOLVED] XDMCP and sudo commands"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Captaindl on 2008-11-11
OK, this may not really be the sort of problem that most beginners are likely to have but I am a beginner.  I'm connecting to my Ubuntu machine from a Windows XP machine using Xming and the XDMCP protocol. The problem is that if, in the terminal, I perform a sudo command that starts a program with a graphical interface (e.g. gedit) then the programme take ages to do all but the simplest tasks (e.g. typing text).  All other programmes run normally at the same time, system resources all have plenty unused and this is only for sudo commands in an XDMCP session.

Any ideas?

---

### Post by webdirectsites on 2008-11-11
Install this editor:
apt-get install vim-full

Then to edit a file:
vi /path/to/your/file

---

### Post by Captaindl on 2008-11-13
Thanks this solves the problem for gedit but gedit was just an example of a programme that I wanted to use, it's not the only one.

Any more ideas?

---

### Post by Captaindl on 2008-11-23
Anyone?

---

### Post by Captaindl on 2008-12-02
Wow, impessive the first problem I can't solve on my own and it seems to have everyone else stumped too!  Well I hope to have a bit more information for you all this weekend.  Hope that will help because it's a right pain as it is.

---

### Post by Captaindl on 2009-01-07
OK, just to update everyone as illogical as it seems to me it's the client that's the problem.  Having tried connecting from a computer running a live session of Ubuntu I had no problems.  Last night I got hold of VirtualBox (a Virtual Machine engine) which has a personal use and evaluation licence.  I booted a virtual machine into a live session of Ubuntu and connected.  The problem above did not occur.  Obviously this is a little bit of a clunky work around but it will do as I only need it for administrating the computer remotely.

---

