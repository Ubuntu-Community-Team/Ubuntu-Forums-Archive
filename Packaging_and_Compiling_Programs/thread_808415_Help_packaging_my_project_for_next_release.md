---
title: "Help packaging my project for next release"
date: 2008-05-26
forum: Packaging and Compiling Programs
---

### Post by curtis on 2008-05-26
Hello,
I would like a bit of help regarding packaging my project (modulargaming.com) into the next release of ubuntu (universe of course)

it is a web game framework using php5, but it does make use of a few libraries such as Smarty and ActivePHP - should they be packaged separately or just bundled? 

What about locations? Should it be installed into /var/www/ ?
Depend ices would probably be libapache2-mod-php5 and apache2 and mysql-server plus libapache2-mod-rewrite (or just enabling it as it is included by default?)

Thanks,
Curtis.

---

### Post by curtis on 2008-05-27
.

---

### Post by 23meg on 2008-05-27
Moved to Packaging and Compiling Programs.

---

### Post by curtis on 2008-05-28
Thanks.

---

### Post by Vadi on 2008-05-29
Here's what I understand:

- to get your program into Ubuntu, you either need to get it packaged in Ubuntu, or in Debian. To try Ubuntu, you either need to be a MOTU (people who get to package), or make a ticket on launchpad with the "needs-packaging" tag. Don't rely on the launchpad ticket - in my personal experience, a program I've submitted already missed two Ubuntu releases. So, try getting it into Debian, because Ubuntu during the alpha stage regularly syncs with Debian.

- you shouldn't bundle anything, at all. If Ubuntu doesn't provide it, you'll need to get that library packaged. Libraries you need should be listed as dependencies, so apt-get automatically installs them. 

In regards to server software though, I have absolutely no idea, so I hope an expert clears this up.

---

