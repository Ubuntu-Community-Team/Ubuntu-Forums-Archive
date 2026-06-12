---
title: "django deployment on shared-hosting"
date: 2010-06-19
forum: Programming Talk
---

### Post by mo.reina on 2010-06-19
i have a django-powered site in my laptop, developed using the development server.  now i'm slightly confused how to set it up in a shared-hosting environment (no access to the httpd.conf file).

i've looked into dedicated django hosting solutions that offer 1-click django installations, but these seem to deal with totally new projects, there isn't any information on how to deploy an already existing project.

---

### Post by DanielWaterworth on 2010-06-19
You'll need to find a server that allows either mod_python or mod_wsgi hosting. For my Django hosting I use a VPS, but this is a little more expensive.

---

### Post by mo.reina on 2010-06-20
how about the .httaccess file?  i read some articles that mention this as a way to deploy on share-hosting but there aren't many details...

---

### Post by mo.reina on 2010-06-24
*bump

---

### Post by trent.josephsen on 2010-06-25
What host are you using?  If you ask nicely, they may set it up for you.  HostGator did for me.

---

### Post by mo.reina on 2010-06-25
it's a host called Enter, based in milan, where i live.  

i'm beginning to think i'm going to have to migrate, they don't allow access to the shell, which i think is paramount, since i don't want to be calling a tech everytime and explaining things when they don't know what i'm talking about.  

i called them today and asked about django support and they didn't know what it was, didn't understand that i wanted them to install it for me (since i have no access to the shell), and documentation on django in italian is scarce (they don't understand english).

on a side note, has anyone deployed django with network solutions? a potential client uses them as hosts and i'll probably need to deploy a django project with them if i take on the project.

---

### Post by DanielWaterworth on 2010-06-25
> **mo.reina said:**
> on a side note, has anyone deployed django with network solutions? a potential client uses them as hosts and i'll probably need to deploy a django project with them if i take on the project.

No, but there are expensive. Take VPS for example, it's probably about 2-3 times more expensive than other companies offering the same.

---

