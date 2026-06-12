---
title: "repos/server location"
date: 2006-04-21
forum: Repositories &amp; Backports
---

### Post by balilu on 2006-04-21
i don't know if this is the right place to post it. but anyway. i wish to know if server mt.ubuntu.com or any other server starting with my country code (mt) such as mt.releseas.ubuntu.com. are these servers found in my country and what is the difference to have gb instead of mt or any other country code. i wish to know because i have a limit on how much i can download from foreign servers but no limit on how much i can download on local servers.

any help?? sry again if this isn't the place to post it

---

### Post by mjm115 on 2006-04-21
Please disregard my last post

---

### Post by balilu on 2006-04-21
anyone??

---

### Post by SgtDude on 2006-04-27
I did a quick nslookup of some different prefixes for releases.ubuntu.com.  Here are the results:

Name:    releases.ubuntu.com
Addresses:  85.133.25.9, 85.133.25.13, 85.133.25.2, 85.133.25.3
          85.133.25.4, 85.133.25.5, 85.133.25.6
Aliases:  us.releases.ubuntu.com

Name:    releases.ubuntu.com
Addresses:  85.133.25.6, 85.133.25.9, 85.133.25.13, 85.133.25.2
          85.133.25.3, 85.133.25.4, 85.133.25.5
Aliases:  gb.releases.ubuntu.com

Name:    releases.ubuntu.com
Addresses:  85.133.25.6, 85.133.25.9, 85.133.25.13, 85.133.25.2
          85.133.25.3, 85.133.25.4, 85.133.25.5
Aliases:  jp.releases.ubuntu.com

And yours...

Name:    releases.ubuntu.com
Addresses:  85.133.25.13, 85.133.25.2, 85.133.25.3, 85.133.25.4
          85.133.25.5, 85.133.25.6, 85.133.25.9
Aliases:  mt.releases.ubuntu.com

It would appear that most of the country-coded servers actually point to the same cluster of servers (releases.ubuntu.com).  Meaning that mt.releases.ubuntu.com is not, in fact, in your country.  Sorry.

If you need a local Repository, Open Sense Solutions will ship you the Main, Restricted, Universe, and Multiverse repositories for Breezy (5.10) on 3 DVD's for about $5 USD plus shipping.  ([www.groovix.com](www.groovix.com))  (I don't mean to advertise, but this is the only place I found where I could buy the repos on DVD).

If you were really motivated, you might even set up a public mirror, and then you could be mt.releases.ubuntu.com.  But maybe I'm way out there...

---

