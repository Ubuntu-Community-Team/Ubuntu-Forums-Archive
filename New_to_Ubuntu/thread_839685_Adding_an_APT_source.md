---
title: "Adding an APT source"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by zaivala on 2008-06-24
I have tried to add a source in Synaptic, to no avail -- after typing in all the Source information, the Add+ button is still ghosted.

In this particular case, I am trying to add Banshee 1.0.0, which is just out.  I'm already off-topic on my own new topic, but I've tried everything I know of to try.  After trying to install it in Terminal and Synaptic, I downloaded the .deb file from the website, and on installation I got the following error message:

Error: Dependency is not satisfiable: libboo2.0-cil

Moss

---

### Post by drs305 on 2008-06-24
I went to the site. Did you select the correct version of the source - hardy or gutsy.

For me, to add the repositories I went to synaptic, settings, repositories, third-party, Add, and then entered separately each of these lines:
```

deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main

```

Both took and I selected Reload when finished and banshee-1 was listed.

This is the link I got the sources from:
[https://edge.launchpad.net/%7Ebanshee-team/+archive]("https://edge.launchpad.net/%7Ebanshee-team/+archive")

---

### Post by zaivala on 2008-06-24
> **drs305 said:**
> I went to the site. Did you select the correct version of the source - hardy or gutsy.

For me, to add the repositories I went to synaptic, settings, repositories, third-party, Add, and then entered separately each of these lines:
```

deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main

```

Both took and I selected Reload when finished and banshee-1 was listed.

This is the link I got the sources from:
[https://edge.launchpad.net/%7Ebanshee-team/+archive]("https://edge.launchpad.net/%7Ebanshee-team/+archive")

OK, what I did wrong is to not type "deb" at the start of the line.  Works fine.  I need a TFM to R...

Hugs,
Moss

---

