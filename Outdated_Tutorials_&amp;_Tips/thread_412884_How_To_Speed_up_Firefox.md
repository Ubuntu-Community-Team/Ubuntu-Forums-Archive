---
title: "How To Speed up Firefox"
date: 2007-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by kittyhawk63 on 2007-04-18
[CENTER]**This is [COLOR=Red]ONLY[/COLOR] for Broadband users**
[/CENTER]
This information was found on the Firefox site.[B]

*Start Firefox*[/B]

Type "[SIZE=3]**about:config**[/SIZE]" into the address bar and hit <return> or <enter>.

Scroll down and look for the following:
network.http.pipelining 
network.http.proxy.pipelining
network.http.pipelining.maxrequests

Normally, the browser will make one request to a web page at a time. When you enable pipelining, it will make several requests at once, which speeds up page loading.

Alter (set) the following lines by **double clicking** them: (They will go from "false" to "true".)

1. Set "network.http.pipelining" to "true"

2. Set "network.http.proxy.pipelining" to  "true"

3. Set "network.http.pipelining.maxrequests" to some number like "30". This means it will make 30 requests at once.

4. Lastly, right click anywhere and select "New" -> "Integer". Type "[SIZE=3]**nglayout.initial.delay**[/SIZE]" and set its value to "[SIZE=3]0[/SIZE]". (zero)
This value is the amount of time the browser waits before it acts on information it retrieves.

Now, if you're using broadband, the web pages should load much faster. I noticed a considerable difference on charter.com. :)

kh

---

### Post by SorenK on 2007-04-19
That actually worked quite well.  I already had most of the settings that way, but the initial delay one made quite a difference.

---

### Post by floke on 2007-04-19
That last one seems to have given me a nice extra zip.
Cheers for the heads up!

---

### Post by pelikan on 2007-04-19
the Fasterfox extension will do this for you as well.

---

### Post by SorenK on 2007-04-21
> **pelikan said:**
> the Fasterfox extension will do this for you as well.

It didn't do the last one.

---

### Post by pelikan on 2007-04-21
> **SorenK said:**
> It didn't do the last one.

Thanks. I'll add that one.

---

