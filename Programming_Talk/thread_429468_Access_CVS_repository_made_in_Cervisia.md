---
title: "Access CVS repository made in Cervisia"
date: 2007-05-01
forum: Programming Talk
---

### Post by Golyadkin on 2007-05-01
Hi everyone.

I am writing a thesis in LaTeX and keep my source files in a CVS repository I created in Cervisia. This works great but now I installed Ubuntu on my other computer as well and I would love to access the repository over the network. I know I can use :pserver: for this, but it can't access the repository. 
I am running Ubuntu 7.04 Feisty Fawn (GNOME) on both computers.

Is there an easy way to make this repository accessible to both machine? 

Any help would be greatly appreciated! 

Thanks in advance,

Golyadkin

---

### Post by thumper on 2007-05-03
Man, still using CVS?

Try Bazaar ([www.bazaar-vcs.org)](www.bazaar-vcs.org)).  There are tools even (I think) that will allow you to keep the version history.

However if that isn't that important to you then "apt-get install bzr"

The docs on the website are great.  Bazaar is a distributed version control system.  Effectively it means that you can commit locally and then push your branches to other machines to make them available.

---

### Post by thumper on 2007-05-03
Oh I forgot...

#bzr on freenode IRC is where the bazaar devs hang out, and you can always get help there.

---

