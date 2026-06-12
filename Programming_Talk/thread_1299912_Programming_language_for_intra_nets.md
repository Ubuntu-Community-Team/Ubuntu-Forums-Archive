---
title: "Programming language for intra nets?"
date: 2009-10-24
forum: Programming Talk
---

### Post by Syndrome on 2009-10-24
Hi all,

In my organization, we keep all our users in an OpenLDAP directory running on a Debian server. We've created a web site (an intra net) using Perl that talks with the LDAP database. Thus, we can edit and display user data, group data and permissions through a web front end. We use this to generate phone lists and such, as well as giving each user the ability to view and change his/hers contact information etc.

This is nice, but Perl is really not my thing. I wish to rewrite this whole site in some other language (was thinking maybe PHP, and also had a quick look at Django the other day) but I want something with nice connectivity with OpenLDAP.

Any suggestions? Maybe someone have already done something like this before?

Thanks,

Syndrome

---

### Post by slavik on 2009-10-24
ldap is not a database, it's a directory. ;)

just about every language has ldap libraries, so it really depends on what language you are comfortable with. For Perl, take a look at Mason, it should make some Perl code easy to write.

---

