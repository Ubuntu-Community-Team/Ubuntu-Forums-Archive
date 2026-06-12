---
title: "no sudo apt-get boswars?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by ant2ne on 2008-09-17
On one ubuntu computer i can ```
sudo apt-get install boswars
``` on the other ubuntu computer I can not. Both systems seem to have universe and multiverse enabled. What gives?

---

### Post by kjohansen on 2008-09-17
This site has some info.  You need to use flags for "unauthenticated"  one computer may have that set in a settings.

[http://ubuntusoftware.info/ubuntu_games/bos_wars.html](http://ubuntusoftware.info/ubuntu_games/bos_wars.html)

```

sudo apt-get install -y --allow-unauthenticated boswars boswars-data

```

---

### Post by drs305 on 2008-09-17
boswars isn't in the standard ubuntu repositories. Go to this page to read how to add the repository:
[http://repoubuntusoftware.info/]("http://repoubuntusoftware.info/")

Your other computer probably has this commericial repository in sources.list.

Read the entire page, there may be a PGP/GPG key and make sure the repo you add is for your version (gutsy, hardy, etc).

---

### Post by nowshining on 2008-09-17
> **drs305 said:**
> boswars isn't in the standard ubuntu repositories. Go to this page to read how to add the repository:
[http://repoubuntusoftware.info/]("http://repoubuntusoftware.info/")

Your other computer probably has this commericial repository in sources.list.

Read the entire page, there may be a PGP/GPG key and make sure the repo you add is for your version (gutsy, hardy, etc).

hmmm i see none for gutsy :/

I tried the instructions only feisty/edgy i guess

---

### Post by drs305 on 2008-09-17
After the last post I did some searching and found references to debs with dates in 2008. Upon further investigation, I think you might find the package in the Updates tab under "unsupported updates - backports" repository. Enable this repository in the Updates tab of synaptic and reload to refresh the list.

---

