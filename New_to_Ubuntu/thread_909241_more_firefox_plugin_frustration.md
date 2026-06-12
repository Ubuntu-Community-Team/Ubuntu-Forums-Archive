---
title: "more firefox plugin frustration"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by cjh19460 on 2008-09-03
I'm running Ubuntu 8.04 with Firefox 3.
Java is enabled in Firefox.
I have sudo apt-get installed all java packages, including the plugin.
I have universe/multiverse

I am running 32-bit Ubuntu and everything else, even though I have a dual-core 64-bit processor (before I started with this, a friend told me that there were sometimes issues with 64-bit).

I've  read a bunch of the forum posts but so far have not seen a definitive answer, other than asking about things I've done, like make sure java is enabled, installed, etc.

Under System|Administration there is now a Sun Java Plugin tool,  I've looked there and don't see anything strange.

here's the site I'm going to:
[URL="http://www.goes.noaa.gov/HURRLOOPS/atvs.html"]
http://www.goes.noaa.gov/HURRLOOPS/atvs.html[/URL]

Any help?

Thanks,
Carl

---

### Post by philinux on 2008-09-03
Loads here but not sure what I'm meant to see.

What does ```
about:plugins
``` report?

---

### Post by gandaran on 2008-09-03
go to tools » addons/extras » plugins, you should see something like this **Java(TM) Plug-in 1.6.0_06-b02 ** right click the plugin, see if it's enabled or disabled.

---

### Post by kaibob on 2008-09-03
I'm also having trouble with the Firefox Java plugin. If I go to the government time page, a message is displayed that a plugin is required: 

[http://www.time.gov/timezone.cgi?Central/d/-6/java](http://www.time.gov/timezone.cgi?Central/d/-6/java)

Firefox offers to install missing plugins and displays four options (see thumbnail). I tried all of the plugins and none work.

---

### Post by kaibob on 2008-09-04
I installed the java6 plug-in by way of synaptic; it included quite a few dependencies. Now, both the site mentioned by the OP and the government time clock work fine. I've provided a thumbnail of the OP's site.

---

### Post by alienexplorers on 2008-09-04
Does your java pass the test on this page:
[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

---

### Post by kaibob on 2008-09-04
> **alienexplorers said:**
> Does your java pass the test on this page:
[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

I don't know who your question was directed at, but I could see the dancing Duke logo image, which means that JRE is functioning correctly. The page did indicate that I was using an older version of JRE, but I intend to stick with what I have until a new version becomes available from Ubuntu updates.

---

