---
title: "kubutu repositories"
date: 2005-03-18
forum: Repositories &amp; Backports
---

### Post by search66 on 2005-03-18
I was so happy to see ubuntu finally get a sweet KDE... 

Anyway.  Has anyone have any ideas on how to add repositories for this release?

---

### Post by lao_V on 2005-03-18
[QUOTE=search66]I was so happy to see ubuntu finally get a sweet KDE... 

Anyway.  Has anyone have any ideas on how to add repositories for this release?[/QUOTE]

Its in the universe repository at the moment. However, I think, after the official release it may be moved to main

---

### Post by search66 on 2005-03-18
Yea... it looks like it is just the universal repository (which isn't a bad thing)... but with (k)naptic, I'm not sure how to actually *add* repositories... doesn't seem like there's a way.

---

### Post by oracledarren on 2005-03-18
easiest way to add respo's is to drop to a terminal and type:-

sudo gedit /etc/apt/sources.list

and add them in manually

gedit can be replaced with your favourite editor by the way  (gedit is due to my preference of gnome) :mrgreen:

---

### Post by search66 on 2005-03-18
You gnomies!  :P

Huhm... no 'sudu' command...

---

### Post by Shambler on 2005-03-18
Read closer. It's "sudo" with an o!  :D

---

### Post by search66 on 2005-03-18
Sometimes I wish I could disappear into the n00bie shadows.   :P

---

### Post by search66 on 2005-03-18
[QUOTE=search66]Sometimes I wish I could disappear into the n00bie shadows.   :P[/QUOTE]
 Worked like a charm... thanks!!

---

### Post by gunnyman on 2005-03-19
IMHO a better package manager is kpackage.
just apt-get install kpackage.  Kynaptic looks like a kludge to me.

---

### Post by lao_V on 2005-03-19
Kynaptic is in a very early development stage, yet stable. You can find/install/upgrage software with it but certain other features like package description and changing repositories are not applied yet. Synaptic is great not sure why they had to develop another for KDE.

---

### Post by josiah on 2005-03-21
synaptic, kynaptic and kpackage are all frustrating to me. for simple update jobs, i like the ubuntu-update applet; but apt-get and aptitude are the way to go. 

upgrading from debian sarge to hoary was murderously painful in synaptic (i think it may actually have been impossible), but aptitude allowed me to filter through all the broken packages and fix **all** of the dependency issues.

---

