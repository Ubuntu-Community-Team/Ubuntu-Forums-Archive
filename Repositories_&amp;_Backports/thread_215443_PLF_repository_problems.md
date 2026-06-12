---
title: "PLF repository problems"
date: 2006-07-13
forum: Repositories &amp; Backports
---

### Post by nietzschewept on 2006-07-13
I've been using these repositories for months now:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

Secondary:

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

Suddenly, they no longer work, and I'm unable to find alternatives that do work.  Any suggestions...

Thanks

---

### Post by evilmrt on 2006-07-14
same here! I guess I'll try back later....

---

### Post by dolby on 2006-07-14
noticed that on the ftp the ubutu section doesnt exist..
maybe the repo wont support ubuntu anymore?

---

### Post by gr8nash on 2006-07-14
yeah its down.. =( i REALLY hope that comes back online soon.. ](*,)

---

### Post by aysiu on 2006-07-15
Still down..

---

### Post by sidd-tx on 2006-07-15
Same here. 

This has happened to me before, but usually after a few hours, I was able to connect. Never have I had to wait this long before. A little worried here.

The RPM repos for PLF all work, but not the Ubuntu ones. ](*,) 

Hope it comes back online...

Sidd...

---

### Post by strumer on 2006-07-15
I've been checking it constantly since yesterday.  I just got a new widescreen monitor and wanted to add dvd support.

It's weird that everything else is there, except the ubuntu packages.

I guess I could use alien to convert from rpms to debian packages.  Although, i've never done this before.

---

### Post by k0fman on 2006-07-15
hi,

the PLF problem is explained on the [manager's blog]("http://blog.freecontrib.org/index.php/2006/07/14/24-ns81-c-est-fini")[french]
so, to summarize, the partnership between OVH and Antesis seems to be broken and so the server (ns81) which is the Ubuntu PLF primary mirror is down BUT Philippe Mironov (the manager) wrote that he will set up a new server to provide the PLF repository.

---

### Post by strumer on 2006-07-16
looks like packages.freecontrib.org is back online.

---

### Post by jsvidyad on 2006-07-16
The following lines seem to work.


deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

---

### Post by matthew on 2006-07-16
FYI: this site keeps updated info posted on repositories, etc. for PLF

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by hazza96 on 2006-07-16
I having issues with the PLF repo, I changed it so that it no longer had ubuntu in the url so that is not the issue.

I hit that with my web browser and found that the directory [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/) contains Packages.gz

My error message indicate that Dapper is looking for Packages.bz2

Anyone else having this problem? What can I do to fix it?

---

### Post by silverback011 on 2006-07-16
Yes, I am having the same issue.  I am not sure what is happening yet.  I am in the process of trying to understand it.  I think it is just a path issue.

The funny part is I have not used ubuntu until yesterday.  I thought I had set up the repositories wrong.  Glad I am not new to Unix/Linux or I would be frustrated at this point.

---

### Post by hazza96 on 2006-07-16
> **silverback011 said:**
> Yes, I am having the same issue.  I am not sure what is happening yet.  I am in the process of trying to understand it.  I think it is just a path issue.
I don't think it is a path issue, I have already corrected that in my sources.list

It's an issue with the file being a GZ file not a bz2 file, are all of them GZ or are they supposed to be bz2?

I just looked at [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/) and there is both a bz2 and a gz file.

How do we configure apt to look for/use the GZ file instead?

---

### Post by heislord5 on 2006-07-17
I can't get it to work either.

---

### Post by Uncle Spellbinder on 2006-07-18
> **jsvidyad said:**
> The following lines seem to work.


deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

They certainly do. Thanks! :D

---

