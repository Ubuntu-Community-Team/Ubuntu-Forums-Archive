---
title: "How can I run 'apt-get build-dep vlc'"
date: 2007-08-02
forum: Programming Talk
---

### Post by yinglcs2 on 2007-08-02
Hi, 

I am trying to run 'apt-get build-dep vlc', but i get the following error:

$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for vlc

Can you please help me to resolve them?

Thank you.

---

### Post by yinglcs2 on 2007-08-02
What does it mean by:

$ sudo apt-get build-dep vlc;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

---

### Post by Rocket2DMn on 2007-08-02
Do you have the universe repository enabled?  In Synaptic, go to Settings->Repositories and make sure the universe repository is enabled.
OR
you can run ```
gksudo gedit /etc/apt/sources.list
``` and removing the # in front of the lines for universe.  Then run
```
sudo apt-get update
sudo apt-get build-dep vlc
```

---

### Post by walkerk on 2007-08-02
I'm sure it did. We covered this in another thread. Was another thread necessary?

---

