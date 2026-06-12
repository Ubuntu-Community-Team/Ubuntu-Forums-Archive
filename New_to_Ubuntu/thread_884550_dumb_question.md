---
title: "dumb question"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-09
how do you do a distribution upgrade in apt-get,or is there another way?
rick

---

### Post by starcannon on 2008-08-09
> **rixtr66 said:**
> how do you do a distribution upgrade in apt-get,or is there another way?
rick

*caveat* be sure to back up all important data in /home unless you have it on its own separate partition.

There are no dumb questions, there may be dumb answers, and I may give some; that said, try:

```
sudo aptitude dist-upgrade
```

and see if that does what your wanting.

---

### Post by zipperback on 2008-08-09
> **rixtr66 said:**
> how do you do a distribution upgrade in apt-get,or is there another way?
rick


I've found that the best way is to just do a full clean reinstall of my computer using whatever the newest version I want to run is. Sometimes things have change dramatically from one release version to another, and I just feel better about having the system clean and tidy rather than possibly have a bunch of old files possibly still on my computer.

It's just a matter of personal preference for myself.

However you can also do it via the apt-get installer and just update your system using the following.

```

sudo apt-get update && sudo apt-get dist-upgrade

```

What ever method you decide to use, be sure to run a full backup of all your important data FIRST.


- zipperback
:popcorn:

---

### Post by rixtr66 on 2008-08-09
thank you!!!!!!!!!!!!!!

---

### Post by zipperback on 2008-08-09
> **rixtr66 said:**
> thank you!!!!!!!!!!!!!!


You're welcome.

- zipperback
:popcorn:

---

### Post by Jimmy9pints on 2008-08-09
> caveat be sure to back up all important data in /home unless you have it on its own separate partition.


A good way to do that can be found here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then reinstall after that. 

Cheers,

---

### Post by hyper_ch on 2008-08-09
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

