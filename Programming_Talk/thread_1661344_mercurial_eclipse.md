---
title: "mercurial eclipse"
date: 2011-01-06
forum: Programming Talk
---

### Post by leg on 2011-01-06
I have 10.04 and installed the eclipse mercurial plugin but every time I start up eclipse I get the error


> Error
Thu Jan 06 20:51:31 GMT 2011
Unsupported hg version:1.4.3. Expected is at least1.5.0.

I have installed mercurial through synaptic and the version in there is 1.4.3. Can I update mercurial to at least 1.5.0 without having to update  the whole os.

---

### Post by leg on 2011-01-07
Does no one else have this problem?

---

### Post by l'oranger on 2011-01-08
Hi Leg,

I do ran into the same issue today.

You can upgrade to a more recent mercurial version (at the time of writing, 1.7.3, sufficient for the Eclipse mercurial plugin which require 1.5.0) by setting-up a PPA:

```
sudo add-apt-repository ppa:mercurial-ppa/releases
sudo apt-get update
sudo apt-get install mercurial
hg --version
```

HTH,

--Laurent

---

### Post by leg on 2011-01-09
thank you

---

