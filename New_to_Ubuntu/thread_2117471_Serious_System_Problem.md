---
title: "Serious System Problem"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by carterlangley on 2013-02-18
Hi all,

Have moved over to Ubuntu as Fedora kept of crashing! Anyway, I am having a problem with Raring. 

Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en

This is what the little no entry sign says. I have tried using apt-get to update the repositories but it won't. Anybody able to help?

---

### Post by ajgreeny on 2013-02-18
> **carterlangley said:**
> Hi all,

Have moved over to Ubuntu as Fedora kept of crashing! Anyway, I am having a problem with Raring. 

Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en

This is what the little no entry sign says. I have tried using apt-get to update the repositories but it won't. Anybody able to help?
It is not a good idea to try Raring Ringtail (13.04) as your first installation of ubuntu, or at least, not at thios time of its life, as it is not fully released and therefore is still in development as an alpha 2, and problems and crashes are to be expected.

If I were you I would start again with 12.04.2, which is an LTS version supported till 2017, and if you like and can manage unity is stable and much more bug-free.  I can't comment on 12.10 as I've not used it, but it does not appear to have much to set it apart from nor better than 12.04.2.

---

### Post by grahammechanical on 2013-02-18
This is something you can try. In a terminal run this command

```
sudo rm /var/lib/apt/lists/* -rf
```

that will remove/delete all the scripts (sources lists) in /var/lib/apt/lists folder.

then run

```
sudo apt-get update
```

that will replace those scripts or lists of packages. I have had to do this a few times in the past when running the development branch. It was the same package (i18n_Translation-en) that caused the problem. Only this happened during the Quantal development cycle.

Of course, you can remove (rm) just that particular package list if you want.

Regards.

---

