---
title: "Need help building an apt repository server"
date: 2006-01-24
forum: Repositories &amp; Backports
---

### Post by tjjackso on 2006-01-24
Greetings,

I'm in the process of building an apt repository server (for internal use).  The goal is to consolidate all the packages into a single "component", i.e. "main".

To accomplish this, I've consolidated all the packages (from the various components) into "main".  I then generated a new Release file and a new Packages.bz2 file.  I then configured Apache and added the new apt repository to the sources.list file.

While I am able to connect to the apt repository, I am getting a warning that the packages are "Not Authenticated".   Despite this, I am still able to download and install them.

How do I "authenticate" the packages?  Also, what is the purpose of the Release.gpg file?

Any help would be greatly appreciated.  Thanks.

---

### Post by bernardfrancois on 2006-01-27
Probably, this will help you further: [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

