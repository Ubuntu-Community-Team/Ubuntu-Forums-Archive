---
title: "Determining mirror locations"
date: 2006-02-12
forum: Repositories &amp; Backports
---

### Post by Tony6316 on 2006-02-12
Hi,

I'm in the US and have a number of mirrors to choose from.  I'd like to use the nearest one to my home in Pennsylvania.  Is there any way to determine the precise geographic location of a mirror?  I've been able to figure some of them out, e.g., one of the sites has 'oakland' as part of its name indicating it's probably in Oakland, California but I'd like to find something closer.  The wiki archive only gives the names and not their locations in the US.

tony6316

---

### Post by nurdin on 2006-02-12
I assume you want to find the mirror with the highest bandwidth for you? I used to use a program called apt-spy in debian and it appears to be in the ubuntu repositories, (although I get pretty decent downloads in ubuntu so I haven't bothered using it anymore) what it does is takes a look at all the servers in a region you specify and finds which one is the fastest and re-writes your /etc/apt/sources.list with that mirror.

Hope that helps.

---

