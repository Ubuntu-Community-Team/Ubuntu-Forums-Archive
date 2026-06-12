---
title: "hoary-updates...what will it be used for ?"
date: 2005-03-22
forum: Repositories &amp; Backports
---

### Post by ubuntu_demon on 2005-03-22
Hi,

hoary-updates what will it be used for ?

I mean these lines in the sources.list :

## Uncomment after release to continue getting updates:
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

Will it be used for introducing new important features like menu editor ? Or just for important bugfixes ? Or for something like service-packs ? Or.... ?

thnx

---

### Post by jdodson on 2005-03-22
[QUOTE=demon666_nl]Hi,

hoary-updates what will it be used for ?

I mean these lines in the sources.list :

## Uncomment after release to continue getting updates:
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

Will it be used for introducing new important features like menu editor ? Or just for important bugfixes ? Or for something like service-packs ? Or.... ?

thnx[/QUOTE]

thats a really good question, any developers want to take a crack at this?  i have seen the repository and i have heard some rumblings about something like this in some comments by developers.

---

### Post by ubuntu_demon on 2005-03-24
anyone?

---

### Post by ubuntu_demon on 2005-03-31
*bump*

---

### Post by steffen on 2005-04-03
Alot of users on this forum have asked this question. And many have reported that their sources.list has a *problem* with hoary-updates not working.

Guess we'll see this start working in a couple of days. But still no-one has been able to tell what the list is for. Is it some sort of "official Ubuntu backports"? I.e. updates to Gaim, OOo, etc. that are not strictly security updates... That's what I would assume.

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=steffen]Alot of users on this forum have asked this question. And many have reported that their sources.list has a *problem* with hoary-updates not working.

Guess we'll see this start working in a couple of days. But still no-one has been able to tell what the list is for. Is it some sort of "official Ubuntu backports"? I.e. updates to Gaim, OOo, etc. that are not strictly security updates... That's what I would assume.[/QUOTE]
 hoary-updates has to be commented untill release.

Maybe it's for bug fixes that don't include new features. But in a sort of service-packs kind of way.

---

### Post by Patrick on 2005-04-04
It says that you uncomment it when there is a release. So i think you uncomment them on wensday at upgrade to the final release

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=Patrick]It says that you uncomment it when there is a release. So i think you uncomment them on wensday at upgrade to the final release[/QUOTE]
 true
or only after they announce there are upgrades in it (if you want to be careful)

---

### Post by Patrick on 2005-04-04
[QUOTE=demon666_nl]true
or only after they announce there are upgrades in it (if you want to be careful)[/QUOTE]

and thats what we want to be  :smile:

---

### Post by daniels on 2005-04-04
Various non-security (but critical bugfix) updates to Hoary: only very well-tested stuff.  This didn't go through for Warty because it was not enabled in sources by default, but we had the conondrum where we had to put calendar updates into the security repositories (I think) because we didn't have a functional warty-updates.  So yeah, just small, well-tested, bug fixes.

---

### Post by jdong on 2005-04-04
A great place to stuff next year's April Fool's joke, right? ;)

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=daniels]Various non-security (but critical bugfix) updates to Hoary: only very well-tested stuff.  This didn't go through for Warty because it was not enabled in sources by default, but we had the conondrum where we had to put calendar updates into the security repositories (I think) because we didn't have a functional warty-updates.  So yeah, just small, well-tested, bug fixes.[/QUOTE]
 sounds good :)

---

### Post by ubuntu_demon on 2005-04-07
I just removed the comments from my sources.list and apt-get update keeps working :)

---

