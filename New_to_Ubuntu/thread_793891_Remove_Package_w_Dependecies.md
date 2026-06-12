---
title: "Remove Package w/ Dependecies"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Sinkingships7 on 2008-05-14
I installed the package ubuntu-restricted-extras. However, I was just messing around to see if it would change something, and I would like to get rid of it. Obviously, the package just has dependencies and doesn't really do anything by itself. I would like to get rid of everything it installed. My problem is that I can't find out *what* it installed to remove them.

Can someone help me out here? My question is: what packages does ubuntu-restricted-extras install so I can 'sudo aptitude remove' them?

---

### Post by Joeb454 on 2008-05-14
I believe it says when you install it. You could also try synaptic to see if that tells you.

I do know that it contains a bunch of codecs, and Flash as well :)

---

### Post by aquavitae on 2008-05-14
In synaptic, there is a list of filters on the bottom left. One of them (I think Custom, but I could be wrong) has a filter for auto-removable. This should list all the packages that you haven't manually installed and which are no longer required. Select them and Completely Remove.

---

### Post by asrai on 2008-05-14
if you're using hardy, there is a list here: [http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)

There are links to the restricted-extras for earlier releases from there too.

---

### Post by Sinkingships7 on 2008-05-14
> **asrai said:**
> if you're using hardy, there is a list here: [http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)

There are links to the restricted-extras for earlier releases from there too.

Just what I was looking for. Thanks!

---

