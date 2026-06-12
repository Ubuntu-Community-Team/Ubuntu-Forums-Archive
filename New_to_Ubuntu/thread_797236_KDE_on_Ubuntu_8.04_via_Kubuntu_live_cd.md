---
title: "KDE on Ubuntu 8.04 via Kubuntu live cd"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by sharks on 2008-05-17
I have Ubuntu HH installed. I also have kubuntu HH live cd. I want to install KDE on Ubuntu thru Kubuntu cd?

---

### Post by Xiong Chiamiov on 2008-05-17
It would be vastly easier to install through the 'net, by doing one of the following:
```

sudo aptitude install kubuntu-desktop
sudo aptitude install kde-core

```
The first will install with all of the KDE apps, the second will install just the necessary things to run KDE.

That said, you might be able to install off of the CD if you enable the CD as a repository in Synaptic.  I'm not quite sure of how to go about it (I use adept), but perhaps... edit -> add CDROM?

---

### Post by .nedberg on 2008-05-17
You could add the cd as a repository and install kubuntu-desktop throug Synaptic.

---

