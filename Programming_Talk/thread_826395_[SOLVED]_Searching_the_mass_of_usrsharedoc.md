---
title: "[SOLVED] Searching the mass of /usr/share/doc"
date: 2008-06-11
forum: Programming Talk
---

### Post by Tigera on 2008-06-11
Greetings,

Most of the time, programs and developer libraries put their documentation in /usr/share/doc, but often times, I find it hard to find anything and the directory is huge.  What I'd really like is an interface that gives me one application to browse all of the documentation, be it info or man pages, HTML files, SGML docbooks, or otherwise.  (It would be REALLY cool if I could type this into, say, my web browser).  I thought of something like Beagle, but it doesn't search info pages or SGML docbooks, and htdig only searches HTML files.
Has anyone thought of any creative solutions for handling this?

---

### Post by bruce89 on 2008-06-11
Yelp is the tool you seek. It has a wee search box. It searches and displays man pages, info pages and docbook stuff.

It is the GNOME help program.

---

### Post by Tigera on 2008-06-11
I looked through yelp but could not find any information that is in /usr/share/doc; I tried putting in "boost.python", for example, and it returned nothing. - is there a way to configure it to do so?

---

### Post by dbera on 2008-06-12
> **Tigera said:**
> Greetings,

Most of the time, programs and developer libraries put their documentation in /usr/share/doc, but often times, I find it hard to find anything and the directory is huge.  What I'd really like is an interface that gives me one application to browse all of the documentation, be it info or man pages, HTML files, SGML docbooks, or otherwise.  (It would be REALLY cool if I could type this into, say, my web browser).  I thought of something like Beagle, but it doesn't search info pages or SGML docbooks, and htdig only searches HTML files.
Has anyone thought of any creative solutions for handling this?

Beagle indeed searches docbook files, info and man pages. And beagle ships with a crontab program that updates the system-wide documentation index from /usr/share/doc each night. This index is not monitored real time like the usual beagle indexes. Google for "beagle system wide index" and look in /etc/beagle/crawl-rules and /etc/cron.daily/beagle...

If beagle is running, then yelp uses beagle to search in those documentation. beagle-search does not search documentation by default, since it clutters too much but IIRC it has a command line switch to enable searching documentation index.

---

### Post by Tigera on 2008-06-12
Works fine!  Thank you!

---

