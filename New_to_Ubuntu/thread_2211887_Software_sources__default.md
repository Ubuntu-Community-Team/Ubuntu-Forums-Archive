---
title: "Software sources : default ?"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-03-18
In software sources, is it best to leave the default repositories checked ?  
What other repos can you check 'safely' ?  
And what about adding PPA's ?  Better to stick with Launchpad or can you actually break your install by adding PPA's from other sources ?

---

### Post by claracc on 2014-03-18
The information in this link: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) can help

---

### Post by Dr. McKay on 2014-03-18
Thx !

---

### Post by claracc on 2014-03-19
You are very welcome

---

### Post by deadflowr on 2014-03-19
> And what about adding PPA's ?  Better to stick with Launchpad or can you  actually break your install by adding PPA's from other sources ? 				

Actually, you probably have a better chance of breaking your system with launchpad ppas then other ppas.

Software from the likes of Oracle and Google, which have their own ppas, outside of the launchpad, tend to keep up with the releases better and so don't tend to break like those from launchpad, which are built by users and updated whenever the maintainer get around to it.
The real problem with launchpad ppas is that a maintainer might just stop at one release, and so if upgrading to a new release, the updating system errors out because the ppa for that release is non-existent.
You see this quite often, here on the forums.
But I don't think I've seen the other ones, like Oracle's or Google's, do that.
(They tend to have other error problems, like badsig errors, which are fixable)

Sometimes the ppas from launchpad are one and done situations, so in those cases, disabling them after install is best practice.
(or even forgoing the ppa and look to install the deb package(s) needed for the program.)

---

