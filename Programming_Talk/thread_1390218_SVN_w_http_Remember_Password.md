---
title: "SVN w/ http: Remember Password"
date: 2010-01-25
forum: Programming Talk
---

### Post by lampyridae on 2010-01-25
Hi, 

At work, I use the command line SVN client in the Ubuntu Terminal to regularly access a SVN repository that is secured with Apache (that is, the address starts with "http://"). 

The problem is that everytime I do a SVN operation involving the repository I have to repeat my username/password. Is there a way to avoid having to constantly authenticate? I have googled about this to no avail.

Thanks,

François

PS : I'm relatively new to ubuntu, although I know the basics of unix (through school and occasional use of OSX Terminal).

---

### Post by lampyridae on 2010-01-27
Here is the solution. Somehow, the ```
~/.subversion
``` folder had an owner and group set to ```
root
```, which prevented the SVN client to cache my username/password. I did:

sudo chown -R *myusername*:*mygroup* ~/.subversion

...and now, I don't have to constantly type in my username/password anymore!

Hope this helps someone.

François

---

### Post by nzmoose on 2010-04-11
Thanks a bunch this helped me out.
Any idea how this happens?

grg

---

### Post by lucasrangit on 2011-07-26
Thanks for the workaround. I submitted a bug report to the Subversion package maintainers at [https://bugs.launchpad.net/ubuntu/+source/subversion/+bug/816738](https://bugs.launchpad.net/ubuntu/+source/subversion/+bug/816738). Check there for more information on what the cause was.

---

