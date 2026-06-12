---
title: "Installing JRE 1.5 from Terminal"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by areyouamogul on 2012-12-12
Hi,

I've already downloaded the thing, but there's no executable I can see. Not like I need one, you silly OS! I mean, why would users want an easy way to install packages?

**Full-lunged* *Sigh**

Well, that's that. Anyone? I'd love if someone could just write a couple lines of sudo, gksudo, install-apt mumbo jumbo and just get through this. 

Thanks.

---

### Post by Cheesemill on 2012-12-12
Why Java 5? It's outdated and unsupported as well being unsecure.

To install Oracle Java 7 you can just do:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

This information can be found on the Java page on the Ubuntu documentation site.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by audiomick on 2012-12-12
> **areyouamogul said:**
> why would users want an easy way to install packages?

You mean other than the software centre or synaptic? Why do you need a Java environment other than that one that is available there?

---

